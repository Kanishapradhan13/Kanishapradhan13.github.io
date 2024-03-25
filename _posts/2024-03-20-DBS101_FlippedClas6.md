---
Title: DBS101 Flipped class 6
categories: (DBS101,Flipped_class 6)
tags: (DBS101,Nonrelational Databases)
---

## Topic: Nonrelational Databases/ NoSQL Databases
----

In our sixth flipped class, we learned about Nonrelational Databases along with their advantages, disadvantages, and applications.NoSQL is used to store the data in the nontabular form. NoSQL stands for Not only SQL.

We were divided into 6 different groups for expert groups and home groups. After discussing the different types of NoSQl databases in our expert group, we shared each of our topics in the home group consisting of members from different expert groups with 6 different topics.

1. ### Document-based Databases

document-based database is a type of database that stores and manages data in a format same as we store documents.

It is typically stored in a JSON or BSON file format.

document-based databases provides flexibility, scalability, and performance advantages, best for applications where data structures may change over time or where easy and efficient data access is important. However, they cannot handle applications requiring complex queries or transactions that are reliably processed and maintain data integrity.

2. ### Key-Value based databases

It is the simpliest form of storing data in a NoSQL database. Each element in the database is stored in key-value pairs and can be retrieved by using a unique key given to each element in the database.

key-value based databases provides simplicity, high performance, and scalability, making them suitable for applications where fast data retrieval by unique identifiers (keys) is required. However, they may not be suitable for applications requiring complex queries or extensive data analysis.

3. ### Graph Databases

These are databases that uses graph structures for storing data. Here, data is stored in the nodes of the graph and the edges represent the relation between them.

It is advantageous in solving many-to-many relationhship problems and it is easy to query relationhship for complex data. However it is not the best solution for an application if it needs to scale horizontally as it will show poor performance. It can however be applicable in banking databases to store the users with the relation of their accounts.

4. ### Vector Databases

A vector database is designed to handle data that's organized as vectors – these are just arrays of numbers that represent different aspects of the data.They're really good at finding similarities between different pieces of data, like words or images, can handle huge amounts of data efficiently, and they work well for real-time analysis. It is used in machine learning and AI to handle lots of data with many dimensions.

5. ### Time-series Databases

Time-series data is data with a timestamp collected to track changes over time. A time-series database is a database system designed to store and retrieve timely data. Timestamped data can include data generated at regular intervals as well as data generated at unpredictable intervals.

6. ### Column oriented Databases

A column-oriented database stores the data in columns instead of rows.We can read those columns directly without consuming memory with the unwanted data.Columnar databases are designed to read data more efficiently and retrieve the data faster. A columnar database is used to store a large amount of data.





