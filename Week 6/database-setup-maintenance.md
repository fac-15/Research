# Database: setup and maintentance

![](https://media.giphy.com/media/3o7527pa7qs9kCG78A/giphy.gif)
---

### What is a build script and why do you need one?

A build script is sequence of tasks to be execution in order, this will run all files, methods, functions within the script. a script has a start and finish which can be rerun whenever required.


- automates database build process over the whole project lifecycle
- allows for easier testing and deployment
- another thing to help you solve integration issues as they arise
- set up remote instances of your database - you may not have access to run SQL commands on a remote server (e.g. Heroku). A Build script will do this for you - presumably run by package.json?
- increase the speed of delivery of database changes
- teams can synchronize application and database changes


### An example from earlier:

> JavaScript file is run with node, which then calls the sql build file, to output the database

- In this example, we used a **Database Schema Script**. This is used to create a fresh database without any data.


**db_build.js**
```javascript
// import the fs module
const fs = require('fs');

// import connections file
const dbConnection = require('./db_connection');

// use fs module to read sql file
const sql = fs.readFileSync(`${__dirname}/db_build.sql`).toString();

// use the db connection with a query
dbConnection.query(sql, (err, res) => {
    if (err) throw err;
    console.log('Superheroes table created with result: ', res);
})
```


**db_build.sql**

```javascript
BEGIN;

DROP TABLE IF EXISTS users CASCADE;

CREATE TABLE users (
    id SERIAL PRIMARY KEY,
    name VARCHAR(100) NOT NULL,
    location TEXT NOT NULL,
);

INSERT INTO users (name, location) VALUES
    ('Sandra', 'Sweden'),
    ('Martin', 'Essex'),
    ('Charlie', 'France'),
    ('Oliver', 'Australia')
    
COMMIT;
```




## Database migration AKA schema migration 

![](https://media.giphy.com/media/xUA7aWCb6JLWK75Gwg/giphy.gif)


:computer: In computer programming, a schema is the organisation or structure of a database. 

- :runner: A database migration can be the process of transforming a previous version of a database into a newer version or of moving it to a different location. This process modifys the data without changing the schema.

- A migration can be done for multiple reasons: 
    - to change database vendors
    - upgrade the database software
    - move a database to the cloud

- :earth_africa: To do this, the data itself must be converted to an appropriate structure and form on the target platform.
 
- :key: Some key tasks in this process include 
    - assessing the database size to determine how much storage is needed
    - testing applications
    -  guaranteeing data confidentiality



The term 'Build' versus migration

![](https://media.giphy.com/media/4EEV33e0ZqtIw8Gmw9/giphy.gif)

-    In environments such as Production, Staging or User Acceptance Testing (UAT), teams sometimes use the term ‘the build’ to mean ” the required version of the database in that environment“. Unless the database doesn’t already exist, ‘the build’ is in fact a migration, and will modify the existing database to the required version, rather than “tear down and start again”.


---

### Building a Build Script

We don't have one at the moment, but when (the royal) we figure(s) out what the hell is going on with databases, we (I) will feel like this:

![database dance](https://media3.giphy.com/media/PBqh6hI41N5mg/giphy.gif?cid=3640f6095c06b15a633466347322a9a4)  ![database dance](https://media0.giphy.com/media/3O2PnmSJOPZvy/giphy.gif?cid=3640f6095c06b15a633466347322a9a4)
![database dance](https://media1.giphy.com/media/ykzXbY24BFqY8/giphy.gif?cid=3640f6095c06b1226341415441a91c06) ![database dance](https://media2.giphy.com/media/gof7cphwW2UMM/giphy.gif?cid=3640f6095c06b15a633466347322a9a4)
