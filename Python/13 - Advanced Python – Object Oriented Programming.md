## 13 - Advanced Python – Object Oriented Programming

Python is a multi-paradigm programming language. It supports different programming approaches, one of the popular approaches to solve programming problems is by creating **objects**.

This is known as **Object Oriented Programming*** or OOP.

An object which is created is going to have two charachteristic:

1. Attributes

2. behaviour
- Example
  
  - **Object:** robot
  
  - **Attributes:** Name, Model, Size, Color
  
  - **Behaviour:** Walk, Talk, Jump

This concept is also known as **DRY: Don't Repeat Yourself**

### Classes

Classes are a blueprint for creating objects.

One class have many, many objects or instances of that class. From a class we can construct instances. An instance is a specific object created from a particular class.(Object = an Instantiation of class) 

When  a class is defined, only the description for the object is defiend. Therefor, no memory or storage is allocated.

###### Example 1:

```python
class Robot:
    pass


robot_obj = Robot()

print(robot_obj)
# <__main__.Robot object at 0x00000241067BA850>

print(type(robot_obj))
# <class '__main__.Robot'>
```

Whenever we're working with classes in Python, we are not going to employ Snake case naming convention. We're going to use the **Pascal** naming convention.

In Pascal naming convention, if you have one word in class name then capitalize the first letter. If you have more than one word, do not sperate with anything like underscore or whatever, just capitalize the first letter of every word.

###### Example 2:

```python
x = 25
print(type(x))    # <class 'int'>

y = 3.14
print(type(y))    # <class 'float'>

z = True
print(type(z))    # <class 'bool'>

my_list = [1, 2, 4]
print(type(my_list))    # <class 'list'>

my_info = {
    "name": "Tommy",
    "last name": "Shelby"
}
print(type(my_info))    # <class 'dict'>


# 25 is an isntance of 'int' class
```

A class is a blueprint for creating new objects.

Every Object that in Python is created using a class which is a blueprint for objects of that type.

Each of data types are actually an object, and they are instances from their certain class.

### Creating  Classes

###### Example 1:

```python
class Robot:
    def walk(self):
        print("The robot is walking.")


robot = Robot()

robot.walk()            # The robot is walking.
print(type(robot))      # <class '__main__.Robot'>
```

The functions inside any classes must have at least one parameter, and by convention, we call that parameter self. Self is actually a reference to the class we are working with.

Some methods may be inherited from a process called inheritence.

`__main__` called a magic method, and this method refers to the current module that we are working.

The entire file is going to be a module which its name is `main`.

###### Example 2: isinstance()

```python
class Robot:
    def walk(self):
        print("The robot is walking.")


robot = Robot()
print(isinstance(robot, Robot))        # True

robot_obj = Robot()
print(isinstance(robot_obj, Robot))    # True
```

A class can have multiple instances.

### Constructors

`self` represents the instance of the class. By using the `self`  we can access the attributes and methods of the class in python. It binds the attributes with the given arguments.

The reason you need to use self. is because Python does not use the @ syntax to refer to instance attributes. Python decided to do methods in a way that makes the instance to which the method belongs be passed automatically, but not received automatically: the first parameter of methods is the instance the method is called on.

**Constructor:**  Generally used for instantiating an object. The task of constructors is to initialize(assign values) to the data members of the class when an object of the class is created. In Python the `__init__()` method is called the constructor and is always called when an object is created.

###### Example 1:

```python
class Robot:
    def walk(self):
        print("walking")


robot = Robot(2.4, 6.5)
# TypeError: Robot() takes no arguments
```

###### Example 2:

```python
class Robot:
    def __init__(self, x, y):        # Constructor
        pass

    def walk(self):
        print("walking")


robot = Robot(2.4, 6.5)
```

###### Example 3:

```python
class Robot:
    def __init__(self, x, y):
        # Default Value
        # self.x = 10

        self.x = x
        self.y = y

    def walk(self):
        print("walking")


robot = Robot(1.1, 2.1)
robot.walk()
# walking

print(robot.x, " - ", robot.y)
# 1.1  -  2.1
```

