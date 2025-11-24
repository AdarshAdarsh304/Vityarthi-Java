Digital Library Management System (DLMS)
Course: CSE2006 - Programming in Java


📖 1. Overview
The Digital Library Management System (DLMS) is a robust, console-based Java application designed to automate and streamline the core operations of a university library. It replaces traditional manual record-keeping with a secure, database-backed digital solution.

This project demonstrates the practical application of Object-Oriented Programming (OOP), JDBC (Java Database Connectivity), Multithreading, and Exception Handling.

🚀 2. Features
🔹 Admin Module (Librarian)
Secure Login: Authentication system to prevent unauthorized access.

Inventory Management: Add new books, update stock quantities, and view book details.

Reporting: View a complete list of available books and track issued items.

🔹 Student Module (Member)
Search Functionality: Search for books by Title to check real-time availability.

Issue Book: Borrow books if stock is available (automatic stock deduction).

Return Book: Return books and automatically calculate overdue fines.

🔹 System Logic (Automated)
Fine Calculation: Automatically calculates fines based on the due date:

Fine = (Return Date - Due Date) * 10 Rs/Day

Background Monitoring: A background thread runs concurrently to check for overdue books and log alerts.

🛠️ 3. Technology Stack
Component

Technology

Language

Java (JDK 21)

Database

MySQL 8.0

Driver

MySQL Connector/J 9.5.0

IDE

Visual Studio Code

Build Tool

Manual Classpath Management

⚙️ 4. Installation & Setup
Prerequisites
Java Development Kit (JDK) 21 or higher installed.

MySQL Server installed and running.

Visual Studio Code (or any Java IDE).

Step 1: Database Setup
Open your MySQL Client (Workbench or Command Line).

Run the SQL script provided in library_setup.sql to create the database and tables.

source library_setup.sql;

Verify the tables (books, members, issue_records) are created.

Step 2: Configure Application
Open DBConnection.java.

Update the username and password to match your local MySQL credentials:

private static final String USER = "root";
private static final String PASSWORD = "your_password";

Step 3: Compile & Run
Method A: Using the Run Script (Windows)

Double-click the run.bat file included in the project folder.

Method B: Manual Compilation (Terminal)

Open a terminal in the project root.

Compile all files:

javac -cp "lib/mysql-connector-j-9.5.0.jar;." *.java

(Note: On Mac/Linux, use : instead of ; as the separator)

Run the application:

java -cp "lib/mysql-connector-j-9.5.0.jar;." Main

🧪 5. Testing Guide
Test Case

Action

Expected Result

Login

Enter admin@library.com / wrongpass

"Invalid Credentials" message.

Issue Book

Enter valid Book ID (Stock > 0)

"Book Issued Successfully". Stock decreases by 1.

Issue Book

Enter Book ID with 0 Stock

"Book Out of Stock" message.

Return Book

Return a book after Due Date

System displays calculated Fine amount.

📂 6. Project Structure
Digital-Library-System/
│
├── lib/
│   └── mysql-connector-j-9.5.0.jar  # JDBC Driver
│
├── src/
│   ├── Main.java               # Entry point & UI Logic
│   ├── DBConnection.java       # Database Connection Singleton
│   ├── BookDAO.java            # Data Access Object (CRUD Logic)
│   ├── Book.java               # Book Model
│   ├── Member.java             # Member Model
│   └── OverdueCheckTask.java   # Background Thread for alerts
│
├── library_setup.sql           # SQL Script for Database
├── run.bat                     # Quick Start Script for Windows
└── README.md                   # Project Documentation

🔮 7. Future Enhancements
GUI Implementation: Migrating from Console to JavaFX for a graphical interface.

Barcode Scanner: Integrating hardware support to scan ISBNs for faster book issuing.

Email Alerts: Using JavaMail API to notify students of upcoming due dates.
