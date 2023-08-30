# MongoDB Shell Commands

#### MongoDB is a popular and versatile NoSQL database management system known for its flexibility, scalability, and speed. It stores data in a flexible, JSON-like format, making it well-suited for a wide range of applications, from small projects to large-scale, data-intensive systems. MongoDB is designed to handle unstructured, semi-structured, and structured data, making it a powerful choice for modern, data-driven applications.

## Table of Contents

- [Show Databases](#show-databases)
- [Show Collections](#show-collections)
- [Switch Database](#switch-database)
- [Find All Documents in a Collection](#find-all-documents-in-a-collection)
- [Insert a Document](#insert-a-document)
- [Find a Single Document](#find-a-single-document)
- [Insert Multiple Documents](#insert-multiple-documents)
- [Filter Documents with Equal Condition](#filter-documents-with-equal-condition)
- [Filter Documents with Comparison Operators](#filter-documents-with-comparison-operators)
- [AND Operation](#and-operation)
- [Proper AND Operation Format](#proper-and-operation-format)
- [OR Operation](#or-operation)
- [Sorting Results](#sorting-results)
- [Limit Results](#limit-results)
- [Count Documents](#count-documents)
- [Count Documents with Filter](#count-documents-with-filter)
- [Projection](#projection)
- [Update Documents](#update-documents)
- [Delete Documents](#delete-documents)

---

## Show Databases
This command displays a list of all available databases.
```mongodb
show dbs
```

## show collections
Use this command to see all the collections present in the current database
```mongodb
show collections
```
## Switch Database
This command switches to the specified database. If the database doesn't exist, it will be created in memory. Data is only saved when you perform actual operations within the database.
```mongodb
use <dbName>
```

## Find All Documents in a Collection
Retrieve all documents present in the specified collection
```mongodb 
db.<collectionName>.find()
```

## Insert a Document
This command creates a collection (if it doesn't exist) and inserts a single document into it.
```mongodb
db.<collectionName>.insertOne({"title": "iPhone"})
```

## Find a Single Document
Use this command to find a single document based on the specified filter.
```mongodb
db.<collectionName>.findOne({"title": "iPhone"})
```

## Insert Multiple Documents
Retrieve documents where the specified field equals a given value.
```mongodb
db.<collectionName>.find({"title": {$eq: "iPhone"}})
```

## Filter Documents with Comparison Operators
Filter documents based on comparison operators like greater than, less than, equal to, etc.
```mongodb
db.<collectionName>.find({"rating": {$gt: 4.5}})
```

## AND Operation
Perform an AND operation to filter documents using multiple conditions.
```mongodb
db.<collectionName>.find({"rating": {$gt: 4.5}, "id": {$gt: 6}})
```

## Proper AND Operation Format
This is the proper format for applying an AND operation in MongoDB queries.
```mongodb
db.<collectionName>.find({$and: [{"rating": {$gt: 4.5}}, {"id": {$gt: 6}}]})
```

## OR Operation
Perform an OR operation to filter documents using multiple conditions.
```mongodb
db.<collectionName>.find({$or: [{"rating": {$gt: 4.5}}, {"id": {$gt: 3}}]})
```

## Sorting Results
Sort the filtered results in ascending order based on a specific field (price in this case).
```mongodb
db.<collectionName>.find({$or: [{"rating": {$gt: 4.5}}, {"id": {$gt: 3}}]}).sort({"price": 1})
```

## Limit Results
Limit the number of results to display, in this case, only the first 2 records after sorting.
```mongodb
db.<collectionName>.find({$or: [{"rating": {$gt: 4.5}}, {"id": {$gt: 3}}]}).sort({"price": 1}).limit(2)
```

## Count Documents
Get the total count of documents in the collection.
```mongodb
db.<collectionName>.countDocuments()
```

## Count Documents with Filter
Count documents in the collection that meet a specific condition.
```mongodb 
db.<collectionName>.countDocuments({"price": {$gt: 500}})
```

## Projection
Projection allows you to specify which fields to include or exclude in the query results.
```mongodb
db.<collectionName>.find({filter}, {projection})
```

- ## Example 1 - Include 'title' Field
    Include only the 'title' field in the query results.
    ```mongodb
    db.<collectionName>.find({"price": {$gt: 500}}, {"title": 1})
    ```

- ## Example 2 - Include 'title' and 'price' Fields
    Include both 'title' and 'price' fields in the query results.
    ```mongodb
    db.<collectionName>.find({"price": {$gt: 500}}, {"title": 1, "price": 1})
    ```

- ## Example 3 - Exclude '_id' Field
    Include 'title' and 'price' fields while excluding the '_id' field.
    ```mongodb
    db.<collectionName>.find({"price": {$gt: 500}}, {"title": 1, "price": 1, "_id": 0})
    ```

# Update Documents

## Update a Single Document
Use $set to update a field in a document. If the field doesn't exist, it will be created.
```mongodb
db.<collectionName>.updateOne({"id": 1}, {$set: {"price": 999}})
```

## Update a Single Document with Upsert
This updates a document if found or creates a new one if not found (upsert).
```mongodb
db.<collectionName>.updateOne({"id": 1}, {$set: {"price": 999}}, {upsert: true})
```

## Update Multiple Documents
Update multiple documents based on a filter condition.
```mongodb
db.<collectionName>.updateMany({"id": {$gt: 3}}, {$set: {"price": 999}})
```

## Replace a Document
This command replaces the entire document, use with caution.
```mongodb
db.<collectionName>.updateOne({"id": 1}, {"price": 999})
```

# Delete Documents

## Delete single Documents
Find and delete a single document based on a filter.
```mongodb
db.<collectionName>.deleteOne({"id": 3})
```

## Delete a Document by ObjectId
Delete a document using its ObjectId.
```mongodb
db.<collectionName>.deleteOne({"_id": ObjectId('6qf3454r43ofn34543')})
```

## Delete Multiple Documents
Delete all documents that match the given filter condition.
```mongodb
db.<collectionName>.deleteMany({"price":999})
```
