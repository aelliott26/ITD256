# CockroachDB

## What is it?
- CockroachDB is a distributed SQL database management system.
- This basically means that the data is distributed among many devices all linked together.
- Even though the data is distributed CockroachDB allows you to query the data as if it was all in one place.

## Why use it?
- One main reasons to use CockroachDB is for its huge horizontal scaling, as you can add a huge amount of devices.
- The other main reason to use CockroachDB is for its high fault tolerence
- It is super difficult to lose all the data as it is stored across many devices
- Google uses a similar system, but CockroachDB does not require special hardware to complete the same task as Google

## What to use it for?
- CockroachDB can be used for massive horizontal scaling, and you can constantly add more devices without reaching a bottleneck.
- It has high availability due to the data being replicated among a lot of different devices.
- It is good for storing data worldwide, as data can be stored locally
- It has a super high fault tolerance, so it is hard to get taken down. 

### Examples of companies that use it
- Netflix
- Uber
- eBay
- Amazon Web Services
- Google

## CockroachDB vs Postgres
| Feature              | Distributed SQL                      | PostgreSQL                                  |
|----------------------|--------------------------------------|---------------------------------------------|
| **Architecture**     | Multi-node, globally distributed     | Single-node, extendable through replication |
| **Scalability**      | Horizontally scalable                | Usually only vertically scalable            |
| **Fault Tolerance**  | Built-in high availability           | Can be configured with replication          |
| **Consistency**      | Usually its ACID-compliant           | Its ACID-compliant                          |
| **Geo-Distribution** | Optimized for multiple regions       | Single-region or manually replicated        |
| **Use Cases**        | Global applications, high traffic    | Traditional relational database needs       |

