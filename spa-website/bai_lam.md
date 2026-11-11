# BÀI LÀM – HACKATHON 02

- **Mã đề:** 07
- **Họ tên:** Phạm Nhật Anh
- **Lớp:** HN-KS26-CNTT3
- **Link repository:** https://github.com/NkatAnh/HNKS26CNTT3_Nhap-Mon-CNTT_Hackathon02.git
- **Hệ điều hành (Windows/macOS):** Windows

## 4.2. Thao tác máy tính cơ bản bằng CLI

### Các lệnh đã chạy

```shell
pwd
ls -Force
mv .\lich_lam_viec.txt .\docs\
mkdir backup
cp .\data\hoa_don_spa_thang_7.xlsx .\backup\
rm .\temp_707.tmp
cd .\logs\
ls
cd..
ls -Recurse -Force
```

### Kết quả liệt kê toàn bộ dự án (Windows: Get-ChildItem -Recurse -Force; macOS: ls -aR)

```text
 Directory: D:\starter-kit\spa-website


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
d-----        11/11/2026  10:51 AM                backup
d-----        11/11/2026  10:51 AM                data
d-----        11/11/2026  10:51 AM                docs
d-----        11/11/2026  10:44 AM                evidence
d-----        11/11/2026  10:51 AM                logs
d-----         11/3/2026   7:07 AM                web
-a----         11/3/2026   7:07 AM             75 .env
-a----        11/11/2026  10:53 AM           2601 bai_lam.md


    Directory: D:\starter-kit\spa-website\backup


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
-a----         11/3/2026   7:07 AM           6149 hoa_don_spa_thang_7.xlsx


    Directory: D:\starter-kit\spa-website\data


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
-a----         11/3/2026   7:07 AM           6149 hoa_don_spa_thang_7.xlsx


    Directory: D:\starter-kit\spa-website\docs


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
-a----         11/3/2026   7:07 AM            149 lich_lam_viec.txt


    Directory: D:\starter-kit\spa-website\logs


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
-a----         11/3/2026   7:07 AM            939 service.log


    Directory: D:\starter-kit\spa-website\web


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
d-----         11/3/2026   7:07 AM                images
-a----         11/3/2026   7:07 AM            597 app.js
-a----         11/3/2026   7:07 AM            523 index.html
-a----         11/3/2026   7:07 AM            460 style.css


    Directory: D:\starter-kit\spa-website\web\images


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
-a----         11/3/2026   7:07 AM           3091 logo-lotuscare.png

```

## 4.3. Lọc log truy cập website

### a) Lệnh lọc các dòng status=500

```shell
Select-String "status=500" .\logs\service.log > .\logs\loi_500.txt
 Get-Content .\logs\loi_500.txt -Head 3
```

### 2 dòng đầu tiên trong logs/loi_500.txt

```text
logs\service.log:4:2026-07-28 08:12:50 POST /api/dat-lich status=500
logs\service.log:7:2026-07-28 08:19:23 POST /api/dat-lich status=500

```

### b) Lệnh đếm số dòng status=404 và kết quả

```shell
(Get-Content .\logs\service.log | Select-String "status=404").Count

```

```text
4

```

## 4.4. Chạy script tong_hop (.ps1 hoặc .sh)

### Lệnh chạy (Windows: nếu dùng Phụ lục 2 thì ghi cả 2 lệnh)

```shell
New-Item tong_hop.ps1
Set-ExecutionPolicy -Scope Process -ExecutionPolicy Bypass
.\tong_hop.ps1
```

### Nội dung file logs/tong_hop.txt

```text
=== BAO CAO SU CO WEBSITE ===

2026-07-28 08:16:12 GET /images/phong-spa-3.jpg status=404
2026-07-28 08:39:18 GET /uu-dai-cu status=404
2026-07-28 08:46:40 GET /tin-tuc status=404
2026-07-28 08:48:51 GET /tin-tuc status=404




Count    : 6
Average  : 
Sum      : 
Maximum  : 
Minimum  : 
Property : 





```

## 4.5. README.md và bảo vệ thông tin bí mật

> README.md, .gitignore và .env.example được chấm trực tiếp trên file ở gốc dự án. Đánh dấu `[x]` vào các mục đã làm để tự kiểm tra.

- [x] README.md: Heading 1, mô tả có **in đậm** và *in nghiêng*, bảng, code block, task list, blockquote
- [x] .gitignore có dòng `.env` (tên file đúng, không có đuôi .txt)
- [x] .env.example có đủ tên biến, giá trị để trống (tên file đúng, không có đuôi .txt)

## 4.6. Kiểm tra trang web bằng DevTools (F12) và báo cáo lỗi

### Bảng lỗi

| STT | Tab DevTools phát hiện lỗi | Tên file hoặc thông báo lỗi | Cách khắc phục |
| --- | --- | --- | --- |
| 1 | Network | sai tên file logo.png | sửa lại tên file |
| 2 | Console | Uncaught ReferenceError: hienThiGoiDichVu is not defined | hỏi trưởng nhóm |

> Ảnh chụp màn hình lưu trong thư mục `evidence/` (network.png, console.png).

### Báo cáo lỗi gửi trưởng nhóm

- **Context:** Tôi là sinh viên năm nhất chưa fix lỗi hiển thị dữ liệu của web bao giờ
- **Expected:** Bây giờ trang web xem phim của tôi muốn có đủ dữ liệu ở bảng hiển thị giao diện
- **Actual:** Dữ liệu trên trang web không có gì và tôi vào tab console thấy thông báo lỗi Uncaught ReferenceError: hienThiGoiDichVu is not defined
- **Log:** Uncaught ReferenceError: hienThiGoiDichVu is not defined

### Câu tìm kiếm Google

```text
site:stackoverflow.com "Uncaught ReferenceError"

```

## 4.7. Excel

> Phần Excel được chấm trực tiếp trên file `data/hoa_don_spa_thang_7.xlsx`, không cần ghi vào đây.
