## Week 1



### Part 1

#### Introduction to the subject, performance factors of DB	1.1 P2-6

<img src="img\w1\1.png" alt="1"  style="zoom:80%;" />

#### Disk drives and their components	1.1 P7-16

* ##### HDD

<img src="img\w1\2.png" alt="2"  />

<img src="img\w1\3.png" alt="3"  />



* ##### SSD (Solid-State Drive)

  * No moving parts like Hard Disk Drive (HDD)
  * Silicon rather than magnetic materials
  * No seek/rotational latency
  * No start-up times like HDD
  * Runs silently
  * Random access of typically under 100 micro-seconds compared 2000 -3000 micro-seconds for HDD
  * Relatively very expensive, thus did not dominate at all fronts yet
  * Certain read/write limitations plagued it for years

<img src="img\w1\4.png" alt="4"  />



* ##### Moore’s law: memory chip capacity doubles every 18 months since 1970

<img src="img\w1\5.png" alt="5"  />



* ##### Joy’s law for processors: processor performance doubles every two years since 1984

<img src="img\w1\6.png" alt="6"  />

* ##### Storage Units

<img src="img\w1\7.png" alt="7"  />



#### Memory hierarchy	1.1 P17-22

<img src="img\w1\8.png" alt="8"  style="zoom:80%;" />

<img src="img\w1\9.png" alt="9"  style="zoom:80%;" />



#### Communication Costs	Live1 P21

Increasingly, another item to model the cost of is data transfer:

**transmit time = (distance/c) + (message_bits/bandwidth)**

c = speed of light (200 million meters/sec) with fibre optics

This means we can no longer reduce latency on contemporary hardware further and increasingly the motto is that **the message length should be large to achieve better utilization**.



### Part 2

#### Types of databases	1.2 P2-9

* ##### Simple file: As a plain text file. Each line holds one record, with fields separated by delimiters (e.g., commas or tabs)

  * Usually very fast for simple applications but can be slow for complex applications
  * Can be less reliable
  * Application dependent optimisation
  * Very hard to maintain them (concurrency problems)
  * Many of the required features (that exist in relational databases) need to be incorporated - unnecessary code development and potential increase in unreliability

* ##### RDBS: As a collection of tables (relations) consisting of rows and column. A primary key is used to uniquely identify each row.

  * Very reliable(consistency of data –we will learn more later)
  * Application independent optimisation
  * Well suited to many applications, very fast due to large main memory machines and SSDs.
  * Some RDB also support Object Oriented model e.g., Oracle, DB2, and XML data+queries
  * Can be slow for some simple applications

* ##### Object oriented: Data stored in the form of ‘objects’ directly (like OOP)

  * Stores as objects directly, not tables
  * May contain both data (attributes) and methods – like OOP
  * Can be slow on some applications
  * Reliable
  * Limited application independent optimisation
  * Well suited for applications requiring complex data
  * Unfortunately, many commercial systems started did not survive the force of RDB technology and basically disappeared from the market.

* ##### No-SQL: Non relational – database modelled other than the tabular relations. Covers a wide range of database types.

  * Flexible/ no fixed schema (unlike RDB)
  * Provides a mechanism for storage and retrieval of data modelled in means other than the tabular relations
  * Simple design, should linearly scale
  * NoSQL has compromise consistency and allows replications
  * Most NoSQL databases offer "eventual consistency”, which might result in reading data from an older version, a problem known as stale reads

* ##### Type of NoSQL databases

  * Key Value
    * Stores data as a collection of key–value pairs, where each key is unique
    * Why useful - Many applications do not require the expressive functionality of transaction processing – e.g. Web search, Big Data Analytics can use MapReduce technology.
    * Can be seen as a type of NoSQL database
    * Used for building very fast, highly parallel processing of large data - MapReduce and Hadoop are examples
    * Atomic updates at Key-value pair level (row update) only.
  * Document-Based
  * Column-Based
  * Graph-Based

