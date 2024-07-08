# What is system designing?

System design is the process of designing
the element of a system such as architecture,
modules and components the 
different interface of those 
components and the data that
goes through that system.


Type of system design:

1. LLD : Low level design
2. HLD : High level design


HLD:

Describes the main components
that would be developed for the 
resulting product.

The system architecture details,
database design, services and
processes, the relationship 
between various modules and
features.

LLD:

Describes the design of each
element mentioned in the High-level
design of the system

Classes, interfaces, relationshis
between different Classes and actual
logic of various components



# Monolithic architecture:


Architecture --> Internal design details for building the application


Web application having main components

Back end
Front end   
Database     

within and deployed together

codebase under same repo


If all the components and functionalities of a project are entangled and combined in a single codebase, then that
is monolithic application.

monolithic architecture has less complexity, easier to understand, higher productivity


monolithic system is also know as centralised system


When it is good

1. When we are just starting

2. In monolithic architecture all the modules are present in the single system, so they require fewer network calls as compared to other architectures.

3. It is comparatively easier to secure monolithic system 

4. Integration testing is easier

5. Less confusion


Disadvantages:

1. In monolithic architecture every module is combined in a single system, so if there is an error or bug in a single module it can destroy the complete system

2. In monolithic architecture whenever a single module is updated the whole system need to be updated to reflect the changes to users. All modules are present in a single system and are connected to one another, so the whole system need to be updated.

3. In monolithic architecture if there is any change in a single module's programming langulage or framework, it will affect the entire system. The entire system needs to be changed because every module is interlinked and tightly coupled. 



What is Distributed system:


A distributed system is collection of multiple individual systems connected through a network that share resources, communicate and coordinate to achieve common goals. 


Advantages:

1. Scalable
2. No single point of failuer
3. Low latency


Disadvantes:

1. Complex
2. Management required
3. Difficult to secure
4. message may be lost in between nodes(severs)


Latency = network delay + computational delay


Monolithic < Distributed



Reduce latency:

1. caching:

    Caching is the process of storing information for a set period of time on a computer.

2. CDN:

    CDN are geographically distributed networks of proxy servers and their objective is to serve content to users more quickly.


3. Upgrade Hardwares



# What is Throughput:

The volume of work or information flowing through a system. 


Throughput is the amount of data transmitted per unit of time. It is the process flow rate. Throughput is measured in bits per second. i.e bps



monolithic < Distributed


Causes of low throughput:

1. Latency
2. Protocol overhead
3. Congestion


Improving throughput

1. CDN
2. Caching
3. Use distributed system
4. Load balancer
5. Upgrade resources



Availability:


Monolithic < Distributed



Fault tolence ∝ Availability


How to increase availability:

1. replication
2. DS
3. Redundancy


Replication means:

Includes redundancy but involves the copying of data from one node to another or the synchronization of state between nodes.

Redundancy:

Redundancy is the duplication of nodes, in case of some of them are failing



* Consistency:


When more than one client requests the system for all such requests it will be called consistent when each client gets the same data. The data should always be consistent regardless of who is accessing it. 



When more than one client requests the system, for all such requests when different clients get different responses due to some recent update that has not been committed to all systems yet this reading operation will be called dirty read. 




Factor improving consistency:

1. Improving network bandwidth
2. stop the read while synchronization
3. replication based on distance anware strategies.


* Types of consistency:

1. Strong consistency:

When the system doen't allow read operation until all the nodes with replicated data are updated.

e.g ticket booking

2. Eventual Consistency:

user read requests are not halted till all the replicas are updated rather the update process is eventual. Some users might receive old data but eventually all the data is updated to the latest data

e.g social media


3. Weak Consisitency:

no need to update other servers (nodes), it's depends on business requirement.



CAP Theorem:

C - Consistency
A - Availability
P - Partition Tolerance


For a distributed system the CAP theorem states that it is possible to attain only two properties and the third would be always compromised. 


The system requirements should define which two properties should be chosen over the rest.



* The system designer can select consistency and partition tolerance but the availability would be compromised then.

* The system designer can select partition tolerance and availability but consistency would be compromised then.

* The system designer can select availability and consistency but the partition tolerance would be compromised then.


we can use only-> CA or CP or AP 

not all at time ->  CAP not use.




In CAP Theorem P is most important we have to compromize either C or A, but can't P.


a. Blogs website - A
b. multiplayer online games - A
c. Stock trading platforms- C
d. video streaming sites - A
e. video chat applications - A
f. ticket booking system - C
g. Bank - C



# What is Lamport logical clock


