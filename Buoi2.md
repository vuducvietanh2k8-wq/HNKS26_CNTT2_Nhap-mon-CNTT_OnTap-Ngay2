# HƯỚNG DẪN GITHUB – BÀI LUYỆN TẬP NGÀY 2

## Môn: Nhập môn Công nghệ thông tin

## 1. Chuẩn bị thư mục bài làm

Sau khi tải và giải nén `starter-kit.zip`, cấu trúc thư mục ban đầu như sau:

```text
starter-kit/
├── bai_lam_ngay2.md
└── trung-tam-tieng-anh/
    ├── .env
    ├── archive/
    ├── data/
    ├── docs/
    ├── media/
    └── logs/
        ├── access.log
        └── payment.log
```

### Mở PowerShell tại thư mục dự án

1. Mở File Explorer và đi vào thư mục `trung-tam-tieng-anh`.
2. Nhấp vào thanh địa chỉ, nhập `powershell` rồi nhấn Enter.
3. Kiểm tra thư mục hiện tại:

```powershell
Get-Location
```

Liệt kê các file và thư mục, bao gồm cả file ẩn:

```powershell
Get-ChildItem -Force
```

**Lưu ý:** Chỉ kiểm tra sự tồn tại của `.env`, không mở nội dung và không tải file này lên GitHub.

## 2. Sao chép file bài làm vào đúng vị trí

Nếu PowerShell đang ở thư mục `starter-kit`, chạy:

```powershell
Copy-Item .\bai_lam_ngay2.md .\trung-tam-tieng-anh\
```

Sau đó chuyển vào thư mục dự án:

```powershell
Set-Location .\trung-tam-tieng-anh
```

Kiểm tra file bài làm:

```powershell
Test-Path .\bai_lam_ngay2.md
```

Nếu kết quả là `True`, file tồn tại ở vị trí hiện tại.

Nếu đã mở PowerShell trong thư mục `trung-tam-tieng-anh`, không cần sao chép lại file.

## 3. Tạo repository trên GitHub

### Bước 1. Đăng nhập GitHub

