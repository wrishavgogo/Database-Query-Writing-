Link : https://leetcode.com/problems/delete-duplicate-emails/description/ 

Question : 196. Delete Duplicate Emails

+-------------+---------+
| Column Name | Type    |
+-------------+---------+
| id          | int     |
| email       | varchar |
+-------------+---------+
id is the primary key (column with unique values) for this table.
Each row of this table contains an email. The emails will not contain uppercase letters.
 

Write a solution to delete all duplicate emails, keeping only one unique email with the smallest id.

For SQL users, please note that you are supposed to write a DELETE statement and not a SELECT one.

For Pandas users, please note that you are supposed to modify Person in place.

After running your script, the answer shown is the Person table. The driver will first compile and run your piece of code and then show the Person table. The final order of the Person table does not matter.

The result format is in the following example.

 

Example 1:

Input: 
Person table:
+----+------------------+
| id | email            |
+----+------------------+
| 1  | john@example.com |
| 2  | bob@example.com  |
| 3  | john@example.com |
+----+------------------+
Output: 
+----+------------------+
| id | email            |
+----+------------------+
| 1  | john@example.com |
| 2  | bob@example.com  |
+----+------------------+
Explanation: john@example.com is repeated two times. We keep the row with the smallest Id = 1.


Solution : 

It came to my mind to use the MIN aggregate function , whenever we are using group by , it has to be applied with a group by function 


delete from Person where id not in ( 

select id from ( 
select  p.email as mail , MIN(p.id) as id from  
Person p  group by p.email  
) as temp
    
    
);

Mistake or rather learning : 

First time i wrote the query it was something like 


delete from Person where id not in ( 

select   MIN(p.id)  from  
Person p  group by p.email  
    
);

this was throwing an error in mysql , 

in MYSQL you have to give an alias name for the temporatey table , which you have to provide in the NOT IN ( ) place 

************ Learning **********************

I saw someone else's solution , where i learnt about WITH keyword , yesterday Mayank was also talking about it , so it is basically used to give an alias name 
for a temporary view that you created 

WITH TEMP AS (
    SELECT MIN(id) AS MIN_ID, EMAIL
    FROM PERSON
    GROUP BY EMAIL
)


WITH <your alias name> AS ( 
--- write the query to generate the view ) 

WITH TEMP AS (
    SELECT MIN(id) AS MIN_ID, EMAIL
    FROM PERSON
    GROUP BY EMAIL
)

DELETE FROM PERSON WHERE ID NOT IN (SELECT MIN_ID FROM TEMP) 

utilize this in future
