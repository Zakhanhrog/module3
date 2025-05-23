✅ **Phân biệt DML và DDL trong SQL**

SQL (Structured Query Language) được chia thành nhiều loại câu lệnh khác nhau, trong đó phổ biến nhất là:

- **DML (Data Manipulation Language)** – Ngôn ngữ thao tác dữ liệu
- **DDL (Data Definition Language)** – Ngôn ngữ định nghĩa dữ liệu

Dưới đây là bảng so sánh chi tiết:

| **Tiêu chí**                 | **DML (Data Manipulation Language)**             | **DDL (Data Definition Language)**             |
|-----------------------------|--------------------------------------------------|------------------------------------------------|
| **Chức năng chính**         | Thao tác dữ liệu trong các bảng                 | Định nghĩa hoặc thay đổi cấu trúc của bảng hoặc CSDL |
| **Tác động đến**            | Nội dung bên trong bảng                         | Cấu trúc bảng, cơ sở dữ liệu                   |
| **Câu lệnh phổ biến**       | `SELECT`, `INSERT`, `UPDATE`, `DELETE`          | `CREATE`, `ALTER`, `DROP`, `TRUNCATE`         |
| **Khả năng Rollback**       | ✅ Có thể rollback (nếu trong transaction)      | ❌ Không rollback được sau khi thực hiện       |
| **Tác động đến dữ liệu**    | Có, thay đổi nội dung của bảng                  | Không (chỉ thay đổi cấu trúc)                 |
| **Ví dụ khi dùng**          | Thêm nhân viên, cập nhật lương, xóa hồ sơ nhân viên | Tạo bảng mới, thêm cột, xóa bảng          |

---

### 🔹 **DML – Data Manipulation Language**
- **1. `SELECT` – Truy vấn dữ liệu:**
    ```sql
    SELECT * FROM Employees WHERE Department = 'IT';

- **2. `INSERT` – Thêm dữ liệu:**
    ```sql
    INSERT INTO Employees (Name, Department, Salary)
    VALUES ('An', 'Sales', 12000000);

- **3. `UPDATE` – Cập nhật dữ liệu:**
    ```sql
    UPDATE Employees
    SET Salary = Salary + 1000000
    WHERE Department = 'IT';

- **4. `DELETE` – Xóa dữ liệu:**
- ```sql
    DELETE FROM Employees WHERE Name = 'An';

### 🔹 **DDL – Data Definition Language**
- **1. `CREATE` – Tạo bảng hoặc đối tượng:**
    ```sql
    CREATE TABLE Employees (
    EmployeeID INT PRIMARY KEY,
    Name VARCHAR(100),
    Department VARCHAR(50),
    Salary DECIMAL(10, 2)
    );

- **2. `ALTER` – Thay đổi cấu trúc bảng:**
    ```sql
    ALTER TABLE Employees ADD COLUMN Email VARCHAR(100);

- **3. `DROP` – Xóa bảng hoặc đối tượng:**
    ```sql
    DROP TABLE Employees;

### 🔍 **Tóm tắt:**
| DML                           | DDL                         |
| ----------------------------- | --------------------------- |
| Làm việc với **dữ liệu**      | Làm việc với **cấu trúc**   |
| Có thể rollback               | Không thể rollback          |
| Cần thiết để thao tác dữ liệu | Cần thiết khi thiết kế bảng |

