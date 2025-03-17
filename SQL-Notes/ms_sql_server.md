# **MS-SQL-Server**

## **References**
- [SQLShack](https://www.sqlshack.com/sql-server-training/)
- [PopSQL](https://popsql.com/learn-sql)

### **What is T-SQL?**  
**T-SQL (Transact-SQL)** is Microsoft's proprietary extension of SQL that provides additional features beyond standard SQL. It includes:  
1. **Procedural Programming Features**:  
   - Variables (`DECLARE`, `SET`)  
   - Conditional statements (`IF...ELSE`)  
   - Loops (`WHILE`)  

2. **Enhanced Transaction Handling**:  
   - `BEGIN TRANSACTION`, `COMMIT`, `ROLLBACK` for better control over database transactions  

3. **Error Handling**:  
   - `TRY...CATCH` blocks for exception handling  

4. **Built-in Functions**:  
   - String functions (`LEN()`, `SUBSTRING()`)  
   - Date functions (`GETDATE()`, `DATEADD()`)  
   - System functions (`@@IDENTITY`, `SCOPE_IDENTITY()`)  

5. **Stored Procedures and Triggers**:  
   - **Stored Procedures** allow reusable query execution  
   - **Triggers** automate actions based on database events  

6. **Cursor Support**:  
   - Cursors enable row-by-row processing of query results  

### **Difference Between SQL and T-SQL**  
| Feature | SQL (Standard) | T-SQL (MS SQL Server) |
|---------|---------------|------------------------|
| **Scope** | General query language | Extended procedural programming features |
| **Control Flow** | No procedural features | Supports loops, conditions (`IF`, `WHILE`) |
| **Error Handling** | Limited (`NULL` checks) | Advanced (`TRY...CATCH`) |
| **Transaction Management** | Basic (`COMMIT`, `ROLLBACK`) | Enhanced control (`SAVEPOINT`, `@@TRANCOUNT`) |

### **Example of T-SQL in SQL Server**  
Let's compare standard SQL and T-SQL:  

#### **Standard SQL (Basic Query)**  
```sql
SELECT name, age FROM Employees WHERE age > 30;
```

#### **T-SQL (With Variables and Control Flow)**  
```sql
DECLARE @AgeLimit INT;
SET @AgeLimit = 30;

SELECT name, age 
FROM Employees 
WHERE age > @AgeLimit;
```

## **Query to check if a particular columng exists in a given table**
```sql
-- query to check if a coulumn exists in a specified table
IF EXISTS (
	SELECT column_name FROM INFORMATION_SCHEMA.columns 
	WHERE 
        table_name = '<table-name>' 
    AND 
        column_name = '<column-name>'
	)
	SELECT 'Column Exists'
ELSE
	SELECT 'Column does not exist'
;
```
---

## **Get the definition of an SQL View**
```sql
-- get the SELECT statement used to create the view
EXEC sp_helptext '<schema_name>.<view_name>';

-- alternative query
SELECT OBJECT_DEFINITION(OBJECT_ID('<view_name>'));
```
---

## **Steps to Add a Column to a View in SQL Server**
To update a **view** in SQL Server by adding a new column, you need to **recreate** the view using `ALTER VIEW` or `CREATE OR REPLACE VIEW` (if using newer versions). Unlike tables, you **cannot directly alter** a view to add a column; instead, you must redefine it.

#### **1. Check the Existing View Definition**
Before modifying the view, check its existing structure using:

```sql
EXEC sp_helptext 'YourViewName';
```
OR  
```sql
SELECT OBJECT_DEFINITION(OBJECT_ID('YourViewName'));
```
This will display the current SQL definition of the view.

---

#### **2. Alter the View to Include the New Column**
- You must include the new column in the `SELECT` statement used to define the view.
- Use `ALTER VIEW` and modify the existing `SELECT` statement.

**Example**: Suppose you have a view named `EmployeeView` based on the `Employees` table:

**Original View:**
```sql
CREATE VIEW EmployeeView AS
SELECT EmployeeID, Name, Department FROM Employees;
```

**Now, you want to add the `Salary` column. Use `ALTER VIEW`:**
```sql
ALTER VIEW EmployeeView AS
SELECT EmployeeID, Name, Department, Salary FROM Employees;
```

---

#### **3. Verify the Updated View**
After modifying the view, check if the new column is present:
```sql
SELECT * FROM EmployeeView;
```

---

### **Important Notes**
1. **Ensure the column exists in the underlying table**  
   - If the column does not exist in the base table (`Employees` in this case), you need to **alter the table first** before updating the view.

2. **Permissions**  
   - You need `ALTER` or `CREATE VIEW` permission on the database.

3. **Impact on Dependent Objects**  
   - If any stored procedures, triggers, or reports depend on the view, ensure they support the added column.