# Reading 12: Bearer Authorization

## Review, Research, and Discussion

**1. Write the following steps in the correct order:**

  1. Register your application to get a client_id and client_secret
  1. Ask the client if they want to sign in via a third party
  1. Redirect to a third party authentication endpoint
  1. Receive authorization code
  1. Make a request to the access token endpoint
  1. Receive access token
  1. Make a request to a third-party API endpoint

**2. What can you do with an authorization code?**

- Get an access token

**3. What can you do with an access token?**

- allows you to access user specific data

**4. What’s a benefit of using OAuth instead of your own basic authentication?**

- far more secure

## Document the following Vocabulary Terms (defenitions from Riva Davidowski)

- Authentication: Authentication is the practice of validating the identity of a registered user attempting to gain access to an application, API, microservices or any other data resource.
- Authorization: Authorization is about deciding whether an individual is permitted to perform a given action on a specific resource once they are authenticated.
- Encryption: The process of converting information or data into a code, especially to prevent unauthorized access.This technique involves a key, which is a set of mathematical values, to turn the data into an encrypted form. The receiver also has the key and uses it to decrypt the data. This process of encryption and decryption is referred to as cryptography.
- Hashing: Hashing is the process of converting a given key into another value. A hash function is used to generate the new value according to a mathematical algorithm. It transforms a string of characters into a value of fixed length. This generated value is called hash.
- Session: A [session](https://en.wikipedia.org/wiki/Session_(computer_science) (Links to an external site.) is a temporary and interactive information interchange between two or more communicating devices
- Cookie: A cookie (Links to an external site.) is a text file stored on a user’s computer by a web browser, at the request of the web server. A cookie is limited to a small amount of data and can only be read by the website that created it.
- Token: Ok, there are different types of tokens. Generally a token is an object (in software or in hardware) which represents the right to perform some operation. There can be client tokens, user tokens, security tokens, payment tokens etc.
- Basic Auth: A simple authentication scheme built into the HTTP protocol. The client sends HTTP requests with the Authorization header that contains the word Basic, followed by a space and a base64-encoded(non-encrypted) string username: password.
- Encoding: Encoding is done to transform data into a form that can be read by other machines or used by other processes.
- Secret: Anything that a developer doesn't want someone else to see. For example, database passcodes, API keys, stuff like that. Anything that could be in an .env file for instance.
- Cryptography: Cryptography is the study of secure communications techniques that allow only the sender and intended recipient of a message to view its contents. The term is derived from the Greek word kryptos, which means hidden.

## JWTs Explained

[Link to Video](https://www.youtube.com/watch?v=926mknSW9Lo&ab_channel=Bitfumes)

## Intro to JWT

[Refer to class 11 notes](read-11.md)

## Are JWTs Secure?

[Link to article](https://stackoverflow.com/questions/27301557/if-you-can-decode-jwt-how-are-they-secure)

- JWTs can be either signed, encrypted or both. If a token is signed, but not encrypted, everyone can read its contents, but when you don't know the private key, you can't change it. Otherwise, the receiver will notice that the signature won't match anymore.
- Answer to your comment: I'm not sure if I understand your comment the right way. Just to be sure: do you know and understand digital signatures? I'll just briefly explain one variant (HMAC, which is symmetrical, but there are many others).
- Let's assume Alice wants to send a JWT to Bob. They both know some shared secret. Mallory doesn't know that secret, but wants to interfere and change the JWT. To prevent that, Alice calculates Hash(payload + secret) and appends this as signature.
- When receiving the message, Bob can also calculate Hash(payload + secret) to check whether the signature matches. If however, Mallory changes something in the content, she isn't able to calculate the matching signature (which would be Hash(newContent + secret)). She doesn't know the secret and has no way of finding it out. This means if she changes something, the signature won't match anymore, and Bob will simply not accept the JWT anymore.
- Let's suppose, I send another person the message {"id":1} and sign it with Hash(content + secret). (+ is just concatenation here). I use the SHA256 Hash function, and the signature I get is: 330e7b0775561c6e95797d4dd306a150046e239986f0a1373230fda0235bda8c. Now it's your turn: play the role of Mallory and try to sign the message {"id":2}. You can't because you don't know which secret I used. If I suppose that the recipient knows the secret, he CAN calculate the signature of any message and check if it's correct.

[Back to code 401 notes](../401-Javascript.md)