Replying Parts perform two distnct acts


Sample Repo
https://github.com/strangerlabs/webauthn/blob/master/src/Webauthn.js

Looking at the above code and it looks like it needs a bunch of work.
# Terminology
## Attestation - authenicate 

## Attestation Certificate
A X.509 certificate for attestation key pair used by an authenticator to attest to its manufacture and capabilities.  At registration 

# Registartion
- public key credential is created on an authenticator and scoped to a Replying Party with the present user's account 

# Authentication
The Replying Party is presented with an Authentication Assertion proving the presence and consent of th user who registered with the public key credential.  At registration the the authenticator uses the attestation private key to sign the Relying Party specific credential public key that it generates and returns via the authenticatorMakeCredential option.  The Relying Parties use the attestation public key conveyed in the attestation certificate to verify the attestation signature.  

# Authentication
The ceremony where a user, and the user's client work to cryptographically prove to a relying party that the user controls the credential private key of a previously registered public key 

# Web Authentication API comprises of the following
- PublicKeyCredential which extends the Credential Management API and infrastructure which allows credentials to be used with the following calls

```

navigator.credentials.create() -- Used for registration

navigator.credentials.get() -- Used for authentication
```

# 1.3.1 Registration
1. The user visits the 
2. Relying Party scripts runs the code snippet below
3. The client platform searchs and locates the authenticator
4. The client connects to the authenticator, performing any pairing actions if necessary
5. The authenticator shows appropriate UI for the user to provide or other authorization gestion
6. The authenticator returns a response to the client, which in turn returns a response to the Relying Party scripts.  If the user declined to select an authenticator or provide authorization, an appropriate error is returned 
7. If a new credential was created.
- The relying party scripts sends the newly generated crednetial public key to the server, along with additional information such as attestation regarding the provenance and characteristics of the authenticator
- The server store the credential public key in its database and associates
- The script may store data such as the credential ID in local storage, to improve future UX 

# 1.3.3 Authentication
1. User visits the side
2. The scripts ask the client for an authentication assertion providing as much information as possible to narrow the choice
3. Replying Party scripts run one of the code snippets below
4. The client platform searchs code snippets below
6. The authenticator presents the user with a notification that their attention is needed
7. The authenticator obtains an authorization gesture
8. the authenticator returns a response to the client, which in turn returns a response to the Relying Party