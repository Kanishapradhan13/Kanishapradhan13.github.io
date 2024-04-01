---
Title: DBS101 Flipped class 6
categories: (DBS101,Flipped_class 6)
tags: (DBS101,Nonrelational Databases)
---
## Topic: Database Storage Structures
----

### Guided Session

In this Practical 7 Guided session we learned about usage of various data storage and management techniques like simulating a fixed-block disk, requiring methods for allocation, reading, writing, and deallocation of contiguous blocks. We simulated RAID levels 0, 1, and 5, with features like striping, mirroring, and parity. It lets us arrange disks and block size, with functions reading, writing, and rebuilding data on failed disks using spare resources. Buffer pool management is important for efficient data retrieval in a database management system. The BufferPool class is made to cache frequently accessed database pages in memory, optimizes access times by fetching pages from the buffer and removing the least recently used pages when the buffer is full. We basically learned about creating a virtual storage system that mimics how real RAID systems work,  looking at how data is stored and retrieved across multiple disks, how to handle disk failures, and how to speed up data access by caching frequently used data.

### Exercise

As for the practical exercise we had do research on how relational databases are created from scratch and procedure to create a relational database. I learned that the process of creating a relational database involves defining the purpose and objectives of the database done by using ERD, followed by designing the schema to define the structure of tables and relationships.Then the third step involves selection of a suitable database management system (DBMS), as it will manage and operate the database. Next comes creating the database and tables based on the schema, showing relationships between tables using foreign keys, and inserting data into the tables. Indexes are then created to better the database performance by allowing faster searches and sorting. Finally, testing makes sure that the database functions correctly and meets the intended requirements.











