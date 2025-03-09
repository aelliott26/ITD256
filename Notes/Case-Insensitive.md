# Notes on Case-Insensitive Search Using Upper or Lower

- You can use `Upper` as a way to search through strings where you do not know the capitalization.
- The default collations used by SQL Server and MYSQL do not distinguish between upper and lower case letters, they are case-insensitive by default.
- When using `UPPER` it will use a full table scan even if there is an index on the collumn you are searching, because the database does not see it as a search through an index.
- To use an index we need one on `UPPER(last_name)` and not `last_name`
- An index whose definition contains functions or expressions is a so-called *function-based index* (FBI).
- A fuction based index first applies the function and then sorts the result into an index.
- You can only use an FBI if the query matches exatly with what the index was built for.
- Contradicting estimates indicate a problem with the database statistics.
- To fix contradicting estimates simply update the statistics.
- MYSQL and SQL Server don't allow for FBIs, so a workaround is to create a new column and then index on the column.