* ##### Deductive database systems (DDBS)

  * Allows recursion
  * Most of the application can be developed entirely using DDBS
  * There are no commercially available systems like RDBs
  * Many applications do not require the expressive power of these systems (e.g. many commerce related applications)
  * Many RDBs do provide some of the functionality –e.g. supporting transitive closure operation (a form of recursion in SQL2).
  * E.g.
    path(X,Y) :- edge(X,Y).
    path(X,Y) :- edge(X,Z), path(Z,Y).

#### Different database architectures	P10-21

* ##### Centralized: Data stored in one location

  * Data in one location
  * System administration is simple
  * Optimisation process is generally very effective
  * PC/Cluster Computing/data centres are examples of this
  * E.g. Client-server architecture that uses a centralized database server
    * A central server with a central DB in one location (but client and server can be in different locations)
    * Client generally provides user interfaces for input and output
    * Server provides all the necessary database functionality
    * System administration is relatively simple
    * System recovery is similar to centralised systems

* ##### Distributed: Data distributed across several nodes, can be in different locations

  * Data is distributed across several nodes in different locations
  * Nodes are connected by network
  * System provides concurrency, recovery and transaction processing
  * System administration is very hard – usually with a single resource manager
  * Crash recovery is complicated
  * There are usually data replication -- potential inconsistency

* ##### WWW: Stored all over the world, several owners of the data

  * Data is stored in many locations
  * Several owners of data - no certainty of data availability or consistency
  * Optimisation process is generally very ineffective
  * Evolving database technology -- no standards have been developed except in case of XML/http and some protocols for accessing data
  * Security could be a potential problem
  * Notions of Transactions is much more difficult to enforce

* ##### Grid: Like distributed, but each node manages own resource; system doesn’t act as a single unit.

  * Very similar to distributed database systems
  * Data and processing are shared among a group of computer systems which may be geographically separated.
  * Usually designed for particular purpose – e.g., a scientific application
  * Administration of such systems are done locally by each owner of the system
  * Reliability and security of such systems are not well developed or studied.
  * Grid systems model is more or less outdated by Cloud Computing model

* ##### P2P: Like grid, but nodes can join and leave network at will (unlike Grid)

  * Data and processing is shared among a group of computer systems which may be geographically separated as in Grid Database systems
  * Computer nodes can join and leave the network at will unlike in Grid Databases => much harder to design transaction models
  * Usually designed for particular usage – e.g. a scientific application
  * Administration of such system is done by the owners of the data

* ##### Cloud: Generalization of grid, but resources are accessed on-demand

  * Cloud computing offers online computing, storage and a range of new services for data and devices that are accessible through the Internet.
  * User pays for the services just like phone services, electricity, etc.
  * Huge potential for developing applications with minimal infrastructure costs
  * Cloud services offered in several forms:
    * Iaas – Infrastructure as a service (provide virtual machines)
    * Paas – Platform as a service (Provide environment like Linux, Windows, etc.)
    * Saas – Software as a service (Specific applications like RDB, Mail, etc.)
  * E.g. Amazon Web Services    1.2 P19-21

#### More on Storage	Live1 P27-30

* Storage today does not come as one disk
* They come as a system and increasingly complex
* Storage systems can determine the performance and also fault tolerance of a database
* In Database Management Systems (DBMSs), rarely data is stored in one location as well
* Storage is now much larger, involves multiple disks, and accessed over a network and at many sites

##### Storage Systems

* RAID : Redundant Array of Independent Disks – different ways to combine multiple disks as a unit
* Storage Area Networks    Live1 P29-30
  * A dedicated network of storage devices
  * Storage can be organized as RAID (Redundant Array of Inexpensive Disks) systems.
  * Storage is partitioned and allocated to each system and can also be shared.
  * They are used for shared-disk file systems
  * Automated backup functionality
  * It was the fundamental storage for data center type systems with mainframes for decades
  * Different versions evolved over time to allow for more data, but fundamentals are the same even today
  * But in short, failure probability of one disk is different than 100s of disks - which requires design choices



