---
title: "Clean up"
date: "2025-09-09"
weight: 4
chapter: false
pre: " <b> 5.5.4. </b> "
---

#### Clean Up Resources

Congratulations on completing the DynamoDB Basic Operations workshop!

In this workshop, you learned how to:
- ✅ Create a DynamoDB table
- ✅ Add data to the table
- ✅ Query data by partition key
- ✅ Scan and filter table data

## Clean Up Steps

To avoid ongoing charges, delete the DynamoDB table:

### Delete DynamoDB Table

1. Navigate to **DynamoDB** console
2. Select your **TaskManagement** table
3. Click **Delete**

![Delete Table](/images/5-Workshop/5.5-DynamoDB/delete-table.png)

4. Type **delete** to confirm
5. Click **Delete table**

![Confirm Delete](/images/5-Workshop/5.5-DynamoDB/confirm-delete.png)

### Verify Cleanup

Ensure the table is deleted from the DynamoDB console:

![Cleanup Verified](/images/5-Workshop/5.5-DynamoDB/cleanup-verified.png)

## Cost Summary

This workshop used:
- **DynamoDB On-Demand**: Pay per request
- **No ongoing charges** after table deletion

## Next Steps

Now that you understand DynamoDB basics, consider:

### Advanced Features
- Global Secondary Indexes (GSI)
- DynamoDB Streams
- Auto Scaling
- Backup and Point-in-time Recovery

### Integration
- Use with AWS Lambda for serverless applications
- Integrate with API Gateway for REST APIs
- Connect with AWS AppSync for GraphQL APIs

### Best Practices
- Design efficient partition keys
- Use composite sort keys for complex queries
- Implement proper error handling
- Monitor performance with CloudWatch

## Resources

- [DynamoDB Developer Guide](https://docs.aws.amazon.com/dynamodb/)
- [DynamoDB Best Practices](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/best-practices.html)
- [NoSQL Design Patterns](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/bp-general-nosql-design.html)

Thank you for completing this workshop! 🎉