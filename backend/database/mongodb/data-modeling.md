# MongoDB/ Mongoose Notes

## Relational Databases (SQL)
* Data is tabular, stored in tables, columns, and rows
* Fixed schemas for data models
* Requires schema normalization (splitting tables into smaller, specific tables)
* Does not allow multiple values in a single "cell" of (row, column) 
* May involve complex JOINs which impacts performance

## Document Databases (NoSQL)
* Data is stored in Documents (BSON/ JSON)
* Document is a dictionary of key-value pairs where the value may be:
  * Primitive JSON types (ex: number, string, etc)
  * Primitive BSON types (ex: datetime, ObjectId, etc)
  * Array of values
  * Objects composed of key-value pairs
  * Null
* No fixed schemas (documents in a collection/ table are not required to have the same schema)
* Allows you to change schema/ structure of documents and update documents to the new structure easily
* Allows for multi-valued properties, so no need for complex normalizations or joins
* Makes mapping documents to code entities/ objects much easier
* Document structure
  * Embedded data
    * This is where you store related data in a single document structure, by embedding document structures in a field or array within a 
document
  * References
    * This is where data is related to one another through storing references/ links (usually by ObjectId) in both documents
* Single document atomicity: where write operations is atomic on the level of single document, even if the operation modifies multiple embedded documents in that single document
  * Note: multi-document write operations may not be atomic, see [transactions](https://docs.mongodb.com/manual/core/transactions/) for some solutions

##  Seeks and Reads
* Random Seeks take far longer time than accessing sequential data (on spinning disk based hard drives)
* JOINS in relational databases involves many seeks, which makes it one of the most expensive operations that relational databases can do
  * This is why denormalization data is better for performance even though it creates redundancy and app complexity
* In MongoDB, its better to embed one-to-many relationships because of data locality
  * Since the database stores documents contiguously on disk, not many seeks are required


## Embedding vs Referencing
* Pros of Embedding
  * **Performance** If app frequently accesses some related data, it is better to embed that data into the document rather than reference it with ID and require multiple seeks to find that data
  * **Atomicity** Enables Atomic and Isolated transactions since you can perform operations with single operations (unlike when your do operations to referenced documents, where you have to make sure to do same operations for both documents)
  * Good for One-to-One and One-to-Many relationships

* Pros of Referencing/ "normalization"
  * Makes queries more flexible
    * Doing queries on embedded documents will often give you more data than you need, and require you to do more filtering than using the normalized model
    * You can do sorting, filtering, limiting, etc on queries with normalized/ referenced documents
  * MongoDB documents have a size limit of 16MB, so referencing is necessary when embedding documents goes over document size limit
  * Embedded documents take up more RAM the larger the document is 

* Embedding and referencing together (embedding IDs into documents)
  * Good for "many-to-many" relationships
  * Embed array of ids of A into B, and embed array of ids of B into A

## Data Modeling

**Things to consider**
* Usage of the data (queries, updates, processing)
* Structure of the data
* Needs of the app
* Performance 
* Data retrieval patterns (ACID)?
* Efficient queries
* Increase throughput of insert and update operations
* Distributing activity to a sharded cluster more effectively
* Structuring schema so app receives all of its required information in a single read operation

## Materials

- MongoDB Applied Design Patterns CH 1: [link](https://www.oreilly.com/library/view/mongodb-applied-design/9781449340056/ch01.html)
- Stackoverflow explanation: [link](https://stackoverflow.com/questions/5373198/mongodb-relationships-embed-or-reference/5373969#5373969)
- MongoDB Docs-Data Modeling: [link](https://docs.mongodb.com/manual/core/data-modeling-introduction/)
- MongoDB Docs-Polymorphism: [link](https://mongodb.github.io/mongo-csharp-driver/2.0/reference/bson/mapping/polymorphism/)
- MongoDB Article on Schema Design Patterns: [link](https://developer.mongodb.com/how-to/polymorphic-pattern/)
