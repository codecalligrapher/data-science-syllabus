# Database  
**What are the different subsets of SQL?**  
Data Definition Language (DDL) – It allows you to perform various operations on the database such as CREATE, ALTER, and DELETE objects.  
Data Manipulation Language(DML) – It allows you to access and manipulate data. It helps you to insert, update, delete and retrieve data from the database.  
Data Control Language(DCL) – It allows you to control access to the database. Example – Grant, Revoke access permissions.  

**What is an ACID transaction?**  
A transaction is any operation that is treated as a single unit of work, which either completes fully or does not complete at all, and leaves the storage system in a consistent state.  
In the context of transaction processing, the acronym ACID refers to the four key properties of a transaction: atomicity, consistency, isolation, and durability. To ensure *ACID*, changes must be committed or rolled back.When a transaction completes normally, a transaction processing system commits the changes made to the data; that is, it makes them permanent and visible to other transactions.When a transaction does not complete normally, the system rolls back (or backs out) the changes; that is, it restores the data to its last consistent state.

#### Atomicity  
Each statement in a transaction (to read, write, update or delete data) is treated as a single unit. Either the entire statement is executed, or none of it is executed. This property prevents data loss and corruption from occurring if, for example, if your streaming data source fails mid-stream
#### Consistency  
Ensures that transactions only make changes to tables in predefined, predictable ways. Transactional consistency ensures that corruption or errors in your data do not create unintended consequences for the integrity of your table.
#### Isolation  
When multiple users are reading and writing from the same table all at once, isolation of their transactions ensures that the concurrent transactions don’t interfere with or affect one another. Each request can occur as though they were occurring one by one, even though they're actually occurring simultaneously.  
#### Durability
After a transaction successfully completes, changes to data persist and are not undone, even in the event of a system failure.  
For example, in an application that transfers funds from one account to another, the durability property ensures that the changes made to each account will not be reversed.  

---

**What do you mean by denormalization?**  
Denormalization refers to a technique which is used to access data from higher to lower forms of a database. It helps the database managers to increase the performance of the entire infrastructure as it introduces redundancy into a table. It adds the redundant data into a table by incorporating database queries that combine data from various tables into a single table.  

**What are Entities and Relationships?**  
*Entities*:  A person, place, or thing in the real world about which data can be stored in a database. Tables store data that represents one type of entity. For example – A bank database has a customer table to store customer information. The customer table stores this information as a set of attributes (columns within the table) for each customer.  

*Relationships*: Relation or links between entities that have something to do with each other. For example – The customer name is related to the customer account number and contact information, which might be in the same table. There can also be relationships between separate tables (for example, customer to accounts).

**What is Normalization and what are the advantages of it?**  
Normalization in SQL is the process of organizing data to avoid duplication and redundancy. Some of the advantages are:  

- Better Database organization
- More Tables with smaller rows
- Efficient data access
- Greater Flexibility for Queries
- Quickly find the information
- Easier to implement Security
- Allows easy modification
- Reduction of redundant and duplicate data
- More Compact Database
- Ensure Consistent data after modification   

**Explain different types of Normalization**
There are many successive levels of normalization. These are called normal forms. Each consecutive normal form depends on the previous one.The first three normal forms are usually adequate.  

- First Normal Form (1NF) – No repeating groups within rows
- Second Normal Form (2NF) – Every non-key (supporting) column value is dependent on the whole primary key.
- Third Normal Form (3NF) – Dependent solely on the primary key and no other non-key (supporting) column value.