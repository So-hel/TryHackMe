# 🌐 HTTP in Detail — TryHackMe Notes

> **Author:** Sohel  
> **Room:** [HTTP in Detail](https://tryhackme.com/room/httpindetail) — TryHackMe Pre-Security Learning Path  
> **Status:** ✅ Completed

---

## 📌 Table of Contents

- [Task 1 — What is HTTP(S)?](#task-1--what-is-https)
- [Task 2 — Requests and Responses](#task-2--requests-and-responses)
- [Task 3 — HTTP Methods](#task-3--http-methods)
- [Task 4 — HTTP Status Codes](#task-4--http-status-codes)
- [Task 5 — Headers](#task-5--headers)
- [Task 6 — Cookies](#task-6--cookies)
- [Task 7 — Making Requests](#task-7--making-requests)
- [Conclusion](#conclusion)

---

## Task 1 — What is HTTP(S)?

**HTTP (HyperText Transfer Protocol)** is the set of rules used for communicating with web servers to transmit webpage data — whether that's HTML, images, videos, and more.

**HTTPS (HyperText Transfer Protocol Secure)** is the secure version of HTTP. Data sent over HTTPS is encrypted, ensuring that:
- The data cannot be intercepted by third parties (**privacy**)
- You are communicating with the correct server, not an impersonator (**integrity**)

> 🔒 A padlock icon in the browser URL bar indicates an HTTPS connection. Clicking the padlock reveals the certificate details. An invalid or missing certificate triggers a browser warning.

### ❓ Questions & Answers

| Question | Answer |
|----------|--------|
| What does HTTP stand for? | `HyperText Transfer Protocol` |
| What does the S in HTTPS stand for? | `Secure` |
| On the mock webpage, there is an issue — click on it. What is the challenge flag? | `THM{INVALID_HTTP_CERT}` |

---

## Task 2 — Requests and Responses

When you visit a website, your browser sends an **HTTP Request** to the server and receives an **HTTP Response** in return.

### 🔗 Anatomy of a URL

A **URL (Uniform Resource Locator)** is an instruction that tells your browser how to access a resource on the internet.

```
http://user:password@tryhackme.com:80/path/page?id=1#section
  |       |              |          |      |       |      |
Scheme  User:Pass       Host      Port   Path   Query  Fragment
```

| Part | Description | Example |
|------|-------------|---------|
| **Scheme** | Protocol to use for access | `http`, `https`, `ftp` |
| **User** | Optional credentials for authentication | `user:password` |
| **Host** | Domain name or IP address of the server | `tryhackme.com` |
| **Port** | Port to connect to (80 for HTTP, 443 for HTTPS) | `:8080` |
| **Path** | File name or location of the resource | `/blog/article` |
| **Query String** | Extra parameters passed to the path | `?id=1` |
| **Fragment** | Internal page reference (named anchor) | `#section` |

### 📨 Example HTTP Request

```
GET / HTTP/1.1
Host: tryhackme.com
User-Agent: Mozilla/5.0
Accept-Language: en-US
```

### 📩 Example HTTP Response

```
HTTP/1.1 200 OK
Server: nginx/1.15.8
Date: Fri, 29 May 2026 12:00:00 GMT
Content-Type: text/html
Content-Length: 98

<html>...
```

### ❓ Questions & Answers

| Question | Answer |
|----------|--------|
| What HTTP protocol is being used in the above example? | `HTTP/1.1` |
| What response header tells the browser how much data to expect? | `Content-Length` |

---

## Task 3 — HTTP Methods

HTTP methods tell the server what **action** the client wants to perform. Each method has a specific intended use.

### 🔧 Common HTTP Methods

| Method | Purpose | Example Use Case |
|--------|---------|-----------------|
| **GET** | Retrieve information from the server | Viewing a news article or webpage |
| **POST** | Submit data to create a new record | Creating a new user account |
| **PUT** | Submit data to update an existing record | Updating your email address |
| **DELETE** | Remove a record from the server | Deleting an uploaded picture |
| **TRACE** | Performs a loop-back test for debugging | Tracing the path to a resource |

> You'll mostly work with **GET** and **POST** in everyday web interactions.

### ❓ Questions & Answers

| Question | Answer |
|----------|--------|
| What method would be used to create a new user account? | `POST` |
| What method would be used to update your email address? | `PUT` |
| What method would be used to remove a picture you've uploaded? | `DELETE` |
| What method would be used to view a news article? | `GET` |

---

## Task 4 — HTTP Status Codes

Every HTTP response includes a **status code** that tells the browser the outcome of its request.

### 📊 Status Code Ranges

| Range | Category | Meaning |
|-------|----------|---------|
| `100–199` | Informational | Request received, continue sending |
| `200–299` | Success | Request completed successfully |
| `300–399` | Redirection | Client is being redirected elsewhere |
| `400–499` | Client Errors | Something was wrong with the request |
| `500–599` | Server Errors | The server failed to handle the request |

### 📋 Common Status Codes

| Code | Name | Description |
|------|------|-------------|
| `200` | OK | Request was successful |
| `201` | Created | A new resource was created (e.g. new user or blog post) |
| `301` | Permanent Redirect | Page has permanently moved to a new URL |
| `302` | Temporary Redirect | Page has temporarily moved to a new URL |
| `400` | Bad Request | Something was wrong or missing in the request |
| `401` | Not Authorised | Login required to access this resource |
| `403` | Forbidden | No permission to access, even when logged in |
| `404` | Page Not Found | The requested page or resource does not exist |
| `405` | Method Not Allowed | The HTTP method used is not accepted for this resource |
| `500` | Internal Server Error | The server encountered an unexpected error |
| `503` | Service Unavailable | Server is overloaded or down for maintenance |

### ❓ Questions & Answers

| Question | Answer |
|----------|--------|
| What response code might you receive if you've created a new user or blog post? | `201` |
| What response code might you receive if you've tried to access a page that doesn't exist? | `404` |
| What response code if the web server cannot access its database and crashes? | `503` |
| What response code if you try to edit your profile without logging in first? | `401` |

---

## Task 5 — Headers

**Headers** are additional pieces of data sent alongside HTTP requests and responses. They provide context and instructions to both the browser and the server.

### 📤 Common Request Headers (Client → Server)

| Header | Purpose |
|--------|---------|
| `Host` | Tells the server which website is being requested (important when a server hosts multiple sites) |
| `User-Agent` | Identifies the browser software and version so the server can format the response correctly |
| `Content-Length` | Tells the server how much data to expect in the request body |
| `Accept-Encoding` | Lists the compression methods the browser supports |
| `Cookie` | Sends stored cookie data back to the server |

### 📥 Common Response Headers (Server → Client)

| Header | Purpose |
|--------|---------|
| `Set-Cookie` | Sends cookie data to be stored in the browser |
| `Cache-Control` | Specifies how long the browser should cache the response |
| `Content-Type` | Tells the browser what type of data is being returned (HTML, CSS, JSON, image, etc.) |
| `Content-Encoding` | Specifies the compression method used on the response data |

### ❓ Questions & Answers

| Question | Answer |
|----------|--------|
| What header tells the web server what browser is being used? | `User-Agent` |
| What header tells the browser what type of data is being returned? | `Content-Type` |
| What header tells the web server which website is being requested? | `Host` |

---

## Task 6 — Cookies

**Cookies** are small pieces of data stored on your computer by websites. They are set when a server sends a `Set-Cookie` response header, and then sent back to the server with every subsequent request.

### 🍪 How Cookies Work

```
Browser                          Server
   |                               |
   |-------- First Request ------->|
   |                               |
   |<--- Set-Cookie: token=abc123 -|   Server sets a cookie
   |                               |
   |-- Cookie: token=abc123 ------>|   Browser sends cookie on next request
   |                               |
   |<------- Response -------------|   Server identifies the user
```

### 🔐 Why Cookies Matter

Since **HTTP is stateless** (the server has no memory of previous requests), cookies allow websites to:
- Keep users **logged in** across multiple pages
- Remember **personal settings** and preferences
- Track whether you've **visited before**

> Cookie values for authentication are usually a **token** (a unique secret code) rather than plain text like a password.

### ❓ Questions & Answers

| Question | Answer |
|----------|--------|
| Which header is used to save cookies to your computer? | `Set-Cookie` |

---

## Task 7 — Making Requests

The practical involves using an interactive HTTP request tool to manually send different types of requests and retrieve flags.

---

### 🟢 GET `/room`

Set method to `GET`, enter `http://tryhackme.com/room` and click **Go**.

```
GET /room HTTP/1.1
Host: tryhackme.com
User-Agent: Mozilla/5.0 Firefox/87.0
```

```
HTTP/1.1 200 Ok
Server: nginx/1.15.8
Content-Type: text/html; charset=utf-8
Content-Length: 233

<html>
  <body>
    Welcome to the Room page THM{YOU'RE_IN_THE_ROOM}
  </body>
</html>
```

> **Flag:** `THM{YOU'RE_IN_THE_ROOM}`

---

### 🟢 GET `/blog?id=1`

Set method to `GET`, enter `http://tryhackme.com/blog`, click the **gear icon ⚙️** and set parameter `id = 1`.

```
GET /blog?id=1 HTTP/1.1
Host: tryhackme.com
User-Agent: Mozilla/5.0 Firefox/87.0
```

```
HTTP/1.1 200 Ok
Server: nginx/1.15.8
Content-Type: text/html; charset=utf-8
Content-Length: 231

<html>
  <body>
    Viewing Blog article 1 THM{YOU_FOUND_THE_BLOG}
  </body>
</html>
```

> **Flag:** `THM{YOU_FOUND_THE_BLOG}`

---

### 🔴 DELETE `/user/1`

Set method to `DELETE`, enter `http://tryhackme.com/user/1` and click **Go**.

```
DELETE /user/1 HTTP/1.1
Host: tryhackme.com
User-Agent: Mozilla/5.0 Firefox/87.0
Content-Length: 4

id=1
```

```
HTTP/1.1 200 Ok
Server: nginx/1.15.8
Content-Type: text/html; charset=utf-8
Content-Length: 231

<html>
  <body>
    The user has been deleted THM{USER_IS_DELETED}
  </body>
</html>
```

> **Flag:** `THM{USER_IS_DELETED}`

---

### 🟡 PUT `/user/2`

Set method to `PUT`, enter `http://tryhackme.com/user/2`, click the **gear icon ⚙️** and set parameter `username = admin`.

```
PUT /user/2 HTTP/1.1
Host: tryhackme.com
User-Agent: Mozilla/5.0 Firefox/87.0
Content-Length: 14

username=admin
```

```
HTTP/1.1 200 Ok
Server: nginx/1.15.8
Content-Type: text/html; charset=utf-8
Content-Length: 232

<html>
  <body>
    Username changed to admin THM{USER_HAS_UPDATED}
  </body>
</html>
```

> **Flag:** `THM{USER_HAS_UPDATED}`

---

### 🔵 POST `/login`

Set method to `POST`, enter `http://tryhackme.com/login`, click the **gear icon ⚙️** and set `username = thm` and `password = letmein`.

```
POST /login HTTP/1.1
Host: tryhackme.com
User-Agent: Mozilla/5.0 Firefox/87.0
Content-Length: 33

username=thm&password=letmein
```

```
HTTP/1.1 200 Ok
Server: nginx/1.15.8
Content-Type: text/html; charset=utf-8
Content-Length: 237

<html>
  <body>
    You logged in! Welcome Back THM{HTTP_REQUEST_MASTER}
  </body>
</html>
```

> **Flag:** `THM{HTTP_REQUEST_MASTER}`

---

### ❓ Questions & Answers

| Question | Answer |
|----------|--------|
| Make a GET request to /room | `THM{YOU'RE_IN_THE_ROOM}` |
| Make a GET request to /blog with id parameter set to 1 | `THM{YOU_FOUND_THE_BLOG}` |
| Make a DELETE request to /user/1 | `THM{USER_IS_DELETED}` |
| Make a PUT request to /user/2 with username set to admin | `THM{USER_HAS_UPDATED}` |
| POST username thm and password letmein to /login | `THM{HTTP_REQUEST_MASTER}` |

---

## Conclusion

This room covers how web browsers and servers communicate using HTTP:

- 🌐 **HTTP/HTTPS** — HTTP transfers web data; HTTPS adds encryption and verification via certificates
- 🔗 **URL Structure** — Scheme → User → Host → Port → Path → Query String → Fragment
- 🔧 **HTTP Methods** — GET (read), POST (create), PUT (update), DELETE (remove)
- 📊 **Status Codes** — 2xx success, 3xx redirect, 4xx client error, 5xx server error
- 📋 **Headers** — Request headers (Host, User-Agent, Cookie) and Response headers (Set-Cookie, Content-Type, Cache-Control)
- 🍪 **Cookies** — Store session data on the browser; sent back to the server on every request to maintain state

---

*Notes by **Sohel** | TryHackMe Pre-Security Learning Path*
