## Python Logic – Control Flow

### Comparison Operators

We use comparison operator to compare values for different variables. The following camparison operators in this part are actually boolean expressions and produce boolean values.

```python
print(14 > 4)         # True
print(14 >= 4)        # True
print(14 < 4)         # False
print(14 <= 4)        # False
print(14 == 14)       # True
print(14 == "14")     # False
print(14 != "14")     # True
print("cat" > "dog")  # False
print("cat" > "CAT")  # False

print(ord(c))         # 99
print(ord(C))         # 67
print(ord(d))         # 100
print(ord(a))         # 97
print(ord(o))         # 111
print(ord(t))         # 116
print(ord(g))         # 103
```

### Conditional Statements

When the program want to make a decision, we use conditional statements

**syntax:**

`if (boolean expression):`

`    execute the statement`

###### Example 1:

```python
temperature = 35

if temperature > 30:
    print("It is a good day for walking!")

print("It is not part of the if statement.")
```

###### Example 2:

```python
temperature = 29

if temperature > 25:
    print("Awesome!")
else:
    print("Cold")
```

###### Example 3:

```python
temperature = 45

if tempreature >= 35:
    print("Hot")
elif temperature > 25
    print("Awesome")
elif temprature < 20
    print("Cold")
else:
    print("Undecided") 
```

### Ternary Operators

###### 1st version:

```python
score = 74
if score >= 75:
    print("Passed")
else:
    print("Failed")
```

###### 2nd Version:

```python
score = 74
if score >= 75:
    result = "Passed"
else:
    result = "Failed"

print("result")
```

###### 3rd version (with ternary operators)

```python
score = 74
result = "Passed" if score >= 75 else "failed"

print(result)
```

## Logical Operators

1. and

2. or

3. not

###### Example 1 (AND logical operator):

```python
high_income = True
good_credit = False

if high_income and good_credit:
    print("Eligible for loan")
else:
    print("Not eligible for loan")
```

###### Example 2 (OR logical operator):

```python
high_income = False
good_credit = False

if high_income or good_credit:
    print("Eligible for loan")
else:
    print("Not eligible for loan")
```

###### Example 3 (NOT logical operator):

```python
# high_income = True
# good_credit = True
student = False

if not student:
    print("Eligible for loan")
else:
    print("Not eligible for loan")
```
