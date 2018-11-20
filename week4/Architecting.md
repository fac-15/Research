# Architecting

## 1. Separation of concerns: 

The tasks that are handled in the **back-end** (or **data access layer**) are those outside the browser and involving the server (principally), the database, and the server-side applications. The users don't see them.
For websites' back-end we use frameworks (like **NodeJS**, **Firebase**, **PhantomJS** etc.) or **JAVA**.
The tasks that are handled in the **front end** are all those the final users interact with and happen in a browser.

![something](https://media1.giphy.com/media/SHw5Qx7PdU5kA/giphy.gif?cid=3640f6095bf425f2374d643767d38b30)

### 1.1 Front-end focused tasks
- **Markup** and web languages such as HTML, CSS, JavaScript, and ancillary libraries commonly used in those languages such as Sass or JQuery
- **Asynchronous** request handling and **AJAX**
- **Single-page applications** (with frameworks like React, AngularJS or Vue.js)
- **Web performance** (first meaningful paint, time to interactive, 60 FPS animations and interactions, memory usage, etc)
- **Responsive web design**
- **Cross-browser compatibility** issues and workarounds
- **End-to-end testing** with a headless browser
- **Build automation** to transform and bundle JavaScript files, reduce images size... with tools like Webpack or Gulp.js
- **Search engine optimization**
- **Accessibility** concerns
- Basic usage of image editing tools such as **GIMP** or **Photoshop**
![](https://media3.giphy.com/media/9i9i3cAkMGB56/200w.webp?cid=3640f6095bf428763242532e73da66e4)

### 1.2 Back-end focused
- **Scripting languages** like Node.js, PHP, Python, Ruby, or Perl or Compiled languages like C#, Java or Go
- **Automated testing frameworks** for the language being used
- **Application Data Access**
- **Application Business Logic**
- **Database administration**
- **Scalability** (the capability of a system, network, or process to handle a growing amount of work, or its potential to be enlarged to accommodate that growth)
- **Security concerns**, authentication and authorization
- **Data transformation**
- **Backup** methods and software
![](https://media.giphy.com/media/128kpIwiArqvUk/giphy.gif)



## 2. Client side vs server side: 


Client Side vs. Server Side. Website scripts run in one of two places – the client side, also called the front-end, or the server side, also called the back-end. The client of a website refers to the web browser that is viewing it. In a nutshell:

- **Client Side** - code run in a client's browser, e.g.
    
> <script>document.getElementById('hello').innerHTML = 'Hello';
> </script>

Client side code will be triggered by some form of interaction with the DOM. This may involve just landing on the webpage.

**Front end code:**

*    Executed in the user’s browser
*    Typically reacts to user input
*    Performs DOM manipulation
*    (Usually) can be seen and edited by the user in full - e.g. viewing linked scripts in the dev tools
*    Cannot read files off of a server directly, must communicate via HTTP requests.
*    Can store data for later use, and to work offline (e.g. in localStorage), and with web workers.

Front-end scripting is good for anything that requires user interaction, such as a simple game. Back-end scripting is good for anything that requires dynamic data to be loaded, such as a notice that tells the user they’re logged in.

Server side code can be used to:
*    Store persistent data (user profiles, instatweets, mybook pages, etc.).
*    Cannot be seen by the user (unless something is terribly wrong).
*    Can only respond to HTTP requests for a particular URL, not any kind of user input.
*    Responds to GET, POST, PUT, and DELETE requests.


- Server Side - A server side or back-end language runs its scripts before the HTML is loaded, not after. This will process data outside of the DOM (i.e. in scripts that aren't loaded in the DOM).


[Client vs server side scripting](https://statesmaneffiomedem.wordpress.com/advantages-and-disadvantages-of-client-side-and-server-side-scripting/)

- Server-side pros:
    1.Search engines can crawl the site for better SEO.
    2.The initial page load is faster.
    3.Great for static sites.
- Server-side cons:
    1.Frequent server requests.
    2.An overall slow page rendering.
    3.Full page reloads.
    4.Non-rich site interactions.
- Client-side pros:
    1.Rich site interactions
    2.Fast website rendering after the initial load.
    3.Great for web applications.
    4.Robust selection of JavaScript libraries.
-    Client-side cons:
    1.Low SEO if not implemented correctly.
    2.Initial load might require more time.
    3.In most cases, requires an external library.


## 3. Alternative back-end technologies: 



Here is a list of the best alternatives to NodeJS
>
> - Vert.x (JVM) almost entirely non-blocking (of kernel threads) - this allows it to handle a lot of concurrency (e.g. handle many connections, or messages) using a very small number of kernel threads, which allows it to scale very well

> - coolio.github.io (ruby) 
event driven programming for Ruby


> - PHP 
 is a widely-used open source general-purpose scripting language that is especially suited for web development and can be embedded into HTML.the code is executed on the server, generating HTML which is then sent to the client

> - Python (Django) 
Django is a high-level Python Web framework that encourages rapid development and clean, pragmatic design
    - very fast



Compared to the overall backend space, Node.js (JavaScript) is a drop in the bucket.

In the 90's [**Pearl**](https://www.theperlreview.com/articles/php.html) was the language of choice for most server side development. 

Developers began to realize that using two different languages for the client and server environments was complicating things.

![](https://img.buzzfeed.com/buzzfeed-static/static/2014-03/enhanced/webdr02/27/14/anigif_enhanced-19793-1395945887-2.gif)

The answer was simple: **_put JavaScript on the server._**


Suddenly, every startup on Earth could reuse developers (i.e., resources) on both the client- and server-side

![](https://66.media.tumblr.com/147707098e14944e51974e6f40ec361f/tumblr_p49m4veHai1s141c3o1_500.gif)


#### Pros and Cons [a list taken from here](http://voidcanvas.com/describing-node-js/):
[more pros from medium](https://medium.com/front-end-hacking/why-nodejs-edc95080f56e)

**Pros**
- asynchronous (unlike php for instance, can complete multiple tasks at once)
- reduces number of languages programmers need to be familiar with (JS for both front and back end)
- lots of pre-written open sourced code in node modules
- can stream big files
- built in multithread.
- Works well with frontend DOM manipulation frameworks, such as React
- good for SPA (single page app) - type websites, which are so hot right now
![so hot right now](https://i.gifer.com/3QwL.gif)
- Simplicity, setting up is very quick. You can get away with just a package.JSON and app.js nothing more.
- Non-blocking, asynchronous 


**Cons**
- not great for scalability. Modern servers have multiple cores, and node.js provides no ability to integrate multiple cores
- callback hell - lots of nested callbacks can get confusing
- requires good knowledge of JavaScript to get started
- not good for CPU intensive task
- node modules installed in your typical project have a lot of dependencies, and take up a lot of disk space
(https://img.devrant.com/devrant/rant/r_760537_vKvzh.jpg)
- good judgement is sometimes required to install node modules, as malicious code could be inserted in them or their dependencies. [See this scaremongering post on medium](https://hackernoon.com/im-harvesting-credit-card-numbers-and-passwords-from-your-site-here-s-how-9a8cb347c5b5)




**In short**:
We finally have a way to make web applications with; 
- real-time, 
- _two-way_ connections, 
- where _both_ the client and server can _initiate_ communication, 
- allowing them to exchange data _freely_.
![](https://mir-s3-cdn-cf.behance.net/project_modules/disp/46f6c836224077.57dedf2450286.gif)
(This is in stark contrast to the typical web response paradigm, where the client always initiates communication.)
![](https://i.imgur.com/aGe27wE.gif)


## 4. Writing for different environments: 

**DIFFERENCES BETWEEN NODE AND THE BROWSER:**
- Both the browser and Node use JavaScript as their programming language.
- Building apps that run in the browser is a completely different thing than building a Node.js application.

Despite the fact that it’s always JavaScript, there are some key differences that make the experience radically different.

**What changes is the ecosystem:**

![](https://thumbs.gfycat.com/RawQualifiedHog-size_restricted.gif)

###### In the browser:
- Most of the time what you are doing is interacting with the _DOM_, or other _Web Platform APIs_.
- We don’t have all the nice _APIs_ that Node.js provides through its modules.
- You **don’t** get the luxury to choose what browser your visitors will use.
- Browsers _can be_ a bit slow and sometimes on the web, you are stuck to use older JavaScript / ECMAScript releases.
- You _may_ need to use **Babel** to transform your code from **ES6** to **ES5** before shipping it to the browser.
- We are starting to see the ES Modules standard being implemented.
    - **In practice, for the time being:** use `import`

![](https://cdn-images-1.medium.com/max/1600/1*jAsnJYAPWTmQLs51nJEp7w.gif)


###### In Node:
- The DOM and APIs **do not** exist in Node, (of course). 
- You don’t have **any** of the objects that are provided by the browser.
- You control the environment.
- No need to transform your code (with Babel etc)! 
- Uses the CommonJS module system
    - **In pracice, for the time being:** use `require()`

![](https://cdn.dribbble.com/users/505482/screenshots/1776789/nodejs-dribbble_1.gif)
