https://w3c.github.io/webauthn/#sctn-defined-attestation-formats

Should be registered with the IANA webauthn attestation statement
All atestation statement formate identifies must be a maximum of 32 octets in length and must consist only of printable USASCII characters excluding backslash and doublequote.



# Cryptographic Algorithm Identifier ( COSEAlgorithmIdenitifer)
The algorithm identifier should be values registered in the IANA COSE algorithm registry (IANA-COSE-ALGS-REG)

```
Keys with algorithm ES256 (-7) MUST specify P-256 (1) as the crv parameter and MUST NOT use the compressed point form.

Keys with algorithm ES384 (-35) MUST specify P-384 (2) as the crv parameter and MUST NOT use the compressed point form.

Keys with algorithm ES512 (-36) MUST specify P-521 (3) as the crv parameter and MUST NOT use the compressed point form.

Keys with algorithm EdDSA (-8) MUST specify Ed25519 (6) as the crv parameter. (These always use a compressed form in COSE.)
```

