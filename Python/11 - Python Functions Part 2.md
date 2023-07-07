## 11 - Python Functions Part 2

## Filter Function

The filter() method filters the given sequence with the help of a function that tests each element in the sequence to be true or not and returns an iterator that is already filtered.

###### Example 1:

```python
letters = ['a', 'b', 'd', 'e', 'i', 'j', 'o']


# Return True if input is vowel letter
def filter_vowels(Letter):
    vowels = ['a', 'e', 'i', 'o', 'u']

    if (Letter in vowels):
        return True
    else:
        return False


filtered_vowels = filter(filter_vowels, letters)
print(filtered_vowels)
# <filter object at 0x0000020A2329E350>

print(type(filtered_vowels))
# <class 'filter'>


print("The filtered vowels are: ")
for vowel in filtered_vowels:
    print(vowel)


"""
a
e
i
o
"""
```

If function is None, return the items that are true. 

**False Values:**  Zero, empty string and _None_.

###### Example 2:

```python
random_list = [1, 0, "a", False, True, "0", None]


filtered_list = filter(None, random_list)

print("Truthy values are:")

for value in filtered_list:
    print(value)

"""
1
a
True
0
"""
```

### Anonymous Or Lambda Function

**Python Lambda Functions** are anonymous function means that the function is without a name.

As we already know that the *def* keyword is used to define a normal function in Python.

Similarly, the *lambda* keyword is used to define an anonymous function in Python.

Lambda functions are provided as arguments to another functions.

###### Example 1:

```python
products = [
    ("Product-1", 15),
    ("Product-2", 25),
    ("Product-3", 5),
    ("Product-4", 45),
    ("Product-5", 20),
    ("Product-6", 30)
]

products.sort(key=lambda product: product[1])
print(products)

"""
[('Product-3', 5), ('Product-1', 15), ('Product-5', 20), 
('Product-2', 25), ('Product-6', 30), ('Product-4', 45)]
"""
```

Lambda functions are passed as argumnets to other functions.

Lamda function has short lifespan in memory, it means whenever we are done with this code, this function will be garbage collected.

###### Example 2:

```python
my_list = [1, 5, 4, 6, 8, 11, 3, 12, 34, 55]

new_list = filter(lambda x: (x % 2 == 0), my_list)
# filter even numbers

for num in new_list:
    print(num, end=" ")
# 4 6 8 12 34
print()

even_nums = list(new_list)
print(even_nums) 
# []    --> Empty List
```

##### Example 3:

```python
my_list = [1, 5, 4, 6, 8, 11, 3, 12, 34, 55]

new_list = filter(lambda x: (x % 2 == 0), my_list)

even_nums = list(new_list)
print(even_nums) 
# [4, 6, 8, 12, 34] 
```

The line `new_list = filter(lambda ...` is going to return an iterator and we iterate over that object. The iterator can only be iterated over once.

It means that whenever we are actually passing new list to `list()` method,   

###### Example 4: lambda + map()

```python
my_list = [1, 5, 4, 6, 8, 11, 3, 12, 34, 55]

new_list = list(map(lambda x: x * 2, my_list))

print(new_list)
# [2, 10, 8, 12, 16, 22, 6, 24, 68, 110]
```

### The Map Function

**map()** function returns a map object(which is an iterator) of the results after applying the given function to each item of a given iterable (list, tuple etc.)

`map(fun, iter)`

###### Example 1:

```python
numbers = (1, 2, 3, 4, 5)


def calculate_square(n):
    return n * n


result = map(calculate_square, numbers)
print(result)
# <map object at 0x0000023E7E98F1C0>

# Converting map object a set
num_square = set(result)
print(num_square)
# {1, 4, 9, 16, 25}
```

###### Example 2:

```python
letters = ["a", "b", "c"]

result = map(lambda x: x, letters)

characters = list(result)
print(characters)
# ['a', 'b', 'c']
```

###### Example 3:

```python
numbers = (1, 2, 3, 4, 5)

result = map(lambda x: x * x, numbers)

nums = tuple(result)
print(nums)
# (1, 4, 9, 16, 25)
```

###### Example 4: Passinf multiple iterables to a map method

