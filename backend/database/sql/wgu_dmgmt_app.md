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

- heap table
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

- Sorted table
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

- Hash table
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

- Table-Clusters (multi-tables)
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
