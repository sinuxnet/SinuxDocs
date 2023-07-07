## Python Data Structures – Lists

### List Introduction

List are used to stroe multiple values in a single variable.

###### Example 1:

```python
numbers = [1, 2, 64, 124, 654]
name = ["John", "Mark", "Emily", "Sandra"]
print(numbers)
# [1, 2, 64, 124, 654]
print(name)
# ['John', 'Mark', 'Emily', 'Sandra']
```

###### Example 2:

```python
likes = [["tv", "gaming"], ["pizza", "pasta"]]
print(likes)
# [['tv', 'gaming'], ['pizza', 'pasta']]
```

###### Example 3:

```python
mixed = [[1, 5], "Cat", "Dog", [["wind", "water"], ["earth", "fire"]]]
print(mixed)
# [[1, 5], 'Cat', 'Dog', [['wind', 'water'], ['earth', 'fire']]]
```

###### Example 4 (identical items):

```python
animal = ["Cat"] * 10
print(animal)
```

###### Example 5 (merging/concatenation):

```python
even_nums = [2, 4, 6, 8, 10]
odd_nums = [1, 3, 5, 7, 9]
cities = ["Tehran", "New York", "London"]
boolean = [True, False]

mixed_data = even_nums + odd_nums + cities + boolean

print(mixed_data)
# [2, 4, 6, 8, 10, 1, 3, 5
#, 7, 9, 'Tehran', 'New York', 'London', True, False]
```

### The List Method

The list method is the second way for creating lists. The first one was creating lists using the square bracket.

**Do not confuse this the list <span style="color: darkblue">method</span> with list <span style="color: darkblue">method</span><span style="color: red">s</span>**

###### Example 1:

```python
numbers = list(range(100)]
print(numbers)
# [0, 1, 2, ..., 97, 98, 99]
```

###### Example 2:

```python
random_name = list("Sinuxnet")
print(random_name)
# ['S', 'i', 'n', 'u', 'x', 'n', 'e', 't']
```

### Accessing List Items

Access to an individul item from a list.

###### Example 1:

```python
collection = [28, "M", 32, "H", "Parrot", "Sea Bisuit"]

collection[5] = "Python"

print(collection)       # [28, 'M', 32, 'H', 'Parrot', 'Python']

print(collection[0])    # 28
print(collection[2])    # 32
print(collection[4])    # Parrot
print(collection[1])    # M
```

###### Example 2:

```python
collection = [28, "M", 32, "H", "Parrot", "Sea Bisuit"]

print(collection[0:2])    # [28, 'M']
print(collection[0:4])    # [28, 'M', 32, 'H']
print(collection[:5])     # [28, 'M', 32, 'H', 'Parrot']
print(collection[0:])     # [28, 'M', 32, 'H', 'Parrot', 'Sea Bisuit']
print(collection[:])      # [28, 'M', 32, 'H', 'Parrot', 'Sea Bisuit']
```

###### Example 3:

```python
collection = [28, "M", 32, "H", "Parrot", "Sea Bisuit", "python"]

print(collection[::2])
# [28, 32, 'Parrot', 'python']

print(collection[::3])
# [28, 'H', 'python']

print(collection[::-1])    # Reverse list
# ['python', 'Sea Bisuit', 'Parrot', 'H', 32, 'M', 28]

print(collection[2::2])    # Start from 2 index (Default = 0)
# [32, 'Parrot', 'python']

print(collection[2:5:2])    # Start form 2, Jump to 5 and go on
# [32, 'Parrot']
```

### List Unpacking

###### Example 1:

```python
numbers = [23, 49, 85]
num1, num2, num3 = numbers

print(num1)     # 23
print(num2)     # 49
print(num3)     # 85
```

###### Example 2:

```python
numbers = [23, 49, 85, 1, 2, 3, 4, 5]
num1, num2, *other_nums = numbers

print(num1)             # 23
print(num2)             # 49
print(other_nums)       # [85, 1, 2, 3, 4, 5]
```

###### Example 3:

```python
numbers = [23, 49, 85, 1, 2, 3, 4, 5]
num1, *other_nums, num2 = numbers

print(num1)             # 23
print(num2)             # 5
print(other_nums)       # [49, 85, 1, 2, 3, 4]
```

