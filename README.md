# Projects-Analysis-Dashboard

### Project Overview

Thsi projects aims to help the company mange it's worksforce, understand the financial risks and monitor project health more effectively.

![Screenshot (56)](https://github.com/user-attachments/assets/5f31c9e6-06d0-487f-a7f6-07cfb1ea2476)

### Data Source:
- completed_projects.csv
- departments.csv
- employees.csv
- head_shots.csv
- projects_assignements.csv
- projects.csv
- upcoming prjects.csv

### Tools
1. SQL Server - Data Analysis
2. Power BI - Visualisation

### Data Cleaning/Preparation

- Created a database forthe company
- joined the various tables from the different csv files to have comprehensive data which can easily be used to create insightful data.

### Exploratory Data Anlysis

EDA involved exploring the data from different sources provided to answer key qustions, such as:

- Which departments are at risking of being over budget or underperforming?
- Can the company cover all its expeses during the year?

### Data Analysis

``` sql
-- project status

with project_status as (
select
project_id,
project_name,
project_budget,
'upcoming' as Status
from upcoming_projects
union all
select
project_id,
project_name,
project_budget,
'completed' as status
from completed_projects)


-- big table
select 
e.employee_id,
e.first_name,
e.last_name,
e.job_title,
e.salary,
d.Department_Name,
pa.project_id,
p.project_name,
p.Status
from employees e

join departments d
on e.department_id = d.Department_ID
join project_assignments pa
on pa.employee_id = e.employee_id
join project_status p
on p.project_id = pa.project_id
```

### Results/Findings

The analysis results are summarised as follows:
1. The Human resources department is over buget and in the red.
2. However not all the departments are overbudget, hence the company is able to cover all its expenses.

### Recommendations

- Cut the budget of other departments which are not over budget like the marketing department and channel the funding to Human Resources.
- Inhouse investigation of the cause in the over budget of the Human Resources and try reduce the cost which are causing the deficit.
  


