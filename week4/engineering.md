# Engineering

## Modules
To include a module, use the ```require()``` function with the name of the module:
```javascript
var http = require('http');
```
This gives the application access to the HTTP module, and is able to create a server:
```javascript
http.createServer(function (req, res) {
    res.writeHead(200, {'Content-Type': 'text/html'});
    res.end('Hello World!');
}).listen(8080);
```

In this example, we're requiring a pre-existing module. You can require your own modules, through putting ``` module.exports ``` at the end of your file. 

You can only export a single variable - so if you only want to export one function:

```
function addTwo(a){
    return a + 2;
}

module.exports = addTwo;
```

What if you've got **multiple functions** you want to export? You'll need to assign those functions as **methods** on an **object**. 

<img src="https://media.giphy.com/media/1n59if8EmpiBNIvRQx/giphy.gif" width="300px"><br><br>

```javascript
const myObj = {
    function1: function(a){
        return a;
    }
    function2: function(a){
        return a + 1;
    }
}

module.exports = myObj;
```

Creating and exporting different parts of our code as modules allows us to **modularise** our code. It helps with **organisation**, but also crucially makes each module easier to understand, test and refactor -  **independently** of others. 

## Asynchronous functions
#### callBack


* What is a call back?
* What makes a function asynchronous?
* When is a callback called?




```javascript=
let items = [1,2,3]
let totalSize = 0;
     items.forEach((item) => {
         totalSize += item;
     });
     return totalSize;
     
```



```javascript=
function readFileAtTheCafe(filename, callback){

     fs.readFile(filename, "theCafe", function(err, data) {

        if (err){ console.log(error)}

         callback(data);
     });
 };

```

## Input/output _(the fs and path modules)_

<img src="https://media.giphy.com/media/5xtDarztR1rCyfIpMDS/giphy.gif" width="300px"><br><br>
### the fs module

The fs module offers us functionality to **access and interact** with our **file system**. It's a part of **node** - you don't need to install it. Instead, you can simply **require** it, as we did in the workshop earlier:

``` const fs = require('fs'); ```

The fs module has a bunch of useful **methods**, for example in the workshop we used:

```fs.readFile()```

in order to read the contents of a specified file. Some other useful methods include ```fs.appendFile()```, which will append data to a file, or create a new one if no file exists. Can anyone guess the functions of ```fs.mkdir()``` and ```fs.rmdir()```?

Interestingly, all of these methods are **asynchronous by default**.

```javascript
fs.readFile(filePath, function(err, file) {
      if (err) {
        console.log(err);
        return;
      }
      console.log("no error!");
      response.end(file);
    });
```

