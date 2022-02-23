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

