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



---

company> db.stud.update( {hobbies:"cricket"},{$set : {age:100 }},{multi:true}  )
{
  acknowledged: true,
  insertedId: null,
  matchedCount: 2,
  modifiedCount: 2,
  upsertedCount: 0
}




































































