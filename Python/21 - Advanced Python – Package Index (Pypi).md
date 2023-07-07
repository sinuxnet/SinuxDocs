## 21 - Advanced Python – Package Index (Pypi) - Shortcut

### Python Package Index (pypi)

The Python Package Index, abbreviated as **PyPI** and also known as the Cheese Shop is the official **third-party** **software repository** for Python. (CPAN repository for Perl & CRAN repository for R)
PyPI is run by the Python Software Foundation, a charity. Some package managers, including **pip**, use PyPI as the default source for packages and their dependencies.

As of 17 January 2022, more than 350,000 Python packages can be accessed through PyPI.

Python PIP is the package manager for Python packages. We can use PIP to install packages that do not come with Python.

| Language      | Package Manager |
| ------------- | --------------- |
| Python        | pip             |
| Javascript    | npm             |
| Ruby          | gem             |
| .NET platform | NuGet           |

###### Install Package:

```shell
> pip install requests
```

###### Specifying Package Version:

```shell
> pip install requests==2.16.2
```

###### Upgrade Package:

```shell
> pip install --upgrade requests
```

###### Display Package information:

```shell
> pip show requests
```

##### Get a list of locally installed Python Modules:

```shell
> pip list
```

###### Uninstall Packages

```shell
> pip unistall requests
```

###### Search Packages

```shell
> pip search request
```

###### Listing additional Packages

```shell
> pip freeze
```

###### Listing Outdated Packages

```shell
> pip list --outdated
```

###### Update pip itself:

```shell
> pip install --upgrade pip
```

###### 

###### Example 1: Using requests module

```python
import requests

response = requests.get("http://google.com")
print(response)
# <Response [200]>
```

###### Example 2: Using pytz module

```python
import pytz
from datetime import datetime

# local (Tehran)
local = datetime.now()
print("Local:\t", local.strftime("%m/%d/%Y, %H:%M:%S"))


tz_NYC = pytz.timezone("America/New_York")
datetime_NYC = datetime.now(tz_NYC)
print("NYC:\t", datetime_NYC.strftime("%m/%d/%Y, %H:%M:%S"))

# Output
# Local:    03/27/2023, 19:15:47
# NYC:      03/27/2023, 11:45:47

print(type(tz_NYC))
# <class 'pytz.tzfile.America/New_York'>
```

##### Links:

