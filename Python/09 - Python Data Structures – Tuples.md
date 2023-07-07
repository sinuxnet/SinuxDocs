## 09 - Python Data Structures – Tuples

### An Introduction to Tuples

* it's a data type in python

* similar to a list

* we can not change the elements of a tuple

###### Example 1:

```python
num = (1, 2, 3)
print(num)            # (1, 2, 3)
print(type(num))      # <class 'tuple'>
```

###### Example 2:

```python
mixed = (1, "Bear", True)
print(mixed)        # (1, 'Bear', True)
```

###### Example 3:

```python
mixed = (
    {"Name": "Saitama", "Job": "Heo"},
    [4, 5, 12],
    (1.23, 2.13, 3.12),
    True,
    "Asia
"
)

print(mixed)            
#({'Name': 'Saitama', 'Job': 'Heo'}, [4, 5, 12], 
# (1.23, 2.13, 3.12), True, 'Asia')
```

### Tuple Packing & Unpacking

**Tuple packing** refers to assigning multiple values into a tuple.

**Tuple unpacking** refers to assigning a tuple into multiple variables.

###### Example 1:

```python
to_do = "buy coffe", "read a book", "finish homework"

print(to_do)
# ('buy coffe', 'read a book', 'finish homework')

print(type(to_do))   
# <class 'tuple'>
```

###### Example 2:

```python
to_do = "buy coffe", "read a book", "finish homework"

to_do1, to_do2, to_do3 = to_do

print(to_do1)
print(to_do2)
print(to_do3)
```

###### Example 3:

```python
name = ("Tommy")
print(name)            # Tommy
print(type(name))      # <class 'str'>

name = ("Tommy",)
print(name)            # ('Tommy',)
print(type(name))      # <class 'tuple'>
```

### Access Tuple Items

###### Example1:

```python
mixed = (False, 3.14159, "Python", ["Web", "45"], 45)

print(mixed[0])    # False
print(mixed[1])    # 3.14159

print(mixed[5])    
# IndexError: tuple index out of range

print(mixed["a"])  
# TypeError: tuple indices must be integers or slices, not str
```

###### Example2:

```python
mixed = (False, 3.14159, "Python", ["Web", "45"], 45)

print(mixed[-1])           # 45
print(mixed[-2])           # ['Web', '45']
print(mixed[-4])           # 3.14159
print(mixed[-5])           # False

print(mixed[-6])           
# IndexError: tuple index out of range
```

###### Example3:

```python
mixed = (False, 3.14159, "Python", ["Web", "45"], 45)


print(mixed[0:2])   # (False, 3.14159)
print(mixed[2:4])   # ('Python', ['Web', '45'])
print(mixed[:4])    # (False, 3.14159, 'Python', ['Web', '45'])
print(mixed[:3])    # (False, 3.14159, 'Python')

print(mixed[:-1])   # (False, 3.14159, 'Python', ['Web', '45'])
print(mixed[:-3])   # (False, 3.14159)
```

### Changing Tuples

Unlike lists, tuples are immutable.

But if an element of tuple is  mutable(for example a list), we can change the element of it.

Note: Reassignment of a tuple is allowed in python.

###### Example1:

```python
numbers = (4, 2, 3, [5, 6, 7, 8, 9])

numbers[1] = 10
# TypeError: 'tuple' object does not support item assignment

print(numbers)            # (4, 2, 3, [5, 6, 7, 8, 9])
numbers[3][0] = 10
print(numbers)            # (4, 2, 3, [10, 6, 7, 8, 9])

numbers[3].insert(4, "BagherZadeh")
print(numbers[3])        # [10, 6, 7, 8, 'BagherZadeh', 9]

print(numbers)           # (4, 2, 3, [10, 6, 7, 8, 'BagherZadeh', 9])
```

###### Example2: repeating tuple

```python
print(("Movie",)*5)
# ('Movie', 'Movie', 'Movie', 'Movie', 'Movie')
```

###### Example3: tuple concatenation

```python
numbers = (222, 333, 444)
letters = ("p", "y", "t", "h", "o", "n")

mixed = numbers + letters
print(mixed)
# (222, 333, 444, 'p', 'y', 't', 'h', 'o', 'n')
```

###### Example4: deleting a tuple entirely

```python
letters = ("p", "y", "t", "h", "o", "n")
del letters

print(letters)
# NameError: name 'letters' is not defined
```

### Tuple Methods

   There are two methods available for tuples:

* count()

* index()

###### Example 1: count() & index()

```python
colors = ("green", "blue", "violet", "lawngreen", "green")

print(colors.count("green"))
# 2
print(colors.count("red"))
# 0
print(colors.index("blue"))
# 1
print(colors.index("violet"))
# 2
print(colors.index("green"))
# 0
print(colors.index("red"))
# ValueError: tuple.index(x): x not in tuple
```

### Tuple Operations

###### Example 1: Tuple Membership Test

```python
colors = ("green", "blue", "violet", "lawngreen", "green")

print("green" in colors)
# True
print("red" in colors)
# False
```

###### Example 2: Iterating Over Tuples

```python
colors = ("green", "blue", "violet", "lawngreen", "green")

for color in colors:
    print("I like the color", color)
# I like the color green
# I like the color blue
# I like the color violet
# I like the color lawngreen
# I like the color green
```

advantages of tuple over lists:

1. Tuples are generally used for different data types and lists for similar data types.

2. Iterating over tuples is faster. (due to immutability)

3. 

Note: Dictionary keys can consisit immutable data types.
