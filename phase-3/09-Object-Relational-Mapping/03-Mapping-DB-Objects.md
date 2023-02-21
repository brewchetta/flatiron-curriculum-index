# Mapping Database Records to Python Objects

## Learning Goals

- Create Python objects using SQL database records.
- Create SQL database records using Python objects.

***

## Key Vocab

- **Object-Relational Mapping (ORM)**: a technique used to convert database
records into objects in an object-oriented language.

***

## Introduction

In this lesson, we'll cover the basics of reading from a database table that is
mapped to a Python object.

Our Python program gets most interesting when we add data. To do this, we use a
database. When we want our Python program to store things, we send them off to a
database. When we want to retrieve those things, we ask the database to send
them back to our program. This works very well, but there is one small problem
to overcome— our Python program and the database don't speak the same language.

Python understands objects. The database understands raw data.

We don't store Python objects in the database, and we don't get Python objects
back from the database. We store raw data describing a given Python object in a
table row, and when we want to reconstruct a Python object from the stored data,
we select that same row in the table.

When we query the database, it is up to us to write the code that takes that
data and turns it back into an instance of the appropriate class. We, the
programmers, will be responsible for translating the raw data that the database
sends into Python objects that are instances of a particular class.

***

## Code Along

Let's continue building out the `Song` class and its object-relational mapping
methods from the previous lesson. We can use our code to make new songs and
persist them to the database, but what if we want to access existing songs from
the database?

We need to build three methods to access all of those songs and convert them to
Python objects.

To start, review the code from the `Song` class. Then take a look at this code
in the `debug.py` file:

```py
# debug.py

from song import Song, CONN, CURSOR

def reset_database():
    Song.drop_table()
    Song.create_table()
    Song.create("Hello", "25")
    Song.create("99 Problems", "The Black Album")


reset_database()

import ipdb; ipdb.set_trace()
```

This file is set up so that you can explore the database using the `Song` class
from an `ipdb` session. We'll use this code later on during this code along.

***

## `new_from_db()`

The first thing we need to do is convert what the database gives us into a Python
object. We will use this method to create all the Python objects in our next two
methods.

One thing to know is that the database, SQLite in our case, will return an array
of data for each row. For example, a row for Michael Jackson's "Billie Jean"
from the album "Thriller" that has an id of 1 would look like this:
`[1, "Billie Jean", "Thriller"]`.

```py
class Song

    # ... rest of methods

    @classmethod
    def new_from_db(cls, row):
        song = cls(row[1], row[2])
        song.id = row[0]
        return song
```

Now, you may notice something — since we're retrieving data from a database, we
are using the class constructor through `cls`. We don't need to _create_
records. With this method, we're reading data from SQLite and temporarily
representing that data in Python.

***

## `get_all()`

Recall that in previous lessons with Python classes, we used the `all` class
attribute to represent all instances of our class. In those examples, `all` was
the **single source of truth** for instances in a particular class.

That approach showed some limitations, however. Using that attribute meant that
our Python objects were only persisted in memory as long as our Python program
was running. If we exited the program and re-ran our code, we'd lose access to
that data.

Now that we have a SQL database, our classes have a new way to persist data:
using the database!

To return all the songs in the database, we need to execute the following SQL
query: `SELECT * FROM songs`. Let's store the statement that represents this
action in a variable called `sql` using a multi-line string (`"""`). This query
won't be very long, but this is best practice for SQL statements as many get
_quite_ long.

```py
sql = """"
  SELECT *
  FROM songs
"""
```

Next, we will make a call to our database using `CURSOR`. This `sqlite3.Cursor`
object is located in `song.py`.

```py
# song.py

import sqlite3

CONN = sqlite3.connect('music.db')
CURSOR = CONN.cursor()
```

Our `sqlite3.Cursor` instance will respond to a method called `execute` that
accepts raw SQL as a string (as we've seen a couple times already). The
`fetchall()` method will then return the rows sequentially in a tuple. Let's
pass in that SQL we stored above:

```py
class Song

    # you don't need this, but default empty values can help you avoid errors later on
    all = []

    # ... rest of methods

    @classmethod
    def get_all(cls):
        sql = """
            SELECT *
            FROM songs
        """

        all = CURSOR.execute(sql).fetchall()
```

This will return an array of rows from the database that matches our query. Now,
all we have to do is iterate over each row and use the `new_from_db()`
create a new Python object for each row:

```py
class Song

    all = []

    # ... rest of methods

    @classmethod
    def get_all(cls):
        sql = """
            SELECT *
            FROM songs
        """

        all = CURSOR.execute(sql).fetchall()

        cls.all = [cls.new_from_db(row) for row in all]
        return cls.all
```

With this method in place, let's try using the `get_all()` method from `ipdb` to
access all the songs in the database. Run `python debug.py`, and then follow
along in the `ipdb` shell:

```py
Song.get_all()
# => [<lib.song.Song object at 0x101346680>, <lib.song.Song object at 0x101e50d60>]
```

To see a bit more detail, we can use the `.__dict__` attribute that Python
assigns to new objects:

```py
[song.__dict__ for song in Song.all]
# => [{'id': 1, 'name': 'Hello', 'album': '25'}, {'id': 2, 'name': '99 Problems', 'album': 'The Black Album'}]
```

Success! We can see both songs in the database as an array of song instances. We
can interact with them just like any other Python objects:

```py
Song.all[0].__dict__
# => {'id': 1, 'name': 'Hello', 'album': '25'}
Song.all[-1].__dict__
# => {'id': 2, 'name': '99 Problems', 'album': 'The Black Album'}
Song.all[-1].name
# => "99 Problems"
Song.all[-1].name[::-1]
# => "smelborP 99"
```

## `find_by_name()`

This one is similar to `get_all()`, with the small exception being that we have
to include a `name` in our SQL statement. To do this, we use a question mark
where we want the `name` parameter to be passed in, and we include `name` as the
second argument to the `execute()` method:

```py
class Song:

    # ... rest of methods

    @classmethod
    def find_by_name(cls, name):
        sql = """
            SELECT *
            FROM songs
            WHERE name = ?
            LIMIT 1
        """

        song = CURSOR.execute(sql, (name,)).fetchone()

        return cls.new_from_db(song)

```

There are a couple important things to note here:

- Bound parameters must be passed to the `execute` statement as a sequence
  data type. This is typically performed with tuples to match the format that
  results are returned in. A tuple containing only one element must have a
  comma after that element, otherwise it is interpreted as a grouped statement
  (think [PEMDAS]https://en.wikipedia.org/wiki/Order_of_operations).
- The `fetchone()` method returns the first element from `fetchall()`.

Let's try out this new method. Exit `pdb` and run `python debug.py` again:

```py
Song.find_by_name("Hello").__dict__
# => {'id': 1, 'name': 'Hello', 'album': '25'}
```

Success!

***

## Conclusion

At this point, we have created a database and records with Python and pointed
those records back toward our Python class. We haven't covered every use case,
but we have a functioning ORM! In the next lesson, we will put these skills to
the test.

***

## Resources

- [sqlite3 - DB-API 2.0 interface for SQLite databases - Python](https://docs.python.org/3/library/sqlite3.html)
