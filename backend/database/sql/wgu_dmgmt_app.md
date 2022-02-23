# C170: Data Management - Applications

## CH 6: Data Storage

### 6.1 Storage media

- Access time
  - the time required to access the first byte in a read or write operations

- Transfer rate
  - the speed at which data is read or written following initial access

- Speed: (of storage) measured as access time and transfer rate

- Volatile memory
  - Memory that is lost when disconnected by from power
  - Non-volatile memory: memory retained when without power

- **Four features of storage media**:
  - Speed
  - Cost (per gigabyte of memory)
  - Capacity
    - Limted by cost
    - More expensive = Less Capacity
  - Volatility (volatile or non-volatile)

- Main memory (RAM)
  - primary memory used when computer programs execute
  - Fast, expensive and limited capacity
  - Volatile

- Flash Memory (SSD)
  - less expensive and higher capacity (than main memory)
  - slower than main, faster than HDD
  - non volatile

- Magnetic disk (HDD)
  - Used to store large amounts of data
  - Slower, cheaper, and higher capacity than all

- Three types of media most important for database:
  - Main Memory (RAM)
  - Flash Memory (SSD)
  - Magnetic Disk (HDD)

- Data grouping
  - Sectors (HDD)
  - Pages (SSD)
  - Blocks
    - uniform size of data used by databases and file systems when transferring data between main memory and storage media
    - Block size is independent of storage device (database are unaware of page and sector sizes)
    - blocks would contain rows in databases

- Row-oriented storage
  - Where databases store an entire row within one block to minimize block transfers
  - Common config for relational databases

- What may make a row size big? 
  - The values stored ...the column size

- Row-oriented storage: Row & Block size
  - Improved query performance
    - Requires: Row size < block size
    - Why?: Fewer blocks are transferred for queries that read and write multiple performance 
      - because blocks hold more rows
      - so less of them are needed to be transferred for X amt of rows
  - Less wasted storage
    - Requires: Row size < block size
    - Rows do not fit evenly into available space
      - So if row size is small, this wasted space is not much as opposed to rows that are big which may result in more wasted space
  - What if row sizes are big due to large column values?
    - Row would contain a link to the large column, which is stored elsewhere, thereby still keeping row size small and helps keep query performance high

- What benefits from row-oriented storage?
  - Transacational applications which often read and write individual rows

- Colum-oriented storage
  - each block stores values for a single column only
  - good for analytic applications that often read jusut a few columns from many rows
  - reading/ writing a row requires access to multiple blocks

- Column-oriented storage benefits to analytic applications
  - Faster data access
    - because more column values are transfeered per block
    - ^ duces time to access storage media
  - Better data compression
    - Since data compression is more effective when  all values have the same type
    - better compression = more values stored per block = more reduction in access time

- Ex of column-oriented databases
  - PostgreSQL and Vertica supports it
  - NoSQL are optimized for analytic applications and uses column-oriented storage

### 6.2 Table Structures

- table structure
  - scheme for organizing rows in blocks on storage media

- **Heap table**
  - no order is imposed on rows
  - What?
    - Databases mantains a list of blocks assigned to the table along with the address of the first available spaces for inserts (as a linked list)
    - All the blocks are full?
      - Database allocates a new block and inserts rows in this new block

- Pros of Heap table
  - Optimizes inserts, updates, and delete operations
  - Fast for bulk loading of many rows (because no specific order is needed)

- Cons of Heap table
  - Not optimal for queries that read rows in specific order since rows are scattered randomly

- **Sorted table**
  - database where a sort column is chosen to determine the physical ordering of rows
    - Ordering: rows are assigned to blocks according to the value of the sort column (ex: primary key)

- Pros of Sorted table
  - optimal for read queries:
    - JOIN on sorted column
    - SELECT with range of sort column values in the WHERE clause
    - SELECT with ORDER BY the sort column
  - Used commonly since by default (or when) reads are more frequent than updates and inserts
    - PK is usually the sort column

