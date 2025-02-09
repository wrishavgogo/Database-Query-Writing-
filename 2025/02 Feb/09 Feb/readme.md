Question Link : https://leetcode.com/problems/duplicate-emails/description/ 

Write a solution to report all the duplicate emails. Note that it's guaranteed that the email field is not NULL.

Return the result table in any order.

The result format is in the following example.

 

Example 1:

Input: 
Person table:
+----+---------+
| id | email   |
+----+---------+
| 1  | a@b.com |
| 2  | c@d.com |
| 3  | a@b.com |
+----+---------+
Output: 
+---------+
| Email   |
+---------+
| a@b.com |
+---------+



My Experience : 

I wrote something like this : 


select p.email AS Email from Person p where count(p.email) > 1 ; 

Error : Invalid use of group function

I feel some group by kind of shit needs to happen here and there and i got no idea of group by . 


***************** COUNT() function , 


So first we learnt about the COUNT functionality 

id	name	email
1	John	john@email.com
2	Alice	alice@email.com
3	Bob	NULL
4	Mike	NULL

Lets say we have the above table , 

Now if we do 
SELECT COUNT(*) FROM table1 --> it returns 4 , it does not care if we have nULL or any value 

But if we do 
SELECT COUNT(email) FROM table1 --> it returns 2 , it only returns non null rows which we have in the column . 






********** DISTINCT Keyword & COUNT(DISTINCT columnName) .... together 

id	name	email
1	John	john@email.com
2	Alice	alice@email.com
3	Bob	NULL
4	Mike	NULL

Query 1 : SELECT DISTINCT email From table1 ; 

Output is :- 
john@email.com
alice@email.com
NULL


Query 2 : SELECT COUNT(DISTINCT email) from table1 ; 

Output is :- 
2 ( it does not count the distinct email ) 

count function ignores the NULL values . 

REMEMBER :-   DISTINCT_COUNT  , no function like that exists , DISTINCT is keyword which returns DISTINCT Values of column and COUNT returns their count skipping NULL values 


Now while doing this question , i was confused that how are COUNT(*) and GROUP BY queries are communicating with each other , 

Then i got to know that there is a BODMAS RULE in SQL query execution as well . 
There is an ordering in sql query execution . 
Look into the PDF which i will upload and you will know what command is executed after which one . 

I would have uploaded a PDF with examples to show you the order of execution . 

Go Read that and then the answer for this question is also written there . 






