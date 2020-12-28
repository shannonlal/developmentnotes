The starting notes on webauthn notes
# FIDO Example
https://github.com/fido-alliance/webauthn-demo

# Sources of information
https://webauthn.io/

# Need to reseach information about make credentials challenge



# First step is to register and some how pass credentials
i. Capture the username and name
ii. Call getMakeCredentialsChallenge - Serer call
iii. Call preformatMakeCredReq - This will decode use base64
iv. call navigator.credentials.create (web browser sdk) - Async call to browser sdk
v. call to publicKeyCredentialToJson -- Local call to encode keys in base64
vi. sendWebAuthnResponse - Call sendWebAuthn (webauthn/response)


# Login
1