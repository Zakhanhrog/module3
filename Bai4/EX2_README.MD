# SQL Queries - Student Management Database

## 1. Display all subjects with the highest credit

```sql
SELECT *
FROM Subject
WHERE Credit = (SELECT MAX(Credit) FROM Subject);
```

## 2. Display subject information that has the highest exam mark

```sql
SELECT s.*
FROM Subject s
JOIN Mark m ON s.SubID = m.SubID
WHERE m.Mark = (SELECT MAX(Mark) FROM Mark);
```

## 3. Display student information along with their average mark, sorted by average mark in descending order

```sql
SELECT st.*, AVG(m.Mark) AS AvgMark
FROM Student st
JOIN Mark m ON st.StudentID = m.StudentID
GROUP BY st.StudentID, st.StudentName, st.Address, st.Phone, st.Status, st.ClassID
ORDER BY AvgMark DESC;
```

---

**Note:** These queries are designed based on the provided EER diagram. Ensure your database schema matches the structure shown in the diagram for the queries to work properly.