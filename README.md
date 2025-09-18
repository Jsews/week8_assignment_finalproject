 # week8_assignment_finalproject
# 📚 Library Management System – Database Design
# 📌 Objective

This project implements a relational database in MySQL for managing a library. It demonstrates:

Well-structured tables

Proper constraints (PRIMARY KEY, FOREIGN KEY, NOT NULL, UNIQUE)

Different types of relationships (One-to-One, One-to-Many, Many-to-Many)

# 🏗️ Database Schema
Entities & Attributes

Members – Stores library member details

member_id (PK), full_name, email, phone, join_date

Books – Stores book information

book_id (PK), title, author, isbn, published_year, copies_available

Staff – Stores librarian/staff details

staff_id (PK), name, role, hire_date

Borrow_Records – Tracks book borrowing activity

borrow_id (PK), member_id (FK), book_id (FK), staff_id (FK), borrow_date, return_date

Payments – Stores membership/payment records

payment_id (PK), member_id (FK, UNIQUE), amount, payment_date

# 🔗 Relationships

One-to-Many: A member can borrow many books (Members → Borrow_Records)

Many-to-Many: A book can be borrowed by many members, and a member can borrow many books (resolved via Borrow_Records)

One-to-One: Each member can have at most one payment record (Members ↔ Payments)

# 💻 SQL Implementation

The implementation includes:

CREATE DATABASE statement

CREATE TABLE statements with constraints

Relationship constraints (FOREIGN KEY, ON DELETE CASCADE, ON DELETE SET NULL)

All SQL code is included in library_db.sql.

# 🚀 How to Run

Open MySQL CLI or Workbench.

Run the .sql file:

mysql -u root -p < library_db.sql


Verify tables:

SHOW TABLES;


Insert sample data and test queries, for example:

-- Show all borrowed books
SELECT m.full_name, b.title, br.borrow_date, br.return_date
FROM Borrow_Records br
JOIN Members m ON br.member_id = m.member_id
JOIN Books b ON br.book_id = b.book_id;

# ✅ Deliverables

library_db.sql → Full database creation script

README.md → Documentation of schema and instructions
 
