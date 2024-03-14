# MongoDB Notes

<!-- https://www.tutorialspoint.com/mongodb/mongodb_create_collection.htm -->

MongoDB is an open-source document database and leading NoSQL database. MongoDB is written in C++.

MongoDB is a cross-platform, document oriented database that provides, high performance, high availability, and easy scalability. MongoDB works on concept of collection and document.


Database
Database is a physical container for collections. Each database gets its own set of files on the file system. A single MongoDB server typically has multiple databases.

Collection
Collection is a group of MongoDB documents. It is the equivalent of an RDBMS table. A collection exists within a single database. Collections do not enforce a schema. Documents within a collection can have different fields. Typically, all documents in a collection are of similar or related purpose.

Document
A document is a set of key-value pairs. Documents have dynamic schema. Dynamic schema means that documents in the same collection do not need to have the same set of fields or structure, and common fields in a collection's documents may hold different types of data.



*   _id: ObjectId(7df78ad8902c):

_id is a 12 bytes hexadecimal number which assures the uniqueness of every document.

12 bytes first 4 bytes for the current timestamp, next 3 bytes for machine id, next 2 bytes for process id of MongoDB server and remaining 3 bytes are simple incremental VALUE.


Data Model Design:

1. Embedded Data Model (also known as de-normalized data model):

embed all the related data in a single document

For example, assume we are getting the details of employees in three different documents namely, Personal_details, Contact and, Address, you can embed all the three documents in a single one as shown below −

```js

{
	_id: ,
	Emp_ID: "10025AE336"
	Personal_details:{
		First_Name: "Radhika",
		Last_Name: "Sharma",
		Date_Of_Birth: "1995-09-26"
	},
	Contact: {
		e-mail: "radhika_sharma.123@gmail.com",
		phone: "9848022338"
	},
	Address: {
		city: "Hyderabad",
		Area: "Madapur",
		State: "Telangana"
	}
}


```


2. Normalized Data Model

you can refer the sub documents in the original document, using references. For example, you can re-write the above document in the normalized model as:
company> db.stud.find({ $and : [ {hobbies : "cricket"},{ hobbies: {$ne:"dancing" }  } ]  } )
[
  {
    _id: ObjectId('65e703be4ee797c1963427cb'),
    name: 'ram',
    age: 10,
    hobbies: [ 'cricket', 'mobile games', 'hocky' ]
  }
]
Employee:

```js
{
	_id: <ObjectId101>,
	Emp_ID: "10025AE336"
}

```

Personal_details:

```js
{
	_id: <ObjectId102>,
	empDocID: " ObjectId101",
	First_Name: "Radhika",
	Last_Name: "Sharma",
	Date_Of_Birth: "1995-09-26"
}

```

Contact:

```js
{
	_id: <ObjectId103>,
	empDocID: " ObjectId101",
	e-mail: "radhika_sharma.123@gmail.com",
	phone: "9848022338"
}

```

Address:

```js
{
	_id: <ObjectId104>,
	empDocID: " ObjectId101",
	city: "Hyderabad",
	Area: "Madapur",
	State: "Telangana"
}

```



Considerations while designing Schema in MongoDB

1. Design your schema according to user requirements.

2. Combine objects into one document if you will use them together. Otherwise separate them (but make sure there should not be need of joins).

3. Duplicate the data (but limited) because disk space is cheap as compare to compute time.

4. Do joins while write, not on read.

5. Optimize your schema for most frequent use cases.

6. Do complex aggregation in the schema.



Create or switch existing database:

```js
use DATABASE_NAME
```

To check your currently selected database, use the command db

```js
>db
mydb

```

If you want to check your databases list, use the command show dbs.

>show dbs
local     0.78125GB
test      0.23012GB


Basic syntax of dropDatabase() command is as follows −

db.dropDatabase()


* MongoDB db.createCollection(name, options) is used to create collection.

Parameter	Type	Description
Name	String	Name of the collection to be created
Options	Document	(Optional) Specify options about memory size and indexing



Field --	Type	-- Description

capped --	Boolean --	(Optional) If true, enables a capped collection. Capped collection is a fixed size  collection that automatically overwrites its oldest entries when it reaches its maximum size. If you specify true, you need to specify size parameter also.


autoIndexId --	Boolean --	(Optional) If true, automatically create index on _id field.s Default value is false.

size --	 number --	(Optional) Specifies a maximum size in bytes for a capped collection. If capped is true, then you need to specify this field also.

max --	number --	(Optional) Specifies the maximum number of documents allowed in the capped collection.


While inserting the document, MongoDB first checks size field of capped collection, then it checks max field.



* Basic syntax of createCollection() method without options is as follows −

>use test
switched to db test
>db.createCollection("mycollection")
{ "ok" : 1 }
>


You can check the created collection by using the command show collections.

>show collections
mycollection
system.indexes




The following example shows the syntax of createCollection() method with few important options −

company> db.createCollection("policy", { capped : true, autoIndexId:true, size: 614200, max: 1000  })


e.g, if we've set maz as 3 then after 3 insertion next value to be insert at last and first value will be deleted.



* MongoDB's db.collection.drop() is used to drop a collection from the database.


Datatypes in mongodb:


1. String − This is the most commonly used datatype to store the data. String in MongoDB must be UTF-8 valid.

2. Integer − This type is used to store a numerical value. Integer can be 32 bit or 64 bit depending upon your server.

3. Boolean − This type is used to store a boolean (true/ false) value.

4. Double − This type is used to store floating point values.

5. Min/ Max keys − This type is used to compare a value against the lowest and highest BSON elements.

6. Arrays − This type is used to store arrays or list or multiple values into one key.

7. Timestamp − ctimestamp. This can be handy for recording when a document has been modified or added.

8. Object − This datatype is used for embedded documents.

9. Null − This type is used to store a Null value.

10. Symbol − This datatype is used identically to a string; however, it's generally reserved for languages that use a specific symbol type.

11. Date − This datatype is used to store the current date or time in UNIX time format. You can specify your own date time by creating object of Date and passing day, month, year into it.

12. Object ID − This datatype is used to store the document’s ID.

13. Binary data − This datatype is used to store binary data.

