# SQL vs NoSQL 

**relational (SQL)** vs **non-relational (NoSQL)** data structure

tl;dr: Key difference: Language, structure.

Analogy: 
- **Relational**: a town where everyone speaks the same language. **Changing that language in one place would be confusing and disruptive for everyone**.

- **Non relational**: another town where every home can speak a different language. Everyone interacts with the world differently, and there’s no “universal” understanding or set organization. **If one home is different, it doesn’t affect anyone else at all**.

### SQL is Relational: 

- It requires that you use **predefined schemas** to determine the structure of your data before you work with it. 
- In addition, all of your data must follow the **same structure**.

### NoSql is non relational 

- has dynamic schema for unstructured data
- data is stored in many ways: it can be column-oriented, document-oriented, graph-based or organized as a KeyValue store. 


#### SQL Pros: 

- SQL databases are **table-based**, while NoSQL databases are either document-based, key-value pairs, graph databases or wide-column stores. This makes **relational SQL databases a better option for applications that require multi-row transactions** - such as an accounting system - or for legacy systems that were built for a relational structure.

#### SQL Cons: 

- This can require **significant up-front preparation**.
- As with the first town (one language), it can mean that a change in the structure would be **both difficult and disruptive** to your whole system.

#### NoSQL Pros: 

- This flexibility means that: You can create documents without having to first define their structure
- Each document can have its own unique structure
- The syntax can vary from database to database, and
- You can add fields as you go.
- NoSQL databases the preferred choice for **large or ever-changing data sets**.

#### NoSQL Cons:

- You **cannot easily query across the diverse collection** of tables.
- Compared to NoSQL - SQL uses a powerful **declarative language** for querying. 


## Example queries:

#### SQL 

```sql
SELECT * FROM inventory
```

#### The same query in MongoDB: 

```mongodb
db.inventory.find( {} )
```
----------
#### SQL

```sql
SELECT * FROM inventory WHERE status = "D"
```

#### This operation corresponds to the following MongoDb statement:

```mongodb
db.inventory.find( { status: "D" } )
```


## SQL Tables vs NoSQL Documents

**SQL databases** provide a store of related data tables. For example, if you run an online book store, book information can be added to a table named `book`:


![](https://i.imgur.com/l0wMPpj.png)


Every row is a different book record. The design is rigid; you cannot use the same table to store different information or insert a string where a number is expected.

---
**NoSQL databases** store JSON-like field-value pair documents, e.g.

```
{
  ISBN: 9780992461225,
  title: "JavaScript: Novice to Ninja",
  author: "Darren Jones",
  format: "ebook",
  price: 29.00
}
```

Similar documents can be stored in a collection, which is analogous to an SQL table. However, you can store any data you like in any document; the NoSQL database won’t complain. For example:

```
{
  ISBN: 9780992461225,
  title: "JavaScript: Novice to Ninja",
  author: "Darren Jones",
  year: 2014,
  format: "ebook",
  price: 29.00,
  description: "Learn JavaScript from scratch!",
  rating: "5/5",
  review: [
    { name: "A Reader", text: "The best JavaScript book I've ever read." },
    { name: "JS Expert", text: "Recommended to novice and expert developers alike." }
  ]
}
```


- When to use one versus another


- **Examples of SQL databases**: include MySQL, Oracle, PostgreSQL, and Microsoft SQL Server. 
- **Examples of NoSQL database**: include MongoDB, BigTable, Redis, RavenDB Cassandra, HBase, Neo4j and CouchDB.
