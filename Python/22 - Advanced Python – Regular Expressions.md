## 22 - Advanced Python – Regular Expressions

### Introduction to Regualr Expression

###### Example 1:

```python
import re

# . all the characters

# Example 1
str1 = "ten"
str2 = "cat"
pattern = ".a."


print(re.match(pattern, str1))
# None

print(re.match(pattern, str2))
# <re.Match object; span=(0, 3), match='tan'>
```

### Understanding Regular Expressions

metacharacter

###### Example 2: `[]`  Square brackets

a set of characters you wish to match 

```python
import re

# 1
match_result = re.finditer("[abc]", "abc de ca")
for match in match_result:
    print(match)
"""
<re.Match object; span=(0, 1), match='a'>
<re.Match object; span=(1, 2), match='b'>
<re.Match object; span=(2, 3), match='c'>
<re.Match object; span=(7, 8), match='c'>
<re.Match object; span=(8, 9), match='a'>
"""


# 2
match_result = re.finditer("[a-e]", "cat elephent")
for match in match_result:
    print(match)
"""
<re.Match object; span=(0, 1), match='c'>
<re.Match object; span=(1, 2), match='a'>
<re.Match object; span=(4, 5), match='e'>
<re.Match object; span=(6, 7), match='e'>
<re.Match object; span=(9, 10), match='e'>
"""


# 3
match_result = re.finditer("[0-2]", "88 99 11 22 10")
for match in match_result:
    print(match)

"""
<re.Match object; span=(6, 7), match='1'>
<re.Match object; span=(7, 8), match='1'>
<re.Match object; span=(9, 10), match='2'>
<re.Match object; span=(10, 11), match='2'>
<re.Match object; span=(12, 13), match='1'>
<re.Match object; span=(13, 14), match='0'>
"""


# 4
match_result = re.finditer("[^abc]", "abc de ca cat dog elephent")
for match in match_result:
    print(match)
"""
everything that is not abc
"""


# 5
match_result = re.finditer("[^a-e]", "abc de ca cat dog elephent")
for match in match_result:
    print(match)
"""
everything that is not a to b
"""
```

###### Example 2: `.` Period

Any single character except new line character

```python
import re


# 1
match_result = re.finditer(".", "123")
for match in match_result:
    print(match)
"""
<re.Match object; span=(0, 1), match='1'>
<re.Match object; span=(1, 2), match='2'>
<re.Match object; span=(2, 3), match='3'>
"""


# 2
match_result = re.finditer("..", "abc")
for match in match_result:
    print(match)
# <re.Match object; span=(0, 2), match='ab'>


# 3
match_result = re.finditer("..", "cicd")
for match in match_result:
    print(match)
"""
<re.Match object; span=(0, 2), match='ci'>
<re.Match object; span=(2, 4), match='cd'>
"""
```

###### Example 3: `^` Caret

Caret within `[]` is going to look for an **<u>opposite</u>** of whatever it is written next to, but when it is used outside the `[]`, then this symbol is going to  use to chek if a string **<u>starts</u>** within a certain character(s).

```python
import re


# 1
match_result = re.finditer("^a", "a")
for match in match_result:
    print(match)
# <re.Match object; span=(0, 1), match='a'>


# 2
match_result = re.finditer("^ab", "abcdf rtry ab")
for match in match_result:
    print(match)
# <re.Match object; span=(0, 2), match='ab'>


# 3
match_result = re.finditer("^ab", "acdf rtry ab")
for match in match_result:
    print(match)
# No Output
```

###### Example 4: `$` Dollar

The `$` metacharacter is going to check a string **<u>ends</u>** with a certain character or not.

```python
import re


# 1
match_result = re.finditer("a$", "formula")
for match in match_result:
    print(match)
# <re.Match object; span=(6, 7), match='a'>


# 2
match_result = re.finditer("a$", "formulas")
for match in match_result:
    print(match)
# No Output
```

###### Example 5: `*` Star

The `*` metacharacter is going to match **<u>zero or more</u>** occurrences of pattern left to it

