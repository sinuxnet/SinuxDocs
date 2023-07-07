## 18 - Advanced Python – Modules

### Introduction to Modules

**Modular programming** refers to the process of breaking a large, unwieldy programming task into separate, smaller, more manageable subtasks or **modules**. Individual modules can then be cobbled together like building blocks to create a larger application.

There are several advantages to **modularizing** code in a large application:

- **Simplicity:** Rather than focusing on the entire problem at hand, a module typically focuses on one relatively small portion of the problem. If you’re working on a single module, you’ll have a smaller problem domain to wrap your head around. This makes development easier and less error-prone.

- **Maintainability:** Modules are typically designed so that they enforce logical boundaries between different problem domains. If modules are written in a way that minimizes interdependency, there is decreased likelihood that modifications to a single module will have an impact on other parts of the program. (You may even be able to make changes to a module without having any knowledge of the application outside that module.) This makes it more viable for a team of many programmers to work collaboratively on a large application.

- **Reusability:** Functionality defined in a single module can be easily reused (through an appropriately defined interface) by other parts of the application. This eliminates the need to duplicate code.

- **Scoping:** Modules typically define a separate **namespace**, which helps avoid collisions between identifiers in different areas of a program

**Functions**, **modules** and **packages** are all constructs in Python that promote code modularization.

There are actually three different ways to define a **module** in Python:

1. A module can be written in Python itself.
2. A module can be written in **C** and loaded dynamically at run-time, like the `re` (**regular expression**) module.
3. A **built-in** module is intrinsically contained in the interpreter, like the `itertools` module.

A Python module is a file containing Python definitions and statements. A module can define functions, classes, and variables. A module can also include runnable code. Grouping related code into a module makes the code easier to understand and use. It also makes the code logically organized.

We can import the functions, and classes defined in a module to another module using the `import` statement in some other Python source file. 

When the interpreter encounters an `import` statement, it imports the module if the module is present in the search path. A search path is a list of directories that the interpreter searches for importing a module.

`import` in python is similar to #include header_file in C/C++. Python modules can get access to code from another module by importing the file/function using import.

When the import is used, it searches for the module initially in the local scope by calling `__import__()` function. The value returned by the function is then reflected in the output of the initial code.

###### Example 1: Importing one method

**File 1:** user_data.py

```python
def user_info():
    pass


def user_posts():
    pass
```

**File 2:** app.py

```python
from user_data import user_info


user_info()
```

###### Example 2: Importing multiple methods

using previous user_data.py from example 1

**File 2:** app.py

```python
from user_data import user_info, user_posts


user_info()
user_posts()
```

###### Example 3: Accessing through dot operator

using previous user_data.py from example 1

**File 2:** app.py

```python
import user_data


user_info()
user_posts()
```

Read about `__pycache__` folder in this [link]([PEP 3147 – PYC Repository Directories | peps.python.org](https://peps.python.org/pep-3147/)).

### Paths & Packages

When the interpreter executes the `import` statement, it searches for `module_name.py` in a list of directories assembled from the following sources:

- The directory from which the input script was run or the **current directory** if the interpreter is being run interactively
- The list of directories contained in the [`PYTHONPATH`](https://docs.python.org/3/using/cmdline.html#envvar-PYTHONPATH) environment variable, if it is set. (The format for `PYTHONPATH` is OS-dependent but should mimic the `PATH` environment variable.)
- An installation-dependent list of directories configured at the time Python is installed.

```python
import sys
print(sys.path)

"""
['d:\\OneDrive\\Desktop\\Python', 
 'C:\\Users\\sina\\AppData\\Local\\Programs\\Python\\Python311\\python311.zip',
 'C:\\Users\\sina\\AppData\\Local\\Programs\\Python\\Python311\\Lib', 
 'C:\\Users\\sina\\AppData\\Local\\Programs\\Python\\Python311\\DLLs', 
 'C:\\Users\\sina\\AppData\\Local\\Programs\\Python\\Python311', 
 'C:\\Users\\sina\\AppData\\Local\\Programs\\Python\\Python311\\Lib\\site-packages', 
 'c:\\Users\\sina\\.vscode\\extensions\\almenon.arepl-2.0.5\\node_modules\\arepl-backend\\python']
 """
```

Python has **packages** for directories and **modules** for files.

Package is any irregular directory with init file in it.

![](D:\OneDrive\z%20-%20My%20Docs\md%20docs\Python%20Bootcamp%202022%20-%20Muslim%20Helalee\images\packages.jpg)

**File:** Python/actions/user_imgs.py

```python
def img():
    print("User Images")


def media():
    print("User Media")
```

###### Importing Packages: (in app.py)

###### Example 1: Approach 1

```python
import actions.user_imgs


actions.user_imgs.img()         # User Images
actions.user_imgs.media()       # User Media
```

###### Example 2: Approach 2

```python
from actions.user_imgs import img, media


img()       # User Images
media()     # User Media
```

###### Example 3: Approach 3

```python
from actions import user_imgs


user_imgs.img()         # User Images
user_imgs.media()       # User Media
```

### Creating Sub Packages

![](D:\OneDrive\z%20-%20My%20Docs\md%20docs\Python%20Bootcamp%202022%20-%20Muslim%20Helalee\images\sub_packages.jpg)

**File:** Python/actions/videos/user_videos.py

```python
def video():
    print("User videos are stored here.")
```

###### Example 1: Access to sub package

```python
from actions.videos import user_videos


user_videos.video()
# User videos are stored here.
```

### The Built-in `dir()` Method

***dir()*** is a powerful inbuilt function in Python3, which returns list of the attributes and methods of any object (say functions , modules, strings, lists, dictionaries etc.)

dir() tries to return a valid list of attributes of the object it is called upon. Also, dir() function behaves rather differently with different type of objects, as it aims to produce the most relevant one, rather than the complete information.

- For Class Objects, it returns a list of names of all the valid attributes and base attributes as well. 
- For Modules/Library objects, it tries to return a list of names of all the attributes, contained in that module. 
- If no parameters are passed it returns a list of names in the current local scope.

###### Example 1:

```python
from actions.videos import user_videos


print(dir())


"""
['__builtins__', '__doc__', '__file__', '__loader__',
 '__name__', '__package__', 'arepl_store', 'help', 'howdoi',
 'input', 'user_videos']
"""


print(user_videos.__name__)
# actions.videos.user_videos

print(user_videos.__package__)
# actions.videos

print(user_videos.__file__)
# d:\OneDrive\Desktop\Python\Python\actions\videos\user_videos.py
```

**Applications :** 

- The **dir()** has it’s own set of uses. It is usually used for *debugging purposes* in simple day to day programs, and even in large projects taken up by a team of developers. The capability of dir() to list out all the attributes of the parameter passed, is really useful when handling a lot of classes and functions, separately.   
- The **dir()** function can also list out all the available attributes for a module/list/dictionary. So, it also gives us information on the operations we can perform with the available list or module, which can be very useful when having little to no information about the module. It also helps to know new modules faster.
