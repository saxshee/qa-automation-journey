# Week 3 – Day 15: Database Fundamentals

## 1. What is a database?
A database is an organized collection of data that can be stored, accessed, managed and updated efficiently.

Example: An employee management system may store employee IDs, names, departments, email addresses and job roles.

## 2. What is a table?
A table stores related data in rows and columns.

Example – `employees`:

| employee_id | name | department |
|---|---|---|
| 101 | Rahul | IT |
| 102 | Priya | HR |
| 103 | Aman | Finance |
| 104 | Neha | IT |

## 3. Rows and columns
- **Row:** One complete record. For example, `101, Rahul, IT`.
- **Column:** One attribute or field, such as `name` or `department`.

The example table has 4 rows and 3 columns.

## 4. Primary Key (PK)
A Primary Key is a column, or combination of columns, that uniquely identifies each row in a table.

Primary Key rules:
- Values must be unique.
- A Primary Key cannot contain NULL.
- Each row must be identifiable by its Primary Key.

Example: `employee_id` can be the Primary Key in the employees table if every value is unique and non-NULL.

A repeated employee ID means that column cannot serve as the table's Primary Key in that data.

## 5. Foreign Key (FK)
A Foreign Key is a column in one table that references a key in another table, creating a relationship between the tables.

**Departments**

| department_id (PK) | department_name |
|---|---|
| 1 | IT |
| 2 | HR |
| 3 | Finance |

**Employees**

| employee_id (PK) | name | department_id (FK) |
|---|---|---|
| 101 | Rahul | 1 |
| 102 | Priya | 2 |
| 103 | Aman | 1 |
| 104 | Neha | 3 |

Here:
- `Departments.department_id` is the Primary Key.
- `Employees.department_id` is a Foreign Key referencing the department key.
- Duplicate Foreign Key values are allowed; multiple employees can belong to the same department.
- A Foreign Key may be NULL if the column and database rules allow it.
- With an enforced Foreign Key constraint, a non-NULL value must reference an existing key in the parent table. An unmatched value such as 5 is rejected if no department with ID 5 exists.

## 6. Primary Key vs Foreign Key

| Primary Key | Foreign Key |
|---|---|
| Uniquely identifies a row in its table | References a key in another (or the same) table |
| Must be unique | Duplicates are allowed |
| Cannot be NULL | May be NULL if permitted |
| One table has one Primary Key constraint (which may contain multiple columns) | A table can have multiple Foreign Key constraints |

## Quick revision
- Database: organized collection of data.
- Table: data arranged in rows and columns.
- Row: record.
- Column: field or attribute.
- Primary Key: unique, non-NULL identifier.
- Foreign Key: reference that establishes a relationship between tables.
