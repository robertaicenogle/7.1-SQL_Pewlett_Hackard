# Pewlett-Hackard-Analysis

## Project Overview
In this project we'll use PostgreSQL to analyze Pewlett Hackards employee database in order to help manage employee retirement/turnover. Specifically, we'll determine the number of retiring employees in each title, and identify which employees are able to engage in an employee mentorship program.

- Deliverable 1: The Number of Retiring Employees by Title
- Deliverable 2: The Employees Eligible for the Mentorship Program
- Deliverable 3: A written report on the employee database analysis

Resources: PostgreSQL, pgAdmin
Data Source: 

## Results

### Deliverable 1: The Number of Retiring Employees by Title

Here, you can see the number of retiring employees based on title.

![](retiring_titles.PNG)


Additionally, you can see the retirees by their title during retirement, as well as additional employee data in table 2.

![](unique_titles.PNG)

![](retirement_titles.PNG)



### Deliverable 2: The Employees Eligible for the Mentorship Program

Below are the employees who are eligible for the Mentorship Program. The full list is available as a CSV file in the data folder.
![](SQL2.PNG)

### Deliverable 3: A written report on the employee database analysis
Summary: 
- Based on the data, there are a total 0f 90,398 employees nearing retirement, nearly 40% of the companies total number of employees. However, there are only just over 1,500 employees eligible to mentor next generation of Pewlett Hackard employees. As a result, I do not think the company is ready for the upcoming "silver tsunami."
- Two additional queries or tables that may provide further insight into the upcoming change in employment include retiring employees per department and eligible mentors per department. Further analysis - and even additional payments for mentorship eligible employees to stay on longer - are necessary.


Employee Database with SQL


Contents
Introduction
Installation
Data Modeling
Identify Data Relationships
Determine Entity Relationships
Quick Database Diagrams Tools
Create ERDs
Data Engineering
Create a Database
Create Tables in SQL
Import Data
Troubleshoot Imports
Data Analysis
Query Dates
Join the Tables
Joins in Action
Use Count, Group By, and Order By
Create Additional Lists
Create a Tailored List


Introduction
In this introduction, we’ll cover SQL background and installation of PostreSQL and pgAdmin.

Background
Background info on SQL.

Installation
First, we’ll need to download and install PostgreSQL and pgAdmin.
Visit the PostgreSQL download website
https://www.enterprisedb.com/downloads/postgres-postgresql-downloads
Initiate download option appropriate for the system (mac, Windows)

PostgreSQL and pgAdmin download as a package
Follow installation instructions:
Record your password (needed to access your SQL database)
Install PostgreSQL to /Library/PostgreSQL/11, the default location
Find install files in Library and then in PostgreSQL
You may uncheck Stack Builder’s box

Add data directory to /Library/PostgreSQL/11/data
Where data will be loaded and stored
Use default port 5432
Under Advanced Options, set the locale as “[Default locale]”
After reviewing the installation summary, click “Next” to begin installation
If final setup screen prompts you to launch Stack Builder at exit, uncheck the box and click “Finish”

If prompted, restart your computer to complete installation

You should be able to access the Postgres 11 folder from your start menu
To confirm installation, start pgAdmin (a new browser will launch) and double-click to connect to the default server and enter your password.
Log in to access and work with pgAdmin and PostgreSQL




Data Modeling



Data Engineering
In SQL, data is organized into tables. We will create a table for each CSV, tailored specifically for the data in each CSV file.

Launch pgAdmin
Launch pgAdmin to open the graphical user interface (GUI)
A GUI is an interface that helps us to navigate the program
We’ll use it to create our database, then connect to it
After connecting to the server, you should see an existing database named “postgres”



Create a New Database
To create a new database to hold the employee information, follow these steps:
Right-click on “PostgreSQL 11”
Hover your pointer over “create”
From the menu that pops up on the right, click “Database”

 A form will pop up prompting for information
Name the database something relevant
Click “save” to create new database

After the new database has been created, the database count in pgAdmin will have increased to two, and the new database will be listed

A red x beside the new database’s name indicates we aren’t yet connected to it, but it is there and ready for use.
Click on the new database to connect
Once connected, will be able to create tables and import data

Create Tables in SQL
To create a functioning database, we’ll need to first create a table for each CSV file, map out the primary and foreign keys, and assign data types.
Right-click on the database PH-EmployeeDB
From the dropdown menu, scroll down to Query Tool and click to select
Query Tool is pgAdmin’s text editor

After opening the Query Tool, a query editor will appear in the pgAdmin window

