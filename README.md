JSON Web Token / React / Spring Boot Example

This is a proof-of-concept project demonstrating how to secure a Spring REST API using JSON Web Tokens (JWT) with a React frontend. It showcases authentication, token validation, and role-based access using modern tools.

JSON Web Tokens (JWT)

JWT is an open standard (RFC 7519) for securely transmitting information between parties as a JSON object. The information can be verified and trusted because it is digitally signed. JWTs can be signed using a secret key (HMAC) or a public/private key pair (RSA).

When to Use JWT

Authentication: The most common use-case. After login, each request includes a JWT, allowing access to permitted routes, services, and resources. JWT is widely used for Single Sign-On (SSO).

Information Exchange: Securely transmit information between parties, verifying the sender’s identity and ensuring the payload hasn’t been tampered with.

More details: https://jwt.io

### Server Side: Spring Boot

Spring Boot is excellent for creating RESTful services. On the server side, the JWT signing is done in the /api/authentication REST call in AuthProviderService (the class that implements the AuthenticationProvider from Spring Security).  In addition, it has an H2 database containing 2 users (username: admin; pass: admin/username: tomcat; pass: tomcat).  The api/user REST call in  UserController returns the user data, if the user is already authenticated.

The verification is done in the Filter (JwtAuthenticationTokenFilter).  It filters every request different from  /api/authentication and api/user. If a correct token isn't found, a 401 HTTP response is returned.  If a correct token is found, the Authentication object is added to the Spring Security Context  and can be used in any REST endpoint (as shown in UserController).

The JWT signing is done by an excellent Java JWT library (https://github.com/jwtk/jjwt).


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
