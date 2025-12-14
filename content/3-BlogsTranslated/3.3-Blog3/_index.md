---
title: "How AWS Lambda SnapStart Works"
date: "2025-08-19"
weight: 3
chapter: false
pre: " <b> 3.3. </b> "
---

# Under the hood: how AWS Lambda SnapStart optimizes function startup latency

*By Ayush Kulkarni and Eric Heinz | August 19, 2025*

When building applications with AWS Lambda, optimizing function startup is an important step to improve performance for latency-sensitive applications. The largest contributor to startup latency (often called cold start time) is the time Lambda spends initializing your function code. Lambda SnapStart is a feature available for Java, Python, and .NET runtimes that reduces cold start latency from seconds (or higher) to sub-second levels. SnapStart typically requires no or minimal changes to your application code and makes it easier to build responsive and scalable applications without implementing complex performance optimizations.

If your function already initializes within a few hundred milliseconds, then AWS recommends using Lambda Provisioned Concurrency to achieve startup latency in the tens of milliseconds.

## What is cold start?

Lambda runs your function code in an isolated, secure execution environment using Firecracker microVM technology. When you invoke a Lambda function for the first time, Lambda creates a new execution environment for that function to run. Lambda downloads your function code, starts the language runtime environment, and runs the function's initialization code (the code outside the handler). This initialization process (INIT) is called a cold start. Lambda then runs the function's handler code to execute the invocation. The following figure shows the lifecycle of a typical function invocation.

![Figure 1. Function invocation lifecycle without SnapStart](/images/3-BlogsTranslated/3.3-Blog3/figure1.png)

A Lambda execution environment only processes one function invocation at a time. After the function finishes running, Lambda doesn't immediately stop the execution environment. When your function receives another invocation request, Lambda will attempt to route that request to an idle but already running execution environment. Since the INIT process has already been run for this execution environment, this invocation is called a warm start.

The final step of cold start, function code initialization, typically takes the most time. This depends on the startup tasks you perform in your code and the language runtime or framework you use. For languages like Java and .NET, startup latency is affected by just-in-time compilation of static code in loaded classes. For Python, it can be affected if your executed code contains many or large modules.

## Phase 1: Creating a snapshot for your Lambda function

When using SnapStart, the Lambda execution environment lifecycle changes. When you enable SnapStart for a specific function, publishing a new function version triggers the snapshot creation process. This process runs the function initialization phase and creates an immutable, encrypted Firecracker microVM snapshot of the initialized execution environment's memory and disk state, then caches and chunks that snapshot for reuse.

Code branches not executed during initialization, such as classes loaded on-demand through dependency injection, will not be included in the function's snapshot. To improve snapshot effectiveness, proactively execute code branches during the initialization phase, or use runtime hooks to run code before Lambda creates the snapshot.

Snapshot creation can take several minutes, during which your function version will be in PENDING state, and transitions to ACTIVE when the snapshot is ready.

When you invoke your function subsequently, Lambda will restore new execution environments from this snapshot. This optimization makes function invocation faster and more predictable, as creating a new execution environment no longer requires the initialization process.

![Figure 2. Function invocation lifecycle with SnapStart](/images/3-BlogsTranslated/3.3-Blog3/figure2.png)

## Phase 2: Storing snapshots for low-latency retrieval at Lambda scale

Lambda operates at large scale, processing tens of billions of function invocations each month. To efficiently manage and retrieve snapshots at this volume of traffic, Lambda uses storage and caching components. These components include three tiers: Amazon S3 for durable storage, a dedicated distributed cache, and a local cache on Lambda worker nodes.

Lambda stores function snapshots in Amazon S3, chunking them into 512 KB pieces to optimize retrieval latency. Retrieval latency from Amazon S3 can take up to hundreds of milliseconds per 512 KB chunk. Therefore, Lambda uses a two-tier cache to accelerate snapshot retrieval.

When you enable SnapStart, during optimization, Lambda will store snapshot chunks in a layer-two (L2 cache). This tier is a cluster of dedicated distributed cache instances built by Lambda. Lambda stores a separate copy of each snapshot for each AWS Availability Zone (AZ).

Lambda also maintains a layer-one (L1 cache) located on Lambda worker nodes, which are Amazon EC2 instances that process function invocations. This tier is locally available, so it provides the fastest performance, typically 1 millisecond for a 512 KB chunk. Functions with more frequent invocations are more likely to have their snapshot chunks stored in this tier.

![Figure 3. SnapStart tiered caching](/images/3-BlogsTranslated/3.3-Blog3/figure3.png)

## Phase 3: Resuming execution from restored snapshots

Resuming execution from snapshots with low latency is the final phase of SnapStart. This phase involves loading the retrieved snapshot chunks into your function's execution environment. Typically, only a small portion of the retrieved snapshot is needed to serve an invocation.

Storing snapshots as chunks allows Lambda to optimize the resumption process by proactively loading only the small subset of chunks needed. To do this, Lambda tracks and records the snapshot chunks that the function accesses during each invocation, as shown in the following figure.

![Figure 4. Initial invocation, recording chunk access pattern](/images/3-BlogsTranslated/3.3-Blog3/figure4.png)

After the first function invocation, Lambda references this recorded chunk access data for subsequent invocations, as shown in the following figure. Lambda proactively retrieves and loads the "working set" of these chunks before they are needed for execution. This significantly accelerates cold-start latency.

![Figure 5. Subsequent invocation, loading chunks in access order](/images/3-BlogsTranslated/3.3-Blog3/figure5.png)

## Understanding SnapStart function performance

### Function performance improves with more invocations

Functions that are invoked more frequently are more likely to have snapshots stored in the L1 tier cache, which provides the fastest retrieval latency. Portions of snapshots that are less accessed for infrequently invoked functions are less likely to be present in the L1 tier, resulting in slower retrieval latency from L2 cache and S3 tiers.

### Preload code branches to optimize snapshot restoration latency

To maximize SnapStart benefits, preload dependencies, initialize resources, and perform heavy computational tasks that cause startup latency in your initialization code rather than in the function handler. Code branches not executed during the function's INIT phase will not be included in the function's snapshot.

### Performance varies depending on function size

SnapStart performance depends on how quickly Lambda can retrieve and load cached snapshots into your function's execution environment. Larger function sizes increase snapshot size, and therefore increase the number of chunks, which causes performance to vary for functions of different sizes.

### Not all functions benefit from SnapStart

SnapStart is designed to improve startup latency when function initialization takes several seconds, due to language-specific factors or due to initializing and loading software dependencies and frameworks. If your function initializes within a few hundred milliseconds, you are unlikely to see significant performance improvement with SnapStart. For these cases, we recommend using Provisioned Concurrency.

## Conclusion

AWS Lambda SnapStart can deliver sub-second startup performance for Java, .NET, and Python functions with long initialization times. This post explored how Lambda's lifecycle changes with SnapStart and how Lambda efficiently stores and loads snapshots to improve startup performance. SnapStart helps developers build responsive and scalable applications without provisioning resources or implementing complex performance optimizations.

To learn more about SnapStart, refer to the documentation and launch posts for Java, Python and .NET. For performance tuning, refer to SnapStart best practices for your preferred language runtime.