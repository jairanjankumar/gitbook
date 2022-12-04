# NoSQL

**NoSQL** (Not Only SQL)

NoSQL databases are optimized for scalable performance and schema-less data models. These types of databases are optimized for applications that require large data volume, low latency, and flexible data models, which are achieved by relaxing some of the data consistency restrictions of traditional relational databases.

They use a variety of data models, including columnar, document, graph, and in-memory key-value stores.

**1) Columnar databases** are optimized for reading and writing columns of data as opposed to rows of data. Used for analytic query performance because it drastically reduces the overall disk I/O requirements and reduces the amount of data you need to load from disk.

database example :Apache Cassandra, Apache HBase

Nice explanation : [https://www.youtube.com/watch?v=mRvkikVuojU](https://www.youtube.com/watch?v=mRvkikVuojU)

**2) Document databases** are designed to store semistructured data as documents. Unlike traditional relational databases, the schema for each NoSQL document can vary, giving you more flexibility in organizing and storing application data and reducing storage required for optional values.

**3) Graph databases** store vertices and directed links called edges. Graph databases can be built on both SQL and NoSQL databases. Vertices and edges can each have properties associated with them.

**4) In-memory key-value** stores are NoSQL databases optimized for read-heavy application workloads or compute-intensive workloads (such as a recommendation engine). In-memory caching improves application performance by storing critical pieces of data in memory for low-latency access.

* Semistructured also known as self-describing structure, Semistructured examples : JSON or XML format.


|      | RethinkDB | MongoDB       | CouchDB                            | Ref     |
| ---- | --------- | ------------- | ---------------------------------- | ------- |
| Join | Supported | Not Supported | Only supported in predeclared view | Page 34 |
|      |           |               |                                    |         |
