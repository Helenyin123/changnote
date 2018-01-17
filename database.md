# Database

#### What's the difference of MySQL and MongoDB?

* **Schema & Flexibility: **MySQL organizes data into tables and links then based on relationship. One row contains all the information about one entity. One column is all entity’s information of an attribute. Its schema is called ER model \(Entity - Relation\). It’s fixed, better for data normalization.NoSQL’s schema organizes data into document or key-value pairs or graph. It is more flexible and dynamic. We can define it by ourselves like an object or class. Each row doesn’t need to contain information for each column.
* **Scalability: **MySQL’s scaling is vertical. NoSQL’s scaling is horizontal which make it more cost effective. **Vertical Scalability**: scale by add more power \(CPU, RAM\) to an existing computer. **Horizontal Scalability:** scale by adding more machines into your pool of resource. \(better for balance between performance and cost\).

* **Consistency & Availability \(CRUD-create, read, update, delete\): **MySQL is more consistency, so it is widely used by bank system. NoSQL sacrifice consistency to make it more available, which is suitable for website service. MySQL follows ACID properties \(Atomicity, Consistency, Isolation, Durability\). NoSQL follows CAP theorem \(Consistency, Availability, Partition Tolerance\).

#### [What's the difference between MongoDB, Cassandra and HBase?](https://www.linkedin.com/pulse/real-comparison-nosql-databases-hbase-cassandra-mongodb-sahu/)

Data are not always structured and fit into tidy rows and columns. Unstructured data is growing at twice the rate of structured data. That's why we need NoSQL database. They are all column-based key-value pair store.

There are at least two kinds of database simplicity: development simplicity and operational simplicity.

**MongoDB **is most suitable for applications that support short run or single processes – it’s not really fit for long run processes found in the likes of an ERP environment

**Cassandra**: Safely run/easy to manage/powerful at scale. It takes care of scaling and replication very well. CQL\(Cassandra Query Language\) is a SQL-like language which makes it easy to learn. It provides AP\(Availability,Partition-Tolerance\) from CAP theorem.

**HBase **provides a record-based storage layer that enables fast, random reads and writes to data, complementing Hadoop by emphasizing high throughput at the expense of low-latency I/O. HBase was designed to provide optimal performance when consistency is critical. HBase is perfect for real-time querying of Big Data. Facebook messenger use it for messaging and real-time analytics. It provides CP form CAP theorem \(Consistency, Availability, Partition\).

| Name | MongoDB | Cassandra | HBase |
| :---: | :---: | :---: | :---: |
| Database Model | Document Store | wide column store based  on BigTable and DynamoDB | wide column store based  on Apache Hadoop and BigTable |
| Replication Method | Master-Slave replication | Selectable Replication Factor | Selectable Replication Factor |
| Consistency | Eventual/Immediate Consistency | Eventually/ Immediate Consistency | Immediate Consistency |
| Partition Method | Sharding | Sharding | Sharding |
| Durability \(make data persistent\) | yes | yes | yes |
| Access Method | JSON | CQL/Thrift | Java API/Restful API/Thrift |
| Data Schema | schema-free | schema-free | schema-free |
| Secondary Index | Support | Not Support | Support |

**HBase**

Pros: Strong consistence, Build on top of Hadoop HDFS. Provide CP \(Consistency and Partition\) on CAP

Cons:  Not good for classical transactional application or relational analytics.

Usage: Facebook Messenger

**Cassandra**

Pros: High availability, Incremental scalability, Eventually Consistent, Provide AP\(Availability, Partition\) on CAP

Cons:

Usage: Twitter

**MongoDB**

Master-Slave model, CP\(Consistency, Partition\) on CAP













