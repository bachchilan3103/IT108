# BÀI TỔNG HỢP SESSION 10 – BỘ CÔNG CỤ VĂN PHÒNG CHO DEVELOPER

## PHẦN 1 – HOÀN THIỆN SRS BẰNG WORD

### 1.1. Khung tiêu đề SRS và Heading Styles

- **Heading 1:** 1. Giới thiệu dự án
  - **Heading 2:** 1.1. Mục tiêu
  - **Heading 2:** 1.2. Đối tượng sử dụng
- **Heading 1:** 2. Chức năng hệ thống
  - **Heading 2:** 2.1. Quản lý mượn sách
    - **Heading 3:** 2.1.1. Luồng mượn sách qua thẻ sinh viên
  - **Heading 2:** 2.2. Quản lý trả sách
- **Heading 1:** 3. Yêu cầu bảo mật

### 1.2. Mô tả yêu cầu chức năng

Hệ thống cho phép sinh viên tra cứu sách và tạo phiếu mượn bằng thẻ sinh viên. Thủ thư có thể ghi nhận việc mượn, trả sách và theo dõi tình trạng phiếu mượn.

### 1.3. Mô tả yêu cầu phi chức năng

Hệ thống phải yêu cầu đăng nhập và phân quyền để bảo vệ dữ liệu người dùng. Thông tin cá nhân và lịch sử mượn sách phải được lưu trữ an toàn, chỉ người có quyền mới được truy cập.

### 1.4. Tạo Auto TOC

1. Gán Heading 1, Heading 2 và Heading 3 cho các tiêu đề.
2. Chọn **References → Table of Contents → Automatic Table**.
3. Thêm nội dung hoặc ngắt trang để mục 3 chuyển sang trang sau.
4. Nhấp phải vào mục lục, chọn **Update Field → Update entire table**.
5. Kiểm tra số trang và chụp ảnh kết quả trong Word.

## PHẦN 2 – CHUẨN HÓA DỮ LIỆU VÀ AUTOFILTER

### 2.1. Ba lỗi vi phạm 5 Quy tắc Vàng

| Lỗi | Vị trí | Quy tắc vi phạm |
|---|---|---|
| Gộp ô tiêu đề | Hàng 1 | Không merge ô trong vùng dữ liệu |
| Hàng trống hoàn toàn | Hàng 5 | Không để hàng trống giữa các bản ghi |
| Dòng tổng cộng nằm trong bảng | Hàng 6 | Không đặt dòng tổng kết trong vùng dữ liệu |

### 2.2. Bảng dữ liệu sau khi sửa

| MSSV | Họ Tên | Mã Sách | Ngày Mượn | Tình Trạng |
|---|---|---|---|---|
| SV001 | Nguyễn Văn An | S001 | 01/10/2026 | Đang mượn |
| SV002 | Trần Thị Bình | S002 | 03/10/2026 | Quá hạn |
| SV003 | Lê Văn Cường | S003 | 10/10/2026 | Đã trả |
| SV004 | Phạm Thu Hà | S099 | 12/10/2026 | Đang mượn |

Tổng cộng: 4 phiếu. Dòng tổng cộng được đặt ngoài vùng dữ liệu.

### 2.3. Record và Field

- **Record:** Một hàng dữ liệu của một sinh viên, ví dụ SV001 – Nguyễn Văn An.
- **Field:** Một cột thông tin, ví dụ Mã Sách hoặc Tình Trạng.

### 2.4. Bật AutoFilter

1. Chọn một ô trong bảng.
2. Nhấn `Ctrl + Shift + L`.
3. Nhấn mũi tên lọc tại cột Tình Trạng.
4. Chỉ chọn **Quá hạn** và nhấn OK.

Kết quả: SV002 – Trần Thị Bình.

## PHẦN 3 – NỐI DỮ LIỆU BẰNG VLOOKUP

### 3.1. Công thức tra cứu tên sách

Giả sử cột Mã Sách là C, cột Tên Sách là F và dữ liệu danh mục nằm trong `DanhMucSach!A2:C4`.

excel
=VLOOKUP(C2,DanhMucSach!$A$2:$C$4,2,FALSE)


- `C2`: Mã sách cần tra cứu.
- `DanhMucSach!$A$2:$C$4`: Vùng tra cứu được cố định bằng `$`.
- `2`: Lấy Tên Sách ở cột thứ hai.
- `FALSE`: Tìm kiếm chính xác.

### 3.2. Xử lý mã sách không tồn tại

Mã `S099` trả về lỗi `#N/A` vì không có trong danh mục sách.

Dùng `IFERROR` để thay lỗi bằng thông báo dễ hiểu:

excel
=IFERROR(VLOOKUP(C2,DanhMucSach!$A$2:$C$4,2,FALSE),"Không tìm thấy sách")

## PHẦN 4 – SLIDE BÁO CÁO TIẾN ĐỘ

### 4.1. Nội dung slide

**Tiêu đề kết luận:** 4 phiếu mượn đã được chuẩn hóa, nhưng còn 1 mã sách không hợp lệ.

- Tổng số phiếu: **4**
- Đang mượn: **2 phiếu**
- Quá hạn: **1 phiếu**
- Đã trả: **1 phiếu**
- Mã sách không tồn tại: **S099**

**Biểu đồ lựa chọn:** Bar Chart (biểu đồ cột), vì dễ so sánh số lượng phiếu giữa các tình trạng.

### 4.2. Áp dụng Rule 10/20/30

- **10 slide:** Slide này chiếm 1/10 tổng bài trình bày.
- **20 phút:** Dự kiến trình bày slide trong khoảng 2 phút.
- **30 pt:** Sử dụng cỡ chữ khoảng 30 pt cho nội dung chính để dễ đọc.