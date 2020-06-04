## PKI - Public key infrastructure

### The problem with key distribution

- How to send keys around? 

- E-commerce: how do you know you’re really communicating with the intended seller?

- - If they send you a public key, it could still be an impostor/MITM
  - How do you know a certificate is really from e.g. Amazon?

- How to hatch an egg? From Horton hears a who. 

- Horton principle: you should say what you mean, mean what you say, and check what you check. 

- PGP/Blockchain 

  - Decentralised peer-based web of trust



PKI widely used and accepted - but has many problems - has an element of security theatre

- Centralised authority based command and control
- The certificate has hash to indicate it hasn’t been altered, and the certificate has been signed
- It’s encrypted with google’s private key, can be decrypted with google’s public key, and within is amazon’s public key
- Here, Google is the **certificate authority** - someone we trust
- How do we know the certificate authority’s keys? Inbuilt with browser
- Registration authority handles who can be listed as a certificate authority







## Trust and the problem of Key Distribution

How to send keys around - how to know what you are authenticating.

How to do e-commerce?

How to Hatch an Egg?



#### **Two** **Approaches**

1. **Centralised authority based Command and Control - eg PKI**
2. **Decentralised peer based web of trust - eg PGP, Blockchain**





#### PKI - Public Key Infrastructure

- based on standard called X.509 from the [International Telecommunication Union](https://en.wikipedia.org/wiki/International_Telecommunication_Union) (EU)

- Nothing to do with PKI the communist party of Indonesia which was brutally eliminated in 1965 with estimates of around 1,000,000 massacred
- originally just designed to support authentication in a particular directory standard x500, but now used generally on the internet.
- idea:

**1.  Certificate Authority**

![image-20200508132431958](https://raw.githubusercontent.com/hbxz/picture-storage/master/2020/05/image-20200508132431958.png)

**2.  Registration Authority**

 ![image-20200508132440746](https://raw.githubusercontent.com/hbxz/picture-storage/master/2020/05/image-20200508132440746.png)

**3.  Validation Authority**

![image-20200508132453078](https://raw.githubusercontent.com/hbxz/picture-storage/master/2020/05/image-20200508132453078.png)





#### TLS/SSL, HTTPS

Typically an SSL Certificate will contain

- "your" domain name,
- "your" company name,
- "your" address, your city, "your" state and "your" country.
-  the expiration date of the Certificate
- details of the Certification Authority responsible for issuing the Certificate.



#### HTTPS 

- http over ssl

- session key and symmetric cipher for **perfect forward secrecy**
- pki for authentication
- mac for integrity





#### fake signing

certificate institution corruption