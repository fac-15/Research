# [Session-management in Express](https://github.com/foundersandcoders/master-reference/blob/master/coursebook/week-8/research-afternoon.md#session-management-in-express)

**TLDR:** [This might work ok](https://medium.com/@evangow/server-authentication-basics-express-sessions-passport-and-curl-359b7456003d)

![](https://media.giphy.com/media/3o6gDRuqYeG11VeBG0/giphy.gif)

 ## What are sessions?
 #### In IT, the word "session" is a reference to a certain time frame for communication between two devices, two systems or two parts of a system.
 #### A session begins when a user logs in to or accesses a particular program or web page and ends when the user logs out, closes the program or web page. A session can temporarily store information related to the activities of the user while connected. A session cookie is used in web pages for storing information in case the user leaves the web page or closes down their browser. For example, this is one way a website can remember what is in your shopping cart if you leave and come back.
 
 #### Websites requiring a username and password use session variables to help transfer data between web pages, but only while the user is logged in. 
 
 express-session: parses session cookie, validates it, etc.
 
session-file-store: saves the session object in JSON files in the local folder (sessions by default). This is not as advanced as other sessions stores, but great for debugging and learning

morgan: is the usual logger middleware for Express

 ## What are the different ways of managing sessions in express?
 
 **Use [express-session](https://www.npmjs.com/package/express-session) (obvs!)**
 
 [A Tutorial we could try out](https://codeforgeek.com/2014/09/manage-session-using-node-js-express-4/). Caveat: uses bodyParser, deprecated at time of this article (2014). **Update:** [ Seems to be active though](https://www.npmjs.com/package/body-parser), probably not something to worry about
 
 [A newer tutorial](https://flaviocopes.com/express-sessions/)
 
 **Mozilla [node-client-sessions](https://github.com/mozilla/node-client-sessions)**
 - [on stormpath.com](https://stormpath.com/blog/everything-you-ever-wanted-to-know-about-node-dot-js-sessions)
 - [Github repo](https://github.com/mozilla/node-client-sessions). Last updated April 2017.

### Session Storage
> All solutions store the session id in a cookie, and keep the data server-side. The client will receive the session id in a cookie, and will send it along with every HTTP request
- Can be achieved with client side cookies, e.g. with `cookie-session`.
- With a memory cache, such as `Redis`

 ## Create a minimal example of how to set up a session
 
 In order to better understand sessions in express, we followed this tutorial from [Code For Geek](https://codeforgeek.com/2014/09/manage-session-using-node-js-express-4/).
 
 It is a little outdated however, and there were some bugs:
1. On copying and running the code (```npm start```) we received this error:
![](https://i.imgur.com/b2KUGMt.png)
Which we fixed after finding this post:
![](https://i.imgur.com/kOCakoB.png)

The original code included:
```javascript
app.use(session({secret: 'ssshhhhh'}))
```

Which worked once amended to:
```javascript
app.use(
  session({
    secret: "alyssassecret",
    resave: true,
    saveUninitialized: true
  })
);
```

2. The original code had the following handler:
```javascript
app.get('/admin',function(req,res){
  sess = req.session;
if(sess.email) {
res.write('
<h1>Hello '+sess.email+'</h1>
');
res.end('<a href="+">Logout</a>');
} else {
    res.write('
     <h1>Please login first.</h1>
    ');
    res.end('<a href="+">Login</a>');
}
});
```
We encountered bugs both with the fact that there are multi-line strings using regular quotes, and that the hrefs of the a tags are not specific. By changing the strings to template literals and defining the paths, everything worked:
```javascript
app.get("/admin", function(req, res) {
  sess = req.session;
  if (sess.email) {
    res.write(`<h1>Hello ${sess.email} </h1>`);
    res.end('<a href="/logout">Logout</a>');
  } else {
    res.write(`<h1>Please login first.</h1>`);
    res.end('<a href="/">Login</a>');
  }
});
```

tutorial on Node.js Server & Authentication Basics: Express, Sessions, Passport, and cURL

https://medium.com/@evangow/server-authentication-basics-express-sessions-passport-and-curl-359b7456003d