```python
numbers1 = [1, 2, 3 ,4, 5]
numbers2 = [7, 8]

result = map(lambda n1, n2: n1 + n2, numbers1, numbers2)
print(tuple(result))
# (8, 10)

print(set(result))
# set()
```

`map()` is going to run as many time as the smallest iterable has items.

### The Zip Function

**Python zip() method** takes iterable or containers and returns a single iterator object, having mapped values from all the containers. 

It is used to map the similar index of multiple containers so that they can be used just using a single entity.

**Syntax:** `zip(*iterators)`

`zip()` continues until the shortest argument is exhausted.

###### Example 1:

```python
# No iterables are passed
result = zip()
print(result, " - ", type(result))
# <zip object at 0x0000023E7EA17D80>  -  <class 'zip'>

result_list = list(result)
print(result_list)
# []
```

###### Example 2:

```python
numbers_list = [1, 2, 3]
names_list = ['Adrianna', 'Cecile', 'Darcey']

result = zip(numbers_list, names_list)
result_list = list(result)
print(result_list)
# [(1, 'Adrianna'), (2, 'Cecile'), (3, 'Darcey')]
```

###### Example 3:

```python
numbers_list = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
names_list = ['Adrianna', 'Cecile', 'Darcey']
numbers_tuple = ('ONE', 'TWO', 'THREE', 'FOUR', 'FIVE', 'SIX')

# different number of iterables
result = zip(numbers_list, numbers_tuple)
result_set = set(result)
print(result_set)
# {(2, 'TWO'), (1, 'ONE'), (4, 'FOUR'),
# (6, 'SIX'), (3, 'THREE'), (5, 'FIVE')}

result = zip(numbers_list, names_list, numbers_tuple)
result_list = list(result)
print(result_list)
# [(1, 'Adrianna', 'ONE'), (2, 'Cecile', 'TWO'), (3, 'Darcey', 'THREE')]
```

###### Example 4: unipping the values

```python
coordinate = ['x', 'y', 'z']
value = [3, 4, 5]

result = zip(coordinate, value)
result_list = list(result)
print(result_list)
# [('x', 3), ('y', 4), ('z', 5)]

unzipped_coordinates, unzipped_values = zip(*result_list)

# unzipped iterables are converted to a tuple
print(unzipped_coordinates)
# ('x', 'y', 'z')

print(unzipped_values)
# (3, 4, 5)
```

### Array Data Structure

###### Example 1:

The first parameter of the array function is a _Type Code_. 

