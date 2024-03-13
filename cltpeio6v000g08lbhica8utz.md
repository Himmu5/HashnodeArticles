---
title: "Refresh token and JWT token"
seoTitle: "Refresh token and JWT token"
seoDescription: "Exploring the two important security tokens"
datePublished: Wed Mar 13 2024 06:09:33 GMT+0000 (Coordinated Universal Time)
cuid: cltpeio6v000g08lbhica8utz
slug: refresh-token-and-jwt-token
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1710301824497/5ec84dcd-f47f-4904-850a-bac359adc4c5.png
tags: authentication, authorization, jwt, refresh-token

---

In this blog, we'll delve into two crucial security tokens utilized during server resource requests: the Refresh token and the JWT token. Our aim is to gain a comprehensive understanding of these tokens, discern their disparities, and underscore the significance of Refresh tokens.

### JWT token

Jwt is a secure way to transmit data between two parties in JSON format. This data can be verified and trusted because it is digitally signed. Jwt is signed by the HMAC algorithm or public/private key pair using RSA or ECDSA. This token can only verified by the parties that have the secret key.

Jwt token is made of three values headers, payload, and verify signature.

### Why would we use a JWT token?

* **Authentication**: To verify user validity, we employ a JWT token. Given the stateless nature of the HTTP protocol, user credentials must be shared in every request for verification. However, to mitigate repetitive data sharing, we utilize an encrypted JWT token for this purpose.
    
* **Authorization**: Additionally, JWT tokens serve as a means of user authorization, enabling verification of user privileges post-authentication. This capability allows for fine-grained control over access levels, facilitating robust access management via the JWT token.
    

How does the JWT look?

```xml
eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiIxMjM0NTY3ODkwIiwibmFtZSI6IkpvaG4gRG9lIiwiaWF0IjoxNTE2MjM5MDIyfQ.SflKxwRJSMeKKF2QT4fwpMeJf36POk6yJV_adQssw5c
```

This JWT token can be separated by `.` This token is made with three values.

* **header**: First is the headers, the header is a JSON-type object that contains algo and type of token.
    
    ```json
    {
      "alg": "HS256",
      "typ": "JWT"
    }
    ```
    
* **payload:** This field contains any data that we want to share with this token.
    
    ```json
    {
      "sub": "1234567890",
      "name": "John Doe",
      "iat": 1516239022
    }
    ```
    
* **signature**: In this field, there is a secret key and some other encrypted data.
    

### Refresh Token

For security purposes, we make the access token(Jwt) invalid after a certain period. so once the access token gets expires then we can get a new access token with the help of a refresh token. That is, a [refresh token](https://auth0.com/docs/tokens/refresh-tokens) [is a credenti](https://auth0.com/docs/tokens/refresh-tokens)al artifact that lets a client application get new access tokens without having to ask the user to log in again.

Securing the refresh token is very important task because if this token is in the wrong person then he can get the access after the expiring the access token.

Refresh tokens make life very convenient but to keeping secure the refresh token is very important.

### Conclusion

In summary, this blog provided an overview of two key security tokens: JWT and Refresh tokens. JWT tokens enable secure data transmission via JSON format, facilitating authentication and authorization with their headers, payload, and signature. Refresh tokens allow clients to obtain new access tokens without reauthentication, enhancing convenience but requiring careful security measures. Understanding the roles and importance of these tokens is essential for robust authentication and authorization in applications.

Thankyou💕💕