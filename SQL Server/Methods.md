## Function

It is used to compute values and return them (mostly scalars). For instance:
+ SUM
+ COUNT
+ LEN

Function will not make an permanent change to the environment. 

Only SELECT is allowed in Functions.

Usually Function should have at least one scalar input and a return scalar value (can have Tabled Values).

Functions can be called in a SELECT, WHERE or in a Stored Procedure.

## Stored Procedure

It is like a mini program. 

It can change the environment. 

Can use INSERT, UPDATE or DELETE.

Stored procedures can not be called in SELECT or WHERE statements.