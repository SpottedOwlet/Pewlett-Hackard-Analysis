<h2><p align=center> Pewlett Hackard Analysis </p> </h2>

<h3><p> Background </p></h3>
Pewlett Hackard is a large company with several thousand employees currently employed. As the baby boomers begin to retire at a rapid rate, Hewlett Packard is looking at the future in two ways:

  - Offer A Retirement Package For Eligible Employees
  - To Figure Out Which Positions Need To Be Filled In The Near Future

<h3><p> Purpose </p></h3>
The purpose of the new analysis is to determine the number of retiring employees per title, and to identify employees who are eligible to participate in a mentorship program, in order to deal with large number of upcoming retirements.


<h3><p> Resources: </p></h3>
Data Source: Pewlett Hackard Employee database files (employees.csv, departments.csv, dept_emp.csv, dept_manager.csv, salaries.csv, titles.csv)
Software: PostgreSQL 14, pgAdmin 4

<h3><p> Analysis Overview: </p></h3>

As a part of initial analysis, the number of retiring employees are filtered and stored into retirement_info as per the retirement eligibility criteria. The retirement_info table contains the employee number, first name, last name for all the employees who are born between January 1,1952 and December 31,1955 and also who are hired between Jan 01,1985 and Dec 31,1988.

<h4> PART I : Retiring Employee Information by Title</h4>

- As part of the further analysis, the employee information like employee number, first name, last name, employee's title, along with from and to date for that title, all of this data is filtered into retirement_titles table. From the retirement titles table, **unique titles are filtered into unique_titles table** using **DISTINCT ON on emp_no field**. 

- In the next step, using the **aggregate function COUNT** on the title field, **retiring_titles** table is obtained, which contains the **title wise retirement data** for the employees.


<kbd>![Screen Shot 2021-12-10 at 3 35 01 PM](https://user-images.githubusercontent.com/90424752/145653961-4e80890f-4db9-4d11-bcd6-28fd86404f49.png)
</kbd>

<h4> PART II : Mentorship Eligibility Information</h4>

As many employees with various titles are expected to retire from the company in a short duration, the Pewlett Hackard is seeking mentors among its employees to guide and train the replacements. The eligible employees for mentorship program is found by JOINING employees, dept_emp and titles table and then filtering the data to check whether the employees and currently employed and are born between January 1, 1965 and December 31, 1965. The mentorship eligibility table gives the following data.

<kbd>![Screen Shot 2021-12-10 at 3 31 18 PM](https://user-images.githubusercontent.com/90424752/145653742-c2f0e5a6-54c7-4699-b606-aab65d3fc6e8.png)
</kbd>

<h3><p> Results </p></h3>

- Part one of the analysis looks into the number of total employees that are going to retire in the near future and their titles.
- The total number of employees that are eligible for the company's retirement package are 90,398
- Majority of the employees that are expected to retire soon, bear the titles Senior Engineer (29,414 employees) and Senior Staff (28,254 employees).
- As per the above analysis, currently there are 1,549 employees at Pewlett Hackard, that are eligible to participate in the mentorship program.


<h2><p align=center> Summary </p></h2>

- A staggering high number of employees are retiring from Pewlett Hackard in the near future. Running the following query gives us the exact number of retiring employees, which is 90,398.

<h4><p align=left>Number of Retiring Employees</p></h4>


<kbd>![Screen Shot 2021-12-10 at 10 00 03 PM](https://user-images.githubusercontent.com/90424752/145666205-5a22d9d7-c75c-4ef4-8d1e-3e617a2e88c4.png) </kbd>

- The ratio of mentors available per new employees is pivotal towards the success of mentorship program. The available mentors for each title as per current mentorship eligibility criteria are found using the following query.

<kbd>![Screen Shot 2021-12-10 at 9 03 53 PM](https://user-images.githubusercontent.com/90424752/145664607-f2dc853b-0f8f-4a9a-a25d-86359c2de281.png)</kbd>

- However, to assess the mentorship program feasibility we need to know the ratio of mentors to future new recruits. To find the ratio, an additional query is performed. The following tables can be referred to compare the ratio.

 Available Mentors by Title| Retiring Employees by Title
:-------------------------:|:-------------------------:
![](https://user-images.githubusercontent.com/90424752/145665517-6bc4df0c-bae1-4626-b4bc-a23f2fc5e64c.png)  |  ![](https://user-images.githubusercontent.com/90424752/145665356-e2dcc791-4251-400c-8bb7-35f75393b790.png)

- As observed from the table above, the ratio of available mentors to retiring employees is very high, indicating that per 50 to 70 employees leaving, there is only 1 mentor to train the replacements. Which is practically impossible to work out.

- Ideally, there should be at least one mentor per 2 to 4 employees. To achieve this ratio, the eligibility criteria was extended to include the year 1964 along with 1965. The results for which are displayed in the tables below:

 Extended Eligibility for Mentorship| Retiring Employees by Title
:----------------------------------:|:--------------------------------:
![](https://user-images.githubusercontent.com/90424752/145671041-e6f38801-4908-4dc2-839b-b99fdd0c6687.png)  |  ![](https://user-images.githubusercontent.com/90424752/145665356-e2dcc791-4251-400c-8bb7-35f75393b790.png)

- The new ratios now lie between 2 to 6 which makes a huge difference and the mentorship program seems feasible. If Pewlett Hackard wants to successfully run the mentorship program, they need to adjust the mentorship eligibility criteria in order to make more mentors available.