```python
import re


# 1
match_result = re.finditer("ma*n", "mn")
for match in match_result:
    print(match)
# <re.Match object; span=(0, 2), match='mn'>


# 2
match_result = re.finditer("ma*n", "man")
for match in match_result:
    print(match)
# <re.Match object; span=(0, 3), match='man'>


# 3
match_result = re.finditer("ma*n", "maaaaaaaan")
for match in match_result:
    print(match)
# <re.Match object; span=(0, 10), match='maaaaaaaan'>


# 4
match_result = re.finditer("ma*n", "main")
for match in match_result:
    print(match)
# No Output


# 5
match_result = re.finditer("ma*n", "woman")
for match in match_result:
    print(match)
# <re.Match object; span=(2, 5), match='man'>
```

###### Example 6: `+` Plus

It is like the `*` metacharacter but the `+` is going to match **<u>one or more</u>** character(s). 

```python
import re


# 1
match_result = re.finditer("ma+n", "mn")
for match in match_result:
    print(match)
# No Output


# 2
match_result = re.finditer("ma+n", "man")
for match in match_result:
    print(match)
# <re.Match object; span=(0, 3), match='man'>


# 3
match_result = re.finditer("ma+n", "maaaan")
for match in match_result:
    print(match)
# <re.Match object; span=(0, 6), match='maaaan'>


# 4
match_result = re.finditer("ma+n", "main")
for match in match_result:
    print(match)
# No Output


# 5
match_result = re.finditer("ma+n", "womaan")
for match in match_result:
    print(match)
# <re.Match object; span=(2, 6), match='maan'>
```

###### Example 7: `?` Question Mark

The `?` metacharacter is going to match **<u>zero or one</u>** occurrence.

```python
import re


# 1
match_result = re.finditer("ma?n", "mn")
for match in match_result:
    print(match)
# <re.Match object; span=(0, 2), match='mn'>


# 2
match_result = re.finditer("ma?n", "man")
for match in match_result:
    print(match)
# N<re.Match object; span=(0, 3), match='man'>


# 3
match_result = re.finditer("ma?n", "maan")
for match in match_result:
    print(match)
# No Output


# 4
match_result = re.finditer("ma?n", "maaan")
for match in match_result:
    print(match)
# No Output


# 5
match_result = re.finditer("ma?n", "main")
for match in match_result:
    print(match)
# No Output


# 6
match_result = re.finditer("ma?n", "woman")
for match in match_result:
    print(match)
# <re.Match object; span=(2, 5), match='man'>
```

###### Example 8: `{}` Braces

The `{}` actually represents a range kind of situation. We are going to look for an <u>**at least number of occurrences to at most number of occurrences**</u> (min to max). 

```python
import re


# 1
match_result = re.finditer("a{2,4}", "abc dat")
for match in match_result:
    print(match)
# No Output


# 2
match_result = re.finditer("a{2,4}", "abc daat")
for match in match_result:
    print(match)
# <re.Match object; span=(5, 7), match='aa'>


# 3
match_result = re.finditer("a{2,4}", "aabc daaat caaaaaaat")
for match in match_result:
    print(match)
"""
<re.Match object; span=(0, 2), match='aa'>
<re.Match object; span=(6, 9), match='aaa'>
<re.Match object; span=(12, 16), match='aaaa'>
<re.Match object; span=(16, 19), match='aaa'>
"""


# 4
match_result = re.finditer("[0-9]{2,4}", "aabc 123 def ghi 45")
for match in match_result:
    print(match)
"""
<re.Match object; span=(5, 8), match='123'>
<re.Match object; span=(17, 19), match='45'>
"""


# 5
match_result = re.finditer("[0-9]{2,4}", "12 345 60893 34564 344 5")
for match in match_result:
    print(match)
"""
<re.Match object; span=(0, 2), match='12'>
<re.Match object; span=(3, 6), match='345'>
<re.Match object; span=(7, 11), match='6089'>
<re.Match object; span=(13, 17), match='3456'>
<re.Match object; span=(19, 22), match='344'>
"""
```

###### Example 9: `|`  Alternation

The alternation or the `|`  metacharacter is like the `OR` operator.  

