---
Title: DBS101 Flipped class 5
categories: (DBS101,Flipped_class 5)
tags: (DBS101,Normal Forms)
---

### Topic: Normal Forms
----

This flipped class we discussed about the five different types of normal form. Before starting with the normal forms, we have to know what normalization is. So normalization is a technique using which we can organize the data in the database to make sure that there is less repetition of data, that a large set of data is stored properly into a bunch of smaller tables, and that the tables have proper relationship between them.

We were divided into 4 different groups and the first group was given the task of presenting about the first and second normal forms(1NF and 2NF). As we were the first group we shared that:

1. ### The first normal form(1NF) 
is basically the first step of the normalization process. 1NF is used to make the tables easier to extend and to retrive data from it whenever required. There are 4 rules we need to follow to design the database:

 - Single valued attributes: each column should have a single value.
 - Attribute domain should not change:each values in the column should be of the same type.
   - For example if we have column storing the age of people it should not contain values such as names of people.
 - Unique name for Attributes: each column should have a unique name.
 - Order doesn't matter: the order of the data stored in the table doesn't matter.

Below is an example of how we can convert a non-1NF table into 1NF form
- the table stores info about students and their courses but the column "courses" have multiple values which violates the 1NF rule

    | Student ID| Name | Courses         |
    |-----------|------|-----------------|
    |1	        | John |Math,Science     |
    |2	        |Alice |English, History |
    |3	        | Bob  |Math,English, Art|

- To convert the table into 1NF form we need to seperate the multivalued attribute to different rows.

     Student ID| Name | Courses         
    -----------|------|---------
    1	       | John |Math     
    1          |John  |Science
    2	       |Alice |English, 
    2          |Alice |History 
    3	       | Bob  |Math
    3          | Bob  |English
    3          |Bob   | Art

2. ### Second normal form(2NF) 
For a table to be in second normal form it needs to fulfill two conditions:

- the table should be in first normal form.
- there should not be any partial dependency.
  - partial dependency is a situation where an attribute depends on only a portion of the primary key rather than the whole primary key.

Below is an example of how we can remove a partial dependency:

Order_ID|Customer_ID|Product_ID|Order_Date|Customer_Name
--------|-----------|----------|----------|-------------
1	    | 101	    |201       |2024-03-24|	John
2	    |102	    |202	   |2024-03-25|	Alice
3	    |103    	|201	   |2024-03-26|	Bob

"Customer_Name" depends only on "Customer_ID" and not on the entire primary key ("Order_ID") which is a case of partial dependency and to remove it we need to make a new table for customers:

Customer_ID	| Customer_Name
------------|--------------
101	        |John
102	        |Alice
103	        |Bob

Modified Table "Orders":
Order_ID|Customer_ID|Product_ID|Order_Date|
--------|-----------|----------|----------|
1	    | 101	    |201       |2024-03-24|	
2	    |102	    |202	   |2024-03-25|	
3	    |103    	|201	   |2024-03-26|

The next presentation by group 2 was done on the topic Third Normal Form (3NF) and they shared that 

3. ### Third Normal Form (3NF)
For a table to be in third normal form it needs to fulfill two conditions:

- the table should be in second normal form.
- there should not be any transitive dependency.
  - transitive dependency is where an attribute is functionally dependent on another attribute, which in turn is functionally dependent on the primary key.

Below is an example of how we can remove a transitive dependency:
If we have a table where "Employee_ID" is the primary key and "Department_Name" depends on "Department_ID" and "Manager_Name" depends on "Manager_ID." but "Manager_ID" itself depends on "Department_ID". This creates a transitive dependency:

Original Table "Employee_Details":

Employee_ID|	Department_ID|	Department_Name|	Manager_ID|	Manager_Name|
-----------|-----------------|-----------------|--------------|-------------|
1	       | 101	         |Sales            |201           |John         |
2	       |102	             |Marketing	       | 202 	      |Alice        |
3	       |101          	 |Sales	           |203           |Bob          |

New Table "Department":

Department_ID|	Department_Name
-------------|------------------
101	         |Sales
102	         |Marketing

New Table "Employee":

Employee_ID	|Department_ID	|Manager_ID
------------|---------------|------------
1	        |101         	|201
2	        |102	        |202
3	        |101	        |203

By doing this, we removed the transitive dependency because "Manager_Name" no longer indirectly depends on "Department_ID" through "Manager_ID.".

The presentation by group 3 was on the topic Boyce-Codd Normal Form (BCNF) which was about:

4. ### Boyce-Codd Normal Form (BCNF)
It is an extension to the third normal form and can be also know as 3.5NF.
For a table to be in BCNF it has to satisfy the following two conditions:

- it should be in the Third Normal Form.
-  for a dependency A → B, A cannot be a non-prime attribute, if B is a prime attribute.
   - if a non-prime attribute determines a prime attribute, then the relation is not in BCNF. To bring the relation into BCNF, you would typically decompose it into smaller relations to eliminate this kind of dependency. 

Below is an example of how we can make the table into a BCNF.

Employee_ID	|Project_ID	|Employee_Name	|Project_Name|	Department
------------|-----------|---------------|------------|-------------
1	        |101        |John	        |Project X	 |IT
1	        |102	    |John	        |Project Y	 |IT
2	        |101	    |Alice	        |Project X	 |HR
3	        |102	    |Bob	        |Project Y	 |Finance

To bring the relation into BCNF, we decompose it into two relations:
- Relation Employees with attributes Employee_ID, Employee_Name, Department
- Relation Projects with attributes Project_ID, Project_Name

Updated relations:

Employees:

Employee_ID	|Employee_Name|	Department
------------|-------------|------------
1        	|John	      |IT
2	        |Alice	      |HR
3	        |Bob	      |Finance

Projects:

Project_ID|	Project_Name
----------|--------------
101	      |Project X
102	      |Project Y

The last group that is group 4 were given the topic Fourth Normal Form.

5. ### Fourth Normal Form(4NF)
For any table satisfy the fourth normal form it should satisfy the following conditions:
- It should be in the Boyce-Codd Normal Form.
- the table should not have any Multi-valued Dependency.
  - a multi-valued dependency occurs when one attribute determines multiple values of another attribute, but a third attribute remains independent of these relationships and you need at least three columns in a table.

Below is an example of how 4NF is implemented:
If we have a relation R(Student_ID, Subjects, Teacher) where:

- Student_ID is the primary key
- Subjects is a multi-valued attribute 
- Teacher is an attribute which not dependent on the subjects.

Student_ID	|Subjects|	Teacher
------------|--------|----------
1	        |Math, Sci|	Mr. A
2	        |Eng, Hist|	Mrs. B
3	        |Math, Eng|	Mr. C

Now to make this into 4NF we need to seperate it into two relations:

Relation R1(Student_ID, Subjects):

Student_ID|Subjects
----------|---------
1	      |Math
1	      |Sci
2	      |Eng
2	      |Hist
3	      |Math
3	      |Eng

Relation R2(Student_ID, Teacher):

Student_ID|	Teacher
----------|---------
1	      |Mr. A
2	      |Mrs. B
3	      |Mr. C

Now, each relation is in Fourth Normal Form (4NF), as there are no multi-valued dependencies, and all attributes are fully functionally dependent on the primary key.

                                                    THANK YOU