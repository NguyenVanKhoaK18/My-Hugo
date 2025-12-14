---
title: "Cơ chế hoạt động AWS Lambda SnapStart"
date: "2025-08-19"
weight: 3
chapter: false
pre: " <b> 3.3. </b> "
---

# Cơ chế hoạt động: cách AWS Lambda SnapStart tối ưu hóa độ trễ khởi động của hàm

*Bởi Ayush Kulkarni và Eric Heinz | ngày 19 tháng 8 năm 2025*

Khi xây dựng ứng dụng bằng AWS Lambda, việc tối ưu hóa khởi động của hàm là một bước quan trọng để cải thiện hiệu suất cho các ứng dụng nhạy cảm về độ trễ. Yếu tố lớn nhất gây ra độ trễ khởi động (thường được gọi là thời gian khởi động nguội hay cold start) là thời gian mà Lambda dùng để khởi tạo mã nguồn của hàm. Lambda SnapStart là một tính năng có sẵn cho các môi trường thực thi Java, Python, và .NET, giúp giảm độ trễ cold start biến thiên từ vài giây (hoặc cao hơn) xuống mức thấp chỉ còn dưới một giây. SnapStart thường không yêu cầu hoặc chỉ cần thay đổi rất ít trong mã nguồn ứng dụng của bạn và giúp việc xây dựng các ứng dụng có khả năng phản hồi nhanh và mở rộng quy mô trở nên dễ dàng hơn mà không cần triển khai các tối ưu hóa hiệu suất phức tạp.

Nếu hàm của bạn đã khởi tạo trong vòng vài trăm mili giây, thì AWS khuyến nghị sử dụng Lambda Provisioned Concurrency để đạt được độ trễ khởi động ở mức hàng chục mili giây.

## Cold-start là gì?

Lambda chạy mã nguồn hàm của bạn trong một môi trường thực thi biệt lập, an toàn, sử dụng công nghệ Firecracker microVM. Khi bạn gọi một hàm Lambda lần đầu tiên, Lambda sẽ tạo một môi trường thực thi mới để hàm đó chạy. Lambda tải xuống mã nguồn hàm của bạn, khởi động môi trường thực thi ngôn ngữ, và chạy mã khởi tạo của hàm (là đoạn mã nằm ngoài handler). Quá trình khởi tạo này (INIT) được gọi là khởi động nguội (cold start). Sau đó, Lambda chạy mã handler của hàm để thực thi lệnh gọi. Hình sau đây cho thấy lifecycle của một yêu cầu gọi hàm thông thường.

![Hình 1. Vòng đời gọi hàm khi không có SnapStart](/images/3-BlogsTranslated/3.3-Blog3/figure1.png)

Sau khi hàm chạy xong, Lambda không dừng môi trường thực thi ngay lập tức. Khi hàm của bạn nhận một yêu cầu gọi khác, Lambda sẽ cố gắng định tuyến yêu cầu đó đến môi trường thực thi đang nhàn rỗi nhưng đã chạy sẵn. Vì quá trình INIT đã được chạy cho môi trường thực thi này, lệnh gọi này được gọi là khởi động nóng (warm start). Khi lưu lượng truy cập đến nhiều hơn số lượng môi trường thực thi nhàn rỗi mà Lambda có sẵn, Lambda sẽ khởi tạo các môi trường thực thi mới để phục vụ các yêu cầu bổ sung, thực hiện lại quá trình khởi tạo cold start.