###### Example 4:

```python
numbers = [23, 49, 85, 1, 2, 3, 4, 5]
num1, num2, *other_nums, num3, num4 = numbers

print(num1)             # 23
print(num2)             # 49
print(num3)             # 4
print(num4)             # 5
print(other_nums)       # [85, 1, 2, 3]
```

### Looping Over Lists

###### Example 1:

```python
letters = ["a", "b", "c"]

for letter in letters:
    print(letter)
```

###### Example 2:

```python
letters = ["a", "b", "c"]

for letter in enumerate(letters):
    print(letter)
#(0, 'a')
#(1, 'b')
#(2, 'c')
```

###### Example 3:

```python
items = (0, "a")
index, letter = items

print(index, letter)
# 0 a
```

###### Example 4:

```python
letters = ["a", "b", "c"]

for index, item in enumerate(letters):
    print(index, item)

# 0 a
# 1 b
# 2 c
```

### Modifying List Items

###### Example 1:

* append()

* insert()

* pop()

* remove()

* del

* clear()

* reverse()

* join()

###### Example 1:  append(), insert(), pop()

```python
numbers = [1, 55, 64, 124, 654]
names = ["John", "Mark", "Emily", "Sandra"]
fruits = ['Apple', "Orange", "Banana"]

names.append("Sandrine")
print(names)        # ['John', 'Mark', 'Emily', 'Sandra', 'Sandrine']

fruits.insert(1, "Lemon")
fruits.insert(0, "Peach")
print(fruits)       # ['Peach', 'Apple', 'Lemon', 'Orange', 'Banana']

# numbers.pop()
# print(numbers)    # [1, 55, 64, 124]

numbers.pop(-1)
numbers.pop(1)
names.pop(3)
print(numbers)      # [1, 64, 124]
print(names)        # ['John', 'Mark', 'Emily', 'Sandrine']
```

###### Example 2: remove()

```python
numbers = [1, 55, 64, 124, 654]
names = ["John", "Mark", "Emily", "Sandra", "Sandrine"]
fruits = ["Peach", "Apple", "Lemon", "Orange", "Banana"]

fruits.remove("Banana")
print(fruits)       # ['Peach', 'Apple', 'Lemon', 'Orange']
```

###### Example 3: del

```python
numbers = [1, 55, 64, 124, 654]
names = ["John", "Mark", "Emily", "Sandra", "Sandrine"]
fruits = ["Peach", "Apple", "Lemon", "Orange", "Banana"]

# del numbers[0]
# print(numbers)      # [55, 64, 124, 654]

del numbers[1:4]
print(numbers)        # [1, 654] 
```

###### Example 4: clear(), reverse(), join()

```python
numbers = [1, 23, 64, 124, 654]
names = ["John", "Mark", "Emily", "Sandra"]
fruits = ['Apple', "Orange", "Banana"]


print(fruits.clear())   # None

names.reverse()
print(names)            # ['Sandra', 'Emily', 'Mark', 'John']

numbers.reverse()
print(numbers)          # [654, 124, 64, 23, 1]

print("".join(names))       # SandraEmilyMarkJohn
print(" ".join(names))      # Sandra Emily Mark John
print(", ".join(names))     # Sandra, Emily, Mark, John
```

### Finding List Items Index

###### Example 1: index()

```python
fruits = ['Apple', "Orange", "Banana"]

print(fruits.index("Orange"))   # 1

print(fruits.index("Mango"))    # ValueError: 'Mango' is not in list

if "Mango" in fruits:
    print(fruits.index("Mango"))        # Nothing to Shows
```

###### Example 2: count()

```python
numbers = [1, 1, 1]
nums = [2, 2, 2] * 5
fruits = ['Apple', "Orange", "Banana"]

print(fruits.index("Mango"))       # 0
print(fruits.index("Banana"))      # 1
print(numbers.index(1))            # 3
print(nums.index(2))            # 15
```

### Sorting Lists

###### Example 1: sort()

```python
numbers = [1, 5, 32, 124, 70, 854, 2356, 6589, 62, 8, 19, 999, 321]

numbers.sort()
# print(numbers)
# 1, 5, 8, 19, 32, 62, 70, 124, 321, 854, 999, 2356, 6589

numbers.sort(reverse=True)
print(numbers)
# 6589, 2356, 999, 854, 321, 124, 70, 62, 32, 19, 8, 5, 1
```

