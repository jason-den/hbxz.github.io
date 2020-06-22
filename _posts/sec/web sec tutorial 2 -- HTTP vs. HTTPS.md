---
layout: post
title: "HTTP vs. HTTPS"
subtitle: "see one, ~~do one~~, teach one"
date: 2020-04-17 12:00:00
author: "Jason Denn"
header-img: "img/post-bg-2015.jpg"
catalog: true
tags:
  - Foundation - security
---
HTTPS = HTTP + 'secure'

[HTTPS](https://www.cloudflare.com/learning/ssl/what-is-https/) is [HTTP](https://www.cloudflare.com/learning/ddos/glossary/hypertext-transfer-protocol-http/) with the encryption layer, [TLS](https://www.cloudflare.com/learning/ssl/transport-layer-security-tls/) ([SSL](https://www.cloudflare.com/learning/ssl/what-is-ssl/)), to encrypt normal HTTP requests and responses

>   Also check this [artical why-is-http-not-secure/](https://www.cloudflare.com/learning/ssl/why-is-http-not-secure/)

>   I suggest using [wireshark](https://www.wireshark.org/) to monitor your web request & response. 



## What does a typical HTTP request look like?

An HTTP request is just a series of lines of text that follow the HTTP protocol. A GET request might look like this:

```
GET /hello.txt HTTP/1.1
User-Agent: curl/7.63.0 libcurl/7.63.0 OpenSSL/1.1.l zlib/1.2.11
Host: www.example.com
Accept-Language: en
```

When an origin server receives an HTTP request, it sends an HTTP response, which is similar:

```
HTTP/1.1 200 OK
Date: Wed, 30 Jan 2019 12:14:39 GMT
Server: Apache
Last-Modified: Mon, 28 Jan 2019 11:17:01 GMT
Accept-Ranges: bytes
Content-Length: 12
Vary: Accept-Encoding
Content-Type: text/plain

Hello World!
```

## What is HTTPS?

The S in HTTPS stands for "secure." HTTPS uses TLS (or SSL) to encrypt HTTP requests and responses, so in the example above, instead of the text, an attacker would see a bunch of seemingly random characters.

Instead of:

```
GET /hello.txt HTTP/1.1
User-Agent: curl/7.63.0 libcurl/7.63.0 OpenSSL/1.1.l zlib/1.2.11
Host: www.example.com
Accept-Language: en
```

The attacker sees something like:

```
t8Fw6T8UV81pQfyhDkhebbz7+oiwldr1j2gHBB3L3RFTRsQCpaSnSBZ78Vme+DpDVJPvZdZUZHpzbbcqmSW1+3xXGsERHg9YDmpYk0VVDiRvw1H5miNieJeJ/FNUjgH0BmVRWII6+T4MnDwmCMZUI/orxP3HGwYCSIvyzS3MpmmSe4iaWKCOHQ==
```





>   When a client opens a channel with an origin server (e.g. when a user navigates to a website), possession of the private key that matches with the public key in a website's SSL certificate proves that the server is actually the legitimate host of the website. This prevents or helps block a number of attacks that are possible when there is no authentication, such as:
>
>   *   [Man-in-the-middle attacks](https://www.cloudflare.com/learning/security/threats/man-in-the-middle-attack/)
>   *   [DNS hijacking](https://www.cloudflare.com/learning/dns/dns-security/)
>   *   [BGP hijacking](https://www.cloudflare.com/learning/security/glossary/bgp-hijacking/)

Surely the PKI (public key infrastructure) is a related topic. 

