# :syringe::syringe::syringe:  Script Injections :syringe::syringe::syringe: 


![](https://media.giphy.com/media/SpmB1emE8v1gk/giphy.gif)
## What is a script injection and how do these happen?

💣 A <b>script injection</b> is a security vulnerability where an attacker can insert malicious code into the user interface of your website. Code injection techniques are popular in system hacking or cracking to gain information, privilege escalation (exploiting a bug or design flaw) or unauthorized access to a system. 

### How does one inject? 👹
- Direct entry into a web page form or inline editable HTML

- As part of a URL path or query string which is used in dynamic HTML generation or form population

- Data acquired using other means that is added to objects or arrays your code creates. This could include POST data sent directly to your server or headers and content you receive by your code making a request of a malicious or hi-jacked server

### Why SQL injection?
- Identify injectable parameters.
- Identify the database type and version. 
- Discover database schema.
- Extracting data.
- Insert, modify or delete data.
- Denial of service to authorized users by locking or deleting tables.
- Bypassing authentication.
- Privilege escalation.
- Execute remote commands by calling stored functions within the DBMS which are reserved for administrators.


### SQL injection method
Here are some methods through which SQL statements are injected into vulnerable systems
- Injected through user input.
- Injection through cookie fields contains attack strings.
- Injection through Server Variables.
- Second-Order Injection where hidden statements to be executed at another time by another function.


![](https://media.giphy.com/media/9VbjdIHeFGgqQ/giphy.gif)

- HTML/Script injection is also called <b>cross-site scripting</b> or <b><i>XSS</i></b>. 
- This is different, however, to SQL injection.
- "The main difference between a SQL and XSS injection attack is that SQL injection attacks are used to steal information from databases whereas XSS attacks are used to redirect users to websites where attackers can steal data from them."💰 ( [XSS vs SQL injections](https://keirstenbrager.tech/sql-vs-xxs-injection-attacks-explained/) )

These are all common places for script injections:
```
<script>
<meta>
<html>
<body>
<embed>
<frame>
<frameset>
<img>
<style>
<link>
<object>
```

![](https://media.giphy.com/media/ZvLUtG6BZkBi0/giphy.gif)

## How would you prevent script injections?

1. You can disable request validation in your Web page



2. Use ```Server.HTMLEncode()``` to encode user's input
    Example: 
    ```Javascript
    String strName =  Server.HtmlEncode(TextBox1.Text);
    Response.Write("Name: "+strName);```
  
3. Rejecting certain special characters like, "<", ">", "*", "%", "!", "@", etc. - using regex, perhaps?

- Often, people suggest 'escaping' characters and sanitizing inputs, but many experts suggest otherwise because those methods are prone to error.
    - Bobby-tables.com claims that there are two ways to avoid it:
    1. Do not create SQL statements that include outside data.
    2. (Learn and) use parameterized SQL calls.

- "A parameterized query is a query in which placeholders are used for parameters and the parameter values are supplied at execution time"
- [this](https://blogs.msdn.microsoft.com/sqlphp/2008/09/30/how-and-why-to-use-parameterized-queries/) website seems to explain it well but there wasn't enough tmie to properly go through it ...

<b>TAKE A LOOK AT THIS SITE FOR INFO ON <i>CLEANER</i> FUNCTIONS:</b>
https://codeburst.io/a-little-cleaner-preventing-html-javascript-injection-fb10ae748b9e


## SQL Injection🛠

<i>SQL injection is where nefarious SQL statements are inputted into an entry field to tamper with the database. </i>

<b>Incorrectly filtered escape characters</b>

An example:
``` 
statement = "SELECT * FROM users WHERE name = '" + userName + "';"
```

This allows a hacker to set the userName variable to 1=1 by inputting something like:

```
' OR '1'='1' --
' OR '1'='1' {
' OR '1'='1' /* 
```


<b>SQL Injection Based on 1=1 is Always True.</b>

If there is nothing to prevent a user from entering "wrong" input, the user can enter some "smart" input like this:

`UserId: 
105 OR 1=1`

Then, the SQL statement will look like this:

`SELECT * FROM Users WHERE UserId = 105 OR 1=1;`

The SQL above is valid and will return ALL rows from the "Users" table, since OR 1=1 is always TRUE.

`SELECT UserId, Name, Password FROM Users WHERE UserId = 105 or 1=1;`

A hacker might get access to all the user names and passwords in a database, by simply inserting 105 OR 1=1 into the input field.


## Bobby Tables (thanks for the tip Emma!)
- Website that contains guides for various languages to help prevenet SQL injection.

![](https://i.imgur.com/XgbPr9z.png)
[Bobby Tables: A guide to preventing SQL injection](http://bobby-tables.com/about)

Below is an explanation from the website about how this would work:

- The school apparently stores the names of their students in a table called Students. When a new student arrives, potentially as follows:

``` 
$sql = "INSERT INTO Students (Name) VALUES ('" . $studentName . "');";
execute_sql($sql);
```

- The problem of this code is that outside data, in this case the content of $studentName, becomes part of the SQL statement.

- Here is how it might work with a regular student's name:

```
INSERT INTO Students (Name) VALUES ('John');
```

- This does exactly what we want: it inserts John into the Students table.

 - Now we insert little Bobby Tables, by setting ```$studentName``` to ```Robert'); DROP TABLE Students;--```. The SQL statement becomes:

```
INSERT INTO Students (Name) VALUES ('Robert'); DROP TABLE Students;--');
```
- This inserts Robert into the Students table. However, the INSERT statement is now followed by a DROP TABLE statement which removes the entire Students table. :sos: 
 

## Script Injection famous cases 

![](https://media.giphy.com/media/NCnIhytUUP7fq/giphy.gif)

**Seagate cloud storage** crikey https://appuals.com/sql-injection-vulnerabilities-in-seagate-personal-cloud-media-server-allow-retrieval-of-private-data/ 

... a public folder exists to which unauthorized users have the right to upload data and files.

According to the advisory, this public folder facility can be abused by malicious attackers when they upload troublesome files and media to the folder in the cloud. These unauthorized attackers’ files can then behave the way they’ve been designed to, allowing for arbitrary data retrieval and modification in the media server’s database. 

**Def Con hackathon - website for the Florida Secretary of State**
https://techcrunch.com/2018/08/12/hacking-the-websites-responsible-for-election-information-is-so-easy-an-11-year-old-did-it/ 

**McAfee in 2017**
https://www.cso.com.au/article/613679/dangerous-hole-found-mcafee-epo-antivirus-central-management-suit/

**Faithless fan website** - https://www.infosecurity-magazine.com/news/faithless-fans-suffer-data-breach/

## Prepare a short demonstration of good (and bad?) practices, including some sample code





u ok hun :sparkles: 

## Extra stuff

[Here's a video](https://www.troyhunt.com/hacking-is-childs-play-sql-injection/) of a developer teaching his 3 year-old how to carry out an SQLi attack 
