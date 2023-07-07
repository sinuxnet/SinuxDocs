## 19 - Advanced Python – Standard Library

### Paths

**Note:** A [path](https://en.wikipedia.org/wiki/Path_(computing)) is the address of a file or folder on your hard drive. The `PATH` environment variable, also referred to as just `PATH` or *Path*, is a list of paths to directories that your operating system keeps and uses to find executable scripts and programs.

###### Example 1:

```python
from pathlib import Path


# Create an absolute path on windows
path = Path("C:\\Program Files\\Python 3")
print(path)
# C:\Program Files\Python 3


# Using raw string to simplify the path creation
path = Path(r"C:\Program Files\Python 3")
print(path)
# C:\Program Files\Python 3

# Relative path
path = Path("users/__init__.py")
print(path)
# users\__init__.py


# A Path() object that represent the current folder
path = Path()
print(path)
# .


# Combining Path() objects together
path_2 = Path("Some_Path") / Path("Users")
print(path_2)
# Some_Path\Users


# Combining a Path() object with a string
path_3 = Path("some_file") / "ecommerce" / "__init__.py"
print(path_3)
# some_file\ecommerce\__init__.py


# Get Home directory of the current user
print(Path.home())
# C:\Users\sina
```

###### Example 2:

Defining Path:

```python
from pathlib import Path


path1 = Path("social/audio")
path2 = Path("social/images/__init__.py")
path3 = Path("users")
```

Check path exists:

```python
print(path1.exists(), ", ", path2.exists(), ", ", path3.exists())
# False ,  False ,  False
```

Check path is a file:

```python
print(path1.is_file(), ", ", path2.is_file(), ", ", path3.is_file())
# False ,  False ,  False
```

Check path is directory:

```python
print(path1.is_dir(), ", ", path2.is_dir(), ", ", path3.is_dir())
# False ,  False ,  False
```

return the file name in path:

```python
print(path1.name, ", ", path2.name, ", ", path3.name)
# audio ,  __init__.py ,  users
```

return the file name in path without extension:

```python
print(path1.stem, ", ", path2.stem, ", ", path3.stem)
# audio ,  __init__ ,  users
```

return the file name extension:

```python
print(path1.suffix, ", ", path2.suffix, ", ", path3.suffix)
#  ,  .py ,
```

return the parent of the file:

```python
print(path1.parent, ", ", path2.parent, ", ", path3.parent)
```

create a new path with file name changed:

```python
path3 = path2.with_name("__initial__.txt")
print(path3)
# social\images\__initial__.txt
```

getting the absolute path for newly created file:

```python
print(path3.absolute())
# d:\OneDrive\Desktop\Python\Python\social\images\__initial__.txt
```

changing the extension of a file:

```python
print(path3.with_suffix(".js"))
# social\images\__initial__.js
```

### Directories

![](D:\OneDrive\z%20-%20My%20Docs\md%20docs\Python%20Bootcamp%202022%20-%20Muslim%20Helalee\images\Directories.jpg)

###### Example 1:

Defining Path for two directories:

```python
from pathlib import Path


my_directory = Path("real_estate")
new_directory = Path("social")
```

1. `exists()`: Checking whether or not the directory exists
   
   ```python
   print(my_directory.exists())
   # False
   ```

2. `mkdir()`: Creating the directory
   
   ```
   my_directory.mkdir()
   ```

3. `rmdir()`: Removing the directory
   
   ```python
   my_directory.rmdir()
   ```

4. `rename()`: Renaming the directory
   
   ```python
   my_directory.rename("property_dealer")
   ```

5. `iterdir()`: getting the list of files and directories at this path
   
   ```python
   print(new_directory.iterdir())
   # <generator object Path.iterdir at 0x000002252D397D80>
   
   # Genarator Object
   for data in new_directory.iterdir():
       print(data)
   """
   social\app.ts
   social\audio
   social\images
   social\main.js
   social\social.py
   social\video
   social\__init__.py
   """
   
   # LC
   social_data = [data for data in new_directory.iterdir()]
   print(social_data)
   
   """
   [WindowsPath('social/app.ts'),
    WindowsPath('social/audio'),
    WindowsPath('social/images'), 
    WindowsPath('social/main.js'), 
    WindowsPath('social/social.py'), 
    WindowsPath('social/video'), 
    WindowsPath('social/__init__.py')]
   """
   ```

```
6. `is_file()`: Getting only the files

```python
path = [data for data in new_directory.iterdir()
        if data.is_file()]
print(path)
"""
[WindowsPath('social/app.ts'), 
 WindowsPath('social/main.js'),
 WindowsPath('social/social.py'), 
 WindowsPath('social/__init__.py')]
"""
```

7. `is_dir()`:
   
   ```python
   path = [data for data in new_directory.iterdir()
           if data.is_dir()]
   print(path)
   """
   [WindowsPath('social/audio'), 
    WindowsPath('social/images'), 
    WindowsPath('social/video')]
   """
   ```
* Case 1: Searching using a pattern using the asterisk symbol (*)
  
  ```python
  python_files = [data for data in new_directory.glob('*.py')]
  print(python_files)
  """
  [WindowsPath('social/social.py'), 
   WindowsPath('social/__init__.py')]
  """
  ```

* Case 2: Searching recursively using the `rglob()` method
  
  ```python
  python_files = [data for data in new_directory.rglob('*.py')]
  print(python_files)
  """
  [WindowsPath('social/social.py'), 
  WindowsPath('social/__init__.py'), 
  WindowsPath('social/audio/audio.py'), 
  WindowsPath('social/audio/__init__.py'), 
  WindowsPath('social/images/images.py'), 
  WindowsPath('social/images/__init__.py'), 
  WindowsPath('social/video/video.py'), 
  WindowsPath('social/video/__init__.py')]
  """
  ```

### Files

There is a directory with the name of prperty_dealer which contains a \_\_init\_\_.py file and  \_\_init\_\_.py has a line which `print("Hello From Jupiter")` has been written in it.

###### Example 1:

Define sources:

```python
from pathlib import Path


source = Path("property_dealer/property.py")
new_source = Path("property_dealer/app.py")
my_directory = Path("property_dealer/__init__.py")
```

1. `exists():` Checking wether or not the file exists
   
   ```pythonag-0-1gs271matag-1-1gs271mat
   print(source.exists())
   # False
   ```

2. `rename()`: Renaming the file
   
   ```python
   source.rename("property_dealer/app.py")
   ```

3. `unlink()`: Removing the file
   
   ```python
   new_source.unlink()
   ```

4. `stat()`: Returns info about the file
   
   ```python
   from time import ctime
   
   print(my_directory.stat())
   """
   os.stat_result(
       st_mode=33206,
       st_ino=3377699720528839,
       st_dev=3894615957,
       st_nlink=1,
       st_uid=0, st_gid=0,
       st_size=25,
       st_atime=1679417804,
       st_mtime=1615278680,
       st_ctime=1615278680)
   """
   print(ctime(my_directory.stat().st_atime))
   # Tue Mar 21 20:26:44 2023
   
   print(ctime(my_directory.stat().st_mtime))
   # Tue Mar  9 12:01:20 2021
   
   print(ctime(my_directory.stat().st_ctime))
   # Tue Mar  9 12:01:20 2021
   ```

```
**NOTE: The following 4 methods take care of opening and closing the files**

5. `read_bytes()`: Reading data form a file, returns the content of the file as a bytes object for representing binary data

```python
print(my_directory.read_bytes())
# b"print('Hello From Venus')"
```

6. `read_text()`: reading the content of the file as a string
   
   ```python
   print(my_directory.read_text())
   # print('Hello From Venus')
   ```

7. `write_bytes()`: writing to a file
   
   ```python
   print(my_directory.write_bytes(b"print('Hello From The Sun')"))
   # 27
   
   print(my_directory.read_text())
   # print('Hello From The Sun')
   ```

```
8. `write_text()`: writing to a file as a string

```python
print(my_directory.write_text("print('Hello From The Venus')"))
# 29

print(my_directory.read_text())
# print('Hello From The Venus')
```

9. Copying a file to another location
   
   Manually create a directory which its name is _astronomy_. 
   
   ```python
   import shutil
   ```
   
   target_directory = Path("astronomy")
   
   shutil.copy(my_directory, target_directory)

```
### Zip Files

###### Example 1:

Manually create a directory with name of *zip_dir*.   

Importing Modules:

```python
from pathlib import Path
from zipfile import ZipFile
```

Creating zip files:

```python
all_z = ZipFile("zip_dir/all.zip", "w")
py_z = ZipFile("zip_dir/py.zip", "w")


print(all_z)
# <zipfile.ZipFile filename='zip_dir/all.zip' mode='w'>

print(type(all_z))
# <class 'zipfile.ZipFile'>
```

Adding files to zip files (zipping files): Approach One:

```python
for path in Path("social").rglob("*.*"):
    all_z.write(path)

all_z.close()
```

Adding files to zip files (zipping files): Approach Two:

```python
with ZipFile("zip_dir/py.zip", "w") as py_files:
    for path in Path("social").rglob("*.py"):
        py_files.write(path)
```

The `with` statement does not take into consideration any sort of errors, it is going to close file. You do not have to worry about any kind of consequences.

###### Example 2:

Showing all files:

```python
with ZipFile("zip_dir/all.zip", ""r) as all_files:
    print(all_files.namelist())


"""
['social/app.ts',
 'social/main.js', 
 'social/social.py', 
 'social/__init__.py', 
 'social/audio/audio.py', 
 'social/audio/index.html', 
 'social/audio/__init__.py', 
 'social/images/images.py', 
 'social/images/__init__.py', 
 'social/video/video.py', 
 'social/video/__init__.py']
"""
```

Getting a single file's info:

```python
with ZipFile("zip_dir/py.zip") as file_info:
    info = file_info.getinfo("social/social.py")
    print(info.file_size)        # 20
    print(info.compress_size)    # 20
    print(info.orig_filename)    # social/social.py
    print(info.__module__)       # zipfile
```

Extracting zip files

```python
with ZipFile("zip_dir/all.zip") as all_files_z:
    all_files_z.extractall("Extracted")
```

### CSV Files

**CSV** (Comma Separated Values) is a simple **file** **format** used to store tabular data, such as a spreadsheet or database. A CSV file stores tabular data (numbers and text) in plain text. Each line of the file is a data record. Each record consists of one or more fields, separated by commas. The use of the comma as a field separator is the source of the name for this file format.  

For working CSV files in Python, there is an inbuilt module called csv.

```python
import csv
```

There are two ways of opening **csv** file:

1. Regular `open()` method

2. `with` statement
   
   The problem with `open()`: If there is any exception, the file will not be close.

###### Example: Opening a CSV file and inserting simple data in it

```python
with open("users_info/users.csv", "w", newline="") as users_data:
    CSV_writer_data = csv.writer(users_data)

    # row 1 --> table heading
    CSV_writer_data.writerow(["User ID", "User Name", "Status"])

    # row 2-6 --> first row of user data
    CSV_writer_data.writerow(["1", "sinuxnet", "online"])
    CSV_writer_data.writerow(["2", "sina", "online"])
    CSV_writer_data.writerow(["3", "sinz", "online"])
    CSV_writer_data.writerow(["4", "sinux", "offline"])
    CSV_writer_data.writerow(["5", "sinaali", "offline"])
    CSV_writer_data.writerow(["6", "sinaalikhani", "online"])
```

###### Taske 2: Reading a

```python
with open("users_info/users.csv") as users_data:
    CSV_reader_data = csv.reader(users_data)
    print(list(CSV_reader_data))

    # for data_row in CSV_reader_data:
    #    print(data_row)

"""
[['User ID', 'User Name', 'Status'], ['1', 'sinuxnet', 'online'], ['2', 'sina', 'online'], ['3', 'sinz', 'online'], ['4', 'sinux', 'offline'], ['5', 'sinaali', 'offline'], ['6', 'sinaalikhani', 'online']]
"""


with open("users_info/users.csv") as users_data:
    CSV_reader_data = csv.reader(users_data)
#    print(list(CSV_reader_data))

    for data_row in CSV_reader_data:
        print(data_row)

"""
['User ID', 'User Name', 'Status']
['1', 'sinuxnet', 'online']
[2', 'sina', 'online']
['3', 'sinz', 'online']
['4', 'sinux', 'offline']
['5', 'sinaali', 'offline']
['6', 'sinaalikhani', 'online']
"""
```

##### Links

1. [Python Docs]([csv — CSV File Reading and Writing &#8212; Python 3.11.2 documentation](https://docs.python.org/3/library/csv.html)

2. [RFC 4180](https://www.ietf.org/rfc/rfc4180.txt)

### JSON Files

**JSON is JavaScript Object Notation.** It means that a script (executable) file which is made of text in a programming language, is used to store and transfer the data. Python supports JSON through a built-in package called JSON. To use this feature, we import the JSON package in Python script. The text in JSON is done through quoted-string which contains the value in key-value mapping within { }. It is similar to the dictionary in Python. JSON shows an API similar to users of Standard Library marshal and pickle modules and Python natively supports JSON features.

<img src="file:///D:/OneDrive/z%20-%20My%20Docs/md%20docs/Python%20Bootcamp%202022%20-%20Muslim%20Helalee/images/JSON_vector_logo.svg" title="" alt="" width="379">

Importing librarie(s) and variable(s) for examples:

```python
import json
from pathlib import Path


products = [
    {"Product": "T-shirt", "Price": 5.99, "Stock Availability": 15},
    {"Product": "Jeans", "Price": 13.99, "Stock Availability": 8},
    {"Product": "Watch", "Price": 99.99, "Stock Availability": 4},
    {"Product": "Sweater", "Price": 29.99, "Stock Availability": 11}
]
```

###### Example 1: Conversion to JSON done by dumps() function

```python
products_data = json.dumps(products)
print(products_data)

"""
[{"Product": "T-shirt", "Price": 5.99, "Stock Availability": 15}, {"Product": "Jeans", "Price": 13.99, "Stock Availability": 8}, {"Product": "Watch", "Price": 99.99, "Stock Availability": 4}, {"Product": "Sweater", "Price": 29.99, "Stock Availability": 11}]
"""

print(type(products_data))
# <class 'str'>
```

###### Example 2:

Writing above data to a json file:

```python
Path("ecommerce/products.json").write_text(products_data)
```

Reading from a json file:

```python
json_data = Path("ecommerce/products.json").read_text()
readable_data = json.loads(json_data)


print(json_data)
"""
[{"Product": "T-shirt", "Price": 5.99, "Stock Availability": 15}, {"Product": "Jeans", "Price": 13.99, "Stock Availability": 8}, {"Product": "Watch", "Price": 99.99, "Stock Availability": 4}, {"Product": "Sweater", "Price": 29.99, "Stock Availability": 11}]
"""


print(readable_data)
"""
[{'Product': 'T-shirt', 'Price': 5.99, 'Stock Availability': 15}, {'Product': 'Jeans', 'Price': 13.99, 'Stock Availability': 8}, {'Product': 'Watch', 'Price': 99.99, 'Stock Availability': 4}, {'Product': 'Sweater', 'Price': 29.99, 'Stock Availability': 11}]
"""


print(json_data[0])
# [
print(readable_data[0])
# {'Product': 'T-shirt', 'Price': 5.99, 'Stock Availability': 15}


print(readable_data[0]["Product"])
# T-shirt

print(readable_data[2]["Price"])

# 9.99
print(readable_data[3]["Stock Availability"])
# 11
```

**Serializing JSON:**

The process of encoding JSON is usually called **serialization**. This term refers to the transformation of data into a series of bytes (hence serial) to be stored or transmitted across a network. To handle the data flow in a file, the JSON library in Python uses dump() function to convert the Python objects into their respective JSON object, so it makes it easy to write data to files. See the following table given below.

| Python object    | JSON object |
| ---------------- | ----------- |
| dict             | object      |
| list, tuple      | array       |
| str              | string      |
| int, long, float | numbers     |
| True             | true        |
| False            | false       |
| None             | null        |

###### Example 3: Serialization

```python
var = {
      "Subjects": {
                  "Maths":85,
                  "Physics":90
                   }
      }



with open("Sample.json", "w") as p:
     json.dump(var, p)


# Here, the dump() takes two arguments 
# first, the data object to be serialized, 
# and second the object to which it will be written(Byte format). 
```

##### Links:

1. [JSON.org](json.org)

2. [RFC 4627](https://www.ietf.org/rfc/rfc4627.txt)

3. [Wikipedia](https://en.wikipedia.org/wiki/JSON)

4. [Python Docs]([json — JSON encoder and decoder &#8212; Python 3.11.2 documentation](https://docs.python.org/3/library/json.html))

5. [GeekForGeeks](https://www.geeksforgeeks.org/python-json/)

6. [Real Python](https://realpython.com/python-json/)

7. [JSON Formatter](https://jsonformatter.curiousconcept.com/)

##### Books

1. Beginning JSON by Ben Smith, Apress 2015, ISBN: 9781484202029, 1484202023

2. JSON at Work - Practical Data Integration for the Web by Tom Marrs, O'Reilly Media 2017, ISBN: 9781491982419, 1491982411

### SQLite Database

**Python SQLite3** module is used to integrate the SQLite database with Python. It is a standardized Python DBI API 2.0 and provides a straightforward and simple-to-use interface for interacting with SQLite databases. There is no need to install this module separately as it comes along with Python after the 2.5x version.

###### Example 1:

Importing librarie(s) and variable(s) for examples:

```python
import sqlite3
import json
from pathlib import Path


products = json.loads(Path("ecommerce/products.json").read_text())

print(products)
"""
[{'Product': 'T-shirt', 'Price': 5.99, 'Stock Availability': 15}, {'Product': 'Jeans', 'Price': 13.99, 'Stock Availability': 8}, {'Product': 'Watch', 'Price': 99.99, 'Stock Availability': 4}, {'Product': 'Sweater', 'Price': 29.99, 'Stock Availability': 11}]
"""

print(type(products))
# <class 'list'>
```

Creating table in database:

```python
with sqlite3.connect("products-db.sqlite3") as connection:
    command = '''
        CREATE TABLE "Products" (
            "Product"    TEXT,
            "Price"    INTEGER,
            "Stock Availability"    INTEGER
        );
    '''
    try:
        connection.execute(command)
    except sqlite3.OperationalError as db_error:
        print(db_error)

    connection.commit()
```

Writing to a database:

```python
with sqlite3.connect("products-db.sqlite3") as connection:
    command = "INSERT INTO Products VALUES(?, ?, ?)"

    for product in products:
        connection.execute(command, tuple(product.values()))

    connection.commit()
```

Reading from database:

```python
with sqlite3.connect("products-db.sqlite3") as connection:
    command = "SELECT * FROM Products"

    cursor = connection.execute(command)

    i = 1
    for data_row in cursor:
        print(f"row {i}:", end=" ")
        print(data_row)
        i += 1
```

##### Links:

1. [Python docs](https://docs.python.org/3/library/sqlite3.html)

2. [PEP 249 – Python Database API Specification v2.0 | peps.python.org](https://peps.python.org/pep-0249/)

3. [GeeksforGeeks](https://www.geeksforgeeks.org/python-sqlite/)

4. [Data Management With Python, SQLite, and SQLAlchemy – Real Python](https://realpython.com/python-sqlite-sqlalchemy/)

##### Books:

1. The Definitive Guide to SQLite by Michael Owens & Mike Owens, Apress 2006, ISBN: 9781430201724, 143020172X

2. SQLite Database System Design and Implementation (Second Edition, Version 2) by Sibsankar Haldar, 2016

3. Using SQLite by Jay A. Kreibich, O'Reilly Media 2010, ISBN: 9781449399641, 1449399649

### Working with Random Values

Python **Random module** is an in-built module of Python which is used to generate random numbers. These are pseudo-random numbers means these are not truly random. This module can be used to perform random actions such as generating random numbers, print random a value for a list or string, etc.

```python
import random
```

###### Example 1: between zero & one

```python
print(random.random())
# 0.18604719590476015
# 0.029440582890317923
# 0.33253447404522574
```

###### Example 2: between two arbitary numbers

```python
print(random.randint(1, 50))
# 48
# 35
# 2
```

###### Example 3: randomly choosing a list item

```python
print(random.choice([1, 3, 6, 87, 89, 2]))
# 6
# 1
# 87
```

###### Example 4: randomly choosing multiple list items

```python
print(random.choices([1, 3, 6, 87, 89, 2, 54, 92, 390, 7, 10], k=2))
# [1, 3]
# [54, 54]
# [3, 390]
```

###### Example 5: shuffling a list

```python
numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]

random.shuffle(numbers)

print(numbers)
# [10, 1, 2, 5, 6, 3, 7, 4, 9, 8]
# [2, 9, 7, 6, 8, 5, 10, 1, 4, 3]
# [6, 3, 5, 10, 2, 7, 8, 1, 4, 9]
```

<table><thead><tr><th>Function Name</th><th>Description</th></tr></thead><tbody><tr><td><a href="https://www.geeksforgeeks.org/random-seed-in-python/">seed()</a></td><td>Initialize the random number generator</td></tr><tr><td><a href="https://www.geeksforgeeks.org/random-getstate-in-python/">getstate()</a></td><td>Returns an object with the current internal state of the random number generator</td></tr><tr><td><a href="https://www.geeksforgeeks.org/random-setstate-in-python/">setstate()</a></td><td>Used to restore the state of the random number generator back to the specified state</td></tr><tr><td><a href="https://www.geeksforgeeks.org/random-getrandbits-in-python/">getrandbits()</a></td><td>Return an integer with a specified number of bits</td></tr><tr><td><a href="https://www.geeksforgeeks.org/randrange-in-python/">randrange()</a></td><td>Returns a random number within the range</td></tr><tr><td><a href="https://www.geeksforgeeks.org/python-randint-function/">randint()</a></td><td>Returns a random integer within the range</td></tr><tr><td><a href="https://www.geeksforgeeks.org/python-numbers-choice-function/">choice()</a></td><td>Returns a random item from a list, tuple, or string</td></tr><tr><td><a href="https://www.geeksforgeeks.org/random-choices-method-in-python/">choices()</a></td><td>Returns multiple random elements from the list with replacement</td></tr><tr><td><a href="https://www.geeksforgeeks.org/python-random-sample-function/">sample()</a></td><td>Returns a particular length list of items chosen from the sequence</td></tr><tr><td><a href="https://www.geeksforgeeks.org/random-random-function-in-python/">random()</a></td><td>Generate random floating numbers</td></tr><tr><td><a href="https://www.geeksforgeeks.org/python-number-uniform-method/">uniform()</a></td><td>Return random floating number between two numbers both inclusive</td></tr><tr><td><a href="https://www.geeksforgeeks.org/random-triangular-method-in-python/">triangular()</a></td><td>Return a random floating point number within a range with a bias towards one extreme</td></tr><tr><td><a href="https://www.geeksforgeeks.org/random-betavariate-method-in-python/">betavariate()</a></td><td>Return a random floating point number with beta distribution</td></tr><tr><td><a href="https://www.geeksforgeeks.org/random-expovariate-function-in-python/">expovariate()</a></td><td>Return a random floating point number with exponential distribution</td></tr><tr><td><a href="https://www.geeksforgeeks.org/random-gammavariate-function-in-python/">gammavariate()</a></td><td>Return a random floating point number with gamma distribution</td></tr><tr><td><a href="https://www.geeksforgeeks.org/random-gauss-function-in-python/">gauss()</a></td><td>Return a random floating point number with Gaussian distribution</td></tr><tr><td><a href="https://www.geeksforgeeks.org/random-lognormvariate-function-in-python/">lognormvariate()</a></td><td>Return a random floating point number with log-normal distribution</td></tr><tr><td><a href="https://www.geeksforgeeks.org/random-normalvariate-function-in-python/">normalvariate()</a></td><td>Return a random floating point number with normal distribution</td></tr><tr><td><a href="https://www.geeksforgeeks.org/random-vonmisesvariate-function-in-python/">vonmisesvariate()</a></td><td>Return a random floating point number with von Mises distribution or circular normal distribution</td></tr><tr><td><a href="https://www.geeksforgeeks.org/random-paretovariate-function-in-python/">paretovariate()</a></td><td>Return a random floating point number with Pareto distribution</td></tr><tr><td><a href="https://www.geeksforgeeks.org/random-weibullvariate-function-in-python/">weibullvariate()</a></td><td>Return a random floating point number with Weibull distribution</td></tr></tbody></table>

##### Links

1. [Python docs](https://docs.python.org/3/library/random.html)

2. [Generating Random Data in Python (Guide) – Real Python](https://realpython.com/python-random/)

3. [Entropy - Wikipedia](https://en.wikipedia.org/wiki/Entropy)

4. [Random number generation - Wikipedia](https://en.wikipedia.org/wiki/Random_number_generation)

##### Books

1. Random Number Generators—Principles and Practices by David Johnston, Deg Press 2018, ISBN: 9781501506062, 1501506064

2. Random Numbers and Computers by Ronald T. Kneusel, Springer International Publishing 2018, ISBN: 9783319776972, 3319776975

3. Random Number Generation and Monte Carlo Methods by James E. Gentle, Springer New York 2006, ISBN: 9780387216102, 0387216103

### Working with the Browser

In Python, **webbrowser module** is a convenient web browser controller. It provides a high-level interface that allows displaying Web-based documents to users. 

webbrowser can also be used as a CLI tool. It accepts a URL as the argument with the following optional parameters: -n opens the URL in a new browser window, if possible, and -t opens the URL in a new browser tab.

```bash
python -m webbrowser -t "https://www.python.org"
```

```python
import webbrowser

webbrowser.open("http://google.com")
# This opens the requested page using the default browser.
```



##### Links:

1. [Python Docs](https://docs.python.org/3/library/webbrowser.html)
   
   