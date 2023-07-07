## 14 - Advanced Python – Iterators

### Introduction to Iterators

Iterator in Python is an object that is used to iterate over iterable objects like lists, tuples, dicts, and sets. The iterator object is initialized using the **iter()** method. It uses the **next()** method for iteration.

1. **__iter__():** The iter() method is called for the initialization of an iterator. This returns an iterator object
2. **__next__():** The next method returns the next value for the iterable. When we use a for loop to traverse any iterable object, internally it uses the iter() method to get an iterator object, which further uses the next() method to iterate over. This method raises a StopIteration to signal the end of the iteration.

###### Example 1: \_\_iter\_\_(), \_\_next\_\_()

```python
numbers = [1, 2, 3, 4, 5]


first_iterator = iter(numbers)
print(next(first_iterator))        # 1
print(next(first_iterator))        # 2


# next() == __next__()

print(first_iterator.__next__())    # 3
print(first_iterator.__next__())    # 4

print(type(first_iterator))                 # <class 'list_iterator'>
print(type(first_iterator.__next__()))      # <class 'int'>

# print(first_iterator.__next__())  # StopIteration
```

### How _for_ Loops Work

The `for` loop, whenever the iteration ends, it is going to raise the `StopIteration` exception and handle it internally all by itself. 

###### Example 1:

```python
numbers = [1, 2, 3, 4, 5]


# for number in numbers:
#     print(number)


iterable_obj = iter(number)

# infinite while loop
while True:
    try:
        # get the next item
        element = next(iterable_obj)

        # do something with element
        print(f"Element: {element}")

    except StopIteration:
        break
```

### Build Custom Iterator

###### Example 1:

```python
class NumberPower:
    def __init__(self, maxi_num):
        self.maxi_num = maxi_num

    # Creating iterator object
    def __iter__(self):
        self.n = 0
        return self

    # iterate over the created iterator object
    # and generate one value each time
    def __next__(self):
        if self.n <= self.maxi_num:
            result = 2 ** self.n
            self.n += 1
            return result
        else:
            raise StopIteration


# creating an instance/object of the class
num_pow = NumberPower(2)

# creating an iterable from the object
iterable_data = iter(num_pow)

# using the next() to go to the next iterator element
print(next(iterable_data))      # 1
print(next(iterable_data))      # 2
print(next(iterable_data))      # 4
# print(next(iterable_data))    # StopIteration


for i in NumberPower(4):
    print(i, end=" ")

# 1 2 4 8 16
```

### Infinite Iterators

###### Example 1:

```python
# print(int())                # 0

number = iter(int, 1)       # 
print(next(number))        # 0
print(next(number))        # 0
print(next(number))        # 0
print(next(number))        # 0
print(next(number))        # 0
```

###### Example 2:

```python
number = iter(int, 1)

for element in number:
    print(number)

# maybe crash
```

###### Example 3:

```python
class OddNums:
    def __iter__(self):
        self.num = 1
        return self

    def __next__(self):
        num = self.num
        self.num += 2
        return num

odd_nums = OddNums()

iterable_data = iter(odd_nums)

print(next(iterable_data))    # 1
print(next(iterable_data))    # 3
print(next(iterable_data))    # 5
print(next(iterable_data))    # 7
```
