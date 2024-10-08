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
  
## What is MongoDB?
MongoDB is a **NoSQL** (non-relational) database management system designed to handle large volumes of unstructured or semi-structured data. Unlike traditional relational databases like MySQL or PostgreSQL, which store data in tables with rows and columns, MongoDB uses a flexible, document-based model.

Here’s a more detailed explanation:

### 1. **Document-Oriented**
   - MongoDB stores data in **BSON** (Binary JSON) format, which is similar to JSON (JavaScript Object Notation). These BSON documents contain key-value pairs, making the structure flexible.
   - A document in MongoDB can represent an entity, such as a user profile, and may contain various data types like strings, arrays, numbers, and even nested documents.
   - Example of a document:
     ```json
     {
       "_id": ObjectId("507f1f77bcf86cd799439011"),
       "name": "John Doe",
       "age": 30,
       "address": {
         "city": "New York",
         "zipcode": 10001
       },
       "hobbies": ["reading", "travelling"]
     }
     ```

### 2. **Collections and Databases**
   - **Documents** are grouped into **collections**, and collections are grouped into **databases**. 
   - A collection in MongoDB is equivalent to a table in relational databases, and a database is equivalent to a relational database schema.
   - Collections are schema-less, meaning documents within the same collection can have different structures.

### 3. **Scalability**
   - MongoDB is designed for horizontal scalability through **sharding**, which means that large datasets can be distributed across multiple machines. 
   - This allows MongoDB to handle high traffic and large amounts of data efficiently.

### 4. **Key Features**
   - **Schema Flexibility**: MongoDB doesn’t require a predefined schema, allowing you to store documents with different structures in the same collection.
   - **High Availability**: It provides high availability through **replication** (Replica Sets), which replicate data across multiple nodes to ensure redundancy and failover.
   - **Indexing**: MongoDB supports advanced indexing techniques (such as compound indexes, text indexes, and geospatial indexes) to speed up query performance.
   - **Aggregation**: It includes a powerful aggregation framework for performing complex data analysis and transformations, similar to SQL's `GROUP BY`.
   - **Transaction Support**: MongoDB supports **ACID transactions**, allowing multiple operations to be grouped into a single transaction.

### 5. **Use Cases**
   - **Big Data Applications**: MongoDB is suitable for handling large datasets, often used in applications with rapidly changing data, like real-time analytics or social media platforms.
   - **Content Management**: Flexible data structures make MongoDB ideal for content management systems where the content types may vary (e.g., blogs, product catalogs).
   - **IoT (Internet of Things)**: Its ability to store different data types and support fast writes makes MongoDB a good fit for IoT applications.
   - **Mobile and Web Applications**: It is commonly used in modern web and mobile apps, especially those that require frequent data changes, scalability, and flexibility.

### 6. **Advantages**
   - **Schema-less**: No need to define a fixed schema upfront, which allows for flexibility in the development phase.
   - **Scalable and Fast**: Handles massive volumes of data with horizontal scaling.
   - **Dynamic Queries**: Queries are executed using a powerful query language that supports filters, sorting, joins (via $lookup), and complex aggregations.
   - **Integration with Modern Development**: MongoDB is widely used with programming languages like JavaScript (Node.js), Python, and others, making it easy to integrate into web applications.

### 7. **Limitations**
   - **Lack of Joins**: MongoDB doesn’t natively support complex joins like relational databases, though you can use the `$lookup` operator in aggregation to perform joins across collections.
   - **Consistency**: In distributed systems, MongoDB may prioritize availability and partition tolerance over strong consistency, though it does offer tunable consistency models.
   - **Complex Transactions**: While MongoDB supports multi-document transactions, complex transactional workflows can be more challenging to implement compared to traditional SQL databases.

### 8. **Query Language**
   - MongoDB uses a **JSON-like query language** to retrieve and manipulate data. It supports a variety of operators for filtering, comparison, logical operations, etc.
   - Example query to find all users above the age of 25:
     ```javascript
     db.users.find({ age: { $gt: 25 } })
     ```

### 9. **Popular MongoDB Tools**
   - **MongoDB Atlas**: A cloud-based, fully managed version of MongoDB.
   - **MongoDB Compass**: A graphical user interface to visually interact with MongoDB databases.
   - **Mongoose**: A popular Object Data Modeling (ODM) library for MongoDB and Node.js, providing schema-based solutions for app data.

### 10. **Popular Alternatives**
   - **Couchbase**
   - **Cassandra**
   - **Amazon DynamoDB**
   - **Redis** (for key-value store)

MongoDB is widely adopted for applications that require high scalability, schema flexibility, and high availability, especially in modern cloud-native and data-driven environments.


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








## MongoDB Commands with Examples

### 1. Database Commands

- **Show all databases:**
  ```bash
  show dbs
  ```
  Example:
  ```
  admin   0.000GB
  local   0.000GB
  mydb    0.001GB
  ```