Bước cuối cùng của cold start, khởi tạo mã nguồn hàm, thường mất nhiều thời gian nhất. Điều này phụ thuộc vào các tác vụ khởi động mà bạn thực thi trong mã nguồn của mình và môi trường thực thi ngôn ngữ hoặc framework bạn sử dụng. Đối với các ngôn ngữ như Java và .NET, độ trễ khởi động bị ảnh hưởng bởi quá trình biên dịch tức thời (just-in-time compilation) của mã tĩnh trong các class được tải. Đối với Python, nó có thể bị ảnh hưởng nếu mã được thực thi của bạn chứa nhiều hoặc các mô-đun lớn. Các tác vụ khởi động khác, chẳng hạn như tải xuống các mô hình học máy (ML models), cũng có thể mất vài giây để hoàn thành, làm tăng thêm độ trễ khởi tạo của hàm. SnapStart được thiết kế để tối ưu hóa bước cuối cùng này của quá trình cold start và thực hiện điều đó qua ba giai đoạn.


## Giai đoạn 1: Tạo snapshot cho hàm Lambda của bạn

Khi sử dụng SnapStart, vòng đời của môi trường thực thi Lambda sẽ thay đổi. Khi bạn bật SnapStart cho một hàm cụ thể, việc xuất bản một phiên bản hàm mới sẽ kích hoạt quá trình tạo snapshot. Quá trình này chạy giai đoạn khởi tạo hàm và tạo một snapshot bất biến, được mã hóa của Firecracker microVM snapshot về trạng thái bộ nhớ và đĩa của môi trường thực thi đã được khởi tạo, sau đó lưu vào bộ đệm và chia nhỏ snapshot đó để tái sử dụng.

Các nhánh mã không được thực thi trong quá trình khởi tạo, chẳng hạn như các class được tải theo yêu cầu thông qua dependency injection, sẽ không được bao gồm trong snapshot của hàm. Để cải thiện hiệu quả của snapshot, hãy chủ động thực thi các nhánh mã trong giai đoạn khởi tạo, hoặc sử dụng các hook của runtime để chạy mã trước khi Lambda tạo snapshot.

Việc tạo snapshot có thể mất vài phút, trong thời gian đó phiên bản hàm của bạn sẽ ở trạng thái PENDING, và chuyển sang ACTIVE khi snapshot sẵn sàng.

Khi bạn gọi hàm của mình sau đó, Lambda sẽ khôi phục các môi trường thực thi mới từ snapshot này. Việc tối ưu hóa này làm cho thời gian gọi hàm nhanh hơn và dễ dự đoán hơn, vì việc tạo một môi trường thực thi mới không còn yêu cầu quá trình khởi tạo nữa.

![Hình 2. Vòng đời gọi hàm khi có SnapStart](/images/3-BlogsTranslated/3.3-Blog3/figure2.png)

## Giai đoạn 2: Lưu trữ snapshot để truy xuất với độ trễ thấp ở quy mô của Lambda

Lambda hoạt động ở quy mô lớn, xử lý hàng chục nghìn tỷ yêu cầu gọi hàm mỗi tháng. Để quản lý và truy xuất các snapshot một cách hiệu quả ở khối lượng truy cập này, Lambda sử dụng các thành phần lưu trữ và bộ đệm. Các thành phần này bao gồm ba lớp: Amazon S3 để lưu trữ bền vững, một bộ đệm phân tán (distributed cache) chuyên dụng, và một bộ đệm cục bộ (local cache) trên các Lambda worker node.

Lambda lưu trữ các snapshot của hàm trong Amazon S3, chia chúng thành các chunk 512 KB để tối ưu hóa độ trễ truy xuất. Độ trễ truy xuất từ Amazon S3 có thể mất đến hàng trăm mili giây cho mỗi chunk 512 KB. Do đó, Lambda sử dụng một bộ đệm hai lớp để tăng tốc độ truy xuất snapshot.

Khi bạn bật SnapStart, trong quá trình tối ưu hóa, Lambda sẽ lưu trữ các chunk của snapshot trong một bộ đệm lớp hai (L2 cache). Lớp này là một cụm các instance bộ đệm phân tán chuyên dụng được Lambda xây dựng riêng. Lambda lưu trữ một bản sao riêng biệt của mỗi snapshot cho mỗi AWS Availability Zone (AZ). Để cân bằng giữa hiệu suất và chi phí, Lambda có thể không chủ động lưu vào bộ đệm các chunk của snapshot không được sử dụng, thay vào đó sẽ lưu chúng sau khi chúng được truy cập lần đầu. Các chunk vẫn được lưu trong cụm L2 miễn là phiên bản hàm của bạn đang hoạt động. Hiệu suất khôi phục snapshot từ lớp L2 thường ở mức mili giây một chữ số cho một chunk 512 KB.