```python
import re


# 1
match_result = re.finditer("a|b", "adc")
for match in match_result:
    print(match)
# <re.Match object; span=(0, 1), match='a'>


# 2
match_result = re.finditer("z|c", "adc")
for match in match_result:
    print(match)
# <re.Match object; span=(2, 3), match='c'>


# 3
match_result = re.finditer("z|c", "zzc")
for match in match_result:
    print(match)
"""
<re.Match object; span=(0, 1), match='z'>
<re.Match object; span=(1, 2), match='z'>
<re.Match object; span=(2, 3), match='c'>
"""


# 4
match_result = re.finditer("z|c|t", "zzcctv")
for match in match_result:
    print(match)
"""
<re.Match object; span=(0, 1), match='z'>
<re.Match object; span=(1, 2), match='z'>
<re.Match object; span=(2, 3), match='c'>
<re.Match object; span=(3, 4), match='c'>
<re.Match object; span=(4, 5), match='t'>
"""
```

###### Example 10: `()` Group

Grouping is used to group sub patterns. If you have more than one pattern, you can use the grouping to group them.

```python
import re


# 1
match_result = re.finditer("(a|b)xz", "abc xz abxz cxz")
for match in match_result:
    print(match)
# <re.Match object; span=(8, 11), match='bxz'>


# 2
match_result = re.finditer("(a|b|c)xz", "abc xz abxz cxz")
for match in match_result:
    print(match)
# <re.Match object; span=(8, 11), match='bxz'>
# <re.Match object; span=(12, 15), match='cxz'>
```

###### Example 11: `\` Backslash

The `\` is not a metacharacter, actually it is **escape character**. 

```python
import re


# 1 (What is problem?)
match_result = re.finditer("^xz", "^xz")
for match in match_result:
    print(match)
# No Output

# 2
match_result = re.finditer("\^xz", "^xz")
for match in match_result:
    print(match)
# <re.Match object; span=(0, 3), match='^xz'>
```

### Regular Expression Methods

###### Example 12: `findall()`

returns a list of strings containing all matches.

```python
# \d ->>> [0-9]
import re

str_1 = "hello 12 hi 65 123 howdy 101 202"
str_2 = "hello"
pattern = "\d+"

result = re.findall(pattern, str_1)
print(result)
# ['12', '65', '123', '101', '202']


result = re.findall(pattern, str_2)
print(result)
# []
```

###### Example 13: `split()`

split given string where there is a match and it returnes a list of strings where the splits have occurred.

```python
import re


str_1 = "hello 12 hi 65 123 howdy 101 202"
pattern = "\d+"

result = re.split(pattern, str_1)
print(result)
# ['hello ', ' hi ', ' ', ' howdy ', ' ', '']
```

###### Example 14: `sub()`

  returnes the string where matched occurrences are replaced wuth the content of the replace variable.

```python
import re


# sub(pattern, replace, string)

str_1 = "abc 12\
    de 23 \n f45 621"
print(str_1)
# abc 12    de 23
#  f45 621

pattern = "\s+"
print(re.findall(pattern, str_1))
# [' ', '    ', ' ', ' \n ', ' ']


replace = ""
str_2 = re.sub(pattern, replace, str_1)
print(str_2)
# abc12de23f45621
```

###### Example 15: `sub()`

```python
import re


str_1 = "abc 12\
    de 23 \n f45 621"
pattern = "\s+"
replace = ""

str_2 = re.sub(pattern, replace, str_1)
print(str_2)
# abc12de23f45621

str_3 = re.sub(pattern, replace, str_1, 1)
print(str_3)
# abc12    de 23
#  f45 621

str_4 = re.sub(pattern, replace, str_1, 2)
print(str_4)
# abc12de 23
#  f45 621

str_5 = re.sub(pattern, replace, str_1, 3)
print(str_5)
# abc12de23
#  f45 621

str_6 = re.sub(pattern, replace, str_1, 4)
print(str_6)
# abc12de23f45 621

str_7 = re.sub(pattern, replace, str_1, 5)
print(str_7)
# abc12de23f45621
```

###### Example 16: `subn()`

Same as `sub()` method but it returns a tuple of two items: 1- modified strings 2- number of substitution(s)

```python
import re

str_1 = "abc 12 de 23 f45"
pattern = '\s+'
replace = ""

str_2 = re.subn(pattern, replace, str_1)
print(str_2)
# ('abc12de23f45', 4)
5
```

###### Example 17: `search()`

```python
import re

pattern = 'python'
str_1 = 'python is fun'
str_2 = 'is python fun'


print("search(): ", re.search(pattern, str_1))
# search():  <re.Match object; span=(0, 6), match='python'>

print("match(): ", re.match(pattern, str_1))
# match():  <re.Match object; span=(0, 6), match='python'>

