---
Title: DBS101 Flipped class 11
categories: (DBS101,Flipped_class 11)
tags: (DBS101,Concurrency Control )
---
# Topic: Concurrency Control  
----

# Concurrency Control 

![concurrencycontrol](/assets/img/concurrency.png)

Locks play a crucial role in concurrency control within database management systems (DBMS). They help ensure data integrity and consistency when multiple transactions are executed simultaneously.

When multiple transactions access and modify the database concurrently, locks ensure that the database remains in a consistent state where it prevent two transactions to modify at the same data simultaneously, which could lead to inconsistencies.

Locks help maintain the ACID properties of transactions

Different types of locks provide different levels of control over the data:

- Shared Locks (S-Locks): Allow multiple transactions to read the same data concurrently but prevent any transaction from modifying the data.

- Exclusive Locks (X-Locks): Allow a transaction to modify data, preventing other transactions from reading or modifying the data.

### Two-Phase Locking (2PL) Protocol

Two-phase locking is a common concurrency control method. Even though 2PL ensures <b>serializability</b> but can lead to deadlocks.

- Growing Phase: A transaction may obtain locks but not release any.

- Shrinking Phase: A transaction releases its locks and cannot obtain any new locks.

### Deadlocks
A potential downside of locking is deadlocks, where two or more transactions wait indefinitely for each other to release locks. Deadlock detection and resolution mechanisms are essential to handle such scenarios.

### Two ways of dealing with deadlocks:
1. Deadlock Detection
2. Deadlock Prevention

### Deadlock Detection
<b>Wait-for Graph (WFG)</b> is constructd based on the current state of resource allocation and process requests.

An edge from process Pi to Pj indicates Pi is waiting for a resource held by Pj.

A cycle in this graph is a direct indication of deadlock.

![wfg](/assets/img/wfg.png)

### Deadlock Prevention
Necessary Conditions for Deadlock

- Mutual Exclusion: At least one resource must be held in a non-shareable mode.
- Hold and Wait: A process holding at least one resource is waiting to acquire additional resources held by other processes.
- No Preemption: Resources cannot be forcibly taken from processes holding them.
- Circular Wait: A closed chain of processes exists such that each process holds at least one resource needed by the next process in the chain.

![holdandwait](/assets/img/holdnwait.png)
### Lock Granularity
Locks can be applied at various levels of granularity:

- Row-Level Locks: Allow concurrent access to different rows of the same table.
- Table-Level Locks: Lock the entire table, preventing other transactions from accessing or modifying any rows in the table.
- Page-Level Locks: Lock a database page (a fixed-length block of data), which can contain multiple rows.


### Predicate Reads in Concurrency Control
- Predicate reads can conflict with inserts/updates that affect tuples satisfying the predicate.
- Known as the <b> phantom phenomenon.</b>
- Prevented by locking index entries/leaf nodes or using predicate locking


### Optimistic vs. Pessimistic Locking

<b>Pessimistic Locking:</b> Assumes that conflicts are likely to occur, so it locks resources before accessing them.

<b>Optimistic Locking:</b> Assumes conflicts are rare, so it checks for conflicts before committing the transaction.

### locking in practice 

![lock](/assets/img/lock.png)

![lock](/assets/img/lock1.png)

#### SHARE Mode:
Allows read and schema modification operations but not data modification operations within the same transaction.

![lock](/assets/img/lock2.png)

#### EXCLUSIVE Mode: 
Allows full access (read, write,delete) to the table, blocking all other transactions.

![lock](/assets/img/lock3.png)

![lock](/assets/img/lock4.png)

#### FOR UPDATE: 
Acquires an exclusive lock on the selected rows, allowing modifications on those rows.

#### FOR SHARE:
Acquires a shared lock on the selected rows,preventing other transactions from acquiring exclusive locks but allows updates within the same transaction.

![lock](/assets/img/lock5.png)

### Timestamp Ordering Concurrency Control
Timestamp Ordering Concurrency Control is a method used in databases to manage transactions and ensure they occur in a consistent and conflict-free manner.

<b>Timestamps:</b> Each transaction is given a unique timestamp when it starts. This timestamp helps determine the order of transactions.

<b>Transaction Order:</b> Transactions are ordered by their timestamps. The database uses these timestamps to decide the sequence in which operations should occur.

- By ordering transactions based on their timestamps, the system ensures that the database remains consistent and free from conflicts, even when multiple transactions occur simultaneously.

## Conclusion
Locks are fundamental to concurrency control as they ensure the safe and consistent execution of concurrent transactions. They maintain ACID properties, and provide a structured way to manage access to the database in multi-user environments. Proper implementation and management of locks are essential for the reliability and performance of a DBMS.




