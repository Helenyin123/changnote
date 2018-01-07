# Database

#### What's the difference of MySQL and MongoDB?

* **Schema & Flexibility: **MySQL organizes data into tables and links then based on relationship. One row contains all the information about one entity. One column is all entity’s information of an attribute. Its schema is called ER model \(Entity - Relation\). It’s fixed, better for data normalization.NoSQL’s schema organizes data into document or key-value pairs or graph. It is more flexible and dynamic. We can define it by ourselves like an object or class. Each row doesn’t need to contain information for each column.
* **Scalability: **MySQL’s scaling is vertical. NoSQL’s scaling is horizontal which make it more cost effective. **Vertical Scalability**: scale by add more power \(CPU, RAM\) to an existing computer. **Horizontal Scalability:** scale by adding more machines into your pool of resource. \(better for balance between performance and cost\).

* **Consistency & Availability \(CRUD-create, read, update, delete\): **MySQL is more consistency, so it is widely used by bank system. NoSQL sacrifice consistency to make it more available, which is suitable for website service. MySQL follows ACID properties \(Atomicity, Consistency, Isolation, Durability\). NoSQL follows CAP theorem \(Consistency, Availability, Partition Tolerance\).



