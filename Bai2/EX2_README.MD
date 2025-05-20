# Bài Tập Chuyển Đổi Mô Hình ERD Sang Mô Hình Dữ Liệu Quan Hệ - Quản Lý Điểm Thi

## 1. Mô tả bài toán

Từ mô hình ERD quản lý thông tin học sinh, môn học, giáo viên và bảng điểm thi, yêu cầu chuyển đổi thành mô hình dữ liệu quan hệ (các bảng SQL) với các ràng buộc khóa chính, khóa ngoại, đồng thời tuân thủ các quy ước:

- **Tên thuộc tính** viết theo quy tắc **CamelCase** (ví dụ: `MaHS`, `TenGV`).
- **Từ khóa và ràng buộc SQL** như `primary key`, `foreign key`, `references` viết **chữ thường**.

Mô hình gồm các thực thể chính:

- `HocSinh` (học sinh)
- `MonHoc` (môn học)
- `GiaoVien` (giáo viên)
- `BangDiem` (bảng điểm)

---

## 2. Cấu trúc dữ liệu quan hệ

Dưới đây là mã SQL tạo các bảng theo mô hình:

```sql
create database QuanLiDiemThi;

use QuanLiDiemThi;

create table HocSinh (
    MaHS varchar(20) primary key,
    TenHS varchar(50),
    NgaySinh datetime,
    Lop varchar(20),
    GT varchar(20)
);

create table GiaoVien (
    MaGV varchar(20) primary key,
    TenGV varchar(20),
    SDT varchar(10)
);

create table MonHoc (
    MaMH varchar(20) primary key,
    TenMH varchar(50),
    MaGV varchar(20),
    constraint FK_MaGV foreign key (MaGV) references GiaoVien(MaGV)
);

create table BangDiem (
    MaHS varchar(20),
    MaMH varchar(50),
    DiemThi int,
    NgayKT datetime,
    foreign key (MaHS) references HocSinh(MaHS),
    foreign key (MaMH) references MonHoc(MaMH)
);
