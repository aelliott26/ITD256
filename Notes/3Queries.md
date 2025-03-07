# 3 Queries

## Sequential Scan

### Query

`SELECT first_name FROM employees WHERE first_name = 'Kmuf';`

### Query Plan
```
                         QUERY PLAN                          
-------------------------------------------------------------
 Seq Scan on employees  (cost=0.00..15536.00 rows=2 width=5)
   Filter: ((first_name)::text = 'Kmuf'::text)
```

### Explanation

This query searches through every row to find the rows that have the first name Kmuf.

## Index Scan
### Query
`SELECT first_name FROM employees WHERE employee_id = 1;`
### Query Plan
```
                                  QUERY PLAN                                  
------------------------------------------------------------------------------
 Index Scan using employees_pk on employees  (cost=0.29..8.31 rows=1 width=5)
   Index Cond: (employee_id = '1'::numeric)
```
### Explanation

This query searches through the index for 1 and then goes through the table to match the index to the first name.

## Index Only Scan

### Query
`SELECT COUNT(*) FROM employees;`
### Query Plan
```
                                           QUERY PLAN                                            
-------------------------------------------------------------------------------------------------
 Aggregate  (cost=2859.29..2859.30 rows=1 width=8)
   ->  Index Only Scan using employees_pk on employees  (cost=0.29..2609.29 rows=100000 width=0)
```
### Explanation
This only uses the index as it counts all the elements in the index.