```sql
create database demo;

use demo;
DROP TABLE IF EXISTS Products;


create table if not exists Products(
 id int auto_increment primary key ,
 productCode varchar(50) not null unique,
 productName varchar(255) not null,
 productPrice decimal(10,2) not null,
 productAmount int not null default 0,
 productDescription text,
 productStatus varchar(100)
);
insert into Products(productCode, productName, productPrice, productAmount, productDescription, productStatus)
 values
 ('P001', 'Laptop ThinkPad X1', 25000000.00, 10, 'Laptop doanh nhân cao cấp, mỏng nhẹ', 'Còn hàng'),
('P002', 'Điện thoại iPhone 15', 30000000.00, 25, 'Điện thoại thông minh đời mới nhất', 'Còn hàng'),
('P003', 'Chuột Logitech MX Master 3', 2200000.00, 50, 'Chuột không dây công thái học', 'Còn hàng'),
('P004', 'Bàn phím cơ Filco', 3500000.00, 15, 'Bàn phím cơ chất lượng cao từ Nhật Bản', 'Sắp về hàng'),
('P005', 'Màn hình Dell UltraSharp 27', 12000000.00, 8, 'Màn hình 27 inch, độ phân giải 2K', 'Còn hàng'),
('P006', 'Ổ cứng SSD Samsung 1TB', 2800000.00, 30, 'Ổ cứng thể rắn tốc độ cao, dung lượng 1TB', 'Hết hàng'),
('P007', 'Tai nghe Sony WH-1000XM5', 8500000.00, 12, 'Tai nghe chống ồn chủ động cao cấp', 'Còn hàng'),
('P008', 'Webcam Logitech C922', 1800000.00, 0, 'Webcam full HD, hỗ trợ streaming', 'Ngừng kinh doanh');

explain select * from Products where productName = 'Laptop ThinkPad X1' AND productPrice > 20000000;

create unique index idx_productCode on Products(productCode);

create index idx_productName_price on Products(productName,productPrice);

explain select * from Products where productCode = 'P003';

EXPLAIN SELECT * FROM Products WHERE productName = 'Laptop ThinkPad X1' AND productPrice > 20000000;

EXPLAIN SELECT * FROM Products WHERE productName = 'Điện thoại iPhone 15';

create view Products_view as
select productCode,productName,productPrice,productStatus
from Products;

select * from Products_view;

create or replace view Products_view as
select productCode,productName,productPrice,productStatus
from Products
where productStatus = 'Còn hàng';

drop view Products_view;
