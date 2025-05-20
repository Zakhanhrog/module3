# Bài Tập Chuyển Đổi Mô Hình ERD Sang Mô Hình Dữ Liệu Quan Hệ - Quản Lý Bán Hàng

## 1. Mô tả bài toán

Từ mô hình ERD quản lý thông tin khách hàng, đơn hàng, sản phẩm và chi tiết đơn hàng, yêu cầu chuyển đổi thành mô hình dữ liệu quan hệ (các bảng SQL) với các ràng buộc khóa chính, khóa ngoại, và quy tắc sau:

- **Tên thuộc tính** viết theo quy tắc **CamelCase** (ví dụ: `cID`, `oDate`, `pPrice`).
- **Từ khóa và ràng buộc SQL** như `primary key`, `foreign key`, `references` viết **chữ thường**.
- Ràng buộc **on delete cascade** được sử dụng để tự động xóa dữ liệu liên quan khi bản ghi cha bị xóa.

Mô hình gồm các thực thể chính:

- `Customer` (khách hàng)
- `Orders` (đơn hàng)
- `Product` (sản phẩm)
- `OrderDetail` (chi tiết đơn hàng)

---

## 2. Cấu trúc dữ liệu quan hệ

Dưới đây là mã SQL tạo các bảng theo mô hình:

```sql
create database QuanLyBanHang;
use QuanLyBanHang;

create table Customer (
  cID varchar(20) primary key,
  cName varchar(50) not null,
  cAge int check (cAge >= 1)
);

create table Orders (
  oID varchar(20) primary key,
  cID varchar(20) not null,
  oDate datetime,
  oTotalPrice float not null,
  foreign key (cID) references Customer(cID) on delete cascade
);

create table Product (
  pID varchar(20) primary key,
  pName varchar(50) not null,
  pPrice float not null
);

create table OrderDetail (
  oID varchar(20) not null,
  pID varchar(20) not null,
  odQTY int not null,
  primary key (oID, pID),
  foreign key (oID) references Orders(oID) on delete cascade,
  foreign key (pID) references Product(pID) on delete cascade
);
