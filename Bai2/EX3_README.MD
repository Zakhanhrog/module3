# Bài Tập Chuyển Đổi Mô Hình ERD Sang Mô Hình Dữ Liệu Quan Hệ - Quản Lý Sinh Viên

## 1. Mô tả bài toán

Từ mô hình ERD quản lý thông tin sinh viên, lớp học, môn học và điểm số, yêu cầu chuyển đổi thành mô hình dữ liệu quan hệ (các bảng SQL) với các ràng buộc khóa chính, khóa ngoại, đồng thời tuân thủ các quy ước:

- **Tên thuộc tính** viết theo quy tắc **CamelCase** (ví dụ: `ClassID`, `StudentName`).
- **Từ khóa và ràng buộc SQL** như `primary key`, `foreign key`, `references` viết **chữ thường**.

Mô hình gồm các thực thể chính:

- `Class` (lớp học)
- `Student` (sinh viên)
- `Subject` (môn học)
- `Mark` (điểm)

---

## 2. Cấu trúc dữ liệu quan hệ

Dưới đây là mã SQL tạo các bảng theo mô hình:

```sql
create database QuanLySinhVien;

use QuanLySinhVien;

create table Class (
    ClassID int primary key auto_increment,
    ClassName varchar(60) not null,
    StartDate datetime not null,
    Status bit
);

create table Student (
    StudentID int primary key auto_increment,
    StudentName varchar(30) not null,
    Address varchar(50),
    Phone varchar(20),
    Status bit,
    ClassID int not null,
    foreign key (ClassID) references Class(ClassID)
);

create table Subject (
    SubID int primary key auto_increment,
    SubName varchar(30) not null,
    Credit tinyint not null default 1 check (Credit >= 1),
    Status bit default 1
);

create table Mark (
    MarkID int primary key auto_increment,
    SubID int not null,
    StudentID int not null,
    Mark float default 0 check (Mark between 0 and 100),
    ExamTimes tinyint default 1,
    unique (SubID, StudentID),
    foreign key (SubID) references Subject(SubID),
    foreign key (StudentID) references Student(StudentID)
);
