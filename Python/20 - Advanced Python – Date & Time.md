## 20 - Advanced Python – Date & Time

### Python datetime module

In Python, date and time are not a data type of their own, but a module named **datetime** can be imported to work with the date as well as time. **Python Datetime module** comes built into Python, so there is no need to install it externally. 

Python Datetime module supplies classes to work with date and time. These classes provide a number of functions to deal with dates, times and time intervals. Date and datetime are an object in Python, so when you manipulate them, you are actually manipulating objects and not string or timestamps.

The DateTime module is categorized into 6 main classes – 

- **date:** An idealized naive date, assuming the current Gregorian calendar always was, and always will be, in effect. Its attributes are year, month and day.
- **time:** An idealized time, independent of any particular day, assuming that every day has exactly 24*60*60 seconds. Its attributes are hour, minute, second, microsecond, and tzinfo.
- **datetime:** Its a combination of date and time along with the attributes year, month, day, hour, minute, second, microsecond, and tzinfo.
- **timedelta:** A duration expressing the difference between two date, time, or datetime instances to microsecond resolution.
- **tzinfo:** It provides time zone information objects.
- **timezone:** A class that implements the tzinfo abstract base class as a fixed offset from the UTC (New in version 3.2).

Links:

1. [Python Docs - datetime - Basic date and time types](https://docs.python.org/3/library/datetime.html)

2. [Python Docs - time - Time access and conversions](https://docs.python.org/3/library/time.html#module-time)

3. [Python Docs - zoneinfo - IANA time zone support](https://docs.python.org/3/library/zoneinfo.html)

4. [Python Docs - calendar — General calendar-related functions](https://docs.python.org/3/library/calendar.html)

5. [Using Python datetime to Work With Dates and Times – Real Python](https://realpython.com/python-datetime/)

6. 

### The Date Class

The object of the Date class represents the naive date containing year, month, and date according to the current Gregorian calendar. This date can be extended indefinitely in both directions. The January 1 of year 1 is called day 1 and January 2 or year 2 is called day 2 and so on.

**Syntax:** class datetime.date(year, month, day)

###### Example 1: Getting the current Date & Time

```python
from datetime import datetime

print(datetime.now())
# 2023-03-24 14:02:30.856380
```

###### Example 2: Getting the current Date

```python
import datetime

print(datetime.date.today())
# 2023-03-24
```

###### Example 3: Getting Datetime attributes

```python
import datetime

print(dir(datetime))
"""
['MAXYEAR', 'MINYEAR', 'UTC', 
'__all__', '__builtins__', '__cached__', 
'__doc__', '__file__', '__loader__', 
'__name__', '__package__', '__spec__', 
'date', 'datetime', 'datetime_CAPI', 
'sys', 'time', 'timedelta', 
'timezone', 'tzinfo']
"""
```

###### Example 4: Creating a date object

```python
import datetime

date_var = datetime.date(2100, 12, 31)
# date method is actually constructor of the date class

print(date_var)         # 2100-12-31
print(type(date_var))   # <class 'datetime.date'>
```

###### Example 5: Importing the date class

```python
from datetime import date

print(date(2100, 12, 30))
# 2100-12-30
```

###### Example 6: getting date from a timestamp

```python
from datetime import date

time_stamp = date.fromtimestamp(2123456789)
print(time_stamp)
# 2037-04-16

epoch_times = [1, 1000000000, 1500000000,
               1625000000, 1656250000, 1656250000, 
               1671875000, 1679687500, 1687500000,
               1750000000, 2000000000]


for var in epoch_times:
    print(f"{var}\t",date.fromtimestamp(var))

"""
1     1970-01-01
1000000000     2001-09-09
1500000000     2017-07-14
1625000000     2021-06-30
1656250000     2022-06-26
1656250000     2022-06-26 
1671875000     2022-12-24
1679687500     2023-03-24 ---> Today
1687500000     2023-06-23
1750000000     2025-06-15
2000000000     2033-05-18
"""
```

###### Example 7: getting today's year, month and day

```python
from datetime import date

today = date.today()

print("Current Year: ", today.year)
print("Current Month: ", today.month)
print("Current Day: ", today.day)

"""
Current Year:  2023
Current Month:  3
Current Day:  24
"""
```

##### Links:

1. [Python DateTime - Date Class - GeeksforGeeks](https://www.geeksforgeeks.org/python-datetime-date-class/)

### Time Class

Time class represents the local time of the day which is independent of any particular day. This class can have the tzinfo object which represents the timezone of the given time. If the tzinfo is None then the time object is the **naive** object otherwise it is the **aware** object.

###### Example 1: Time object to represent time

```python
from datetime import time


time_1 = time()
print("Time A:", time_1)
# Time A: 00:00:00

time_2 = time(13, 55, 00)
print("Time B:", time_2)
# Time B: 13:55:00

time_3 = time(hour=9, minute=51, second=00)
print("Time C:", time_3)
# Time B: 13:55:00

time_4 = time(13, 55, 00, 100000)
print("Time D:", time_4)
# Time B: 13:55:00
```

###### Example 2:

```python
from datetime import time


time_5 = time(11, 34, 56)

print("Hour:", time_5.hour)                 # Hour: 11
print("Minute:", time_5.minute)             # Minute: 34
print("Second:", time_5.second)             # Second: 56
print("Microsecond:", time_5.microsecond)   # Microsecond: 0
```

##### Links:

1. [Python DateTime - Time Class - GeeksforGeeks](https://www.geeksforgeeks.org/python-datetime-time-class/)

### Datetime Class

DateTime class of the DateTime module as the name suggests contains information on both date as well as time. Like a date object, DateTime assumes the current Gregorian calendar extended in both directions; like a time object, DateTime assumes there are exactly 3600*24 seconds in every day. But unlike date class, the objects of DateTime class are potentially aware objects i.e. it contains information regarding time zone as well.

###### Example 1: Python datetime object

```python
from datetime import datetime


time_1 = datetime(2100, 1, 1)
print(time_1)
# 2100-01-01 00:00:00


time_2 = datetime(2050, 10, 25, 20, 50, 50)
print(time_2)
# 2100-01-01 00:00:00


# first three arguments are mandatory
```

###### Example 2: getting year, month, hour, minute, second and timestamp

```python
from datetime import datetime


time_3 = datetime(2050, 10, 25, 20, 50, 50)

print("Year:\t", time_3.year)               # Year:     2050
print("Month:\t", time_3.month)             # Month:    10
print("Day:\t", time_3.day)                 # Day:      25
print("Hour:\t", time_3.hour)               # Hour:     20
print("Minute:\t", time_3.minute)           # Minute:   50
print("Second:\t", time_3.second)           # Second:   50
print("Timestamp:", time_3.timestamp())   # Timestamp: 2550331250.0
```

##### Links:

1. [Python DateTime - DateTime Class - GeeksforGeeks](https://www.geeksforgeeks.org/python-datetime-datetime-class/)

### Timedelta Class

**Timedelta** class is used for calculating differences between dates and represents a duration. The difference can both be positive as well as negative.

###### Example 1: Difference between two date object

```python
from datetime import date


t1 = date(year=2060, month=12, day=15)
t2 = date(year=1970, month=1, day=1)


t3 = t1 - t2
print(t3)
# 33221 days, 0:00:00

print(type(t3))
# <class 'datetime.timedelta'>
```

###### Example 2: Difference between two datetime object

```python
from datetime import datetime


t1 = datetime(year=2060, month=12, day=15, hour=5, minute=39, second=31)
t2 = datetime(year=1970, month=1, day=1, hour=15, minute=23, second=47)


t3 = t1 - t2
print(t3)
# 33220 days, 14:15:44

print(type(t3))
# 33220 days, 14:15:44
```

###### Example 3: Difference between two timedelta object

```python
from datetime import timedelta


t1 = timedelta(weeks=2, days=5, hours=1, seconds=33)
t2 = timedelta(days=5, hours=11, minutes=12, seconds=33)


t3 = t1 - t2
print(t3)
# 13 days, 13:48:00

print(type(t3))
# 13 days, 13:48:00
```

###### Example 4: Getting negative timedelta object

```python
from datetime import timedelta


t1 = timedelta(seconds=33)
t2 = timedelta(seconds=54)


t3 = t1 - t2
print(t3)
# -1 day, 23:59:39
```

###### Example 5: Time duration in seconds

```python
from datetime import timedelta


time = timedelta(days=110, hours=126, minutes=70, seconds=1000)


print("total seconds:", time.total_seconds())
# total seconds: 9962800.0
```

##### Links:

1. [Python DateTime - Timedelta Class - GeeksforGeeks](https://www.geeksforgeeks.org/python-datetime-timedelta-class/)

### The strftime() Method

Date formats:

* **US:** mm/dd/yyy

* **UK:** dd/mm/yyyy 

###### Example 1: Formatting date using `strftime()`

```python
from datetime import datetime


# current date & time
now = datetime.now()

t1 = now.strftime("%H:%M:%S")
print(t1)
# 20:38:18

t2 = now.strftime("%m/%d/%Y, %H:%M:%S")
print(t2)
# 03/26/2023, 20:38:18

print(type(t2))
# <class 'str'>
```

###### Example 2: datetime to string using `strftime()`

```python
from datetime import datetime


now = datetime.now()

year = now.strftime("%Y")
month = now.strftime("%m")
day = now.strftime("")


print("Year: ", year, " Month: ", month, " Day: ", day)
# Year:  2023  Month:  03  Day:
```

###### Example 3: Creating string from a timestamp

```python
from datetime import datetime


timestamp = 4333259999
date_time = datetime.fromtimestamp(timestamp)


print(date_time)
print(type(date_time))
# 2107-04-26 14:49:59
# <class 'datetime.datetime'>

d1 = date_time.strftime("%m/%d%Y, %H%M%S")
print(d1)
print(type(d1))
# 04/262107, 144959
# <class 'str'>

d2 = date_time.strftime("%d %b, %Y")
print(d2)
# 26 Apr, 2107

d3 = date_time.strftime("%d %B, %Y")
print(d3)
# 26 April, 2107

t1 = date_time.strftime("%I%p")
print(t1)
# 02PM
```

###### Example 4: Locale's appropriate date and time

```python
from datetime import datetime


timestamp = 1599998989
date_time = datetime.fromtimestamp(timestamp)


d1 = date_time.strftime("%c")
print(d1)
# Sun Sep 13 15:39:49 2020

d2 = date_time.strftime("%x")       # dd/mm/year
print(d2)
# 09/13/20

d3 = date_time.strftime("%X")       # hh:mm:ss
print(d3)
# 15:39:49
```

###### Example 5: Python's datetime to timestamp

```python
from datetime import datetime


now = datetime.now()

# converting to timestamp
time_stamp = datetime.timestamp(now)
print(time_stamp)
# 1679854009.747897


# converting from timestamp
date_time = datetime.fromtimestamp(time_stamp)
print(date_time)
# 2023-03-26 21:37:03.417151
```

### The strptime() Method

###### Example 1: `strptime()`

```python
from datetime import datetime


date_str = "21 December, 2111"

date_obj = datetime.strptime(date_str, "%d %B, %Y")
print(date_obj)
# 2111-12-21 00:00:00

print(type(date_obj))
# <class 'datetime.datetime'>
```

###### Example 2: String to datetime object

```python
from datetime import datetime


date_str = "14 Aug, 2009"

date_obj = datetime.strptime(date_str, "%d %b, %Y")
print(date_obj)
# 2009-08-14 00:00:00
```

###### Example 3: String to datetime object

```python
from datetime import datetime


date_str1 = "31/01/2200 19:10:50"
date_str2 = "12/31/1917 09:01:14"


# considering the date is in dd/mm/yyyy format
date_obj1 = datetime.strptime(date_str1, "%d/%m/%Y %H:%M:%S")
print(date_obj1)            # 2200-01-31 19:10:50
print(type(date_obj1))      # <class 'datetime.datetime'>
print(type(date_str1))      # <class 'str'>


# considering the date is in mm/dd/yyyy format
date_obj2 = datetime.strptime(date_str2, "%m/%d/%Y %H:%M:%S")
print(date_obj2)            # 1917-12-31 09:01:14
print(type(date_obj2))      # <class 'datetime.datetime'>
```

### The sleep() method

###### Example 1: `sleep()`

```python
from datetime import datetime
import time


print("Immediately at ",
      datetime.strftime(datetime.now(), "%H:%M:%S"))
# Immediately at  21:56:20

time.sleep(4.0)

print("Immediately after 4 seconds at: ",
      datetime.strftime(datetime.now(), "%H:%M:%S"))
# Immediately after 4 seconds at:  21:56:24
```

###### Example 2: Creating a simple low level digital clock

```python
import time


while True:
    local_time = time.localtime()
    result = time.strftime("%I:%M:%S", localtime)
    print(result)
    time.sleep(1)
""""
10:01:35
10:01:36
10:01:37
10:01:38
10:01:39
10:01:40
...
..
.
"""
```
