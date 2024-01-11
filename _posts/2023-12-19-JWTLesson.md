---
title: "JWT - Java, Security Lesson"
description: "Lesson on Java exploits and cybersecurity."
toc: true
layout: post
type: hacks
courses:
  csa:
    week: 17
---

## What is JWT
- JSON Web Token (JWT)
    - popular way to authenticate users in a web application. It is a compact, URL-safe means of representing claims to be transferred between two parties. The claims in a JWT are encoded as a JSON object that is digitally signed using JSON Web Signature (JWS).
    - Compact, URL-safe means of representing claims to securely transmit information between parties.
        - These claims are encoded as JSON objects that are digitally signed using a JSON web signature
    - Concise and efficient representation, allows for ease of transmissions over networks
    - No need to reference external source/database to validate info
- Common use cases:
    - Authentication
    - Information exchange
    - Authorization
    - Secure your APIs!

<mark>Popcorn hack</mark>: list 3 real world applications of JWT:

- Personal identification for exclusive access
- Store persistent login token so that it lasts a while before you'd have to sign in
- Banks!!! Amazon shopping, Target, wow...so many incredible wonderful things, holy cow

## Why do you need JWT
JSON Web Tokens (JWT) are crucial for secure and efficient user authentication in web development.
- They help manage user identity and sessions across different parts of a system.
- They play a key role in stateless authentication, allowing servers to verify user identity without storing session data.
- JWTs are especially useful in decentralized systems, enabling smooth communication between different services and ensuring secure user roles and permissions.
- JWTs simplify and enhance user authentication in modern web development.

# Components of JWT

- What is a web token?
    - A web token is a piece of information that represents a user's identity or session and is used for authentication and authorization in web applications. It is typically a string of characters, often encoded in a JSON format, and is digitally signed to ensure its integrity.

### Structure of Web Token

<mark>I'm saving this for myself because I didn't know this and it's kind of interesting.</mark>

- This is the structure of a JSON Web Token:

1. Header
    - The header typically consists of two parts: the type of the <mark>token</mark>, which is JWT, and the <mark>algorithm</mark> that is used, such as HMAC SHA256 or RSA SHA256. It is Base64Url encoded to form the first part of the JWT
2. Payload
    - Claims and user data
    - Claims are statements about the entity (users)
    - There are three types of claims:
        - Registered: predefined claims that are no mandatory but recommended
        - <mark>Public</mark>: claims defined within the IA and JSON web token registry
        - Private: custom claims created to share information between parties that agree to using them
3. Signature
    - Ensuring integrity and authenticity
    - Verify the sender of the JWT
    - Function
        - Creating a signature
        - Verification process
        - Signature tampering activity

# Deep Dive into Anatomy of JWT

- Navigate to this website: [Link](https://jwt.io/)

Encoded: Json Web Token (what you send to and from the client)
Decoded: algorithm, data, verify token hasn't been changed

```plaintext
eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.
eyJzdWIiOiIxMjM0NTY3ODkwIiwibmFtZSI6IkpvaG4gRG9lIiwiaWF0IjoxNTE2MjM5MDIyfQ.
SflKxwRJSMeKKF2QT4fwpMeJf36POk6yJV_adQssw5c
```

```java
// header
{
    "alg": "HS256", //type of sign in algorithm used for encoding and decoding
    "typ": "JWT"    //type of token
}
```

- Base 64 encoded
- useful to signature type to decode

```java
// payload
{
"sub": "123", //example of a registered claim
"name": "jwt lesson",
"iat": 1516239022",
"authorities": [
    "ADMIN",
    "MANAGER"
],
"extra-claims": "some data here"
}
```

- where all different data for application is
- sub = subject: id of user you're authenticating
- iat = issued at (when token was created)
- exp/eat = expired at (date when token becomes invalid)

<mark>This last one is really good for logins with temporary authority</mark>

```java
// signature
{
HMACSHA256(
    base64UrlEncode(header) + "." +
    base64UrlEncode(payload),
    your-256-bit-secret
) secret

 base in your app
}
```

- Hash-based message authentication code
- Make sure that the JWT hasn't been tampered with
- Ensures data hasn't been tampered

# How to use JWT in Java

## Creating a JWT

- Use a library
    - Libraries like <mark>jjwt</mark> (Java JWT) simplify the process of creating and parsing JWTs in Java.
- Here's a basic example of how you can create a JWT using the jjwt library:

```java
import io.jsonwebtoken.Jwts;
import io.jsonwebtoken.SignatureAlgorithm;
import java.util.Date;

public class JwtGenerator {
    public String generateJwt(String subject, String secretKey, long expirationMillis) {
        Date now = new Date();
        Date expirationDate = new Date(now.getTime() + expirationMillis);

        return J Sts.builder()
            .setSubject(subject)
            .setIssuedAt(now)
            .setExpiration(expirationDate)
            .signWith(SignatureAlgorithm.HS256, secretKey)
            .compact();
    }
}
```

- In this example, the `generateJwt` method takes the subject (user ID), secret key, and expiration time in milliseconds as parameters.
- It uses the `Jwts.builder()` to create a JWT builder, sets the subject, issued date, expiration date, and signs the token with the specified signature algorithm and secret key.
- The `compact()` method is then called to generate the final compact JWT string.

## Parsing a JWT

- Similarly, parsing a JWT is straightforward using the jjwt library:

```java
import io.jsonwebtoken.Claims;
import io.jsonwebtoken.Jwts;

public class JwtParser {
    public Claims parseJwt(String jwt, String secretKey) {
        return Jwts.parser()
            .setSigningKey(secretKey)
            .parseClaimsJws(jwt)
            .getBody();
    }
}
```

- The `parseJwt` method takes the JWT string and secret key as parameters.
- It uses the `Jwts.parser()` to create a JWT parser, sets the signing key, and parses the JWT to extract the claims using the `parseClaimsJws` method.
- The `getBody()` method then returns the claims.

# Conclusion

JSON Web Tokens (JWT) are a powerful tool for secure user authentication and authorization in web applications.
- They provide a compact and efficient way to transmit claims between parties, ensuring data integrity and authenticity.
- Understanding the structure and components of JWTs, along with using libraries like jjwt in Java, empowers developers to implement robust and secure authentication mechanisms.
- As with any security-related implementation, it's crucial to stay informed about best practices and potential vulnerabilities in order to build and maintain secure systems.
```
