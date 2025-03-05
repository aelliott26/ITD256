# Notes on The Equality Operator 

## Primary Keys
- The primary key lookup is the most simple and common where clause
- The database automatically creates an index for the primary key.
- When using the where clause with a primary key it uses an Index Unique Scan as it is only looking for one unique value
- If the query where you had a where clause on a primary key is running slow it is not the primary key lookup at fault it is finding any aditional data with that primary key. (in the examples this would be first and last name)

## Concatenated Indexes
- If there are multiple columns for a primary key the database creates an index on all primary key columns (concatenated index)
- The column order of a concatenated index has a significant impact on its usability
- When a query uses the complete primary key the database can use an Index Unique Scan no matter how many columns the index has
- If you do not use the complete primary key in a query it will sarch through a Table Access Full which takes a long time
- The ordering of a two column index is like the ordering of a telephone directory
- The single index solution is perferable over the two index solution

## Slow Indexes, Part II
- Changing an index may affect all queries on the indexed table.
- If there are multiple access paths avilible it is the optimizer's job to choose the best one.
- When making an index change, compare an execution plan before an after to help analyse its effects.
- Using an index can be slower than a full Table Scan but this means there is an issue with the index
- To figure out why an index is running slow you can breakdown an execution plan and follow it along its path
- The example with the employees database runs slow due to the index lookup returning many RowIDs.
- If the cost value of using the index is the same or higher than a full table scan the optimizer will automatically use the full table scan
- A slow index does not mean indexing is the wrong solution
- Using an index also does not mean a statement is executed in the best way possible