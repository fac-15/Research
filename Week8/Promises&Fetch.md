
# Promises and Fetch



## What is a promise
![](https://media.giphy.com/media/4bkntU55gntFV2O58d/giphy.gif)

A promise allows you to transform an async program to continuation passing style:


Callbacks return in order.
    

A promise is an object that may produce a single value some time in the future: either a resolved value, or a reason that it’s not resolved (e.g., a network error occurred). 

## An Incomplete History of Promises
Early implementations of promises began to appear in languages such as Lisp and Prolog as early as the 1980s. The use of the word “promise” was coined by Barbara Liskov and Liuba Shrira in 1988.

Ref: [https://medium.com/javascript-scene/master-the-javascript-interview-what-is-a-promise-27fc71e77261]

Liuba Shrira
<img src="https://i.imgur.com/VSzIkEl.png" style="width: 200px"/>


Barbara Liskov
<img src="https://i.imgur.com/Cowfnwc.png" style="width: 200px"/>



### How Promises Work

Promises are eager, meaning that a promise will start doing whatever task you give it as soon as the promise constructor is invoked. 

A promise is an object which can be returned synchronously from an asynchronous function. It will be in one of 3 possible states:

* Fulfilled:    onFulfilled() will be called (e.g., resolve() was called)
* Rejected:    onRejected() will be called (e.g., reject() was called)
* Pending:    not yet fulfilled or rejected


Promise users can attach callbacks to handle the fulfilled value or the reason for rejection.

``` javascript

const wait = time => new Promise(
   (resolve) => setTimeout(resolve, time));

   wait(3000)
   .then(() => console.log('Hello!')
   ); 
   
   // after waiting 3 seconds console.logs 'Hello!'


```

![and then](https://media1.tenor.com/images/6bb2321834756daa0c3957e346ac464f/tenor.gif?itemid=10273608)

## What is fetch and how do you use it?



 - Same kind of functionality as the XMLHttpRequest

This is what a basic fetch request looks like:
``` javascript=
fetch('http://example.com/movies.json')
  .then(function(response) {
    return response.json();
  })
  .then(function(myJson) {
    console.log(JSON.stringify(myJson));
  });
```
- FETCH takes one argument — **the path to the resource you want to fetch** — and **returns a promise containing the response** (a Response object).

-  What fetch brings back is a HTTP response, and you'll need to extract the JSON body content from it, using the **json() method**

- It can accept a second parameter, an init object that allows you to control a number of different settings such as: 

``` javascript=
    return fetch(url, {
        method: "POST", // *GET, POST, PUT, DELETE, etc.
        mode: "cors", // no-cors, cors, *same-origin
        cache: "no-cache", // *default, no-cache, reload, force-cache, only-if-cached
        credentials: "same-origin", // include, *same-origin, omit
        headers: {
            "Content-Type": "application/json; charset=utf-8",
            // "Content-Type": "application/x-www-form-urlencoded",
        },
        redirect: "follow", // manual, *follow, error
        referrer: "no-referrer", // no-referrer, *client
        body: JSON.stringify(data), // body data type must match "Content-Type" header
    })
```

### SUMMARY 

Fetch() will do all of the things a XMLHttprequest does, and more.

.... and also better, just sayin

![that is so fetch](https://media.giphy.com/media/3oKIPkMhoaMlhtarF6/giphy.gif)



## What advantages do promises provide over callbacks, what are the downsides of using promises?

you pretty much never want to write code that is a mix of callbacks and promises for async operations. If you're moving to promises or introducing some promises, then you probably want to refactor the callbacks in that same section of code into promises.

### Advantages of promises

* Readability over callbacks 
* Easy to catch errors. 
* Simultaneous callbacks

```javascript=
Promise.all([api(), api2(), api3()]).then(function(result){

        //do work with result.
        //result is an array with values of fulfuilled promises
}).catch((error)=>{//handle the error. one api rejected })
```



### Plain callbacks are good for things that promises cannot do:

* Synchronous notifications (such as the callback for Array.prototype.map())
* Notifications that may occur more than once (and thus need to call the callback more than once). Promises are one-shot devices and cannot be used for repeat notifications. Promises only have three states:
**Once they go from pending to resolved or pending to rejected, the state can not be changed.**
* Situations that cannot be mapped into the pending, fulfilled, rejected one-way state model.
**So for example: In place of events that can occur multiple times.**
* Running code that contains promises can be slower than running code that is using callbacks, this might improve over time though.
* There's nothing promises can do that callbacks can't do.


## What are the downsides to using Fetch? i.e. what does fetch not do for you?

![](https://media.giphy.com/media/BkUj9IAaHL2ZW/giphy.gif)

### FETCH<span style='color: red'> DRAWBACKS</span>

* In general ```fetch``` has <span style='color: darkred'>**no way to abort a request**</span>, once it’s done, <span style='color: orange'>**it's done**</span>. 

![](https://66.media.tumblr.com/e809545ec031f0110839ff7b3ec0db64/tumblr_ncc2yofrCN1rz6w0do1_500.gif)
* With Fetch it’s also hard to <span style='color: darkblue'>**measure upload progress**</span>.

### HOW TO <span style='color: red'>CANCEL</span> A FETCH REQUEST

* For a few years after ```fetch``` was introduced, there was no way to <span style='color: darkred'>**abort**</span> a request once opened.
    * Browsers have started to add <span style='color: orange'>_experimental_</span>  support for the ```AbortController``` and ```AbortSignal``` interfaces.
        * <span style='font-size: 14px'>(aka ABORT API)</span>
 ![](https://media.giphy.com/media/G7iGNzr3VBING/giphy.gif)
    * This allows operations like ```fetch``` and ```XHR``` to be <span style='color: darkred'>**aborted**</span> if they have not already completed.

    * You integrate this **API** by passing a signal as a ```fetch``` parameter:
* Meet the AbortController and AbortSignal:
```javascript=
const controller = new AbortController()
const signal = controller.signal

fetch('./file.json', { signal })
```
* The controller only has one method:
```javascript=
controller.abort();
```
* When you do this, it notifies the signal:
```javascript=
signal.addEventListener('abort', () => {
  // Logs true:
  console.log(signal.aborted);
});
```
* Fetch can take an AbortSignal. 
    * For instance, here's how you'd make a fetch timeout after 5 seconds:
```javascript=
setTimeout(() => controller.abort(), 5000);

fetch(url, { signal }).then(response => {
  return response.text();
}).then(text => {
  console.log(text);
});
```
<span style='font-size: 13px'>(When you abort a ```fetch```, it aborts both the ```request``` and ```response```, so any reading of the response body (such as ```response.text()```) is also aborted.)</span>

<span style='color: darkblue'>**Conveniently**, if the fetch already returned, calling <span style='font-size: 20px'>```abort()```</span> won’t cause any error.</span>

<span style='color: darkblue'>When an abort signal occurs, fetch will <span style='color: darkred; font-size: 20px'>**reject**</span> the promise with a ```DOMException``` named ```AbortError```:</span>
```javascript=
fetch(url, { signal })
  .then(response => response.text())
  .then(text => console.log(text))
  .catch(err => {
      if (err.name === 'AbortError') {
        console.log('Fetch aborted');
  } else {
    console.error('Uh oh, an error!', err);
  }
});
```

* By default, ```fetch``` <span style='color: darkred; font-size: 20px'>**won't**</span> ⎆ <span style='color: green; font-size: 18px'>send</span> ⎆ or &nbsp;📨<span style='color: orange; font-size: 18px'>receive</span> 📨 any 🍪<span style='color: brown; font-size: 18px'>cookies</span> 🍪 from the server
* This results in <span style='color: darkred'>**unauthenticated**</span> requests if the site relies on maintaining a user session


* ```fetch``` is not supported by all browsers;
 ![](https://i.makeagif.com/media/5-09-2015/al4lVy.gif)
    * <span style='color: darkblue'>To use ```fetch``` in <span style='color: darkred; font-size: 18px'>**unsupported browsers**</span>, there is a <span style='font-size: 20px'>```Fetch Polyfill```</span> available that <span style='color: darkgreen'>**recreates the functionality**</span> for **non-supporting browsers**.</span>
    
![](https://cdn-images-1.medium.com/max/1600/1*M_hmyl6NjFHXBUYFz3yObA.gif)

Fetch method --> [MDN documentation](https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API/Using_Fetch)