print("search(): ", re.search(pattern, str_2))
# search():  <re.Match object; span=(3, 9), match='python'>

print("match(): ", re.match(pattern, str_2))
# match():  None
```

###### Example 18: `${MATCH}.group()`

```python
import re


str_1 = "12345 67, 789 1122"
pattern = r"(\d{3}) (\d{2})"

result = re.search(pattern, str_1)


if result:
    print(result.group())       # 345 67

    print(result.start())       # 2
    print(result.end())         # 8
    print(result.span())        # (2, 8)
else:
    print("Match not found")
```

### The Raw String

###### Example 19:

```python
str_1 = "\tBook"
str_2 = r"\tBook"

print(str_1)
#     Book

print(str_2)
# \tBook
```

### Special Sequences

###### Example 20: `\d - [0-9]`

```python
import re


results = re.finditer(r"\d", "12 3.4 5 67.9 90")

for result in results: 
    print(result)

# <re.Match object; span=(0, 1), match='1'>
# <re.Match object; span=(1, 2), match='2'>
# <re.Match object; span=(3, 4), match='3'>
# <re.Match object; span=(5, 6), match='4'>
# <re.Match object; span=(7, 8), match='5'>
# <re.Match object; span=(9, 10), match='6'>
# <re.Match object; span=(10, 11), match='7'>
# <re.Match object; span=(12, 13), match='9'>
# <re.Match object; span=(14, 15), match='9'>
# <re.Match object; span=(15, 16), match='0'>
```

###### Example 21: `\D ` = [a-zA-Z_ ] + symbols

```python
import re


results = re.finditer(r"\D", "12 45 # HI There < ? _")

for result in results:
    print(result)
# <re.Match object; span=(2, 3), match=' '>
# <re.Match object; span=(5, 6), match=' '>
# <re.Match object; span=(6, 7), match='#'>
# <re.Match object; span=(7, 8), match=' '>
# <re.Match object; span=(8, 9), match='H'>
# <re.Match object; span=(9, 10), match='I'>
# <re.Match object; span=(10, 11), match=' '>
# <re.Match object; span=(11, 12), match='T'>
# <re.Match object; span=(12, 13), match='h'>
# <re.Match object; span=(13, 14), match='e'>
# <re.Match object; span=(14, 15), match='r'>
# <re.Match object; span=(15, 16), match='e'>
# <re.Match object; span=(16, 17), match=' '>
# <re.Match object; span=(17, 18), match='<'>
# <re.Match object; span=(18, 19), match=' '>
# <re.Match object; span=(19, 20), match='?'>
# <re.Match object; span=(20, 21), match=' '>
# <re.Match object; span=(21, 22), match='_'>
```

###### Example 22: `\s` = (space, tab, " ", "\t", "\n")

```python
import re


results = re.finditer(r"\s", "12 45 # HI \t There \n< ? _")

for result in results:
    print(result)
# <re.Match object; span=(2, 3), match=' '>
# <re.Match object; span=(5, 6), match=' '>
# <re.Match object; span=(7, 8), match=' '>
# <re.Match object; span=(10, 11), match=' '>
# <re.Match object; span=(11, 12), match='\t'>
# <re.Match object; span=(12, 13), match=' '>
# <re.Match object; span=(18, 19), match=' '>
# <re.Match object; span=(19, 20), match='\n'>
# <re.Match object; span=(21, 22), match=' '>
# <re.Match object; span=(23, 24), match=' '>
```

###### Example 23: `\S` = [a-zA-Z0-9] + symbols

```python
import re


results = re.finditer(r"\S", "12 45 # HI \t There \n< ? _")

for result in results:
    print(result)
import re


results = re.finditer(r"\S", "12 45 # HI \t There \n< ? _")

for result in results:
    print(result)
# <re.Match object; span=(0, 1), match='1'>
# <re.Match object; span=(1, 2), match='2'>
# <re.Match object; span=(3, 4), match='4'>
# <re.Match object; span=(4, 5), match='5'>
# <re.Match object; span=(6, 7), match='#'>
# <re.Match object; span=(8, 9), match='H'>
# <re.Match object; span=(9, 10), match='I'>
# <re.Match object; span=(13, 14), match='T'>
# <re.Match object; span=(14, 15), match='h'>
# <re.Match object; span=(15, 16), match='e'>
# <re.Match object; span=(16, 17), match='r'>
# <re.Match object; span=(17, 18), match='e'>
# <re.Match object; span=(20, 21), match='<'>
# <re.Match object; span=(22, 23), match='?'>
# <re.Match object; span=(24, 25), match='_'>
```

###### Example 24: `\w` = not [a-zA-Z0-9_] (alphanumeric)

```python
import re

