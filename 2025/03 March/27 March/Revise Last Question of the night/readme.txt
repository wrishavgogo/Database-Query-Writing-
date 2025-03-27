Link : https://leetcode.com/problems/second-highest-salary/

Question : 

Table: Employee

+-------------+------+
| Column Name | Type |
+-------------+------+
| id          | int  |
| salary      | int  |
+-------------+------+
id is the primary key (column with unique values) for this table.
Each row of this table contains information about the salary of an employee.
 

Write a solution to find the second highest distinct salary from the Employee table. If there is no second highest salary, return null (return None in Pandas).

The result format is in the following example.

 

Example 1:

Input: 
Employee table:
+----+--------+
| id | salary |
+----+--------+
| 1  | 100    |
| 2  | 200    |
| 3  | 300    |
+----+--------+
Output: 
+---------------------+
| SecondHighestSalary |
+---------------------+
| 200                 |
+---------------------+
Example 2:

Input: 
Employee table:
+----+--------+
| id | salary |
+----+--------+
| 1  | 100    |
+----+--------+
Output: 
+---------------------+
| SecondHighestSalary |
+---------------------+
| null                |
+---------------------+

Query : 

Its mentioned in the pdf follow that 


Offset function is new , 

in the query at the end use offset k - 1 , to skip k - 1 rows and the kth row will be your answer 

below is the actual soln if you are having doubts read the pdf for explanation 


select ifnull(

    # subquery hence wrap around parathesis
    # be kind to sql compiler
    (
        select distinct(salary) from Employee 
        order by salary desc
        limit 1 offset 1
        # you can do offset k - 1 solves for kth highest salary
    )
    , 
    null
) as SecondHighestSalary


// we learnt offset in page / offset  based pagination 

