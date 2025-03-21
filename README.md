# Mongodb

Mongodb is a NoSQL (non-relational) database. IT stroes data in a type of JSON format Called **BSON**.

## Database

A database is a collection of data stored in a format that can easily be accessed.

## NOSQL Database

```mongodb
<!-- -----------------collection----------------- -->

<!-- document 1 -->
{
    name: "Ram Kumar",
    age: 21,
    gender: "MALE"
}

<!-- document 2 -->
{
    name: "Ram Kumar",
    age: 21,
    gender: "MALE"
}
```

## Datatype

| JSON | BSON (Binary JSON)     |
| :-------- | :------- |
| `String` | `String` | 
| `Number` | `Double` | 
| `Boolean` | `32bit and 64bit Integer` | 
| `Array` | `Boolean` | 
| `Object` | `Array` | 
| `Null` | `Object` | 
|| `Null` | 
|| `Regular Expression` | 
|| `Timestamp` | 
|| `Date` | 
|| `ObjectId` | 

#

> [!NOTE]
> In date format is ```ISODate("yyyy-mm-ddThh:mm:ssZ")```


## Benifit
* Flexible in schema design
* Horizontal scalability through sharding
* High performance for read and write operation
* powerful query language 
* Built in replication for high vaiblability
* Geospatial data support
* JSON like BSON data format
* Real time analytics capability
* easy integration with big data tools
 open-source and community-driven

## ***Create Database, Show Database & Delete Database Command***

``` 
use database_name;
```
``` use ``` keyword  work is two type one is create new database and another one is if exist this database then switch to thst database 

``` 
show dbs;
```
``` show dbs ``` use for show all existing databases.

``` 
db.dropDatabase();
```
``` db.dropDatabase() ``` use for delete database.


## ***Create, Rename, Show & Delete Collection Command***

``` 
db.createCollection("collection_name"); 
```
``` db.createCollection("collection_name") ``` use for Create Collection.

``` 
db.old_name.renameCollection("new_name"); 
```
``` db.old_name.renameCollection("new_name") ``` use for Rename Collection.

``` 
show collections; 
```
``` show collections ``` use for show all Collections.

``` 
db.collection_name.drop(); 
```
``` db.collection_name.drop()``` use for Delete Collection.

## ***Insert Command***
Insert command are two type those are -
```
db.collection_name.insertOne({field1 : "Value", field2: "value",.....})
```
use for Insert One Document in the collection

```
db.collection_name.insertMany(
    {field1 : "Value", field2: "value",.....},
    {field1 : "Value", field2: "value",.....}, 
    )
```
use for insert many document in the collection at a time.

## ***Validate Schema Command***
create a collection and give some validation.
```
db.createCollection("collection_name",{
    validator:{
        $jsonSchema:{
            title:"your message",
            requied:["field1","field2",...],
            propertices:{
                field1:{
                    bsonType: "String",
                    description: "your message"
                },

                field2:{
                    bsonType: "int",
                    minimum: 2,
                    maximum:10,
                    description: "youre message"
                },
                .
                .
                .
                .

            }
        }
    }
})
```
existing collection validation
```
db.runCommand({
    collMod: "collection_name",
        validator:{
            $jsonSchema:{
                requied:["field1","field2",...],
                propertices:{
                    field1:{
                        bsonType: "String",
                        description: "your message"
                    },

                    field2:{
                        bsonType: "int",
                        minimum: 2,
                        maximum:10,
                        description: "youre message"
                    },
                    .
                    .
                    .
                    .

                }
            }
        }
    })
```
## ***Update Command***
Insert command are two type those are -
```
db.collection_name.updateOne(
    {field1 : "Value"},
    {$set: {update_field: "update_value"}}
)
```
use for update One Document in the collection

```
db.collection_name.updateMany(
    {field1 : "Value"},
    {$set: {update_field: "update_value"}}
)
```
use for update many document in the collection at a time.

### Operators For Update Command
* ``` $unset ```: Remove the field from the document.
* ``` $rename ```: Renames the fields.
* ```$mul ```: Multiplies the field value.
* ``` $inc ```: Increments the field value.
* ``` $currentDate ```: Sets the field value to the current date.

### Array Operators For Update Command
* ``` $push ```: adds an element to an array.
* ``` $pop ```: Removes the first or last element of an array.
* ```$pull ```: Remove all elements from an array that match the query.
* ``` $pullAll ```: Remove all.
* ``` $addToSet ```: Check first then adds distinct element to an array.

## ***Replace Command***

```
db.collection_name.replaceOne(
    {field1 : "Value"},
    {$set: {new_field: "new_value"}}
)
```
use for replace One Document in the collection

## ***Delete Command***
Insert command are three type those are -
```
db.collection_name.deleteOne(
    {field1 : "Value"}
)
```
use for delete One Document in the collection

```
db.collection_name.deleteMany(
    {field1 : "Value"}
)
```
use for delete many document in the collection at a time.
```
db.collection_name.deleteMany({})
```
use for delte all document







<!-- 
[MIT](https://choosealicense.com/licenses/mit/) -->