Truy cập [GitHub](https://github.com/) và đăng nhập tài khoản cá nhân.

### Bước 2. Tạo repository mới

Mở [Create a new repository](https://github.com/new).

Điền các thông tin:

* **Owner:** Tài khoản GitHub cá nhân.
* **Repository name:** `[Tên Lớp]_Nhap-mon-CNTT_OnTap-Ngay2`.
* **Description:** `Bài luyện tập Ngày 2 - Nhập môn CNTT`.
* **Visibility:** Chọn theo yêu cầu của giảng viên.
* **Add a README file:** Không chọn nếu chuẩn bị đẩy thư mục dự án hiện có lên Git và muốn tránh xung đột ban đầu.

Ví dụ tên repository:

```text
HN-KS26-CNTT1_Nhap-mon-CNTT_OnTap-Ngay2
```

Nhấn **Create repository** để hoàn tất.

## 4. Đưa bài làm lên GitHub bằng PowerShell

### Bước 1. Kiểm tra Git

```powershell
git --version
```

Nếu Git đã được cài đặt, lệnh sẽ hiển thị phiên bản.

Nếu PowerShell không nhận diện được lệnh, cài đặt [Git for Windows](https://git-scm.com/download/win), sau đó mở lại PowerShell.

### Bước 2. Khởi tạo Git

Tại thư mục `trung-tam-tieng-anh`, chạy:

```powershell
git init
```

Kiểm tra trạng thái:

```powershell
git status
```

### Bước 3. Bảo vệ file `.env`

Tạo file `.gitignore`:

```powershell
New-Item -ItemType File -Path .gitignore -Force
```

Mở file bằng Notepad:

```powershell
notepad .gitignore
```

Thêm nội dung:

```gitignore
.env
```

Lưu file rồi kiểm tra quy tắc bỏ qua:

```powershell
git check-ignore -v .env
```

Nếu lệnh hiển thị quy tắc trong `.gitignore`, file `.env` đang được bỏ qua theo quy tắc đó.

**Quan trọng:** Nếu `.env` đã được Git theo dõi trước khi tạo `.gitignore`, quy tắc này không tự động gỡ file khỏi vùng theo dõi. Phải kiểm tra trạng thái Git trước khi commit và bảo đảm `.env` không bị đưa lên GitHub.

### Bước 4. Thêm các file cần nộp

```powershell
git add .
```

Kiểm tra các file chuẩn bị commit:

```powershell
git status
```

Chỉ tiếp tục khi đã xác nhận không có `.env` hoặc dữ liệu bí mật trong danh sách file được thêm.

### Bước 5. Commit bài làm

```powershell
git commit -m "Hoan thanh bai luyen tap Ngay 2"
```

Nếu Git yêu cầu cấu hình danh tính, thay các giá trị mẫu bằng tên và email phù hợp:

```powershell
git config --global user.name "Ten Cua Ban"
git config --global user.email "EmailCuaBan"
```

Sau đó chạy lại lệnh commit.

### Bước 6. Kết nối với repository GitHub

Sao chép URL HTTPS từ repository vừa tạo. Thay URL mẫu dưới đây bằng URL thực tế của bạn:

```powershell
git remote add origin https://github.com/TEN_TAI_KHOAN/TEN_REPOSITORY.git
```

Kiểm tra địa chỉ remote:

```powershell
git remote -v
```

Đặt tên nhánh chính là `main`:

```powershell
git branch -M main
```

Đẩy bài làm lên GitHub:

```powershell
git push -u origin main
```

Nếu GitHub yêu cầu xác thực, hãy làm theo hướng dẫn đăng nhập của Git hoặc trình duyệt.

## 5. Kiểm tra và nộp bài

Sau khi lệnh `git push` hoàn tất, mở repository trên GitHub và kiểm tra:

* [ ] Tên repository đúng cú pháp yêu cầu.
* [ ] Có file `bai_lam_ngay2.md` ở thư mục gốc.
* [ ] Có hai file log ban đầu trong `logs/`.
* [ ] Có các file báo cáo và script đã tạo trong quá trình thực hành.
* [ ] File `.env` không xuất hiện trên GitHub.
* [ ] Không có thông tin bí mật hoặc dữ liệu cá nhân không cần thiết.
* [ ] File bài làm đã ghi lệnh, kết quả và phần tự chấm theo yêu cầu.

### Link repository

Ví dụ định dạng URL:

```text
https://github.com/TEN_TAI_KHOAN/HN-KS26-CNTT1_Nhap-mon-CNTT_OnTap-Ngay2
```

Thay bằng URL repository thực tế của bạn, sau đó dán vào sheet nộp bài do giảng viên quản lý trước **23:00 ngày 21/10/2026**.

## 6. Cập nhật bài làm sau khi chỉnh sửa

Nếu sửa file Markdown hoặc tạo thêm báo cáo, kiểm tra trạng thái:

```powershell
git status
```

Sau khi xác nhận không có file bí mật, chạy:

```powershell
git add .
git commit -m "Cap nhat bai lam Ngay 2"
git push
```

## 7. Ghi nhớ các lệnh Git quan trọng

| Lệnh                      | Chức năng                            |
| ------------------------- | ------------------------------------ |
| `git --version`           | Kiểm tra phiên bản Git               |
| `git init`                | Khởi tạo kho Git cục bộ              |
| `git status`              | Kiểm tra trạng thái file             |
| `git add .`               | Đưa các thay đổi phù hợp vào staging |
| `git commit -m "..."`     | Lưu bản ghi thay đổi                 |
| `git remote -v`           | Kiểm tra địa chỉ repository từ xa    |
| `git branch -M main`      | Đổi tên nhánh hiện tại thành `main`  |
| `git push -u origin main` | Đẩy nhánh `main` lên GitHub lần đầu  |
| `git push`                | Đẩy các commit mới lên repository    |

**Kết luận:** Thực hiện đúng quy trình giúp quản lý bài làm bằng Git, đưa tài liệu lên GitHub và tránh tải nhầm file `.env` chứa dữ liệu bí mật.
