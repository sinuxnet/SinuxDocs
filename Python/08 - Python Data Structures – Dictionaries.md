## 08 - Python Data Structures – Dictionaries

## Introduction To Dictionaries

Dictionaries in Python are a collection of key value pairs, a real world example of dictionary would be a phone book where we have a persons's name as the dictionary **key** and the phone number as the dictionary **value**.

In Python, only the dictionary keys are immutable types, but the value can be any types of data.

[Python Basics: Mutable vs Immutable Objects](https://towardsdatascience.com/https-towardsdatascience-com-python-basics-mutable-vs-immutable-objects-829a0cb1530a)

###### Example 1:

```python
contacts = {
    "Samantha": 456,
    "John": 123,
}

print(contacts)    # {'Samantha': 456, 'John': 123}

```

###### Example 2:

```python
employee_info = {
    "Name": "Will",
    "Last Name": "Bayers",
    "Address": "Hawkins",
    "Job": "Student",
    "Age": 12
}

print(employee_info)
# {'Name': 'Will', 'Last Name': 'Bayers',
# 'Address': 'Hawkins', 'Job': 'Student', 'Age': 12}

```

###### Example 3: dict()

```python
animal_names = dict(cat="sebastian", dog="Togo")

print(animal_names)
```

### Accessing Dictionary Key-Values

###### Example 1:

```python
employee_info = {
    "Name": "Will",
    "Last Name": "Bayers",
    "Address": "Hawkins",
    "Job": "Student",
    "Age": 12
}


print(employee_info["Name"])
print(employee_info["Job"])

employee_info["Job"] = "Developer"
employee_info["Hobbies"] = "Reading", "Painting"

print(employee_info)
# {'Name': 'Will', 'Last Name': 'Bayers',
# 'Address': 'Hawkins', 'Job': 'Developer',
# 'Age': 12, 'Hobbies': ('Reading', 'Painting')}
```

whenever a key has more than one value, the value is going to end up with tuple.

###### Example 2:

```python
employee_info = {
    "Name": "Will",
    "Last Name": "Bayers",
    "Address": "Hawkins",
    "Job": "Student",
    "Age": 12
}


# print(employee_info["Favorite Color"])    # KeyError 'Favorite Color'

# 1. Checking wether a key exist
if "Favorite Color" in employee_info:
    print(employee_info["Favorite Color"])    # Nothing to show

# 2. get()
print(employee_info.get("Favorite Color"))    # None
print(employee_info.get("Job"))               # Student

print(employee_info.get("Favorite Color", Green))    # Green 
print(employee_info.get("Job", Developer))           # Student
```

### Dictionary Methods

* **get():** Return the value for the given key if present in the dictionary. If not, then it will return None (if get() is used with only one argument).

* **clear():** Clear out all key-value pairs.

* **copy():**  Returns a **shallow copy** of the dictionary.

* **fromkeys():** Returns the dictionary with key mapped and specific value. It creates a new dictionary from the given sequence with the specific value.

* **items():** It is used to return the list with all dictionary keys with values.

* **keys():** Returns a view object that displays a list of all the keys in the dictionary in order of insertion using Python.

* **values():**  It is an inbuilt method in Python programming language that returns a view object. The view object contains the values of the dictionary, as a list. If you use the type() method on the return value, you get “dict_values object”. It must be cast to obtain the actual list.

* **popitem():** Removes the last inserted key-value pair from the dictionary and returns it as a tuple.

* **setdefault():** Returns the value of a key (if the key is in dictionary). Else, it inserts a key with the default value to the dictionary.

* **pop():** Removes and returns the specified element from the dictionary.
  
  * Value associated to deleted key-value pair, if key is present.
  
  * Default value if specified if key is not present.
  
  * KeyError, if key not present and default value not specified.

* **update():** Updates the dictionary with the elements from another dictionary object or from an iterable of key/value pairs.

###### Example 1: clear(), copy()

```python
employee_info = {
    "Name": "Will",
    "Last Name": "Bayers",
    "Address": "Hawkins",
    "Job": "Student",
    "Age": 12
}


# employee_info.clear()
# print(employee_info)        # {}


gerald_info = employee_info.copy()
```

###### Example 2: fromkeys()

```python
letters = ['a', 'e', 'i', 'o', 'u']
numbers = [1, 2]

vowels = dict.fromkeys(letters)
print(vowels)
# {'a': None, 'e': None, 'i': None, 'o': None, 'u': None}

vowels_2 = dict.fromkeys(letters, numbers)
print(vowels_2)
# {'a': [1, 2], 'e': [1, 2], 'i': [1, 2], 'o': [1, 2], 'u': [1, 2]}
```

###### Example 3: fromkeys()

```python
employee_info = {
    "Name": "Will",
    "Last Name": "Bayers",
    "Address": "Hawkins",
    "Job": "Student",
    "Age": 12
}


print({}.fromkeys(employee_info))
# {'Name': None, 'Last Name': None,
# 'Address': None, 'Job': None, 'Age': None}
```

###### Example 4: items(), keys()

```python
employee_info = {
    "Name": "Will",
    "Last Name": "Bayers",
    "Address": "Hawkins",
    "Job": "Student",
    "Age": 12
}

print(employee_info.items())
# dict_items([('Name', 'Will'), ('Last Name', 'Bayers'),
# ('Address', 'Hawkins'), ('Job', 'Student'), ('Age', 12)])

print(employee_info.keys())
# dict_keys(['Name', 'Last Name', 'Address', 'Job', 'Age'])


del employee_info["Age"]

print(employee_info.items())
# dict_items([('Name', 'Will'), ('Last Name', 'Bayers'), 
# ('Address', 'Hawkins'), ('Job', 'Student')])

print(employee_info.keys())
# dict_keys(['Name', 'Last Name', 'Address', 'Job'])
```

###### Example 5: values()

```python
employee_info = {
    "Name": "Will",
    "Last Name": "Bayers",
    "Address": "Hawkins",
    "Job": "Student",
    "Age": 12
}


print(employee_info.values())
# dict_values(['Will', 'Bayers', 'Hawkins', 'Student', 12])

del employee_info["Age"]

print(employee_info.values())
# dict_values(['Will', 'Bayers', 'Hawkins', 'Student'])
```

###### Example 6: popitem()

```python
employee_info = {
    "Name": "Will",
    "Last Name": "Bayers",
    "Address": "Hawkins",
    "Job": "Student",
    "Age": 12
}


print(employee_info.popitem())
# ('Age', 12)

print(employee_info)
# {'Name': 'Will', 'Last Name': 'Bayers', 
# 'Address': 'Hawkins', 'Job': 'Student'}
```

###### Example 7: setdefault()

```python
employee_info = {
    "Name": "Will",
    "Last Name": "Bayers",
    "Address": "Hawkins",
    "Job": "Student",
    "Age": 12
}


print(employee_info.setdefault("Job"))
# Student

print(employee_info.setdefault("Height"))
# None

print(employee_info.setdefault("Weight", "N/A"))
# N/A

print(employee_info.setdefault("Name", "jonathan"))
# Will

print(employee_info)
# {'Name': 'Will', 'Last Name': 'Bayers',
# 'Address': 'Hawkins', 'Job': 'Student',
# 'Age': 12, 'Height': None, 'Weight': 'N/A'}
```

###### Example 8: pop() : Case 1

```python
employee_info = {
    "Name": "Will",
    "Last Name": "Bayers",
    "Address": "Hawkins",
    "Job": "Student",
    "Age": 12
}


target_item = employee_info.pop("Job")
print(target_item)        # Students

print(employee_info)
# {'Name': 'Will', 'Last Name': 'Bayers',
# 'Address': 'Hawkins', 'Age': 12}
```

###### Example 9: pop() : Case 2, 3

```python
employee_info = {
    "Name": "Will",
    "Last Name": "Bayers",
    "Address": "Hawkins",
    "Job": "Student",
    "Age": 12
}


target_item = employee_info.pop("Height", "170cm")
print(target_item)        # 170cm

print(employee_info)
# {'Name': 'Will', 'Last Name': 'Bayers', 
# 'Address': 'Hawkins', 'Job': 'Student', 'Age': 12}


target_item = employee_info.pop("Weight")
print(target_item)        # KeyError
```

###### Example 10: update(): Case 1, Case2

```python
employee_info = {
    "Name": "Will",
    "Last Name": "Bayers",
    "Address": "Hawkins",
    "Job": "Student",
    "Age": 12
}


lost_key = {"Favorite Movie": "The Hacksaw Ridge"}
employee_info.update(lost_key)
# print(employee_info)
# {'Name': 'Will', 'Last Name': 'Bayers',
# 'Address': 'Hawkins', 'Job': 'Student',
# 'Age': 12, 'Favorite Movie': 'The Hacksaw Ridge'}

found_key = {"Favorite Movie": "1917"}
employee_info.update(found_key)
# print(employee_info)
# {'Name': 'Will', 'Last Name': 'Bayers',
# 'Address': 'Hawkins', 'Job': 'Student',
# 'Age': 12, 'Favorite Movie': '1917'}
```

###### Example 11: update(): Case 2

```python
employee_info = {
    "Name": "Will",
    "Last Name": "Bayers",
    "Address": "Hawkins",
    "Job": "Student",
    "Age": 12
}


employee_info.update(Dog_Name="Krypto", Bird_Name="Precious")
print(employee_info)
# {'Name': 'Will', 'Last Name': 'Bayers',
# 'Address': 'Hawkins', 'Job': 'Student',
# 'Age': 12, 'Dog_Name': 'Krypto', 'Bird_Name': 'Precious'}
```

### Dictionary Comprehensions

###### Example 1:

```python
# coordinates = {}
# for x in range(5):
#    coordinates[x] = (((x * 5) / 2) + 12 ) - (2.4 / 1.2) * 6

coordinates = {
    x: (((x * 5) / 2) + 12) - (2.4 / 1.2)* 6 for x in range(5)}

print(coordinates)
# {0: 0.0, 1: 2.5, 2: 5.0, 3: 7.5, 4: 10.0}
```

###### Example 2:

```python
old_price = {"milk": 1.02, "coffe": 2.5, "bread": 1.89}

dollar_to_pound = 0.76

new_price = {
    item: value * dollar_to_pound for (item, value) in old_price.items()}

print(new_price)
# {'milk': 0.7752, 'coffe': 1.9, 'bread': 1.4364}
```

###### Example 3:

```python
original_dict = {
    'Jack': 38,
    'Lincoln': 48,
    'Theodore': 57,
    'John': 33,
    'Cecile': 18 
}


even_dict = {k: v for (k, v) in original_dict.items() if v % 2 == 0 }
print(even_dict)
# {'Jack': 38, 'Lincoln': 48, 'Cecile': 18}
```

###### Example 4:

```python
original_dict = {
    'Jack': 38,
    'Lincoln': 48,
    'Theodore': 57,
    'John': 33,
    'Cecile': 21,
    'Tony': 18
}


new_dict = {
    k: v for (k, v) in original_dict.items() if v % 2 != 0 if v < 40
}
print(new_dict)
# {'John': 33, 'Cecile': 21} 


new_dict_2 = {
    k: "old" if v > 40 else "young" for (k, v) in original_dict.items()
}
print(new_dict_2)
# Jack': 'young', 'Lincoln': 'old',
# 'Theodore': 'old', 'John': 'young', 
# 'Cecile': 'young', 'Tony': 'young'}
```

###### Example 5:

```python
# _*_*_*_*_*_*_*_*_*_*_*_*_*_*_*_*_*_*_*_*_
new_dict = {
    k1: {k2: k1 * k2 for k2 in range(1, 6)} for k1 in range(2, 5)
}

print(new_dict)
# {
#     2: {1: 2, 2: 4, 3: 6, 4: 8, 5: 10},
#     3: {1: 3, 2: 6, 3: 9, 4: 12, 5: 15},
#     4: {1: 4, 2: 8, 3: 12, 4: 16, 5: 20}
# }

# _*_*_*_*_*_*_*_*_*_*_*_*_*_*_*_*_*_*_*_*_
new_dict_2 = {}

for k1 in range(2, 5):
    new_dict_2[k1] = {k2: k1 * k2 for k2 in range(1, 6)}

print(new_dict_2)
# {
#     2: {1: 2, 2: 4, 3: 6, 4: 8, 5: 10},
#     3: {1: 3, 2: 6, 3: 9, 4: 12, 5: 15},
#     4: {1: 4, 2: 8, 3: 12, 4: 16, 5: 20}
# }

# _*_*_*_*_*_*_*_*_*_*_*_*_*_*_*_*_*_*_*_*_
new_dict_3 = {}

for k1 in range(2, 5):
    new_dict_3[k1] = {}
    for k2 in range(1, 6):
        new_dict_3[k1][k2] = k1 * k2

print(new_dict_3)
# {
#     2: {1: 2, 2: 4, 3: 6, 4: 8, 5: 10},
#     3: {1: 3, 2: 6, 3: 9, 4: 12, 5: 15},
#     4: {1: 4, 2: 8, 3: 12, 4: 16, 5: 20}
# }
```

### Iterating Over Dictionaries

###### Example 1:

```python
random = {
    1: 456,
    2: 123,
    45: "Hey",
    "is_emplyed": False
}

for key in random:
    print(key)
# 1
# 2
# 45
# is_employed
```

###### Example 2:

```python
employee_info = {
    "Name": "Will",
    "Last Name": "Bayers",
    "Address": "Hawkins",
    "Job": "Student",
    "Age": 12
}


for i in employee_info:
    print(employee_info[i])
# Will
# Bayers
# Hawkins
# Student
# 12
```
