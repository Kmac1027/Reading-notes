# Reading: Class 11: Authentication

## Review, Research, and Discussion

1. Explain what a “Singleton” is (in Computer Science terms) - a design pattern used in object-oriented programming to permit no more than one instance of a class

1. Explain how the Singleton pattern can be used with Node modules, specifically with classes

1. If you were tasked with building a middleware system like Express uses, what approach might you take to construct/operate it?

## Document the following Vocabulary Terms

Router Middleware
Dynamic Module Loading
Singleton Pattern
CRUD -> REST Method Matches
Mock Testing

## Securing Passwords

### Securing Passwords with Bcrypt Hashing Function

-[Link to article](https://thehackernews.com/2014/04/securing-passwords-with-bcrypt-hashing.html)

- Passwords are the first line of defense against cyber criminals. It is the most vital secret of every activity we do over the internet and also a final check to get into any of your user account
- Cryptographic hash algorithms MD5, SHA1, SHA256, SHA512, SHA-3 are general purpose hash functions, designed to calculate a digest of huge amounts of data in as short a time as possible. Hashing is the greatest way for protecting passwords and considered to be pretty safe for ensuring the integrity of data or password.

### PROBLEMS WITH CRYPTOGRAPHIC HASH ALGORITHM

- Brute Force attack: Hashes can't be reversed, so instead of reversing the hash of the password, an attacker can simply keep trying different inputs until he does not find the right now that generates the same hash value, called brute force attack.
- Hash Collision attack: Hash functions have infinite input length and a predefined output length, so there is inevitably going to be the possibility of two different inputs that produce the same output hash. MD5, SHA1, SHA2 are vulnerable to Hash Collision Attack i.e. two input strings of a hash function that produce the same hash result.

### BCrypt, IT's SLOW AND STRONG AS HELL

- To overcome such issues, we need algorithms which can make the brute force attacks slower and minimize the impact. Such algorithms are PBKDF2 and BCrypt, both of these algorithms use a technique called **Key Stretching**.
- Bcrypt is an adaptive hash function based on the Blowfish symmetric block cipher cryptographic algorithm and introduces a work factor (also known as security factor), which allows you to determine how expensive the hash function will be.
- This work factor value determines how slow the hash function will be, means different work factor will generate different hash values in different time span, which makes it extremely resistant to brute force attacks. When computers become faster next year we can increase the work factor to balance it out i.e. to make the attack slower.

## Basic Auth

[Link to Article](https://en.wikipedia.org/wiki/Basic_access_authentication)

- In the context of an HTTP transaction, basic access authentication is a method for an HTTP user agent (e.g. a web browser) to provide a user name and password when making a request. In basic HTTP authentication, a request contains a header field in the form of Authorization: Basic < credentials >, where credentials is the Base64 encoding of ID and password joined by a single colon
- HTTP Basic authentication (BA) implementation is the simplest technique for enforcing access controls to web resources because it does not require cookies, session identifiers, or login pages; rather, HTTP Basic authentication uses standard fields in the HTTP header.

## Intro to JWT

[Link to Article](https://jwt.io/introduction/)

### Introduction to JSON Web Tokens

- JSON Web Token (JWT) is an open standard (RFC 7519) that defines a compact and self-contained way for securely transmitting information between parties as a JSON object. This information can be verified and trusted because it is digitally signed. JWTs can be signed using a secret (with the HMAC algorithm) or a public/private key pair using RSA or ECDSA.

### hen should you use JSON Web Tokens?

- Authorization: This is the most common scenario for using JWT. Once the user is logged in, each subsequent request will include the JWT, allowing the user to access routes, services, and resources that are permitted with that token. Single Sign On is a feature that widely uses JWT nowadays, because of its small overhead and its ability to be easily used across different domains.
- Information Exchange: JSON Web Tokens are a good way of securely transmitting information between parties. Because JWTs can be signed—for example, using public/private key pairs—you can be sure the senders are who they say they are. Additionally, as the signature is calculated using the header and the payload, you can also verify that the content hasn't been tampered with.

### What is the JSON Web Token structure?

- In its compact form, JSON Web Tokens consist of three parts separated by dots (.), which are:
  1. Header
  1. Payload
  1. Signature
- Therefore, a JWT typically looks like the following. - **xxxxx.yyyyy.zzzzz**
- **Header** -The header typically consists of two parts: the type of the token, which is JWT, and the signing algorithm being used, such as HMAC SHA256 or RSA.
- Example

```js
{
  "alg": "HS256",
  "typ": "JWT"
}
```

- **Payload** - The second part of the token is the payload, which contains the claims. Claims are statements about an entity (typically, the user) and additional data. There are three types of claims: registered, public, and private claims.
  1. Registered claims: These are a set of predefined claims which are not mandatory but recommended, to provide a set of useful, interoperable claims. Some of them are: iss (issuer), exp (expiration time), sub (subject), aud (audience), and others.
  1. Public claims: These can be defined at will by those using JWTs. But to avoid collisions they should be defined in the IANA JSON Web Token Registry or be defined as a URI that contains a collision resistant namespace.
  1. Private claims: These are the custom claims created to share information between parties that agree on using them and are neither registered or public claims.
- Example

```js
{
  "sub": "1234567890",
  "name": "John Doe",
  "admin": true
}
```

- **Signature** - To create the signature part you have to take the encoded header, the encoded payload, a secret, the algorithm specified in the header, and sign that. For example if you want to use the HMAC SHA256 algorithm, the signature will be created in the following way:

```js
HMACSHA256(
  base64UrlEncode(header) + "." +
  base64UrlEncode(payload),
  secret)
```

- The signature is used to verify the message wasn't changed along the way, and, in the case of tokens signed with a private key, it can also verify that the sender of the JWT is who it says it is.

### Putting all together

- The output is three Base64-URL strings separated by dots that can be easily passed in HTML and HTTP environments, while being more compact when compared to XML-based standards such as SAML.
[JWT debugger for practace with JWT](https://jwt.io/#debugger-io)

### How do JSON Web Tokens work?

- In authentication, when the user successfully logs in using their credentials, a JSON Web Token will be returned. Since tokens are credentials, great care must be taken to prevent security issues. In general, you should not keep tokens longer than required.
- This can be, in certain cases, a stateless authorization mechanism. The server's protected routes will check for a valid JWT in the Authorization header, and if it's present, the user will be allowed to access protected resources. If the JWT contains the necessary data, the need to query the database for certain operations may be reduced, though this may not always be the case.
- If the token is sent in the Authorization header, Cross-Origin Resource Sharing (CORS) won't be an issue as it doesn't use cookies.
- The following diagram shows how a JWT is obtained and used to access APIs or resources:

[](https://cdn2.auth0.com/docs/media/articles/api-auth/client-credentials-grant.png)

  1. The application or client requests authorization to the authorization server. This is performed through one of the different authorization flows. For example, a typical OpenID Connect compliant web application will go through the /oauth/authorize endpoint using the authorization code flow.
  1. When the authorization is granted, the authorization server returns an access token to the application.
  1. The application uses the access token to access a protected resource (like an API)

- Do note that with signed tokens, all the information contained within the token is exposed to users or other parties, even though they are unable to change it. This means you should not put secret information within the token.

### Why should we use JSON Web Tokens?

- As JSON is less verbose than XML, when it is encoded its size is also smaller, making JWT more compact than SAML. This makes JWT a good choice to be passed in HTML and HTTP environments.
- Security-wise, SWT can only be symmetrically signed by a shared secret using the HMAC algorithm. However, JWT and SAML tokens can use a public/private key pair in the form of a X.509 certificate for signing. Signing XML with XML Digital Signature without introducing obscure security holes is very difficult when compared to the simplicity of signing JSON.
- JSON parsers are common in most programming languages because they map directly to objects. Conversely, XML doesn't have a natural document-to-object mapping. This makes it easier to work with JWT than SAML assertions.

 ## OWASP auth cheatsheet

 [Link](https://cheatsheetseries.owasp.org/cheatsheets/Authentication_Cheat_Sheet.html)

 ## bcrypt docs

 [Link](https://www.npmjs.com/package/bcrypt)
