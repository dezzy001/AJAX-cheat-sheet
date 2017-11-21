# AJAX-cheat-sheet
resource: https://www.w3schools.com/js/js_ajax_intro.asp

# AJAX Introduction #
## What is AJAX? ##
* Summary:
  * AJAX allows web pages to be updated __asynchronously__ by exchanging data with a web server behind the scenes.
  * This means that it is possible to update parts of a web page, without reloading the whole page.
* AJAX = **A**synchronous **J**avascript **A**nd **X**ML
* Not a programming language
* how AJAX works: <br> <img src="https://github.com/dezzy001/AJAX-cheat-sheet/blob/master/AJAX%20image1.png" width="450px">
## The XMLHttpRequest Object ##
* Modern browsers (e.g Chrome, Firefox, etc..) support XMLHttpRequestobject
  * For security reasons, modern browsers do not allow access across domains.
  * Your files (e.g XML) must be located on your own server with the webpage you are using
* Older browsers (e.g IE5/6) use ActiveX objects instead.
* To Handle both cases, use: 
```
if (window.XMLHttpRequest) {
  // code for modern browsers
  xmlhttp = new XMLHttpRequest();
} else {
  // code for old IE browsers
  xmlhttp = new ActiveXObject("Microsoft.XMLHTTP");
}
```
### XMLHttpRequest Object Methods ###
Method|Description
------|-----------
var = new XMLHttpRequest()|creates a new XMLHttpRequest object
abort()|Cancels the current request
open(method, url, async, user, psw)|Specifies the request<br><br>method: the request type (GET or POST)<br> url: the file location<br>async: true or false (asynchronous or synchronous)<br>user: username (_optional_)<br>psw: password (_optional_)
send()|Sends the request to the server <br> Used for GET requests
send(_string_)|Sends the request to the server <br> Used for POST requests
getAllResponseHeaders()|Returns header information
getResponseHeader()|Returns specific header information
setRequestHeader()|Adds a label/value pair to header to be sent

### XMLHttpRequest Object Properties ###
Property|Description
--------|-----------
onreadystatechange|Defines a function to be called when the readyState property changes
readyState|	Holds the status of the XMLHttpRequest.<br>0: request not initialized<br>1: server connection established<br>2: request received <br>3: processing request <br>4: request finished and response is ready
responseText|	Returns the response data as a string
responseXML|Returns the response data as XML data
status|Returns the status-number of a request <br>200: "OK" <br>403: "Forbidden" <br>404: "Not Found" <br>For a complete list go to the Http Messages Reference
statusText|	Returns the status-text (e.g. "OK" or "Not Found")

* Sample code:
```
<!DOCTYPE html>
<html>
<body>

<h2>The XMLHttpRequest Object</h2>

<p id="demo">Let AJAX change this text.</p>

<button type="button" onclick="loadDoc()">Change Content</button>

<script>
function loadDoc() {
  var xhttp;
  if (window.XMLHttpRequest) {
    // code for modern browsers
    xhttp = new XMLHttpRequest();
    } else {
    // code for IE6, IE5
    xhttp = new ActiveXObject("Microsoft.XMLHTTP");
  }
  xhttp.onreadystatechange = function() {
    if (this.readyState == 4 && this.status == 200) {
      document.getElementById("demo").innerHTML = this.responseText;
    }
  };
  xhttp.open("GET", "ajax_info.txt", true);
  xhttp.send();
}
</script>

</body>
</html>

```