### Part 3

#### Fault tolerance introduction	1.3 P3-6

##### The property that enables a system to continue operating properly in the event of the failure of some of its components.

* P(A) = probability of an event A is happening in a certain period.
  * P(A and B) = probability both A and B happening in that period = P(A) * P(B) assuming A and B are independent events.
  * **P(A or B)** = P(A) + P(B) - P(A and B) = P(A) + P(B) -P(A)*P(B) [Assuming A and B are independent] ≈ **P(A) + P(B)** [if P(A) and P(B) are very small]

* Mean time to event A is, **MT(A) = 1/P(A)**
  * If events A, B, have mean time MT(A), MT(B), then the mean time to the first event, **MT(A or B) = 1/P (A or B)**
  * If there are n events, each with the same probability p, then
    * Probability that one of the events occur = p + p + …. (n times) = **n*p** [assuming p is small]
    * Mean time to one of the events (i.e., mean time to the first event) = 1/(n*p) = (1/p) * (1/n) = m * (1/n) = **m/n**

* ##### A system's life cycle

<img src="img\w1\10.png" alt="10"  />



#### RAID	1.3 P7-14

##### Redundant Array of Independent Disks – different ways to combine multiple disks as a unit for fault tolerance or performance improvement, or both of a database system

Terminologies:

* A means Block (4K or 8K bytes of storage)
* MTTF = Mean Time To Failure
* b means bit
* B means Byte
* P is parity
* Parity (or check bits) are used for error detection
* ⊕ is an exclusive-or operator

| Type                                       | Features                                                     |
| ------------------------------------------ | ------------------------------------------------------------ |
| Raid 0                                     | A0, A1, A2, ... are contiguous blocks of data of a file<br />• Provides balanced I/O of disk drives –throughput ~ doubles<br/>• Any disk failure will be catastrophic and MTTF reduces by a factor of 2<br/>**Higher throughput at the cost of increased vulnerability to failures** |
| Raid 1 (mirroring)                         | • Provides higher read throughput but lower write throughput (half of the total speed – i.e. single disk speed)<br/>• Half storage utilization.<br/>• MTTF increases substantially (quadratic improvement – i.e. MTTF<sup>2</sup>)<br/>**Continues to operate as long as 1 disk is functional** |
| RAID 2 (bit level striping)                | • Striping takes place at bit level<br/>• Provides higher transfer rate (double the single disk)<br/>• MTTF reduced by half as in RAID 0<br/>• rarely used |
| RAID 3 (Byte level striping)               | B0, B1, B2, B3, .. are bytes of data of file<br/>• Striping takes place at byte level<br/>• Rarely used<br/>• Provides higher transfer rate as in RAID 0<br/>• P0 is parity for bytes B0 and B1<br/>• Pi = B<sub>2i</sub> ⊕ B<sub>2i+1</sub><br/>MTTF increases substantially (1/3 of RAID1 = MTTF<sup>2</sup>/3), as 1 disk failure can be recovered from the data of the other 2 disks |
| RAID 4 (Block level level striping)        | • Striping takes place at block level<br/>• Dedicated disk for parity blocks<br/>• Provides higher throughput but very slow writes. Disk3 has more writes as Parity needs to be updated for every data write.<br/>• MTTF increases substantially (same as RAID3)<br/>•P<sub>i</sub> = A<sub>2i</sub> ⊕ A<sub>2i+1</sub> |
| RAID 5 with 3 disks (Block level striping) | • A0, A1, A2, A3, .. are contiguous blocks of data of a file<br/>• Striping takes place at block level<br/>• Parity blocks are also striped<br/>• Provides higher throughput but slower writes but better than RAID 4 as Parity bits are distributed among all disks and the number of write operations on average equal among all 3 disks.<br/>• MTTF increases substantially (same as RAID3)<br/>•P<sub>i</sub> = A<sub>2i</sub> ⊕ A<sub>2i+1</sub> |
| RAID 6 (Block level level striping)        | • Similar to RAID 5 except two parity bocks used.<br/>• Reliability is of the order of MTTF<sup>3</sup>/10<br/>• P0 and P1 are parity blocks for blocks A0, A1 and A2. These are computed in such way that any two disk failures can be safe to recover the data. |

