# WEB STORAGE 

![](https://media.giphy.com/media/RQSuZfuylVNAY/giphy.gif)
RANDOM GIF FOR YOUR VIEWING PLEASURE. YOU'RE WELCOME 


## What are local storage and session storage and what is the difference between the two?

![](https://giphy.com/gifs/end-by-customer-5JMQL3hcBcWc0)

##### HTML Web Storage, better than cookies. Before HTML5 this data was stored in cookies

#### What is local storage?

Local storage is a JS object.
Local storage can be viewed simplistically as an improvement on cookies, providing much greater storage capacity. Available size is 5MB 

The data is not sent back to the server for every HTTP request 

The data stored in localStorage persists until explicitly deleted. 

It works on same-origin policy. So, data stored will only be available on the same origin. _(Under the policy, a web browser permits scripts contained in a first web page to access data in a second web page, but only if both web pages have the same origin.)_


#### What is session storage?

Session storage method is a javascript object for the current Session. The object holds key values properties within a website browser. These can be discarded when the page session ends. A typical session will survive over page reloads (f5 or refresh) and only terminate when closed. The data stored is specific to the page itself. 
     
We should check if the browser supports Web Storage
    
```javascript
if (typeof(Storage) !== "undefined") {
    // Code for localStorage/sessionStorage.
} else {
    // Sorry! No Web Storage support..
}
```
    

#### What is the difference

The main difference is that the localStorage object stores the data with no expiration date. SessionStorage stores the data for only one session.


## Why would you use cookies vs local/session storage?
#### What are cookies ?

![](https://media.giphy.com/media/l3vRmjIZpfYp8MLwA/giphy.gif)
- Each cookie is essentially a small look-up table containing pairs of key data values which are stored on a users computer by the users web browser. 
- They hold a small amount of data pertinant to the individual user and the website which they are using. 
- This data can be accsessed from the client side or by the webserver and can be used to remember pieces of information that the user previously entered into form fields. 
- Authentication cookies are the most common method used by web server to workout if the user is logged in or not and what account they are logged in with.  
#### pros/cons cookies ?

:heavy_check_mark: **Convenient**: Cookies can be used to personalise a users experience. Allowing things like form auto completion.
:heavy_check_mark:**Personalisation**: Tracking cookies allows for a personalised user experience think amazon's 'recommended for you' list or google's adds.

:x:**Privacy**: Cookie tracking enables web-browsers can keep track of all of the websites that you have visited. Third parties can accses this information. 
:x:**Security**: Many holes have been found in cookie security some being so bad that they have allowed malicious webmasters to gain access to users’ email, different passwords, and credit card information. Developers need to do hashing and use tokens. This is why **encryption is important**. 

***
:cookie::cookie::cookie::cookie::cookie::cookie::cookie::cookie::cookie::cookie::cookie::cookie:cookie segway:cookie::cookie::cookie::cookie::cookie::cookie::cookie::cookie::cookie::cookie::cookie::cookie:
***
![segway gif](https://media.giphy.com/media/T18dP2CYO8Ypy/giphy.gif)

:lock: Decide **how long** your cookie should be valid. The more sensitive the data, the sooner it should expire. Cookies allow you to specify this If both fields are omitted, you get a non-persistent cookie or session-cookie. This means the cookie is automatically removed when your session ends (when the browser is closed). **Session cookies are more secure** than persistent cookies.

:lock: Use **cookie attribute flags** such as 'secure' and  'HttpOnly'.

:lock:Leave the **'Domain' attribute empty**, to avoid subdomains from using the cookie.




## pros/cons local session storage? 


![not safe](https://media.giphy.com/media/mo8MAe2maHrva/giphy.gif)

:heavy_check_mark:**Convenient**: Good for storing non-sensitive data needed within client scripts between pages (for example: preferences, scores in games).

:heavy_check_mark:**Does not need to be sent to your server**: Local session storage allows you to store a lot of data without having to send data back and fourth to and from the server.

:x:**Security**: Can easily be read or changed.

:x:**Not possible to store private tokens here**: When a user clicks on a link, there is no way to specify custom headers that should be sent alongside the HTTP GET request.


## Demo a simple usage of local Storage and Session Storage

Web applications can store data locally within the user's browser

HTML web storage provides two objects for storing data on the client:
- window.localStorage -stores data with no expiration date
- window.sessionStorage - stores data for one session (data is lost when the browser tab is closed)
>// Store
localStorage.setItem("lastname", "Smith");

>// Retrieve
localStorage.getItem("lastname");

>//Remove!
localStorage.removeItem("lastname");

![](https://i.imgur.com/7SjIrsJ.png)

![](https://i.imgur.com/YY8to3X.png)

### Conclusion 
:package: Web storage is good for persisting non-sensative information need to use from page to page: because it can hold more however the data is less protected. 

:lock: Cookies cannot hold as much but are more secure because they can be encrypted. They are best to use for authentication purpouses.  

##### Useful links: 

'what all developers need to know about cookie security' : https://techblog.topdesk.com/security/cookie-security/

'what is the difference between sessionstorage, localstorage and Cookies?'
https://www.quora.com/What-is-the-difference-between-sessionstorage-localstorage-and-Cookies

