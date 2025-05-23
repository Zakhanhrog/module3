```sql
use classicmodels;

CREATE VIEW customer_views AS
    SELECT 
        customerNumber, customerName, phone
    FROM
        customers;
        select * from customer_views;
        
        create or replace view customer_views as 
        select customerNumber, customerName, contactFirstName, contactLastName, phone
		from customers
        where city = 'Nantes';