Find event sequence.


event -> count + 1
rec -> max(event1, event2) + 1



# Scalability:

1. Vertical 

Pros:

1. Easy to implementation
2. Less power
3. management is easy

Cons:

1. Single point of failuer (SPOF)
2. Limited
3. Price



2. Horizontal

Pros:

1. Overcome Single point of failuer (SPOF)

2. Less price

Cons:

1. Management complex
2. security
3. power consumption




# Difference between Redundancy and Replication:


* Redundancy:

It is simply the duplication of nodes or components so that when a node or component fails, the duplicate node is availbale to service customers.


Type of redundancy:

1. Active redundancy:

Active reduncdancy is considered when each unit is operating/active and reponding to the action multiple nodes are connected to load balancer, and each unit receives and equal load.


2. Passive redundancy:

It is considered when one node is active or operational and the other is not operating. During the breakdown of the active node the passive node maintains availability by becoming the active node. 



# Replication 

Redundancy + Synchronization

Type of Replication:

1. Active Replication:

All nodes is in active state and perform read and write operation synchronously. 

2. Passive Replication:

Every read and write done by master node.


If master goes down one slave becomes master

Master-slave replication can be either synchronous or asynchronous. The difference is simply the timing of propagation of changes. If the changes are made to the master and slave at the same time it is synchronous. If changes are queued up and written later it is asynchronous. 




# Load Balancers


Load balancing is the process of efficient distribution of network traffic across all nodes in a distributed system.


 Roles of load balancer:

 1. The load distribution equal over every node.

 2. Health check (if the node is not operational, the request is passed to another)
 3. Load balancers ensure high scalability, high throughput and high availability.



* When to use it and when not to?

In monolithic or in case of vertically scaled system we dont need it. But in microservice architecture we need it.


Challenes of load balancing:


Single point of failure - During a load balancer malfunctioning the communication between clients and servers would be broken. To solve this issue, we can use redundancy. The system can have an active load balancer and one passive load balancer.



Advantages of using load balancer:

1. Optimisation: load balancers help in resource utilisation and lower response time thereby optimising the system in high traffic environment.

2. Better user experience: Load balancer help in reducing the latency and increasing availability making the user's request go smoothly and error free

3. Prevent Downtime: load balancer maintain a record of servers that are non-perational and distribute the traffic accordingly therefore ensuring security and preventing downtime which also helps increase profits and productivity.

4. Flexibility: Load balancer have the flexibility to re-route the traffic in case of any breakdown and work on server maintenance to ensure efficiency. This helps in avoiding traffic bottlenecks.

5. Scalability: When the traffic of a web application increases suddenly load balancers can use physical or virtual servers to deliver the responses without any disruption. 

6. Redundancy: load balancing also provides in-build redundancy by re-routing the traffic in case of any failuer.





# Load Balancing Algorithms:

1. Round Robin (Static):

Rotational fashion

2. Weighted Round Robin (Static):

It is similar to round robin when the servers are different capacities. (some node can have better resources, others might not have)

3. IP Hash Algorithm (Static):

The servers have almost equal capacity and the hash function(input is source IP) i used for random or unbiased distribution of requests to the nodes.


4. Source IP Hash (Static): 

Source IP hash combines the server and client's source and destination IP addresses to produce a hash key. The key can be used to determine the request distribution.


5. Least connection algorithm (Dynamic): client requests are distributed to the application server with the least number of active connections at the time the client request is received.

6. Least response time (Dynamic): 

The request is distributed based on ther server which has the least response time.




# What is caching ?


Types Of caching:

1. In memory / local cache

e.g Mem-cach

2. Distributed / central cache

e.g redis



When to use?

1. Read intensive
2. static content


1. Application server cache
2. CDN (Content Delievery Network)




Cache Eviction Strategies:


It's meaning deleting cache

1. LRU (Least recently used)
2. MRU (Most recently used)
3. LFU (Least frequently used)
4. FIFO (First in first out)
5. LIFO (Last in First out)
6. RR (Random replacement)



# File-Based Storage System File Based Database Management System (DBMS):


A file-based storage system is a database management system where data is stored in the form of files.



# Challenges of File-Based Storage System


1. Data redundancy 

update anamoly, delete anamoly leading to data inconsistency. 





# Can RDBMS scale horizontaly?


What is RDBMS ?

It performs data operations on relational database.

Store, manage, query and retrieve data

Data is represented in the form of tables.

The relationship between the two tables is represented by foreign keys.



Advantages:

1. No data redundancy and inconsistency.

