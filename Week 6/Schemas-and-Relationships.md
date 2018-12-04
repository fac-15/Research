![schema santa](https://i.redd.it/x6snxvaykg301.jpg)

# Schemas and relationships

## What is a schema and why/when would you need one?

![schema visual representation](https://join-monster.readthedocs.io/en/stable/img/schema-sql.png)


A schema in relation to SQL is a collection of database objects (sorted in a **TABLE**).
The schema is associated with **ONE** database username, and this username is called the **schema owner**. 

You can have one or multiple schemas in a database.

A database schema represents the logical configuration of all or part of a relational database. It can exist both as a **visual** representation and as a **set of formulas** known as integrity constraints that govern a database. These formulas are expressed in a data definition language, such as SQL.

As part of a data dictionary, a database schema indicates how the entities that make up the database **relate to one another**, including tables, views, stored procedures, and more.

Typically, a database designer creates a database schema to **help programmers** whose software will interact with the database. 

![](https://media.giphy.com/media/SS2FYGce5XcWc/giphy.gif)



The process of creating a database schema is called **data modeling**. 



## What are primary keys and why do we need them?

![](https://cdn.dribbble.com/users/1309335/screenshots/3057896/key_dribbble.gif)

* **Good primary keys** are **essential** to good database design.
* They let you query and modify each table row individually without changing other rows in the same table. 
 
* A primary key's main features are:

    * It must contain a unique value for each row of data.
    * It cannot contain null values.

* It is important because it helps you link your table to other tables (relationships) using primary key as links.

* The major function of a primary key when creating a database is to implement relationships between tables in a relational database.

* You can **not** declare a foreign key in a table 'Q' to relate with table 'R' unless you have defined the primary key in table 'R'.
>
> ______________
> **Table 'R'** &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Table 'Q'**
> ______________
> **id** = PK &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | &nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **id** = PK &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;| &nbsp;&nbsp;&nbsp; **R-id** = FK
> ______________
> 300 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 220 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 300 <br/>
> 301 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 221 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 301 <br/>
> 302 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 222 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 302 <br/>
> 303 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 223 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 303 <br/>
> 304 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 224 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 304 <br/>
> 305 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 225 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 305 <br/>
> 306 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 226 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 306 <br/>
> ____________________________________________

* Every table should have a primary key. 
* Primary keys from other tables are foreign keys.
* When you create a new record or row, a new unique number is assigned to it's primary key column.
* If you delete a record from a table the unique primary key will be deleted and never used again.

The **PRIMARY KEY** uniquely identifies each record in a table. 

Primary keys must contain **UNIQUE** values, and cannot contain **NULL** values. A table can have only one primary key, which may consist of single or multiple fields.

>
> **Example:**

>CREATE TABLE Persons (
>    id SERIAL PRIMARY KEY,
>    LastName VARCHAR(255) NOT NULL,
>    FirstName VARCHAR(255) NOT NULL,
>    Age INTEGER
>);
>

Almost all individuals deal with primary keys frequently but unknowingly in everyday life. For example, students are routinely assigned unique identification (ID) numbers


## Joins
PKs can be used to join tables. 


SELECT * FROM publishers;

 id |           name           
----+--------------------------
  1 | The Big Publishing House
  2 | McGraw-Hill
  3 | No Starch Press
  4 | Mega Corp Ltd



SELECT * FROM books;

 id |               name                | release_date | publisher_id 
----+-----------------------------------+--------------+--------------
  1 | Python Made Easy                  | 1994-01-26   |    3
  2 | SQL: Part 2                       | 1979-06-01   |    1
  3 | JavaScript: The Really Good Parts | 1995-09-18   |    3
  4 | Java in Japanese                  | 1996-01-23   |            2
  5 | Elm Street                        | 2012-04-01   |            4
  6 | CSS: Cansei                       | 1994-10-10   |            1
  7 | Ruby Gems                         | 1996-12-25   |            2
  8 | C++                               | 2017-07-06   |            1
  9 | CoffeeScript in Java              | 2009-12-24   |            2
 10 | Swift in 10 Days                  | 2014-06-02   |            2

SELECT publishers.name 
FROM publishers 
INNER JOIN books 
	ON books.publisher_id = publishers.id 
	WHERE books.name = 'Python Made Easy';

      name       
-----------------
 No Starch Press

Find all the books published by 'No Starch Press'
SELECT publishers.name, books.name FROM publishers
INNER JOIN books
ON books.publisher_id = publishers.id
WHERE publishers.name = 'No Starch Press';

      name       |               name                
-----------------+-----------------------------------
 No Starch Press | Python Made Easy
 No Starch Press | JavaScript: The Really Good Parts
 
 
## Normalisation
A Database is in first normal form if:
Each record in a table is unique. It contains a unique key (or Primary key).
All values relate directly to the table and not part of another table.


## Create a visual representation of a mock schema for a database about Founders & Coders, using as many different kinds of relationship as you can. Explain the logic behind it.

![](https://i.imgur.com/H8SSVPx.png)