Lambda cũng duy trì một bộ đệm lớp một (L1 cache) đặt trên các Lambda worker node, là các instance  Amazon Elastic Compute Cloud (Amazon EC2) xử lý các lệnh gọi hàm. Lớp này có sẵn cục bộ, do đó nó cung cấp hiệu suất nhanh nhất, thường là 1 mili giây cho một chunk 512 KB. Các hàm có lệnh gọi thường xuyên hơn có nhiều khả năng được lưu các chunk của snapshot trong lớp này. Các hàm có ít lệnh gọi hơn sẽ tự động bị loại bỏ khỏi bộ đệm này, vì nó bị giới hạn bởi dung lượng đĩa của worker instance. Khi một chunk của snapshot không có sẵn trong L1 cache, Lambda sẽ truy xuất chunk đó từ lớp L2 cache.


![Hình 3. Bộ đệm phân tầng của SnapStart](/images/3-BlogsTranslated/3.3-Blog3/figure3.png)

## Giai đoạn 3: Tiếp tục thực thi từ các snapshot đã được khôi phục

Việc tiếp tục thực thi từ các snapshot với độ trễ thấp là giai đoạn cuối cùng của SnapStart. Giai đoạn này bao gồm việc tải các chunk của snapshot đã được truy xuất vào môi trường thực thi hàm của bạn. Thông thường, chỉ một phần nhỏ của snapshot được truy xuất là cần thiết để phục vụ một lệnh gọi.

Việc lưu trữ snapshot dưới dạng các chunk cho phép Lambda tối ưu hóa quá trình tiếp tục bằng cách chủ động tải chỉ phần nhỏ các chunk cần thiết. Để làm được điều này, Lambda theo dõi và ghi lại các chunk của snapshot mà hàm truy cập trong mỗi lần gọi, như được hiển thị trong hình sau.

![Hình 4. Lệnh gọi ban đầu, ghi lại mẫu truy cập chunk](/images/3-BlogsTranslated/3.3-Blog3/figure4.png)

Sau lần gọi hàm đầu tiên, Lambda tham chiếu đến dữ liệu truy cập chunk đã được ghi lại này cho các lệnh gọi tiếp theo, như được hiển thị trong hình sau. Lambda chủ động truy xuất và tải "working set" gồm các chunk này trước khi chúng cần thiết để thực thi. Điều này giúp tăng tốc đáng kể độ trễ cold-start. Nếu mọi lệnh gọi đều thực thi cùng một nhánh mã, thì tất cả các chunk cần thiết sẽ được theo dõi sau lần gọi đầu tiên. Nếu hàm Lambda của bạn bao gồm một phương thức được gọi có điều kiện một lần sau mỗi năm lần cold-start, thì Lambda sẽ thêm các chunk tương ứng đại diện cho phương thức này vào siêu dữ liệu truy cập chunk (chunk access metadata) sau năm lần cold-start đó.

![Hình 5. Lệnh gọi tiếp theo, tải các chunk theo thứ tự truy cập](/images/3-BlogsTranslated/3.3-Blog3/figure5.png)

## Hiểu về hiệu suất của hàm SnapStart

### Hiệu suất hàm cải thiện khi có nhiều lệnh gọi hơn

