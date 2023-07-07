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



















##### Links:

1. 



##### Books:

1. 
