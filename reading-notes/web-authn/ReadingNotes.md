# Notes from different articles

Password issues. - Users need to worry about phising and remebering their passwords.  Devs need to worry about storing them.

If a hacker has your password they can impersonate you unless you ahve 2 factor authentication

# pulbic key crtyptography and web Authentication
The web authentication API is a spec written by w3c and FIDO.  The API allows server to register and authenticate users using public key cryptography instead of passwords.  It allows servers to integrate with strong authentication (built into devies touch id).  It uses a private-public keypair that is created for the website.  The private key is stored securly on the devie and the public key and a randomly generated credential id is sent to the server for storage.  The server can then use the public key to prove the user's identity

Note: Public key is of no value with out the private key

# Webauthn is part of the FIDO2 frameworkd 
this is a passwordless authentication framework between servers, browsers, and authenticators.  

# Public Key
Addresses the problem of shared secrets.  

# Web Authentication 
- strong -- is ideally backed by a hardward security module that can safely store private keys and perform cryptophic operations 
- scoped -- a key is useful for a specific origin
- attested -- authenticators can provide a certificate that helps servers verify that the public key did in fact come from an authenticator they trust