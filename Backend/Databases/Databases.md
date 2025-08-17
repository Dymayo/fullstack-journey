- What is a database?
- What are relational databases?
- In what ways are relational databases different from XML?
- What is SQL?
- What is SQL used for?
- How to get all the records from a table in SQL?
- How to insert a record in SQL?

---

> _“The more we can organize, find, and manage information,
> the more we can function in our modern world.”_
> — *V.Cerf*

---

## The Importance of Data

- The right decisions come by successfully collecting data, organizing it, and studying it.

- Example: **Hans Rosling’s** _200 countries, 200 years_ (YouTube video) explains how Human progress is easily visualized by organizing data in graphs.



## Structured Data

To learn better the importance of structured data, we need to understand why unstructured data is a problem.

- If it accumulates for years, it will be a time-wasting task to find particular information.
- A system to structure your data is a must for effective browsing.

Here comes the role of **databases**:
**Definition:** A database is a structured set of data held in a computer.



## Spreadsheet as Database

- **Spreadsheet** ↔️ **Database**
- Worksheet ↔️ Tables
- Rows and columns ↔️ Records and columns  
Each row contains data for one individual.  
Each column contains data of one specific attribute.



## Relational Database Management System (RDBMS)

For a small-scale, spreadsheets can do their job.  
But as information grows over time, the amount is bound to increase.  
At this point, a spreadsheet is not enough to manage the data → here comes **RDBMS**.

#### Relational Database

is a database organized according to the **relational model** of data.

- A relational model defines a set of relations (tables) and describes the relationships between them, so the data stored in them is meaningful (rq: This model avoids duplicates. )

#### RDBMS

- A **RDBMS** is a software app or system for managing relational databases.
- It allows the user to interact with a database using established syntax.

**Examples of RDBMS:**

- MySQL
- SQLite
- MS SQL
- PostgreSQL

They all have the same underlying language: **SQL**.



## Other Structured Data Models

Besides RDBMS, other models exist:

- Document-oriented data storage models (e.g., **MongoDB** was its first).
- Non-relational data storage.
- Retrieved models (**NoSQL**).



## SQL

**Definition:**  
SQL is a programming language that is different.  
It is a **declarative language** → you write _what_ needs to be done, instead of _how_ it is done.  
The **RDBMS** handles the "how".

- SQL was conceived by **E.F. Codd** in the 1970s in his paper _“A Relational Model for Large Data Banks”_.
