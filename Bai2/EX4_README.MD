# Bài Tập Chuyển Đổi Mô Hình ERD Sang Mô Hình Dữ Liệu Quan Hệ

## 1. Mô tả bài toán

Từ mô hình ERD đã cho, yêu cầu chuyển đổi thành mô hình dữ liệu quan hệ (các bảng SQL), đảm bảo các ràng buộc khóa chính và khóa ngoại chính xác, đồng thời tuân theo các quy ước sau:

- **Tên thuộc tính** viết theo quy tắc **CamelCase** (ví dụ: `MaNCC`, `TenVTU`,...).
- **Từ khóa và ràng buộc SQL** như `primary key`, `foreign key`, `references` phải viết **chữ thường**.

Mô hình gồm các thực thể chính:

- VATTU (vật tư)
- NHACC (nhà cung cấp)
- PHIEUXUAT (phiếu xuất)
- PHIEUNHAP (phiếu nhập)
- DONDH (đơn đặt hàng)

Cùng với các mối quan hệ:

1. **Chi tiết phiếu xuất**
2. **Chi tiết phiếu nhập**
3. **Chi tiết đơn đặt hàng**
4. **Cung cấp** (liên kết giữa nhà cung cấp và vật tư)

---

## 2. Cấu trúc dữ liệu quan hệ

Dưới đây là mã SQL tạo các bảng theo đúng mô hình:

```sql
create table NHACC (
    MaNCC varchar(10) primary key,
    TenNCC varchar(100),
    DiaChi varchar(200),
    SDT varchar(20)
);

create table VATTU (
    MaVTU varchar(10) primary key,
    TenVTU varchar(100)
);

create table CUNG_CAP (
    MaNCC varchar(10),
    MaVTU varchar(10),
    primary key (MaNCC, MaVTU),
    foreign key (MaNCC) references NHACC(MaNCC),
    foreign key (MaVTU) references VATTU(MaVTU)
);

create table PHIEUXUAT (
    SoPX varchar(10) primary key,
    NgayXuat date
);

create table PHIEUNHAP (
    SoPN varchar(10) primary key,
    NgayNhap date
);

create table CT_PHIEUXUAT (
    SoPX varchar(10),
    MaVTU varchar(10),
    DGXuat decimal(10,2),
    SLXuat int,
    primary key (SoPX, MaVTU),
    foreign key (SoPX) references PHIEUXUAT(SoPX),
    foreign key (MaVTU) references VATTU(MaVTU)
);

create table CT_PHIEUNHAP (
    SoPN varchar(10),
    MaVTU varchar(10),
    DGNhap decimal(10,2),
    SLNhap int,
    primary key (SoPN, MaVTU),
    foreign key (SoPN) references PHIEUNHAP(SoPN),
    foreign key (MaVTU) references VATTU(MaVTU)
);

create table DONDH (
    SoDH varchar(10) primary key,
    NgayDH date,
    MaNCC varchar(10),
    foreign key (MaNCC) references NHACC(MaNCC)
);

create table CT_DONDH (
    SoDH varchar(10),
    MaVTU varchar(10),
    primary key (SoDH, MaVTU),
    foreign key (SoDH) references DONDH(SoDH),
    foreign key (MaVTU) references VATTU(MaVTU)
);
