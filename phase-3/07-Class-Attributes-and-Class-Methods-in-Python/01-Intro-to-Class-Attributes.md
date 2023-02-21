# Intro to Class Attributes and Class Methods

## Learning Goals

- Use class attributes and methods to write durable and powerful code.
- Accomplish complex programming tasks using knowledge from previous modules.

***

## Key Vocab

- **Attribute**: variables that belong to an object.
- **Constant**: variable whose value cannot be changed.
- **Instance**: one specific working copy of a class. It is created when a
  class's `__init__` method is called.
- **Class**: a bundle of data and functionality. Can be copied and modified to
  accomplish a wide variety of programming tasks.
- **Static**: an attribute or method that cannot manipulate the class or
  instance it belongs to.
- **Exception**: an error that occurs during the execution of a program.
  Exceptions can be anticipated and handled without disrupting the execution of
  the program.

***

## Introduction

Classes are like the blueprint from which individual objects are created. When
you make use of classes you can reuse code rather than writing similar code over
and over again. This makes code more readable, and follows the principle of
_"DRY"_ (**Don't Repeat Yourself**).

So far, we've primarily created **instance methods** and **instance attributes**
for our individual objects to use. However, we can also create **class methods**
and **class attributes**. Class attributes are used to store values related to a
class in general rather than a particular instance. Class methods are similarly
used for implementing behavior that is related to a class in general rather than
an instance.

In the next several lessons we'll be taking a look at:

- How to recognize a class variable.
- Utilizing class attributes.
- Using class attributes to keep track of data pertaining to a class.
- Using instance, class, and static methods.
- The concept of remembrance in object-oriented programming.

At a glance, you might assume class attributes work like instance attributes;
however, this is not the case. In this section, we'll distinguish the difference
between class methods and attributes and when to use them.

***

## Resources

- [Python Documentation](https://docs.python.org/3/)
- [Classes - Python](https://docs.python.org/3/tutorial/classes.html)
- [Python Class Attributes: An Overly Thorough Guide - Toptal](https://www.toptal.com/python/python-class-attributes-an-overly-thorough-guide)
- [Python's Instance, Class, and Static Methods Demystified - Real Python](https://realpython.com/instance-class-and-static-methods-demystified/)
