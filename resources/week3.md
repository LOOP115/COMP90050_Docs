## Week 3



### Transaction models (ACID)

#### Atomicity

All changes to data are performed as if they are a single operation. That is, all the changes are performed, or none of them are.

#### Consistency

Data is in a ‘consistent’ state when a transaction starts and when it ends – in other words, any data written to the database must be valid according to all defined rules (e.g., no duplicate student ID, no negative fund transfer, etc.)

#### Isolation

Transaction are executed as if it is the only one in the systems.

#### Durability

The system should tolerate system failures and any committed updates should not be lost.



#### Types of Actions

- **Unprotected actions** - no ACID property
- **Protected actions** - these actions are not externalised before they are completely done. These actions are controlled and can be rolled back if required. These have ACID property.
- **Real actions** - these are real physical actions once performed cannot be undone. In many situations, atomicity is not possible with real actions (e.g., firing two rockets as a single atomic action)



#### Nested Transaction Rules

**Commit rule**

- A subtransaction can either commit or abort, however, commit cannot take place unless the parent itself commits.
- Subtransactions have A, C, and I properties but not D property unless all its ancestors commit.
- Commit of a sub transaction makes its results available only to its parents.

**Roll back Rules**

If a subtransaction rolls back, all its children are forced to roll back.

**Visibility Rules**

Changes made by a subtransaction are visible to the parent only when the subtransaction commits. All objects of parent are visible to its children. Implication of this is that the parent should not modify objects while children are accessing them. This is not a problem as parent does not run in parallel with its children.



#### Transaction Processing Monitor	3.1 P24-26



### Concurrency Control

* **Dekker's algorithm (using code)** - needs almost no hardware support, but the code is very complicated to implement for more than two transactions/processes	3.2 P5
  * needs almost no hardware support although it needs atomic reads and writes to main memory. That is exclusive access of one time cycle of memory access time!
  * the code is very complicated to implement if more than two transactions/process are involved
  * harder to understand the algorithm for more than two process
  * takes lot of storage space
  * uses busy waiting
  * efficient if the lock contention (that is frequency of access to the locks) is low
* **OS supported primitives (through interruption call)** - expensive, independent of number of processes, machine independent
  * OS supported primitives such as lock and unlock
  * through an interrupt call, the lock request is passed to the OS
  * need no special hardware
  * are very expensive (several hundreds to thousands of instructions need to be executed to save context of the requesting process.)
  * do not use busy waiting and therefore more effective
  * All modern processors do support some form of spin locks.
* **Spin locks (using atomic lock/unlock instructions)** – most commonly used
  * Executed using atomic machine instructions such as test and set or swap
  * need hardware support – should be able to lock bus (communication channel between CPU and memory + any other devices) for two memory cycles (one for reading and one for writing). During this time no other devices’ access is allowed to this memory location.
  * use busy waiting
  * algorithm does not depend on number of processes
  * are very efficient for low lock contentions – all DB systems use them



#### Semaphore	3.2 P15-20

Pointer to a queue of processes

If the semaphore is busy but there are no waiters, the pointer is the address of the process that owns the semaphore.

If some processes are waiting, the semaphore points to a linked list of waiting processes. The process owning the semaphore is at the end of this list.

After usage, the owner process wakes up the oldest process in the queue (first in, first out scheduler)

To **avoid convoys**, a process may simply free the semaphore (set the queue to null) and then wake up every process in the list after usage.

In that case, each of those processes will have to re-execute the routine for acquiring semaphore.



#### Deadlocks	3.2 P22-25

* Pre-declare all necessary resources and allocate in a single request.
* Periodically check the resource dependency graph for cycles. If a cycle exists -rollback (i.e., terminate) one or more transaction to eliminate cycles (deadlocks). The chosen transactions should be cheap (e.g., they have not consumed toomany resources).
* Allow waiting for a maximum time on a lock then force Rollback. Many successful systems (IBM, Tandem) have chosen this approach.
* Many distributed database systems maintain only local dependency graphs and use time outs for global deadlocks.



#### Dependencies

![2](img\w3\2.png)

##### Read-Read dependency do not affect isolation

![1](img\w3\1.png)

![3](img\w3\3.png)

A history is serial if it runs one transaction at a time sequentially, or equivalent to a serial history.

A serial history is an isolated history.

**Wormhole theorem:** A history is isolated if and only if it has no wormholes.



**SLOCK (shared lock):** allows other transactions to read, but not write/modify the shared resource

