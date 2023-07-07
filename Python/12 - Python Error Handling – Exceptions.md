## 12 - Python Error Handling – Exceptions

### What are Exeptions?

Errors and exceptions are raised whenever the Python interpreter encounter errors.

There are two types of errors:

* Syntax Errors

* Logical Errors (Exceptions)

[Built-in Exceptions](https://docs.python.org/3/library/exceptions.html)

###### Example 1: SyntaxError

```python
if 2 > 1    # SyntaxError: expected ':'
if 2 > 1:   # IndentationError: expected an indented block after ...
```

###### Example 2: Python Logical Errors

```python
1 / 0        # ZeroDivisionError: division by zero
open("imaginary.txt")   # FileNotFoundError: [Errno 2] No such file or..
```

###### Example 3: Exceptions

```python
nuumbers = [1, 2]
print(numbers[3])    # IndexError: list index out of range
```

###### Example 4: Exceptions

```python
age = int(input("age: "))
# Input: a

# ValueError: invalid literal for int() with base 10: 'a'
```

### Exception Handling

`try` : The part of profram that we suspect that might throw an error.

`except`: The part of program that actually handles that error.

NOTE: Whenever you create a block, the block is denoted by indentation and you must do something in that block, if you don't you're going to get an error. The `pass` keyword in Python shows that we don't want to do something with that block.

###### Example 1:

```python
try:
    age = int(input("Age: "))
except:
    print("Please enter a valid age")
```

###### Example 2:

```python
try:
    age = int(input("Age: "))
except ValueError:        # if ValueError raise
    print("Please enter a valid age")
else:
    print("No Errors Here!")
```

###### Example 3:

```python
try:
    age = int(input("Age: "))
except ValueError as exp_error:     
    print("Please enter a valid age")
    print(exp_error)              
    print(type(exp_error))        # <class 'ValueError'>
else:
    print("No Errors Here!")
```

###### Example 4:

```python
import sys


random_list = ["a", 0, 2]

for entry in random_list:
    try:
        print("The entry is: ", entry)
        r = 1 / int(entry)
        break
    except:
        print("oops!", sys.exc_info()[0], "occured.")
        # exc_info return a tuple of data

    print("Next entry.")
    print()

print()
print("The reciprocal of", entry, "is", r)


'''
The entry is:  a
oops! <class 'ValueError'> occured.
Next entry.

The entry is:  0
oops! <class 'ZeroDivisionError'> occured.
Next entry.

The entry is:  2

The reciprocal of 2 is 0.5
'''
```

###### Example 5:

```python
import sys


random_list = ["a", 0, 2]

for entry in random_list:
    try:
        print("The entry is: ", entry)
        r = 1 / int(entry)
        break
    except Exception as exp_error:    
        # Exception : Common base class for all non-exist exceptions 
        # Exception is the same as __class__
        print("oops!", exp_error.__class__, "occured.")
        print("Next entry.")
        print()

print()
print("The reciprocal of", entry, "is", r)


# the output is like the Example 4's output
```

###### Example 6: get a ZeroDivisionError

```python
try:
    age = int(input("Age: "))
    x = 10 / age
except ValueError:
    print("please enter a valid age")
else:
    print("No Errors Here!")

'''
Input --> 0

Traceback (most recent call last):
  File "./app.py", line 3, in <module>
    x = 10 / age
        ~~~^~~~~
ZeroDivisionError: division by zero
'''
```

###### Example 7: Resolving a ZeroDivisionError

```python
try:
    age = int(input("Age: "))
    x = 10 / age
except ValueError:
    print("please enter a valid age")
except ZeroDivisionError:
    # print("age can not be zero")
    print("please enter a valid age")
else:
    print("No Errors Here!")
```

###### Example 8: Creating a tuple

```python
try:
    age = int(input("Age: "))
    x = 10 / age
except (ValueError, ZeroDivisionError):
    print("please enter a valid age")
else:
    print("No Errors Here!")
```

Whenever we open a file or we want to work with a database of some kind of Python, we need to close it after we're done with the operations that we want to perform on that specific file and we want to close it because we want to release that resource, Otherwise another process or program may not  be able to open that file.

###### Example 9:

```python
# Create a somefile.txt near app.py


try:
    note = open("somefile.txt")
    age = int(input("Age: "))
    x = 10 / age
    # note.close()
except (ValueError, ZeroDivisionError):
    print("please enter a valid age")
    # note.close()
else:
    print("No Exceptions here")
    # note.close()
finally:
     note.close()
```

### The with Statement

In Python, **with statement** is used in exception handling to make the code cleaner and much more readable. It simplifies the management of common resources like file streams. Observe the following code example on how the use of with statement makes code cleaner.

The `with` statement is a replacement for commonly used `try/finally` error-handling statements. More importantly, it ensures closing resources right after processing them

- When you call the `with` statement, the `__enter__()` method is invoked.
- When you exit the scope of the `with` block, the `__exit__()` function is called.

###### Example 1: opening a single file

```python
# Create a somefile.txt near app.py


try:
    with open("somefile.txt") as note:
        print("note opened")

    age = int(input("Age: "))
    x = 10 / age
except (ValueError, ZeroDivisionError):
    print("please enter a valid age")
except FileNotFoundError:
    print("oops! file not found")
else:
    print("No Exceptions here")
```

###### Example 2: opening a multiple file

```python
# Create someFile.txt and anotherFile.txt near app.py


try:
    with open("someFile.txt") as note, open("anotherFile.txt") \
            as my_note:
        print("note opened")

    age = int(input("Age: "))
    x = 10 / age
except (ValueError, ZeroDivisionError):
    print("please enter a valid age")
except FileNotFoundError:
    print("oops! file not found")
else:
    print("No Exceptions here")
```

### Raising Exceptions

###### Example 1: raising an exception

```python
def calculate_age(age):
    if age <= 0:
        raise ValueError("age can not be zero or less")

    return age / 10


calculate_age(0)
# ValueError: age can not be zero or less
```

###### Example 2: raising an exception and handling it

```python
def calculate_age(age):
    if age <= 0:
        raise ValueError("age can not be zero or less")

    return age / 10


try:
    calculate_age(0)
except ValueError as error:
    print(error)


# age can not be zero or less
```

### The Bad Side of Raising Exceptions

 When you're working with small applications, it's OK to raise exceptions. It's not going to be a big deal, but if you're working with very huge e-commerce or social media applications like very large applications, in thousands lines of code if you raise exception, then it is going to cost you in performance. 

###### Example 1:

```python
from timeit import timeit


test_run1 = """

def calculate_age(age):
    if age <= 0:
        raise ValueError("age can not be zero or less")

    return age / 10


try:
    calculate_age(0)
except ValueError as error:
    pass

"""

print("Test 1:", timeit(test_run1, number=10000))

# 10 times of running code
# Test 1: 0.004410299996379763
# Test 1: 0.003956200001994148
# Test 1: 0.004017200000816956
# Test 1: 0.003975700004957616
# Test 1: 0.004487599995627534
# Test 1: 0.004557500004011672
# Test 1: 0.0042579000000841916
# Test 1: 0.004183600001852028
# Test 1: 0.0042461999983061105
# Test 1: 0.003985499999544118
```

###### Example 2:

```python
from timeit import timeit


test_run2 = """

def calculate_age(age):
    if age <= 0:
        return None

result = calculate_age(0)

if result == None:
    pass
"""

print("Test 2:", timeit(test_run2, number=10000))

# 10 times of running code
# Test 2: 0.0011404000033508055
# Test 2: 0.0010694999946281314
# Test 2: 0.0010610000026645139
# Test 2: 0.001237800002854783
# Test 2: 0.001061999995727092
# Test 2: 0.001110600001993589
# Test 2: 0.0011393000022508204
# Test 2: 0.0011147000041091815
# Test 2: 0.0011130999992019497
# Test 2: 0.0011378999988664873
```
