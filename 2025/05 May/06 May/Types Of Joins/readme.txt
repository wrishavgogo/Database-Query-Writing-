I will write queries and my understanding about the joins 
Mainly 5 main types of Joins are there


CROSS JOIN -> m*n ( on condition not required)

Below everyone requires ON condition 

INNER JOIN -> intersection , there is no Left inner join or Right Inner join , Inner join is just the intersection remember that 
LEFT OUTER JOIN ( same as LEFT JOIN)  ->  shows all the rows of Left Table and if no match just populated null in the right side
RIGHT OUTER JOIN (same as RIGHT JOIN ) -> shows all the rows of Right Table and if no match just populated null in the left Side

There is No such thing as only OUTER JOIN 
I was thinking OUTER JOIN is ( A UNION B ) - ( A INTERSECTION B)

there is Only FULL OUTER JOIN 
in which 
both the rows of the left and right table are there 
, its just that LEFT and RIGHT table's rows which are together are mapped 
