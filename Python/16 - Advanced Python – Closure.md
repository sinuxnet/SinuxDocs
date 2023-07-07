## 16 - Advanced Python – Closure

### Introduction to Closure

Before seeing what a closure is, we have to first understand what nested functions and non-local variables are.

A function that is defined inside another function is known as a nested function. Nested functions are able to access variables of the enclosing scope.

In Python, these non-local variables can be accessed only within their scope and not outside their scope.

###### Example 1:

```python
def person(address):

    def john():
        print(address)

    john()


person("USA")
```

###### Example 2: non-local variable

```python
def outer():
    number = 85
    number2 = 100

    def inner():
        nonlocal number

        number = 95
        number2 = 90
        print("inner function var 1: ", number)
        print("inner function var 2:", number2)

    inner()

    print("Outer Function var 1:", number)
    print("Outer Function var 2:", number2)


outer()

"""
inner function var 1:  95
inner function var 2: 90
Outer Function var 1: 95
Outer Function var 2: 100
"""
```

###### Example 3: defining a closure

A Closure is a function object that remembers values in enclosing scopes even if they are not present in memory.

- It is a record that stores a function together with an environment: a mapping associating each free variable of the function (variables that are used locally but defined in an enclosing scope) with the value or reference to which the name was bound when the closure was created.
- A closure—unlike a plain function—allows the function to access those captured variables through the closure’s copies of their values or references, even when the function is invoked outside their scope.

```python
def person(address):

    def john():
        print(address)

    return john


john_address = person("USA")
print(john_address)
# <function person.<locals>.john at 0x000001EBACE804A0>


john_address()  # USA
# person function returns john function (it doesn't execut it)
# the function name itself passes a reference to that that function
```

###### Example 4: deleting the original/enclosing sccope

```python
def person(address):

    def john():
        print(address)

    return john


john_address = person("USA")

del person
# person()    # NameError: name 'person' is not defined


john_address()    # USA
```

### When to use Closure

Closures can be used to avoid global values and provide data hiding, and can be an elegant solution for simple cases with one or few methods.

###### Example 1:

```python
def numbers(n):

    def multiply_by(x):
        return x * n

    return multiply_by


three = numbers(3)
four = numbers(4)
five = numbers(5)
name = numbers("Sina")

print(three)
# <function numbers.<locals>.multiply_by at 0x000001EBACE78360>

print(type(three))
# <class 'function'>

print(three(10))    # 30
print(four(40))     # 160
print(five(50))     # 250


print(numbers.__closure__)
# None

print(three.__closure__)
# (<cell at 0x000001EBACE61E70: int object at 0x00007FF8C42FE368>,)

print(name.__closure__)
# (<cell at 0x000001EBACE54700: str object at 0x000001EBACE84FF0>,)

print(three.__closure__[0].cell_contents)   # 3
print(four.__closure__[0].cell_contents)    # 4
print(five.__closure__[0].cell_contents)    # 5
```