14. Code − This datatype is used to store JavaScript code into the document.

15. Regular expression − This datatype is used to store regular expression.



Insert in mongodb:

db.COLLECTION_NAME.insert(document)

we can use .insertOne() or .insertMany() or.updateOne({upsert:true}) as well


using insert we can insert many documents in []



* find() :

db.COLLECTION_NAME.find()

db.COLLECTION_NAME.findOne()



* The pretty() Method:

To display the results in a formatted way, you can use pretty() method.


db.COLLECTION_NAME.find().pretty()



---

RDBMS Where Clause Equivalents in MongoDB


1. Equality	==>	db.mycol.find({"by":"tutorials point"}) ==>	where by = 'tutorials point'

2. Less Than ==> db.mycol.find({"likes":{$lt:50}}) ==> where likes < 50

3. Less Than Equals ==> db.mycol.find({"likes":{$lte:50}}) ==>	where likes <= 50

4. Greater Than	==>	db.mycol.find({"likes":{$gt:50}}) ==>	where likes > 50

5. Greater Than Equals ==>	db.mycol.find({"likes":{$gte:50}}) ==>	where likes >= 50

6. Not Equals	==>	db.mycol.find({"likes":{$ne:50}}) ==>	where likes != 50

7. Values in an array	==>	db.mycol.find({"name":{$in:["Raj", "Ram", "Raghu"]}}) ==>	Where name matches any of the value in :["Raj", "Ram", "Raghu"]

8. Values not in an array	==>	db.mycol.find({"name":{$nin:["Ramu", "Raghav"]}}) ==>	Where name values is not in the array :["Ramu", "Raghav"] or, doesn’t exist at all


---

* AND in MongoDB

>db.mycol.find({ $and: [ {<key1>:<value1>}, { <key2>:<value2>} ] })


company> db.stud.find({ $and : [ {hobbies : "cricket"},{ hobbies: {$ne:"dancing" }  } ]  } )


[
  {
    _id: ObjectId('65e703be4ee797c1963427cb'),
    name: 'ram',
    age: 10,
    hobbies: [ 'cricket', 'mobile games', 'hocky' ]
  }
]



* or


>db.mycol.find(
   {
      $or: [
         {key1: value1}, {key2:value2}
      ]
   }
).


company> db.stud.find({ $or : [ {hobbies:"cricket"}, {hobbies:"trekking"}  ]  })


[
  {
    _id: ObjectId('65e703be4ee797c1963427cb'),
    name: 'ram',
    age: 10,
    hobbies: [ 'cricket', 'mobile games', 'hocky' ]
  },
  {
    _id: ObjectId('65e703be4ee797c1963427cd'),
    name: 'virat',
    age: 21,
    hobbies: [ 'cricket', 'dancing', 'cooking' ]
  },
  {
    _id: ObjectId('65e703be4ee797c1963427ce'),
    name: 'rahul',
    age: 31,
    hobbies: [ 'trekking', 'swimming', 'basketball' ]
  }
]



* nor

company> db.stud.find({ $nor : [ {hobbies:"cricket"}  ]  })
[
  {
    _id: ObjectId('65e703be4ee797c1963427cc'),
    name: 'sham',
    age: 17,
    hobbies: [ 'football', 'tennis', 'reading' ]
  },
  {
    _id: ObjectId('65e703be4ee797c1963427ce'),
    name: 'rahul',
    age: 31,
    hobbies: [ 'trekking', 'swimming', 'basketball' ]
  }
]
db.inventory.find( { price: { $not: { $gt: 1.99 } } } )



* not 

db.inventory.find( { price: { $not: { $gt: 1.99 } } } )


* Mongodb update query: 

update is deprecated, so use updateOne, updateMany, bulkWrite

company> db.stud.updateOne({name:"virat"},{$set : { age:30 } })
{
  acknowledged: true,
  insertedId: null,
  matchedCount: 1,
  modifiedCount: 1,
  upsertedCount: 0
}

* Remove any property from document ($unset)

company> db.employee.updateOne({name:"yogesh"},{$unset:{age:""}})


---

company> db.stud.update( {hobbies:"cricket"},{$set : {age:100 }},{multi:true}  )
{
  acknowledged: true,
  insertedId: null,
  matchedCount: 2,
  modifiedCount: 2,
  upsertedCount: 0
}



* findOneAndUpdate

db.stud.findOneAndUpdate({name:"virat"},{$addToSet:{hobbies:"pc games"}})


company> db.employee.updateOne({name:"yogesh"},{$set:{age:33 }})


company> db.employee.updateMany({age:{$gt : 30}}, {$set:{age:18}})

company> db.employee.updateMany({name:{$in:["I","t"]}},{$set: {name:"test"}}  )


Mongodb delete:


db.employee.remove({name:"test",age:18})

Collection.remove() is deprecated. Use deleteOne, deleteMany, findOneAndDelete, or bulkWrite.


company> db.employee.deleteOne({name:"test"})


remove all 

db.employee.deleteMany()



* The Limit() Method:

To limit the records in MongoDB, you need to use limit() method. The method accepts one number type argument, which is the number of documents that you want to be displayed.


>db.COLLECTION_NAME.find().limit(NUMBER)
company> db.employee.find().limit(2)


* MongoDB Skip() Method
Apart from limit() method, there is one more method skip() which also accepts number type argument and is used to skip the number of documents.


>db.COLLECTION_NAME.find().limit(NUMBER).skip(NUMBER)


company> db.employee.find().skip(1)

or we can use both 

company> db.employee.find().skip(1).limit(2)


* The sort() Method

To sort documents in MongoDB, you need to use sort() method. The method accepts a document containing a list of fields along with their sorting order. To specify sorting order 1 and -1 are used. 1 is used for ascending order while -1 is used for descending order.

company> db.employee.find().sort({age:-1})

company> db.employee.find().sort({age:1})


* MongoDB - Indexing


Indexes support the efficient resolution of queries. Without indexes, MongoDB must scan every document of a collection to select those documents that match the query statement. This scan is highly inefficient and require MongoDB to process a large volume of data.

Indexes are special data structures, that store a small portion of the data set in an easy-to-traverse form. The index stores the value of a specific field or set of fields, ordered by the value of the field as specified in the index.


