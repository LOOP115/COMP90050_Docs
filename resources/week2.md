## Week 2



#### How data are stored

* Files - A database is mapped into different files. A file is a sequence of records
* Data blocks - Each file is mapped into fixed length storage units, called data blocks (also called logical blocks, or pages)
* Cost of a query - The number of pages/ disk blocks that are **accessed from disk** to answer the query



#### Query plans and optimisation

**Steps in cost-based query optimisation**

1. Generate logically equivalent expressions of the query
2. Annotate resultant expressions to get alternative query plans

3. Choose the cheapest plan based on estimated cost

**Estimation of plan cost based on:**

- Statistical information about tables.
  - Example: number of distinct values for an attribute
- Statistics estimation for intermediate results to compute cost
- Cost formulae for algorithms, computed using statistics again



#### How to estimate costs

**Step 1: Result size calculation using Reduction Factor**

Depends on the type of the predicate:

1. Col = value: RF = 1/Number of unique values (Col)
2. Col > value: RF = (High(Col) –value) / (High(Col) –Low(Col))
3. Col < value: RF = (val–Low(Col)) / (High(Col) –Low(Col))
4. Col_A= Col_B(for joins): RF = 1/ (Max number of unique values in Col_A,Col_B)

**Step 2: Different options for retrieving data and calculating cost (again, estimation)**



Cost-based optimization is expensive, thus….
- Systems may use heuristics to reduce the number of choices that must be made in a cost-based fashion
- Heuristic optimization transforms the query-tree by using a set of rules that typically (but not in all cases) improve execution performance:

1. Perform selections early (reduces the number of tuples)
2. Perform projections early (reduces the number of attributes)
3. Perform most restrictive selection and join operations (i.e., with smallest result size) before other similar operations



#### Query costs

* Query rewriting with parameters for execution plan reuse
* We expect the optimizer to generate essentially the same plan and reuse the plans - parameterize
* Store derived data
  * When you frequently need derived values
  * Data do not change frequently
* Use pre-joined tables
  * When tables need to be joined frequently
  * Regularly check and update pre-joined table for updates in the original table
  * May still return some ‘outdated’ result



### Indexing

#### Ordered index

* **Clustering index/ Primary index:** in a sequentially ordered file, the index whose search key specifies the sequential order of the file
  * The search key of a primary index is usually but not necessarily the primary key
* **Non-clustering index/ Secondary index:** an index whose search key specifies an order different from the sequential order of the file
  * Secondary indices improve the performance of queries that use keys other than the search key of the clustering index.

#### B+ trees	2.3 P14-31

#### Hash indices	2.4 P2-4

#### Bitmap indices	2.4 P5-6

#### Spatial indices

* Quadtrees	2.4 P8-11
* R-Trees	2.4 P12-14

