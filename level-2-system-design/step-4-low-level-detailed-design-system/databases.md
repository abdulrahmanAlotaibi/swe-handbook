# Databases

## Relational

### Sharding

* App-level joins
* Distributed transactions
* App-level partitioning of data

**Example :**&#x20;

{% embed url="https://medium.com/pinterest-engineering/sharding-pinterest-how-we-scaled-our-mysql-fleet-3f341e96ca6f" %}

#### Challenges  of app-level partitioning

* Partitioning function among DB instances
* How to rebalance if instance become hot/big (a lot of writes and reads)
* Since you split data across instances, you need to sub-divide your queries to sub queries
* Also if you want to do ACID transactions across partitions there is a need for distributed protocols such as 2PC

{% embed url="https://cseweb.ucsd.edu/classes/sp16/cse291-e/applications/ln/lecture8.html" %}

### Replication

* Chain-based replication
* The Raft Consensus Algorithm

![Chain-based replication from Understanding distributed systems book ](<../../.gitbook/assets/image (14).png>)

{% embed url="https://raft.github.io/" %}

### Optimization

* Caching slow to compute data or frequently accessed&#x20;
* Queries
  * n+1
  * Archive old records
  * Return only needed columns → because I/O , CPU, and memory load
  * Use enums for categorical data
  * Add indexes (usually it’s b-tree data structure)
  * Use explain to inspect
  * Use slow query log for debugging
* DB optimization
  * Horizontal scaling
    * Replication
    * App-level partitioning/sharding
  * Vertical Scaling: Increasing hardware resources (CPU cores and core speed, RAM, disk space)

### Data modeling

* The Entity-Relationship Model
* Identifying Data Objects
* Developing basic schema (attributes, primary key, relationships ,foreign keys, integrity rules)

{% embed url="https://www.liberty.edu/media/1414/[6330]ERDDataModeling.pdf" %}

### Migrations

* App-level migrations (migrations scripts or tools such as knexjs)
  * Altering tables and columns and rolling back in migration history
* From DBMS to DBMS
* Transfer all data form source to target and shutdown source
* Transfer all data from source to target and then leave source running → DB replication
* Transfer data → complete or partial
* Humongous/Heterogenous → source and target DBMS are the same or not
* There is _migrations systems_ which moves data from source to target
* From machine to another machine

### SQL Vs NoSQL

### NoSQL

* Better support for locality (embedding) which results in less network requests
* Closer to application data structures usage: For example, an account page contains account info and profile info embedded inside the same account document
* If the data in your application has a document-like structure (i.e., a tree of one-to-many relationships, where typically the entire tree is loaded at once)
* Flexible schema
  * Easy to change
  * No pre design overhead, you design on the go
* You model based on your application queries not based on how your entities is designed

### SQL

* The relational model counters by providing better support for joins, and better many-to-one and many-to-many relationships.
  * Joins can be emulated in application code by making multiple requests to the database, but that also moves complexity into the application and is usually slower than a join performed by specialized code inside the database.

## Use cases

### NoSQL

* Big data
* When you need horizontal scaling for high throughput in writes and reads
* Flexible schema

### SQL

* Need ACID
* JOINs for many-to-many or one-to-many
* Analytics using aggregations
* You need to know your queries in advance

### App-level

* Migrations scripts
* ORMs
* Query builders

{% embed url="https://levelup.gitconnected.com/raw-sql-vs-query-builder-vs-orm-eee72dbdd275" %}

* [ ] TODO: There is a reference for optimizing SQL queries&#x20;

