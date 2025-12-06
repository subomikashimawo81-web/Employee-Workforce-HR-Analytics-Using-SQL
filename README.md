# 📊 HR Analytics SQL Project  
### Employee Insights Using SQL (MySQL)
This project explores an HR employee database using SQL to answer real business questions on workforce demographics, salaries, hiring trends, and employee retention.  
It demonstrates my ability to write clean SQL queries, analyze multi-table relational data, and translate insights into meaningful business decisions.

## 📂 *Database Structure*
The database contains the following relational tables:

- *employees* – employee demographic information  
- *departments* – list of departments  
- *dept_emp* – employee → department assignments  
- *dept_manager* – department managers  
- *salaries* – salary history of employees  
- *titles* – job titles assigned to employees  
These tables are connected through primary/foreign keys, allowing real-world HR analysis.

# 🧩 *Business Questions & SQL Solutions*

## 👥 *1. Gender Distribution*
### 🔧 SQL Query
SELECT 
    gender, COUNT(*) AS total_employees
FROM 
    employees
GROUP BY gender;
## 📝Insight
The results show that males form a larger portion of the workforce than females.

## 2. Average Employee Age
## SQL Query
SELECT 
    AVG(TIMESTAMPDIFF(YEAR, 
        birth_date, CURDATE())) AS average_age
FROM 
    employees;
## Insight
The average employee age is approximately 67 years, indicating a senior workforce.
## 📅3. Total Employees Hired per Year
## 🔧SQL Query
SELECT 
    YEAR(hire_date) AS hire_year,
    COUNT(*) AS total_employees
FROM 
    employees
GROUP BY YEAR(hire_date)
ORDER BY hire_year;
## 📝Insight
Hiring peaked between 1985–1988, with more than 30,000 hires annually. Hiring slowed after 1989, possibly due to restructuring or automation.

## 💰Salary & Compensation Analysis
## 🏆4. Highest & Lowest Paid Departments
## 🔧SQL Query
SELECT 
    d.dept_name,
    AVG(s.salary) AS average_salary
FROM 
    departments d
JOIN
    dept_emp de ON d.dept_no = de.dept_no
JOIN
    salaries s ON de.emp_no = s.emp_no
GROUP BY d.dept_name
ORDER BY average_salary DESC;
## 📝Insight 
•	Sales Department has the highest average salaries.
•	Human Resources Department appears to be the lowest paid.

## 💵 5.Top 5 Highest-Paid Employees
## 🔧SQL Query
SELECT 
    e.emp_no, e.first_name, e.last_name, s.salary
FROM
    employees e
JOIN 
    salaries s ON e.emp_no = s.emp_no
ORDER BY s.salary DESC
LIMIT 5;
## 📝Insight
The highest-paid employee earns 158,220.

## 📈6. Salary Growth Trend Over Time
## 🔧SQL Query
SELECT 
    y.year, ROUND(AVG(s2.salary), 2) AS avg_salary
FROM 
    (SELECT DISTINCT YEAR(from_date) AS year
FROM 
    salaries) y
    JOIN
salaries s2
    ON YEAR(s2.from_date) = y.year
GROUP BY y.year;
## 📝Insight
Average salaries steadily increased from 1986–2002, followed by a slight decline, likely due to budget changes or market downturn.

## 🕒Tenure & Retention
## 🏅7. Longest-Serving Employees
## 🔧SQL Query
SELECT
  e.emp_no,
  e.first_name,
  e.last_name,
  e.hire_date,
  TIMESTAMPDIFF(YEAR, e.hire_date, CURDATE()) AS years_with_company
FROM 
    employees e LIMIT 5;
## 📝Insight
The longest-serving employee has been with the company for 40 years, showing excellent retention and institutional loyalty.

## 🏁Conclusion
## This HR Analytics SQL Project demonstrates the ability to:
	•	Query and analyze multi-table relational databases
	•	Use JOINs, GROUP BY, ORDER BY, aggregate functions, and date functions
	•	Translate SQL results into meaningful business insights
	•	Build a clean, structured portfolio project

This project reflects my improved SQL proficiency and serves as part of my growing Data Analytics portfolio.

