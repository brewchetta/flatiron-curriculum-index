# Sets

## Learning Goals

- Utilize Python's `set` data type to accomplish several programming tasks.
- Execute and test Python code using the Python shell.

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

**Sets** are the last built-in data structure in Python. Sets share the
following characteristics:

- Set elements are _unique_. Duplicates are not supported.
- Set elements are _unordered_. This means that they cannot be accessed by
  index.
- Sets are mutable, but can only _store_ immutable data.

Like lists, tuples, and dictionaries, sets can be defined using their class
constructor or with brackets:

```py
my_set = set([1, 2, 3])
my_set = {1, 2, 3}
```

> NOTE: Instantiating an empty set requires the use of the `set()` class
> constructor. Closed curly brackets `{}` will instantiate an empty dictionary.

***

## When Are Sets Used?

Sets are much less commonly used than sequences and maps, but they can be
helpful in accomplishing a handful of common tasks:

Instantiating a set using a sequence is a good way to isolate unique members:

```py
my_list = [1, 2, 1, 3, 2]
set(my_list)
# {1, 2, 3}
```

...though it is important to remember that sets are unordered, so our output
might not be pretty:

```py
my_string = "the big red cat ate the fat rat"
set(my_string)
# {'g', 'h', 'b', 'r', 'e', 'd', 'f', 'c', 't', 'a', 'i', ' '}
```

To determine if two collections have the same members, we can check their sets:

```py
set(range(1, 10)) == set([1, 2, 3, 4, 5, 6, 7, 8, 9])
# True
```

If the sets are not identical, we can use the intersection `&` operator to see
what they have in common:

```py
set_1 = {1, 2, 3}
set_2 = {3, 4, 5}
set_1 & set_2
# 3
```

...or we can check for differences using the difference `-` operator:

```py
set_1 = {1, 2, 3}
set_2 = {3, 4, 5}
set_1 - set_2
# {1, 2}
set_2 - set_1
# {4, 5}
```

Using these operators also allows us to dynamically modify sets as our program
runs:

```py
set_1 = {1, 2, 3}
set_2 = {3, 4, 5}
set_1 &= set_2
# {3}
set_2 -= set_1
# {4, 5}
```

Sets also support comprehensions with the same syntax as lists:

```py
sentence = "Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua."
unique_consonants = {c.lower() for c in sentence if c not in "aeiou ,."}
# {'g', 'p', 'b', 'l', 'r', 'd', 'm', 'q', 'c', 't', 's', 'n'}
```

For more set features, see the [Python `set` documentation.][python set docs]

***

## Conclusion

Sets are not the most common data structure in Python, but they can be useful
when you need to create and compare unique collections of data. Remember that
sets are **unique, unordered, and mutable**.

## Resources

- [Python `set` - Python][python set docs]
- [Python Sets - W3Schools](https://www.w3schools.com/python/python_sets.asp)
- [Sets in Python - Real Python](https://realpython.com/python-sets/)

[python set docs]: https://docs.python.org/3/library/stdtypes.html#set
