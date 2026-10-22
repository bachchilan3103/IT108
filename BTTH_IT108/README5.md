# BÀI TỔNG HỢP IT101 – POWERSHELL

## PHẦN 1 – CLI VS GUI

### 1. Cấu trúc câu lệnh

`ls -Force C:\Windows\Logs`

- **Command:** `ls` – liệt kê nội dung thư mục.
- **Options/Flags:** `-Force` – hiển thị cả file ẩn.
- **Argument:** `C:\Windows\Logs` – thư mục cần xem.

### 2. Vì sao cần dùng Terminal?

Máy chủ Cloud thường được quản lý từ xa bằng SSH, không có giao diện đồ họa. Terminal giúp quản lý file, cài đặt và chạy chương trình nhanh chóng, đồng thời dễ tự động hóa.

## PHẦN 2 – ĐIỀU HƯỚNG FILE

### 3. Relative Path

`cd .\quan-ly-sinh-vien`

### 4. Absolute Path của main.py

`C:\Users\student\Desktop\quan-ly-sinh-vien\src\main.py`

### 5. Xem thư mục data, kể cả file ẩn

`ls ..\data -Force`

`..` là thư mục cha, `-Force` hiển thị cả mục ẩn.

## PHẦN 3 – THAO TÁC FILE VÀ THƯ MỤC

### 6. Tạo thư mục src và data

`New-Item -Path ".\quan-ly-sinh-vien\src", ".\quan-ly-sinh-vien\data" -ItemType Directory -Force`

### 7. Tạo ba file trong một dòng lệnh

Đứng tại thư mục gốc dự án:

`New-Item -Path ".\src\main.py", ".\src\utils.py", ".\README.md" -ItemType File -Force`

### 8. Đổi tên và sao lưu dự án

Đổi tên:

`Rename-Item ".\quan-ly-sv" "quan-ly-sinh-vien"`

Sao lưu toàn bộ:

`Copy-Item ".\quan-ly-sinh-vien" ".\backup-quan-ly-sinh-vien" -Recurse`

## PHẦN 4 – XỬ LÝ LỖI TERMINAL

### 9. Log lỗi số 2

**Nguyên nhân:** Gõ sai tên thư mục `scr`, tên đúng là `src`.

**Khắc phục:** Gõ `cd .\s` rồi nhấn `Tab` để tự động hoàn thành tên thư mục; dùng `ls` để kiểm tra.

### 10. Log lỗi số 3

**Nguyên nhân:** `Access is denied` – quyền truy cập hoặc thực thi bị từ chối.

**Khắc phục:** Kiểm tra quyền và chính sách bằng `Get-ExecutionPolicy -List`. Nếu file tải từ Internet đã được xác minh an toàn và bị chặn, dùng `Unblock-File .\setup.ps1`. Không tự ý tắt cơ chế bảo mật.

### 11. Log lỗi số 1

**Nguyên nhân:** Thư mục `old-version` có chứa file hoặc thư mục con nên PowerShell yêu cầu xác nhận.

**Lệnh xóa không hỏi xác nhận thông thường:**

`Remove-Item ".\old-version" -Recurse -Force`

`-Recurse` xóa nội dung con, `-Force` xử lý các mục ẩn hoặc chỉ đọc trong phạm vi cho phép.

### 12. Phân tích Log lỗi số 4

| Bước | Câu trả lời |
|---|---|
| (a) Dòng lỗi | `FileNotFoundError: [Errno 2] No such file or directory: 'data/input.csv'` |
| (b) Từ khóa lỗi | `FileNotFoundError` – không tìm thấy file. |
| (c) Kiểm tra | Đang chạy trong `src`, nên đường dẫn `data/input.csv` bị tìm sai vị trí. File thực tế nằm ở thư mục `data` ngang cấp với `src`. |

**Cách sửa:** Trong `main.py`, tạo đường dẫn dựa trên vị trí file:

```python
from pathlib import Path

BASE_DIR = Path(__file__).resolve().parent.parent
DATA_PATH = BASE_DIR / "data" / "input.csv"
```

Sử dụng `DATA_PATH` khi đọc CSV để tránh phụ thuộc vào thư mục đang chạy.

## KẾT LUẬN

PowerShell giúp tạo, di chuyển, sao chép và xóa file bằng lệnh. Khi gặp lỗi, cần đọc thông báo, xác định từ khóa lỗi và kiểm tra vị trí hiện tại cùng đường dẫn để tìm nguyên nhân và sửa chính xác.