# Day 15 – Database Fundamentals

## What is a database?
A database is an organized collection of data that can be stored, accessed, managed and updated efficiently.

Example: An employee management system stores employee IDs, names, departments, email addresses and job roles.

## What is a table?
A table stores related data in rows and columns.

| employee_id | name | department |
|---|---|---|
| 101 | Rahul | IT |
| 102 | Priya | HR |
| 103 | Aman | Finance |
| 104 | Neha | IT |

## Rows and columns
- **Row:** A complete record, such as `101, Rahul, IT`.
- **Column:** An attribute or field, such as `name` or `department`.

The example table has 4 rows and 3 columns.

## Primary Key (PK)
A Primary Key is a column, or combination of columns, that uniquely identifies each row.
- Values must be unique.
- A Primary Key cannot contain NULL.
- Each row must be identifiable by its Primary Key.

Example: `employee_id` can be the Primary Key if every value is unique and non-NULL.

## Foreign Key (FK)
A Foreign Key is a column in one table that references a key in another table, creating a relationship.

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

- `Departments.department_id` is the Primary Key.
- `Employees.department_id` is a Foreign Key referencing the department key.
- Duplicate Foreign Key values are allowed.
- A Foreign Key may be NULL if permitted by the column and database rules.
- When the Foreign Key constraint is enforced, a non-NULL value must reference an existing parent key.

## Primary Key vs Foreign Key

| Primary Key | Foreign Key |
|---|---|
| Uniquely identifies a row | References a key in another table |
| Must be unique | Duplicates are allowed |
| Cannot be NULL | May be NULL if permitted |

## Quick revision
- Database: organized collection of data.
- Table: data arranged in rows and columns.
- Row: record.
- Column: field or attribute.
- Primary Key: unique, non-NULL identifier.
- Foreign Key: reference that establishes a relationship between tables.