str_1 = "12 54 # \n Theme < ? _"
results = re.finditer(r"\w", str_1)


for result in results:
    print(result)
# <re.Match object; span=(0, 1), match='1'>
# <re.Match object; span=(1, 2), match='2'>
# <re.Match object; span=(3, 4), match='5'>
# <re.Match object; span=(4, 5), match='4'>
# <re.Match object; span=(10, 11), match='T'>
# <re.Match object; span=(11, 12), match='h'>
# <re.Match object; span=(12, 13), match='e'>
# <re.Match object; span=(13, 14), match='m'>
# <re.Match object; span=(14, 15), match='e'>
# <re.Match object; span=(20, 21), match='_'>
```

###### Example 25: `\W` = not [a-zA-Z0-9_]

```python
import re

str_1 = "12 54 # \n Theme < ? _"
results = re.finditer(r"\W", str_1)


for result in results:
    print(result)
# <re.Match object; span=(2, 3), match=' '>
# <re.Match object; span=(5, 6), match=' '>
# <re.Match object; span=(6, 7), match='#'>
# <re.Match object; span=(7, 8), match=' '>
# <re.Match object; span=(8, 9), match='\n'>
# <re.Match object; span=(9, 10), match=' '>
# <re.Match object; span=(15, 16), match=' '>
# <re.Match object; span=(16, 17), match='<'>
# <re.Match object; span=(17, 18), match=' '>
# <re.Match object; span=(18, 19), match='?'>
# <re.Match object; span=(19, 20), match=' '>
```

###### Example 26: `\b`

any letter or any set of letters which are at the start or at the end of a specific block.

```python
import re


# Check at the begining
str_1 = """possible 12 54 # . hi \n possible There \t \
    `< ? _ > possible % ^ impossible"""

results_1 = re.finditer(r"\bpossible", str_1)

for result in results_1:
    print(result)

# <re.Match object; span=(0, 8), match='possible'>
# <re.Match object; span=(24, 32), match='possible'>
# <re.Match object; span=(54, 62), match='possible'>


# Check at the end
str_2 = """possibleis 12 54 # . hi \n possible There \t \
    `< ? _ > possible % ^ impossible"""
results_2 = re.finditer(r"possible\b", str_2)

for result in results_2:
    print(result)

# <re.Match object; span=(26, 34), match='possible'>
# <re.Match object; span=(56, 64), match='possible'>
# <re.Match object; span=(71, 79), match='possible'>


```

###### Example 27: `\B`

```python
import re


# Check NOT at the begining
str_1 = """heater 12 54 # . hi \n  There \t \
    `< ? _ > unheated % ^ noheat"""

results_1 = re.finditer(r"\Bheat", str_1)

for result in results_1:
    print(result)

# <re.Match object; span=(46, 50), match='heat'>
# <re.Match object; span=(59, 63), match='heat'>


# Check NOT at the end
str_2 = """heater 12 54 # . hi \n  There \t \
    `< ? _ > unheated % ^ noheat"""

results_2 = re.finditer(r"heat\B", str_2)

for result in results_2:
    print(result)

# <re.Match object; span=(0, 4), match='heat'>
# <re.Match object; span=(46, 50), match='heat'>


```

### Working with dates

we have three files:

1. dates
   
   > 15/10/2100
   > 
   > 06/29/2099
   > 
   > 01-01-1975
   > 
   > 08-31-1299
   > 
   > 15.10.2035
   > 
   > 09_12_1885
   > 
   > 2020/01/16
   > 
   > 2020-17-11

2. emails
   
   > Anderson456@gmail.com
   > 
   > Katie-Smith@evolutive.edu
   > 
   > galactic_Bradly@new-era.io
   > 
   > cool.awesome@google-anlytics.academy

3. URLs
   
   > https://google.com
   > 
   > http://www.paiting.studio
   > 
   > http://awesome.dev
   > 
   > https://www.planet.org 

###### Example 28:

```python
import re


