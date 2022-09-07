# MongoDb Cheatsheet

Show the version of a database server
```
db.version()
```
Returns some staticstics about MongoDB server
```
db.stats
```
List all database in MongoDb server
```
show dbs
```
List all database in the MongoDb server
```
use <dbname>
```
Create new collection in the database
```
db.createCollection("name")
```
Show all Collections in the database
```
show collections

```
##Inserting document

Insers one document into the collection
```
insertOne({...})
Syntax:
db.<collectionName>.insertOne({})
```

Insert many into the collection
```
insertMany([{},{}...{}])
Syntax:
db.<collectionName>.insertMany
([{}, {}...{}])
```

## Finding document in the collection
Returns all the document in the collection that matches the query. It will return an empty array if there is no document in the collection.if an empty object ({}) is passed in a query it will return all the document in the collection
```
find({query})
```
Returns a single document that matches the query
```
findone({query})
```

### Match by field name and it’s exact value
```
Syntax
{<fieldName1> : <value1>, <fieldName1> : <value1>}
Example
{"name": "John Doe" }
{“age”: 30}
{gender": "male", "maritalStatus" :"“single"}
```
*** NB ***
comma (,) represents AND

### QUERY OPERATORS
```
$or $eq $lt
$and $ne $gt
$gte $lte $in
$nin $regex
```
### COMPARISON OPERATORS
Operators add conditions that compares two or more values
```
Syntax
{<fieldName1>: {<operator1>: <value1>}, …}

Examples
{age": {$gt : 25}}
{“age”: {$lt : 25}}
{"favouriteFruit": {"$in": ["apple", "orange"]}}#
```
### This comparison operators require an ARRAY
```
Syntax
{<fieldName1>: { <operator1>: [ <value1>,
<value2>] }, …}
Examples
{"eyeColor": {"$in": ["blue", "brown"]}}
{"favouriteFruit": {"$nin": ["apple", "orange"]}}
```

### "AND" OPERATOR
Logically combines multiple conditions. Resulting documents
must much ALL conditions
```
Syntax
{ $and: [ { <condition1> }, { <condition2> } … ] }
Example
{ $and: [ {"gender" : male"} ,"“age" : 25 } ] }
```
 *** NB ***
 Explicit $and MUST be used if conditions contains same field or
operator

