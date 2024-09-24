# MongoDB Tutorial
<div align ="center">
  
![Image](https://i.pinimg.com/736x/01/15/9b/01159bc9b0bc4ba22f834d06d4974230.jpg)

</div>

## What is NoSQL?
NoSQL (Not Only SQL) refers to a class of non-relational databases that emerged in the late 2000s to handle the vast amounts of unstructured or semi-structured data that traditional SQL (relational) databases were not designed for. Unlike SQL databases that rely on fixed schemas and ACID transactions, NoSQL databases are more flexible, allowing for rapid development and scaling.

## Key Characteristics of NoSQL Databases:
**Non-relational data models:** NoSQL databases use different data models like key-value pairs, documents, wide-column stores, or graphs.

**Flexible schemas:** Unlike relational databases, NoSQL databases can store unstructured, semi-structured, or structured data without requiring a fixed schema.

**Horizontal scalability:** Designed to scale out on distributed clusters, making them ideal for big data and cloud-based environments.

**Eventual consistency:** Many NoSQL databases prioritize availability and partition tolerance over immediate consistency (as defined by the CAP theorem).

## NoSQL Database Types

1. **Document-based Databases**:
   - These databases store data as documents, typically in JSON or BSON format.
   - Example: **MongoDB**

2. **Key-value Stores**:
   - Data is stored as key-value pairs, where a key is associated with a specific value.
   - Examples: **Redis**, **Amazon DynamoDB**

3. **Wide-column Stores**:
   - Data is stored in columns rather than rows, allowing for efficient querying in big data applications.
   - Examples: **Apache Cassandra**, **HBase**

4. **Graph Databases**:
   - These databases represent data in graph structures with nodes, edges, and properties, optimized for querying relationships.
   - Example: **Neo4j**
## Common MongoDB Commands

### Database Commands
- **Show databases**: `show dbs`
- **Use a database**: `use <database_name>`
- **Create a database**: `use <database_name>` (it creates the DB when you insert data)
- **Drop a database**: `db.dropDatabase()`

### Collection Commands
- **Show collections**: `show collections`
- **Create a collection**: `db.createCollection("<collection_name>")`
- **Drop a collection**: `db.<collection_name>.drop()`

### Document Commands
- **Insert a document**: `db.<collection_name>.insertOne({<document>})`
- **Insert multiple documents**: `db.<collection_name>.insertMany([{<doc1>}, {<doc2>}])`
- **Find documents**: `db.<collection_name>.find({<query>})`
- **Find one document**: `db.<collection_name>.findOne({<query>})`
- **Update a document**: `db.<collection_name>.updateOne({<query>}, { $set: {<update>}})`
- **Update multiple documents**: `db.<collection_name>.updateMany({<query>}, { $set: {<update>}})`
- **Delete a document**: `db.<collection_name>.deleteOne({<query>})`
- **Delete multiple documents**: `db.<collection_name>.deleteMany({<query>})`

### Query Operators
- **Equality**: `{ field: value }`
- **Not equal**: `{ field: { $ne: value } }`
- **Greater than**: `{ field: { $gt: value } }`
- **Less than**: `{ field: { $lt: value } }`
- **In array**: `{ field: { $in: [value1, value2] } }`
- **Regular expression**: `{ field: /pattern/ }`

### Indexing Commands
- **Create an index**: `db.<collection_name>.createIndex({<field>: <1 or -1>})`
- **Drop an index**: `db.<collection_name>.dropIndex("<index_name>")`
- **List indexes**: `db.<collection_name>.getIndexes()`

### Aggregation Commands
- **Aggregation pipeline**: `db.<collection_name>.aggregate([{<stage1>}, {<stage2>}])`

### Administration Commands
- **Server status**: `db.runCommand({ serverStatus: 1 })`
- **List users**: `db.getUsers()`
- **Create user**: `db.createUser({ user: "<username>", pwd: "<password>", roles: [ { role: "<role>", db: "<database>" } ] })`

### Views Commands in MongoDB

- **Create a View**: `db.createView("<view_name>", "<source_collection>", [<pipeline>])`


### Backup and Restore Commands
- **Backup**: `mongodump --db <database_name> --out <backup_directory>`
- **Restore**: `mongorestore --db <database_name> <backup_directory>`
