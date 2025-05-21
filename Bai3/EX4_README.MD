# Quản lý Bán Hàng

## 1. Thêm dữ liệu vào 4 bảng

### Bảng `Customer`
```sql
INSERT INTO Customer (cID, cName, cAge) VALUES
('1', 'Minh Quan', 10),
('2', 'Ngoc Oanh', 20),
('3', 'Hong Ha', 50);
```

### Bảng `Orders`
```sql
INSERT INTO Orders (oID, cID, oDate, oTotalPrice) VALUES
('1', '1', '2006-03-21', NULL),
('2', '2', '2006-03-23', NULL),
('3', '1', '2006-03-16', NULL);
```

### Bảng `Product`
```sql
INSERT INTO Product (pID, pName, pPrice) VALUES
('1', 'May Giat', 3),
('2', 'Tu Lanh', 5),
('3', 'Dieu Hoa', 7),
('4', 'Quat', 1),
('5', 'Bep Dien', 2);
```

### Bảng `OrderDetail`
```sql
INSERT INTO OrderDetail (oID, pID, odQTY) VALUES
('1', '1', 3),
('1', '3', 7),
('1', '4', 2),
('2', '1', 1),
('2', '5', 4),
('2', '3', 3);
```

---

## 2. Các truy vấn hiển thị

### a. Hiển thị oID, oDate, oTotalPrice từ bảng Orders
```sql
SELECT oID, oDate, oTotalPrice FROM Orders;
```

### b. Hiển thị danh sách các khách hàng đã mua hàng và các sản phẩm đã mua
```sql
SELECT DISTINCT c.cName, p.pName
FROM Customer c
JOIN Orders o ON c.cID = o.cID
JOIN OrderDetail od ON o.oID = od.oID
JOIN Product p ON od.pID = p.pID;
```

### c. Hiển thị tên những khách hàng không mua sản phẩm nào
```sql
SELECT cName
FROM Customer
WHERE cID NOT IN (SELECT DISTINCT cID FROM Orders);
```

### d. Hiển thị mã hóa đơn, ngày bán và tổng giá trị từng hóa đơn
```sql
SELECT o.oID, o.oDate, SUM(od.odQTY * p.pPrice) AS TotalPrice
FROM Orders o
JOIN OrderDetail od ON o.oID = od.oID
JOIN Product p ON od.pID = p.pID
GROUP BY o.oID, o.oDate;
```