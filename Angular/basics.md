
# What is XML?

- XML stands for eXtensible Markup Language
- XML is a markup language much like HTML
- XML was designed to store and transport data
- XML was designed to be self-descriptive
- XML is a W3C Recommendation

- XML is a software- and hardware-independent tool for storing and transporting data.

#### Rule for XML:

1.	There is only one root tag
2.	Xml is case sensitive
3.	Every opening tag needs to closing tag

- Structure of XML: 

```html

<?xml version="1.0" encoding="UTF-8"?>
<note>
  <to>Tove</to>
  <from>Jani</from>
  <heading>Reminder</heading>
  <body>Don't forget me this weekend!</body>
</note>

```
---

### AJAX: 

- AJAX = Asynchronous JavaScript And XML.
- AJAX is not a programming language.

Ajax is a mechanism for making partial page updates. It enables you to update sections of a page with data that comes from the server, avoid full page refresh.

#### AJAX just uses a combination of:
- A browser built-in XMLHttpRequest object (to request data from a web server)
- JavaScript and HTML DOM (to display or use the data)


AJAX Request: 

```js
  var xhttp = new XMLHttpRequest();
  xhttp.onreadystatechange = function() {
    if (this.readyState == 4 && this.status == 200) {
     //  logic after getting response
     document.getElementById("demo").innerHTML = this.responseText;
    }
  };
  xhttp.open("GET", "ajax_info.txt", true);
  xhttp.send();
```
---

### Angular - Ajax: 

- Angular http client uses ajax internally for api calls. 
- Uses XMLHttpRequest (XHR) or fetch(). 
- Sends an asynchronous request using AJAX. 
- Listens for the response. 
- Returns an Observable instead of a Promise. 
- Automatically parses JSON response.

 
#### Why Use Angular HttpClient Instead of Raw AJAX?

- Uses RxJS Observables (Better than Promises).
- Automatically converts JSON data (No need for JSON.parse()).
- Handles HTTP Headers, Authentication, and Interceptors.
- Better Error Handling.

---

#### Xhr vs fetch: 


|Sr.no| XMLHttpRequest (XHR) | fetch() API |
|----------- | ----------- | ----------- |
| 1 | Uses event callbacks (onreadystatechange) | Uses Promise chaining (.then().catch())  |
| 2 | limited flexibility | More flexible and modern  |
| 3 | Requires manual xhr.status checking for error handling | Uses .catch() for cleaner error handling |
| 4 | Caching	Difficult to handle manually | Supports caching via options.cache  |
| 5 | Request Cancellation	Uses .abort() method | Requires AbortController |
| 6 | Progress Tracking	- Supported (xhr.onprogress) | Not directly supported |

---

