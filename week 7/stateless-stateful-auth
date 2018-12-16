# Stateful Vs Stateless Authentication

![](https://media.giphy.com/media/l1J9EBp9Dcd6jtsbu/giphy.gif) 

<span style='color:red'>**STATEFUL AUTHENTICATION**</span> = This means that an authentication record or session must be kept **both server and client-side**. 

<span style='color:green'>**STATELESS AUTHENTICATION**</span> = The server **does not keep a record of which users are logged in or which JWTs have been issued**. Instead, every request to the server is accompanied by a token which the server uses to verify the authenticity of the request.


* **The biggest difference** here is that *the user’s state is not stored on the server*, as the state is stored inside the token on the client side instead. Most of the modern web applications use JWT for authentication for reasons including scalability and mobile device authentication.


## Session based authentication (Stateful)
![image](https://cdn-images-1.medium.com/max/1600/1*Hg1gUTXN5E3Nrku0jWCRow.png)

1. User enters their login credentials
2. **Server** verifies the credentials are correct and creates a session which is then **stored in a database**
3. A <span style='color:red'>cookie</span> with the **session ID** is placed in the users browser
4. On subsequent requests, the session ID is verified against the database and if valid the request processed
5. Once a user logs out of the app, the session is destroyed on **both client and server side**.

- **Cookie based** authentication has been the default, tried-and-true method for handling user authentication for a long time.

- <span style='color:red'>**Cookie**</span> based authentication is <span style='color:red'>**stateful**</span>. 

- The server will create a session for the user after the user logs in.
- The session id is then stored on a cookie on the user’s browser / are **stored in the server’s memory**
- The server needs to keep track of active sessions in a database, while on the front-end a cookie is created that holds a session <span style='color:red'>identifier</span>, thus the name _"cookie based authentication"_. 


## Token based authentication (Stateless)
![image](https://cdn-images-1.medium.com/max/1600/1*PDry-Wb8JRquwnikIbJOJQ.png)

1. User enters their login credentials
2. Server verifies the credentials are correct and **returns a signed token**
3. This token is stored **client-side**, most commonly in local storage - but can be stored in session storage or a cookie as well
4. Subsequent requests to the server include this token as an additional Authorization header or through
one of the other methods mentioned above
5. The server decodes the JWT and if the token is valid processes the request
6. Once a user logs out, the token is destroyed client-side, no interaction with the server is necessary.


- Many web applications use JSON Web Token (JWT) instead of sessions for authentication.
- The server creates JWT with a secret and sends the JWT to the client.

- <span style='color:green'>**Token**</span>-based authentication is <span style='color:green'>**stateless**</span>. 

- The token is generally sent as an addition Authorization header in form of Bearer {JWT}, but can additionally be sent in the body of a POST request or even as a query parameter.

![](https://media.giphy.com/media/12OIWdzFhisgww/giphy.gif)

<br/>
<br/>

## What are the advantages and disadvantages of each?

## **Stateful** 🧩
* <span style='color: lightgreen; font-size: 20px'>**Advantages 🤩**</span>
    * <span style='color: green; font-weight: bold'>Revoke the session anytime</span>
        * From the server side.
    * <span style='color: green; font-weight: bold'>Easy to implement and manage for one-session-sever</span>
        * Each session only goes to one server.
    * <span style='color: green; font-weight: bold'>Session data can be changed later</span>
        * (assume that for a one-session-sever, no inconsistency problem)

* <span style='color: darkred; font-size: 20px'>**Disadvantages 😭**</span>
    * <span style='color: red; font-weight: bold'>Increasing server overhead: </span>
        * As the number of logged-in users increases, the more server resources are occupied.
    * <span style='color: red; font-weight: bold'>Fail to scale: </span>
        * If the sessions are distributed in different servers, we need to implement a <span style='color: purple'>_tracking algorithm_</span> to link a <span style='color: blue'>specific user session</span> and the <span style='color: blue'>specific session sever</span>. 
        * That means, once Bob’s session is handled by <span style='color: orange'>**server 'X'**</span>, then all Bob’s following requests must be handled by <span style='color: orange'>**server'X'**</span>. 
        * This can be done by adding a tag to the client request in the proxy layer (<span style='font-size: 14px'>e.g. HAProxy</span> <span style='color: purple; font-size: 12px'>(High Availability Proxy)</span>) before routing to the backend. 
        * The proxy layer uses this tag to determine which backend server route to use.
    * <span style='color: red; font-weight: bold'>Furthermore, if the session servers are deployed with duplication to have fail-over.</span>
        * The problem becomes more complicated since the 2+ peers duplicating each other must implement an algorithm to guarentee the consistency of their sessions.
    * <span style='color: red; font-weight: bold'>Difficult for 3rd party applications to use your credentials: </span>
        * In fact, this is also one of the <span style='color: orange'>“**fail to scale**”</span> examples, but we note it separately since it is <span style='color: blue'>**important**</span>. 
        * When a 3rd party application enables your users to login to their website, the 3rd party application is not able to directly verify each users’ session (they are stored on your backend). 
        * The verification must be redirected to the credential servers. 
        * Therefore, there is more work between 3rd party application and the backend.

## **Stateless** 🔐

* <span style='color: lightgreen; font-size: 20px'>**Advantages 🤩**</span>
    * <span style='color: green; font-weight: bold'>Lower server overhead:</span>
        * The great numbers of sessions data does <span style='color: red'>not</span> store on the server side. 
        * We can store more user properties on the <span style='color: green'>**client-side**</span> to reduce the number of database requests without worrying the memory overhead on the server.
    * <span style='color: green; font-weight: bold'>Easy to <span style='color: green; font-size: 10px;'>S</span><span style='color: green; font-size: 15px;'>C</span><span style='color: green; font-size: 20px;'>A</span><span style='color: green; font-size: 25px;'>L</span><span style='color: green; font-size: 30px;'>E</span>:</span>
        * The advantages of stateless authentication is <span style='color: green; font-size: 20px;'>S</span><span style='color: green; font-size: 22px;'>C</span><span style='color: green; font-size: 24px;'>A</span><span style='color: green; font-size: 26px;'>L</span><span style='color: green; font-size: 28px;'>A</span><span style='color: green; font-size: 30px;'>B</span><span style='color: green; font-size: 32px;'>I</span><span style='color: green; font-size: 34px;'>L</span><span style='color: green; font-size: 36px;'>I</span><span style='color: green; font-size: 38px;'>T</span><span style='color: green; font-size: 40px;'>Y</span>.
        * Since the session data is stored on the <span style='color: green'>**client-side**</span>, it does not matter which backend server the request is routed to. 
        * As long as all backend servers share the same <span style='color: purple'>**private key**</span>, then <span style='color: green'>**ALL**</span> servers have the same capability to verify the validity of the session.
    * <span style='color: green; font-weight: bold'>Good to integrate with 3rd party application: </span>
        * In the single sign-on protocols, the 3rd party applications and IdP <span style='color: purple'>(intergrated data processing)</span> must be able to communicate with each other via user agents <span style='color: purple'>(browser)</span>. 
        * During the account linking process between 3rd party applications and IdP, IdP sends a <span style='color: green; font-weight: bold'>signed message</span> to the browser, and the browser redirects this message to the 3rd party applications. 
        * Using a pre-configured shared <span style='font-size: 20px'>🤫</span><span style='font-size:14px'>secret</span> <span style='font-size: 20px'>🤫</span>, the 3rd party applications can determine whether the account linking (single sign-on) is valid by itself.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;![](https://engineering.giphy.com/wp-content/uploads/2018/01/fiking.gif)

* <span style='color: darkred; font-size: 20px'>**Disadvantages 😭**</span>
    * <span style='color: red; font-weight: bold'>Cannot revoke the session anytime: </span>
        * Since the user session is stored on the client side, the server does not have any rights to <span style='color: red'>**delete**</span> the session.
    * <span style='color: red; font-weight: bold'>Relatively complex to implement for one-session-server scenario: </span>
        * One of the greatest advantages of stateless authentication is <span style='color: green; font-size: 20px;'>S</span><span style='color: green; font-size: 22px;'>C</span><span style='color: green; font-size: 24px;'>A</span><span style='color: green; font-size: 26px;'>L</span><span style='color: green; font-size: 28px;'>A</span><span style='color: green; font-size: 30px;'>B</span><span style='color: green; font-size: 32px;'>I</span><span style='color: green; font-size: 34px;'>L</span><span style='color: green; font-size: 36px;'>I</span><span style='color: green; font-size: 38px;'>T</span><span style='color: green; font-size: 40px;'>Y</span> <span style='color: red; font-size: 20px;'>...however</span>, it increases the technical complexity and it is not extremely useful when we only have a one-session-server.
    * <span style='color: red; font-weight: bold'>Session data cannot be changed until its expiration time: </span>
        * Suppose we want to add “Age” property to the session data above.
        * Since its session data is not expired yet, the client still has the chance to make requests with old session data.
        * We can ask the client to update it, but we <span style='color:red'>_**cannot**_</span> make sure the client <span style='color:green'>_**does update**_</span>  it. 
        

![](https://media.giphy.com/media/3og0IMJcSI8p6hYQXS/giphy.gif)
