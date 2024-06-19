# GW-Project-3-Workforce-Diversity-and-Salary-Analysis-Using-Power-BI-SQL

## Project Overview

This project aims to analyze employee demographic and compensation data from SQL database tables to provide insights into workforce distribution, diversity, and salary structures across various business units and departments. By leveraging Power BI's powerful visualization capabilities, the project delivers actionable insights to aid strategic decision-making and resource allocation.

## Objectives

- Understand the ethnic diversity across different business units.
- Determine the count of employees within each business unit.
- Analyze the average salaries by department, both before and after bonuses.
- Examine the distribution of employees by zip code.
- Identify the departments with the highest number of employees.

## Data Sources

- **EmployeeSampleDataCSV**
- **DepartmentSampleDataCSV**

## Data Import and Setup

1. **Import CSV Files to SQL Database:**
   - Import the `EmployeeSampleDataCSV` and `DepartmentSampleDataCSV` tables to the `EMPDEPDB` SQL database.
   - Ensure to select the right data types for each attribute (e.g., Hire Date & Exit Date as Date, Annual_Sal as Int/Float, Bonus as float).
   - Set `Employee_ID` and `Dept_ID` as primary keys.

2. **Create Foreign Key Relationships:**
   - After the tables are created in `Emp_DB`, use the `ALTER` command to add foreign keys:
     ```sql
     ALTER TABLE EmployeeSampleDataCSV
     ADD FOREIGN KEY (EDept_ID) REFERENCES DepartmentSampleDataCSV(Dept_ID);
     ```

3. **SQL Query for Direct Query in Power BI:**
   - Create a direct query containing the required data attributes:
     ```sql
     Select
     Employee_ID,Full_Name,Business_Unit,Gender,Ethnicity,
     Annual_Salary,
     (Annual_Salary+(Annual_Salary*Convert(float,Bonus)/100)) as Revised_Sal,
     Bonus,Department_Name,Dept_State,Dept_Zip,Dep_Country
     From EmployeeSampleDataCSV E
     Join DepartmentSampleDataCSV D
     on E.Edept_ID = D.Dept_ID;
     ```

## Power BI Visualizations

### Sheet 1: Business Unit Analysis
1. **Ethnicity by Business Unit (Stacked Bar Chart)**
   - Filters: Business Unit, Ethnicity, Gender, Department
2. **Count of Employees by Business Unit (Funnel Chart)**
   - Filters: Business Unit, Gender, Department, Ethnicity
3. **Count of Employees by Department (Stacked Column Chart)**
   - Filters: Department, Business Unit, Gender, Ethnicity

### Sheet 2: Salary Analysis
1. **Average of Salaries by Department (Stacked Column Chart)**
   - Filters: Department, Business Unit, Gender, Ethnicity
2. **Average of Salaries by Department after Bonus (Clustered Bar Chart)**
   - Filters: Department, Business Unit, Gender, Ethnicity
3. **Count of Employees by Dept_Zip Code (Stacked Column Chart)**
   - Filters: Department, Business Unit, Gender, Ethnicity

## Dashboard Glimpse

![sc](https://github.com/ramyakrj5/GW-Project-3-Workforce-Diversity-and-Salary-Analysis-Using-Power-BI-SQL/blob/main/GW%20Project%203%20using%20Power%20Bi%2CSQL-images-0.jpg)
![sc](https://github.com/ramyakrj5/GW-Project-3-Workforce-Diversity-and-Salary-Analysis-Using-Power-BI-SQL/blob/main/GW%20Project%203%20using%20Power%20Bi%2CSQL%20(1)-images-4.jpg)
![sc](https://github.com/ramyakrj5/GW-Project-3-Workforce-Diversity-and-Salary-Analysis-Using-Power-BI-SQL/blob/main/GW%20Project%203%20using%20Power%20Bi%2CSQL%20(1)-images-5.jpg)
![sc](https://github.com/ramyakrj5/GW-Project-3-Workforce-Diversity-and-Salary-Analysis-Using-Power-BI-SQL/blob/main/GW%20Project%203%20using%20Power%20Bi%2CSQL%20(1)-images-6.jpg)


## Recommendations

- Enhance diversity initiatives, especially in business units with lower ethnic representation.
- Focus on strategic roles within Speciality Products and IT departments.
- Review compensation strategies to ensure alignment with market standards, particularly in high-skill departments like Human Resources and Marketing.


