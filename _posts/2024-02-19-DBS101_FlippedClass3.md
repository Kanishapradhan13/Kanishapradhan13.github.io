---
Title: DBS101 Flipped class 2
categories: (DBS101,Flipped_class 2)
tags: (DBS101)
---

### Topic: Set Operations and Null Values in SQL
----

In this flipped class we learned that in SQL, the Structured Query Language, accessing and modifying database tables is fundamental.We learned how null values are implemented and why we should put null values in a database. Null values are those values which has no data value. Null values are possible because information might not be available at the time of data entry. 
Null values has 3 different interpretations
- the value is unknown (data exists but is not known)
- the value is not available (data exists but is purposely withheld)
- Attribute is not applicable. For example if the value is 1000 for a Age column, the value is applied to the   age column

We can use 'IS NULL' command to check for null values and null values can be used for any datatypes.We also learned about set operations which can be used to combine two or more tables in a database.

The 4 different types of set operations are:
1.Union- this operation cancels duplicates from the tables and sorts the rest of the data in an ascending order.
2.Union all- this operation doesnot cancel the duplicates and lists all the values in the table.
3.Intersect- this operation returns common rows from both the tables.
4.Minus- this operation eliminates common rows from both the tables and displays rows present in the first      query but not in the second.

Understanding these principles in SQL is crucial for effective database management.