JSON Web Token / React / Spring Boot Example

This is a proof-of-concept project demonstrating how to secure a Spring REST API using JSON Web Tokens (JWT) with a React frontend. It showcases authentication, token validation, and role-based access using modern tools.

JSON Web Tokens (JWT)

JWT is an open standard (RFC 7519) for securely transmitting information between parties as a JSON object. The information can be verified and trusted because it is digitally signed. JWTs can be signed using a secret key (HMAC) or a public/private key pair (RSA).

When to Use JWT

Authentication: The most common use-case. After login, each request includes a JWT, allowing access to permitted routes, services, and resources. JWT is widely used for Single Sign-On (SSO).

Information Exchange: Securely transmit information between parties, verifying the sender’s identity and ensuring the payload hasn’t been tampered with.

More details: https://jwt.io

Server Side: Spring Boot
JWT signing is handled in /api/authentication via AuthProviderService.
Uses an SQL database (MySQL, PostgreSQL, etc.) for storing users and data.
Example users for testing:
username: admin / password: admin
username: user / password: user
/api/user returns user data if authenticated.
Token verification is done via JwtAuthenticationTokenFilter. Requests without a valid token return HTTP 401. Valid tokens are added to the Spring Security Context.
JWT implementation uses JJWT library.


### Client Side: ReactJS

The simple React app shows a login page. On successful login it, the user is redirected to the main page, which shows his username and token.


### Setup
- Install Node version 20.5.0
- Install npm version 9.8.1
- Install Java JDK 17 LTS
- Install Maven 3.x
- Add Java and Maven to the env variable PATH 



### Install
- In the folder back-end, run "mvn install"
- In the folder back-end/targe,t run "sample-app-1.0-SNAPSHOT.jar " and keep it running
- In the folder front-end/app-reac, run "sh run.sh" and keep it running

### Usage
URL access:  http://localhost:8080


### References

[1] https://jwt.io/introduction/