The createIndex() Method:

To create an index, you need to use createIndex() method of MongoDB.


>db.COLLECTION_NAME.createIndex({KEY:1})

company> db.employee.createIndex({name:1})
name_1


Here key is the name of the field on which you want to create index and 1 is for ascending order. To create index in descending order you need to use -1.


company> db.employee.getIndexes()
[
  { v: 2, key: { _id: 1 }, name: '_id_' },
  { v: 2, key: { name: 1 }, name: 'name_1' }
]



we can pass fields while creating index

company> db.employee.createIndex({name:1,age:-1})
name_1_age_-1


background ==>	Boolean ==>	Builds the index in the background so that building an index does not block other database activities. Specify true to build in the background. The default value is false.

unique ==>	Boolean ==>	Creates a unique index so that the collection will not accept insertion of documents where the index key or keys match an existing value in the index. Specify true to create a unique index. The default value is false.


name ==>	string ==>	The name of the index. If unspecified, MongoDB generates an index name by concatenating the names of the indexed fields and the sort order.


sparse ==>	Boolean ==>	If true, the index only references documents with the specified field. These indexes use less space but behave differently in some situations (particularly sorts). The default value is false.


expireAfterSeconds ==>	integer ==>	Specifies a value, in seconds, as a TTL to control how long MongoDB retains documents in this collection.


weights	==> document ==>	The weight is a number ranging from 1 to 99,999 and denotes the significance of the field relative to the other indexed fields in terms of the score.



default_language ==>	string  ==>	For a text index, the language that determines the list of stop words and the rules for the stemmer and tokenizer. The default value is English.



language_override ==>	string ==>	For a text index, specify the name of the field in the document that contains, the language to override the default language. The default value is language.





Drop index:

company> db.employee.getIndexes({name:"name_1"})
[
  { v: 2, key: { _id: 1 }, name: '_id_' },
  { v: 2, key: { name: 1 }, name: 'name_1' },
  { v: 2, key: { name: 1, age: -1 }, name: 'name_1_age_-1' }
]
company> db.employee.dropIndex({name:1})
{ nIndexesWas: 3, ok: 1 }
company> db.employee.getIndexes({name:"name_1"})
[
  { v: 2, key: { _id: 1 }, name: '_id_' },
  { v: 2, key: { name: 1, age: -1 }, name: 'name_1_age_-1' }
]


or we can use index name directly

company> db.employee.dropIndex("name_1_age_-1")
{ nIndexesWas: 2, ok: 1 }



* Create multiple indexes:

company> db.employee.createIndexes([{name:1},{age:-1}])
[ 'name_1', 'age_-1' ]
company> db.employee.getIndexes()
[
  { v: 2, key: { _id: 1 }, name: '_id_' },
  { v: 2, key: { name: 1 }, name: 'name_1' },
  { v: 2, key: { age: -1 }, name: 'age_-1' }
]


---

* Aggregation

Aggregations operations process data records and return computed results. Aggregation operations group values from multiple documents together, and can perform a variety of operations on the grouped data to return a single result. In SQL count(*) and with group by is an equivalent of MongoDB aggregation.


for implementing aggregation we use aggregate() methiod

>db.COLLECTION_NAME.aggregate(AGGREGATE_OPERATION)





Expression	Description	Example:

$sum ==>	Sums up the defined value from all documents in the collection.
==>	db.mycol.aggregate([{$group : {_id : "$by_user", num_tutorial : {$sum : "$likes"}}}])

$avg ==>	Calculates the average of all given values from all documents in the collection. ==>	db.mycol.aggregate([{$group : {_id : "$by_user", num_tutorial : {$avg : "$likes"}}}])

$min ==>	Gets the minimum of the corresponding values from all documents in the collection. ==>	db.mycol.aggregate([{$group : {_id : "$by_user", num_tutorial : {$min : "$likes"}}}])

$max ==>	Gets the maximum of the corresponding values from all documents in the collection. ==>	db.mycol.aggregate([{$group : {_id : "$by_user", num_tutorial : {$max : "$likes"}}}])

$push ==>	Inserts the value to an array in the resulting document. 
==>	db.mycol.aggregate([{$group : {_id : "$by_user", url : {$push: "$url"}}}])

$addToSet ==>	Inserts the value to an array in the resulting document but does not create duplicates.	
==> db.mycol.aggregate([{$group : {_id : "$by_user", url : {$addToSet : "$url"}}}])

$first ==>	Gets the first document from the source documents according to the grouping. Typically this makes only sense together with some previously applied “$sort”-stage.
==>	db.mycol.aggregate([{$group : {_id : "$by_user", first_url : {$first : "$url"}}}])

$last ==>	Gets the last document from the source documents according to the grouping. Typically this makes only sense together with some previously applied “$sort”-stage.

==>	db.mycol.aggregate([{$group : {_id : "$by_user", last_url : {$last : "$url"}}}])




Pipeline Concept
In UNIX command, shell pipeline means the possibility to execute an operation on some input and use the output as the input for the next command and so on. MongoDB also supports same concept in aggregation framework. There is a set of possible stages and each of those is taken as a set of documents as an input and produces a resulting set of documents (or the final resulting JSON document at the end of the pipeline). This can then in turn be used for the next stage and so on.


Following are the possible stages in aggregation framework −

$project − Used to select some specific fields from a collection.

$match − This is a filtering operation and thus this can reduce the amount of documents that are given as input to the next stage.

$group − This does the actual aggregation as discussed above.

$sort − Sorts the documents.

$skip − With this, it is possible to skip forward in the list of documents for a given amount of documents.

$limit − This limits the amount of documents to look at, by the given number starting from the current positions.

$unwind − This is used to unwind document that are using arrays. When using an array, the data is kind of pre-joined and this operation will be undone with this to have individual documents again. Thus with this stage we will increase the amount of documents for the next stage.



* MongoDB - Replication



Replication is the process of synchronizing data across multiple servers. Replication provides redundancy and increases data availability with multiple copies of data on different database servers. Replication protects a database from the loss of a single server. Replication also allows you to recover from hardware failure and service interruptions. With additional copies of the data, you can dedicate one to disaster recovery, reporting, or backup.