To create our new table, type the following code into the query editor
-- Creating tables for PH-EmployeeDB
CREATE TABLE departments (
	dept_no VARCHAR(4) NOT NULL,
	dept_name VARCHAR(40) NOT NULL,
	PRIMARY KEY (dept_no),
	UNIQUE (dept_name)
);
This code creates a table called “departments”

Explain: Write Statements to Create Tables
Let’s Break down the above code. We’re creating a table called Departments with two columns, defining the primary key, and adding a unique constraint.
The first line is a comment that states the reason for the code
A SQL comment begins with two hyphens (--)
CREATE TABLE is the syntax required to create a new table in SQL
departments (
the name of the table and how it will be referenced in queries
dept_no VARCHAR(4) NOT NULL, 
creates a column named “dept_no” that can hold up to four varying characters
NOT NULL tells SQL that no null fields will be allowed when importing data
dept_name VARCHAR(40) NOT NULL, 
creates a column similar to dept_no, only the varying character count has a maximum of 40
PRIMARY KEY (dept_no), 
means that the dept_no column is use as a primary key for this table
UNIQUE (dept_name) 
adds the unique constraint to the dept_name column
Note: A constraint is a rule applied to a column in a SQL table. It limits the data in a way that provides more accuracy and reliability when working with it. The unique constraint implies that the data is unique and ensures that if the table were to be updated in the future, nothing will be duplicated.
); 
Signal that the SQL CREATE TABLE statement is complete.
Any additional code will need to be included in a new statement
Note: Each SQL statement will have the same syntax, or set of rules to follow, to perform a successful query. For instance, in the CREATE TABLE statement, we tell SQL we’re creating a table, we name it, and then enclose any additional parameters within a set of parentheses. The parameters within parentheses, such as column names and primary key, are all indented (to help keep the code clean and readable). A semicolon at the end signals that the statement is complete.

Execute the Code
To save the table to the database we’ll need to execute the code. In the toolbar of the pgAdmin webpage, find and click the lightning bolt symbol toward the right of the bar. This button runs the code and saves our work to the database.

Clicking this button will run the CREATE TABLE statement and save the empty table to the database
A successful execution will return a message confirming the table creation


Troubleshoot Error Messages
An error message will appear in the same manner (as successful execution). Troubleshooting these errors is a huge part of the data analysis process. Each message in SQL will tell us why the error occurred. If you run the CREATE TABLE statement again, for example, we’ll get this error message: 

This error occurs because SQL data is persistent and cannot be overwritten if the same command is run again. Once a table has been committed to a database, it is there until a different command is run to delete it. This helps to preserve the data already in place.
To avoid encountering this error, highlight the code block you want to run first, then execute it. This tells pgAdmin to run only that code.
Often error messages are more confusing and require additional research to solve. Googling the error message itself will likely bring you to a conversation between developers about why the problem occurred and how to fix it.

Create Additional Tables
Create another table for each CSV file. Just as before, we’ll need to know the name of the table, the number of name of columns, and the data type for each.
To create a new table, start with the CREATE TABLE statement and name the table
CREATE TABLE employees (
     emp_no INT NOT NULL,
     birth_date DATE NOT NULL,
     first_name VARCHAR NOT NULL,
     last_name VARCHAR NOT NULL,
     gender VARCHAR NOT NULL,
     hire_date DATE NOT NULL,
     PRIMARY KEY (emp_no)
);
Examining the code, we have everything needed to create the table: the SQL statement, the table components, and the closing parenthesis and semicolon.
Execute the CREATE TABLE statement
Make sure to highlight only the code you want to run
Click lightning bolt (execute) button

Create an another new table (dept_manager) – this time with foreign keys
Run the following code:
CREATE TABLE dept_manager (
	dept_no VARCHAR(4) NOT NULL,
	emp_no INT NOT NULL,
	from_date DATE NOT NULL,
	to_date DATE NOT NULL,
FOREIGN KEY (emp_no) REFERENCES employees (emp_no),
FOREIGN KEY (dept_no) REFERENCES departments (dept_no),
	PRIMARY KEY (emp_no, dept_no)
);

This table is like the last one, except for two lines: 
FOREIGN KEY (emp_no) REFERENCES employees (emp_no),
FOREIGN KEY (dept_no) REFERENCES departments (dept_no),
Remember that foreign keys reference the primary key of other tables.
This shows us the following:
The FOREIGN KEY constraint tells Postgres that there is a link between the two tables
The parentheses following FOREIGN KEY specify which of the current table’s columns is linked to another table
REFERENCES table_name (column_name), tells Postgres which other table uses that column as a primary key



Data Analysis
