## 17 - Advanced Python – Decorators

### Decorators Prerequisites

Before we learn about decorators, we need to understand a few important concepts related to Python functions. Also, remember that everything in Python is an object, even functions are objects.

In Python, functions are **first class objects** which means that functions in Python can be used or passed as arguments.

- A function is an instance of the Object type.
- You can store the function in a variable.
- You can pass the function as a parameter to another function.
- You can return the function from a function.
- You can store them in data structures such as hash tables, lists, …

###### Example 1: functions with different names

In Python, we can also **return a function as a return value.**

```python
def name1(name):
    print(name)


name1("John")       # John

name2 = name1
name2("Jane")       # Jane

print(id(name1("John")))        # John      140717840690376
print(id(name2("Jane")))        # Jane      140717840690376
```

**Functions are objects:** Python functions are first class objects. In the example above, we are assigning function to a variable. This assignment doesn’t call the function. It takes the function object referenced by `name1` and creates a second name pointing to it, yell.

###### Example 2: higher order functions

We can pass a function as an argument to another function in Python.

```python
def increment(x):
    return x + 1


def decrement(x):
    return x - 1


def operation(result, x):
    output = result(x)

    return output


number_inc = operation(increment, 50)
number_dec = operation(decrement, 50)


print(number_inc)
print(number_dec)
```

###### Example 3:

```python
def add(x, y):
    return x + y

def calculate(func, x, y):
    return func(x, y)

result = calculate(add, 4, 6)
print(result)  # 10
```

**Functions can be passed as arguments to other functions:** Because functions are objects we can pass them as arguments to other functions. Functions that can accept other functions as arguments are also called higher-order functions.

**Higher Order Functions**

A function is called **Higher Order Function** if it contains other functions as a parameter or returns a function as an output i.e, the functions that operate with another function are known as Higher order Functions. It is worth knowing that this higher order function is applicable for functions and methods as well that takes functions as a parameter or returns a function as a result.

###### Example 4: A function returning another function (Nested function)

We can include one function inside another, known as a nested function.

```python
def operation():

    def increment():
        print("The number has been added")

    return increment


number_inc = operation()
number_inc()

operation()()
```

###### Example 5:

```python
def outer(x):
    def inner(y):
        return x + y
    return inner


add_five = outer(5)
result = add_five(6)
print(result)       # 11
```

**Functions can return another function:** Because functions are objects we can return a function from another function. In the below example, the create_adder function returns adder function.

### Introduction to Decorators

**Decorators** are a very powerful and useful tool in Python since it allows programmers to modify the behaviour of a function or class. Decorators allow us to wrap another function in order to extend the behaviour of the wrapped function, without permanently modifying it.

A decorator is a design pattern that allows you to modify the functionality of a function by wrapping it in another function.

The outer function is called the decorator, which takes the original function as an argument and returns a modified version of it.

In fact, any object which implements the special `__call__()` method is termed callable. So, in the most basic sense, a decorator is a callable that returns a callable.

![](D:\OneDrive\z%20-%20My%20Docs\md%20docs\Python%20Bootcamp%202022%20-%20Muslim%20Helalee\images\qxf2-gun-decorator1.jpg)

###### Example 1:

```python
# decorator
def operation(func):

    def increment():
        print("before the func")

        # the execution of decrement function
        func()

        print("after the func")

    return increment


# decorated
def decrement():
    print("The number has been decremented")


# decrement()
# operation(decrement)


decorated_function = operation(decrement)
decorated_function()
# before the func
# The number has been decremented
# after the func
```

###### Example 2: the syntactic sugar of a decorator

