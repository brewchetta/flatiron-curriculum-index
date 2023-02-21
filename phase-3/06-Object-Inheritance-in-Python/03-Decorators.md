# Decorators

## Learning Goals

- Reduce repeated code and enhance objects using inheritance.
  - Use decorators to add functionality to our functions.
- Accomplish complex programming tasks using knowledge from previous modules.

***

## Key Vocab

- **Inheritance**: a tool that allows us to recycle code by creating a class
that "inherits" the attributes and methods of a parent class.
- **Composition**: a tool that enables you to recycle code by adding objects to
other objects. Rather than building on a base class as in inheritance,
composition leverages the attributes and methods of an instance of another class.
- **Subclass**: a class that inherits from another class. Colloquially called
a "child" class.
- **Superclass**: a class that is inherited by another class. Colloquially
called a "parent" class.
- **Child**: another name for a subclass.
- **Parent**: another name for a superclass.
- **`super()`**: a built-in Python function that allows us to manipulate the
attributes and methods of a superclass from the body of its subclass.
- **Decorator**: syntax that allows us to add functionality to an object
without modifying its structure.

***

## Introduction

In this module, we have explored a number of ways to live by the **D**on't
**R**epeat **Y**ourself principle of object-oriented programming. Inheritance
allows us to create classes with functionality from parent classes, and the
`super()` function allows us to extend that functionality when we need to
without rewriting any code.

**Decorators** provide us yet another way to write DRY code through providing
extra functionality to _functions._

***

## Functions Are First Class Objects

While we primarily think of functions as procedures, it's important to remember
that in Python, they are objects too. Just like any other object, they can be
saved as variables, passed as arguments to other functions, and returned by
functions:

```py
def hello(name):
    return "Hello " + name

print(hello("Guido"))
# Hello Guido

greeting = hello
print(greeting("Guido"))
# Hello Guido

def salutation(func):
    return func("Guido")

print(salutation(greeting))
# Hello Guido.
```

Furthermore, we can define functions inside of other functions, just as we
could any other object. We call these **inner functions**:

```py
def hello(name):
    print("Hello from the hello() function.")

    def greet():
        print("Greetings from the greet() function.")

    return greet
```

What do you think we'll see if we `print()` the result of our `hello()`
function?

```py
hello("Guido")
# Hello from the hello() function.
# <function hello.<locals>.greet at 0x103287b80>
```

By returning `greet()` without parentheses, `hello()` is returning the function
itself so that we can use it later on. When we're ready to invoke it later on,
we can do so with parentheses as we would with any other function:

```py
hello("Guido")()
# Hello from the hello() function.
# Greetings from the greet() function.
```

<details><summary>What would be the output of the code above if
<code>return greet</code> were left out?</summary>
<p>

<h3>Hello from the hello() function.</h3>

<p>While there's a <code>print()</code> statement inside of the
<code>greet()</code> function, it won't be interpreted if <code>greet()</code>
is not invoked.</p>

</p>
</details>
<br/>

***

## Writing Your First Decorator

To write your first **decorator**, you'll need to tie all of these concepts
together. You will need to write a function that...

1. Takes a function as an argument.
2. Has an inner function defined inside of it.
3. Returns the inner function.

Open up the Python shell and enter the following code:

```py
def decorator(func):
    def wrapper():
        print("I am the output that lets you know the function is about to be called.")
        func()
        print("I am the output that lets you know the function has been called.")
    return wrapper

def get_called():
    print("I am the function and I am being called.")
```

We've created a decorator and we've created a function to pass in. All that's
left to do is put it all together:

```py
get_called = decorator(get_called)
get_called()
# I am the output that lets you know the function is about to be called.
# I am the function and I am being called.
# I am the output that lets you know the function has been called.
```

Python allows us to perform the decoration step in a more decorative fashion
with the `@` symbol. This is also called _"pie syntax"_.

```py
@decorator
def get_called():
    print("I am the function and I am being called.")

get_called()
# I am the output that lets you know the function is about to be called.
# I am the function and I am being called.
# I am the output that lets you know the function has been called.
```

***

## When To Use Decorators

The primary function of decorators is reducing the amount of code that you need
to write in your applications. If you find yourself reusing a lot of the same
code in different functions, that's a great opportunity to use decorators. If
you're only doing something once or twice, decorators might be overkill.

Let's look at an example of when we _would_ want to use decorators.

```py
def sweep_floors(time):
    if 1100 < time < 2100:
        print("Sweeping the floors...")
    else:
        print("I'm off duty!")

def wash_dishes(time):
    if 1100 < time < 2100:
        print("Washing the dishes...")
    else:
        print("I'm off duty!")

def chop_vegetables(time):
    if 1100 < time < 2100:
        print("Chopping the vegetables...")
    else:
        print("I'm off duty!")
```

There's a pretty clear pattern here: our employees only work from 11 to 9!
Including code in every single function to check if anyone's working is not
ideal. Let's refactor this with a decorator:

```py
def check_working_hours(func):
    def wrapper(time):
        if 1100 < time < 2100:
            func(time)
        else:
            print("I'm off duty!")
    return wrapper

@check_working_hours
def sweep_floors(time):
    print("Sweeping the floors...")

@check_working_hours
def wash_dishes(time):
    print("Washing the dishes...")

@check_working_hours
def chop_vegetables(time):
    print("Chopping the vegetables...")

sweep_floors(800)
# I'm off duty!
wash_dishes(1000)
# I'm off duty!
chop_vegetables(1200)
# Chopping the vegetables...
```

<details><summary>What are the two options for invoking a decorator?</summary>
<p>

<h3>A <code>function_call()</code> or <code>@pie_syntax</code>.</h3>

</p>
</details>
<br/>

***

## Conclusion

Functions are first-class objects in Python. This means that they can be
passed as arguments to other functions, created inside of other functions
(as _inner functions_), and returned by other functions. Decorators leverage
these features to allow us to avoid repetitive code and are an important tool
in any Python programmer's toolbox.

***

## Resources

- [Python 3.8 Documentation](https://docs.python.org/3.8/)
- [Inheritance - Python](https://docs.python.org/3/tutorial/classes.html#inheritance)
- [Decorators in Python - GeeksforGeeks](https://www.geeksforgeeks.org/decorators-in-python/)