![4](C:\Users\cjhm0\Desktop\COMP90050_Docs\resources\img\w3\4.png)

**Well-formed transactions:**A transaction is well formed if all READ, WRITE and UNLOCK operations are covered by appropriate LOCK operations

**Two phase transactions:** A transaction is two phased if all LOCK operations precede all its UNLOCK operations.



#### Isolation Theorems

* A transactions is a sequence of READ, WRITE, SLOCK, XLOCK actions on objects ending with COMMIT or ROLLBACK.

* A transaction is **well formed** if each READ, WRITE and UNLOCK operation is covered earlier by a corresponding lock operation.

* A history is **legal** if does not grant conflicting grants.

* A transaction is **two phase** if its all lock operations precede its unlock operations.
* **Locking theorem:** If all transactions are well formed (READ, WRITE and UNLOCK operation is covered earlier by a corresponding lock operation) and two-phased (locks are released only at the end), then any legal (does not grant conflicting grants) history will be isolated.
* **Locking theorem (Converse):** If a transaction is not well formed or is not two-phase, then it is possible to write another transaction such that it is a wormhole.
* **Rollback theorem:** An update transaction that does an UNLOCK and then does a ROLLBACK is not two phase.



#### Degrees of Isolation	3.3 P25-26

| Degree | Definition                                                   | Description                                                  |
| ------ | ------------------------------------------------------------ | ------------------------------------------------------------ |
| 3      | A Three degree isolated Transaction has no lost updates, and has repeatable reads. This is “true”isolation. | Lock protocol is two phase and well formed.<br/>It is sensitive to the following conflicts:<br/>write->write; write ->read; read->write |
| 2      | A Two degree isolated transaction has no lost updates and no dirty reads. | Lock protocol is two phase with respect to exclusive locks and well formed with respect to Reads and writes. (May have Non repeatable reads.)<br/>It is sensitive to the following conflicts:<br/>write->write; write ->read; |
| 1      | A One degree isolation has no lost updates.                  | Lock protocol is two phase with respect to exclusive locks and well formed with respect to writes.<br/>It is sensitive the following conflicts:<br/>write->write; |
| 0      | A Zero degree transaction does not overwrite another transactions dirty data if the other transaction is at least One degree. | Lock protocol is well-formed with respect to writes.<br/>It ignores all conflicts. |



#### Actual granular locks in practice

* X: exclusive lock
* S: shared lock
* U: update lock -- Intention to update in the future
* IS: Intent to set shared locks at finer granularity
* IX: Intent to set shared or eXclusive locks at finer granularity
* SIX: a coarse granularity shared lock with an Intent to set finer granularity exclusive locks

To acquire an S mode or IS mode lock on a non-root node, one parent must be held in IS mode or higher (one of {IS,IX,S,SIX,U,X}).

To acquire an X, U, SIX, or IX mode lock on a non-root node, all parents must be held in IX mode or higher (one of {IX,SIX,U,X}).



#### Tree locking and Intent Lock Modes

* None : no lock is taken all requests are granted.
* IS (intention to have shared lock at finer level) allows IS and S mode locks at finer granularity and prevents others from holding X on this node.
* IX (intention to have exclusive lock at finer level) allows to set IS, IX, S, SIX, U and X mode locks at finer granularity and prevents others holding S, SIX, X, U on this node.
* S (shared ) allows read authority to the node and its descendants at a finer granularity and prevents others holding IX, X, SIX on this node.
* SIX (share and intension exclusive) allows reads to the node and its descendants as in IS and prevents others holding X, U, IX, SIX, S on this node or its descendants but allows the holder IX, U, and X mode locks at finer granularity. SIX = S + IX
* U (Update lock) allows read to the node and its descendants and prevents others holding X, U, SIX, IX and IS locks on this node or its descendants.
* X (exclusive lock) allows writes to the node and prevents others holding X, U, S, SIX, IX locks on this node and all its descendants.



#### Compatibility Mode of Granular Locks

![5](C:\Users\cjhm0\Desktop\COMP90050_Docs\resources\img\w3\5.png)



#### Optimistic locking

When conflicts are rare, transactions can execute operations without managing locks and without waiting for locks - **higher throughput**

* Use data without locks
* Before committing, each transaction verifies that no other transaction has modified the data (by taking appropriate locks) – **duration of locks are very short**
* If any conflict found, the transaction repeats the attempt
* If no conflict, make changes and commit



#### Snapshot Isolation	3.4 P19

#### Time stamping	3.4 P20-21