1. [Python Package Index - Wikipedia](https://en.wikipedia.org/wiki/Python_Package_Index)

### Virtual Environments

A virtual environment is a tool that helps to keep dependencies required by different projects separate by creating isolated python virtual environments for them.

**Why do we need a virtual environment?**

Imagine a scenario where you are working on two web-based python projects one of them uses Django 4.0 and the other uses Django 4.1. In such situations virtual environment can be really useful to maintain the dependencies of both projects.

**When and where to use a virtual environment?**

By default, every project on your system will use these same directories to store and retrieve site packages (third-party libraries). How does this matter? Now, in the above example of two projects, you have two versions of Django. This is a real problem for Python since it can’t differentiate between versions in the “site-packages” directory. So both v1.9 and v1.10 would reside in the same directory with the same name. This is where virtual environments come into play. To solve this problem, we just need to create two separate virtual environments for both projects. The great thing about this is that there are no limits to the number of environments you can have since they’re just directories containing a few scripts. A virtual Environment should be used whenever you work on any Python-based project. It is generally good to have one new virtual environment for every Python-based project you work on. So the dependencies of every project are isolated from the system and each other.

#### Pipenv

**Pipenv** is a Python virtualenv management tool that supports a multitude of systems and nicely bridges the gaps between pip, pyenv and virtualenv. *Linux, macOS, and Windows are all first-class citizens in pipenv.*

It automatically creates and manages a virtualenv for your projects, as well as adds/removes packages from your `Pipfile` as you install/uninstall packages. It also generates the ever-important `Pipfile.lock`, which is used to produce deterministic builds.

Pipenv is primarily meant to provide users and developers of applications with an easy method to setup a working environment.

The problems that Pipenv seeks to solve are multi-faceted:

- You no longer need to use `pip` and `virtualenv` separately. They work together.

- Managing a `requirements.txt` file with package hashes can be problematic. Pipenv uses `Pipfile` and `Pipfile.lock` to separate abstract dependency declarations from the last tested combination.

- Hashes are documented in the lock file, always. Security considerations are put first.

- Strongly encourage the use of the latest versions of dependencies to minimize security risks [arising from outdated components](https://www.owasp.org/index.php/Top_10-2017_A9-Using_Components_with_Known_Vulnerabilities).

- Gives you insight into your dependency graph (e.g. `$ pipenv graph`).

- Streamline development workflow by supporting local customizations with `.env` files.

Pipenv is a package and dependency manager for Python projects. It harnesses the power of different existing tools, bringing their functionalities together:

- **pip** for Python package management
- **pyenv** for Python version management
- **Virtualenv** for creating different virtual Python environments
- **Pipfile** for managing project dependencies

###### Example 1: Using pipenv

The python code with name of  *app.py* is:

```python
import requests

response = requests.get("http://google.com")
print(response)
# <Response [200]>
```

Note: *requests* module is not installed on computer.

**Install Vitual Environment tool:**

```shell
> pip install pipenv
```

**Create vitruall environment and Install request module in it:**

```shell
> pipenv install requests
```

Two files will create in working directory `Pipfile` & `Pipfile.lock`.

`Pipfile` contains the specification for the project top-level requirements and any desired specifiers. This file is managed by the developers invoking pipenv commands. The `Pipfile` uses inline tables and the [TOML Spec](https://github.com/toml-lang/toml#user-content-spec%3E).

`Pipfile.lock` replaces the `requirements.txt` file used in most Python projects and adds security benefits of tracking the packages hashes that were last locked. This file is managed automatically through locking actions.

**Show the location (path) of virtuall environment:**

```shell
> pipenv --venv
C:\Users\sina\.virtualenvs\Ex_venv-14F82Xpz
```

Note that this venv folder differs with project folder. Because of large project folder size.

if we run the code we encouter with this error:

<span style="color:orange">**ModuleNotFoundError: No module named 'requests'**</span>

We did not activated our virtual environment.

**Activating virtual environment and launching subshell:**

```shell
> pipenv shell
> python.exex app.py
# <Response [200]>
```

##### Links:

1. [Pipenv: Python Dev Workflow for Humans](https://pipenv.pypa.io/en/latest/)

2. [Pipenv : Python Package Management Tool - GeeksforGeeks](https://www.geeksforgeeks.org/pipenv-python-package-management-tool/)

3. [Scaleway](https://www.scaleway.com/en/docs/compute/gpu/how-to/use-pipenv/)

4. [Python Venv (Virtual Environment) with Pipenv | DataCamp](https://www.datacamp.com/tutorial/virtual-environment-in-python)

5. [Pipenv: A Guide to the New Python Packaging Tool – Real Python](https://realpython.com/pipenv-guide/)

6. [Python Pipenv: Another Package Manager &bull; Python Land Tutorial](https://python.land/virtual-environments/pipenv)

7. [Python Docs - venv — Creation of virtual environments](https://docs.python.org/3/library/venv.html)

8. [Python Virtual Environments: A Primer – Real Python](https://realpython.com/python-virtual-environments-a-primer/)

9. [How to Set Up a Virtual Environment in Python – And Why It's Useful](https://www.freecodecamp.org/news/how-to-setup-virtual-environments-in-python/)

10. [Python Virtual Environment | Introduction - GeeksforGeeks](https://www.geeksforgeeks.org/python-virtual-environment/)

### Yelp API

The API documentation is: https://docs.developer.yelp.com/reference/v3_business_search

You must sign up and request an API key to do examples.

###### Example 1: Getting Data From Yelp API

without authorization:

```python
import requests

response = requests.get("https://api.yelp.com/v3/businesses/search")
print(response)
print(response.text)
"""
<Response [400]>
{"error": {"code": "VALIDATION_ERROR", "description": "Authorization is a required parameter.", "field": "Authorization", "instance": null}}
"""
```

```python
import requests

client_ID = "Uhn1-e6XFpe68Yg"

api_key = "zmiqXje9KUSlxEg884WNonnVTl934qjgcNSEPWg01yxJA_4hZHYx"

api_url = "https://api.yelp.com/v3/businesses/search"

params = {
    "term": "salon",
    "limit": 30,
    "location": "Miami"
}

header = {
    "Authorization": "Bearer " + api_key
}

response = requests.get(api_url, headers=header, params=params)
print(response)
# <Response [200]>

businesses = response.json()["businesses"]

names = [business["name"]
         for business in businesses
         if business["rating"] > 4.5]
print(names)
"""
['Le Hair Salon', 'The Glam Studio Miami', 'Art & Chemistry', 'Elegance beauty salon', 'Hair Healers International', 'Edward James', 'Roxy Hair Salon', 'Arturo Orta Beauty Salon', 'Avalon Salon', 'The Mane Group Salon', 'Ling Chow Salon', 'Art & Beauty Salon']
"""
```

##### Links:

1. [HTTP request methods - HTTP | MDN](https://developer.mozilla.org/en-US/docs/Web/HTTP/Methods)

2. [HTTP response status codes - HTTP | MDN](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status)

### Sending Text Messages

As we know Python is a cool scripting language and can be used to write scripts to easify day-to-day task. Also, since python has large community support and lots of module/API available, it makes Python more versatile and popular among users.

**Head to [Twilio’s registration page](https://www.twilio.com/try-twilio). Complete the registration by filling in with the required details.**

First of all install required module in a virtual environment:

```shell
> pipenv install twilio
```

The Project:

```python
from twilio.rest import Client

account_sid = "ACa4bcbba29xxxxxxxxxxx"

auth_token = "1d595edefbf4xxxxxxxxx"

message = Client(account_sid, auth_token)

message.messages.create(
    to="+989924948758",
    from_="14346235265",
    body="Hello This is My first POST Method in Python"
)


print(message.sid)
```

### Web Scraping

Web scraping is an automated method used to extract large amounts of data from websites. The data on the websites are unstructured. Web scraping helps collect these unstructured data and store it in a structured form. There are different ways to scrape websites such as online Services, APIs or writing your own code.

![](D:\OneDrive\z%20-%20My%20Docs\md%20docs\Python%20Bootcamp%202022%20-%20Muslim%20Helalee\images\web%20scraping_def.png)

The following are few of the many uses of Web Scraping:

- In eCommerce, Web Scraping is used for competition price monitoring.
- In Marketing, Web Scraping is used for lead generation, to build phone and email lists for cold outreach.
- In Real Estate, Web Scraping is used to get property and agent/owner details.
- Web Scraping is used to collect training and testing data for Machine Learning projects.

To extract data using web scraping with python, you need to follow these basic steps:

1. Find the URL that you want to scrape
2. Inspecting the Page
3. Find the data you want to extract
4. Write the code
5. Run the code and extract the data
6. Store the data in the required format

##### Is it legal?

While the act of scraping is legal, the data you may extract can be illegal to use. Make sure that you're not messing with any:

- Copyrighted content – since it's someone's intellectual property, it's protected by law and you can't just reuse it.
- Personal data – if the information you gather can be used to identify a person, then it's considered personal data and for EU citizens, it's protected under the GDPR. Unless you have a lawful reason to store that data, it's better to just skip it altogether.

#### BeautifulSoup Library

BeautifulSoup is used extract information from the HTML and XML files. It provides a parse tree and the functions to navigate, search or modify this parse tree.

- Beautiful Soup is a Python library used to pull the data out of HTML and XML files for web scraping purposes. It produces a parse tree from page source code that can be utilized to drag data hierarchically and more legibly. 
- It was first presented by Leonard Richardson, who is still donating to this project, and this project is also supported by Tide lift (a paid subscription tool for open-source supervision).
- Beautiful soup3 was officially released in May 2006, Latest version released by Beautiful Soup is 4.9.2, and it supports Python 3 and Python 2.4 as well.

##### Features of Beautiful Soup

**Beautiful Soup** is a Python library designed for quick turnaround projects like screen-scraping. Three features make it powerful:

1. Beautiful Soup provides a few simple methods and Pythonic idioms for navigating, searching, and modifying a parse tree: a toolkit for dissecting a document and extracting what you need. It doesn't take much code to write an application
2. Beautiful Soup automatically converts incoming documents to Unicode and outgoing documents to UTF-8. You don't have to think about encodings, unless the document doesn't specify an encoding and Beautiful Soup can't detect one. Then you just have to specify the original encoding.
3. Beautiful Soup sits on top of popular Python parsers like [lxml](http://lxml.de/) and [html5lib](http://code.google.com/p/html5lib/), allowing you to try out different parsing strategies or trade speed for flexibility.

###### Example 1: satckoverflow.com

Installing required module(s) in venv:

```shell
> pipenv install beautifulsoup4
> pipenv install requests
```

We want to get latest question of stackoverflow.com

Getting the first question (step by step):

```python
import requests

from bs4 import BeautifulSoup

url = "https://stackoverflow.com/questions/"

response = requests.get(url)
# print(response.text)

soup = BeautifulSoup(response.text, "html.parser")

questions = soup.select(".s-post-summary")
# print(type(questions))
# <class 'bs4.element.ResultSet'>
# print(questions[0])
# print("*" * 10)
print(questions[0].attrs)
print("*" * 10)
print(questions[0].get("id", 0))  # 0 is default value
print("*" * 10)
print(questions[0].select_one(".s-link"))
print("*" * 10)
print(questions[0].select_one(".s-link").getText())
```

Getting All (50) of question with their votes:

```python
import requests

from bs4 import BeautifulSoup

url = "https://stackoverflow.com/questions/"

response = requests.get(url)
# print(response.text)

soup = BeautifulSoup(response.text, "html.parser")

questions = soup.select(".s-post-summary")

i = 1
print("N.O\tVotes\tQuestion")
for question in questions:
    # N.O
    print(f"{i} \t", end="")

    # number of votes
    print(question.select_one(
        ".s-post-summary--stats-item-number").getText(), "\t", end="")

    # question text
    print(question.select_one(".s-link").getText())
    i += 1
```

Output:

![](D:\OneDrive\z%20-%20My%20Docs\md%20docs\Python%20Bootcamp%202022%20-%20Muslim%20Helalee\images\webscraping.png)

###### Example 2: Using realpython.com example

```python
from urllib.request import urlopen


url = "http://olympus.realpython.org/profiles/aphrodite"
page = urlopen(url)
print(page)
# <http.client.HTTPResponse object at 0x0000013708F8BFD0>

html_bytes = page.read()
print(html_bytes)

"""
b'<html>\n<head>\n<title>Profile: Aphrodite</title>\n</head>\n<body bgcolor="yellow">\n<center>\n<br><br>\n<img src="/static/aphrodite.gif" />\n<h2>Name: Aphrodite</h2>\n<br><br>\nFavorite animal: Dove\n<br><br>\nFavorite color: Red\n<br><br>\nHometown: Mount Olympus\n</center>\n</body>\n</html>\n'
"""

html = html_bytes.decode("utf-8")
print(html)
"""
<html>
<head>
<title>Profile: Aphrodite</title>
</head>
<body bgcolor="yellow">
<center>
<br><br>
<img src="/static/aphrodite.gif" />
<h2>Name: Aphrodite</h2>
<br><br>
Favorite animal: Dove
<br><br>
Favorite color: Red
<br><br>
Hometown: Mount Olympus
</center>
</body>
</html>
"""
```

Now extracting the content of HTML `title` element:

```python
from urllib.request import urlopen


url = "http://olympus.realpython.org/profiles/aphrodite"
page = urlopen(url)
html_bytes = page.read()
html = html_bytes.decode("utf-8")

title_index = html.find("<title>")              # 14
start_index = title_index + len("<title>")      # 21
end_index = html.find("</title>")               # 39
title = html[start_index:end_index]
print(title)
# 'Profile: Aphrodite'
```

##### Links:

1. [A Practical Introduction to Web Scraping in Python – Real Python](https://realpython.com/python-web-scraping-practical-introduction/)

2. [Beautiful Soup: Build a Web Scraper With Python – Real Python](https://realpython.com/beautiful-soup-web-scraper-python/)

3. [Beautiful Soup: We called him Tortoise because he taught us.](https://www.crummy.com/software/BeautifulSoup/)

4. [Beautiful Soup Documentation](https://www.crummy.com/software/BeautifulSoup/bs4/doc/)

5. [What is Web Scraping? ](https://www.webharvy.com/articles/what-is-web-scraping.html)

6. [Web Scraping With Python - Full Guide to Python Web Scraping](https://www.edureka.co/blog/web-scraping-with-python/)

7. [Python Web Scraping Tutorial – How to Scrape Data From Any Website with Python](https://www.freecodecamp.org/news/how-to-scrape-websites-with-python-2/)

8. [Web Scraping with Python: Everything you need to know (2022) | ScrapingBee](https://www.scrapingbee.com/blog/web-scraping-101-with-python/)

##### Books:

1. Web Scraping with Python: Collecting Data from the Modern Web by Ryan Mitchell, O'Reilly Media 2015, ISBN: 9781491910276, 1491910275

2. Hands-On Web Scraping with Python by Anish Chapagain, Packt Publishing 2019, ISBN: 9781789533392, 1789533392

3. Web Scraping with Python by Richard Lawson, Packt Publishing 2015, ISBN: 9781782164371, 1782164375

4. Python Web Scraping by Katharine Jarmul & Richard Lawson, Packt Publishing 2017, ISBN: 9781786464293, 1786464292

5. Practical Web Scraping for Data Science by Seppe vanden Broucke & Bart Baesens, Apress 2018, ISBN: 9781484235829, 1484235827

### Automating The Browser

**Selenium** is a powerful tool for controlling web browser through program. It is functional for all browsers, works on all major OS and its scripts are written in various languages i.e Python, Java, C#, etc, we will be working with Python.

Selenium has four major components:

![](.\images\Components-of-Selenium.png)

* **Selenium IDE**
  
  * It is the major tool in the Selenium Suite. It is a complete integrated development environment (IDE) for Selenium tests.
  
  * It is implemented as a Firefox Add-On and as a Chrome Extension.
  
  * It allows for recording, editing and debugging of functional tests. It was previously known as Selenium Recorder.

* **Selenium RC**
  
  * Selenium Remote Control (RC) is a server, written in Java, that accepts commands for the browser via HTTP.
  
  * RC makes it possible to write automated tests for a web application in any programming language, which allows for better integration of Selenium in existing unit test frameworks.
  
  * To make writing tests easier, Selenium project currently provides client drivers for PHP, Python, Ruby, .NET, Perl and Java. The Java driver can also be used with JavaScript (via the Rhino engine).
  
  *  An instance of selenium RC server is needed to launch html test case – which means that the port should be different for each parallel run. However, for Java/PHP test case only one Selenium RC instance needs to be running continuously.

* **Selenium Web driver**
  
  * Selenium WebDriver is the successor to Selenium RC.
  
  * Selenium WebDriver accepts commands (sent in Selenese, or via a Client API) and sends them to a browser. This is implemented through a browser-specific browser driver, which sends commands to a browser and retrieves results.
  
  * Most browser drivers actually launch and access a browser application (such as Firefox, Google Chrome, Internet Explorer, Safari, or Microsoft Edge); there is also an HtmlUnit browser driver, which simulates a browser using the headless browser HtmlUnit.
  
  * Selenium WebDriver does not need a special server to execute tests. Instead, the WebDriver directly starts a browser instance and controls it.

* **Selenium GRID**
  
  * Selenium Grid is a server that allows tests to use web browser instances running on remote machines.
  
  *  With Selenium Grid, one server acts as the hub. Tests contact the hub to obtain access to browser instances. The hub has a list of servers that provide access to browser instances (WebDriver nodes), and lets tests use these instances.
  
  *  Selenium Grid allows running tests in parallel on multiple machines and to manage different browser versions and browser configurations centrally (instead of in each individual test).
  
  * The ability to run tests on remote browser instances is useful to spread the load of testing across several machines and to run tests in browsers running on different platforms or operating systems.
  
  * The latter is particularly useful in cases where not all browsers to be used for testing can run on the same platform.

Selenium Python bindings provides a simple API to write functional/acceptance tests using Selenium WebDriver. Through Selenium Python API you can access all functionalities of Selenium WebDriver in an intuitive way.

###### Preparing environment to use selenium webdriver:

Installing the module:

```shell
> pipenv install selenium
```

Selenium requires a web driver to interface with the chosen browser. Web drivers is a package to interact with a web browser. It interacts with the web browser or a remote web server through a wire protocol which is common to all. You can check out and install the web drivers of your browser choice.

| Browser | Link                                                                 |
| ------- | -------------------------------------------------------------------- |
| Chrome  | https://sites.google.com/chromium.org/driver/                        |
| Edge    | https://developer.microsoft.com/en-us/microsoft-dge/tools/webdriver/ |
| Firefox | https://github.com/mozilla/geckodriver/releases                      |
| Safari  | https://webkit.org/blog/6900/webdriver-support-in-safari-10/         |

###### Example 1:

```python
from selenium import webdriver
from selenium.webdriver.common.by import By
from selenium.webdriver.common.keys import Keys
import time

# opening the browser
# driver = webdriver.Chrome("C:\Windows\geckodriver.exe")
browser = webdriver.Chrome()
browser.get("https://accounts.google.com")

# username
# username_field = browser.find_element_by_id("identifierID")
username_field = browser.find_element(
    By.XPATH, "/html/body/div[1]/div[1]/div[2]/div/c-wiz/div/div[2]/div/div[1]/div/form/span/section/div/div/div[1]/div/div[1]/div/div[1]/input")
username_field.send_keys("testpythoton@gmail.com")

time.sleep(5)

# clicking the next button
# browser.find_element(By.CLASS_NAME, "VfPpkd-RLmnJb").click()
next_btn = browser.find_element(
    By.XPATH, "/html/body/div[1]/div[1]/div[2]/div/c-wiz/div/div[2]/div/div[2]/div/div[1]/div/div/button")
time.sleep(5)
next_btn.click()


# sending password
password_field = browser.find_element(By.CLASS_NAME, "whsOnd zHQkBf")
password_field.send_keys("Test$@Python321")

# clicking the next button
next_btn = browser.find_element_by_class_name("VfPpkd-RLmnJb")
next_btn.click()
```

### Working with PDF Files

PDF stands for **Portable Document Format**. It uses **.pdf** extension. It is used to present and exchange documents reliably, independent of software, hardware, or operating system.  
Invented by **Adobe**, PDF is now an open standard maintained by the International Organization for Standardization (ISO). PDFs can contain links and buttons, form fields, audio, video, and business logic.

PyPDF2 is a Python library that allows the manipulation of PDF documents. It can be used to create new PDF documents, modify existing ones and extract content from documents. PyPDF2 is a pure Python library that requires no non-standard modules.

The low-level API (based on Pygments) allows writing programs that generate or efficiently manipulate documents. The high-level API (based on ReportLab) enables the creation of complex documents such as forms, books, or magazines with just a few lines of code.

PyPDF2 is a python library built as a PDF toolkit. It is capable of:

- Extracting document information (title, author, …)
- Splitting documents page by page
- Merging documents page by page
- Cropping pages
- Merging multiple pages into a single page
- Encrypting and decrypting PDF files
- and more!

PyPDF2 isn’t the only python library you can use for PDF ocr using python. Here are some common Python PDF libraries:  

- **PDFQuery:** PDFQuery is a PDF scraping library, and it is a fast and user-friendly python wrapper for PyQuery, PDFMiner, and XML.
- **Tabula.py:** It is a Python wrapper around tabula-java used to read tables in PDF. Tabula.py enables you to read tables and can be converted into Pandas DataFrame.
- **Slate:** It is used to extract text from PDF files, depending on the PDFMiner package. Slate is a lightweight annotation tool that supports annotation in Python.
- **PDFMiner**: It is an open-source PDF library used to extract text from PDF. You can use PDFMiner to perform analysis on data. However, it only supports Python3.
- **pdflib:** PDFlib is a library for creating PDFs in python. This development library contains several levels for creating, personalizing, and importing PDFs.
- **Xpdf:** It is a Python wrapper for pdf.
- **PyPDF2:** It is one of the best-known python libraries that enable you to perform tasks on PDFs, including merging PDF files, extracting document information, splitting PDF pages, and much more.

###### Example 1: Reading & Writing

```python
import PyPDF2


with open("flexbox.pdf", "rb") as file:
    reader = PyPDF2.PdfReader(file)

    print(reader.pages)
    # <PyPDF2._page._VirtualList object at 0x7f20dbe9beb0>
    print(len(reader.pages))
    # 20

    page = reader.pages[10]
    page.rotate(180)

    writer = PyPDF2.PdfWriter()
    writer.add_page(page)

    with open("flexboxV2.pdf", "wb") as result:
            writer.write(result)
```

###### Example 2: Merging PDF files

```python
import PyPDF2

merger = PyPDF2.PdfMerger()
pdf_files = ["flexbox.pdf", "grid.pdf"]

for pdf_file in pdf_files:
    merger.append(pdf_file)

merger.write("Felx-Grid-Guid.pdf")
```

##### Links:

1. [PyPDF2 documentation](https://pypdf2.readthedocs.io/en/3.0.0/index.html)

2. [Working with PDF files in Python - GeeksforGeeks](https://www.geeksforgeeks.org/working-with-pdf-files-in-python/)

3. [How to Work With a PDF in Python – Real Python](https://realpython.com/pdf-python/)

4. [PYPDF2 Tutorial - Working with PDF in Python | Nanonets](https://nanonets.com/blog/pypdf2-library-working-with-pdf-files-in-python/)

5. [PyPDF2 · PyPI](https://pypi.org/project/PyPDF2/)

### Working with Excel Spreadsheets

**Openpyxl** is a Python library for reading and writing Excel (with extension xlsx/xlsm/xltx/xltm) files. The openpyxl module allows Python program to read and modify Excel files.
For example, users might have to go through thousands of rows and pick out a few handful of information to make small changes based on some criteria. Using Openpyxl module, these tasks can be done very efficiently and easily.

**Some practical use cases:**

- Importing New Products Into a Database

- Exporting Database Data Into a Spreadsheet

- Appending Information to an Existing Spreadsheet

##### Learning Some Basic Excel Terminology

| Term                    | Explanation                                                                                                                             |
| ----------------------- | --------------------------------------------------------------------------------------------------------------------------------------- |
| Spreadsheet or Workbook | A **Spreadsheet** is the main file you are creating or working with.                                                                    |
| Worksheet or Sheet      | A **Sheet** is used to split different kinds of content within the same spreadsheet. A **Spreadsheet** can have one or more **Sheets**. |
| Column                  | A **Column** is a vertical line, and it’s represented by an uppercase letter: *A*.                                                      |
| Row                     | A **Row** is a horizontal line, and it’s represented by a number: *1*.                                                                  |
| Cell                    | A **Cell** is a combination of **Column** and **Row**, represented by both an uppercase letter and a number: *A1*.                      |

##### Load the Excel file:

Load the file for example 1 to  5

```python
import openpyxl


work_book = openpyxl.load_workbook("users.xlsx")
print(work_book.sheetnames)
# ['Sheet_1']

sheet = work_book["Sheet_1"]
print(sheet)
# <Worksheet "Sheet_1">
```

#### Exampe 1 to 5:

###### Example 1: Accessing Indivijual cell

```python
# Approach 1 --> Cell coordinates
cell = sheet["A1"]
print(cell)             # <Cell 'Sheet_1'.A1>
print(cell.value)       # User Name
print(cell.row)         # 1
print(cell.column)      # 1
print(cell.coordinate)  # A1

# Approach 2 --> cell() method
cell = sheet.cell(row=2, column=3)
print(cell)
# <Cell 'Sheet_1'.C2>
```

###### Example 2: Accessing row/columns cells and iterating over them

```python
print("Number of Rows: ", sheet.max_row)
# Number of Rows:  6
print("Number of Columns: ", sheet.max_column)
# Number of Columns:  3

for row in range(1, sheet.max_row+1):
    for column in range(1, sheet.max_column+1):
        cell = sheet.cell(row, column)
        if cell.column < sheet.max_column:
            print(cell.value, end=",")
        else:
            print(cell.value)

"""
User Name,User ID,Status
cool555,111,online
333awesome,222,offline
dog,333,online
cat,444,online
wolf,555,online
"""
```

###### Example 3: Accessing a range of cells

```python
# getting all the cells in a coll
column = sheet["A"]
print(column)
# (<Cell 'Sheet_1'.A1>, <Cell 'Sheet_1'.A2>, <Cell 'Sheet_1'.A3>, <Cell 'Sheet_1'.A4>, <Cell 'Sheet_1'.A5>, <Cell 'Sheet_1'.A6>)


# getting a range of cells
print(sheet["A1:B5"])
# ((<Cell 'Sheet_1'.A1>, <Cell 'Sheet_1'.B1>), (<Cell 'Sheet_1'.A2>, <Cell 'Sheet_1'.B2>), (<Cell 'Sheet_1'.A3>, <Cell 'Sheet_1'.B3>), (<Cell 'Sheet_1'.A4>, <Cell 'Sheet_1'.B4>), (<Cell 'Sheet_1'.A5>, <Cell 'Sheet_1'.B5>))


# getting a range of cells using coordinates
print(sheet["A:C"])
# ((<Cell 'Sheet_1'.A1>, <Cell 'Sheet_1'.A2>, <Cell 'Sheet_1'.A3>, <Cell 'Sheet_1'.A4>, <Cell 'Sheet_1'.A5>, <Cell 'Sheet_1'.A6>), (<Cell 'Sheet_1'.B1>, <Cell 'Sheet_1'.B2>, <Cell 'Sheet_1'.B3>, <Cell 'Sheet_1'.B4>, <Cell 'Sheet_1'.B5>, <Cell 'Sheet_1'.B6>), (<Cell 'Sheet_1'.C1>, <Cell 'Sheet_1'.C2>, <Cell 'Sheet_1'.C3>, <Cell 'Sheet_1'.C4>, <Cell 'Sheet_1'.C5>, <Cell 'Sheet_1'.C6>))


# getting all the cells in the first row
print(sheet[1])
# (<Cell 'Sheet_1'.A1>, <Cell 'Sheet_1'.B1>, <Cell 'Sheet_1'.C1>)

# getting all the cells in a range of rows
print(sheet[1:3])
# ((<Cell 'Sheet_1'.A1>, <Cell 'Sheet_1'.B1>, <Cell 'Sheet_1'.C1>), (<Cell 'Sheet_1'.A2>, <Cell 'Sheet_1'.B2>, <Cell 'Sheet_1'.C2>), (<Cell 'Sheet_1'.A3>, <Cell 'Sheet_1'.B3>, <Cell 'Sheet_1'.C3>))
```

###### Example 4: Sheet object methods

```python
# append()
sheet.append(["wolf", 555, "online"])

# insert_rows(starting index, # of empty rows)
sheet.insert_rows(3, 10)

# insert_cols(starting index, # of empty rows)
sheet.insert_cols(2, 5)

# delete_rows(starting index, # of rows)
sheet.delete_rows(3, 10)
# delete_cols(starting index, # of rows)
sheet.delete_cols(2, 5)


work_book.save("users.xlsx")
```

###### Example 5: Adding sheets to the workbook

```python
 work_book.create_chartsheet("PY_sheet_1")

# save as another(new) file
work_book.save("nes_users.xlsx")
```

###### Example 6:

**Download Dataset:** [Click here to download the dataset for the openpyxl exercise you’ll be following in this tutorial.](https://realpython.com/bonus/openpyxl-sample-dataset/)

```python
from openpyxl import load_workbook
import json

workbook = load_workbook(filename="sample.xlsx")
sheet = workbook.active

products = {}

# Using the values_only because you want to return the cells' values
for row in sheet.iter_rows(min_row=2,
                           max_row=5,
                           min_col=4,
                           max_col=7,
                           values_only=True):

    product_id = row[0]
    product = {
        "parent": row[1],
        "title": row[2],
        "category": row[3]
    }
    products[product_id] = product

# Sample data of loop:
# ('B00FALQ1ZC', 937001370,
# 'Invicta Women ... own Leather Watch', 'Watches')


# Using json here to be able to format the output for displaying later
print(json.dumps(products))

```

```json
{
  "B00FALQ1ZC": {
    "parent": 937001370,
    "title": "Invicta Women's 15150 \"Angel\" 18k Yellow Gold Ion-Plated Stainless Steel and Brown Leather Watch",
    "category": "Watches"
  },
  "B00D3RGO20": {
    "parent": 484010722,
    "title": "Kenneth Cole New York Women's KC4944 Automatic Silver Automatic Mesh Bracelet Analog Watch",
    "category": "Watches"
  },
  "B00DKYC7TK": {
    "parent": 361166390,
    "title": "Ritche 22mm Black Stainless Steel Bracelet Watch Band Strap Pebble Time/Pebble Classic",
    "category": "Watches"
  },
  "B000EQS1JW": {
    "parent": 958035625,
    "title": "Citizen Men's BM8180-03E Eco-Drive Stainless Steel Watch with Green Canvas Band",
    "category": "Watches"
  }
}
```

##### Links:

1. [openpyxl documentation](https://openpyxl.readthedocs.io/en/stable/)

2. [openpyxl · PyPI](https://pypi.org/project/openpyxl/)

3. [Reading an excel file using Python openpyxl module - GeeksforGeeks](https://www.geeksforgeeks.org/python-reading-excel-file-using-openpyxl-module/)

4. [A Guide to Excel Spreadsheets in Python With openpyxl – Real Python](https://realpython.com/openpyxl-excel-spreadsheets-python/#importing-new-products-into-a-database)

### NumPy

**Numpy** is a general-purpose array-processing package. It provides a high-performance multidimensional array object, and tools for working with these arrays. It is the fundamental package for scientific computing with Python. 
Besides its obvious scientific uses, Numpy can also be used as an efficient multi-dimensional container of generic data.

Array in Numpy is a table of elements (usually numbers), all of the same type, indexed by a tuple of positive integers. In Numpy, number of dimensions of the array is called rank of the array.A tuple of integers giving the size of the array along each dimension is known as shape of the array. An array class in Numpy is called as **ndarray**. Elements in Numpy arrays are accessed by using square brackets and can be initialized by using nested Python Lists.

##### What’s the difference between a Python list and a NumPy array?

NumPy gives you an enormous range of fast and efficient ways of creating arrays and manipulating numerical data inside them. While a Python list can contain different data types within a single list, all of the elements in a NumPy array should be homogeneous. The mathematical operations that are meant to be performed on arrays would be extremely inefficient if the arrays weren’t homogeneous.

**Why use NumPy?**

NumPy arrays are faster and more compact than Python lists. An array consumes less memory and is convenient to use. NumPy uses much less memory to store data and it provides a mechanism of specifying the data types. This allows the code to be optimized even further.

##### What is an array?

An array is a central data structure of the NumPy library. An array is a grid of values and it contains information about the raw data, how to locate an element, and how to interpret an element. It has a grid of elements that can be indexed in [various ways](https://numpy.org/doc/stable/user/quickstart.html#quickstart-indexing-slicing-and-iterating). The elements are all of the same type, referred to as the array `dtype`.

An array can be indexed by a tuple of nonnegative integers, by booleans, by another array, or by integers. The `rank` of the array is the number of dimensions. The `shape` of the array is a tuple of integers giving the size of the array along each dimension.

One way we can initialize NumPy arrays is from Python lists, using nested lists for two- or higher-dimensional data.

###### Exampe 1: Arrays

```python
import numpy as np

print(20 * "_")
# simple array
array = np.array([1, 2, 3])
print(array)
# [1 2 3]
print(type(array))
#<class 'numpy.ndarray'>


# multidimentional array (matrix)
array = np.array([[1, 2, 3, 4], [5, 6, 7, 8]])
print(array)
# [[1 2 3 4]
#  [5 6 7 8]]
print(array.shape)
#  (2, 4)

```

###### Example 2: NumPy Helper Methods

```python
import numpy as np


# zeros()
array = np.zeros((4, 6))
print(array)
"""
[[0. 0. 0. 0. 0. 0.]
 [0. 0. 0. 0. 0. 0.]
 [0. 0. 0. 0. 0. 0.]
 [0. 0. 0. 0. 0. 0.]]
"""


# ones()
array = np.ones((4, 6), dtype=int)
print(array)
"""
[[1 1 1 1 1 1]
 [1 1 1 1 1 1]
 [1 1 1 1 1 1]
 [1 1 1 1 1 1]]
"""


# full()
array = np.full((4, 6), 11, dtype=int)
print(array)
"""
[[11 11 11 11 11 11]
 [11 11 11 11 11 11]
 [11 11 11 11 11 11]
 [11 11 11 11 11 11]]
"""


# random()
array = np.random.random((2, 3))
print(array)
"""
[[0.89817395 0.14336194 0.54239885]
 [0.52297149 0.07238398 0.0916898 ]]
"""
# accessing the number at first row and first  column
print(array[0, 0])
"""
0.8981739529679694
""""


# using a comparison operator
print(array < 0.5)
"""
[[False  True False]
 [False  True  True]]
"""


# boolean indexing
print(array[array > 0.3])
"""
[0.89817395 0.54239885 0.52297149]
"""
```

###### Example 3: Array Computation

```python
import numpy as np


array = np.array([1, 2, 3, 4, 2.1, 3.9, 5.5, 11.8, 15.7, 13.3])
print(array)
"""
[ 1.   2.   3.   4.   2.1  3.9  5.5 11.8 15.7 13.3]
"""


# sum()
print(np.sum(array))
# 62.3


# floor()
print(np.floor(array))
"""
[ 1.  2.  3.  4.  2.  3.  5. 11. 15. 13.]
"""


# ceil()
print(np.ceil(array))
"""
[ 1.  2.  3.  4.  3.  4.  6. 12. 16. 14.]
"""


# round()
print(np.round(array))
"""
[ 1.  2.  3.  4.  2.  4.  6. 12. 16. 13.]
"""

```

###### Example 4: Perfoming Arithmetic Operations between Numbers and Arrays

```python
import numpy as np


first_array = np.array([111, 333, 555])
second_array = np.array([222, 444, 666])

print(first_array + second_array)   # [ 333  777 1221]
print(first_array + 1)  # [112 334 556]


```

##### Example 5: Unit Conversion (Length)

```python
import numpy as np



# Unit Conversion (Length)
feet = np.array([1, 2, 3, 4, 5])
cm = feet * 30.48
inch = feet * 12
meter = feet * 0.3048
yard = feet * 0.3333
print(cm)
"""
[ 30.48  60.96  91.44 121.92 152.4 ]
"""

print(inch)
"""
[12 24 36 48 60]
"""

print(meter)
"""
[0.3048 0.6096 0.9144 1.2192 1.524 ]

"""

print(yard)
"""
[0.3333 0.6666 0.9999 1.3332 1.6665]
"""

```

##### Links:

1. [NumPy](https://numpy.org/)

2. [numpy · PyPI](https://pypi.org/project/numpy/)

3. [Python Numpy - GeeksforGeeks](https://www.geeksforgeeks.org/python-numpy/)

4. [NumPy - Wikipedia](https://en.wikipedia.org/wiki/NumPy)

5. [1. Introduction to NumPy | Numerical Programming | python-course.eu](https://python-course.eu/numerical-programming/introduction-to-numpy.php)

6. [1.4. NumPy: creating and manipulating numerical data Scipy lecture notes](http://scipy-lectures.org/intro/numpy/index.html)

7. [Array programming - Wikipedia](https://en.wikipedia.org/wiki/Array_programming)

8. [GitHub - numpy/numpy](https://github.com/numpy/numpy)

9. [NumPy Tutorial](https://www.tutorialspoint.com/numpy/index.htm)

10. [Matrix (mathematics) - Wikipedia](https://en.wikipedia.org/wiki/Matrix_(mathematics))

11. [Array Programming With NumPy – Real Python](https://realpython.com/numpy-array-programming/)

12. 

##### Books:

1. **NumPy: Beginner's Guide** by Ivan Idris, Packt Publishing 2015, ISBN: 9781785288838, 1785288830

2. **Guide to NumPy**  by Travis E. Oliphant, Continuum Press 2015, ISBN: 9781517300074, 151730007X

3. **NumPy Simply In Depth** by Ajit Singh and Ravi Kumar Singh

4. **Learning NumPy Array** by Ivan Idris, Packt Publishing 2015, ISBN: 9781783983919, 1783983914

5. **Hands-On Data Analysis with NumPy and Pandas** by Curtis Miller, Packt Publishing 2018, ISBN: 9781789534245, 1789534240
   
   
