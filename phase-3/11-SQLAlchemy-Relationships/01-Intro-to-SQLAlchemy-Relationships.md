# Intro to SQLAlchemy Relationships

## Learning Goals

- Use SQLAlchemy to join tables with one-to-one, one-to-many, and
  many-to-many relationships.

***

## Introduction

Previously, we worked through object-relational mapping and building Python
classes that can represent SQL tables. We also saw how SQLAlchemy is an
interface that gives you the tools to link a database to your application. It
lets you query and manipulate your data models in a logical and nearly
plain-English way.

So far, we've worked with applications that only have a single model. However,
as we saw in the SQL section, it's possible for data to be stored in multiple
related (associated) tables. How can we use SQLAlchemy to access that data
across multiple tables?

We'll cover topics that will include answers to these questions:

- What are common relationship methods accessible through SQLAlchemy?
- How do you configure one-to-one, one-to-many, and many-to-many relationships
  in SQLAlchemy?

Having a solid understanding of SQLAlchemy will make working with data much
easier. This will replace the need for a lot of the custom code we wrote when
creating ORMs. We’ll cover working with models, setting them up, and building
relationships between them.

***

## Resources

- [Python 3.8.13 Documentation](https://docs.python.org/3/)
- [SQLAlchemy ORM Documentation](https://docs.sqlalchemy.org/en/14/orm/)
- [Alembic 1.8.1 Documentation](https://alembic.sqlalchemy.org/en/latest/)
- [Basic Relationship Patterns - SQLAlchemy](https://docs.sqlalchemy.org/en/14/orm/basic_relationships.html)