2. A locking system is provided by RDBMS to prevent abnormalities from occurring.

3. Built-in searching capabilites (no need of a separate programme as in FS)

4. Ex-To maintain data integrity numberic columns won't have aplhabetic data

(There is no process in the file system to check these constraints automatically)


Dis advantages:

1. Rigid schema
2. High cost
3. Scalability issues (Horizontal scaling/sharding is very dificult);


# NoSQL

It stands for "non-SQL" database or we can say that it is a non-relational database.



NoSQl is the umbrella term comprising of four different tpyes of databases.

Key value db: key value db (generally used for caching)

e.g Redis

Document db: Brings best of both RDBMS and NoSQL. It combines the relationship concept from RDBMS and dynamic schema and horizontal scaling from NoSQL databases.

E.g. mongodb

Columnar db: The columns are stored together instead of rows. Because of that the aggregation in such databases is rapid. It is widely used for Data analysis.

when we query on subset of your data's columns.

Because it just needs to read these specific columns, columnar DB conducts such queries quickly (while row-based DB would have to read the entire data).

e.g Cassandra


Graph db: Graph database represents and stores entites and relationships in the form of graph data structure. It is majorly used for social networks. 

When your data is in the form of a graph like social networks we use this.

e.g Neo4j



# What is Polyglot Persistence?


E-comm website

shopping cart & session data -> key-value store

completed order -> document store

inventory and item price -> RDMS (LegacyDB)

Customer social graph -> Graph store




# Normalization and Denomralization

Normalization : Putting data in multiple tables to avoid redundancy.


Denomralization : Putting data in single table.

It combines the data and organizes it in a single table. Denormalization is the process of adding redundant data to the normalized relational database to optimize it's perfomance.


Benifits of Denormalization:

1. faster data read operations
2. management convenience
3. high data availability
4. reduces the number of network calls to fetch data from multiple places.

Challenges of Denormalization

1. Redundant data -> wastage of  memory
2. It increases the complexity
3. Data incosistency
4. it will cause slow write operations since we will need to write multiple places due to redundancy.

 

# Indexing in DB:


 Indexing creates a lookup table with column and the pointer to the memory location of the  row, containing this column.


Before indexing apply time complexity is O(n)

After indexing applying time complexity is O(log n)


In indexing it's creates separate memory location and store column and row reference with sorted manner with respect to original table


B-trees data structure used for indexing


B-tree data structure is used to store the indexing as it is a multilevel format of tree-based indexing, which has balanced binary search trees.



Read intensive work apply indexing. 

not recommended for insert, update and delete. (taking too much time)


# Synchronous communication ( Blocking call )


1. To achieve consistency
2. Transaction


High consistency (Industrial use cases):

1. Stock market
2. Bank payments
3. Ticket booking
4. Real time decision making


# Asynchronous commnication(Non blocking calls)


where is it necessary?

1. Computation takes a lot of time
2. scalability of application
3. Avoid cascading failure



# Message based Communication


1. Client sends request in the form of message
2. receives response in form of message
3. it is async so client is not required to halt the process and wait for the process.



Producer -> who sends request
Consumer -> who receive req
Agent -> channel where req communication (queue)

* P2P  (peer to peer) Model:

e-mail service

* Publish subscribe model:

news-later


Message based communication tools:

Kafka 
RabbitMQ



# Web server

Tools or programs that helps keep the web application always up and running.


Apache
NgInx



# Communication Protocols


The rules, syntax, semantics and timing of commnunication and possible error recovery methods.


These protocols can be implemented using hardware, software or a combination of both.


Models:

1. Push: 

the clients opnes the connection with the server and keeps it always active.

The server pushesh new events to the client. This method reduces the server load. 
 

2. Pull/Polling:

client requests and server respond

issue: what if client sends 100 requests but get response to just 5 request

3. Long polling: 

Client requests and server keep in open until it gives response



4. Socket:

when we need continuous frequent connections

two way connection channel


5. Server sent events:


client subscrbes to the server "stream" and server will send a message ("stream of events") to the client until the server or client closes the stream. 

One way connection

Long lived connection



# Rest API 

1. Client: Syste that initiates the commnication over the network.

e.g mobile apps, browsers, web based consoles, laptops

A web server can also act as a cient when requesting information to other server.


2. Server: System that receives the request over the network.



What is required for commnication to happen?

1. Language independent
2. Fast 
3. Enable commnication over the network
4. Light weighted



REST: REpresentational State Transfer

A technique/ style/ standard to provide those requirement.


REST API -> URI and HTTP verb

Get
Post
Put/patch
Delete