**sorted()** method will not modify the original list; it will return a new list.

###### Example 2: sorted()

```python
numbers = [1, 5, 32, 124, 70, 854, 2356, 6589, 62, 8, 19, 999, 321]

# print(sorted(numbers))
# 1, 5, 8, 19, 32, 62, 70, 124, 321, 854, 999, 2356, 6589

print(sorted(numbers, reverse=True))
# 6589, 2356, 999, 854, 321, 124, 70, 62, 32, 19, 8, 5, 1
```

###### Example 3: sort()

```python
products = [
    ("Cup", 5),
    ("T-Shirt", 19),
    ("Hat", 29),
    ("Watch", 49),
    ("UV Lamp", 27),
    ("Mug", 7)
]

products.sort()
print(products)
# [('Cup', 5), ('Hat', 29), ('Mug', 7), ('T-Shirt', 19), 
# ('UV Lamp', 27), ('Watch', 49)]
```

###### Example 4: sort()

```python
products = [
    ("Cup", 5),
    ("T-Shirt", 19),
    ("Hat", 29),
    ("Watch", 49),
    ("UV Lamp", 27),
    ("Mug", 7)
]


def sort_products(product):
    return product[1]

# products.sort(sort_products)
# TypeError: sort() takes no positional arguments


products.sort(key=sort_products)
# [('Cup', 5), ('Mug', 7), ('T-Shirt', 19),
# ('UV Lamp', 27), ('Hat', 29), ('Watch', 49)]
```

### List Comprehensions

List comprehensions is a powerful tool that allows us to create modified data structure duplicates with literally one line of code. 

###### Example 1:

```python
numbers = [23, 54, 67, 89, 15, 99]


numbers2 = [num for num in numbers]
print(numbers2)    # [23, 54, 67, 89, 15, 99]

numbers3 = [num * 2 for num in numbers]
print(numbers3)     # [46, 108, 134, 178, 30, 198]

numbers4 = [(num / 2) * 5 for num in numbers]
print(numbers4)     # [57.5, 135.0, 167.5, 222.5, 37.5, 247.5]
```

###### Example 2:

```python
fruits = ['Apple', "Orange", "Banana"]


fruits2 = [fruit.lower() for fruit in fruits]
print(fruits2)        # ['apple', 'orange', 'banana']
```

###### Example 3:

```python
products = [
    ("Cup", 5),
    ("T-Shirt", 19),
    ("Hat", 29),
    ("Watch", 49),
    ("UV Lamp", 27),
    ("Mug", 7)
]


items = [item for item in products]
print(items)
# [('Cup', 5), ('T-Shirt', 19), ('Hat', 29), 
# ('Watch', 49), ('UV Lamp', 27), ('Mug', 7)]

product_name = [item[0] for item in products]
print(product_name)
# ['Cup', 'T-Shirt', 'Hat', 'Watch', 'UV Lamp', 'Mug']

prices = [item[1] for item in products]
print(prices)
# [5, 19, 29, 49, 27, 7]
```

###### Example 4: Single Condition

```python
products = [
    ("Cup", 5),
    ("T-Shirt", 20),
    ("Hat", 29),
    ("Watch", 49),
    ("UV Lamp", 27),
    ("Mug", 7)
]


items = [item[1] for item in products if item[1] >= 20]
print(items)    # [20, 29, 49, 27]
```

###### Example 5: Two Conditions

```python
numbers = [21, 24, 56, 564, 102, 504, 79, 84]


modified_numbers = [
    num if num < 100 else int(num / 10) for num in numbers
]
print(modified_numbers)    # [21, 24, 56, 56, 10, 50, 79, 84]


modified_numbers_2 = [
     num if num > 100 else num * 10 for num in numbers
]
print(modified_numbers_2) # [210, 240, 560, 564, 102, 504, 790, 840]
```

### Swapping List Items

###### Example 1:

```python
nums= [2, 4, 6]


nums[0], nums[1], nums[2] = nums[2], nums[1], nums[0]

print(nums) # [6, 4, 2]

```
