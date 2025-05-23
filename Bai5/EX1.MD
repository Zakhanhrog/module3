```sql
use classicmodels;

SELECT
    C.customerNumber,       
    C.customerName,        
    COUNT(O.orderNumber) AS SoLuongDonHang 
FROM customers C            
JOIN orders O ON C.customerNumber = O.customerNumber
GROUP BY C.customerNumber, C.customerName 
ORDER BY SoLuongDonHang DESC;   

select 
SUM(od.quantityOrdered * od.priceEach) AS TongDoanhThuThang5
from orders o 
join 
orderdetails od ON o.orderNumber = od.orderNumber
where
MONTH(o.orderDate) = 5
AND o.status IN ('Shipped' , 'Resolved');

ALTER TABLE customers ADD INDEX idx_full_name(contactFirstName, contactLastName);

EXPLAIN SELECT * FROM customers WHERE customerName = 'Land of Toys Inc.'; 

EXPLAIN SELECT * FROM customers WHERE contactFirstName = 'Jean' or contactFirstName = 'King';

ALTER TABLE customers DROP INDEX idx_full_name;

