## 10 - Python Data Structures – Sets

### Introduction to sets

* Sets are mutable.

* The set's items must be of  immutable types.

* Sets will never hav duplicates

* Capable to perform mathematical operations like union, intersections, symmetric difference, etc.

* Set's items are going to be unordered.

###### Example 1:

```python
first_set = {21, 32, 54, 665, 999}
print(first_set)
# {32, 21, 54, 999, 665}


mixed = {5.19, "Set", ("London", "paris")}
print(mixed)
# {('London', 'paris'), 5.19, 'Set'}


numbers = {1, 2, 3, 4, 5, 6, 1, 2, 3, 4, 5, 6, 7}
print(numbers)
# {1, 2, 3, 4, 5, 6, 7}
```

###### Example 2: Creating a set from a tuple, list & dictionary

```python
colors = set(("blue", "red", "green", "blue"))
print(colors)
# {'blue', 'red', 'green'}

colors = set(["blue", "red", "green", "blue"])
print(colors)
# {'blue', 'red', 'green'}

colors = set({
    "blue": 1,
    "red": 2,
    "green": 3,
    "blue": 4
})
print(colors)
# {'blue', 'red', 'green'}
```

**Note:** A set can not have a mutable data type as an item

###### Example 3:

```python
colors = {"red", "blue", [1, 2, 3]}
# TypeError: unhashable type: 'list'
```

###### Example 4: Creating an empty set

```python
names = {}
print(names)          # {}
print(type(names))    # <class 'dict'>

numbers = set()
print(numbers)
print(type(numbers))
```

### Modifying Sets

**Note:** Since sets are unordered, the indexing doesn't mean anything and we can not use indexing to grab any set item and modify that way. (also slicing)

###### Example 1:

```python
mixed_info = {"python", "Dog"}
print(mixed_info)

mixed_info[1]
# TypeError: 'set' object is not subscriptable
```

###### Example 2: add(), update()

```python
mixed_info = {"python", "Dog"}

mixed_info.add(31)
print(mixed_info)
# {'Dog', 'python', 31}

mixed_info.update([12, "Jar", "Send"])   # Iterable
print(mixed_info)
# {'Dog', 12, 'Jar', 'Send', 'python', 31}

mixed_info.update(["Bird", "Island"], ("Cat", "Island"),
                  {"Rabbit", "Island"})
print(mixed_info)
# {'Island', 'Dog', 12, 'Jar', 'Cat', 'Bird',
#  'Send', 'Rabbit', 'python', 31}
```

### Removing Set Items

**Note:** Unlike _remove()_ method, the _discard()_ does not show error when input value does not exist

###### Example 1: discard()

```python
numbers = {1, 2, 3, 4, 5, 6}
print(numbers)
# {1, 2, 3, 4, 5, 6}

numbers.discard(4)
print(numbers)
# {1, 2, 3, 5, 6}

numbers.discard(15)
print(numbers)
# {1, 2, 3, 5, 6}
```

###### Example 2: remove()

```python
numbers = {1, 2, 3, 4, 5, 6}
print(numbers)
# {1, 2, 3, 4, 5, 6}

numbers.remove(5)
print(numbers)
# {1, 2, 3, 4, 6}

numbers.remove(16)
print(numbers)
# Traceback (most recent call last) , KeyError: 16
```

###### Example 3: pop()

```python
numbers = {1, 2, 3, 4, 5, 6}
print(numbers)
# {1, 2, 3, 4, 5, 6}

numbers.pop()
print(numbers)
# {2, 3, 4, 5, 6}
```

**Note:** We do not know which  item would  be poped.

```python
numbers = {1, 2, 3, 4, 5, 6}
print(numbers)
# {1, 2, 3, 4, 5, 6}

numbers.clear()
print(numbers)
# set()
```

### Set Operations

###### Example 1:  Union

```python
A = {1, 2, 3, 4, 5}
B = {4, 5, 6, 7, 8}

# With Uninon Operator
print(A | B)
# print(B | A)
# {1, 2, 3, 4, 5, 6, 7, 8}

print(A.union(B))
# print(A.union(B))

# {1, 2, 3, 4, 5, 6, 7, 8}
```

###### Example 2: Intersection

```python
A = {1, 2, 3, 4, 5}
B = {4, 5, 6, 7, 8}

print(A & B)
# print(B & A)
# {4, 5}

print(A.intersection(B))
# print(B.intersection(A))
# {4, 5}
```

###### Example 3: difference

```python
A = {1, 2, 3, 4, 5}
B = {4, 5, 6, 7, 8}

print(A - B)
# {1, 2, 3}

print(B - A)
# {8, 6, 7}

print(A.difference(B))
# {1, 2, 3}

print(B.difference(A))
# {8, 6, 7}
```

###### Example 4: symmetric difference

```python
A = {1, 2, 3, 4, 5}
B = {4, 5, 6, 7, 8}

print(A ^ B)
# print(B ^ A)
# {1, 2, 3, 6, 7, 8}

print(A.symmetric_difference(B))
# print(B.symmetric_difference(A))
# {1, 2, 3, 6, 7, 8}
```

### More Set Methods