- Cons of Sorted table:
  - maintaining correct sort order of rows is slow
    - this is because free space for new rows may not be the correct location for maintaining sort order
  - Updates and insert operations not optimized

- How is sort order maintained?
  - Sort column order is based on linked list so inserts don't require moving all rows up or down

- **Hash table**
  - Where database allocates blocks to buckets (that contain initially one block) which become a chain of linked blocks as table grows
    - Allocation? How?
      - Bucket assignment is determined by hash function (computes bucket) & key (group of columns; commonly primary key)
      - hash function scambles row locations and evenly distributes rows across blocks
        - dynamic hash functions are used to automatically allocate more blocks to table, create additional buckets, and distribute rows across all buckets
        - More buckets = fewer rows per bucket = fewer linked blocks = reduce inefficiency from queries having to read several blocks to access a single row

- Pros of Hash table, optimized for:
  - Inserts and deletes of individual rows
    - Why? Row location can quickly be determined from hash key
  - Selecting oh single rows when hash key value is specified in WHERE clause

- Cons of hash table, not optimized for:
  - Queries that select many rows with a range of values
    - Why? Rows are randomly distributed across many blocks

- **Table-Clusters** (multi-tables)
  - where rows of multiple tables are interleaved in the same storage area, maintained with the cluster key
  - Cluster key
    - a column that is avaiable in all interleaved tables
      - usually the primary key of one table and the corresponding foreign key of another
    - determines the order in which rows are interleaved
      -  rows with same cluster keys are stored together

- Pros of Table Clusters
  -   Optimal when joining interleaved tables on the cluster key
    -  Because physical row location is the same as output order

- Cons of Table Clusters, not optimized for
  - Join on columns other than the cluster key
  - read multiple rows of a single table
    - requires accessing more blocks since the rows are spread out across many blocks
  - update clustering key

### 6.3 Single-level indexes

