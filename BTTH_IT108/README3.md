# BÀI TỔNG HỢP IT101 – QUẢN LÝ HỆ ĐIỀU HÀNH VÀ TỔ CHỨC FILE

## PHẦN 1 – KIẾN TRÚC HỆ ĐIỀU HÀNH

### 1. Chức năng cốt lõi của hệ điều hành

Đây là chức năng **quản lý tiến trình và quản lý tài nguyên** của hệ điều hành. Windows phân chia thời gian CPU, RAM và các tài nguyên khác cho Word, Chrome, VS Code và Portal, giúp các phần mềm hoạt động đồng thời mà hạn chế xung đột. RAM 8GB có thể khiến máy chậm nếu nhiều ứng dụng sử dụng bộ nhớ cùng lúc.

### 2. Phân biệt Shell và Kernel

Khi double-click vào file báo cáo, thao tác ban đầu được thực hiện thông qua **Shell**, cụ thể là giao diện đồ họa Windows File Explorer. Shell tiếp nhận thao tác của người dùng và yêu cầu hệ điều hành mở file bằng ứng dụng phù hợp; Kernel chịu trách nhiệm quản lý tiến trình, bộ nhớ và các hoạt động truy cập tài nguyên cần thiết. Người dùng thường không tương tác trực tiếp với Kernel vì đây là thành phần cốt lõi, có quyền truy cập hệ thống ở mức thấp và cần được bảo vệ để đảm bảo tính ổn định, an toàn.

## PHẦN 2 – CÂY THƯ MỤC VÀ Ổ ĐĨA

### 1. Xác định thành phần trong cây thư mục

- **Root Directory:** `D:\`
- **Parent Directory trực tiếp của `anh 1.jpg`:** `D:\Nam1\HocKy1\MonHoc\CongNgheThongTin\BaiTapLon\Session02\BaoCaoCuoiKy\Chuong1\Hinh anh\`
- **Vai trò của `anh 1.jpg`:** Là lá trong cây thư mục vì đây là file, không phải thư mục chứa các thành phần khác.

### 2. Rủi ro khi lưu dự án trong Desktop hoặc Downloads

Thứ nhất, các thư mục này thuộc User Profile trên ổ `C:\`, nên khi ổ hệ điều hành gặp sự cố hoặc Windows cần cài đặt lại, dữ liệu có nguy cơ bị mất nếu chưa sao lưu. Thứ hai, Desktop và Downloads dễ chứa nhiều file tạm, file tải về và dữ liệu lộn xộn, làm tăng nguy cơ nhầm lẫn hoặc xóa nhầm dự án.

**Đề xuất:** Lưu dự án tại `D:\02_Projects\BaiTapLonIT101\` và thường xuyên sao lưu lên thiết bị hoặc dịch vụ lưu trữ khác.

## PHẦN 3 – ĐƯỜNG DẪN PATH

### 1. Absolute Path của `anh 1.jpg`

Đường dẫn tuyệt đối đầy đủ là:

`D:\Nam1\HocKy1\MonHoc\CongNgheThongTin\BaiTapLon\Session02\BaoCaoCuoiKy\Chuong1\Hinh anh\anh 1.jpg`

Đường dẫn này bắt đầu từ gốc ổ `D:\` và xác định vị trí cụ thể của file trên máy tính.

### 2. Relative Path của `logo.png`

Trong file `report.html`, sử dụng đường dẫn tương đối:

`assets/logo.png`

Có thể viết trong HTML như sau:

`<img src="assets/logo.png" alt="Logo dự án">`

Đường dẫn này được tính từ vị trí của `report.html`. Khi nén toàn bộ thư mục `BaiTapLonIT101` và chuyển sang máy khác, đường dẫn vẫn hoạt động nếu giữ nguyên cấu trúc thư mục và tên file, không phụ thuộc vào ký tự ổ đĩa hay vị trí lưu dự án trên máy ban đầu.

## PHẦN 4 – QUY TẮC ĐẶT TÊN CHUẨN

Tên file ban đầu:

`Báo cáo bài tập lớn IT101 (bản cuối) v2.docx`

Tên file theo quy tắc `kebab-case`:

`bao-cao-bai-tap-lon-it101-ban-cuoi-v2.docx`

Tên mới không dấu, sử dụng chữ thường và dấu gạch ngang để phân tách các từ, giúp dễ đọc và thuận tiện khi quản lý file.

## PHẦN 5 – TỔ CHỨC VÀ DỌN DẸP Ổ ĐĨA

### 1. Đếm cấp thư mục và thiết kế lại đường dẫn

Đường dẫn ban đầu:

`D:\Nam1\HocKy1\MonHoc\CongNgheThongTin\BaiTapLon\Session02\BaoCaoCuoiKy\Chuong1\Hinh anh\anh 1.jpg`

Có **9 cấp thư mục**, không tính tên ổ đĩa và file `anh 1.jpg`. Cấu trúc này vi phạm nguyên tắc tổ chức dự án theo tối đa 3 cấp thư mục đã học, khiến việc tìm kiếm, quản lý và di chuyển dữ liệu khó khăn hơn.

Đường dẫn đề xuất theo mô hình 4 trụ cột và quy tắc 3 cấp:

`D:\01_HocTap\IT101\HinhAnh\anh-1.jpg`

Trong đó:

- **Cấp 1:** `01_HocTap` – trụ cột học tập.
- **Cấp 2:** `IT101` – môn học.
- **Cấp 3:** `HinhAnh` – nhóm nội dung.
- **File:** `anh-1.jpg`.

Cấu trúc mới giúp đường dẫn ngắn gọn, dễ tìm kiếm và thuận tiện khi sao lưu hoặc chuyển dự án sang máy khác.

## PHẦN 6 – ĐUÔI FILE VÀ FILE ẨN

### 1. Phát hiện file có đuôi mở rộng giả mạo

File hiển thị `de-thi-dap-an.pdf` có thể là một file thực thi hoặc file mã độc được đặt tên nhằm đánh lừa người dùng. Do Windows đang ẩn phần mở rộng đã biết, tên thật có khả năng là `de-thi-dap-an.pdf.exe`, khiến người dùng tưởng rằng đây là tài liệu PDF thông thường.

Để kiểm tra, mở **File Explorer → View → Show → File name extensions** trên Windows 11. Sau khi bật tùy chọn này, kiểm tra lại tên file đầy đủ trước khi thao tác. Không mở file đáng ngờ; nên xóa hoặc cách ly file, quét bằng Windows Security và xác minh nguồn gửi trước khi sử dụng.

## KẾT LUẬN

Việc hiểu cách hệ điều hành quản lý tài nguyên, tổ chức cây thư mục, sử dụng đường dẫn phù hợp và đặt tên file chuẩn giúp sinh viên làm việc hiệu quả hơn. Đồng thời, bật hiển thị phần mở rộng và kiểm tra file tải về là những biện pháp cần thiết để hạn chế lỗi kỹ thuật và nguy cơ bảo mật khi nộp bài tập lớn.