# Service Oriented Architecture (SOA):


Service-Oriented Architecture (SOA) is a style of architecture that promotes loose coupling and granular application to make the components of the software reusable.



* Advantages of Service-Oriented Architecture


1. Selective scaling
2. Different tech stacks
3. Loose coupling
4. Agile


* Disadvantages of service-oriented architecture

1. Higher latency
2. Complex to secure
3. Cascading failuer
4. Complex understanding



Microservices architecture is an evolved version of SOA that promotes software components to be loosely coupled. 

It is the most granulated tpye of architecture design and every service is completely independent of the other.


 
SOA VS Microservices:


1. Services can share data storage

        vs

1. Each microservice has separate and independent data storage


2. Less scalable architecture

        vs

2. Highly scalable architecture


3. Deployment is time-consuming

        vs

3. Deployment is easy and less time-consuming


4. Focused on maximize application service reusability

        VS 

4. More focused on decoupling



# Tier architecture

A web application can be designed according to the n-tier architecture where tiers are different layers of architecture.


A Tier is a logical separation between different components of the application.

 Tier architecture helps make modifications and updation of different components easy. It helps in assigning dedicated tasks and roles to each component



1. 1 Tier

FE + BE + DB ==> at same place

2. 2 Tier

FE & BE + DB ==> at different place

3. 3 Tier

FE & BE & DB ==> at differet places


# Authorization vs Authentication 


Authentication - who are you?

Authorization : What can you do ?


# JWT authentication
# OAuth authentication


# Forward proxy and reverse proxy:

A proxy server is a hardware or a piece of software that is placed between a client and an application.


The proxy server provides a gateway between the user and the internet.


1. Forward Proxy:

It hides the client.


2. Reverse Proxy:

It hides the server


When to use reverse proxy?

1. When I don't want to expose the server

2. To make user feel there is only one server

3. Provide load balancing for the server

4. Allows administrators to swap the backend servers without distrubing the traffic

5. Filter out some requests.



# URL Shortner:


1. Feature (length of url, domain)


Funcational Requirements:

i. Shorten
ii. Redirection
iii. Expiry

Non-functional Requirements:

i. Highly available
ii. Low latency
iii. URL's should not be predicatable


2. Estimates (memory, CPU requirements)

i. Esitmating the system capacity (RAM, Storage)

ii. Decide Ready heavy or Write heavy

100 : 1

Read calls : Write calls


Every month -> 1 million new URLs

Every month -> 100 million redirections

QPS (Queries per seconds):

100,000,000 / 30 * 24 * 3600 = 50 qps


Expiry will be 10 years

Total Url's in 10 yrs = 1,000,000 * 12 * 10


Assume 1 url size is 500 byte

Total size = 1,000,000 * 12 * 10 * 500 = 60 GB


Cashing:

RAM -> 1 day TTL (Time to Leave)


Per day queries:

50 qps

50 * 12 * 3600 = 5 million qpd


25% of 5 million queries will be go for caching:


25% of 5 million = 1.25 million

1.25 million * 500 bytes = 1GB



3. Design goal (CAP)

i. Read intensive 
ii. Highly available
iii. Low latency
iv. Security (not everybody can shorten url)


4. HLD

i. API's :

shorten-url
delete-url
redirection

signup
login
logout


ii. Database - Mongodb
iii. Algorithm - 

long - short
avoid collisions

md5-#


iv. Design


5. Scaling


# Dropbox system design 

Functional Requirements:

i. Upload
ii. Download
iii. Share


Non-functional Requirements:

i. Scalable 
ii. Highly Available
iii. Low latency
iv. Optimize data transfer by minimizing bandwidth 
v. ACID


System Capacity:

1 Billion users

Average user stores 20GB
Total space 20 Billion GB


HLD:

client -> 
storage layer ->
metadata storage layer -> synchronizer 



* Clinet use case:

i. upload the file

ii. Download the file

iii. Detect any changes

iv. break the file into smaller changes thereby optimizing the file transfer (now only file changes has to be transferred instead of whole file)

client -->

chunker --> calculate hash of each chunk and upload to x

watcher --> notifies chunker and indexer about changes

internalDB --> stores hashes, URL & metadata

Indexer --> takes hash & URL of chunks from chunker and save to internalDB


Storage layer

i. Highly distributed (HDFS,GFS)

ii. Add caching


Metadata storage layer:

i. Permissions 

ii. Devices list

iii. Info of chunks (chunk_id,chunk_order,etc)

iv. workspace folders

v. versions

vi. Hashesh
















