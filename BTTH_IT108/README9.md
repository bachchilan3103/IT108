# SmartCampus

SmartCampus là **ứng dụng di động** hỗ trợ sinh viên PTIT tra cứu lịch học, phòng trống và nhận *thông báo mới nhất* từ nhà trường.

## Tính năng chính

- Tra cứu lịch học theo mã sinh viên.
  - Giúp sinh viên kiểm tra lịch học nhanh chóng.
- Xem danh sách phòng trống theo tòa nhà.

Tham khảo [trang chủ CLB Lập trình](https://clblaptrinh.ptit.edu.vn).

![Logo SmartCampus](https://placehold.co/200x100?text=SmartCampus)

> Lưu ý: Dự án đang trong giai đoạn phát triển, chưa dùng cho mục đích chính thức.

---

## Cài đặt

```bash
git clone https://github.com/clb-lap-trinh/smartcampus.git
npm install
npm start
```

## Trạng thái phát triển

- [x] Tra cứu lịch học theo mã sinh viên
- [x] Xem danh sách phòng trống theo tòa nhà
- [ ] Thông báo đẩy (push notification)
- [ ] Đăng nhập bằng tài khoản trường

## Thư viện sử dụng

| Thư viện | Phiên bản | Mục đích |
|:---|:---:|:---|
| React Native | 0.74 | Xây giao diện đa nền tảng iOS/Android |
| Axios | 1.6 | Gọi API lấy dữ liệu lịch học |

Ký hiệu `*` dùng để đánh dấu cú pháp nhấn mạnh trong Markdown.

## Hướng phát triển

SmartCampus tiếp tục hoàn thiện các tính năng đang phát triển để hỗ trợ sinh viên thuận tiện hơn.
PHẦN 3 – HỎI AI VÀ LƯU TÀI LIỆU
1. Prompt theo công thức 3 phần
## Tôi là ai / Bối cảnh

Tôi là sinh viên K26 PTIT, đang tham gia dự án SmartCampus và chưa hiểu rõ thuật ngữ API.

## Chủ đề / Nội dung cần xử lý

Hãy giải thích API (Application Programming Interface) trong phát triển ứng dụng di động.

## Yêu cầu

- Giải thích API bằng ngôn ngữ đơn giản, dễ hiểu.
- Nêu vai trò của API trong ứng dụng SmartCampus.
- Đưa ra một ví dụ thực tế dễ hình dung.
- Trình bày ngắn gọn, có tiêu đề và gạch đầu dòng.

## Không cần

Không trình bày kiến thức lập trình nâng cao hoặc ví dụ code phức tạp.
2. Câu trả lời AI mẫu về API
- API là giao diện cho phép các phần mềm giao tiếp và trao đổi dữ liệu với nhau.
- Trong SmartCampus, ứng dụng có thể gọi API để lấy lịch học từ máy chủ.
- Ví dụ: ứng dụng gửi yêu cầu lấy lịch học theo mã sinh viên và nhận dữ liệu để hiển thị lên màn hình.
3. Tóm tắt theo chiến lược đọc 3 bước
API là cầu nối giúp ứng dụng giao tiếp với máy chủ hoặc phần mềm khác. SmartCampus có thể sử dụng API để lấy dữ liệu lịch học và hiển thị cho sinh viên. Nhờ đó, ứng dụng không cần tự lưu toàn bộ dữ liệu lịch học trên điện thoại.
4. Quy trình 4 bước lưu tài liệu
1. Sao chép prompt và gửi cho AI.
2. Đọc, kiểm tra và chỉnh sửa câu trả lời.
3. Sao chép câu trả lời vào StackEdit.
4. Lưu thành file api_giai_thich.md.
PHẦN 4 – BẪY CÚ PHÁP
1. Hai lỗi cú pháp
- Lỗi 1: Bảng thiếu dòng phân cách giữa tiêu đề và dữ liệu.
- Lỗi 2: Task list thiếu khoảng trắng sau dấu -, cần viết - [x] và - [ ].
2. Đoạn Markdown đã sửa
| Tính năng | Trạng thái |
|---|---|
| Tra cứu lịch học | Xong |
| Push notification | Đang làm |

- [x] Tra cứu lịch học
- [ ] Push notification