## 15 - Advanced Python – Generators

### Introdution to Generators

###### When to use yield instead of return in Python?

The `yield` statement suspends a function’s execution and sends a value back to the caller, but retains enough state to enable the function to resume where it left off. When the function resumes, it continues execution immediately after the last `yield` run. This allows its code to produce a series of values over time, rather than computing them at once and sending them back like a list.

`return` sends a specified value back to its caller whereas `yield` can produce a sequence of values. We should use `yield` when we want to iterate over a sequence, but don’t want to store the entire sequence in memory. `yield` is used in Python **generators**. 

| N.O | YIELD                                                                                            | RETURN                                                                                                  |
| --- |:------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------- |
| 1   | Yield is generally used to convert a regular Python function into a generator.                   | Return is generally used for the end of the execution and “returns” the result to the caller statement. |
| 2   | It replace the return of a function to suspend its execution without destroying local variables. | It exits from a function and handing back a value to its caller.                                        |
| 3   | It is used when the generator returns an intermediate result to the caller.                      | It is used when a function is ready to send a value.                                                    |
| 4   | Code written after yield statement execute in next function call.                                | while, code written after return statement wont execute.                                                |
| 5   | It can run multiple times.                                                                       | It only runs single time.                                                                               |
| 6   | Yield statement function is executed from the last state from where the function get paused.     | Every function calls run the function from the start.                                                   |

###### Generator Function

A generator-function is defined like a normal function, but whenever it needs to generate a value, it does so with the `yield` keyword rather than return. If the body of a `def` contains yield, the function automatically becomes a generator function.

Generator functions return a **generator object**. Generator objects are used either by calling the next method on the generator object or using the generator object in a `for in` loop.

So a generator function returns an generator object that is iterable.

###### Application

Suppose we create a stream of Fibonacci numbers, adopting the generator approach makes it trivial; we just have to call next(x) to get the next Fibonacci number without bothering about where or when the stream of numbers ends. A more practical type of stream processing is handling large data files such as log files. Generators provide a space-efficient method for such data processing as only parts of the file are handled at one given point in time. We can also use Iterators for these purposes, but Generator provides a quick way (We don’t need to write __next__ and __iter__ methods here).

###### Example 1:

```python
"""
Normal functions
    1- return
    2- after return, the variables are garbage collected
    3- return terminates function
    4- performs a task or calculates a value

Generator functions
    1- yeild
    2- access to variables after function execution
    3- yield does not terminate a function
    4- return an iterato object
"""


def first_generator():
    x = 1
    print("1st iteration")

    yield x

    x += 1     # x = 2
    print("2nd iteration")

    yield x

    x += 1    # x = 3
    print("1st iteration")

    yield x


my_gen = first_generator()
print(my_gen)  # <generator object first_generator at 0x000001EBACD8D630>
print(type(my_gen))     # <class 'generator'>


print(next(my_gen))
print(next(my_gen))
print(next(my_gen))

# 1st iteration
# 1
# 2nd iteration
# 2
# 1st iteration
# 3

# print(next(my_gen))     # StopIteration
```

###### Example 2: using a `for` loop

```python
def first_generator():
    x = 1
    print("1st iteration")

    yield x

    x += 1.1
    print("2nd iteration")

    yield x

    x += 1.2
    print("1st iteration")

    yield x


for element in first_generator():
    print(element)


# 1st iteration
# 1
# 2nd iteration
# 2.1
# 1st iteration
# 3.3
```

### Generator Expressions

There are various other expressions that can be simply coded similar to list comprehensions but instead of brackets we use parenthesis. These expressions are designed for situations where the generator is used right away by an enclosing function. Generator expression allows creating a generator without a yield keyword. However, it doesn’t share the whole power of the generator created with a yield function.

###### Example 1:

```python
numbers = [1, 2, 11, 9, 5, 2, 0, 12]


# sqauring each item using list comprehension
sqrt_nums_LC = [x**2 for x in numbers]
print(sqrt_nums_LC)
# [1, 4, 121, 81, 25, 4, 0, 144]


# sqauring each item using generator expression
# it has lazy execution
sqrt_nums_GE = (x**2 for x in numbers)

print(next(sqrt_nums_GE))   # 1
print(next(sqrt_nums_GE))   # 2
print(next(sqrt_nums_GE))   # 121
print(next(sqrt_nums_GE))   # 81
print(next(sqrt_nums_GE))   # 25
```

###### Example 2:

```python
numbers = [1, 2, 11, 9, 5, 2, 0, 12, -1]

print(sum(x * 2 for x in numbers))    # 82

print(max(x ** 2 for x in numbers))   # 144

print(min(x for x in numbers))        # -1
```

### Generator Expressions Advantages

1. Memory Efficient

2. Ease of Implementation

3. Representing Infinite Stream

4. Piplining Generators

###### Example 1: Ease of Implemention

```python
def number_power(maxi_num):
    n = 0
    while n <= maxi_num:
        yield 2 ** n
        n += 1


result = number_power(2)
print(next(result))    # 1
print(next(result))    # 2
print(next(result))    # 4
# print(next(result))    # StopIteration
```

###### Example 2: Representing Infinite Stream, Memory Efficeient

**Memory Efficeient:** A normal function to return a sequence will create the entire sequence in memory before returning the result. This is an overkill, if the number of items in the sequence is very large.

Generator implementation of such sequences is memory friendly and is preferred since it only produces one item at a time.

**Representing Infinite Stream:** Generators are excellent mediums to represent an infinite stream of data. Infinite streams cannot be stored in memory, and since generators produce only one item at a time, they can represent an infinite stream of data.

The following generator function can generate all the even numbers (at least in theory).

```python
def even_nums():
    n = 0
    while True:
        yield n

        n += 2


all_even = even_nums()

print(next(all_even))   # 0
print(next(all_even))   # 2
print(next(all_even))   # 4
print(next(all_even))   # 6
print(next(all_even))   # 8
print(next(all_even))   # 10
```

###### Example 3: Pipelining Generators

Multiple generators can be used to pipeline a series of operations. This is best illustrated using an example.

Suppose we have a generator that produces the numbers in the Fibonacci series. And we have another generator for squaring numbers.

If we want to find out the sum of squares of numbers in the Fibonacci series, we can do it in the following way by pipelining the output of generator functions together.

```python
def fibonacci_numbers(nums):
    x, y = 0, 1

    for _ in range(nums):
        x, y = y, x+y

        yield x


fib_nums = fibonacci_numbers(10)
print(next(fib_nums))   # 1
print(next(fib_nums))   # 1
print(next(fib_nums))   # 2
print(next(fib_nums))   # 3
print(next(fib_nums))   # 5
print(next(fib_nums))   # 8


def square(nums):
    for num in nums:
        yield num ** 2


sqrt_nums = square(fibonacci_numbers(10))


print(next(sqrt_nums))  # 1
print(next(sqrt_nums))  # 1
print(next(sqrt_nums))  # 4
print(next(sqrt_nums))  # 9
print(next(sqrt_nums))  # 25
print(next(sqrt_nums))  # 64


print(sum(square(fibonacci_numbers(10))))   # 4895
```
