# HDP_Test_Q1
Data, process and output of   Hadoop test Question 1

Q1: 
Calculate average the salary of each 'Senior' employee. Please upload the final CSV along with the code and jar files(if any) to your github and provide the link below. The CSV should be formatted as empid, Name, Designation, Avg_salary


Here In this question we have to get the all "Senior" employees record from employees table along with emp.no and salary and designation.

To get this done we have used below quries as:

Query one:

"" 
INSERT OVERWRITE LOCAL DIRECTORY '/home/vishnu/Documents/1stquestion_csv' select e.first_name,t.title from employees e left join titles t on e.emp_no = t.emp_no where t.title like '%Senior%';

""

Using above query we are getting the all Senior employees list from the title table under employees database.
here we have used leFt join to get the employee first_name  from employee table, and made left join on Title table on emp.no column and taken the all employee records which have Senior string in it.

and then we taken average salary of all above output record with Senior employee records.
Here under senior category we found two types of senior emplyees are present in given data.
1. Senior Staff
2.Senior Engineer.
Using these both emploee list along with emp.no, name, salary we have performed average function on it and got average salary of senior staff and senior engineer 


1. Query to get average salary of Senior staff emloyees:

INSERT OVERWRITE LOCAL DIRECTORY '/home/vishnu/Documents/Q2_senior_Stuff_avg' select avg(s.salary) from employees e left join titles t on (e.emp_no = t.emp_no) left join salaries s on (e.emp_no = s.emp_no) where t.title like '%Senior Staff%';

In above query we have performed action to get average salary on salaries table and made 2 left joines on it.
one left join on titles table and another one left join on the salaries table  both on emp.no column 
 and the output of this quesry stored in local derictory in csv format.
 
 2.Quesry to get average saalry of Senior engineer employees:
 
 hive> INSERT OVERWRITE LOCAL DIRECTORY '/home/vishnu/Documents/Q1_senior_Engineer_CSVavg' select avg(s.salary) from employees e left join titles t on (e.emp_no = t.emp_no) left join salaries s on (e.emp_no = s.emp_no) where t.title like '%Senior Engineer%';
 
 Same , in above query we have performed average function on salaries table along with two left join on Titles and salaries on both emp.no column with getting matching employee records which have Senior Engineer.
 
 
 In this way we get the average salary of all Senioer ( Senioer staff and Senior Engineer) employees along with the emp.no , Emp name, Designation and Average salary.
 
 