Why Replication?

- To keep your data safe
- High (24*7) availability of data
- Disaster recovery
- No downtime for maintenance (like backups, index - rebuilds, compaction)
- Read scaling (extra copies to read from)
- Replica set is transparent to the application



How Replication Works in MongoDB:

MongoDB achieves replication by the use of replica set. A replica set is a group of mongod instances that host the same data set. In a replica, one node is primary node that receives all write operations. All other instances, such as secondaries, apply operations from the primary so that they have the same data set. Replica set can have only one primary node.

- Replica set is a group of two or more nodes (generally minimum 3 nodes are required).

- In a replica set, one node is primary node and remaining nodes are secondary.

- All data replicates from primary to secondary node.

- At the time of automatic failover or maintenance, election establishes for primary and a new primary node is elected.

- After the recovery of failed node, it again join the replica set and works as a secondary node.



A typical diagram of MongoDB replication is shown in which client application always interact with the primary node and the primary node then replicates the data to the secondary nodes.

```js
Client application Driver 
    ||          ||
    \/          \/

        Primary
          ||
          \/
        /    \
       /      \
      \/      \/
    Secondary  Secondary
      (replication of primary)
```

Replica Set Features:

A cluster of N nodes
Any one node can be primary
All write operations go to primary
Automatic failover
Automatic recovery
Consensus election of primary



* MongoDB - Sharding

Sharding is the process of storing data records across multiple machines and it is MongoDB's approach to meeting the demands of data growth. As the size of the data increases, a single machine may not be sufficient to store the data nor provide an acceptable read and write throughput. Sharding solves the problem with horizontal scaling. With sharding, you add more machines to support data growth and the demands of read and write operations.


In replication, all writes go to master node

Latency sensitive queries still go to master

Single replica set has limitation of 12 nodes

Memory can't be large enough when active dataset is big

Local disk is not big enough

Vertical scaling is too expensive



There are three main components in sharding −

Shards − Shards are used to store data. They provide high availability and data consistency. In production environment, each shard is a separate replica set.

Config Servers − Config servers store the cluster's metadata. This data contains a mapping of the cluster's data set to the shards. The query router uses this metadata to target operations to specific shards. In production environment, sharded clusters have exactly 3 config servers.

Query Routers − Query routers are basically mongo instances, interface with client applications and direct operations to the appropriate shard. The query router processes and targets the operations to shards and then returns results to the clients. A sharded cluster can contain more than one query router to divide the client request load. A client sends requests to one query router. Generally, a sharded cluster have many query routers.



* MongoDB - Create Backup:


Dump MongoDB Data

To create backup of database in MongoDB, you should use mongodump command. This command will dump the entire data of your server into the dump directory. There are many options available by which you can limit the amount of data or create backup of your remote server.


Syntax
The basic syntax of mongodump command is as follows −

>mongodump


* MongoDB - Deployment


The best approach incorporates prototyping your set up, conducting load testing, monitoring key metrics, and using that information to scale your set up. The key part of the approach is to proactively monitor your entire system - this will help you understand how your production system will hold up before deploying, and determine where you will need to add capacity. Having insight into potential spikes in your memory usage, for example, could help put out a write-lock fire before it starts.

To monitor your deployment, MongoDB provides some of the following commands −


- mongostat:

This command checks the status of all running mongod instances and return counters of database operations. These counters include inserts, queries, updates, deletes, and cursors. Command also shows when you’re hitting page faults, and showcase your lock percentage. This means that you're running low on memory, hitting write capacity or have some performance issue.

To run the command, start your mongod instance. In another command prompt, go to bin directory of your mongodb installation and type mongostat.

D:\set up\mongodb\bin>mongostat



- mongotop:


This command tracks and reports the read and write activity of MongoDB instance on a collection basis. By default, mongotop returns information in each second, which you can change it accordingly. You should check that this read and write activity matches your application intention, and you’re not firing too many writes to the database at a time, reading too frequently from a disk, or are exceeding your working set size.

To run the command, start your mongod instance. In another command prompt, go to bin directory of your mongodb installation and type mongotop.

D:\set up\mongodb\bin>mongotop



D:\set up\mongodb\bin>mongotop 30
The above example will return values every 30 seconds.



Apart from the MongoDB tools, 10gen provides a free, hosted monitoring service, MongoDB Management Service (MMS), that provides a dashboard and gives you a view of the metrics from your entire cluster