- Single-level index
  - file consisting of column values and pointers (block identifiers) to the rows of the values in the table
    - ![image](https://user-images.githubusercontent.com/14286113/155352456-ab3a76c4-8885-42bf-b17d-122e202b6843.png)
  - Sorted on the column value 
  - If column is unique, one entry in index for each column value
    -  If not unique, then:
      -  multiple entries for column values, or
      -  one entry for each column value, followed by multiple pointers 
  -  Multi-column index
    -  Where an index is defined on multiple columns 
      -  as opposed to single column which is the norm

**Query processing**

- table scan
  - operations where table blocks are read directly without using an index
  
- index scan  
  - operations where index blocks are read sequentially, in order to located the needed table blocks

- Hit ratio
  - percentage of table rows selected by a query
  - AKA filter factor or selectivity

- How are SELECT queries done?
  - table scan or index scan

- When is table or index scan used?
  - If no index column, then table scan
  - Else index column exists in WHERE clause, then database examines the WHERE clause and estimates the hit ratio 
    - High hit ratio: table scan
    - Low hit ratio:
      - Look for indexed column in WHERE clause
      - Scan index
      - Find matching values
      - Retrieve rows from the linked blocks to the found index values

- Pros of using index
  - Requires fewer blocks than a table 
    - since column value and pointer occupies less space
  - Fewer blocks = faster (than table scans) (when hit ratio is low)
    - If small enough, then can reside in main memory to make it faster
    - If sorted, then binary search can be used to make it faster

**Sorted table indexes**

- Dense index
  - contains an entry for every table row

- Sparse Index
  - contains an entry for every table block

- primary index
  - unique sort column
  - sparse (usually)

- clustering index
  - non-unique sort column
  - sparse

- secondary index
  - non-sort column
  - dense

- Sort columns 
  - Sorted table can only have one sort column
    - so only one primary or clustering index
  - Tables can have many secondary indexes
    - Ex: all indexes of hash & heap tables are secondary; no sort column exists

- Sparse is much faster
  - Why?
    - fewer entries and occupy fewer blocks
    - stored in main memory (if small enough)

- Operations on dense indexes
  - Inserts
    - slow because entries need to be moved
      - Split block and reallocate entries to new block to make space for new entry
  - Deletes
    - Slow because entries need to be moved
    - Entries are marked as "deleted"
      - so periodically, database reorganizes the index to remove deleted entries and compress the index
  - Updates
    - Similiar to delete followed by an insert

- Operations on sparse indexes
  - Since each entry corresponds to table block (rather than table row like in dense index), entries are inserted or deleted when blocks split or merge
    - this occurs less often than row inserts and deletes

### 6.4 Multi-level indexes

- multi-level index
  - stores column values and row pointers in a hierarchy, bottom to top:
    - Bottom:
      - sorted column for single-level index that is:
        -  sparse for primary & clustering indexes
        -  dense for secondary indexes  
    - Each level above the bottom:
      - sparse sorted index to the level below
    - Bottom to top:
      - becomes smaller and smaller till its only one block at the top
  - ![image](https://user-images.githubusercontent.com/14286113/155369277-bc98673e-470f-4b1f-bb82-416da023d0ae.png)


- How rows containing indexed value is located:
  - Start from top-level block
  - compare index values to entries in the block
  - locate the next level block containing the value
  - Continue until bottom-level block containing the value is located
    - this block cotnains the pointer to the correct table block

- Multi-level index vs Single-level index
  - multi-level index are faster than single-level indexes (on most queries)
  - multi-level index are more commonly used
  - ![image](https://user-images.githubusercontent.com/14286113/155373970-53330972-37c2-429f-9166-a801f88cca91.png)

**Balanced indexes**

- Branch
  - path from top-level block to a bottom-level block

- Balanced indexes
  - multi-level indexes when all branches are the same length

- Imbalanced indexes
  - multi-level indexes when all branches are the different lengths
  - undesirable due to processing time being unpredictable

**B- & B+ tree indexes**

- B+tree
  - balanced multi-level index where all indexed values abd pointers to table blocks appear in the bottom level 
  - values can be repeated
  - simpler than b-tree
  - more commonly used
  - Pros:
    - bottom level is a single-level index that can be scanned or searched
    - less harder to implement inserts, deletes, updates since all table pointers are at bottom level rather than on different levels like on b-tree

- B-tree
  - where if an indexed values appears in a higher level, then the pointer appears as well and then the value is not repeated at lower levels
  - more compact than b+tree 
    - since index values are not repeated

### 6.5 Other Indexes

- **Hash index**
  - index where entires are assigned to buckets
  - buckets
    - block or group of blocks containing index entries
    - starts with one block and more are created/linked as indiex grows
  - hash function
    - computes a bucket number from the value of the indexed column
    - determines the bucket for index entry
  - ![image](https://user-images.githubusercontent.com/14286113/155393335-2a57a1c9-2ed2-46f4-aa13-47f3ad0758f6.png)

- Hash index: how rows with specific column value are located 
  - Apply hash function to column value to compute the bucket number
  - Read index blocks for the bucket number
  - find the index entry for the column value and read the table block pointer
  - reads the table block containing the 

- Hash index vs hash table
  - hash index stores index entries in each bucket
  - hash table stores table rows in each bucket

- **Bitmap indexes**
  - grid of bits (1s and 0s) where:
    - row corresponds to unique table row
      - row number can be primary key value or internal table row number maintained by the database
    - column corresponds to a distinct table value
    - `1` indicates that the table row corresponding to the index row number contains the table value coressponding to the index column number
    - `0` indicates row does not contain the value

- Bitmap index: locating row containing a table value
  - Determine index column corresponding to the value that is being sought
  - Read index column and finds index rows that are set to `1`
  - Determines table rows corresponding to the index rows
  - Determines pointers to blocks containing the table rows
  - Reads the blocks containing the table rows

- Pros of bitmap index
  - quickly determine  the block containing a table row from index row number
  - 