###### Example 4:

```python
class Robot:
    def __init__(self, x, y):
        # Default Value
        # self.x = 10

        self.x = x
        self.y = y

    def walk(self):
        print(f"Walking Coordinates ({self.x}, {self.y})")


robot = Robot(1.3, 11.2)
robot.walk()        
```

### Instance Attributes VS  Class Attributes

1. **Instance Attr:** Refers to the kind of attributes thath ar declared in the constructor of a class. They can be acceessed by all the instance of class. These instances are able to also create more attributes.

2. **Class Attributes:** Kind of attributes that are shared for all instances.

###### Example 1: Instance attr

```python
class Robot:
    def __init__(self, x, y):
        self.x = x            # Instance Attributes
        self.y = y            # Instance Attributes

    def walk(self):
        print(f"Walking Coordinates ({self.x}, {self.y})")


# 1st instantiation
test_walk1 = Robot(8.9, 99.7)
test_walk1.walk()
print("x = ", test_walk1.x, ", y= ", test_walk1.y)
# Walking Coordinates (8.9, 99.7)
# x =  8.9 , y=  99.7


# 2nd instantation
test_walk2 = Robot(4.5, 6.7)
test_walk2.walk()
print("x = ", test_walk2.x, ", y= ", test_walk2.y)
# Walking Coordinates (4.5, 6.7)
# x =  4.5 , y=  6.7


# different instantation
test_walk1.z = 2.3
print("z = ", test_walk1.z)
# z =  2.3

print("z = ", test_walk2.z)
# AttributeError: 'Robot' object has no attribute 'z'
```

###### Example 2: class attr

```python
class Robot:

    coordinate_z = 45.87

    def __init__(self, x, y):
        self.x = x
        self.y = y

    def walk(self):
        print(f"Walking Coordinates ({self.x}, {self.y})")


test_walk1 = Robot(8.9, 99.7)
print(test_walk1.coordinate_z)    # 45.87

test_walk2 = Robot(4.5, 6.7)
print(test_walk2.coordinate_z)    # 45.87
```

### Instance Methods VS Class Methods

###### Example 1: instance methods

```python
class Robot:
    def __init__(self, x, y):
        self.x = x
        self.y = y

    def walk(self):
        print(f"Walking coordinates ({self.x}, {self.y})")


test_walk = Robot(1.1, 4.6)
test_walk.walk()                # instance(object) method --> walk()
# Walking coordinates (1.1, 4.6)
```

###### Example 2: class method

```python
class Robot:
    def __init__(self, x, y):
        self.x = x
        self.y = y

    # decorator
    @classmethod
    def specific_coordinate(cls):        # class method
        return cls(3.2, 5.7)

    def walk(self):
        print(f"Walking coordinates ({self.x}, {self.y})")


test_walk = Robot.specific_coordinate()
test_walk.walk()
# Walking coordinates (3.2, 5.7)
```

### Magic Methods

Dunder or magic methods in Python are the methods having two prefix and suffix underscores in the method name. Dunder here means “Double Under (Underscores)”. These are commonly used for operator overloading. Few examples for magic methods are: `__init__, __add__, __len__, __repr__` etc.

Magic methods are not meant to be invoked directly by you, but the invocation happens internally from the class on a certain action. For example, when you add two numbers using the + operator, internally, the `__add__()` method will be called.

###### Example 1:

```python
class Robot:
    def __init__(self, x, y):
        self.x = x
        self.y = y

    def walk(self):
        print(f"Walking coordinates ({self.x}, {self.y})")


test = Robot(0.1, 0.5)
print(test)
# <__main__.Robot object at 0x0000018B86F66390>
print(type(test))
# <class '__main__.Robot'>
```

###### Example 2:

```python
class Robot:
    def __init__(self, x, y):
        self.x = x
        self.y = y

    def __str__(self):
        return f"I am a mgic method a coordinates ({self.x},{self.y})"

    def walk(self):
        print(f"Walking coordinates ({self.x}, {self.y})")


test = Robot(0.1, 0.5)
print(test)
# I am a mgic method a coordinates (0.1,0.5)
print(type(test))
# <class '__main__.Robot'>
```

### Comparing Objects Using Magic Methods

###### Example 1:

```python
class Robot:
    def __init__(self, x, y):
        self.x = x
        self.y = y


test_1 = Robot(4.015, 9.2345)
test_2 = Robot(4.015, 9.2345)

print(test_1 == test_2)     # False

print(id(test_1))           # 1698776381520
print(id(test_2))           # 1698776622800
```

###### Example 2: \_\_eq\_\_()

```python
class Robot:
    def __init__(self, x, y):
        self.x = x
        self.y = y

    def __eq__(self, other):
        return self.x == other.x and self.y == other.y

    def __gt__(self, other):
        return self.x > other.x and self.y > other.y        

    def __lt__(self, other):
        return self.x < other.x and self.y < other.y           

test_1 = Robot(4.015, 9.2345)
test_2 = Robot(4.015, 9.2345)
test_3 = Robot(15, 35)

print(test_1 == test_2)    # True
print(test_3 > test_1)     # True
print(test_3 < test_1)     # False
```

### Arithmetic Operations Using Magic Methods

