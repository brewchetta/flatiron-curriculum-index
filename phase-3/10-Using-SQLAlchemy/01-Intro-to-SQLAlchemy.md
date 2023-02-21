# Intro to SQLAlchemy

## Learning Goals

- Use an external library to simplify tasks from earlier ORM lessons.
- Manage database tables and schemas without ever writing SQL through Alembic.
- Use SQLAlchemy to create, read, update and delete records in a SQL database.

***

## Key Vocab

- **Schema**: the blueprint of a database. Describes how data relates to other
  data in tables, columns, and relationships between them.
- **Persist**: save a schema in a database.
- **Engine**: a Python object that translates SQL to Python and vice-versa.
- **Session**: a Python object that uses an engine to allow us to
  programmatically interact with a database.
- **Transaction**: a strategy for executing database statements such that
  the group succeeds or fails as a unit.
- **Migration**: the process of moving data from one or more databases to one
  or more target databases.

***

## Introduction

In our previous module, we learned about **ORMs**. Using `sqlite3` and concepts
in object-oriented programming in Python, we built tools to map Python classes
to database tables and vice-versa. This is a useful skill for your future work,
but it has some distinct limitations:

- It only works with one type of SQL database, `sqlite3`.
- It only covers the functionality that we needed for our `Dog` and `Song`
  classes.
- We won't know how other groups' ORMs work.
- Others won't know how our ORM works.

In order to address these concerns, several groups of programmers began
development on ORMs that had a broad range of compatibilites and functionality,
robust documentation, and regular maintenance to keep up with evolving
programming languages.

In our curriculum, we will be working with
[SQLAlchemy](https://www.sqlalchemy.org/), a popular Python ORM. There are
several other popular Python ORMS- most notably the
[Django](https://www.djangoproject.com/) ORM- but SQLAlchemy provides us the
most functionality without too much that we don't need. It is used by many big
tech companies like _Yelp!_, _reddit_, and _DropBox_.

That being said, SQLAlchemy is a _very_ powerful library, and we will only
cover a small fraction of its capabilities in this curriculum. There are many
fantastic resources available to you for free online or through Flatiron that
will allow you to continue to learn all about SQLAlchemy as you proceed through
your career.

***

## Resources

- [Python 3.8.13 Documentation - Python](https://docs.python.org/3.8/)
- [sqlite3 — DB-API 2.0 interface for SQLite databases - Python](https://docs.python.org/3/library/sqlite3.html)
- [SQLAlchemy ORM Documentation - SQLAlchemy](https://docs.sqlalchemy.org/en/14/orm/)
- [SQLAlchemy — Python Tutorial - Towards Data Science](https://towardsdatascience.com/sqlalchemy-python-tutorial-79a577141a91)
- [Alembic 1.8.1 Documentation - SQLAlchemy](https://alembic.sqlalchemy.org/en/latest/)
- [Tutorial (Alembic) - SQLAlchemy](https://alembic.sqlalchemy.org/en/latest/tutorial.html)
