## Python Functions Part 1

Functions are smaller, reusable chunks of code that we write in order to keep our application maintanable and more manageable.

###### Example 1:

```python
def book():
    print("Thriller")


book()  # Thriller
```

###### Example 2:

```python
success = True


def operation():
    if success:
        print("Yay!!!")


operation()    # Yay!!!
```

###### Example 3:

```python
def sum():
    for number in range(4, 34, 4):
        print(number)


sum()
"""
4
8
12
16
20
24
28
32
"""
```

### Functions Parameters & Arguments

The whole idea behind using functions is the reusablity of them. When we define a function we provide like a set of parentheses, but we have not provided anything inside those parantheses.

###### Example 1:

```python
def arithmetic_operation(x, y):
    print(f"{x} * {y} = {x * y}")
    print(f"{x} / {y} = {x / y}")
    print(f"{x} + {y} = {x + y}")
    print(f"{x} - {y} = {x - y}")


arithmetic_operation(20, 5)
arithmetic_operation(112, 32)
arithmetic_operation(301, 201)
```

###### Example 2:

```python
def legal_age(name, age, allowed_age):
    if age >= allowed_age:
        print(f"{name} is allowed to drive.")
    else:
        print(f"{name} is not allowed to drive.")


legal_age("Dany", 21, 18)        # Danny is allowed to drive.
legal_age("John", 17, 18)        # John is not allowed to drive.
legal_age("Alex", 19, 21)        # Alex is not allowed to drive.
```

### Function Types

There are two type of functions:

1. Functions that do perform a task.

2. Functions that calculate and return value.

###### Example 1:

```python
def facebook(name, status):
    return f"{name} is {status}"


user1_status = facebook("William", "offline")
user2_status = facebook("Tiffany", "online")
print(user1_status)
print(user1_status)
```

###### Example 2 (Keyword argument):

When you're working with a large function and you lose track of which argument belongs to which parameter, then you can use keyword arguments to denote inside your function call thaht which argument belong to which parameter.

```python
def multiply(number, by):
    return number * by


# result = multiply(15, 4)
# print(result)

# print(multiply(1.2, 1.3))


result = multiply(number=3, by=15)
print(result)
```

### Required & Optional Parameters

By default, arguments for all of the function parameters are **required**. But we can have **optional** parameters ad well  

Optional parameters have **default** argumnets.

Optional parameter must be the **last** parameters in the function defenition, and if you provide any required parameter after an optional parameter, you will end up with a **<span style="color: red">Syntax ERROR</span>**. 

###### Example 1:

```python
def working_condition(device, status="working"):
    return f"The {device} is {status}"


print(working_condition("Drill Press"))
# The Drill Press is working.

print(working_condition("Welding Machine", "out of order"))
# The Welding Machine is out of order
```

##### Example 2:

```python
# def subtract(x, y=15, z):
#    return x- y - z
# >>> ERROR: non-default argument follows default argumnet

def subtract(x, z, y=15):
    return x - y - z


print(subtract(20, 5))
print(subtract(20, 5, 10))
```

### Non-Keyword Arguments (\*args)

**?** What if you don't know how many parameters you have?

**?** What if the number of arguments that you provide are more than the number of parameters?

###### Example 1 (with ERROR):

```python
def sum(x, y):
    return x + y


print(sum(89, 98, 23, 56, 45))
# >>> ERROR: sum() takes 2 positional arguments but 5 were given
```

**Use Case:** Non-Arguments are used whenever we do not know how many arguments we need to pass.

###### Example 2:

```python
def num(*numbers):        # numbers: this take in a tuple
    return numbers


print(num(10, 21, 65, 112, 555, 666))
```

###### Example 3:

```python
def subtract(*nums):
    number = 100
    for x in nums:
        number = number - x
    return number


print(subtract(2, 3, 5, 25, -45, 111))
# -1
```

### Keyword Arguments (\*\*kwargs)

###### Example 1:

```python
def employee(**info):    # it is going to print a dictionary
    print(info)


employee(name="Clint", last_name="Johnson", age=34, skill_set="Python")
```

###### Example 2:

```python
def to_do(**to_do_status):
    return to_do_status


to_do_status_result = to_do(get_coffe="Done",
                            exercise="Pending", watch_tv="In Progress")

print(to_do_status_result)
```

### Scope

We have two types of variables:

1. Global variables

2. Local variables

###### Example 1 (with ERROR):

```python
def message(date):
    content = "something very cool has happend"


message("May 22, 2100")

print(date)     # NameError: name 'date' is not defined
print(content)  # NameError: name 'content' is not defined
```

 variables have short lifetime.

Python is a **garbage collected** language. It means whenever you're done with a variable, whenever the code is executed, this space in memory which is allocated to specific variable, is going to be released.

###### Example 2:

```python
content = "just do it"


def post(date):
    content = "i am on a trip"


post("Jan 1, 1970")
print("content")                # just do it
```

###### Example 3:

```python
dog_name = "Hachi"


def animal_names():
    global dog_name    # one the wrost things that you can do in python
    dog_name = "Georgie"


print(dog_name)        # Hachi
animal_names()
print(dog_name)        # Georgie
```

### Debuging Code

```python
def subtract(*nums):
    target_num = 1000

    for x in nums:
        target_num -= x
        return target_num
#    return target_num


print(subtract(50, 32, 91, 24, 7, 123, 306, 68))
# 299 --> When return belongs to function
# 950 --> When returne belongs to for loop

# set break point in line which include 'print' (last line)
# then see how function and loop work
# then change the location of return and run debug 
# again in your IDE. 
```
