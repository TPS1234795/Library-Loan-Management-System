# Library Loan Management System

A JDBC-based Library Loan Management System developed using Java and Apache Derby database. The project demonstrates database connectivity, CRUD operations, transaction management, and performance benchmarking through a menu-driven console application.

------------------------------------------------------------

# Project Overview

The system automates basic library operations such as:
- Adding members
- Adding books
- Processing book loans
- Returning books
- Viewing records
- Performance benchmarking

The project also demonstrates JDBC transaction management using commit and rollback mechanisms to maintain database consistency.

------------------------------------------------------------

# Features

- JDBC database connectivity
- CRUD operations
- Transaction management
- Loan processing system
- Menu-driven console interface
- Performance benchmarking
- Batch insert optimization
- Apache Derby embedded database

------------------------------------------------------------

# Technologies Used

| Technology     | Purpose                    |
|----------------|----------------------------|
| Java           | Application development    |
| JDBC           | Database connectivity      |
| Apache Derby   | Embedded relational DB     |
| SQL            | Database operations        |
| Eclipse IDE    | Development environment    |

------------------------------------------------------------

# Project Structure

src/
└── com/
    └── dbms/
        └── project_2341016436/
            ├── BusinessLogic.java
            ├── ConnectionManager.java
            ├── DatabaseSetup.java
            ├── MainApp.java
            ├── PerformanceEvaluator.java
            └── TransactionService.java

------------------------------------------------------------

# Module Description

| Class Name            | Responsibility                 |
|-----------------------|--------------------------------|
| ConnectionManager     | Database connection handling   |
| DatabaseSetup         | Table creation and setup       |
| BusinessLogic         | CRUD operations                |
| TransactionService    | Transaction management         |
| PerformanceEvaluator  | Benchmark evaluation           |
| MainApp               | Menu-driven execution          |

------------------------------------------------------------

# Database Tables

Members Table

| Column Name  | Data Type |
|--------------|-----------|
| MemberID     | INT       |
| Name         | VARCHAR   |
| ActiveLoans  | INT       |

Books Table

| Column Name | Data Type |
|-------------|-----------|
| BookID      | INT       |
| Title       | VARCHAR   |
| ISBN        | VARCHAR   |
| Available   | BOOLEAN   |

Loans Table

| Column Name | Data Type |
|-------------|-----------|
| LoanID      | INT       |
| MemberID    | INT       |
| BookID      | INT       |
| LoanDate    | DATE      |
| ReturnDate  | DATE      |

# JDBC Connection

ConnectionManager.java

private static final String URL =
        "jdbc:derby:libraryDB;create=true";

public static Connection getConnection()
        throws SQLException {

    return DriverManager.getConnection(URL);
}

This class establishes and manages database connectivity with Apache Derby database.

------------------------------------------------------------

# Database Initialization

DatabaseSetup.java

stmt.executeUpdate(
    "CREATE TABLE Books (" +
    "BookID INT PRIMARY KEY GENERATED ALWAYS AS IDENTITY, " +
    "Title VARCHAR(200), " +
    "ISBN VARCHAR(50), " +
    "Available BOOLEAN)"
);

This module creates all required database tables and initializes schema.

------------------------------------------------------------

# Transaction Management

TransactionService.java

con.setAutoCommit(false);

con.commit();

con.rollback();

Transaction management ensures database consistency during loan processing operations.

------------------------------------------------------------

# CRUD Operations

Add Book Example

String sql =
    "INSERT INTO Books(Title, ISBN, Available) " +
    "VALUES(?,?,true)";

Show Books Example

String sql =
    "SELECT * FROM Books";

CRUD operations are implemented using PreparedStatement for secure and efficient query execution.

------------------------------------------------------------

# Performance Benchmarking

PerformanceEvaluator.java

long start = System.nanoTime();

ps.executeBatch();

long end = System.nanoTime();

The project compares:
- Normal insert operations
- Batch insert operations

to evaluate JDBC performance optimization.

------------------------------------------------------------

# Benchmark Results

| Operation      | Records Inserted | Execution Time |
|----------------|------------------|----------------|
| Normal Insert  | 1000             | 106.46 ms      |
| Batch Insert   | 1000             | 30.95 ms       |

Observation:
Batch insert execution performed significantly faster than normal insert execution due to reduced database communication overhead.

------------------------------------------------------------

# How to Run the Project

Step 1:
Open project in Eclipse IDE.

Step 2:
Ensure JDK 21 is installed.

Step 3:
Add Apache Derby library to project build path.

Step 4:
Run MainApp.java

Step 5:
Use menu options to perform operations.

------------------------------------------------------------

# Sample Menu

===== LIBRARY MENU =====

1. Add Member
2. Add Book
3. Show Books
4. Process Loan
5. Return Book
6. Run Benchmark
7. Show Members
8. Show Loans
0. Exit

------------------------------------------------------------

# Key Highlights

- Implemented JDBC connectivity successfully
- Demonstrated transaction management
- Used commit and rollback operations
- Performed CRUD operations
- Evaluated batch insert performance
- Developed modular Java application

------------------------------------------------------------

# Conclusion

The Library Loan Management System successfully demonstrates practical implementation of Java JDBC, database connectivity, transaction management, CRUD operations, and performance optimization using Apache Derby database.

------------------------------------------------------------


