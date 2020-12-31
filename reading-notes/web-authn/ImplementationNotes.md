# Notes to implement.
1. Start by building a backend that works correctly.  Lift the packed function from this

Looking at the 

WebAuthn uses a Attestation Challenge builder

- First step.  Move webauthn Backend to talk to new UI and see what happens

# Attestation Notes:
- none. value indicates that the relying party is not interested in authentication attestation.  

Note: Needed to change the origin source
Disabling the authtenticator.
cross-platform are removeable and can be moved across devices
platform (touch id)

# Issues with webauthn client
1. Missing Apple Implementation
2. Intertwined the Client with API calls.  They should be seperate
3. Should use typescript with better types
4. Should be built with a library

## Library
-- Client
Webauthn -> getAssertionChallenge
Webauthn -> getAttesetationChallenger
Webauthn -> Typescript Types
-- Use Unit Test

-- Server Library
AssertionChallengeBuilder
AttestationChallengeBuilder
