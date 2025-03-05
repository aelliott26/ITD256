# Notes on Anatomy of an SQL Index

## The Index Lead Nodes

- The primary purpose of an index is to provide an ordered representation of the indexed data.
- Moving large amounts of data is very time consuming so the insert statement wold be very slow.
- Logical order is established by a doubly linked list
- By doing this you can insert a new node by changing only 2 of the links instead of every single one. 
- It is easier to change two pointers than a whole set of data

## The Search Tree (B-Tree) Makes the Index Fast

- The index lead nodes are stored in an arbitrary order, and the position on the disk does not corresponf to the logical position according to the index order.
- A balanced search tree - B-Tree
- There is a root that is linked to a branch that is then linked to a leaf and these are linked through pointers,
- Each branc node entry correspond to the biggest value in the respective leaf node.
- The B-Tree is built starting from the leaves out to ensure the distance between the root node and leaf nodes is the same everywhere.
- Once created the database maintains the index automatically. 
- This way of searching is extremely quick

## Slow Indexes, Part I

- Sometimes the tree traversal doesn't work as fast as expected.
- TT can run slow on the leaf node chain as it needs to check the leaf node next to it incase there are other values in it that match the search.
- TT can run slow when accessing the table, as each leaf node might contain many hits (often hundreds)
- Each hit requires an additional table access.
- It is steps 2 and 3 of an index lookup that can slow down the lookup.

### Index Unique Scan
> Performs the tree traverals and follows the leaf node chain to find all matching entries.
>> No more than one entry will match the search entry

### Index Range Scan
> Performs the tree traverals and follows the leaf node chain to find all matching entries.
>> This is used if multiple entries could match the search entry.

## Table Access by Index RowID
> Retirives the row from the table
>> This is used for every matched record from a preceding index scan operation.


