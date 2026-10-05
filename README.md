# Báo Cáo Thực Hành: Khởi Tạo Local Repository Và Cấu Hình Danh Tính Git

- **Bài tập**: Bài 1 - Khởi tạo Local Repository và Cấu hình danh tính (Session 04 / Git Version Control)
- **Đường dẫn nộp bài**: `SS04/Bai01/README.md`
- **GitHub Remote Repository**: `https://github.com/DevOpsPTIT/SS04_Bai01.git`
- **Phạm vi cấu hình**: Cấp độ cục bộ (`--local`)

---

## 1. Bối cảnh & Mục tiêu

### Bối cảnh
Khi bắt đầu một dự án phần mềm mới, kỹ sư DevOps cần tạo một môi trường quản lý mã nguồn độc lập bằng Git tại máy cục bộ (Local Repository). Việc cấu hình đúng danh tính tác giả (Name & Email) cho từng repository riêng biệt giúp đảm bảo tính minh bạch, theo vết lịch sử chính xác và tránh bị đè hoặc lẫn lộn với cấu hình Git toàn cục (`--global`) của các dự án khác trên cùng máy tính.

### Mục tiêu
- Khởi tạo thành công một Git repository trống tại thư mục làm việc cục bộ `SS04/Bai01`.
- Thiết lập thông tin danh tính tác giả (`user.name` và `user.email`) ở cấp độ cục bộ (`--local`).
- Tạo tệp tin nguồn mới (`index.html`), đưa vào vùng chuẩn bị (Staging Area) và tiến hành commit đầu tiên.
- Khai báo liên kết với Remote Repository tại GitHub (`https://github.com/DevOpsPTIT/SS04_Bai01.git`).
- Phân tích và kiểm tra trạng thái thư mục làm việc cùng lịch sử commit thông qua các lệnh `git log --oneline` và `git config --local --list`.

---

## 2. Thông Số Cấu Hình & Ràng Buộc

| Thông số / Cấu hình | Giá trị thiết lập | Ràng buộc / Ghi chú |
| :--- | :--- | :--- |
| **Thư mục làm việc** | `SS04/Bai01` | Môi trường repository cục bộ |
| **Cấu hình Tên (`user.name`)** | `DevOps Student` | Bắt buộc sử dụng tùy chọn `--local` |
| **Cấu hình Email (`user.email`)** | `devops.student@example.com` | Bắt buộc sử dụng tùy chọn `--local` |
| **Tệp tin ban đầu** | `index.html` | Đã đưa vào Staging Area và commit |
| **Commit đầu tiên** | `e0b334c` | Thông điệp: `Initial commit: Khoi tao local repository va cau hinh danh tinh` |
| **Remote Origin** | `https://github.com/DevOpsPTIT/SS04_Bai01.git` | Liên kết kho lưu trữ trên GitHub |

---

## 3. Các Bước Thực Hiện Chi Tiết

### Bước 1: Khởi tạo Git Local Repository

Di chuyển vào thư mục bài tập `SS04/Bai01` và tiến hành khởi tạo kho lưu trữ Git cục bộ:

```bash
cd SS04/Bai01
git init
```

*Kết quả*: Hệ thống khởi tạo thư mục ẩn `.git` chứa toàn bộ dữ liệu quản lý phiên bản.

---

### Bước 2: Cấu hình danh tính tác giả ở cấp độ cục bộ (`--local`)

Thiết lập tên và email tác giả chỉ áp dụng riêng cho kho lưu trữ này:

```bash
# 1. Cấu hình tên tác giả cục bộ
git config --local user.name "DevOps Student"

# 2. Cấu hình email tác giả cục bộ
git config --local user.email "devops.student@example.com"
```

> **Lưu ý quan trọng**: Không dùng cờ `--global` để tránh ghi đè cấu hình cá nhân toàn hệ thống của máy tính.

---

### Bước 3: Tạo tệp tin nguồn, đưa vào Staging Area và commit

Tạo tệp `index.html` làm sản phẩm mã nguồn ban đầu của dự án, sau đó thực hiện add và commit:

```bash
# 1. Đưa tệp tin vào vùng chuẩn bị (Staging Area)
git add index.html

# 2. Tạo commit đầu tiên kèm thông điệp rõ nghĩa
git commit -m "Initial commit: Khoi tao local repository va cau hinh danh tinh"
```

---

### Bước 4: Liên kết kho lưu trữ từ xa (Remote Repository)

Thêm địa chỉ repository trên GitHub làm remote origin cho dự án:

```bash
git remote add origin https://github.com/DevOpsPTIT/SS04_Bai01.git
```

---

## 4. Trích Xuất Log Terminal Chứng Minh (Verification Logs)

### 1. Kiểm tra cấu hình danh tính cục bộ

Chạy các lệnh kiểm tra cấu hình `user.email`, `user.name` và danh sách cấu hình local:

```console
$ git config --local user.email
devops.student@example.com

$ git config --local user.name
DevOps Student

$ git config --local --list
core.repositoryformatversion=0
core.filemode=false
core.bare=false
core.logallrefupdates=true
core.symlinks=false
core.ignorecase=true
user.name=DevOps Student
user.email=devops.student@example.com
```

---

### 2. Kiểm tra liên kết Remote Repository

```console
$ git remote -v
origin  https://github.com/DevOpsPTIT/SS04_Bai01.git (fetch)
origin  https://github.com/DevOpsPTIT/SS04_Bai01.git (push)
```

---

### 3. Xem lịch sử commit (`git log` & `git log --oneline`)

```console
$ git log
commit e0b334c4c425e59e1471d466d96a12c19a9a6140
Author: DevOps Student <devops.student@example.com>
Date:   Mon Oct 5 22:54:59 2026 +0700

    Initial commit: Khoi tao local repository va cau hinh danh tinh

$ git log --oneline
e0b334c Initial commit: Khoi tao local repository va cau hinh danh tinh
```

---

## 5. Phân Tích & So Sánh Cấu Hình `--local` vs `--global`

| Cụm tùy chọn | Phạm vi tác động | Vị trí lưu trữ tệp cấu hình | Trường hợp sử dụng |
| :--- | :--- | :--- | :--- |
| **`git config --local`** | Chỉ có hiệu lực trong repository hiện tại | `.git/config` tại thư mục dự án | Dành cho từng dự án cụ thể (dự án công ty, dự án học tập, dự án mã nguồn mở) |
| **`git config --global`** | Áp dụng cho toàn bộ các repository của user hiện tại | `~/.gitconfig` (hoặc `C:\Users\<User>\.gitconfig`) | Dành cho thông tin mặc định cá nhân trên máy |

> **Đánh giá**: Sử dụng `--local` đảm bảo tính bảo mật và độc lập dữ liệu khi làm việc trên nhiều dự án khác nhau cùng lúc.

---

## 6. Kết Luận

- Khởi tạo thành công Local Repository Git tại thư mục `SS04/Bai01`.
- Cấu hình chuẩn xác thông tin danh tính tác giả cấp độ cục bộ (`DevOps Student` - `devops.student@example.com`).
- Thực hiện thành công commit đầu tiên (`e0b334c`) lưu trữ tệp nguồn `index.html`.
- Liên kết kho lưu trữ với Remote Repository trên GitHub `https://github.com/DevOpsPTIT/SS04_Bai01.git`.
- Báo cáo và đầy đủ log chứng minh đã hoàn thành 100% yêu cầu bài tập.
