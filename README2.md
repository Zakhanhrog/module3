# 📚 Cơ Sở Dữ Liệu Quan Hệ - SQL Cơ Bản

Tài liệu này tổng hợp các câu lệnh SQL cơ bản dùng để làm việc với **cơ sở dữ liệu quan hệ**, bao gồm: tạo cơ sở dữ liệu, bảng, thao tác dữ liệu và giải thích từ khóa SQL phổ biến.

---

## 🗂️ 1. Quản lý Cơ sở dữ liệu

- **Tạo CSDL**:
  ```sql
  CREATE DATABASE test_database DEFAULT CHARACTER SET utf8 COLLATE utf8_unicode_ci;
- **Xóa CSDL**:
    ```sql
    DROP DATABASE new_database;
- **Chọn CSDL để làm việc**:
    ```sql
    USE test_database;

## 📋 2. Tạo bảng

- **Tạo bảng Student**:
    ```sql
    CREATE TABLE Student (
    ID INT,
    name VARCHAR(200),
    age INT,
    country VARCHAR(50)
    );

- **Tạo bảng có khóa chính và tự động tăng ID**:
    ```sql
    CREATE TABLE Student (
    ID INT AUTO_INCREMENT,
    name VARCHAR(200),
    age INT,
    country VARCHAR(50),
    PRIMARY KEY (ID)
    );

- **Tạo bảng có khóa ngoại**:
    ```sql
    CREATE TABLE Class (
    class_id INT PRIMARY KEY,
    class_name VARCHAR(100)
    );

    CREATE TABLE Student (
    student_id INT PRIMARY KEY,
    name VARCHAR(100),
    class_id INT,
    FOREIGN KEY (class_id) REFERENCES Class(class_id)
    );

- **Tạo bảng có đặt tên ràng buộc**:
    ```sql
    CREATE TABLE Contacts (
    contact_id INT,
    name VARCHAR(100),
    phone VARCHAR(20),
    email VARCHAR(100),
    CONSTRAINT contacts_pk PRIMARY KEY (contact_id)
    );

## 🔄 3. Thao tác dữ liệu (DML)

- **Thêm dữ liệu**:
    ```sql
    INSERT INTO Student (ID, name, age, country)
    VALUES (1, 'Nguyen Van A', 20, 'Vietnam');

- **Cập nhật dữ liệu**:
    ```sql
    UPDATE Student
    SET age = 21
    WHERE ID = 1;

- **Xóa dữ liệu**:
    ```sql
    DELETE FROM Student
    WHERE ID = 1;

## 🔍 4. Truy vấn dữ liệu (SELECT)

- **Chọn tất cả dữ liệu**:
    ```sql
    SELECT * FROM Student;

- **Chọn có điều kiện**:
    ```sql
    SELECT name, country
    FROM Student
    WHERE age > 18;

- **Sắp xếp kết quả**:
    ```sql
    SELECT * FROM Student
    ORDER BY age DESC;

- **Gộp nhóm và điều kiện nhóm**:
    ```sql
    SELECT country, COUNT(*) AS total
    FROM Student
    GROUP BY country
    HAVING total > 1;

## 🧠 5. Từ khóa SQL phổ biến

| Từ khóa       | Ý nghĩa                                    |
| ------------- | ------------------------------------------ |
| `CREATE`      | Tạo mới cơ sở dữ liệu, bảng, v.v.          |
| `DROP`        | Xóa cơ sở dữ liệu hoặc bảng                |
| `SELECT`      | Truy vấn dữ liệu từ bảng                   |
| `INSERT INTO` | Thêm dữ liệu mới vào bảng                  |
| `UPDATE`      | Cập nhật dữ liệu                           |
| `DELETE`      | Xóa dữ liệu                                |
| `PRIMARY KEY` | Định danh duy nhất cho mỗi bản ghi         |
| `FOREIGN KEY` | Khóa tham chiếu từ bảng khác               |
| `NOT NULL`    | Cột không được để trống                    |
| `UNIQUE`      | Đảm bảo giá trị không bị trùng             |
| `DEFAULT`     | Giá trị mặc định khi không có dữ liệu nhập |
| `ORDER BY`    | Sắp xếp kết quả theo cột                   |
| `GROUP BY`    | Nhóm kết quả theo cột                      |
| `HAVING`      | Điều kiện sau `GROUP BY`                   |
| `JOIN`        | Kết nối nhiều bảng                         |
| `LIKE`        | Tìm kiếm với ký tự đại diện (`%`, `_`)     |
| `LIMIT`       | Giới hạn số dòng kết quả                   |




