# MAKING AN API REQUEST FROM SERVER

![](https://i.imgur.com/rPbf1Vi.png)

1. <i> Research what npm modules are available to make a request from a node server to another server (equivalent of XMLHttpRequest for the server). </i>

    A. <b>Request Library </b> </br>            https://github.com/request/request
    - widely used
    - popular amongst community
    - simple way to make an http request


    B. <b> Using standard HTTP Library & GET </b>
    - built into Node (no need to install dependency)
    - not very user friendly


    ``` javascript
    var http = require('http');
    function getLoginDetails(callback) {
        return http.get({
        host: 'locatemap.in',
        path: '/userDetail'
    }, function(response) {
        // Continuously update stream with data
        var body = '';
        response.on('data', function(d) {
            body += d;
        });
        response.on('end', function() {
        // Data received, let us parse it using JSON!
            var parsed = JSON.parse(body);
            callback({
                userDetail: parsed.name,
                userId: parsed.Id
            });
        });
    });
    }
    ```
    C. <b>Axios Library</b>
    - https://www.npmjs.com/package/axios


    ![](https://i.imgur.com/a6kvIsS.png)



    - Uses promises

     D. <b>Express Library</b>
     - https://expressjs.com/

2. <i> Using a module of your choice, create a node server which makes a request to an online API (it's up to you what one you'd like to use, I'd recommend either Unsplash.it, Guardian, Tesco, or Recipe Puppy), then serve the response when a client requests the home ('/') route of your server.</i>
const https = require("https");

<b>Node-fetch </b>

![](https://i.imgur.com/pbygncC.png)
Fetch is a simpler way to get the api data in. It uses ES6 and Promises.






<b>A simple GET request </b>

Below is a GET request to NASA’s API which get a response to the terminal.
``` javascript
https
  .get("https://api.nasa.gov/planetary/apod?api_key=DEMO_KEY", resp => {
    let data = "";

    // A chunk of data has been recieved.
    resp.on("data", chunk => {
      data += chunk;
    });

    // The whole response has been received. Print out the result.
    resp.on("end", () => {
      console.log(JSON.parse(data).explanation);
    });
  })
  .on("error", err => {
    console.log("Error: " + err.message);
  });
```

``` javascript
node cat.js
Welcome to Mars, NASA Insight.  Yesterday NASA's robotic spacecraft InSight made a dramatic landing on Mars after a six-month trek across the inner Solar System. Needing to brake from 20,000 km per hour to zero in about seven minutes, Insight decelerated by as much as 8  g's and heated up to 1500 degrees Celsius as it deployed a heat shield, a parachute, and at the end, rockets.  The featured image was the first taken by InSight on Mars, and welcome proof that the spacecraft had shed enough speed to land softly and function on the red planet. During its final descent, InSight's rockets kicked up dust which can be seen stuck to the lens cap of the Instrument Context Camera. Past the spotty dirt, parts of the lander that are visible include cover bolts at the bottom and a lander footpad on the lower right. Small rocks are visible across the rusty red soil, while the arc across the top of the image is the Martian horizon dividing land and sky. Over the next few weeks InSight will deploy several scientific instruments, including a rumble-detecting seismometer.  These instruments are expected to give humanity unprecedented data involving the interior of Mars, a region thought to harbor formation clues not only about Mars, but Earth.
```


3. <i>(Bonus), when the server receives the API response, instead of serving the response at the home route, make another GET request to a different API, then combine that response with the original response and serve it to the home route.</i>


## Helpful Links
1. https://www.twilio.com/blog/2017/08/http-requests-in-node-js.html
2. https://codeburst.io/how-to-make-an-http-request-in-nodejs-http-mechanism-libraries-f25ec990d307
