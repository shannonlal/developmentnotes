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

# Registering a webauthn credential
Steps
1. user wants to create a new account
2. create a new key pair
3. user sends server the new public key
4. server completes the registration


## First stage 
The server will present a username and password and will store the password in the server

## Second stage
A server must provide data that binds a user to a credential (private-public keypair).  This data includes identifies for the user and oranization - (relying party-- rp).  The website would then use the web auth api to prompt the user to create a new keypair.  Also we need a randomly generated string from the server as a challenge to prevent replay attacks

# Thrird stage
Call navigator.credentials.create.  This is called on the client.  In the example there is a function
```
publicKeyCredentialCreationOptions
```

This function is responsible for creating a new credential for a user.  The credentials include the following

-- challenge- random string from server
-- rp (relying party) {
    name,
    id
}
-- user {
    id,
    name,
    displayName
}
-- pubKeyCredParams - this is array of objects descripbing what public key types are acceptable to a server.  
{
    alg -- described in the COSE registry

}
-- authenticatorSelection {

}
-- timeout {
    the time in milliseconds that the user has to respond to the registration
}

-- attestation {
    indicates how the information should be tracked.  options: none, indirect and direct
}

```
return {
        challenge: randomBase64URLBuffer(32),

        rp: {
            name: "ACME Corporation"
        },

        user: {
            id: id,
            name: username,
            displayName: displayName
        },

        attestation: 'direct',

        pubKeyCredParams: [
            {
                type: "public-key", alg: -7 // "ES256" IANA COSE Algorithms registry
            }
        ]
    }
```

# Credential Object
-- This will return the public key to the server

```
PublicKeyCredential {
    id: 'ADSUllKQmbqdGtpu4sjseh4cg2TxSvrbcHDTBsv4NSSX9...',
    rawId: ArrayBuffer(59),
    response: AuthenticatorAttestationResponse {
        clientDataJSON: ArrayBuffer(121),
        attestationObject: ArrayBuffer(306),
    },
    type: 'public-key'
}
```

id -- for newly generated credential.  
rawId -- Id again but in binary form
attestationObject - {
    credential public key and optiona attetestation certificate.
}