-- **[Link for node.js docs on the fs module!](https://nodejs.org/api/fs.html)** -- Lists all methods


### Useful: _dirname and _filename
<img src="https://media.giphy.com/media/3o7aCTPPm4OHfRLSH6/giphy.gif" width="300px"><br><br>
Node can tell you where in the file system it is working by using the **_filename** and **_dirname** variables. The **_filename** variable provides the absolute path to the **file** that is currently executing; **_dirname** provides the absolute path to **the working directory** where the file being executed is located. 



### the path module

**The path module** is also a part of node, and as some people did in the workshop, we require it like so: 

``` const path = require("path"); ```

Like the fs module, path has **lots of handy methods**. One example we used earlier is ```path.join()```:

```javascript
var filePath = path.join(__dirname, "..", "public", "index.html");
console.log(filePath);
```
Instead of manually writing out file paths as strings, this allows us to easily pass in variables. There's also no need to include "/"s - the method will join the provided arguments with "/"s between them.

Another good example is ```path.basename()``` - it allows us to extract the the **filename** from a filepath:

```javascript
var path = require('path');
var filename = path.basename('/Users/Refsnes/demo_path.js'));
console.log(filename);
```

Can anyone guess what the console will read?

-- **[Link for node.js docs on the path module!](https://nodejs.org/api/path.html)** -- Lists all methods


## Working with URLs _(the url and querystring modules)_

### URL Strings and URL Objects
* A **URL string** is a structured string containing multiple meaningful components. When parsed, a URL object is returned containing properties for each of these components.

* The **urlObject** (require('url').Url) is created and returned by the url.parse() function. 


### querystring
The ```querystring``` module provides utilities for parsing and formatting URL query strings. It can be accessed using:

```javascript
const querystring = require('querystring');
```

### Query String Methods
```1. escape()``` Returns an escaped querystring
```2. parse()``` Parses the querystring and returns an object
```3. stringify()``` Stringifies an object, and returns a query string
```4. unescape()	``` Returns an unescaped query string

### How are Query String Methods used?
#### ```1. escape()```

 ```javascript
 querystring.escape(str)
 ```
 
* The ```querystring.escape()``` method performs URL percent-encoding on the given ```str``` optimized for the specific requirements of URL query strings.

* The ```querystring.escape()``` method is used by ```querystring.stringify()``` and is generally not expected to be used directly. 

* It is exported primarily to allow application code to provide a replacement percent-encoding** implementation if necessary by assigning ```querystring.escape``` to an alternative function.

> _**What is URL encoding?_
> Encoding certain characters in a URL by replacing them with one or more character triplets that consist of the percent character "%" followed by two hexadecimal digits. The two hexadecimal digits of the triplet(s) represent the numeric value of the replaced character.

##### Before Encoding:
```javascript
www.foundersandcoders.com/thisisatest-for-research-purposes-&-engineering!
```
##### After Encoding:  
```javascript
www.foundersandcoders.com%2Fthisisatest-for-research-purposes-%26-engineering%21
```

##### Unreserved Characters:
_The unreserved characters can be encoded, but should not be encoded. The unreserved characters are:_

```javascript
A B C D E F G H I J K L M N O P Q R S T U V W X Y Z 
a b c d e f g h i j k l m n o p q r s t u v w x y z 0 1 2 3 4 5 6 7 8 9 - _ . ~
```

##### Reserved Characters:
The reserved characters have to be encoded only under certain circumstances. The reserved characters are:

```javscript
! * ' ( ) ; : @ & = + $ , / ? % # [ ]
```
</br>

#### ```2. parse()```
 ```javascript
 querystring.parse(str[, sep[, eq[, options]]])
 ```

 
 The ```querystring.parse()``` method parses a URL query string (```str```) into a collection of key and value pairs.

For example, the query string

```javascript
founders=bar&coders=xyz&abc=123
``` 
is parsed into:

```javascript
{
  founders: 'bar',
  coders: ['xyz', '123']
}
```
 The object returned by the ```querystring.parse()``` method does not prototypically inherit from the JavaScript Object. This means that typical Object methods such as ```obj.toString()```, ```obj.hasOwnProperty()```, and others are not defined and will not work.

By default, percent-encoded characters within the query string will be assumed to use UTF-8 encoding. If an alternative character encoding is used, then an alternative ```decodeURIComponent``` option will need to be specified.


</br>

#### ```3. stringify()```

```javascript
querystring.stringify(obj[, sep[, eq[, options]]])
```
The ```querystring.stringify()``` method produces a URL query string from a given obj by iterating through the object's "own properties".

It serializes the following types of values passed in obj: ```<string>``` | ```<number>``` | ```<boolean>``` | ```<string[]>``` | ```<number[]>``` | ```<boolean[]>``` 
Any other input values will be coerced to empty strings.

```javascript
querystring.stringify({ foo: 'bar', baz: ['qux', 'quux'], corge: '' });
// returns 'foo=bar&baz=qux&baz=quux&corge='

querystring.stringify({ foo: 'bar', baz: 'qux' }, ';', ':');
// returns 'foo:bar;baz:qux'
```

By default, characters requiring percent-encoding within the query string will be encoded as UTF-8. If an alternative encoding is required, then an alternative ```encodeURIComponent``` option will need to be specified:
</br>

#### 4. ```str```

```querystring.unescape(str)```

* The ```querystring.unescape()``` method performs decoding of URL percent-encoded characters on the given ```str```.
* The ```querystring.unescape()``` method is used by ```querystring.parse()``` and is generally not expected to be used directly. It is exported primarily to allow application code to provide a replacement decoding implementation if necessary by assigning ```querystring.unescape``` to an alternative function.



###### Helpful Links:
* https://www.url-encode-decode.com/
* https://nodejs.org/api/querystring.html
