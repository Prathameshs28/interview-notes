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























