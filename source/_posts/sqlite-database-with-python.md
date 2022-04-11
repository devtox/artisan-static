---
title: SQLite Database with Python
date: 2022-04-11
image: /assets/images/pyqt-qpushbutton.png
comments: true
---
SQLite is a relational database management system (RDBMS), similar to MySQL, Oracle, PostgreSQL, and Microsoft SQL Server. However, unlike these other database systems, SQLite is not a client-server database engine. Instead, it is embedded into the application that accesses the database. This makes SQLite suitable for use in mobile applications, web browsers, and general purpose programming languages.

SQLite was first released in 2000 and has since become one of the most widely used database systems in the world. As of 2019, SQLite is installed on more than 1 billion devices worldwide. The source code for SQLite is in the public domain and can be used for any purpose without restrictions.

SQLite supports standard relational database features such as tables, indexes, transactions, and constraints. It also supports some non-standard features such as triggers and foreign key constraints.

## SQL language

SQL is a language used to manage databases. It stands for Structured Query Language and can be pronounced as "sequel" or "S-Q-L." SQL is used to query, insert, update, and delete data from a database. In addition, it can be used to create views, indexes, and stored procedures. SQL is not case sensitive, meaning that you can use upper or lower case letters interchangeably. However, most people prefer to use all uppercase letters when writing SQL code.


## sqlite3

The Python standard library includes a module called sqlite3 which allows developers to easily interact with stored data using Python objects and syntax.  SQLite is a lightweight disk-based database which doesn't require a separate server process and allows accessing the database using a nonstandard variant of the SQL query language.

Example usage:

```
# sqlite3 is built into python3 and can be used direct
import sqlite3

# Get the database connection
con = sqlite3.connect('database.db3')

# Get the cursor object
cur = con.cursor()

# add table called foo in the database
cur.execute('CREATE TABLE foo (o_id INTEGER PRIMARY KEY, fruit VARCHAR(20), veggies VARCHAR(30))')
con.commit()

# add data to table
cur.execute('INSERT INTO foo (o_id, fruit, veggies) VALUES(NULL, "apple", "broccoli")')
con.commit()

# add another row to the table
cur.execute('INSERT INTO foo (o_id, fruit, veggies) VALUES(NULL, "berry", "salad")')
con.commit()

# show data
cur.execute('SELECT * FROM foo')
print(cur.fetchall())
```

This program outputs

```
[(1, 'apple', 'broccoli'), (2, 'berry', 'salad')]
```

If you run it again, it shows an error that the table already 
exists.

```
Traceback (most recent call last):
  File "/home/frank/test.py", line 8, in <module>
    cur.execute('CREATE TABLE foo (o_id INTEGER PRIMARY KEY, fruit VARCHAR(20), veggies VARCHAR(30))')
sqlite3.OperationalError: table foo already exists
```

To solve this either remove the table, delete the database file or simply just skip creating the table (only create the database table on first run).

In this example you saw several SQL queries. Namely:

* the *CREATE TABLE* query which creates a dataasbe table.
* the *INSERT INTO* query that adds data to the table
* the *SELECT* query that gets data from the table

You can also loop over the database table like so:

```
# show data
cur.execute('SELECT * FROM foo')
res = cur.fetchall()
for line in res:
    for f in line:
        print(f)
```
  
**Common Methods**

Using the cursor you can fetch data or run SQL queries directly from Python. 

```
cur.execute('sql') # Execute sql
cur.fetchone() # fetches the first result
cur.fetchmany(n) # fetch n results
cur.fetchall() # Get all results
```

You use the SQL language to interact with the database.  Execute sql to get the result.

```
sql = 'select * from table_name'
cur.execute(sql)
res = cur.fetchall()
```

When closing your program, you want to close the connections.

```
# Close the connection
cur.close()
conn.close()
```


### CRUD

A database has four operations: Create, Read, Update, Delete (CRUD). You can do those operations using SQL queries. In this paragraph I will explain these operations.

Let's say we have a table called "users" and it has three columns: "name", "email", and "password". Creating this table is as simple as running the following SQL:

```
CREATE TABLE users (name TEXT, email TEXT, password TEXT);
```

To insert data into the table, we use the INSERT INTO statement:

```
INSERT INTO users (name, email, password) VALUES ('John', 'john@example.com', '1234');
```

Reading from the database is just as easy. We use the SELECT statement to select specific columns from our table: 

```
SELECT name FROM users; // Returns all names in the 'users' table
```

Alternatively we can select all columns (*):

```
SELECT * FROM users; // Returns everything in the 'users' table
```

Updating data in our database is done using the UPDATE statement:

```
UPDATE users SET name = 'Jane' WHERE id = 1; // Sets Jane as the name for user with id 1
```

Finally, deleting data is done with DELETE:

```
DELETE FROM users WHERE id = 1; // Deletes user with id 1
```


