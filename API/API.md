# API and Web Service Introduction

## 1. API

### 1.1 - What is an API?

API is an acronym.

* **A (Application):** Software that does a task

* **P (Programming):**  Program (P) that does the task in the Application (A)

* **I (Interface):** Place (I) to tell the program (P) to run

An API exists where you can tell (I) a computer program (p) to run in an application (A).

In other words, you tell a program to run s.th which you don't own it.

What makes APIs great?

* Just use the program don't write it!

* Platform independent

* Upgrade safe

### 1.2 API Excercise

**Interface(I):** From where are you telling the program what to run?

**Program(P):** What task is being done/what does program d?

**Application(A):** What software has the program being run?

| Level of Difficulty | Example                                              | I (Interface)      | P (Program)  | A (Application) |
|:-------------------:| ---------------------------------------------------- | ------------------ | ------------ | --------------- |
| Simple              | Viber message using cell phone                       | Cell phone         | Messaging    | Viber           |
| Simple              | google search using computer                         | Computer(Broweser) | Search       | Google          |
| Moderate            | Create orders in eBay when you get them (no Browser) | eBay               | Create order | eBay            |
| Moderate            | Create order in SAP when you get them (no Browser)   | SAP                | Create order | SAP             |

[Good Web site for searching APIs](https://programmableweb.com)

### 1.3 API Details

3 things happen in every API transaction:

1. **Request:** A request is made fo something to be done.

2. **Program:** A program is run to complete that requset.

3. **Response:** Sending Back response.

Example:

In browser(http client): 

    www.google.com/search?q=tuna

        q: search term (query)

    www.google.com/searrch?tbm=isch&q=tuna

        tbm: To Be Matched

        isch: Image Search

---

## 2. Web Service

### 2.1 What is a web service?

**Web:** internet

**Service:** API

**Web Service:** API that uses the internet

:memo: So, all web services is an API.

:bulb: But not all APIs are web services. Not all APIs use the internet.

Web Services use:

* **XML** or **JSON** to format data over the internet.

* REST, SOAP, or XML/RPC to transfer that data.

---

## 3. HTTP

### 3.1 Introduction to HTTP

**HTTP:** HyperText Transfer Protocol

* **HyperText**
  
  * What does regular text do? Nothong
  
  * HTTP make the text special in order to hyper(send) to somewhere else. 

HTTP request & response includes:

1. **Start line** (Mandatory) 

2. **Headers** 

3. **Blank Line** (Just seperate headers from body)

4. **Body**

| HTTP           | Request                                                        | Response                                |
| -------------- | -------------------------------------------------------------- | --------------------------------------- |
| Start Line     | HTTP **Version** (v1.1) <br>**Method** (GET,POST, PUT, DELETE) | HTTP Version (v1.1) <br>**Status Code** |
| Header<u>s</u> | HOST: url.domain.com, Token: xxxxxx                            | Cookie1, Cookie2                        |
| Blank Line     |                                                                |                                         |
| Body           | username, password                                             | HTML(web page)                          |

### 3.2 HTTP Parts

#### 3.2.1 HTTP Start Line

##### 3.2.1.1 Request

**Name:** Start Line, Request Line

**HTTP Version:** HTTP/1.1

**Method:** GET, POST, PUT, DELETE, etc

**API Program Folder Location:** Yes (example: /search)

**Parameters:** Yes (example: ?q=tuna)

**Status Code:** No

**Format:** Method(space)API Progran Folder Location+Parameters(space) HTTP Version

**Example:** GET /search?q=tuna HTTP/1.1

##### 3.2.1.2 Response

**Name:** Start Line, Response Line, Status Line

**HTTP Version:** HTTP/1.1

**Method:** No

**API Program Folder Location:** No

**Parameters:** No

**Status Code:** Yes (example: 200 OK)

**Format:** HTTP Version + Status Code

**Example:** HTTP/1.1 200 OK

|                                 | Request                                                                 | Response                               |
| ------------------------------- | ----------------------------------------------------------------------- | -------------------------------------- |
| **Name**                        | Start Line, Request Line                                                | Start Line, Response Line, Status Line |
| **HTTP Version**                | HTTP/1.1                                                                | HTTP/1.1                               |
| **Method**                      | GET, POST, PUT, DELETE, etc                                             | No                                     |
| **API Program Folder Location** | Yes (example: /search)                                                  | No                                     |
| **Parameters**                  | Yes (example: ?q=tuna)                                                  | No                                     |
| **Status Code**                 | No                                                                      | Yes (example: 200 OK)                  |
| **Format**                      | Method(space)API Progran Folder Location+Parameters(space) HTTP Version | HTTP Version + Status Code             |
| **Example**                     | GET /search?q=tuna HTTP/1.1                                             | HTTP/1.1 200 OK                        |

##### 3.2.1.3 What is idempotence?

Can do as many times as you want and result stay the same.

In other words: **Safe** to repeat

| Method | Idemptent (safe to repeat) |
| ------ | -------------------------- |
| GET    | Yes                        |
| POST   | No                         |
| PUT    | Yes                        |
| DELETE | Yes                        |

##### 3.2.1.4 Review

:question: **What is in the request HTTP start line?**

:arrow_right_hook:  Method, API Program Folder (optional), Parameter(s) (optional), HTTP Version

:question: What is in the response HTTP start line?

:arrow_right_hook: HTTP Version, Status Code

:question: Which HTTP start line method is not idempotent?

:arrow_right_hook: POST

#### 3.2.2 HTTP Headers

##### 3.2.2.1 Request fields

**Accept-Language:** List of acceptable human languages for response

**Authorization:** Authentication credentials for [HTTP authentication](https://en.wikipedia.org/wiki/Basic_access_authentication)

**Cache-Control:**  Used to specify directives that *must* be obeyed by all caching mechanisms along the request-response chain.

**Content-Type:** The [Media type](https://en.wikipedia.org/wiki/Media_type "Media type") of the body of the request (used with POST and PUT requests).

**Date:** The date and time at which the message was originated (in "HTTP-date" format as defined by RFC 9110: HTTP Semantics, section 5.6.7 "Date/Time Formats").

**Host:** The domain name of the server (for [virtual hosting](https://en.wikipedia.org/wiki/Virtual_hosting "Virtual hosting")), and the [TCP port](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers "List of TCP and UDP port numbers") number on which the server is listening. The [port](https://en.wikipedia.org/wiki/Port_(computer_networking) "Port (computer networking)") number may be omitted if the port is the standard port for the service requested. Mandatory since HTTP/1.1.

##### 3.2.2.2 Response field

**Cache-Control:** Tells all caching mechanisms from server to client whether they may cache this object. It is measured in seconds.

**Date:** The date and time that the message was sent (in "HTTP-date" format as defined by RFC 9110)

**Expiers:** Gives the date/time after which the response is considered stale (in "HTTP-date" format as defined by RFC 9110)

**Set-Cookie:** An [HTTP cookie](https://en.wikipedia.org/wiki/HTTP_cookie "HTTP cookie")

**Server:** A name for the server

Links

1. [List of HTTP header fields - Wikipedia](https://en.wikipedia.org/wiki/List_of_HTTP_header_fields)

2. [RFC 9110 - HTTP Semantics](https://www.rfc-editor.org/rfc/rfc9110.html)

3. [RFC 9111 - HTTP Caching](https://datatracker.ietf.org/doc/html/rfc9111)

4. [📄 HTTP Documentation](https://httpwg.org/specs/)

5. 
