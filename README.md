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