[Efficient arrays of numeric values](https://docs.python.org/3/library/array.html)

The type-code is a string of one charachter which determines the type of object in an array.

###### Example 1:

```python
from array import array

numbers = array("i", [1, 2, 3])
numbers.append(4)

print(type(numbers))
# <class 'array.array'>

print(numbers)
# array('i', [1, 2, 3, 4])

numbers[0] = 2.3
# TypeError: 'float' object cannot be interpreted as an integer
```

### Generator Expressions

When you are working with a really large dataset or an infinite stream of data, in this situation you should not store all the values in memory because it is very memory inefficient, you should use **generator** object.

A generator object is just like a list which we can iterate it over, and in each iteration the generator object is going to create or genereate a new value.

###### Example 1: list comprehensions

```python
numbers = [x * 2 for x in range(15)]

print(numbers)
# [0, 2, 4, 6, 8, 10, 12, 14, 16, 18, 20, 22, 24, 26, 28]

print(type(numbers))
# <class 'list'>

for x in numbers:
    print(x, end="-")
# 0-2-4-6-8-10-12-14-16-18-20-22-24-26-28-
```

###### Example 2: generator object

```python
numbers = (x * 2 for x in range(15))

print(numbers)
# <generator object <genexpr> at 0x0000023E7EB10380>

print(type(numbers))
# <class 'generator'>

for x in numbers:
    print(x, end="-")
# 0-2-4-6-8-10-12-14-16-18-20-22-24-26-28-
```

###### Example 3: getting the size of a generator object

```python
from sys import getsizeof

numbers0 = (x * 2 for x in range(1))
numbers1 = (x * 2 for x in range(10))
numbers2 = (x * 2 for x in range(100))
numbers3 = (x * 2 for x in range(1000))
numbers4 = (x * 2 for x in range(10000))
numbers5 = (x * 2 for x in range(100000))

print("Generator Size:", getsizeof(numbers0))   # 208 Byte
print("Generator Size:", getsizeof(numbers1))   # 208 Byte
print("Generator Size:", getsizeof(numbers2))   # 208 Byte
print("Generator Size:", getsizeof(numbers3))   # 208 Byte
print("Generator Size:", getsizeof(numbers4))   # 208 Byte
print("Generator Size:", getsizeof(numbers5))   # 208 Byte

numbers_list0 = [x * 2 for x in range(1)]
numbers_list1 = [x * 2 for x in range(10)]
numbers_list2 = [x * 2 for x in range(100)]
numbers_list3 = [x * 2 for x in range(1000)]
numbers_list4 = [x * 2 for x in range(10000)]
numbers_list5 = [x * 2 for x in range(100000)]

print("List Size: ", getsizeof(numbers_list0))  # 88 Byte
print("List Size: ", getsizeof(numbers_list1))  # 184 Byte
print("List Size: ", getsizeof(numbers_list2))  # 920 Byte
print("List Size: ", getsizeof(numbers_list3))  # 8856 Byte
print("List Size: ", getsizeof(numbers_list4))  # 85176 Byte
print("List Size: ", getsizeof(numbers_list5))  # 800984 Byte
```

### Unpacking Operator

The unpacking operator unpacks the items of an iterable without their actual syntax.

###### Example 1:

```python
numbers = [1, 2, 3]

print(numbers)
# [1, 2, 3]

print(1, 2, 3)
# 1, 2, 3

print(*numbers)
# 1 2 3
```

###### Example 2:

```python
values = list(range(15))
print(values)
# [0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14]

print(*values)
# 0 1 2 3 4 5 6 7 8 9 10 11 12 13 14


values2 = [*range(20)]
print(*values2)
# 0 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19

print(values2)
# [0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17, 18, 19]
```

###### Example 3:

```python
print({"Python"})       # {'Python'}
print({*"Python"})      # {'h', 'P', 'n', 'o', 't', 'y'}
print(*{"Python"})      # Python
print(*{*"Python"})     # h P n o t y
```

###### Example 4:

```python
cities = ["Berlin", "Denver", "Palermo", "Tokyo", "Rio"]
names = ["Olivia", "Amelia", "Oliver", "Charlotte", "Liam"]

info = [*names, *cities]
print(info)
#
#
```

###### Example 5:

```python
dict_one = {
    "name": "Jasper",
    "city": "Tokyo"
}

dict_two = {
    "full name": "Dick Van Dyke",
    "address": "USA"
}

dict_three = {
    "name": "William",
    "job": "Developer"
}


combined = {**dict_one, **dict_two, "Country": "France", **dict_three}


print(combined)
# {'name': 'William', 'city': 'Tokyo', 'full name': 'Dick Van Dyke',
#  'address': 'USA', 'Country': 'France', 'job': 'Developer'}
```

If two keys of  a dictionary have the same name, the value for that common name, the latest value will be used.

### Recursive Functions

A recursive function is a function  that calls itself.

![](D:\OneDrive\z%20-%20My%20Docs\md%20docs\Python%20Bootcamp%202022%20-%20Muslim%20Helalee\images\recursive%20function%202.jpg)

###### Example 1:

```python
def factorial(x):
    if x == 1:
        return 1
    else:
        return (x * factorial(x - 1))



for x in range(1,11):
    print("The factorial of", x, "is", factorial(x))

# The factorial of 1 is 1
# The factorial of 2 is 2
# The factorial of 3 is 6
# The factorial of 4 is 24
# The factorial of 5 is 120
# The factorial of 6 is 720
# The factorial of 7 is 5040
# The factorial of 8 is 40320
# The factorial of 9 is 362880
# The factorial of 10 is 3628800
```

![](D:\OneDrive\z%20-%20My%20Docs\md%20docs\Python%20Bootcamp%202022%20-%20Muslim%20Helalee\images\recursive%20function%201.jpg)

###### Example 2:

```python
import sys

print(sys.getrecursionlimit()) # 1000
```

###### Example 3:

```python
def recursor():
    recursor()


recursor()
# RecursionError: maximum recursion depth exceeded
```
