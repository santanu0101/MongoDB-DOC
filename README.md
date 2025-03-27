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


## Find Command
* use for find value in the collection
```
    db.collection_name.find({field1: "value"});

    db.collection_name.findOne({field1: "value"});
```
* use for find value but which value we need to show that define using projection
```
    db.collection_name.find(
        {field1: "value"},
        {filed2: 1, filed3: 1, field4: 0} //1 is mean show and 0 mean not show
    );
```
OR
```
db.collection_name.find({field1: "value"})
    .projection({filed2: 1, filed3: 1, field4: 0});
```

### Find with count record

```
db.collection_name.find().count();
```

### Find with sorthing order

```
db.collection_name.find().sort({field: 1})
```
> [!NOTE]
> assending order: 1,
> desending order: -1

### Find with limited records
```
db.collection_name.find().limit(3); // 3 record show
```
```
db.collection_name.find().limit(3).skip(3); // 1,2,3 skip then 3 record show
```

## Comparison Operator
* $eq - values are equal ```{"age":{$eq: 20}}```
* $ne - values are not equal ```{"age":{$ne: 20}}```
* $gt - values are greater than another value ```{"age":{$gt: 20}}```
* $gte - values are greater than equal to another value ```{"age":{$gte: 20}}```
* $lt - values are less than or equal to another value ```{"age":{$lt: 20}}```
* $lte - values are less than or equal to another value ```{"age":{$lte: 20}}```
* $in - values are matched within an array ```{"age":{$in: [20,24,28]}}```
* $nin - values are not matched within an array ```{"age":{$nin: [20,24]}}```
## Logical operator

* ```$and```- Returns documents where both queries match ```{$and:[condition1, condition2]}```
* ```$or```- Returns documents where either query matches ```{$or:[condition1, condition2]}```
* ```$nor```- Returns documents where both queries fail to match ```{$nor:[condition1, condition2]}```
* ```$not```- Returns documents where the query does not match ```{$not:[condition]}```

### Some Example of Logical Operators
* AND operator:
    ```
    db.student.find({$and:[
        {"age": {$gt: 20}},
        {"age": {$lt: 23}},
    ]})
    ```
* OR Operator:
    ```
    db.student.find({$or:[
        {"age": {$gt: 20}},
        {"class": {$eq: "Btech"}},
    ]})
    ```
* NOR Operator: 
    ```
    db.student.find({$nor:[
        {"age": {$gt: 20}},
        {"class": {$eq: "Btech"}},
    ]}); 
    ```
* NOT Operator:
    ```*
    db.student.find({"age": {$not: {$gte: 20}}})
    ```

## Element Query Operator
* ```$exists```- Matches documents that have the specified field ```{field: {$exist:<boolean>}}``` true/false.
* ```$type```- Selects documents if a field is of the specified type ```{field:{$type:<type>}}```.

### Some Example of Element Query Operators
* Exists Operator:
    ```
    db.students.find({
        class: {$exists: false}
    }); 
    db.students.find({
        class: {$exists: true}
    }); 
    ```
* Type Operator:
    ```
    db.students.find({ age: {$type: "string"}});
    ```
## Evaluation Query Operators
> [!NOTE]
> This Operators using for Advance search.
* ```$regex```- Matchs string fields to a pattern ```{field:{$regex:/pattern/<options}}``` like "^S" mean starting letter 'S', "an$" mean last letter 'an'.
* ```$expr```- Allows field comparisons within documents ```{$expr:{<expression>}}``` like {catagory:"food", budget:400, spent:450}.
* ```$mod```- Matches numbers based on remainder ```{field: {$mod:[divisor, remainder]}}``` like {age:{$mod:[2,0]}}.
* ```$jsonSchema```-validate document =s against the given JSON Schema.
### Some Example of Evaluation Query Operators
* Regex Operator:

    ```
    db.students.find({name:{$regex:"Das"}});
    ```
    ```
    db.students.find({name:{$regex:/das/i}});
    ```
    ```
    db.students.find({name:{$regex:"^S"}});
    ```
    ```
    db.students.find({name:{$regex:"as$"}});
    ```
* Expr Operator:
    ```
    db.monthlyBudget.find({
        $expr:{$gt: ["$spent", "$budget"]} //spent > budget compareing 
    });
    ```
    ```
    db.sales.find({
        $expr:{$gt: ["$price", {$multiply: ["$cost",1.2]}]}
    });
    ```
* Mod Operator:
    ```
    db.sales.find({cost: {$mod: [7,0]}});
    ```

## FindOneAndUpdate() Method
```
db.collection_name.findOneAndUpdate(
    {field:"Value"},
    {$set: {upadted_field: "new_value"}},
    {Options} // projection, returnDocument="after"/"befor", sort=1/-1, upsert=true/false
);
```
### Examples
```
db.students.findOneAndUpdate(
    {name: "Santanu Raj"},
    {$set: {age: 30}},
    {returnDocument: "after"} //after updated record return
)

db.students.findOneAndUpdate(
    {name: "Santanu Raj"},
    {$set: {age: 30}},
    {
        returnDocument: "after",
        projection: {name:1, age:1, _id:0} //1 means show, 0 means not show

    } //after updated record return
)

db.students.findOneAndUpdate(
    {name: "Suvam Raj"},
    {$set: {age: 30, class: "BIT"}},
    {
        returnDocument: "after",
        projection: {name:1, age:1, _id:0}, //1 means show, 0 means not show
        upsert: true //if this hole record not find then insert that record in collection
        
    } //after updated record return
)

db.students.findOneAndUpdate(
    {name: "Jack Das"},
    {$set: {class: "MCA"}},
    {sort: {age:1}} 
)
```
## FindOneAndReplace() Method
```
db.collection_name.findOneAndReplace(
    {field:"Value"},
    {filed:"value", field1:"value1", field2: "value2"},
    {Options} 
);
```
### Examples
```
db.students.findOneAndReplace(
    {name: "Jack Das"},
    {name: "Jone due", age: 20, class: "Mtech"},
    {returnDocument: "after"} 
)
```
## findOneAndDelete() Method
```
db.collection_name.findOneAndDelete(
    {field:"value"},
    {options} // projection, sort
)
```
### Examples
```
db.students.findOneAndDelete(
    {name: "Jack Das"} 
)

db.students.findOneAndDelete(
    {name: "Jack Das"},
    {projection: {name:1, age:1, _id:0}} 
)

db.students.findOneAndDelete(
    {name: "Jack Das"},
    {
        projection: {name:1, age:1, _id:0},
        sort:{age:1}
    } 
)

```






<!-- 
[MIT](https://choosealicense.com/licenses/mit/) -->