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


















































































































