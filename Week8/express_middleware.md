# Express Middleware

![](https://media.giphy.com/media/w7mLEAMcpjrpe/giphy.gif)

## What are express middlewares?

- Middleware are functions that have access to the **`request`** object, the **`response`** object, and the **`next`** middleware function in the application’s request-response cycle. 

- If we think of our previous projects, middlewares are like our **`router`** `if` statements which received the request and interpreted it before handling each req and res.

- Express is a **routing and middleware web framework** that has minimal functionality of its own: An Express application is essentially a series of middleware function calls.

**A good analogy is to imagine yourself as a business owner looking to open a restaurant:**

![](https://i.imgur.com/jn630VH.png)

1. `set up express`: Hire a manager
2. `app.use()`: Define what to do before accepting customer requests
3. `app.get()`: Determine what to do with specific customer requests once they come in
4. `app.listen`: Determine the address for the location where all this will happen

### The process:

1. A web server takes in a `request` and outputs a `response`. 
2. `Middlewares` are functions executed **in the middle** after the incoming request. 
3. Middlewares produce an output which could be the **final** output passed or could be used by the **next middleware** until the cycle is completed.


#### The `next` argument

<iframe src="https://giphy.com/embed/l0HlJiVs2oAtVet0c" width="480" height="268" frameBorder="0" class="giphy-embed" allowFullScreen></iframe>

- We can have more than one middleware and they will execute in the order they are declared. 
- The `next()` function, when invoked, executes the middleware succeeding the current middleware.
- Crucially, it **carries across** to the next middleware any modifications you've made to the `req` and `res` objects.
- Middleware functions are the perfect place to modify the `req` and `res` objects with relevant information. For instance, after a user has logged in, you could fetch their user details from a database, and then store those details in `res.user`.
- Unless you're calling the final function that ends the request and response, if you don't call **`next()`**, you won't pass onto the next middleware function and your request will just hang and eventually timeout!

![](https://media.giphy.com/media/p5S2Qg4a9snKg/giphy.gif)

### An Express application can use the following types of middleware:

**Application-level middleware**

- These are  written either using **app.use()** or **app.METHOD()** - for example **app.get()** or **app.post()**! 
- We've already had experience writing application-level middleware. Here's an example:

```
app.get('/dogs', function (req, res, next) {
  res.send('dogs')
})

```

**Router-level middleware**
- Router-level middleware works in the same way as the application-level middleware above, except it is bound to an instance of express.Router().
- What is express.Router()?

**Error-handling middleware**
- Important: error-handling middleware takes **4 arguments** like so: ``` (err, req, res, next) ```.

**Built-in middleware**

- There are three important **built-in** Express middleware functions:
- **```express.static```**: 
helps to serve static files such as images, CSS files, and JavaScript files. For example: ``` app.use(express.static('public')) ``` will let Express know where to look for your static files - and you'll just have to retrieve those files like so: ``` http://localhost:3000/images/kitten.jpg``` or ```http://localhost:3000/css/style.css```
- **```express.json```**: 
parses incoming requests with JSON payloads!
- **```express.urlencoded```**: 
parses incoming requests with URL-encoded payloads

**Third-party middleware**
- We've already used some of these - like ```morgan```, ```compression```, and ```serve-favicon```. 
- You'll need to ``` npm i ``` these, as well as requiring them!
- Here's a list of popular middleware modules: https://expressjs.com/en/resources/middleware.html


## What functionality do they provide?

- **Take action** on any incoming request and modify it before sending back a response:

![](https://i.imgur.com/lKwcWBJ.png)

## Using middleware

- **Retrieving important objects from a database**
A common architecture is having many routes that in some way manipulate or output data of the same database object, so a middleware can be used to retrieve that object and error out if it’s not found or access is not allowed:

``` 
function dbMiddleware (req, res, next) {
  getFromDb(req.params.id) //see app.get below
  .then(function(data) {
    req.dbData = data
    next()
  })
  .catch(function (error) {
    res.status(500).end() //replace with proper error handling
  })
}
app.get('/data/:id', [dbMiddleware], handler)
```

In the previous example, the handler will now only be called if the data was successfully added to the Request object, so no further error handling or database code is needed here. Also note how I’m using the id value from the route.

- **Authentication**
The most common example is authentication, so you can have a reference to the current User object in all routes:

```
function userMiddleware (req, res, next) {
  getUserViaJWT(req.headers.authentication)
  .then(function(user) {
    req.user = user
    next()
  })
  .catch(function (error) {
    res.status(401).end() //replace with proper error handling
  })
}
app.use(userMiddleware)
app.get('/someroute', handler)
```

That middleware just parses an authentication header and uses it to determine which user is currently logged in and adds it to the Request object. Again, if there is an error, it will just end the response and not call subsequent middlewares or the route Handler.

- **Logging**
You could also use middlewares for logging, like the following to log the latest activity of a user, this could be used in combination with the previous middleware to get the user object:

```
function logMiddleware (req, res, next) {
  logLastActiveAt(req.user.id, new Date())
  next()
}
app.use(userMiddleware)
app.use(logMiddleware)
app.get('/someroute', handler)
```

## What are some examples of useful express middleware and how do you use them (several useful examples)

**1. Using ``` app.get ``` and writing our own authentication function in order to check that the user is logged in:**


![](https://i.imgur.com/Q74OZIp.png)


**2. Using ```morgan``` in order to create an access log of the HTTP request:**

Create a write stream, so morgan will know where to write the log:

```
const accessLogStream = fs.createWriteStream(
  path.join(__dirname, '..', 'logs-demo', 'access.log'),
  { flags: 'a' }
);
```

and then call ```morgan```, with two args - the format of the log, and where to write the stream:
```

app.use(morgan('combined', { stream: accessLogStream }));
```

**A list of popular middleware modules:**

![](https://i.imgur.com/oeCcu79.png)
![](https://i.imgur.com/r2JJws4.png)


- [Compression](https://www.npmjs.com/package/compression): 
    - makes requests lighter and load faster
    - responsible for compacting the JSON responses and also the static files which your application will serve to GZIP format, a compatible format to several browsers

- [Handlebars](https://www.npmjs.com/package/handlebars): 
    - Handlebars.js is an extension to the Mustache templating language created by Chris Wanstrath.
    - Handlebars.js and Mustache are both logicless **templating languages** that keep the view and the code separated like we all know they should be.

- [CORS](https://www.npmjs.com/package/cors): 
    - CORS (Cross-origin resource sharing) is an important HTTP mechanism
    - Responsible for allowing (or not) asynchronous requests from other domains.
