# Intro to Data Structures

## Learning Goals

- Understand what a data structure is and how they are used in Python.
- Learn which types of tasks data structures are used to solve.

***

## Key Vocab

- **Sequence**: a data structure in which data is stored and accessed in a
specific order.
- **Index**: the location, represented by an integer, of an element in a
sequence.
- **Iterable**: able to be broken down into smaller parts of equal size that
can be processed in turn. You can loop through any iterable object.
- **Slice**: a group of neighboring elements in a sequence.
- **Mutable**: an object that can be changed.
- **Immutable**: an object that cannot be changed. (_Many immutable objects
appear mutable because programmers reuse their names for new objects_.)
- **List**: a mutable data type in Python that can store many types of data.
The most common data structure in Python.
- **Tuple**: an immutable data type in Python that can store many types of
data.
- **Range**: a data type in Python that stores integers in a fixed pattern.
- **String**: an immutable data type in Python that stores unicode characters
in a fixed pattern. Iterable and indexed, just like other sequences.

***

## Introduction

**Data** is information that has been standardized in such a way that it is
useful to the individual or machine that is working with it. Everything that
you see on your computer screen right now is composed of data. The letters
in this paragraph, the colors on this page, the links and buttons that navigate
to and from resources on the internet- all data.

In **Python Fundamentals**, we talked about the importance of organizing our
code for other humans to be able to read. After all, [a foolish consistency is
the hobgoblin of little minds][pep 8 hobgoblin]. **Data structures** are a way
for us to organize data in a way that is easy for computers to read.

[pep 8 hobgoblin]: https://peps.python.org/pep-0008/#a-foolish-consistency-is-the-hobgoblin-of-little-minds

***

## Why Don't We Just Put Everything in a List?

`list` objects are very useful for storing data in Python, but there are many
situations where a computer would want data stored in a different way.

To provide some perspective, let's compare a `list` with a `set`:

<table>
<tr>
<th> list </th>
<th> set </th>
</tr>
<tr>
<td>

<ul>Can store all types of data.</ul>

<ul>Indexed - Each item in a list has a set location.</ul>

<ul>Mutable - Can be extended or converted to another data type.</ul>

<ul>Items can be repeated.</ul>

<ul>Items can be changed or replaced.</ul>

</td>
<td>

<ul>Can store all types of data.</ul>

<ul>Unindexed - Items in a set are stored using an item's name.</ul>

<ul>Mutable - Can be extended or converted to another data type.</ul>

<ul>Items are unique.</ul>

<ul>Items cannot be changed or replaced.</ul>

</td>
</tr>
</table>

There are a number of similarities here, and it's clear that `list` objects
are much more flexible than `set` objects. But if we're looking for _which_
items exist rather than _how many_, a data structure with unique items that
allows us to access them by _name_ rather than _index_ is more useful. Lucky
for us, Python provides the `set` data structure out of the box!

***

## Types of Data Structures in Python

Python gives us access to a number of different data structures to help us
communicate with our computers. Some are built-in **data types** while others
require a little more work to set up.

### Data Types that are Data Structures

- Sequences:
  - `list`
  - `tuple`
  - `str`
- Sets:
  - `set`
  - [_`frozenset`_*](https://docs.python.org/3/library/stdtypes.html#frozenset)
- Maps:
  - `dict` (the only map type in Python!)

\* _We won't be covering these in our curriculum, but they may be useful to you
in advanced computing contexts_

### Trees and Linked Lists

Python does not come with _every_ data structure built into its data types, but
the standard library includes several modules and packages that help us build
out more complex data structures. Trees and linked lists are two of the most
common. We'll discuss these later on in Phase 3.

Be sure to check out the resources below as well, and bookmark them for future
reference!

***

## Resources

- [Python 3.8 documentation](https://docs.python.org/3.8/)
- [Python documentation: Data Structures](https://docs.python.org/3/tutorial/datastructures.html)
- [Common Python Data Structures](https://realpython.com/python-data-structures/)
