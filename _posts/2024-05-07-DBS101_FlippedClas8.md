---
Title: DBS101 Flipped class 8
categories: (DBS101,Flipped_class 8)
tags: (DBS101,Indexing)
---
# Topic: Indexing 
----

In our eighth flipped class session, we learned about different types of indexing. The types of indexing we discussed about are: Indexing of Spatial and Temporal Data, Bitmap Indices and Buffer Tree.

We were divided into 6 different groups but the the group division was done interestingly. Each of ur were give a piece of paper with a snippet of lyrics of a popular song and to find our group members we had to sing the song. We were then given our topic after forming the discussion groups.

After finishing the discussion we into two expert groups where each member from the discussion group shared their topics.

## 1. Indexing of Spatial and Temporal Data

- Spatial Data: This refers to anything related to location, like addresses, points of interest on a map, or geographical boundaries.
- Temporal Data: is anything  about time-related information, like dates, timestamps, or durations (e.g., how long a video is).

Indexing spatial and temporal data is like creating specialized search tools for location and time-based information. This allows for faster and more efficient retrieval of data, making it a crucial technique for various applications that deal with these data types.

---

## 2. Bitmap Indices

Bitmap indexes are designed to efficiently search for data based on specific values.For each value , a separate bitmap is created. The size of the bitmap is equal to the number of data records in the table.In each bitmap, a bit position corresponds to a specific data record. If the record has the desired value, its corresponding bit is set to 1. Otherwise, it's set to 0.When searching for a specific value, the computer only needs to look at the corresponding bitmap. The marked bits (1s) tell it which records have that value.

---

## 3. Buffer Tree

Buffer trees are efficient for handling write-heavy workloads.A buffer tree is not a standard data structure used within a DBMS itself. However, the term "buffer" in DBMS often refers to a memory area that temporarily stores frequently accessed data from disk storage. This buffer can be implemented using various data structures, including B-trees.

#### Advantages of Using B-Tree-Based Buffers:

- Faster Data Access: By searching the B-tree index, the DBMS can quickly identify the relevant data block on disk.

- Improved Cache Utilization: Frequently accessed data blocks are more likely to be located in the buffer, reducing disk I/O and overall query execution time.

- Scalability: B-trees can handle large data effectively due to their self-balancing nature. As the data volume increases, the B-tree index can adapt to maintain search efficiency,

After discussing our topics with the other group members we did a quiz session competing with the other group. 

This flipped class was unique and interesting compared to the previous flipped classes.





