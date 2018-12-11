# :unlock: HTTP vs HTTPS :lock: 

![http vs https diagram](https://i.imgur.com/vOpiP3I.png)

## How does HTTPS work? What are TLS/SSL certificates?

![](https://i.imgur.com/zWE2zgH.png)

Think of an SSL/TLS certificate as a driver’s license of sorts—it serves two functions. 

It grants permissions to use encrypted communication via Public Key Infrastructure, and also authenticates the identity of the certificate’s holder.

- <b>HTTPS</b> (Hyper Text Transfer Protocol Secure) is the secure version of HTTP
- HTTPS encripts all communication between your computer and the browser

- SSL and TLS are both cryptographic protocols that provide authentication and data encryption between servers, machines and applications operating over a network 

- HTTPS is nothing more than the HTTP protocol on top of SSL/TLS!

### A HTTPS Handshake 🤝🏼

![](https://media.giphy.com/media/36otikFtpDJq8/giphy.gif)

![](https://dab1nmslvvntp.cloudfront.net/wp-content/uploads/2015/09/1442392132sequence.png)

- The web browser connects to the server using SSL/HTTPS.
- The server responds with the **certificate** (i.e SSL/TLS), which includes the **public key**. 
- The web browser then looks at this response, in particular at the **signature** on the certificate. If the signature is part of the browser's trusted store, it verifies the certificate, and agrees to the key exchange, enabling the private key. 
- The web browser gives the cipher spec, and once this is confirmed by the server, **encrypted data** can be exchanged. Woohoo!!


  
### Certificates  

#### <i> SSL </i> (Secure Socket Layer) & <i> TLS </i> (Transport Layer Security) certificates

![](https://i.imgur.com/W4eRLVj.png)
- TLS was developed as an upgrade to SSL, in response to various vulnerabilities (such as the POODLE attack in 2014!)
![](https://media.giphy.com/media/nT5udSPy3Ocjm/giphy.gif)


- TLS is basically a **more secure** version of SSL.

- SSL/TLS use **the public and private key system** for data encryption and data integrity.

- What are **Public** and **Private Keys**?
 -- Two keys that are mathematically related (they belong as a key pair), but are essentially **different**.
 -- This means a message encrypted with a public key **cannot** be decrypted with the same public key.

- **Almost all** encryption **methods** in use today employ public and private keys.


## Why is it important to implement HTTPS in your projects?



![lock gif](https://media.giphy.com/media/OTnDHCCFNZHwc/giphy.gif)

![](https://i.imgur.com/JmQzkVO.png)

![](https://i.imgur.com/4wJiKje.png)

- From 2017 Chrome has stated displaying "not secure" in the browser bar for any http sites that ask users for login or credit card information.
- HTTPS protects sensitive / confidential information such as banking information, credit card numbers and addresses.
- HTTPS validates your webpage, which allows users trust your site.
- Sites with HTTPS are favoured in the Google searches algorithum in preference over similar sites without HTTPS.
- SSL helps to prevent "Man in the middle attacks"
- SSL is required for AMP 'Accelerated Mobile Pages' a project from Google and Twitter designed to make really fast mobile pages. 
- In order for a mobile site to be indexable, Google recommends a site to have HTTPS.



## Demo how to generate certificates and use them in a node project

- Step 1:

    - Generate a certificate
      ```openssl req -x509 -newkey rsa:2048 -keyout key.pem -out cert.pem -days XXX```
      
![](https://i.imgur.com/uyiXXot.png)

![](https://i.imgur.com/tzq8KNG.png)

2. Create an HTTPS server

![](https://i.imgur.com/S1gfmH7.png)

3. Include flag to reject unauthorised certificates:

``` process.env[‘NODE_TLS_REJECT_UNAUTHORIZED’] = 0; ```

![](https://i.imgur.com/T1VRfzv.png)



## Extra stuff/Resources:

Simplified article on SSL certificates:
http://www.steves-internet-guide.com/ssl-certificates-explained/ 

'The First Few Milliseconds of an HTTPS Connection':
http://www.moserware.com/2009/06/first-few-milliseconds-of-https.html

'How does my browser inherently trust a CA?': https://security.stackexchange.com/questions/158997/how-does-my-browser-inherently-trust-a-ca

<b>TLS node module</b>
https://nodejs.org/api/tls.html

<b>Medium tutorial</b>
https://medium.com/nodejs-tips/ssl-certificate-explained-fc86f8aa43d4
