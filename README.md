# 2023 Winter - COMP90050 - Advanced Database Systems



## [Week 1](resources/week1.md)

#### [Part 1](lectures/week1/1.1.pdf)

* Introduction to the subject, performance factors of DB
* Disk drives and their components
* Memory hierarchy

#### [Part 2](lectures/week1/1.2.pdf)

* Types of databases
* Different database architectures

#### [Part 3](lectures/week1/1.3.pdf)

- Fault tolerance introduction
- RAID
- Failvote, Failfast
- Communication reliability

#### [Part 4](lectures/week1/1.4.pdf)

* Disk writes for consistency
* Duplex write, logged write
* CRC

#### [Live 1](lectures/week1/live1.pdf)

#### Tutorial

* [Slides](tutorials/slides/slide1.pdf)

* [Sheet](tutorials/sheets/t1.pdf) & [Solutions](tutorials/sheets/t1s.pdf)



## [Week 2](resources/week2.md)

#### [Part 1-2](lectures/week2/2.1.pdf)

* Database engine
* Background: relational algebra and join
* Join algorithms
* Query costs 
* Advanced query optimization

#### [Part 3](lectures/week2/2.2.pdf)

* Managing query costs in practice

#### [Part 4-5](lectures/week2/2.3.pdf) / [Part 6](lectures/week2/2.4.pdf)

* Indexing concepts
* Different types of indexes: B+tree, hash index, bitmap index, Quadtree, R-tree,
* Using indexes in SQL

#### [Live 2](lectures/week2/live2.pdf)

#### Tutorial

* [Slides](tutorials/slides/slide2.pdf)
* [Sheet](tutorials/sheets/t2.pdf) & [Solutions](tutorials/sheets/t2s.pdf)

#### Quiz 1	[1-2](quizzes/1.1.png) [3-4](quizzes/1.2.png)

#### Quiz 2	[1-3](quizzes/2.1.png) [4](quizzes/2.2.png)



## Week 3

#### [Part 1-2](lectures/week3/3.1.pdf)

- Transactions
- Types of transactions
- Transaction processing monitor

#### [Part 3](lectures/week3/3.2.pdf)

- Concurrency control
- Exclusive access
- Spin locks
- Atomic operations to get and release locks
- Semaphore
- Convoy
- Deadlocks

#### [Part 4](lectures/week3/3.3.pdf)

- Isolation concepts
- Dependency relations
- Wormhole
- Isolation theorems

#### [Part 5](lectures/week3/3.4.pdf)

- Granular locks
- Optimistic locking
- Snapshot isolation
- Timestamping

#### [Live 3](lectures/week3/live3.pdf)

#### Tutorial

* [Slides](tutorials/slides/slide3.pdf)
* [Sheet](tutorials/sheets/t3.pdf) & [Solutions](tutorials/sheets/t3s.pdf)

#### [Quiz 3](quizzes/3.png)

#### Quiz 4	[1-2](quizzes/4.1.png) [3-4](quizzes/4.2.png)



## Week 4

#### [Part 1-2: Crash recovery](lectures/week4/4.1.pdf)

- Buffer pool and disk transfers
- Logging and WAL for crash recovery
- Checkpointing
- Simple transaction abort
- Transaction commit
- ARIES algorithm

#### [Part 3: Backups](lectures/week4/4.2.pdf)

- Remote backups
- Shadow paging
- Backup design strategy

#### [Part 4: Distributed databases](lectures/week4/4.3.pdf)

- Atomicity in distributed DB
- Two phase commit protocol
- Concurrency in distributed DB
- Transactions with replicated data

#### [Part 5: Distributed databases continued](lectures/week4/4.4.pdf)

- CAP theorem
- Different types of consistency
- Dynamic trade-off between consistency and availability
- Data partitioning for trade-off
- BASE properties
- NoSQL and BASE

#### [Part 6: Specialised DB - data warehousing](lectures/week4/4.5.pdf)

#### [Live 4](lectures/week4/live4.pdf)

#### Tutorial

* [Slides](tutorials/slides/slide4.pdf)
* [Sheet](tutorials/sheets/t4.pdf) & [Solutions](tutorials/sheets/t4s.pdf)

#### Quiz 5	[1-2](quizzes/5.1.png) [3-4](quizzes/5.2.png)