##### Choosing the suitable RAID level

The factors to consider:

* Reliability
* Performance
* Storage utilization
* Price/number of disks



#### Failvote, Failfast	1.3 P15-21

##### Fault Tolerance by voting: Use more than one module, voting for higher reliability

* **Failvote** - Stops if there are no majority agreement
  * Failvote needs majority agreement to accept an action (eg, Read/write)
  * If we start with 10 devices, the system works as long as 6 of them are working. Action is accepted when 6 or more agreeing on the decision.
  * The moment 5th one fails, system stops as there cannot be 6 devices agreeing
  * n is odd: majority = (n + 1) / 2
  * n is even: majority = 1 + n / 2
* **Failfast (voting)** - Similar to failvote except the system senses which modules are available and uses the majority of the available modules.
  * In Failfast, we are only concerned of majority among the working ones. We are assuming that we can tell which ones are working. Hence we can continue to operate until 2 working ones and if both agree we can proceed with the action. But if they differ the system stops.
* A 10 module Failfast system continues to operate until the failure of 9 modules where as Failvote stops when 5 modules fail.
* Failfast system has better availability than failvoting (since failvote stops when there is no majority agreement).
* **Supermodule** – Naturally, a system with multiple hard disk drives is expected to function with only one working disk (use voting when multiple disks are working/available, but still work even when only one is available)

##### Availability of failvote systems

If there are n events, mean time to the first event = m/n

Consider a system with modules each with MTTF of 10 years

Failvoting with 2 devices:

* MTTF = 10/2 = 5 years (system fails with 1 device failure)

Failvoting with 3 devices:

* MTTF = 10/3 for the first failure + 10/2 for 2nd failure = 8.3 years.

Lower availability for higher reliability (multiple modules agreeing on a value means that value is more likely to be accurate/reliable)

##### Fault tolerance with repair

With repair of modules: the faulty equipment is repaired with an average time of **MTTR (mean time to repair)** as soon as a fault is detected (Sometimes MTTR is just time needed to replace)

Typical Values for recent disks:

* MTTR = Few hours (assuming we stock spare disks) to 1 Day
* MTTF = 750000 hours (~ 86 years) [hard fault]
* Probability of a particular module is not available = MTTR/(MTTF+MTTR) ≅ **MTTR/MTTF** if MTTF >> MTTR

##### Fault tolerance of a supermodule with repair

<img src="img\w1\11.png" alt="11"  style="zoom:80%;" />



#### Communication reliability	1.3 P22-33



### Part 4

#### Disk writes for consistency, Duplex write, logged write	1.4 P3-13

Either entire block is written correctly on disk or the contents of the block is unchanged. To achieve disk write consistency we can do –

* Duplex write
  * Each block of data is written in two places sequentially
  * If one of the writes fail, system can issue another write
  * Each block is associated with a version number. The block with the latest version number contains the most recent data.
  * While reading - we can determine error of a disk block by its CRC.
  * It always guarantees at least one block has consistent data.
* Logged write
  * Similar to duplex write, except one of the writes goes to a log. This method is very efficient if the changes to a block are small.

#### CRC	1.4 P14-19	Live1 P41

**An error detection algorithm**

1. A polynomial needs to be specified
2. A sequence of bitwise exclusive-or (XOR) operation needs to be performed
3. The final CRC value needs to be stored for each data block (or the data unit on which CRC is performed)
4. Data correctness can be checked with CRC -

  a. its corresponding CRC value is retrieved

  b. A sequence of bitwise XOR operation needs to be performed to find out the correctness of data