###### Example 1: copy()

```python
numbers = {101, 202, 303, 404, 505, 606}

other_numbers = numbers        # object reference
print(numbers)          # {404, 101, 505, 202, 606, 303}
print(other_numbers)    # {404, 101, 505, 202, 606, 303}


numbers.remove(606)     # other reffrence will be affected
print(numbers)          # {404, 101, 505, 202, 303}
print(other_numbers)    # {404, 101, 505, 202, 303}

other_numbers.discard(505)  # other reffrence will be affected
print(numbers)              # {404, 101, 202, 303}
print(other_numbers)        # {404, 101, 202, 303}

# ----------------------------
some_numbers = numbers.copy()
print(numbers)          # {404, 101, 202, 303}
print(some_numbers)     # {404, 101, 202, 303}


some_numbers.add(909)
print(numbers)          # {404, 101, 202, 303}
print(some_numbers)     # {101, 202, 909, 303, 404}

# -----------------------------
print(id(numbers))          # 2242563475040
print(id(other_numbers))    # 2242563475040
print(id(some_numbers))     # 2242563481984
```

![](D:\OneDrive\z%20-%20My%20Docs\md%20docs\Python%20Bootcamp%202022%20-%20Muslim%20Helalee\images\Copy.jpg)

**isdisjoint():** If two set data types do not have any common item(s), they are disjoint and **isdisjoint()** return _True_ boolean value,  otherwise it will return _False_ value.  

###### Example 2: isdisjoint()

```python
A = {1, 2, 3, 4}
B = {5, 6, 7}
C = {4, 5, 6}
D = {10, 20, 30, 7}


print('Are A and B disjoint?', A.isdisjoint(B))    # True
print('Are A and C disjoint?', A.isdisjoint(C))    # False
print('Are A and D disjoint?', A.isdisjoint(D))    # True
print('Are B and C disjoint?', B.isdisjoint(C))    # False
print('Are B and D disjoint?', B.isdisjoint(D))    # False
print('Are C and D disjoint?', C.isdisjoint(D))    # True
```

###### Example 3: isdisjoint() with other iterables

```python
A = {'a', 'b', 'c', 'd'}
B = ['b', 'e', 'f']
C = '5de4'
D = {1: 'a', 2: 'b'}
E = {'a': 1, 'b': 2}
F = ("z", "g", "s")


print('Are A and B disjoint?', A.isdisjoint(B))    # False
print('Are A and C disjoint?', A.isdisjoint(C))    # Flase
print('Are A and D disjoint?', A.isdisjoint(D))    # True
print('Are A and E disjoint?', A.isdisjoint(E))    # Flase  
print('Are A and F disjoint?', A.isdisjoint(F))    # True
```

###### Example 4: issubset(), issuperset()

```python
A = {1, 2, 3}
B = {1, 2, 3, 4, 5}
C = {1, 2, 4, 5}
# A and C are subset of B
# B is superset of A and C

# subset (smaller to bigger)
print(A.issubset(B))    # True
print(A.issubset(C))    # Flase
print(B.issubset(A))    # False
print(B.issubset(C))    # False
print(C.issubset(A))    # False
print(C.issubset(B))    # True

# superset (bigger to smaller)
print(A.issuperset(B))  # False
print(A.issuperset(C))  # Flase
print(B.issuperset(A))  # True
print(B.issuperset(C))  # True
print(C.issuperset(A))  # False
print(C.issuperset(B))  # False
```

### More Set operations

###### Example 5: Membership Test

```python
numbers = {1, 2, 3, 4}

print(1 in numbers)         # True
print(5 in numbers)         # False
print("a" in numbers)       # False
```

###### Example 6: Iterating Through a Set

```python
numbers = {1, 2, 3, 4}

for num in numbers:
    print(num)
"""
1
2
3
4
"""
```

### Frozen Set

Tuples are equivalent to **immutable** lists and Frozen set are equivalent to immutable set. 

Frozen sets are hashable (unlike set) and can be use as keys to a dictionary.

Frozen sets like sets are **not ordered**.

###### Example 1: Creating a frozenset

```python
numbers = frozenset([1, 2, 3, 4, 5, 6])    # Iterable
print(numbers)          # frozenset({1, 2, 3, 4, 5, 6})
print(type(numbers))    # <class 'frozenset'>


some_nums = frozenset([3, 4, 5, 6])
print(numbers.isdisjoint(some_nums))    # False
print(numbers.difference(some_nums))    # frozenset({1, 2})
```

###### Example 2; frozenset() method

```python
vowels = ("a", "e", "i", "o", "u")
forzen_vowels = frozenset(vowels)
print(forzen_vowels)
# frozenset({'u', 'i', 'a', 'e', 'o'})

print("Empty Frozen Set: ", frozenset())
# Empty Frozen Set:  frozenset()

print(frozenset())
# frozenset()

print(frozenset().add("Y"))
# AttributeError: 'frozenset' object has no attribute 'add'
```

### Set Comprehensions

```python
numbers1 = {number ** 2 for number in range(10)}
print(numbers1)
#

numbers2 = {number ** 3 for number in range(5)}
print(numbers2)
```
