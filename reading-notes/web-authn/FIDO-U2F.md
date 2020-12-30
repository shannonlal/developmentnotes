The attestation statement formate is used for FIDO U2F authenticators using the formates defined

- formate 'fideo-u2f'
- attestation types supported - BASIC, AttCA

## Syntax
- $$attStmtType = {
    fmt: fido-u2f,
    attStmt: u2fStmtFormat
}
u2fStmtFormat = {
    x5c: [attestnCert: bytest],
    sig: bytest
}

x5c - A single element array containing the attestation certificate in X.509 formate
sig - The attestation signature  - The signature was calculated over the (raw) registration response messgae

## Signing Procedure
If the credential public key of the attested credentials is not algorithm "-7" STOP AND RETURN ERROR.  Otherwise, let authenticatorData denote the authentication data for the attestation and let clientDataHas

Generate a registattion response message 
- application parameter set to the SHA-256 has of the RP ID scoped to.  The challenge parameter set to the clientDataHash and the key handler parameter set to the creeidneial Id