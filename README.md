# Tinfoil-Chat
Simple chat app that uses 2048 bit RSA encryption. Everything is made from scratch python and should be a good first example for someone who wants to start learning about encryption, gui's or networking.

# Note

Not to be confused with Tinfoil chat which can be found here.
https://github.com/maqp/tfc

# <-- EDUCATIONAL USE ONLY -->

This was a project make in my spare time to create all the aspects of an encrypted platform from scratch. This of course taught me a lot about, optimization, security, networking and GUI's. This is not however sufficient to stop anyone who knows what there doing from compromising your messages.

## Requirements 
Python 3.10

These should all be default

dotenv 
pickle
tinkter
socket


## Server set up

1) Run the server file.
2) enter your ip, port and password.
3) Wait for connections.

Note that the password is unsecure on your system and is in the python shell. Use only on secure hardware



## Client set up

1) Run the Gui File.
2) Wait for your RSA keys to generate.
3) Enter in the global ip of the server your connecting to, port and password.

Note: Due to this program using pickle you should NEVER connect to a server that you dont trust.


## Server Client Verification 

Its worth going over the verification process becuase this is an algorithem that I improvised to stop man in the middle attacks and is potentialy very flawed.

1. Client sends public key
2. Server sends public key
3. Sever makes a temporary user account with the client public key
4. Client sends an encrypted message of a shaw256 hash of password + public key. 
5. Sever sever then is able to check that the password is correct and that the person with the key in 1 sent it.
6. Server then sends a hash of its public key and the password.
7. Client does the same verification
8. verification complete



## Security Vulnerabilities 

* The client uses the pickel library "It is possible to construct malicious pickle data which will execute arbitrary code during unpickling. Never unpickle data that could have come from an untrusted source, or that could have been tampered with."
* If the client or server loses their public keys its possibul to falseify messages. 
* RSA uses prime numbers in a certain range so its possibul to generate a ton of keys and mass attack cyphers.
* This code is not secure against timing attacks.
* <b> THIS IS TEXT BOOK RSA WHICH IS NOT SUFFICENT FOR ANYTHING IMPORTANT 
* The encryption key is the same as the signing key, which is a big no no.
* Keys are close together, making it not safe against fermats method.
* Key exchange is more of a make it work situation rather than anything that is safe.

If you want to try breaking this program more power to you More power to you, just be sure to send me how you did it.




## To Do
* Make it more restitant to timming attacks. Ie when checking for signatures we use the  "=="  operator which is far from ideal.
* Maybe make a branch with AES insted of RSA because were already require a password, so RSA is far from ideal when made worse by the fact that python is not a fast language. 
* Find a better solution than useing pickle because its really not a good idea. We the risk with signature verifycation, but its still not a good idea.
* Codes messy and could use a clean up
* Make the signing key diffrent from the encryption key.
* Try to adress the timeing attack problem
* Write code to detect if the .env is not fully generated, and to redo it. (If the proceses doesnt compleate it will screw things up)


## Its not a bug its a feature 

* Anytime someone joins they will unable to see the message's sent before joining, this has the benefit of not having your message history comprimised if someone suspicious joins.
* All names are randomly generated and keys + names are genrated for each log in. This makes it so that a user doesnt trust the program too much with out adiquite verifycation.
* Keys are saved in the .env file so dont give that out.



## Example Chat
![alt text](https://i.imgur.com/yAv1Ynx.png)