with open("dates.txt") as file:
    # print(type(file.read())) --> <class 'str'>
    dates = file.read()

    results_1 = re.finditer(r"\d\d.\d\d.\d\d\d\d", dates)
    for result in results_1:
        print(result)
# <re.Match object; span=(0, 10), match='15/10/2100'>
# <re.Match object; span=(12, 22), match='06/29/2099'>
# <re.Match object; span=(24, 34), match='01-01-1975'>
# <re.Match object; span=(36, 46), match='08-31-1299'>
# <re.Match object; span=(48, 58), match='15.10.2035'>
# <re.Match object; span=(60, 70), match='09_12_1885'>

    results_2 = re.finditer(r"\d{2}.\d{2}.\d{4}", dates)
    for result in results_2:
        print(result)
# <re.Match object; span=(0, 10), match='15/10/2100'>
# <re.Match object; span=(12, 22), match='06/29/2099'>
# <re.Match object; span=(24, 34), match='01-01-1975'>
# <re.Match object; span=(36, 46), match='08-31-1299'>
# <re.Match object; span=(48, 58), match='15.10.2035'>
# <re.Match object; span=(60, 70), match='09_12_1885'>

    results_3 = re.finditer(r"\d{2}/\d{2}/\d{4}", dates)
    for result in results_3:
        print(result)
# <re.Match object; span=(0, 10), match='15/10/2100'>
# <re.Match object; span=(12, 22), match='06/29/2099'>

    results_4 = re.finditer(r"\d{2}-\d{2}-\d{4}", dates)
    for result in results_4:
        print(result)
# <re.Match object; span=(24, 34), match='01-01-1975'>
# <re.Match object; span=(36, 46), match='08-31-1299'>

    results_5 = re.finditer(r"\d{2}\.\d{2}\.\d{4}", dates)
    for result in results_5:
        print(result)
# <re.Match object; span=(48, 58), match='15.10.2035'>

    results_6 = re.finditer(r"\d{2}[/-]\d{2}[/-]\d{4}", dates)
    for result in results_6:
        print(result)
# <re.Match object; span=(48, 58), match='15.10.2035'>
# <re.Match object; span=(0, 10), match='15/10/2100'>
# <re.Match object; span=(12, 22), match='06/29/2099'>
# <re.Match object; span=(24, 34), match='01-01-1975'>
# <re.Match object; span=(36, 46), match='08-31-1299'>

    results_7 = re.finditer(r"\d{4}[/-]\d{2}[/-]\d{2}", dates)
    for result in results_7:
        print(result)
# <re.Match object; span=(72, 82), match='2020/01/16'>
# <re.Match object; span=(84, 94), match='2020-17-11'>

```

### Working with emails

###### Example 29:

```python
import re


with open("emails.txt") as file:
    emails = file.read()

    pattern = r""
    results = re.finditer(pattern, emails)


    for result in results:
        print(result)
```

###### Example 30:

```python
import re


with open("emails.txt") as file:
    emails = file.read()

    pattern = r"[a-zA-Z0-9]+@"
    pattern = r"[a-zA-Z0-9-_\.]+@"
    pattern = r"[a-zA-Z0-9-_\.]+@[a-zA-Z-]+\.(com|edu)"
    pattern = r"[a-zA-Z0-9-_\.]+@[a-zA-Z-]+\.[a-z]+"
    pattern = r"([a-zA-Z0-9-_\.]+)@([a-zA-Z-]+)\.([a-z])+"

    results = re.finditer(pattern, emails)
    for result in results:
        print(result)
# <re.Match object; span=(0, 21), match='Anderson456@gmail.com'>
# <re.Match object; span=(23, 48), match='Katie-Smith@evolutive.edu'>
# <re.Match object; span=(50, 76), match='galactic_Bradly@new-era.io'>
# <re.Match object; span=(78, 114), match='cool.awesome@google-anlytics.academy'>

    results = re.finditer(pattern, emails)
    print("__")
    for result in results:
        print(result.group())
# Anderson456@gmail.com
# Katie-Smith@evolutive.edu
# galactic_Bradly@new-era.io
# cool.awesome@google-anlytics.academy

    results = re.finditer(pattern, emails)
    print("__")
    for result in results:
        print(result.group(2))
# gmail
# evolutive
# new-era
# google-anlytics

```

# 
