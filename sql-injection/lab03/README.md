# Lab 03

## SQLi - Product category filiter

**Gaol**: determine the number of clumns returned by the query.

**Background (Union)**
table1 | table2
...A  B | C  D
...1, 2 | 2, 3
...3, 4 | 4, 5

Query #1:

> SELECT A, B FROM TABLE1

1,2
3,4

Query #2:

> SELECT A, B FROM TABLE1 UNION SELECT C,D FROM TABLE2

1,2
3,2
2,3
4,5

**Rules**
- The number and the order of the colums must be the same in all queries
- The data type must be comatible

**SQLi attack (method #1)**

> SLECT ? FROM TALBE1 UNION SELECT NULL

- error -> incorrect number of columns (Internal Server Error)

> SELECT ? FROM TALBE1 UNION SELECT NULL, NULL, NULL

- 200 response cod -> correct number of columns

**SQLi attack (method #2)**

>  SELECT A, B FROM TABLE1 ORDER BY 3