# Intro to Object-Relational Mapping

## Learning Goals

- Create Python objects using SQL database records.
- Create SQL database records using Python objects.

***

## Key Vocab

- **Object-Relational Mapping (ORM)**: a technique used to convert database
records into objects in an object-oriented language.

***

## Introduction

As a relative newcomer to the programming world, terms like
_Object-Relational-Mapper_, or ORM, can sound really intimidating. The nice part
about ORM is that they can make it easier to write code once you understand
them.

You’ve already written your fair share of SQL queries in the previous section.
They usually look something like this:

```sql
SELECT * FROM schools WHERE name = 'Flatiron';
```

Object-relational mapping allows you to write queries like the one above, as
well as much more complicated ones, using the object-oriented paradigm of your
preferred programming language — in this case that would be Python.

In these lessons, we'll be covering these topics:

- The benefits of ORM.
- How ORMs can abstract database logic.
- How to use data from a database to make Python objects.
- Turning database rows into Python objects.
- Mapping a database table to a Python object.

In this section, you'll get to write in the language you are already learning
anyway. SQL is a powerful language, but most of us don’t write in it often.
Being able to leverage the fluency of Python to perform these actions is
awesome!

**IMPORTANT NOTE**: In this section, we'll be writing our very own Python ORM
that maps Python objects to a SQL relational database. In the section following
this one, we'll introduce an incredibly powerful Python ORM library called
SQLAlchemy that will have some of the same features we're building here by hand,
along with many, _many_ more.

Just like the section on SQL, it's less important that you are able to gain
mastery over writing your very own ORM. It's more important that you understand
_conceptually_ what an ORM is and how it works. So as long as you're able to
follow the code and grasp what it's doing, you are in good shape!

Think of this section like building a soap-box car: It's a fun project, but
ultimately, you wouldn't want to drive one every day! In the next section,
you'll get the keys to the _actual_ car (SQLAlchemy), along with our drivers ed
course so that you can operate it safely.

***

## Resources

- [sqlite3 - DB-API 2.0 interface for SQLite databases - Python](https://docs.python.org/3/library/sqlite3.html)
- [What is an ORM, how does it work, and how should I use one? - Stack Overflow](https://stackoverflow.com/questions/1279613/what-is-an-orm-how-does-it-work-and-how-should-i-use-one)
