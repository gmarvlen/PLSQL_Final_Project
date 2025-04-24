# Final Project - BookStore SQL Database

## Objective
Design and implement a comprehensive SQL-based database system for a small bookstore. The project demonstrates advanced SQL features including DDL, DML, stored procedures, functions, and dynamic SQL.

---

## Database Setup
- **Database Name:** `BookStore`
- **Core Tables:**
  - `Books(BookID, Title, Author, Price, ISBN, PublishDate)`
  - `Customers(CustomerID, FirstName, LastName, Email, JoinDate)`
  - `Orders(OrderID, CustomerID, BookID, Quantity, OrderDate)`
  - `Employees(EmployeeID, FirstName, LastName, HireDate, Email)`

---

## Data Insertions
- 5 rows inserted into each of the `Books`, `Customers`, `Orders`, and `Employees` tables.
- Additional records added to support function and query validations.

---

## Stored Procedures

### 1. `AddNewOrder`
- **Inputs:** OrderID, CustomerID, BookID, Quantity
- **Process:** Inserts a new record into the `Orders` table.
- **Output:** Confirmation message.

### 2. `UpdateBookPrice`
- **Inputs:** BookID, NewPrice
- **Process:** Updates price for a specified book.
- **Output:** Confirmation message.

---

## Functions

### 1. `CalculateOrderTotal`
- **Input:** OrderID
- **Process:** Multiplies quantity with book price for a given order.
- **Returns:** Total price.

### 2. `TotalBooksSoldByAuthor`
- **Input:** AuthorName
- **Process:** Aggregates quantities of all books by a given author.
- **Returns:** Total units sold.

---

## Queries

### a. Books Published After 2020
```sql
SELECT * FROM Books WHERE PublishDate > TO_DATE('2020-01-01', 'YYYY-MM-DD');
```

### b. Customers with More Than 5 Orders
```sql
SELECT c.CustomerID, c.FirstName, c.LastName, COUNT(o.OrderID) AS OrderCount
FROM Customers c
JOIN Orders o ON c.CustomerID = o.CustomerID
GROUP BY c.CustomerID, c.FirstName, c.LastName
HAVING COUNT(o.OrderID) > 5;
```

### c. Longest Serving Employee
```sql
SELECT * FROM Employees WHERE HireDate = (SELECT MIN(HireDate) FROM Employees);
```

---

## Dynamic SQL Procedure

### `SearchBooksDynamic`
- **Inputs:** SearchType (`'Author'`, `'Title'`, `'PublishYear'`), SearchValue
- **Output:** Book details matching search criteria

### Example Use:
```sql
BEGIN
    SearchBooksDynamic('Author', 'George Orwell');
END;
```

---


## Tools Used
- **Oracle SQL Developer**: Main development environment for creating, executing, and debugging SQL scripts, procedures, and functions.
- **PL/SQL (Procedural Language for SQL)**: Used for procedural operations such as loops, conditions, and exception handling in the BookStore system.
- **DBMS_OUTPUT.PUT_LINE**: Utilized for displaying messages and debug information during execution of procedures and functions.

## Submission Contents
- SQL scripts for all DDL, DML, procedures, and functions
- Example executions with `DBMS_OUTPUT.PUT_LINE` outputs
- Demonstration of dynamic query capabilities
- Screenshots of query results and outputs for documentation

This project showcases practical usage of advanced PL/SQL features in building a real-world bookstore management system.