[text](https://www.tutorialspoint.com/mongodb/mongodb_database_references.htm)


* What is a Covered Query?

- All the fields in the query are part of an index.
- All the fields returned in the query are in the same index.


Since all the fields present in the query are part of an index, MongoDB matches the query conditions and returns the result using the same index without actually looking inside the documents. 

Since indexes are present in RAM, fetching data from indexes is much faster as compared to fetching data by scanning documents.


Lastly, remember that an index cannot cover a query if −

Any of the indexed fields is an array
Any of the indexed fields is a subdocument


# MongoDB - Analyzing Queries

Using $explain
The $explain operator provides information on the query, indexes used in a query and other statistics. It is very useful when analyzing how well your indexes are optimized.

```js

db.users.find({gender:"M"},{user_name:1,_id:0}).explain()

```


We will now look at the fields in this result set −

The true value of indexOnly indicates that this query has used indexing.

The cursor field specifies the type of cursor used. BTreeCursor type indicates that an index was used and also gives the name of the index used. BasicCursor indicates that a full scan was made without using any indexes.

n indicates the number of documents matching returned.

nscannedObjects indicates the total number of documents scanned.

nscanned indicates the total number of documents or index entries scanned.




# Using $hint


The $hint operator forces the query optimizer to use the specified index to run a query. This is particularly useful when you want to test performance of a query with different indexes. For example, the following query specifies the index on fields gender and user_name to be used for this query −


```js
>db.users.find({gender:"M"},{user_name:1,_id:0}).hint({gender:1,user_name:1})
{ "user_name" : "tombenzamin" }

```

To analyze the above query using $explain −

```js
>db.users.find({gender:"M"},{user_name:1,_id:0}).hint({gender:1,user_name:1}).explain()

```


# MongoDB - Atomic Operations


Model Data for Atomic Operations

The recommended approach to maintain atomicity would be to keep all the related information, which is frequently updated together in a single document using embedded documents. This would make sure that all the updates for a single document are atomic.


```js

db.createCollection("products")
{ "ok" : 1 }
> db.productDetails.insert(
	{
		"_id":1,
		"product_name": "Samsung S3",
		"category": "mobiles",
		"product_total": 5,
		"product_available": 3,
		"product_bought_by": [
			{
				"customer": "john",
				"date": "7-Jan-2014"
			},
			{
				"customer": "mark",
				"date": "8-Jan-2014"
			}
		]
	}
)

```

 whenever a new customer buys the product, we will first check if the product is still available using product_available field. If available, we will reduce the value of product_available field as well as insert the new customer's embedded document in the product_bought_by field


 ```js
>db.products.findAndModify({ 
   query:{_id:2,product_available:{$gt:0}}, 
   update:{ 
      $inc:{product_available:-1}, 
      $push:{product_bought_by:{customer:"rob",date:"9-Jan-2014"}} 
   }    
})

 ```

Note: However, it is possible that between the executions of these two queries, some other user has purchased the product and it is no more available. Without knowing this, our second query will update the purchase information based on the result of our first query. This will make the database inconsistent because we have sold a product which is not available.



# MongoDB - Advanced Indexing

# MongoDB - Indexing Limitations


Extra Overhead :

Every index occupies some space as well as causes an overhead on each insert, update and delete. So if you rarely use your collection for read operations, it makes sense not to use indexes.


RAM Usage: 

Since indexes are stored in RAM, you should make sure that the total size of the index does not exceed the RAM limit. If the total size increases the RAM size, it will start deleting some indexes, causing performance loss.


Query Limitations
Indexing can't be used in queries which use −

- Regular expressions or negation operators like $nin, $not, etc.
- Arithmetic operators like $mod, etc.
- $where clause


Index Key Limits: 

Starting from version 2.6, MongoDB will not create an index if the value of existing index field exceeds the index key limit.


Index Key Limits: 

Starting from version 2.6, MongoDB will not create an index if the value of existing index field exceeds the index key limit.


Maximum Ranges: 
- A collection cannot have more than 64 indexes.
- The length of the index name cannot be longer than 125 characters.
- A compound index can have maximum 31 fields indexed.


# MongoDB - ObjectId

An ObjectId is a 12-byte BSON type having the following structure −

The first 4 bytes representing the seconds since the unix epoch
The next 3 bytes are the machine identifier
The next 2 bytes consists of process id
The last 3 bytes are a random counter value



MongoDB uses ObjectIds as the default value of _id field of each document, which is generated while the creation of any document. The complex combination of ObjectId makes all the _id fields unique.


* Creating New ObjectId


newObjectId = ObjectId()

```js
> const objId= ObjectId();

> console.log(objId)
ObjectId('65f14d83b7f572c2c76c85c5')


```



* Creating timestamp of a document

Since the _id ObjectId by default stores the 4-byte timestamp, in most cases you do not need to store the creation time of any document.

```js

console.log(objId.getTimestamp())
ISODate('2024-03-13T06:53:55.000Z')

```


Converting ObjectId to String


```js

console.log(objId.toString());

65f14d83b7f572c2c76c85c5

```


* MongoDB - Map Reduce


MongoDB uses mapReduce command for map-reduce operations. MapReduce is generally used for processing large data sets.

(Collection.mapReduce() is deprecated. Use an aggregation instead )


* MongoDB - Text Search

```js

db.posts.createIndex({post_text:"text"})

db.posts.find({$text:{$search:"tutorialspoint"}})

```



# MongoDB - Regular Expression

MongoDB also provides functionality of regular expression for string pattern matching using the $regex operator. MongoDB uses PCRE (Perl Compatible Regular Expression) as regular expression language.


```js

db.posts.find({ post_text:{$regex:"tutorialspoint"  }  })


or we can also written as 

db.posts.find({post_text:/tutorialspoint/})

```

# MongoDB - GridFS


GridFS is the MongoDB specification for storing and retrieving large files such as images, audio files, video files, etc. It is kind of a file system to store files but its data is stored within MongoDB collections. GridFS has the capability to store files even greater than its document size limit of 16MB.

GridFS divides a file into chunks and stores each chunk of data in a separate document, each of maximum size 255k.

GridFS by default uses two collections fs.files and fs.chunks to store the file's metadata and the chunks. Each chunk is identified by its unique _id ObjectId field. The fs.files serves as a parent document. The files_id field in the fs.chunks document links the chunk to its parent.


# MongoDB - Capped Collections


Capped collections are fixed-size circular collections that follow the insertion order to support high performance for create, read, and delete operations. By circular, it means that when the fixed size allocated to the collection is exhausted, it will start deleting the oldest document in the collection without providing any explicit commands.

Capped collections restrict updates to the documents if the update results in increased document size. Since capped collections store documents in the order of the disk storage, it ensures that the document size does not increase the size allocated on the disk. Capped collections are best for storing log information, cache data, or any other high volume data.



db.createCollection("cappedLog",{capped:true,size:10000})

db.cappedLog.isCapped()
true



db.createCollection("cappedUserLog",{capped:true,size:1000,max:10})
{ ok: 1 }


If you want to check whether a collection is capped or not, use the following isCapped command −

> db.stud.isCapped()
false

we can create stud as capped below

> db.runCommand({"convertToCapped":"stud",size:10000,max:20})
{ ok: 1 }
> db.stud.isCapped()
true



Querying Capped Collection:

By default, a find query on a capped collection will display results in insertion order. But if you want the documents to be retrieved in reverse order, use the sort command as shown in the following code −

db.stud.find().sort({$natural:-1})



# MongoDB - Auto-Increment Sequence



Using Counter Collection
Consider the following products document. We want the _id field to be an auto-incremented integer sequence starting from 1,2,3,4 upto n.


{
  "_id":1,
  "product_name": "Apple iPhone",
  "category": "mobiles"
}


For this, create a counters collection, which will keep track of the last sequence value for all the sequence fields.

>db.createCollection("counters")


db.counters.insert({
	"_id":"productid",
	"sequence_value": 0
})




The field sequence_value keeps track of the last value of the sequence.

Use the following code to insert this sequence document in the counters collection −

>db.counters.insert({_id:"productid",sequence_value:0})


Creating Javascript Function
Now, we will create a function getNextSequenceValue which will take the sequence name as its input, increment the sequence number by 1 and return the updated sequence number. In our case, the sequence name is productid.

>function getNextSequenceValue(sequenceName){
   var sequenceDocument = db.counters.findAndModify({
      query:{_id: sequenceName },
      update: {$inc:{sequence_value:1}},
      new:true
   });
   return sequenceDocument.sequence_value;
}



Using the Javascript Function
We will now use the function getNextSequenceValue while creating a new document and assigning the returned sequence value as document's _id field.

Insert two sample documents using the following code −

>db.products.insert({
   "_id":getNextSequenceValue("productid"),
   "product_name":"Apple iPhone",
   "category":"mobiles"
})
>db.products.insert({
   "_id":getNextSequenceValue("productid"),
   "product_name":"Samsung S3",
   "category":"mobiles"
})




<!-- Notebook notes -->

MySQL <------> Mongodb

Database = Database
Table = Collection
Rows = Document (JSON Format)

BSON: Binary JSON

It is binary structure encodes type and length information which allow it to be traversed much more quickly compared to json.

1) create DB