Các hàm được gọi thường xuyên có nhiều khả năng được lưu snapshot trong bộ đệm lớp L1 (L1 layer), nơi cung cấp độ trễ truy xuất nhanh nhất. Các phần của snapshot ít được truy cập đối với các hàm có lệnh gọi không thường xuyên ít có khả năng hiện diện trong lớp L1, dẫn đến độ trễ truy xuất chậm hơn từ các lớp bộ đệm L2 và S3. Dữ liệu truy cập chunk cho các hàm có nhiều lệnh gọi hơn cũng có nhiều khả năng "hoàn chỉnh" hơn, giúp tăng tốc độ trễ khôi phục snapshot.

### Tải trước các nhánh mã để tối ưu hóa độ trễ khôi phục snapshot

Để tối đa hóa lợi ích của SnapStart, hãy tải trước các phụ thuộc, khởi tạo tài nguyên, và thực hiện các tác vụ tính toán nặng gây ra độ trễ khởi động trong mã khởi tạo của bạn thay vì trong handler của hàm. Các nhánh mã không được thực thi trong giai đoạn INIT của hàm, chẳng hạn như các lớp ứng dụng được tải theo yêu cầu thông qua dependency injection, sẽ không được bao gồm trong snapshot của hàm. Bạn có thể cải thiện hơn nữa hiệu quả của SnapStart bằng cách chủ động thực thi các nhánh mã này trong quá trình khởi tạo hàm. Bạn cũng có thể chạy mã bằng cách sử dụng các hook của runtime và gọi handler của bạn trong giai đoạn khởi tạo trước khi tạo snapshot. Để làm điều này, hãy tham khảo tài liệu và các bài viết cho ứng dụng Spring Boot và .NET để triển khai việc tinh chỉnh hiệu suất.


### Hiệu suất khác nhau tùy thuộc vào kích thước hàm

Hiệu suất của SnapStart phụ thuộc vào tốc độ Lambda có thể truy xuất và tải các snapshot đã được lưu vào bộ đệm vào môi trường thực thi hàm của bạn. Kích thước hàm lớn hơn làm tăng kích thước của snapshot, và do đó tăng số lượng chunk, điều này khiến hiệu suất khác nhau đối với các hàm có kích thước khác nhau.

### Không phải tất cả các hàm đều được hưởng lợi từ SnapStart

SnapStart được thiết kế để cải thiện độ trễ khởi động khi quá trình khởi tạo hàm mất vài giây, do các yếu tố đặc thù của ngôn ngữ hoặc do việc khởi tạo và tải các phụ thuộc phần mềm và framework. Nếu hàm của bạn khởi tạo trong vòng vài trăm mili giây, bạn khó có thể thấy được sự cải thiện hiệu suất đáng kể với SnapStart. Đối với những trường hợp này, chúng tôi khuyến nghị sử dụng Provisioned Concurrency, một tính năng khởi tạo trước các môi trường thực thi, mang lại độ trễ ở mức hàng chục mili giây.


## Kết luận

AWS Lambda SnapStart có thể mang lại hiệu suất khởi động thấp chỉ còn dưới một giây cho các hàm Java, .NET, và Python có thời gian khởi tạo dài. Bài viết này khám phá cách vòng đời của Lambda thay đổi với SnapStart và cách Lambda lưu trữ và tải các snapshot một cách hiệu quả để cải thiện hiệu suất khởi động. SnapStart giúp các nhà phát triển xây dựng các ứng dụng có khả năng phản hồi cao và mở rộng quy mô mà không cần cấp phát tài nguyên hoặc triển khai các tối ưu hóa hiệu suất phức tạp.

Để tìm hiểu thêm về SnapStart, hãy tham khảo tài liệu và các bài đăng ra mắt cho Java, và  Python and .NET. Để tinh chỉnh hiệu suất, hãy tham khảo  SnapStart best practices cho môi trường thực thi ngôn ngữ bạn ưa thích. Bài viết này phác thảo các phương pháp để tải trước các nhánh mã nhằm tối ưu hóa hơn nữa độ trễ khởi động. Tìm thêm thông tin và các ứng dụng mẫu được xây dựng bằng SnapStart trên Serverlessland.com.




