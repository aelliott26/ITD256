# Notes on Join

## The Join Operation
- The join operation transforms data from a normalized model into a denormalized for that suits a specific processing purpose.
- Join algorithms only process two tables at a time.
- Join order has no impact on final result, though it changes the time required to join the tables.
- The optimizer will evaluate all possible join order permutations and select the best one.

## Nested Loops
- Nested loops in join use two nested queries, one to fetch the results and one for each row from the driving query to fetch corresponding data from the other table. 
- Nested loops is a join algorithm.
- Manualy using nested selects is a troublesome approach because network latencies occur on top of disk latencies(its slow)
- N + 1 problem is a problem where it executes N+1 selects in total if the driving query returns N rows.
- Indexing for a nested loops join is a function based index
- An SQL join is faster than the nested selects approach because it avoids a lot of network communication
- The number ofdatabase round trips is more important for the repsonse time than the amount of data transferred.
- The eager fetching is the ability to load subclase data and related objects along with the base instances being queried.
- Different ORM tools offer different ways to control join behavior
- Nested loops are a good option if the driving query returns a small result set.
