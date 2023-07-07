## Python Variables – Data Types – Basic Grammar

Variables Stores data in memory.

```python
# *_*_*_*_*_*_*_ String
my_story = "A thousand splendid suns"
# *_*_*_*_*_*_*_ Number
my_grade = 85
# *_*_*_*_*_*_*_ Boolian
am_i_young = True 
```

### Variable name

1. Variable names must make sense

2. Python convention is to use lowercase letters

3. Python is snake case

4. Variables names must start with a letter or _ 

5. Following the pep8 standards

```python
movie_rating = 8.5
my_name = "Sina Alikhani"
# myName ---> camel case
user_info = "Online" # snake case
# 15street --> error 
```

### Data types

Every value in python has a data type.

Data types are bulding blocks of any programming language that you can work with.

| Data Types             | Class | Value                                    |
| ---------------------- | ----- | ---------------------------------------- |
| integers               | int   | 45                                       |
| floating point numbers | float | 4.5                                      |
| booleans               | bool  | True/False                               |
| strings                | str   | "Sina Alikhani"                          |
| list                   | list  | [1, 2, 3]                                |
| dictionary             | dict  | {"user_name": "awesome50, "user_id": 56} |
| tuple                  | tuple | (10, 20, 30)                             |
| set                    | set   | {"cat", 99}                              |

```python
# Integer
age = 23
print(type(age)) # <class 'int'>

# Floats
grade = 8.9
print(type(grade)) # <class 'floats'>

# Booleans
alarm = True
offline = False
print(type(alarm)) # <class 'bool'>
print(type(offline)) # <class 'bool'>

# Strings
movie_name = "The good, bad and ugly"
print(type(movie_name)) # <class 'str'>

# List
# Ordered
number = [1, 2, 3.2, 5.4]
mixed = [1, 2, 3.2, 5.4, True, "Sina Alikhani", [1, 2, 3]]
print(type(mixed)) # <class 'list'>

# Dictionary
# Unorderd, collection of key-value pairs {"key": "value"}
user_info = {"user_name": "awesome50", "use_id": 56}
print(type(user_info) # <class 'dict'>

# Tuple
# Ordered --> immutable 
# usually faster than list, write protected data
mixed_tuple = (1, 2, 3.2, 5.4, True, "Sina Alikhani", [1, 2, 3])
print(type(mixed_tuple)) # <class 'tuple'>

# Set
# Unordered
mixed_set = {1, 2, 3.2, 5.4, "Python", "Sina Alikhani"}
print(type(mixed_set)) # <class 'set'>
```

### String Methods

1. len()

2. [x] Notation

3. [x:y] Notation

4. Concatenation >>> formatted strings

5. upper()

6. lower()

7. title()

8. strip()

9. find()

10. replace()

11. in operator

12. not operator

```python
address = "Iran_Tehran"
# 1- len()
print(len(address))        # >>> 11

# 2- [x] Notation
print(address[0])          # >>> I
print(address[1])          # >>> r
print(address[-1])         # >>> n
print(address[-4])         # >>> h

# 3- [x:y] Notation
print(address[0:4])        # >>> Iran
print(address[-7:-1])      # >>> _Tehra
print(address[0:])         # >>> Iran_Tehran
print(address[:9])         # >>> Iran_Tehr
print(address[:])          # >>> Iran_Tehran

# 4- Concatenation >>> formatted strings
country = "USA"
city = "NYC"
full_address = city + ", " + country
full_address =  f"{city},{country}" #formatted string
print(full_address)        # >>> NYC, USA

# 5- upper()
print(address.upper())     # >>> IRAN_TEHRAN

# 6- lower()
print(address.lower())     # >>> iran_tehran

# 7- title()
print(full_address.title()) # >>> Nyc, Usa

# 8- strip()
job = "         Programmer    "
print(job)                 # >>>         Programmer    
print(job.strip())         # >>> Programmer
print(job.lstrip())        # >>> Programmer    
print(job.rstrip())        # >>>        Programmer

# 9- find()
print(address.find("n"))    # >>> 3
print(address.find("i"))    # >>> -1
print(address.find("I"))    # >>> 0

# 10- replace()
print(address.replace("r", "t"))    # >>> Itan_Tehtan
print(address.replace("n", "q"))    # >>> Iraq_Tehraq

# 11- in operator
print("an" in address)       # >>> True
print("en" in address)       # >>> False

# 12- not operator
print("an" not in address)   # >>> False
print("en" not in address)   # >>> True 
```

### None Special

None is special data type, it is the absence of a value.

The use case of None is when there is a lack of info.   

```python
# The absence of a value
print(None)       # None
print(type(None)) # <class 'NoneType'>
```

### Escape Sequences

1. \\'

2. \"

3. \\\

4. \n

```python
#story_desc = "It's a touching story"
story_desc = 'It\'s a touching story'
print(story_desc)
```

### Numbers Operation

1. Arithimetic Operation

2. Augmented Assignment Operations

```python
# Arithmetic Operation
print(23 + 12)        # 35
print(50 - 10)        # 40
print(50 * 10)        # 500
print(50 / 10)        # 5.0
print(53 // 10)       # 5
print(53 % 10)        # 3
print(2 ** 5)         # 32 
```

```python
# Augmented Assignment Operations
number = 10
# number = number + 5
number += 5
print(number)        # 15
number *=2
print(number)        # 30
number /= 5
print(number)        # 6.0  
```

### Number Methods

1. round()

2. abs()

3. methods in math module

[Math Module Documentation](https://docs.python.org/3/library/math.html)

```python
import math

# 1- round()
print(round(3.1245))        # 3
print(round(110.2356))      # 110

# 2- abs() 
print(abs(-1.45))           # 1.45
print(abs(+1.45))           # 1.45

# 3- math module
print(math.sin(180))
print(math.cos(0))
print(math.ceil(1.4))       # 2
print(math.ceil(2.03))      # 3
```

### Type Conversion

Convert one data type to another.

* **False Values:** zero, empty string & non objective

* **True Values:** All other values

```python
number = input("number: ")        # take input from user
print(type(number))       # <class 'str'>

y = int(number) + 202
print(type(y))            # <class 'int'>

# Falsy Vlues
print(bool(0))             # False
print(bool(""))            # False
print(bool(None))          # False

# True Values
print(bool(1))             # True
print(bool(" "))           # True
print(bool("False"))       # True
```

### Namespace

**Name:** a name also called an identifier is simply  a name given to objects.  A name is a way to access the underlaying object. All things in python is object.(even functions)

```python
number = 1001
# location of an object in memory
print(id(1001))            # 2358770899312
print(id(number))          # 2358770899312
# both store in same place
# number is a refrence to object
```

```python
a = 2
print("a: ", id(a))            # a: 140721591411528

a = a + 1
print("a1: ", id(a))           # a1:  140721591411560        
print("Three:", id(3))         # Three:  140721591411560
b = 2
print("b: ", id(b))            # b: 140721591411528
print("Two:", id(2))           # Two: 140721591411528
```

<img src="file:///D:/OneDrive/Desktop/Python/Python%20Variables%20–%20Data%20Types%20–%20Basic%20Grammar/Memory_Diagram.jpg" title="" alt="" data-align="center">

**namespace:** is basically a collection of names.

**scope:** is a portion of the program from where a namespace can be accessed directly without any prefix.

<img src="file:///D:/OneDrive/Desktop/Python/Python%20Variables%20–%20Data%20Types%20–%20Basic%20Grammar/nested_namespace.jpg" title="" alt="" data-align="center">

```python
def outer():
    outer_number = 100
    print(id(outer_number))                        # 140721591414664

    # print("Global number: ", global_number)        # 300

    global global_number
    global_number = 101 
    print("Global number: ", global_number)          # 101   

    def inner():
        inner_number = 200
        inner_number = "Jack"
        print("Inner number: ", inner_number)      # Inner number: Jack 

        # print(id(outer_number))                    # Outer number: 100
        # print("Outer number: ", outer_number)      # 140721591414664

        outer_number = 500
        print(id(outer_number))                    # 2422790732592
        print("Outer number: ", outer_number)      # Outer number:  500

    inner()

global_number = 300
print(global_number)        # 300

outer()
print(global_number)        # 101
```

 If the variable are local to a namespace, you **<span style="color: green">can access</span>** them and you **<span style="color: green">can modify</span>** them, if a variable is not local to a namespace, you **<span style="color: green">can access</span>** them but you **<span style="color: red">can not modify</span>** them.

**Note:** Try to never use `global` in python.

### Input & Output

```python
# Output
print("Hello from python")
print(101)
print(True)
print([1, 2, 3])
print({"name": "sina"})

first_name = "Sina"
last_name = "Alikhani"

print("My first name is {} and my last name is {}, \
so my full name is {} {}".format(first_name, last_name, first_name, \
last_name)
```

```python
num1 = input("num1: ")
print(type(num1))            # <class 'str'>

num2 = int(input("num2: "))
print(type(num2))            # <class 'int'>
```
