## About Cookies

Cookies are objects of data, stored in a database on your computer. When a web server has sent a web page to a browser, the connection is shut down, and the server forgets everything about the user. Cookies were invented to solve the problem "how to remember information about the user" by sending the info ( cookie ) with the HTTP header in every request.

### What's inside a cookie?

Cookies are saved in name-value pairs like:
"username=John Doe;
creationdate=10/01/2015;
expirydate=sessionend;
sessionid=13425657;
secure=true;
host=github.com;
value=hello.9428u24891928u3"

### Signed Cookies

Cookies can be "signed" to detect if the client has modified the cookie. It works by taking the value of the current cookie and base64 encoding them with a secret key. When the cookie gets read by the server, the signatures are matched.

### JSON Cookies

Cookies can come stored in various ways, but JSON format is often used. 

## What is cookie-parser?

Cookie-parser takes various types of cookies (signed or unsigned, JSON or string) and converts them into an unsigned object that can be accessed more easily.

JSON cookies are converted to an object. If the cookies are signed, cookie-parser removes the signature before returning the object. If they are already unsigned and given in string format, it simply returns the value as an object. If it does not match, then it will return false.

eg. cookies in the format **"Cho=Kim;Greet=Hello"** are returned as **{ Cho: 'Kim', Greet: 'Hello' }**

### Dependencies

This library relies on two other npm modules: **cookie** and **cookie-signature**.

Cookie is a basic cookie parser and serialiser: a way to read and write HTTP cookie headers.

Cookie-signature provides the functions to sign and unsign cookies. 

## Limitations

* This library must be used on top of Express.js, so is not versatile for other node users.
* Cookie-parser does not provide functionality for decrypting the cookies themselves.

### What is this library useful for?

Cookie-parser is great for reading already-existing cookies and making them usable by the server. However this library does not give functionality for writing cookies.
