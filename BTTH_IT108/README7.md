# BÀI TỔNG HỢP IT101 – XỬ LÝ LOG BẰNG POWERSHELL

## PHẦN 1 – ĐỌC VÀ ĐỊNH VỊ TỆP TIN

### 1. Đọc toàn bộ file log

powershell
Get-Content .\logs\server.log

### 2. Vì sao file 500 MB có thể làm Notepad treo?

Notepad có thể phải nạp và xử lý lượng lớn nội dung trong RAM, khiến máy thiếu bộ nhớ và phản hồi chậm. PowerShell có thể đọc log theo từng dòng hoặc theo luồng xử lý, giảm nhu cầu nạp toàn bộ file vào RAM.

### 3. Tìm tất cả file `.log` trong project

powershell
Get-ChildItem -Path . -Filter *.log -Recurse -File


## PHẦN 2 – LỌC DỮ LIỆU VÀ PIPE

### 4. Lọc các dòng chứa `ERROR`

powershell
Get-Content .\logs\server.log | Select-String "ERROR"

### 5. Phân biệt tìm file và tìm nội dung

| Câu hỏi | Lệnh PowerShell |
|---|---|
| File `server.log` nằm ở đâu? | `Get-ChildItem -Path . -Filter server.log -Recurse -File` |
| File có dòng chứa lỗi 404 không? | `Select-String -Path .\logs\server.log -Pattern "404"` |

Kết hợp Pipe để đọc file rồi lọc `404`:

powershell
Get-Content .\logs\server.log | Select-String "404"


### 6. Tìm file `.log` và lọc dòng không chứa `INFO`

powershell
Get-ChildItem -Path . -Filter *.log -Recurse -File | Select-String -NotMatch "INFO"

## PHẦN 3 – TOÁN TỬ `>` VÀ `>>`

### 7. Lọc 404 và ghi đè báo cáo

powershell
Get-Content .\logs\server.log | Select-String "404" > .\reports\daily_report.txt

### 8. Thêm lỗi mới vào cuối báo cáo

powershell
Get-Content .\logs\server.log | Select-String "404" | Select-Object -Last 1 >> .\reports\daily_report.txt

`>>` ghi nối vào cuối file, giữ nội dung cũ. Nếu dùng `>` thì báo cáo cũ sẽ bị ghi đè.

## PHẦN 4 – SHELL SCRIPT VÀ WRITE-OUTPUT

### 9. In thông báo và ghi tiêu đề báo cáo

In thông báo:

powershell
Write-Output "Dang loc log..."

Ghi tiêu đề làm dòng đầu tiên:

powershell
"=== LOG REPORT ===" > .\reports\daily_report.txt

### 10. Nội dung file `scripts\auto_report.ps1`

powershell
Write-Output "Dang loc log..."

"=== LOG REPORT ===" > .\reports\daily_report.txt
Get-Content .\logs\server.log | Select-String "404" >> .\reports\daily_report.txt

Script đọc log, lọc dòng chứa `404` và ghi kết quả vào báo cáo sau dòng tiêu đề.

## PHẦN 5 – CHẠY VÀ THẨM ĐỊNH SCRIPT AI

### 11. Quy trình chạy và kiểm tra

**Bước 1 – Viết:** Lưu nội dung vào `scripts\auto_report.ps1`.

**Bước 2 – Chạy:** Tại thư mục gốc `devops-lab`, thực hiện:

powershell
.\scripts\auto_report.ps1

**Bước 3 – Kiểm tra:** Xem nội dung báo cáo:

powershell
Get-Content .\reports\daily_report.txt

### 12. Thẩm định script AI

**a. Dòng lệnh nguy hiểm:**

powershell
Remove-Item -Recurse -Force C:\*

Lệnh này có thể xóa hàng loạt file và thư mục trên ổ `C:\`, gây mất dữ liệu hoặc làm Windows không hoạt động.

**b. Sửa để chỉ tác động vào thư mục tạm của project:**

powershell
$tempPath = "C:\Users\student\Desktop\devops-lab\temp"
if (Test-Path $tempPath) {
    Remove-Item -Path "$tempPath\*" -Recurse -Force
}


Lệnh chỉ xóa nội dung bên trong thư mục `temp` nếu thư mục tồn tại. Cần kiểm tra chính xác đường dẫn trước khi chạy.

**Ba nguyên tắc vàng khi kiểm tra script AI:**
1. **Đọc kỹ:** Xác định các lệnh xóa, ghi đè hoặc thay đổi hệ thống.
2. **Kiểm tra phạm vi:** Xác nhận đường dẫn và đối tượng bị tác động.
3. **Thử an toàn:** Kiểm tra đường dẫn, dùng dữ liệu thử hoặc chế độ mô phỏng trước khi chạy thật.

## KẾT LUẬN

PowerShell hỗ trợ tìm file, lọc log bằng `Select-String`, kết hợp lệnh qua Pipe và xuất báo cáo bằng `>` hoặc `>>`. Trước khi chạy script do AI tạo, cần kiểm tra lệnh nguy hiểm và phạm vi tác động để tránh mất dữ liệu.