use demo_db

2) create collection with insert document

db.students.insertOne({})

or 

db.createCollection("products")


* Document nesting level 100

* Every document having max limit of 16 MB

db.students.find().forEach((x)=> {printjson(x.name)});

instead of prinjson we can use console.log()

* with using "$" symbol any text means reserved words in mongo db.

# Projection:

db.stud.find({},{name:1,_id:0})

it include only names and excludes age and _id


# Data types in mongo DB

1. Text 
2. Boolean 
3. Number (Integer (32 bit), Number long (64 bit), Number Decimal )
4. ObjectId
5. IsoDate
6. Timestamp
7. Array
8. Embeded Documents


* Drop DB:

db.dropDatabase()
 
* Drop collection

db.stud.drop()


* Write concern in mongodb:

db.books.insertOne({name:"A",price:20},{writeConcern: {w:0}})


* Atomicity in Mongodb:

import json into mongodb using mongoimport (db tool)


* Query: 

mongoimport "/home/am-lp-44/downloads/dummy.json" -d college -c stud --jsonArray --drop

here college is DB and stud is Collection


* Comparison operators in Mongodb:

$eq
$ne
$lt
$gt
$lte
$gte
$in
$nin


* Logical Operators

$and
$or
$nor
$not

* $exits and $type operators:

db.stud.find({hasMobile:{$exists:true,$type:8}})

or 

for $type : 8 we can use as $type: 'bool'



* Evaluation operators:

$expr
$jsonSchema
$mod
$regex
$text
$where


* $text:

db.stud.createIndex({bio:"text"})

db.stud.find({$text:{ $search:"dev" }})


* Querying arrays

db.stud.find().count()

or 

db.stud.find().size()

db.stud.find({experience: {$size:3}})


* Greater than 4 skills

db.stud.find({$and:[{skills: { $exists:true}},{$expr:{$gte: [{$size:"$skills"},4] }}]});


* Update array using $push and $each 


db.stud.updateOne({name:'Vikram'},{$push:{skills:{$each:['java','C#','Angular']}}},{upset:true})


students whose hobbies are walking and reading

db.stud.find({hobbies:{$all: [ "walking","reading" ] }})

instead of $all we can use $in


Product whose name is apple and with quantity greater than 15

db.products.find({products: { $elemMatch : { quantity : { $gt : 11 }, name : "apple" } } })


* Sorting : 


Asc : db.stud.find().sort({age:1})

Desc: db.stud.find().sort({age:-1})


if users having same age then we can add multiple sorting

db.stud.find().sort({age:1,name:1})


$inc
$min
$max
$mul
$unset
$rename
$upsert


1) db.emp.updateMany({},{$inc: {salary : 500 } })

for decrease -> {salary: -500 }



2) db.emp.updateOne({name:"Ramesh"},{$max:{age:50}})


for min -> {$min:{age:-50}}

3) {$mul : { age: 2 } }

4) { $unset : {age: 222} }

it removes age property

5) updateMany({$rename:{age:"emp_age"}})

it renames property key name


* if record exists update it but if record not found create new record

db.emp.updateOne({name:"Vijay"},{$set:{emp_age:90}},{upsert:true})


* Array update:

$push
$pull
$pop
$addToSet

* Employee having less than and equal to 1 yr of exp

db.emp.find({exp:{$elemMatch:{exp_yr:{$lte:1}}}})

* add {neglect : true} property with only first matched item having less than 1 yr exp

db.emp.updateMany({exp:{$elemMatch:{exp_yr:{$lte:1}}}}, {$set:{"exp.$.neglect" : true}});


* add neglect: 1 for all matched and unmatched

({},{$set: { "experience.$[].neglect":1 }})


* add neglect for all matched

({},{$set:{"exp.$[e].neglect":true}},{arrayFilters:[{"e.duration": {$lte:1} }]})


* $push:

db.emp.updateOne({name:"ram"},{$push:{exp:{company:"MSoft",exp_yr:2}}})


if we pushed same data multiple times it will pushed. Redundancy is happening

for avoid such issues use $addToSet instead of $push


* $pull - removes all matched data


db.emp.updateOne({name:"ram"},{$pull:{exp:{company:{"x-soft",exp_yr:2}}}})


* $pop: removes last entry

({$pop:{exp:1}})


* for removing 1st set as -1

{$pop:{exp:-1}}


* Indexing in MongoDB:


- Indexes are stored in a B-tree data structure

- It stores

1. Index keys
2. Pointers to the documents in the collection

- when a query is executed mongodb can use the index to quickly locate the documents that match the query by searching through the B-tree.


* The Trade off

1. storage space: index requires separate storage
2. Write performance: will be slow it is good for read intensive task


* There are several types of indexes available in mongodb

1. single field indexes
2. compound indexes
3. text indexes


* get detailed info about query


db.teachers.find().explain()


db.teachers.find().explain("executionStats")


# 1 Single field Index:


Create index:

db.emp.createIndex({age:1})

db.emp.getIndexes()


* Drop index:

db.emp.dropIndex("age_1")


when not to use indexing in mongodb

1. when the collection is small 
2. when the collection is frequently updated
3. when the queries are complex (multiple feilds)
4. when the collection is large (make less indices)

# 2 Compound Indexes:

db.emp.createIndex({age:1,"gender:-1})

firstly by age sorting/indexing done. if age same then genderwise sorting (in desceding order) will done.


* 3 Cases:

i. db.emp.find({age:{$gte:27},gender:"male"}).explain("executionStats");

ii. db.emp.find({age:{$gte : 27}}).explain("executionStats")

above both will scan on basis of index (Ixscan)

iii. db.emp.find({gender:"male"}).explain("executionStats")

above will scan on basis of collection (collscan)


* Indexing also help in sorting 

db.emp.createIndex({name:1},{unique:true})

* Partial filters:

db.emp.createIndex({age:1})

{partialFilterExpression : {age:{$gt : 22 }}}


* db.teachers.createIndex({name:1}, {partialFilterExpression :{gender : {$exists : true} }})

* db.teachers.createIndex({"expire":1},{expireAfterSeconds:3600})

this works on date fields and on single field index.


* What is a covered query?

A covered query is a query which 

- all the fields in the query are part of an index.
- all the fields returned in the query are in the same index.

* Find only name:

db.emp.find({name:"mark"},{_id:0,name:1}).explain("executionStats");


* Winning plan:

In case of multiple indexes mangodb checks the performance of index on a sample of documents once the queries is run and 
set it as winning plan.

Then for second query of similar type it doesn't race them again.

it store that winning plan in cache.

* Cache is reset after:

1. After 1000 writes
2. Index is reset
3. Mongo server is restarted
4. Other indexes are manipulated

db.emp.find({name:"Mike"}).explain("allPlansExecution")


* Multi-Key Index:

- A multi key index is an index that can be created on an array field

- Mongodb will create a separate index entry for each value in each array

- so it can quickly look up documents that match a specific value.


# 3 Text index:

- single text index per collection
- tokenization and stemming
- relevance score

db.emp.createIndex({name:"text", bio: "text"})

-> db.emp.find({$text:{ $text : {$search : "singer" } }});

we can check score of index as well{}

db.stud.find({$text : {$search : "youtube actor"}}, {myscore:{$meta: "textScore" }})


we can execute the value as well.

db.stud.find({$text:{$search: "youtube-actor"}}, {myScore:{$meta:"textScore"}});

we can set priorities as well to properties.

db.emp.createIndex({name:"text",bio:"text"},{weights:{name:1000,bio:1}})



* To find above with sorting

db.emp.find({$text : {$search : "actor sita" }}.{myScore:{$meta : "textScore"}}).sort({myScore: {$meta:"textScore"}})


suppose there is million's of data and we have hitted the index query then in background mongodb lock the collection and any query will not be execute so instead of this we can set {background:true} so in background we can execute queries which are not dependent on indexing and indexing related queries will be locked these all process will done in forground.


db.stud.createIndex({name:"text",bio:"text"},{background:true})


# Aggregation

It group the data from multiple documents into a single document based on the specified expression.

Aggregation Pipeline:

The aggregation process in mongodb consist of several stages each stage transforming the data in same way.

The output of one stage is fed as input to next stage and so on until the final stage produce the desired result.

Mongodb provides several built in aggregation pipeline stages to perform various operations on the data such as $group, $sum, $avg, $min, $max etc

db.teachers.aggregate({$match: {gender: "male"}})

* Group teachers by age:

db.teachers.aggregate([{$group:{_id:"$age"}}])


The $group operator groups documents by the age field creating a new document for each unique age value.

The _id field in the group stage specifies the field based on which the documents will be grouped.

db.teachers.aggregate([ { $group : { _id : "$age", name:{ $push :  "$name"  } } } ])

* To copy entire document in array

db.teachers.aggregate([ { $group : {_id : "$age", entireDoc:{ $push : { "$$ROOT" } } } } ])

The $$ROOT vlaue is a  reference to the current document being processed in the pipeline which represents the complete document.



* Q. Give a count per age of male teacher

db.teacher.aggregate([ { $match : {gender: "male"} }, {$group : {_id: "$age", number: { $sum: 1 }} } ])

the value of sum is 1 which means that for each document in the group the value of "number" will be increamented by 1

* Q. Give a count per age of male students and sort them by count in descending manner

db.teachers.aggregate([ {$match: {gender: "male"} }, {$group: {_id:  "$age" , countOfTeachers : {$sum:1 }}}, {$sort : {countOfTeachers:-1}} ])


* we can create pipeline as much as we want


* Find max numbers in age group:

...., {$sort: {countOfTeachers:-1}}, {$group: {_id:null, maxNumberAge: {$max: "$countOfTeachers"}} }



* $toDouble operator: 

db.teachers.aggregate([ {$group: {_id:"$age", sumOfAges: {$sum: { $toDouble: "$age" } } }} ])


* Q. find hobbies per age group

db.teachers.aggregate([ {$group: {_id: "$age", hobbies: {$push: "$hobbies"} } } ])


Date stored in separate doc


db.teachers.aggregate([ {$unwind: "$hobbies"} ])




db.teachers.aggregate([ {$unwind: "$hobbies"}, {$group : { _id: "$age", hobbies:"$push": "$hobbies"}} ])


* Find number of students per each hobbies

db.teachers.aggregate([ {$unwind: "$hobbies"}, {$group: {_id: "$hobbies", count: {$sum : 1}}} ])

* Find average age of all students

db.teachers.aggregate([ { $group: { _id: null, avgAge: { $avg: "$age" }} } ])

if you specify _id:null in the $group operator it means that all the documents in the collection will be grouped together into a single group


* Q. find the total number of hobbies for all the students in a collection


db.teachers.aggregate([ {$unwind: "$hobbies"},{$group: {_id:null, count: {$sum:1}}} ])



- One more way:

db.teachers.aggregate([ {$group: {_id:null,count: { $sum: {$size "$hobbies"}}}} ])


Note: above query will produce an error if field not present


db.teachers.aggregate([ {$group: {_id: null, count: { $sum:{$size: { $ifNull : ["$hobbies"],[]}} }}} ])



* Q. List of all hobbies


db.teachers.aggregate( [ { $unwind : "$hobbies" }, {$group: {_id: null, allHobbies: {$push:"$hobbies"}}} ] )


Note: Hobbies will repeatedly added instead of $push use $addToSet


* $filter operator:

input : <array exp>, as : <identifier>, condition:<exp>

- input: specifies the array expession to filter.
- as : specifies a variable name that can be used inside the condition expression to reference that current element of the input array
- condition: specifies the condition that must be met in order for an element to be included in the result set. The expression must return either true or false



* Q. Find average of scores for students whose age is greater than 20

smaple data:

{
  _id: ,
  name: "abcd",
  age: 21,
  scores: [20,30,40,50,60]
}


db.teachers.aggregate([{$group: {_id: null, avgScore: {$avg: {$filter: {input:"$score",as:"score",cond:{$gt:["$age",20]}}}}}}])


# Bucket

when you want to categarize into discrete groups based on specified boundaries.

Q. categories male teachers based on their ages into three buckets ages less than 30 ages between 30 and 40 and ages greater than 40

db.teachers.aggregate([ {$match: {gender: "male"}}, {$bucket:{groupBy:"$age", boundaries:[0,30,40], default: "Greater than 40 group", output: {count: {  $sum: 1}, names:{$push:"$name"}}}} ])



* $lookup operator:


the lookup is an aggregation pipeline stage that allows you to perform a left outer join between two collection


Show collections

cust 
ord


Query: 

db.cust.aggregate([ { $lookup: {from: 'ord', localField: "_id",foreignField: "cust_id", as: "orderDetails"} } ])


# $project

$project stage is used in the aggregation pipeline to reshape documents include or exclude fields and create computed fields

db.emp.aggregate([ { $project: { fname: 1, lname: 1, _id: 0 } } ])


db.emp.aggregate( [ { $project: {fname:1,lname:1,monthlySalary: "$salary", annualSalary: {$multipy: [12, "$salary"]}}} ] )



* Capped: 

db.createCollection("order_logs", {capped: true, max: 4, size: 100000})


db.order_logs.isCapped()
true


# Authenication and Authorization


Windows: 

c:\program files\ mongodb\server\<version> \ bin \ mongod.cfg

Linux: sudo nano /etc/mongod.conf


security: 

  authorization : enabled


Restart service linux:

sudo systemctl restart mongod

or

sudo service mongod restart


1. use admin

2. db.getUsers()

3. db.createUser({ user: "adminUser",pwd: "password", roles: ["userAdminAnyDatabase","dbAdminAnyDatabase"] })

4. db.auth("adminUser","password")

5. db.logout()

6. db.dropUser("userName")


* Roles:

Read 
ReadWrite
dbAdmin
userAdmin
dbOwner


readAnyDatabase
readWriteAnyDatabase
userAdminAnyDatabase
dbAdminAnyDatabase

clusterManager
clusterMonitor
hostManager
clusterAdmin

dbOwner
userAdmin
userAdminAnyDatabase
root

backup
restore


db.createUser({
  user: "demo-user-1",
  pwd: "1234",
  roles: [ { role: "read", db:"amazon" },{role: "readWrite", db:"customer"} ]
})

db.runCommand({connectionStatus: 1})

---

# Replication and Sharding

* Transaction:

- A transaction is a set of operations that are executed as a single atomic unit

- Transactions provide data consistency by ensuring that either all the operations within the transaction are commited to the database or none of them are

- Transactions are designed to provide ACID properties

ACID:

1. A (Atomicity):

It guarantees that a transaction is as a single individual unit of work. Either all the operations within the transaction are successfully completed and commited or none of them are. If any part of the transaction fails all changes made by the transaction are rolled back leaving the data in it's original state.

2. C (Consistency) :

It ensures that a transaction brings the database from one valid state to another. It enforces any integrity constaints defined on the data, such as referential integrity or uniqueness constraints. If a transaction violates any constraints the entire transaction is rolled back, preserving data integrity

3. I (Isolation) : 

Isolation ensures that each transaction operates independently of other concurrent transactions. It prevents inter reference between concurrent transactions preserving data integrity and preventing unintended size effects. Isolation levels define different levels of concurrency control, allowing developers to choose the appropriate level of isolation for their use case.


4. D (Durability) :


Durability guarantees that once a transaction is commited it's changes are permently stored and will survive any subsequent system failures. Commited transactions are made durable by writing their changes to disk or other persistent storage. This ensures that the data is not lost and can be recovered in the event of a crash of failuer.


When it comes to transaction, replication is crucial for maintaining the consistency and durability gurantees across multiple documents and collection involved in transaction.


* Code:

var session = db.getMongo().startSession();

session.startTransaction();


var cust = session.getDatabase('bank').cust;

cust.updateOne({_id:1},{$inc:{bal:-100}});

cust.updaeOne({_id:2},{$inc:{bal:100}})

session.commitTransaction();

// session.abortTransaction();

session.endSession();

---


# $year, $month, $dateToString:

db.cust.insertOne({_id:3, name: 'vikas', dob: ISODate("2000-01-22")})


date: ISODate("2004-06-08T 14:32:45Z") // UTC

Time Zone offset:

date: ISODate("2004-06-08T 14:32:45Z +2:00")


db.stud.find({dob:{$gte:ISODate("2000-01-01")}})


date with aggregation:

db.cust.aggregate([  { $group:{_id:{$year:"$dob"}, names:{$push:"$name"}} } ])


db.cust.aggregate([{$match:{name:"sham"}}, {$project: {dayOfMonth: {$dayOfMonth: "$dob"},month:{$month:"$dob"}, month: {$month:"$dob"}, dayOfYear :{$dayOfYear: "$dob"}, hour: { $hour : "$dob" }, ms: {$millisecond: "$dob"} }}])


* $dateToString:

db.cust.aggregate([ { $project: { name:1,_id:0,dob:{$dateOfString: {format:"%d - %m - %Y %H:%M:%S", date:"$dob"}} } } ])



















