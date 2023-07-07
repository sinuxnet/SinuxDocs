## Python Loops

### For Loops

**DRY:** Don't Repeat Yourself

**Iterated:** Something that can iterated over,  and itrerable is something that can be counted. 

```python
for number in range(5):    # 0, 1, 2, 3, 4
    print(f"The code has run for {number} time(s)")
```

```python
for a in range(5, 15):    # 5, 6, 7, ..., 13, 14
    print(a)
```

```python
for a in range(0, 100, 10)       # 0, 10, 20, ..., 70, 80, 90
    print(a)
```

```python
status = True

for number in range(1, 4):
    print(f"Attemt {number}")

    if status:
        print("Success")
        break
else:
    print("Failed")
```

## Nested Loops

Using loop inside another loop.

```python
for x in range(3):
    for y in range(6):
        print(f"Point({x}),{y}")
```

```python
for x in range(5):
    for y in range(2):
        for z in range(3):
            print(f"Point({x},{y},{z})")
        print("End of z")
    print("End of y")
print("End of x")
```

## Iterables

range, strings, list and etc are iterable.

```python
print(type(range(5)))    # <class 'range'>
```

```python
for char in "Sina Alikhani"
    print(char)    
```

```python
for something in ["Coffe", "Play with cat", "Walk the dog"]:
    print(something)
```

## While Loops

`while` loops are a different way of iterating over an iterable but the difference is that we are not actually iterating over an iterating like a range object or a string or a list. 

We are evaluating a condition and repeating a task as long as that condition holds true.

```python
temperature = 40

while temperature >= 20:
    print(f"it is a good day to go out when \
the temperature is {temperature}")  
    temperature -= 5
```

### Infinite Loops

Whenever you're creating loops, you hav to be very carefull that you have a starting point and you have an ending point. 

Infinite loops happen whenever you don't have an ending condition.

```python
number = 100
while number > 1:
    print(number)

    number -= 10
```
