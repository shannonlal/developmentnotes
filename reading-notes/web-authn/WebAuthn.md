The starting notes on webauthn notes
# FIDO Example
https://github.com/fido-alliance/webauthn-demo

# Sources of information
https://webauthn.io/

# Need to reseach information about make credentials challenge

https://github.com/nodkz/mongodb-memory-server


# First step is to register and some how pass credentials
i. Capture the username and name
ii. Call getMakeCredentialsChallenge - Serer call
iii. Call preformatMakeCredReq - This will decode use base64
iv. call navigator.credentials.create (web browser sdk) - Async call to browser sdk
v. call to publicKeyCredentialToJson -- Local call to encode keys in base64
vi. sendWebAuthnResponse - Call sendWebAuthn (webauthn/response)


# Login
i. Check for username
ii. getAssertationChallenge - Makes API call to ``` /webauthn/login```
iii. preformatGetAssertReq -- decode the challenge
iv. navigator.credentials.get -- publicKey
v. public key credential to json
vi. send response to web authn


## Registeration API
i. Check request body for username and name
ii. Check in database(array) to persist information
iii. Makes generateServerMAkeRequestCredRequest
iv. Submit request challenge in request.session
v. Return the response json.  Register returns the server make cred request

## Login API
i. verify the username has been defined
ii. check the database that the credentials match
iii.  generateServerMakeGetAssertion - Get is different
iv. request username response

## Response 
i. verify parameters are passed - rawId, id, response, type
ii. Client Data -- webauthn response clientDataJSON
iii. verity that the clientData.challenge matches the request.session.challenge
iv. verify the clientData.origin and config.origin
v. verify authenticator attestation response

## generate Server Make Cred Request
i. this will return an object which has the following parameters
- challenge -- Random challenge
- rp - 
- user.id,
- user.name,
- user.displayName,
- attestation: direct?
- pubKeyCredParams.type

-- TODO need to investigation

## generate Server Get Assertion
-- Returns an object with the following attributes
{
 - challenge - a random number
 - allowCredentials

}

-- allowCredential is an array of objects with the following
- type
- id
- transports

## verifyAuthenticatorAssertionResponse


# TODO
## Research WebAuthn example with Angular/NestJS.  Question is this worth it?

## Finish reading up on generate server make cred request methods

## Fix local authentication issue

## Read documents on web
https://webauthn.guide/