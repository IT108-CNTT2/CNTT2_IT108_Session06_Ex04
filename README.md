## Phần 1: Bảng so sánh toán tử và lệnh PowerShell

| Tiêu chí | Toán tử ghi đè (\>)Lệnh tương đương: Out-File | Toán tử ghi nối (\>\>)Lệnh tương đương: Add-Content |
| :---- | :---- | :---- |
| Cơ chế hoạt động | Ghi đè (Overwrite): Xóa toàn bộ nội dung cũ của file (nếu đã tồn tại) và ghi đè nội dung mới hoàn toàn từ đầu. Nếu file chưa có, sẽ tự động tạo file mới. | Ghi nối tiếp (Append): Giữ nguyên nội dung cũ và bổ sung nội dung mới vào dòng cuối cùng của file. Nếu file chưa có, sẽ tự động tạo mới. |
| Rủi ro mất dữ liệu | Cực kỳ cao. Toàn bộ lịch sử ghi chép trước đó sẽ bốc hơi vĩnh viễn ngay khi lệnh được thực thi nếu file đã tồn tại. | Thấp. An toàn tuyệt đối cho dữ liệu cũ, không làm thay đổi hay xóa dữ liệu đã ghi trước đó. |
| Ngữ cảnh sử dụng | Phù hợp cho việc tạo báo cáo mới (ví dụ: báo cáo tổng kết ca sáng, khởi tạo file log mới mỗi khi reset hệ thống). | Phù hợp cho việc theo dõi liên tục 24/7, ghi nhật ký hệ thống, kiểm toán lỗi (*Audit Log*) diễn ra theo thời gian thực. |

## Phần 2: Cảnh báo — Tại sao nhầm \> thành \>\> là "thảm họa" trong ngân hàng?

Trong môi trường vận hành hạ tầng ngân hàng và tài chính, nhật ký hệ thống (history.log, audit.log, transaction\_log) không chỉ để đọc lúc lỗi mà còn là chứng cứ pháp lý và tuân thủ (Compliance) để truy vết mọi thay đổi, sự cố hoặc thao tác bảo trì.

Việc gõ nhầm \> thay vì \>\> trong một Script tự động chạy ngầm sẽ dẫn đến hậu quả nghiêm trọng:

1. Xóa trắng toàn bộ lịch sử: Toàn bộ nhật ký bảo trì từ các ca trước, các mốc thời gian chẩn đoán lỗi quan trọng bị xóa sạch trong một tích tắc.  
2. Mất dấu vết điều tra sự cố: Khi hệ thống gặp sự cố lớn vào ngày mai, đội ngũ kỹ sư hoặc cơ quan kiểm tra nội bộ sẽ không còn dữ liệu quá khứ để đối chiếu nguyên nhân gốc (*Root Cause Analysis*), gây gián đoạn quy trình xử lý khủng hoảng.  
3. Vi phạm quy chuẩn vận hành: Làm mất mát dữ liệu kiểm toán hệ thống lõi (*Core Banking / System Infrastructure*), có thể dẫn đến hậu quả pháp lý hoặc bị phạt vi phạm quy định an toàn thông tin.

"# CNTT2_IT108_Session06_Ex04" 