[A  Guide To Python's Magic Methods](https://rszalski.github.io/magicmethods/)

###### Example 1: \_\_add\_\_()  , \_\_sub\_\_() , \_\_mul\_\_() , \_\_floordiv\_\_()

```python
class Robot:
    def __init__(self, x, y):
        self.x = x
        self.y = y

    def __add__(self, other):
        return f"Coordinates({self.x + other.x}, {self.y + other.y})"

    def __sub__(self, other):
        return f"Coordinates({self.x - other.x}, {self.y - other.y})"

    def __mul__(self, other):
        return f"Coordinates({self.x * other.x}, {self.y * other.y})"

    def __floordiv__(self, other):
        return f"Coordinates({self.x // other.x}, {self.y // other.y})"


test_1 = Robot(20, 5)
test_2 = Robot(10, 2)

print(test_1 + test_2)
# Coordinates(16.12, 9.45)

print(test_1 - test_2)
# Coordinates(10, 3)

print(test_1 * test_2)
# Coordinates(200, 10)

print(test_1 // test_2)
# Coordinates(2, 2)
```

### Custom Containers Part 1

Built-In container types such as lists, dictionary, sets, tuples are useful and suffice for most cases. but what if you want to create your own custom container types.

Example:  you want to keep track of all of your bookmarked web pages in your browser.

###### Example 1: Create a custom container

We're going to get the count of a specific key

```python
class BookmarkedPage:
    def __init__(self):
        self.bookmarks = {}

    def add(self, bookmark):
        self.bookmarks[bookmark.lower()] = \
            self.bookmarks.get(bookmark.lower(), 0) + 1
#        self.bookmarks[bookmark] = self.bookmarks.get(bookmark, 0) + 1


target_bookmark = BookmarkedPage()

target_bookmark.add("python")
target_bookmark.add("python")
target_bookmark.add("python")
target_bookmark.add("Python")

print(target_bookmark.bookmarks)
# # # {'python': 3, 'Python': 1}
# {'python': 4}
```

###### Example 2: \_\_getitem\_\_()

```python
class BookmarkedPage:
    def __init__(self):
        self.bookmarks = {}

    def add(self, bookmark):
        self.bookmarks[bookmark.lower()] = \
            self.bookmarks.get(bookmark.lower(), 0) + 1

    def __getitem__(self, bookmark):
        return self.bookmarks.get(bookmark.lower(), 0)


target_bookmark = BookmarkedPage()

target_bookmark.add("python")
target_bookmark.add("python")
target_bookmark.add("python")
target_bookmark.add("Python")
target_bookmark.add("python")
target_bookmark.add("Python")

print(target_bookmark.bookmarks)        # {'python': 6}
print(target_bookmark["python"])        # 6
```

###### Example 3: \_\_setitem\_\_() : setting the number of bookmark types

```python
class BookmarkedPage:
    def __init__(self):
        self.bookmarks = {}

    def add(self, bookmark):
        self.bookmarks[bookmark.lower()] = \
            self.bookmarks.get(bookmark.lower(), 0) + 1

    def __getitem__(self, bookmark):
        return self.bookmarks.get(bookmark.lower(), 0)

    def __setitem__(self, bookmark, count):
        self.bookmarks[bookmark.lower()] = count


target_bookmark = BookmarkedPage()

target_bookmark.add("python")
target_bookmark.add("python")
target_bookmark.add("python")
target_bookmark.add("Python")
target_bookmark.add("python")
target_bookmark.add("Python")

print(target_bookmark.bookmarks)        # {'python': 6}
print(target_bookmark["python"])        # 6

target_bookmark["python"] = 110

print(target_bookmark.bookmarks)        # {'python': 110}
print(target_bookmark["python"])        # 110
```

###### Example 4: \_\_len\_\_() getting number of the bookmark types

```python
class BookmarkedPage:
    def __init__(self):
        self.bookmarks = {}

    def add(self, bookmark):
        self.bookmarks[bookmark.lower()] = \
            self.bookmarks.get(bookmark.lower(), 0) + 1

    def __len__(self):
        return len(self.bookmarks)


target_bookmark = BookmarkedPage()

target_bookmark.add("python")
target_bookmark.add("python")
target_bookmark.add("python")
target_bookmark.add("Python")
target_bookmark.add("python")
target_bookmark.add("Java")
target_bookmark.add("Python")
target_bookmark.add("Python")
target_bookmark.add("GoLang")
target_bookmark.add("GoLang")
target_bookmark.add("Java")
target_bookmark.add("JavaScript")
target_bookmark.add("JavaScript")
target_bookmark.add("C")
target_bookmark.add("Vue")


print(target_bookmark.bookmarks)
# {'python': 7, 'java': 2, 'golang': 2,
# 'javascript': 2, 'c': 1, 'vue': 1}

print(len(target_bookmark))
# 6
```

###### Example 5: \_\_iter\_\_() : iterating over the class

```python
class BookmarkedPage:
    def __init__(self):
        self.bookmarks = {}

    def add(self, bookmark):
        self.bookmarks[bookmark.lower()] = \
            self.bookmarks.get(bookmark.lower(), 0) + 1

    def __iter__(self):
        return iter(self.bookmarks)


target_bookmark = BookmarkedPage()

target_bookmark.add("python")
target_bookmark.add("python")
target_bookmark.add("python")
target_bookmark.add("Python")
target_bookmark.add("python")
target_bookmark.add("Java")
target_bookmark.add("Python")
target_bookmark.add("Python")
target_bookmark.add("GoLang")
target_bookmark.add("GoLang")
target_bookmark.add("Java")
target_bookmark.add("JavaScript")
target_bookmark.add("JavaScript")
target_bookmark.add("C")
target_bookmark.add("Vue")

print(target_bookmark.bookmarks)
# {'python': 7, 'java': 2, 'golang': 2,
#  'javascript': 2, 'c': 1, 'vue': 1}

for bookmark in target_bookmark:
    print(bookmark)

# python
# java
# golang
# javascript
# c
# vue
```

###### Example 6: blocking a dict key access from outside

Python doesn't have any mechanism that effectively restricts access to any instance variable or method. Python prescribes a convention of prefixing the name of the variable/method with a single or double underscore to emulate the behavior of protected and private access specifiers.

The double underscore `__` prefixed to a variable makes it **private**. It gives a strong suggestion not to touch it from outside the class.

```python
class BookmarkedPage:
    def __init__(self):
        self.__bookmarks = {}

    def add(self, bookmark):
        self.__bookmarks[bookmark.lower()] = \
            self.__bookmarks.get(bookmark.lower(), 0) + 1

    def __getitem__(self, bookmark):
        return self.__bookmarks.get(bookmark.lower(), 0)

    def __iter__(self):
        return iter(self.__bookmarks)


target_bookmark = BookmarkedPage()

target_bookmark.add("python")
target_bookmark.add("python")
target_bookmark.add("python")
target_bookmark.add("Python")
target_bookmark.add("python")
target_bookmark.add("Java")
target_bookmark.add("Python")
target_bookmark.add("Python")
target_bookmark.add("GoLang")
target_bookmark.add("GoLang")
target_bookmark.add("Java")
target_bookmark.add("JavaScript")
target_bookmark.add("JavaScript")
target_bookmark.add("C")

# Befor converting bookmark to a private member of class
# print(target_bookmark["PYTHON"])       # 7
# print(target_bookmark.bookmarks["python"]) # 7
# print(target_bookmark.bookmarks["PYTHON"]) # KeyError: 'PYTHON'

# We don't have a key by the name "PYTHON"
# PROBLEM: the class allows to
#           access the underlaying dictionary

# After converting bookmark to a private member of class

print(target_bookmark.bookmarks)
print(target_bookmark.__bookmarks)
# AttributeError:
# 'BookmarkedPage' object has no attribute 'bookmarks'
```

###### Example 6:accessing a blocked dict from outside

```python
class BookmarkedPage:
    def __init__(self):
        self.__bookmarks = {}

    def add(self, bookmark):
        self.__bookmarks[bookmark.lower()] = \
            self.__bookmarks.get(bookmark.lower(), 0) + 1

    def __getitem__(self, bookmark):
        return self.__bookmarks.get(bookmark.lower(), 0)

    def __iter__(self):
        return iter(self.__bookmarks)


target_bookmark = BookmarkedPage()

target_bookmark.add("python")
target_bookmark.add("python")
target_bookmark.add("python")
target_bookmark.add("Python")
target_bookmark.add("python")
target_bookmark.add("Java")
target_bookmark.add("Python")
target_bookmark.add("Python")
target_bookmark.add("GoLang")
target_bookmark.add("GoLang")
target_bookmark.add("Java")
target_bookmark.add("JavaScript")
target_bookmark.add("JavaScript")
target_bookmark.add("C")


print(target_bookmark.__dict__)
# {'_BookmarkedPage__bookmarks':
#   {'python': 7, 'java': 2, 'golang': 2, 'javascript': 2, 'c': 1}}

print(target_bookmark._BookmarkedPage__bookmarks)
# {'python': 7, 'java': 2, 'golang': 2,
#  'javascript': 2, 'c': 1}
```

### Class Property & Property Decorator

**Python property() function** returns the object of the property class and it is used to create property of a class. 

> **Syntax:** property(fget, fset, fdel, doc)
> 
> **Parameters:** 
> 
> - **fget()** – used to get the value of attribute
> - **fset()** – used to set the value of attribute
> - **fdel()** – used to delete the attribute value
> - **doc()** – string that contains the documentation (docstring) for the attribute
> - 

Python’s [`property()`](https://docs.python.org/3/library/functions.html#property) is the Pythonic way to avoid formal getter and setter methods in your code. This function allows you to turn class attributes into **properties** or **managed attributes**. Since `property()` is a built-in function, you can use it without importing anything. Additionally, `property()` was implemented in C to ensure optimal performance.

**Note:** It’s common to refer to `property()` as a built-in function. However, `property` is a class designed to work as a function rather than as a regular class. That’s why most Python developers call it a function. That’s also the reason why `property()` doesn’t follow the Python convention for naming classes.

Properties are **class attributes** that manage **instance attributes**.

###### Example 1:

```python
class MovieRating:
    def __init__(self, rating):
        self.set_rating(rating)

    def get_rating(self):
        return self.__rating

    def set_rating(self, value):
        if value < 0:
            raise ValueError("Movie ratings can not be\
 zero or less than zero ")
        self.__rating = value


movie_rating = MovieRating(-10)
# ValueError: Movie ratings can not be zero or less than zero
```

This code is not a pythonic code.

###### Example 2:

```python
class MovieRating:
    def __init__(self, rating):
        self.set_rating(rating)

    def get_rating(self):
        return self.__rating

    def set_rating(self, value):
        if value < 0:
            raise ValueError("Movie ratings can not be \
zero or less than zero ")
        self.__rating = value

    rating = property(get_rating, set_rating)


movie_rating = MovieRating(8)

print(movie_rating.rating)      # 8
```

###### Example 3:

The main work of decorators is they are used to add functionality to the existing code. Also called metaprogramming, as a part of the program tries to modify another part of the program at compile time.

```python
class MovieRating:
    def __init__(self, rating):
        self.__rating = rating

    @property
    def rating(self):
        return self.__rating

    @rating.setter
    def set_rating(self, value):
        if value < 0:
            raise ValueError("Movie ratings can not be \
zero or less than zero ")
        self.__rating = value


movie_rating = MovieRating(8)
print(movie_rating.rating)      # 8
```

### Inheritance

One of the core concepts in object-oriented programming (OOP) languages is inheritance. It is a mechanism that allows you to create a hierarchy of classes that share a set of properties and methods by deriving a class from another class. Inheritance is the capability of one class to derive or inherit the properties from another class. 

## Benefits of inheritance are:

- It represents real-world relationships well.
- It provides the **reusability** of a code. We don’t have to write the same code again and again. Also, it allows us to add more features to a class without modifying it.
- It is transitive in nature, which means that if class B inherits from another class A, then all the subclasses of B would automatically inherit from class A.
- Inheritance offers a simple, understandable model structure. 
- Less development and maintenance expenses result from an inheritance. 

### Python Inheritance Syntax

> Class BaseClass:
>     {Body}
> Class DerivedClass(BaseClass):
>     {Body}

###### Example 1:

```python
# class john:
#     def sing(self):
#         print("Singing")

#     def run(self):
#         print("Running")

# class jane:
#     def sing(self):
#         print("Singing")

#     def jog(self):
#         print("Jogging")


class Person:
    def sing(self):
        print("Singing")


class John(Person):
    def run(self):
        print("Running")


class Jane(Person):
    def jog(self):
        print("Jogging")


runner = John()
runner.sing()        # Singing

jogger = Jane()
jogger.sing         # Singing
```

###### Example 2: attribute inheritance

```python
class Person:
    def __init__(self):
        self.employed = True

    def sing(self):
        print("Singing")


class John(Person):
    def run(self):
        print("Running")


class Jane(Person):
    def jog(self):
        print("Jogging")


runner = John()
runner.empolyed    
```

### The Object Class

In Python3, all classes implicitly inherit from the built-in `object` base class. The `object` class provides some common methods, such as `__init__`, `__str__`, and `__new__`, that can be overridden by the child class.

###### Example 1:

```python
class Person:
    def __init__(self):
        self.employed = True

    def sing(self):
        print("Singing")


class John(Person):
    def run(self):
        print("Running")


class Jane(Person):
    def jog(self):
        print("Jogging")


runner = John()

# to find out if an object is an instance of a class
print(isinstance(runner, John))         # True
print(isinstance(runner, Person))       # True
print(isinstance(Person, object))       # True


base_object = object()


# to find out if a class inherits from another class
print(issubclass(John, object))         # True
```

### Method Overriding

Method overriding is an ability of any object-oriented programming language that allows a subclass or child class to provide a specific implementation of a method that is already provided by one of its super-classes or parent classes. When a method in a subclass has the same name, same parameters or signature and same return type(or sub-type) as a method in its super-class, then the method in the subclass is said to **override** the method in the super-class.

![](D:\OneDrive\z%20-%20My%20Docs\md%20docs\Python%20Bootcamp%202022%20-%20Muslim%20Helalee\images\overriding-in-python.png)

###### Example 1:

```python
class Person:
    def __init__(self):
        self.employed = True

    def sing(self):
        print("Singing")


class John(Person):
    # Method Overriding
    def __init__(self):
        self.jogger = True

    def run(self):
        print("Running")


runner = John()

print(runner.jogger)        # True
print(runner.employed)
# AttributeError: 'John' object has no attribute 'employed'
```

###### Example 2: supermethod

```python
class Person:
    def __init__(self):
        self.employed = False
        print("Base Class")

    def sing(self):
        print("Singing")


class John(Person):
    # Method Overriding
    def __init__(self):
        super().__init__()
        self.jogger = True
        print("Sub Class")

    def run(self):
        print("Running")


runner = John()
# Base Class
# Sub Class

print(runner.jogger)        # True
print(runner.employed)      # Flase
```

###### Example 3:

```python
class Person:
    def __init__(self):
        self.employed = False
        print("Base Class")

    def sing(self):
        print("Singing")


class John(Person):
    # Method Overriding
    def __init__(self):
        self.jogger = True
        print("Sub Class")
        super().__init__()

    def run(self):
        print("Running")


runner = John()
# Sub Class
# Base Class

print(runner.jogger)        # True
print(runner.employed)      # Flase
```

### Multiple Inheritence

Inheritance is the mechanism to achieve the re-usability of code as one class(child class) can derive the properties of another class(parent class). It also provides transitivity ie. if class C inherits from P then all the sub-classes of C would also inherit from P.

**Multiple Inheritance** 
When a class is derived from more than one base class it is called multiple Inheritance. The derived class inherits all the features of the base case.

![](D:\OneDrive\z%20-%20My%20Docs\md%20docs\Python%20Bootcamp%202022%20-%20Muslim%20Helalee\images\multipleinh.png)

**Syntax:**

> Class Base1:
>        Body of the class
> Class Base2:
>      Body of the class
> Class Derived(Base1, Base2):
>      Body of the class

###### Example 1:

```python
class Person:
    def sport_status(self):
        print("Runner")


class John:
    def sport_status(self):
        print("Jogger")


class Jane(Person, John):
    pass


class Mark(John, Person):
    pass


jane = Jane()
jane.sport_status()     # Runner


mark = Mark()
mark.sport_status()     # Jogger
```

###### Example 2:

```python
class Person:
    def runner(self):
        print("Runner")


class John:
    def jogger(self):
        print("Jogger")


class Jane(Person, John):
    pass


jane = Jane()
jane.runner()       # Runner
jane.jogger()       # Jogger
```

### Data Classes

A data class is a regular Python class. The only thing that sets it apart is that it has basic data model methods like `.__init__()`, `.__repr__()`, and `.__eq__()` implemented for you.

###### Example 1:

```python
class Robot:
    def __init__(self, x, y):
        self.x = x
        self.y = y


robot1 = Robot(1, 2)
robot2 = Robot(1, 2)


print(robot1 == robot2)     # False
print(id(robot1))           # 2124770302480
print(id(robot2))           # 2124770309072
```

###### Example 2: \_\_eq\_\_()

```python
class Robot:
    def __init__(self, x, y):
        self.x = x
        self.y = y

    def __eq__(self, other):
        return self.x == other.x and self.y == other.y


robot1 = Robot(1, 2)
robot2 = Robot(1, 2)


print(robot1 == robot2)     # True
print(id(robot1))           # 2124769250896
print(id(robot2))           # 2124769979088
```

###### Example 3: namedtuple()

Python supports a type of container dictionaries called “**namedtuple()**” present in the module, **collections**. Like dictionaries, they contain keys that are hashed to a particular value. But on contrary, it supports both access from key-value and iteration, the functionality that dictionaries lack.

```python
from collections import namedtuple

Robot = namedtuple("Robot", ["x", "y"])

robot1 = Robot(x=1, y=2)
robot2 = (1, 2)

print(robot1 == robot2)     # True
```
