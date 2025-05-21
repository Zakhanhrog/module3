### Hiển thị tất cả sinh viên có tên bắt đầu bằng chữ "h"
```sql
SELECT * 
FROM Student 
WHERE StudentName LIKE 'h%';
```
### Hiển thị các thông tin lớp học có thời gian bắt đầu vào tháng 12
```sql
SELECT * 
FROM Class 
WHERE MONTH(StartDate) = 12;
```

### Hiển thị tất cả thông tin môn học có credit trong khoảng từ 3-5  
```sql
SELECT * 
FROM Subject 
WHERE Credit BETWEEN 3 AND 5;
```

### Thay đổi mã lớp (ClassID) của sinh viên có tên 'Hung' thành 2
```sql
UPDATE Student 
SET ClassID = 2 
WHERE StudentName = 'Hung';
```

### Hiển thị các thông tin: StudentName, SubName, Mark. Dữ liệu sắp xếp theo điểm giảm dần, nếu trùng thì theo tên tăng dần
```sql
SELECT s.StudentName, sub.SubName, m.Mark
FROM Mark m
JOIN Student s ON m.StudentID = s.StudentID
JOIN Subject sub ON m.SubID = sub.SubID
ORDER BY m.Mark DESC, s.StudentName ASC;
```