Instead, Python allows you to **use decorators in a simpler way with the `@` symbol**, sometimes called the [“pie” syntax](https://www.python.org/dev/peps/pep-0318/#background).

```python
def operation(func):

    def increment():
        print("before the func")

        # the execution of decrement function
        func()

        print("after the func")

    return increment


@operation        # @operation ==>> decrement = operation(decrement)
def decrement():
    print("The number has been decremented")


decrement()
# before the func
# The number has been decremented
# after the func
```

### Decorate Functions with Parameter

###### Example 1:

```python
# def operation(x, y):
#     return x / y


# print(operation(10, 20))        # 0.5
# print(operation(101, 32))       # 3.15625
# print(operation(54, 0))         # ZeroDivisionError: division by zero


# use a decorator
def operation(func):

    def inner(x, y):
        print(f"{x} / {y} =")

        if y == 0:
            print("cannot divided by zero")
            return

        return func(x, y)

    return inner


@operation
def divide(x, y):
    print(x / y)


divide(2, 5)
divide(20, 5)
divide(78, 0)

# 2 / 5 =
# 0.4
# 20 / 5 =
# 4.0
# 78 / 0 =
# cannot divided by zero
```

### Arguments & Keyword Arguments

###### Example 1: *args*

```python
def multiply(func):
    def digits(*args):
        func(*args)

    return digits


@multiply
def operation(x, y, z):
    print(x * y * z)

# operation()
# TypeError: operation() missing
#   3 required positional arguments: 'x', 'y', and 'z'


operation(10, 20, 30)
# 6000
```

###### Example 2: *args

```python
def do_arithmetic(func):
    def number(*numbers):
        func(*numbers)

    return number


@do_arithmetic
def operation(x, y, z, a, b, c):
    print((a / b) + z + (x + y) / c)


operation(100, 200, 300, 400, 500, 600)        # 301.3
```

###### Example 3: **kwargs

```python
def do_arithmetic(func):
    def number(**kwargs):
        func(**kwargs)

    return number


@do_arithmetic
def operation(x, y, z, a, b, c, m, n, o):
    print(((a / b) * m + z * n + (x / o + y) / c + m * n + o) / o - n)


operation(x=100, y=200, z=300, a=400, b=500, c=600, m=700, n=800, o=900)
# 90.51148168724274
```

###### Example 4:

```python
def hello_decorator(func):
    def inner1(*args, **kwargs):

        print("before Execution")

        # getting the returned value
        returned_value = func(*args, **kwargs)
        print("after Execution")

        # returning the value to the original frame
        return returned_value

    return inner1


# adding decorator to the function
@hello_decorator
def sum_two_numbers(a, b):
    print("Inside the function")
    return a + b


a, b = 1, 2

# getting the value through return of the function
print("Sum =", sum_two_numbers(a, b))


# before Execution
# Inside the function
# after Execution
# Sum = 3
```

### Chaining Decorators

In simpler terms chaining decorators means decorating a function with multiple decorators.

Python allows us to implement more than one decorator to a function. It makes decorators useful for reusable building blocks as it accumulates several effects together. It is also known as nested decorators in Python.

###### Example 1:

```python
def info_name(func):
    def full_name(*args):
        func(*args)

    return full_name


def info_last_name(func):
    def full_name(*args):
        func(*args)

    return full_name


@info_name
@info_last_name
def info(name, lastname):
    print(f"My full name is {name} {lastname}")


info("Arthur", "Shelby")
# My full name is Arthur Shelby
```

###### Example 2:

```python
def decor1(func):
    def inner():
        x = func()
        return x * x
    return inner


def decor2(func):
    def inner():
        x = func()
        return 2 * x
    return inner


@decor1
@decor2
def num():
    return 10


@decor2
@decor1
def num2():
    return 10


print(num())    # 400   decor1(decor2(num))
print(num2())   # 200   decor2(decor1(num2))
```

![](D:\OneDrive\z%20-%20My%20Docs\md%20docs\Python%20Bootcamp%202022%20-%20Muslim%20Helalee\images\Screenshot%202023-03-17%20193248.png)

###### Example 3:

```python
def decor1(func):
    def wrap():
        print("************")
        func()
        print("************")

    return wrap


def decor2(func):
    def wrap():
        print("@@@@@@@@@@@@")
        func()
        print("@@@@@@@@@@@@")
    return wrap


@decor1
@decor2
def sayhellogfg():
    print("Hello")


sayhellogfg()

"""
************
@@@@@@@@@@@@
Hello
@@@@@@@@@@@@
************
"""
```


