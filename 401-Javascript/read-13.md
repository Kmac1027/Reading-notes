# Reading 13: OAuth

## Review, Research, and Discussion

1. Why is authentication important? - for protection of user information
1. Why should we be careful about storing a user’s password? - so we are not the cause of a breach of their data
1. What is the difference between hashing and encryption? - Hashing scrambles a users info and cant be unscrambled. Encryption can be undone
1. What is the difference between encryption and encoding? - encoding makes data more readable to a computer, encrytion is security on information and data
1. What is a token used for? - to show the user is who they say they are

## What is OAuth Really All About?

[Link to Video](https://www.youtube.com/watch?v=t4-416mg6iU&ab_channel=JavaBrains)

## OAuth2 simplified

[Link to Article](https://aaronparecki.com/oauth-2-simplified/)

### Roles

The client is the application that is attempting to get access to the user's account. It needs to get permission from the user before it can do so.
**The API: "Resource Server"**
The resource server is the API server used to access the user's information.
**The Authorization Server**
This is the server that presents the interface where the user approves or denies the request. In smaller implementations, this may be the same server as the API server, but larger scale deployments will often build this as a separate component.
**The User: "Resource Owner"**
The resource owner is the person who is giving access to some portion of their account.


### Authorization

The first step of OAuth 2 is to get authorization from the user. For browser-based or mobile apps, this is usually accomplished by displaying an interface provided by the service to the user.

OAuth 2 provides several "grant types" for different use cases. The grant types defined are:

1. Authorization Code for apps running on a web server, browser-based and mobile apps
1. Password for logging in with a username and password (only for first-party apps)
1. Client credentials for application access without a user present
1. Implicit was previously recommended for clients without a secret, but has been superseded by using the Authorization Code grant with PKCE.

## Build a Node API with OAuth

[Link to article](https://developer.okta.com/blog/2018/08/21/build-secure-rest-api-with-node)

- Server B sends a secret key to the authorization server to prove who they are and asks for a temporary token.
- Server B then consumes the REST API as usual but sends the token along with the request.
- Server A asks the authorization server for some metadata that can be used to verify tokens.
- Server A verifies the Server B’s request.
  - If it’s valid, a successful response is sent and Server B is happy.
  - If the token is invalid, an error message is sent instead, and no sensitive information is leaked.

- This is where Okta comes into play. Okta can act as an authorization server to allow you to secure your data. You’re probably asking yourself “Why Okta? Well, it’s pretty cool to build a REST app, but it’s even cooler to build a secure one. To achieve that, you’ll want to add authentication so users have to log in before viewing/modifying groups. At Okta, our goal is to make identity management a lot easier, more secure, and more scalable than what you’re used to. Okta is a cloud service that allows developers to create, edit, and securely store user accounts and user account data, and connect them with one or multiple applications. Our API enables you to:
  1. Authenticate and authorize your users
  1. Store data about your users
  1. Perform password-based and social login
  1. Secure your application with multi-factor authentication

[Back to code 401 notes](../401-Javascript.md)