- **Use a database (or create if it doesn't exist):**
  ```javascript
  use mydb
  ```

- **Show current database:**
  ```javascript
  db
  ```

- **Drop a database:**
  ```javascript
  db.dropDatabase()
  ```
  Example:
  ```javascript
  { "dropped" : "mydb", "ok" : 1 }
  ```

### 2. Collection Commands

- **Show all collections in the current database:**
  ```javascript
  show collections
  ```

- **Create a collection:**
  ```javascript
  db.createCollection("users")
  ```
  Example:
  ```javascript
  { "ok" : 1 }
  ```

- **Drop a collection:**
  ```javascript
  db.users.drop()
  ```
  Example:
  ```javascript
  true
  ```

### 3. Document Insertion Commands

- **Insert a single document:**
  ```javascript
  db.users.insertOne({ name: "John Doe", age: 30, city: "New York" })
  ```
  Example:
  ```javascript
  { acknowledged: true, insertedId: ObjectId("...") }
  ```

- **Insert multiple documents:**
  ```javascript
  db.users.insertMany([
    { name: "Alice", age: 25, city: "Los Angeles" },
    { name: "Bob", age: 28, city: "Chicago" }
  ])
  ```
  Example:
  ```javascript
  { acknowledged: true, insertedIds: { "0": ObjectId("..."), "1": ObjectId("...") } }
  ```

### 4. Document Query Commands

- **Find all documents in a collection:**
  ```javascript
  db.users.find()
  ```
  Example:
  ```javascript
  { "_id": ObjectId("..."), "name": "John Doe", "age": 30, "city": "New York" }
  { "_id": ObjectId("..."), "name": "Alice", "age": 25, "city": "Los Angeles" }
  ```

- **Find documents with a specific condition:**
  ```javascript
  db.users.find({ age: { $gt: 25 } })
  ```
  Example:
  ```javascript
  { "_id": ObjectId("..."), "name": "John Doe", "age": 30, "city": "New York" }
  ```

- **Find a single document:**
  ```javascript
  db.users.findOne({ name: "Alice" })
  ```
  Example:
  ```javascript
  { "_id": ObjectId("..."), "name": "Alice", "age": 25, "city": "Los Angeles" }
  ```

### 5. Document Update Commands

- **Update one document:**
  ```javascript
  db.users.updateOne(
    { name: "John Doe" }, 
    { $set: { age: 31 } }
  )
  ```
  Example:
  ```javascript
  { acknowledged: true, matchedCount: 1, modifiedCount: 1 }
  ```

- **Update multiple documents:**
  ```javascript
  db.users.updateMany(
    { city: "Los Angeles" }, 
    { $set: { city: "San Francisco" } }
  )
  ```
  Example:
  ```javascript
  { acknowledged: true, matchedCount: 2, modifiedCount: 2 }
  ```

### 6. Document Deletion Commands

- **Delete one document:**
  ```javascript
  db.users.deleteOne({ name: "Alice" })
  ```
  Example:
  ```javascript
  { acknowledged: true, deletedCount: 1 }
  ```

- **Delete multiple documents:**
  ```javascript
  db.users.deleteMany({ age: { $lt: 30 } })
  ```
  Example:
  ```javascript
  { acknowledged: true, deletedCount: 2 }
  ```

### 7. Index Commands

- **Create an index:**
  ```javascript
  db.users.createIndex({ name: 1 })
  ```
  Example:
  ```javascript
  { "createdCollectionAutomatically" : false, "numIndexesBefore" : 1, "numIndexesAfter" : 2, "ok" : 1 }
  ```

- **Show all indexes:**
  ```javascript
  db.users.getIndexes()
  ```

- **Drop an index:**
  ```javascript
  db.users.dropIndex("name_1")
  ```

### 8. Aggregation Commands

- **Simple aggregation example (group by city and count):**
  ```javascript
  db.users.aggregate([
    { $group: { _id: "$city", total: { $sum: 1 } } }
  ])
  ```
  Example:
  ```javascript
  { "_id": "New York", "total": 1 }
  { "_id": "San Francisco", "total": 2 }
  ```

### 9. Backup and Restore Commands

- **Backup a database (using `mongodump` command-line utility):**
  ```bash
  mongodump --db mydb --out /backup/directory
  ```

- **Restore a database (using `mongorestore` command-line utility):**
  ```bash
  mongorestore --db mydb /backup/directory/mydb
  ```

## 10. Administrative Commands

- **Server status:**
  ```javascript
  db.serverStatus()
  ```

- **Check replication status:**
  ```
  rs.status()
  ```

- **List all users:**
  ```javascript
  db.getUsers()
  ```

- **Create a new user:**
  ```javascript
  db.createUser({
    user: "new_user",
    pwd: "password123",
    roles: [ { role: "readWrite", db: "mydb" } ]
  })
  ```
  Example:
  ```javascript
  { ok: 1 }
  ```

- **List roles for the current user:**
  ```javascript
  db.getRole({ role: "<role>", db: "<db_name>" })
  ```

---

These examples cover frequently used MongoDB commands for managing databases, collections, documents, and administrative tasks.





# MongoDB Commands: DML, DQL, DCL, and TCL

In MongoDB, commands are categorized similarly to SQL in terms of **DML (Data Manipulation Language)**, **DQL (Data Query Language)**, **DCL (Data Control Language)**, and **TCL (Transaction Control Language)**. Below is a breakdown of these categories with corresponding MongoDB commands:


## **1. DML (Data Manipulation Language)**

DML commands modify data in MongoDB collections (documents).

- **INSERT**: Add new documents to a collection.
  ```javascript
  db.collection.insertOne({ <document> })
  db.collection.insertMany([{ <document1> }, { <document2> }])
  ```
  Example:
  ```javascript
  db.users.insertOne({ name: "John Doe", age: 30, city: "New York" })
  ```

- **UPDATE**: Modify existing documents.
  ```javascript
  db.collection.updateOne({ <query> }, { $set: { <field1>: <value1>, ... } })
  db.collection.updateMany({ <query> }, { $set: { <field1>: <value1>, ... } })
  ```
  Example:
  ```javascript
  db.users.updateOne({ name: "John Doe" }, { $set: { age: 31 } })
  ```

- **DELETE**: Remove documents from a collection.
  ```javascript
  db.collection.deleteOne({ <query> })
  db.collection.deleteMany({ <query> })
  ```
  Example:
  ```javascript
  db.users.deleteOne({ name: "John Doe" })
  ```

- **REPLACE**: Replace an entire document with a new one.
  ```javascript
  db.collection.replaceOne({ <query> }, { <new_document> })
  ```
  Example:
  ```javascript
  db.users.replaceOne({ name: "John Doe" }, { name: "John Doe", age: 32, city: "San Francisco" })
  ```

---

## **2. DQL (Data Query Language)**

DQL commands are used to query and retrieve data from collections.

- **FIND**: Retrieve documents from a collection.
  ```javascript
  db.collection.find({ <query> })
  db.collection.findOne({ <query> })
  ```
  Example:
  ```javascript
  db.users.find({ age: { $gt: 25 } })
  db.users.findOne({ name: "Alice" })
  ```

- **COUNT**: Count the number of documents that match a query.
  ```javascript
  db.collection.countDocuments({ <query> })
  ```
  Example:
  ```javascript
  db.users.countDocuments({ age: { $gte: 30 } })
  ```

- **AGGREGATE**: Perform complex queries like group by, filtering, sorting, etc.
  ```javascript
  db.collection.aggregate([{ <stage1> }, { <stage2> }])
  ```
  Example:
  ```javascript
  db.users.aggregate([
    { $group: { _id: "$city", total: { $sum: 1 } } }
  ])
  ```

---

## **3. DCL (Data Control Language)**

DCL commands are used to manage access to the database and its collections (user privileges).

- **CREATE USER**: Create a new user with specific roles.
  ```javascript
  db.createUser({
    user: "username",
    pwd: "password",
    roles: [ { role: "readWrite", db: "mydb" } ]
  })
  ```
  Example:
  ```javascript
  db.createUser({
    user: "john_doe",
    pwd: "securepassword",
    roles: [ { role: "readWrite", db: "companyDB" } ]
  })
  ```

- **GRANT ROLE**: Assign a role to a user.
  MongoDB handles roles and privileges through `createUser` and `updateUser`. For granting roles, you would generally update the user's privileges using `updateUser`.

  Example:
  ```javascript
  db.updateUser("john_doe", { roles: [ { role: "dbAdmin", db: "companyDB" } ] })
  ```

- **DROP USER**: Delete an existing user.
  ```javascript
  db.dropUser("username")
  ```
  Example:
  ```javascript
  db.dropUser("john_doe")
  ```

---

## **4. TCL (Transaction Control Language)**

TCL commands manage transactions in MongoDB, allowing multiple operations to be grouped and executed as a single unit.

- **START TRANSACTION**: Begin a transaction.
  ```javascript
  session = db.getMongo().startSession()
  session.startTransaction()
  ```

- **COMMIT**: Commit the current transaction (persist changes).
  ```javascript
  session.commitTransaction()
  session.endSession()
  ```

- **ROLLBACK (ABORT)**: Rollback the current transaction (undo changes).
  ```javascript
  session.abortTransaction()
  session.endSession()
  ```

### Example of a Transaction in MongoDB:
```javascript
session = db.getMongo().startSession();
session.startTransaction();

try {
  session.getDatabase("mydb").users.insertOne({ name: "John Doe", age: 30 });
  session.getDatabase("mydb").orders.insertOne({ user: "John Doe", item: "Laptop" });

  // If all goes well, commit the transaction
  session.commitTransaction();
} catch (error) {
  // If there is an error, rollback the transaction
  session.abortTransaction();
} finally {
  session.endSession();
}
```

---

## Summary of MongoDB Commands

| Category   | SQL Equivalent | MongoDB Command                                      |
|------------|----------------|-----------------------------------------------------|
| **DML**    | `INSERT`       | `insertOne`, `insertMany`, `updateOne`, `deleteOne`  |
|            | `UPDATE`       | `updateOne`, `updateMany`                            |
|            | `DELETE`       | `deleteOne`, `deleteMany`                            |
| **DQL**    | `SELECT`       | `find`, `findOne`, `countDocuments`, `aggregate`     |
| **DCL**    | `GRANT/REVOKE` | `createUser`, `dropUser`, `grant roles`, `updateUser`|
| **TCL**    | `BEGIN/COMMIT` | `startTransaction`, `commitTransaction`, `abortTransaction` |



In MongoDB, **aggregate functions** are used in the **aggregation framework** to perform operations like grouping, filtering, sorting, and transforming data. MongoDB’s aggregation pipeline allows you to process and analyze documents in a collection, similar to SQL’s aggregate functions but with more flexibility.

## Common Aggregate Functions in MongoDB:

MongoDB's **aggregation framework** is a powerful tool for performing data transformations and computations in the database. It works by processing data through a **pipeline** of stages, where each stage performs an operation on the input data and passes the result to the next stage. The most common aggregation symbols, also known as **operators**, include mathematical, logical, array manipulation, and string operators.

### Key Aggregate Operators in MongoDB

#### 1. **$match**
Filters documents to pass only the ones that match the specified condition.

```javascript
db.orders.aggregate([
  { $match: { status: "shipped" } }
]);
```

#### 2. **$group**
Groups documents by a specified field and can calculate aggregates for each group, such as counts, sums, averages, etc.

```javascript
db.orders.aggregate([
  { $group: { _id: "$customerId", total: { $sum: "$amount" } } }
]);
```

#### 3. **$project**
Reshapes documents by including, excluding, or computing new fields. It's used to control the output structure.

```javascript
db.orders.aggregate([
  { $project: { item: 1, quantity: 1, total: { $multiply: ["$price", "$quantity"] } } }
]);
```

#### 4. **$sort**
Sorts documents in ascending or descending order.

```javascript
db.orders.aggregate([
  { $sort: { date: -1 } }  // -1 for descending, 1 for ascending
]);
```

#### 5. **$limit**
Limits the number of documents passed to the next stage.

```javascript
db.orders.aggregate([
  { $limit: 5 }
]);
```

#### 6. **$skip**
Skips a specified number of documents.

```javascript
db.orders.aggregate([
  { $skip: 10 }
]);
```

#### 7. **$lookup** (Join)
Performs a left outer join to another collection in the same database to combine documents.

```javascript
db.orders.aggregate([
  {
    $lookup: {
      from: "customers",    // the foreign collection
      localField: "customerId",  // the field in the current collection
      foreignField: "_id",   // the field in the foreign collection
      as: "customerDetails"  // name of the output array
    }
  }
]);
```

#### 8. **$unwind**
Deconstructs an array field from the input documents to output a document for each element of the array.

```javascript
db.orders.aggregate([
  { $unwind: "$items" }
]);
```

#### 9. **$addFields**
Adds new fields to documents or modifies existing fields.

```javascript
db.orders.aggregate([
  { $addFields: { totalCost: { $multiply: ["$price", "$quantity"] } } }
]);
```

#### 10. **$set**
An alias for `$addFields`. Used for adding or updating fields.

```javascript
db.orders.aggregate([
  { $set: { discountedPrice: { $multiply: ["$price", 0.9] } } }
]);
```

#### 11. **$bucket**
Categorizes incoming documents into groups, called buckets, based on a specified expression and boundary values.

```javascript
db.sales.aggregate([
  {
    $bucket: {
      groupBy: "$price",
      boundaries: [0, 100, 200, 300],
      default: "Other",
      output: { "count": { $sum: 1 }, "totalSales": { $sum: "$amount" } }
    }
  }
]);
```

#### 12. **$bucketAuto**
Similar to `$bucket`, but automatically calculates boundaries for the specified number of buckets.

```javascript
db.sales.aggregate([
  {
    $bucketAuto: {
      groupBy: "$price",
      buckets: 3,  // Number of buckets
      output: { "count": { $sum: 1 }, "totalSales": { $sum: "$amount" } }
    }
  }
]);
```

#### 13. **$out**
Writes the result of the aggregation pipeline into a new collection.

```javascript
db.orders.aggregate([
  { $match: { status: "shipped" } },
  { $out: "shippedOrders" }
]);
```

#### 14. **$merge**
Merges the aggregation result into an existing collection. If the collection does not exist, it creates it.

```javascript
db.orders.aggregate([
  { $match: { status: "shipped" } },
  {
    $merge: {
      into: "shippedOrders",  // The target collection
      whenMatched: "merge",   // What to do when there’s a match
      whenNotMatched: "insert"  // What to do when there’s no match
    }
  }
]);
```

---

### Arithmetic Operators

#### 15. **$sum**
Returns the sum of numerical values. Often used with `$group`.

```javascript
db.sales.aggregate([
  { $group: { _id: "$category", totalSales: { $sum: "$amount" } } }
]);
```

#### 16. **$avg**
Calculates the average value of numeric fields.

```javascript
db.sales.aggregate([
  { $group: { _id: "$category", avgPrice: { $avg: "$price" } } }
]);
```

#### 17. **$min** and **$max**
Returns the minimum or maximum value in a group of documents.

```javascript
db.sales.aggregate([
  { $group: { _id: "$category", lowestPrice: { $min: "$price" } } }
]);
```

#### 18. **$multiply**
Multiplies values together.

```javascript
db.orders.aggregate([
  { $project: { totalCost: { $multiply: ["$price", "$quantity"] } } }
]);
```

#### 19. **$divide**
Divides one value by another.

```javascript
db.orders.aggregate([
  { $project: { unitPrice: { $divide: ["$total", "$quantity"] } } }
]);
```

---

### String Operators

#### 20. **$concat**
Concatenates strings.

```javascript
db.users.aggregate([
  { $project: { fullName: { $concat: ["$firstName", " ", "$lastName"] } } }
]);
```

#### 21. **$substr**
Extracts a substring from a string.

```javascript
db.users.aggregate([
  { $project: { username: { $substr: ["$email", 0, 5] } } }  // First 5 chars of email
]);
```

---

### Array Operators

#### 22. **$size**
Returns the size of an array.

```javascript
db.orders.aggregate([
  { $project: { itemCount: { $size: "$items" } } }
]);
```

#### 23. **$filter**
Filters array elements based on a condition.

```javascript
db.orders.aggregate([
  {
    $project: {
      expensiveItems: {
        $filter: {
          input: "$items",
          as: "item",
          cond: { $gt: ["$$item.price", 100] }
        }
      }
    }
  }
]);
```

---

### Logical Operators

#### 24. **$and**, **$or**, **$not**
Logical operators for combining conditions.

```javascript
db.orders.aggregate([
  {
    $match: {
      $and: [
        { status: "shipped" },
        { amount: { $gt: 100 } }
      ]
    }
  }
]);
```

---

### Example Aggregation Pipeline

Here is a full example of a MongoDB aggregation pipeline that uses multiple stages:

```javascript
db.orders.aggregate([
  { $match: { status: "shipped" } },                   // Stage 1: Match shipped orders
  { $group: { _id: "$customerId", total: { $sum: "$amount" } } },  // Stage 2: Group by customer and sum amounts
  { $sort: { total: -1 } },                            // Stage 3: Sort by total in descending order
  { $limit: 5 },                                      // Stage 4: Limit to top 5 customers
  {
    $lookup: {                                         // Stage 5: Lookup customer details
      from: "customers",
      localField: "_id",
      foreignField: "_id",
      as: "customerDetails"
    }
  },
  { $project: { total: 1, customerDetails: 1 } }       // Stage 6: Project required fields
]);
```

This pipeline:
1. Filters orders by the `shipped` status.
2. Groups them by `customerId` and sums up the total order amount.
3. Sorts the results by total in descending order.
4. Limits the output to the top 5 customers.
5. Performs a join (using `$lookup`) to get customer details from the `customers` collection.
6. Projects the output to include the total and customer details.









#### Some more fuctions are
In MongoDB, there are several query operators similar to `$gt` (greater than), used for various purposes like comparison, logical, and evaluation. Here’s a list of some of the most commonly used query operators:

### **Comparison Operators**

1. **$gt**: Greater than
   - Matches values that are greater than the specified value.
   ```javascript
   db.collection.find({ age: { $gt: 30 } })
   ```

2. **$gte**: Greater than or equal to
   - Matches values that are greater than or equal to the specified value.
   ```javascript
   db.collection.find({ age: { $gte: 30 } })
   ```

3. **$lt**: Less than
   - Matches values that are less than the specified value.
   ```javascript
   db.collection.find({ age: { $lt: 30 } })
   ```

4. **$lte**: Less than or equal to
   - Matches values that are less than or equal to the specified value.
   ```javascript
   db.collection.find({ age: { $lte: 30 } })
   ```

5. **$eq**: Equal to
   - Matches values that are equal to the specified value.
   ```javascript
   db.collection.find({ age: { $eq: 30 } })
   ```

6. **$ne**: Not equal to
   - Matches values that are not equal to the specified value.
   ```javascript
   db.collection.find({ age: { $ne: 30 } })
   ```

7. **$in**: Matches any of the values specified in an array.
   ```javascript
   db.collection.find({ age: { $in: [25, 30, 35] } })
   ```

8. **$nin**: Matches none of the values specified in an array.
   ```javascript
   db.collection.find({ age: { $nin: [25, 30, 35] } })
   ```

### **Logical Operators**

1. **$and**: Joins query clauses with a logical AND.
   ```javascript
   db.collection.find({ $and: [{ age: { $gt: 25 } }, { age: { $lt: 35 } }] })
   ```

2. **$or**: Joins query clauses with a logical OR.
   ```javascript
   db.collection.find({ $or: [{ age: { $lt: 25 } }, { age: { $gt: 35 } }] })
   ```

3. **$not**: Inverts the effect of a query expression.
   ```javascript
   db.collection.find({ age: { $not: { $gt: 30 } } })
   ```

4. **$nor**: Joins query clauses with a logical NOR.
   ```javascript
   db.collection.find({ $nor: [{ age: { $gt: 30 } }, { name: "John" }] })
   ```

### **Element Operators**

1. **$exists**: Matches documents that have the specified field.
   ```javascript
   db.collection.find({ age: { $exists: true } })
   ```

2. **$type**: Selects documents if a field is of the specified type.
   ```javascript
   db.collection.find({ age: { $type: "int" } })
   ```

### **Array Operators**

1. **$all**: Matches arrays that contain all elements specified in the query.
   ```javascript
   db.collection.find({ tags: { $all: ["mongodb", "database"] } })
   ```

2. **$elemMatch**: Matches documents that contain an array field with at least one element that matches all the specified criteria.
   ```javascript
   db.collection.find({ scores: { $elemMatch: { score: { $gt: 80, $lt: 90 } } } })
   ```

3. **$size**: Matches any array with the specified number of elements.
   ```javascript
   db.collection.find({ tags: { $size: 3 } })
   ```

### **Evaluation Operators**

1. **$regex**: Performs regular expression searches.
   ```javascript
   db.collection.find({ name: { $regex: /^John/ } })
   ```

2. **$mod**: Performs a modulo operation and matches documents where the field value is a multiple of the divisor.
   ```javascript
   db.collection.find({ age: { $mod: [10, 0] } }) // age is a multiple of 10
   ```

### **Other Operators**

1. **$text**: Performs text search.
   ```javascript
   db.collection.find({ $text: { $search: "mongodb" } })
   ```

2. **$where**: Matches documents that satisfy a JavaScript expression.
   ```javascript
   db.collection.find({ $where: "this.age > 30" })
   ```

3. **$expr**: Allows the use of aggregation expressions in query filters.
   ```javascript
   db.collection.find({ $expr: { $gt: ["$age", 30] } })
   ```

---

These operators provide a wide range of functionalities in MongoDB to match and filter documents based on various criteria.

### Conclusion

MongoDB's aggregation framework provides extensive capabilities for data transformation, computation, and analysis. It allows you to run complex queries on large datasets efficiently using these operators and stages.

## Joins in MongoDB

In MongoDB, joins are handled differently than in traditional relational databases such as MySQL or PostgreSQL, where you can use `JOIN` operations to combine data from multiple tables. MongoDB is a NoSQL database that stores data in a document-based model. Initially, MongoDB didn’t support joins, encouraging developers to design schemas that minimize the need for them, often through **denormalization** (embedding documents within documents). However, as of **MongoDB 3.2**, the **$lookup** aggregation operator was introduced, enabling developers to perform **left outer joins** between collections.

### **1. What is a Join in MongoDB?**
MongoDB’s **$lookup** operator allows for the equivalent of an SQL **left outer join**, which combines documents from two collections based on a related field. It only supports left outer joins, which means every document in the "local" (primary) collection is returned, even if no matching documents are found in the "foreign" (secondary) collection. Non-matching documents from the foreign collection will result in empty arrays.

#### Syntax of `$lookup`:
```javascript
db.localCollection.aggregate([
  {
    $lookup: {
      from: "foreignCollection",    // Name of the foreign collection to join with
      localField: "<localField>",   // Field in the local collection
      foreignField: "<foreignField>", // Field in the foreign collection
      as: "<outputField>"           // Field name to store joined results
    }
  }
])
```

### **2. Example Scenario for $lookup Join**

Consider two collections:
- **Orders** collection, which contains the orders placed by customers.
- **Customers** collection, which contains customer information.

#### Orders Collection:
```json
[
  { "_id": 1, "item": "Notebook", "customer_id": 101, "quantity": 2 },
  { "_id": 2, "item": "Laptop", "customer_id": 102, "quantity": 1 },
  { "_id": 3, "item": "Tablet", "customer_id": 103, "quantity": 3 }
]
```

#### Customers Collection:
```json
[
  { "_id": 101, "name": "Alice", "email": "alice@example.com" },
  { "_id": 102, "name": "Bob", "email": "bob@example.com" },
  { "_id": 104, "name": "Charlie", "email": "charlie@example.com" }
]
```

### Performing a Join:

We can use `$lookup` to join the `orders` collection with the `customers` collection based on the `customer_id`.

```javascript
db.orders.aggregate([
  {
    $lookup: {
      from: "customers",           // Foreign collection name
      localField: "customer_id",   // Field from the local collection
      foreignField: "_id",         // Field from the foreign collection
      as: "customerDetails"        // Name of the output field for joined data
    }
  }
])
```

### Result:
```json
[
  {
    "_id": 1,
    "item": "Notebook",
    "customer_id": 101,
    "quantity": 2,
    "customerDetails": [
      { "_id": 101, "name": "Alice", "email": "alice@example.com" }
    ]
  },
  {
    "_id": 2,
    "item": "Laptop",
    "customer_id": 102,
    "quantity": 1,
    "customerDetails": [
      { "_id": 102, "name": "Bob", "email": "bob@example.com" }
    ]
  },
  {
    "_id": 3,
    "item": "Tablet",
    "customer_id": 103,
    "quantity": 3,
    "customerDetails": []  // No matching customer, result is an empty array
  }
]
```

In this result:
- Each order contains an array field `customerDetails` which stores the corresponding customer information.
- The third order does not have a matching customer in the `customers` collection, so `customerDetails` is an empty array.

### **3. $lookup with a Pipeline (Advanced Join)**
Starting from MongoDB 3.6, the **$lookup** operator supports joining with a **pipeline**. This is more flexible and powerful because it allows you to apply additional filtering, sorting, or transformation to the foreign collection before performing the join.

#### Example:
```javascript
db.orders.aggregate([
  {
    $lookup: {
      from: "customers",
      let: { customerId: "$customer_id" },  // Define variables for pipeline
      pipeline: [
        { $match: { $expr: { $eq: [ "$_id", "$$customerId" ] } } },
        { $project: { _id: 0, name: 1, email: 1 } }  // Select only specific fields
      ],
      as: "customerDetails"
    }
  }
])
```

Here, the join is based on `customer_id`, and only the `name` and `email` fields from the `customers` collection are included in the result.

### **4. Using $unwind to Flatten the Joined Data**
The result of `$lookup` is an array (even if there is only one matching document). To work with a single document instead of an array, you can use **$unwind**. It deconstructs an array field from the input documents to output a document for each element of the array.

#### Example with `$unwind`:
```javascript
db.orders.aggregate([
  {
    $lookup: {
      from: "customers",
      localField: "customer_id",
      foreignField: "_id",
      as: "customerDetails"
    }
  },
  { $unwind: "$customerDetails" }  // Flatten the array
])
```

### Result:
```json
[
  {
    "_id": 1,
    "item": "Notebook",
    "customer_id": 101,
    "quantity": 2,
    "customerDetails": { "_id": 101, "name": "Alice", "email": "alice@example.com" }
  },
  {
    "_id": 2,
    "item": "Laptop",
    "customer_id": 102,
    "quantity": 1,
    "customerDetails": { "_id": 102, "name": "Bob", "email": "bob@example.com" }
  }
]
```

Now each document has a single `customerDetails` object instead of an array.

### **5. Joining Collections with Different Fields**
Sometimes, you might need to join collections based on different fields, or even use computed values. MongoDB’s **aggregation pipeline** with `$lookup` allows you to define complex expressions.

#### Example:
You can use the `$expr` operator inside the `$match` stage of the pipeline to perform a join using an expression.

```javascript
db.orders.aggregate([
  {
    $lookup: {
      from: "customers",
      let: { customerId: "$customer_id" },
      pipeline: [
        { $match: { $expr: { $eq: [ "$_id", "$$customerId" ] } } }
      ],
      as: "customerDetails"
    }
  }
])
```

This is useful when you need to perform a join based on more complex logic or calculated values.

### **6. Performance Considerations**
- **Indexing**: Ensure that the fields used in the `$lookup` (both `localField` and `foreignField`) are properly indexed. This helps improve the performance of the join operation.
- **Large Collections**: MongoDB is not optimized for frequent cross-collection joins. For large datasets, joins may become slow, so it's better to denormalize the schema (embed related data within the documents) when possible.
- **Memory Usage**: Be mindful of memory usage when performing joins on large collections, as MongoDB's aggregation pipeline operates in memory. You can use the `allowDiskUse` option if the aggregation pipeline exceeds the memory limits.

### **7. Limitations of MongoDB Joins**
- **Only Left Outer Joins**: MongoDB only supports left outer joins, meaning that even if there is no match in the foreign collection, the document from the local collection will still be included in the result. There is no built-in support for inner joins, right joins, or full outer joins.
- **Join Across Databases**: The `$lookup` operator works only within a single database. It cannot join collections from different databases directly.
- **Joins on Arrays**: MongoDB can also perform joins using fields that are arrays. However, the results can become more complex, and performance may suffer if you don’t handle array fields carefully.

### **8. Example: Nested Joins**
MongoDB allows you to perform nested joins by including multiple `$lookup` stages in the aggregation pipeline. This can be useful when you need to combine data from more than two collections.

#### Example:
If you have three collections — `orders`, `customers`, and `products` — you can perform nested joins to include customer and product details in each order.

```javascript
db.orders.aggregate([
  {
    $lookup: {
      from: "customers",
      localField: "customer_id",
      foreignField: "_id",
      as: "customerDetails"
    }
  },
  { $unwind: "$customerDetails" },  // Flatten the customer details
  {
    $lookup: {
      from: "products",
      localField: "item",
      foreignField: "name",
      as: "productDetails"
    }
  },
  { $unwind: "$productDetails" }  //
```


In MongoDB, **views** are a way to create a **virtual collection** that does not store any data itself but provides a way to query data from other collections. Views allow you to define a dynamic query or transformation that MongoDB executes when the view is accessed. This can be useful for abstracting complex aggregation queries or for exposing a subset of data to applications with read-only access.

Views in MongoDB are **read-only**; you cannot modify data through a view. They are useful when you want to create a simplified or transformed version of the data for different use cases, such as analytics or restricted access.

### **1. Creating a View**

Views in MongoDB are created using the `db.createView()` method. The method requires the name of the view, the name of the source collection (or another view), and an aggregation pipeline that transforms the data.

#### **Syntax**:
```javascript
db.createView(
  "<viewName>",            // The name of the view
  "<sourceCollection>",     // The name of the source collection or view
  [<aggregationPipeline>]   // An array representing the aggregation pipeline
)
```

#### **Example**:
Suppose you have a `sales` collection that contains documents with sales data, and you want to create a view that shows only sales with amounts greater than 1000.

##### Sample `sales` Collection:
```json
[
  { "_id": 1, "item": "Laptop", "amount": 2000, "customer": "Alice" },
  { "_id": 2, "item": "Tablet", "amount": 500, "customer": "Bob" },
  { "_id": 3, "item": "Phone", "amount": 1500, "customer": "Charlie" }
]
```

##### Creating the View:
```javascript
db.createView(
  "highValueSales",   // Name of the view
  "sales",            // Source collection
  [
    { $match: { amount: { $gt: 1000 } } }  // Aggregation pipeline to filter sales
  ]
)
```

In this example:
- The view `highValueSales` will return only the documents from the `sales` collection where the `amount` is greater than 1000.

##### Querying the View:
```javascript
db.highValueSales.find()
```

##### Output:
```json
[
  { "_id": 1, "item": "Laptop", "amount": 2000, "customer": "Alice" },
  { "_id": 3, "item": "Phone", "amount": 1500, "customer": "Charlie" }
]
```

### **2. Working with Views**

- **Read-Only**: Views in MongoDB are **read-only**, so you can only perform read operations such as `find()` or aggregations on views. Any attempt to modify the data (e.g., `insert`, `update`, `delete`) through a view will result in an error.
  
  For example, the following would fail:
  ```javascript
  db.highValueSales.insert({ item: "Smartwatch", amount: 200 });
  ```
  This will result in an error like:
  ```
  Cannot modify a read-only view.
  ```

- **Aggregation Pipeline**: Views are based on an aggregation pipeline. This means you can apply complex transformations, filters, joins, or projections to the underlying data before it is presented in the view.

  For example, to create a view that shows only certain fields:
  ```javascript
  db.createView(
    "salesSummary", 
    "sales", 
    [
      { $project: { item: 1, amount: 1, customer: 1 } }  // Include only these fields
    ]
  )
  ```

- **Indexing**: Views do not have indexes of their own, but they can take advantage of indexes on the underlying collections. Therefore, it is important to ensure that the fields used in the view’s aggregation pipeline are indexed in the source collection for optimal performance.

### **3. Modifying a View**

You cannot directly modify a view once it is created. To change a view, you must drop the view and recreate it with the updated aggregation pipeline.

#### Dropping a View:
```javascript
db.highValueSales.drop()
```

After dropping the view, you can recreate it with a new pipeline or logic.

### **4. Creating Views with Joins**
MongoDB’s `$lookup` aggregation stage allows you to create views that join data from multiple collections. This is similar to performing SQL-style joins.

#### Example:
Consider two collections, `orders` and `customers`, and you want to create a view that combines customer information with each order.

##### Customers Collection:
```json
[
  { "_id": 1, "name": "Alice", "email": "alice@example.com" },
  { "_id": 2, "name": "Bob", "email": "bob@example.com" }
]
```

##### Orders Collection:
```json
[
  { "_id": 101, "item": "Laptop", "quantity": 1, "customer_id": 1 },
  { "_id": 102, "item": "Tablet", "quantity": 2, "customer_id": 2 }
]
```

##### Creating the View:
```javascript
db.createView(
  "customerOrders",
  "orders",
  [
    {
      $lookup: {
        from: "customers",           // Foreign collection
        localField: "customer_id",   // Field in the orders collection
        foreignField: "_id",         // Field in the customers collection
        as: "customerInfo"           // Output array field
      }
    },
    { $unwind: "$customerInfo" },    // Flatten the array
    { $project: { item: 1, quantity: 1, "customerInfo.name": 1, "customerInfo.email": 1 } }
  ]
)
```

##### Querying the View:
```javascript
db.customerOrders.find()
```

##### Output:
```json
[
  { "_id": 101, "item": "Laptop", "quantity": 1, "customerInfo": { "name": "Alice", "email": "alice@example.com" } },
  { "_id": 102, "item": "Tablet", "quantity": 2, "customerInfo": { "name": "Bob", "email": "bob@example.com" } }
]
```

In this example, the view `customerOrders` contains joined data from the `orders` and `customers` collections.

### **5. Performance Considerations**

- **No Data Storage**: Views do not store data, so every time you query a view, MongoDB runs the aggregation pipeline defined for the view. This means that the performance of querying a view is equivalent to running the aggregation pipeline manually each time.
  
- **Indexes**: Since views don’t store data, you cannot define indexes on them. However, queries against a view can use indexes defined on the source collection(s).

- **Complex Aggregations**: Views based on complex aggregation pipelines (e.g., multiple stages, $lookup, $group) can be slower to query, especially on large datasets. Optimizing queries by indexing and limiting pipeline complexity is important for performance.

### **6. Use Cases for Views**

- **Data Abstraction**: Views provide a way to hide the complexity of data transformation and provide a simplified interface to users or applications.
- **Security and Access Control**: You can use views to expose only a subset of the data to users with restricted permissions.
- **Reusable Queries**: If you have a common query or transformation that is used across multiple applications, creating a view allows you to avoid repeating the same query logic.
- **Data Aggregation**: For reports or analytics, views can provide a dynamic way to aggregate or transform data without creating new collections or duplicating data.

### **7. Limitations of MongoDB Views**

- **Read-Only**: Views are inherently read-only, meaning you cannot modify the underlying data through a view. Any write operations must be performed on the source collection directly.
- **No Materialization**: Views are computed in real-time when queried, and they don’t store the result of the aggregation. This means performance can be slower compared to querying a materialized collection.
- **No Indexes on Views**: Since views don’t store data, you cannot create indexes on them. Indexes on the source collection(s) should be utilized for improving query performance.

### **8. Materialized Views**
MongoDB does not natively support **materialized views** (views that store a copy of the data and are refreshed periodically). However, you can simulate materialized views by creating collections and periodically running aggregation pipelines to update the collection with the desired data.

---

In summary, MongoDB views are a powerful tool for creating virtual collections that transform or filter data dynamically using aggregation pipelines. They allow for data abstraction, simplification, and security, but come with performance and write limitations that need to be considered when designing a system.


## Special Features in MangoDB

Here’s a concise overview of some of MongoDB's key features, along with code examples to illustrate their use:

### 1. **Document-Oriented Storage**
Documents are stored in BSON format, which is similar to JSON.

```javascript
db.users.insertOne({
  name: "Alice",
  age: 30,
  hobbies: ["reading", "traveling"]
});
```

### 2. **Scalability (Sharding)**
MongoDB can distribute data across multiple servers.

```javascript
sh.addShard("shard01/exampledb");
```

### 3. **High Performance**
MongoDB provides fast read and write operations.

```javascript
db.products.insertMany([
  { item: "Laptop", qty: 100 },
  { item: "Tablet", qty: 200 }
]);
```

### 4. **Rich Query Language**
You can perform complex queries easily.

```javascript
db.users.find({ age: { $gt: 25 } });
```

### 5. **Aggregation Framework**
Allows data transformation and analysis.

```javascript
db.orders.aggregate([
  { $group: { _id: "$customerId", total: { $sum: "$amount" } } }
]);
```

### 6. **Indexing**
Create indexes to speed up queries.

```javascript
db.users.createIndex({ name: 1 });
```

### 7. **Replication**
Set up replication for high availability.

```javascript
rs.initiate();
```

### 8. **Flexible Schema**
Documents can have different structures.

```javascript
db.orders.insertOne({
  orderId: 1,
  items: [{ product: "Book", qty: 1 }],
  status: "shipped"
});

db.orders.insertOne({
  orderId: 2,
  items: [{ product: "Pen", qty: 2 }],
  deliveryDate: new Date(),
  status: "pending"
});
```

### 9. **Geospatial Queries**
Support for geospatial data and queries.

```javascript
db.places.createIndex({ location: "2dsphere" });

db.places.find({
  location: {
    $geoWithin: {
      $centerSphere: [[-73.97, 40.77], 1 / 3963.2]
    }
  }
});
```

### 10. **Text Search**
Full-text search capabilities.

```javascript
db.articles.createIndex({ title: "text", content: "text" });

db.articles.find({ $text: { $search: "MongoDB" } });
```

### 11. **Transactions**
Support for multi-document transactions.

```javascript
const session = db.getMongo().startSession();

session.startTransaction();
try {
  session.getDatabase("shop").orders.insertOne({ ... }, { session });
  session.getDatabase("shop").inventory.updateOne({ ... }, { $inc: { qty: -1 } }, { session });
  session.commitTransaction();
} catch (error) {
  session.abortTransaction();
}
```

### 12. **Change Streams**
Listen for real-time data changes.

```javascript
const changeStream = db.collection.watch();
changeStream.on("change", (change) => {
  console.log(change);
});
```

### 13. **Data Lake Integration**
Query data across different storage formats.

```javascript
// Example of querying a data lake would require specific setup in Atlas.
```

### 14. **Aggregation Pipeline Optimization**
Use optimized aggregation pipelines.

```javascript
db.sales.aggregate([
  { $match: { date: { $gte: new Date("2023-01-01") } } },
  { $group: { _id: "$productId", totalSales: { $sum: "$amount" } } }
]);
```

### 15. **Cloud-Native Solutions**
Deploy MongoDB in the cloud with Atlas.

```javascript
// Use the Atlas UI or CLI for deployment configurations.
```

### 16. **Community and Ecosystem**
Leverage libraries and tools.

```javascript
// Example using Mongoose for schema definition and validation.
const mongoose = require('mongoose');

const userSchema = new mongoose.Schema({
  name: String,
  age: Number,
});

const User = mongoose.model('User', userSchema);
```

### 17. **Data Model Flexibility**
Store nested documents.

```javascript
db.blogs.insertOne({
  title: "Introduction to MongoDB",
  content: "MongoDB is a NoSQL database...",
  comments: [
    { user: "John", message: "Great article!", date: new Date() },
    { user: "Jane", message: "Very informative.", date: new Date() }
  ]
});
```

### 18. **Schema Validation**
Define validation rules.

```javascript
db.createCollection("products", {
  validator: {
    $jsonSchema: {
      bsonType: "object",
      required: ["name", "price"],
      properties: {
        name: {
          bsonType: "string",
          description: "must be a string and is required"
        },
        price: {
          bsonType: "number",
          minimum: 0,
          description: "must be a positive number and is required"
        }
      }
    }
  }
});
```

These features make MongoDB a powerful and flexible database solution suitable for a variety of applications.

