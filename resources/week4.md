## Week 4



#### Buffer Caches (pool)

1. Data is stored on disks
2. Reading a data item requires reading the whole page of data (typically 4K or 8K bytes of data depending on the page size) from disk to memory containing the item.
3. Modifying a data item requires reading the whole page from disk to memory containing the item, modifying the item in memory and writing the whole page to disk.
4. Steps 2 & 3 can be very expensive and we can minimize the number of disk reads and writes by storing as many disk pages as possible in memory (buffer cache) –this means always check in buffer cache for the disk page of interest if not copy the associated page to buffer cache and perform the necessary operation.
5. When buffer cache is full we need to evict some pages from the buffer cache in order fetch the required pages from the disk .
6. Eviction needs to make sure that no one else is using the page and any modified pages should be copied to the disk.
7. Since several transactions are executing concurrently this requires additional locking procedures using latches. These latches are used only for the duration of the operation (e.g. READ/WRITE) and can be released immediately unlike record locks which have to be kept locked until the end of the transaction.

**fix(pageid)**

* reads pages from disk into the buffer cache if it is not already in the buffer cache
* fixed pages cannot be dropped from the buffer cache as transactions are accessing the contents

**unfix(pageid)**

* The page is not in use by the transaction and can be evicted as far as the unfix calling transaction is concerned. (We need to check to see that no one else wants the page before it can be evicted)



#### Write-Ahead Logging (WAL)

The Write-Ahead Logging Protocol:

1. Must force the log record which has both old and new values for an update before the corresponding data page gets to disk (stolen).
2. Must write all log records to disk (force) for a Xact before commit.

* guarantees Atomicity because we can undo updates performed by aborted transactions and redo those updates of committed transactions.
* guarantees Durability.



#### WAL & Log

* Each log record has a unique Log Sequence Number (LSN).
  * LSNs always increasing.
* Each data page contains a pageLSN.
  * The LSN of the most recent log record for an update to that page.
* System keeps track of flushedLSN.
  * The max LSN flushed so far.
* WAL: Before a page is written
  * to disk make sure: pageLSN <= flushedLSN



<img src="img\w4\1.png" alt="1"/>



#### Crash Recovery	4.1 P35-41

Start from a checkpoint (found via master record).

Three phases. Need to:

* Figure out which Xacts committed since checkpoint, which failed (**Analysis**).
* **REDO** all actions. (repeat history)
* **UNDO** effects of failed Xacts.



#### Remote Backup Systems	4.2 P3-6

#### Shadow Paging	4.2 P7-12



#### Two-phase Commit	4.3 P4-8

#### Concurrency control in distributed DBs	4.3 P9-18



#### CAP

**Consistency:** every node always sees the same data at any given instance (i.e., strict consistency)

**Availability:** the system continues to operate, even if nodes crash, or some hardware or software parts are down due to upgrades

**Partition Tolerance:** the system continues to operate in the presence of network partitions

**CAP theorem: any distributed database with shared data, can have at most two of the three desirable properties, C, A or P**



#### Types of Consistency

* Strong Consistency
  * After the update completes, any subsequent access will return the same updated value.
* Weak Consistency
  * It is not guaranteed that subsequent accesses will return the updated value.
* Eventual Consistency
  * Specific form of weak consistency
  * It is guaranteed that if no new updates are made to object, eventually all accesses will return the last updated value (e.g., propagate updates to replicas in a lazy fashion)
  * Causal consistency
    * Processes that have causal relationship will see consistent data
  * Read-your-write consistency
    * A process always accesses the data item after it’s update operation and never sees an older value
  * Session consistency
    * As long as session exists, system guarantees read-your-write consistency
    * Guarantees do not overlap sessions
  * Monotonic read consistency
    * If a process has seen a particular value of data item, any subsequent processes will never return any previous values
  * Monotonic write consistency
    * The system guarantees to serialize the writes by the same process
  * In practice
    * A number of these properties can be combined
    * Monotonic reads and read-your-writes are most desirable



#### BASE

**Basically Available:** the system guarantees Availability

**Soft-State:** the state of the system may change over time

**Eventual Consistency:** the system will eventually become consistent



#### CAP -> PACELC

If there is a **partition (P)**, how does the system trade off **availability and consistency (A and C)**; **else (E)**, when the system is running normally in the absence of partitions, how does the system trade off **latency (L) and consistency (C)**?

* PA/EL Systems: Give up both Cs for availability and lower latency
  * Dynamo, Cassandra, Riak
* PC/EC Systems: Refuse to give up consistency and pay the cost of availability and latency
  * BigTable, Hbase, VoltDB/H-Store
* PA/EC Systems: Give up consistency when a partition happens and keep consistency in normal operations
  * MongoDB
* PC/EL System: Keep consistency if a partition occurs but gives up consistency for latency in normal operations
  * Yahoo! PNUTS

