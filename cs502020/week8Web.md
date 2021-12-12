- [Home](../index.md)
---
# Web Track
**What is IpV4/6**

Ipv4 - 32bit - IP addresses which is limited to 4billion
1pv6 - 128bit - IP addresses which is new and due to the limitation above
## **PORTS**

<pre>
Service     Ports
FTP         21      File transfer protocol
SMTP	    25      Commonly used for email
HTTP	    80      For sending messaging information in the form of web pages
...         ...     Many more ports available and thats for another time!!!
</pre>

## An example of an IP address:*
1.2.3.4:80	IpAdress/Port(80) which is for HTTP
	
***	
**How do URLs relates to IP Addresses?**
## DNS	
**It's just a mapping between a URL and an IP address**

| URL         | IP ADDRESS    |
| ----------- | ------------- |
| google.com  | 171.217.7.206 |
| harvard.edu | 23.22.75.102  |
| yale.edu    | 104.16.243.4  |

**DNS** are just servers that knows which URL belongs to which IP address  

---

# HTTP 
**Hiper Text Transfer Protocol**  
*Yet another protocol on the internet*

HTTP is actually what's inside the envelope, whats the content inside!!!  

**Inside** of the envelope we might see content like this.  

**Get - Request**  
`GET    /   HTTP/1.1`  
`Host: www.example.com`  
GET - Is an request  
/ - Is where you want to go, in this case, is the root.

**Response**  
`HTTP/1.1   200     ok`   
`Content-Type: text/html`  
HTTP/1.1 - is the version of HTTP protocol that is being used in order to comunicate this infomation  
200 - Status code, specifies the how the response was resolved  
OK - is the status  
Content-Type: text/html - is the type that was returned

## HTTP Status Codes
| Status Code | Description           |
| :-----------: | :---------------------: |
| 200         | OK                    |
| 301         | Moved Permanently     |
| 403         | Forbidden             |
| 404         | Not Found             |
| 500         | Internal Server Error |  

---  

# HTML  

```html
<!DOCTYPE html>
<html lang="en">
    <head>
        <title>
            Hello!
        </title>
    </head>
    <body>
        Hello, world!
    </body>
</html>
```

## HTML Tags
**Image Tag**
```html
<!-- Image tag -->
<img src="quick_meals.jpeg" alt="Picture of a doughnut">
```

<img src="quick_meals.jpeg" alt="Picture of a doughnut"></img>
---
**Anchor Tag**
```html
<!-- Anchor Link tag -->
<a href="https://harvard.edu">Visit harvard</a>
```
An HTML link to visit <a href="https://harvard.edu">Harvard</a>
---
**HTML Table**
```html
<table>
    <tr>
        <td>cell 1</td>
        <td>cell 2</td>
        <td>cell 3</td>
    </tr>
    <tr>
        <td>cell 4</td>
        <td>cell 5</td>
        <td>cell 6</td>
    </tr>
</table>
```
<table>
    <tr>
        <th>cell 1</th>
        <th>cell 2</th>
        <th>cell 3</th>
    </tr>
    <tr>
        <td>cell 4</td>
        <td>cell 5</td>
        <td>cell 6</td>
    </tr>
</table>

---
**HTML Form**
```html
<form action="https://www.google.com/search" method="get">
    <input name="q" type="text"></input>
    <input type="submit" value="Search Google"></input>
</form>
```  

<form action="https://www.google.com/search" method="get">
    <input name="q" type="text"></input>
    <input type="submit" value="Search Google"></input>
</form>  

---



  



