# Packed Attestation Statement Format
Used by authenticators with limited resources

## Packed Parameters

Attestation Types - Basic, Self, AttCA
$$ attStmtType = {
    ftm:"packed",
    attStmt: packedStatementFormat
}

packedStmtFormat = {
    alg: COSEAlgorithmIdentifier,
    sig: bytes,
    x5c: [ attestnCert: bytes, * (caCert: bytes)]
}
{
    alg: COSEAlgorithmIdentify
    sig: bytes
}

x5c -- the elements of the array contain attestnCert and its certificate chain.  Each encoded in X.509 format.  The attesation certificate (attestnCert) Must be the first element in the araray

## Signing Procedure
The following is the signing procedure for this attestation statement format

1. Let authenticatorData denote the authenicate data for the attestation, and let clientDataHash denote the has of the serialized data
2. If Basic of AttCa attestation is in use, the authenticator proceduces the sig by contatentation the authentaticatorData and clientDataHash and signing the result with the attesetation private key
3. If self attestation is in use, the authenticator produces sig by contcating authenticatingData and clientDataHash and signing the result using the credentialprivatekey it sets the alg to the algorith of the private key and omits the other fields

## Verification Procedure
The following are the inputs:
- attStmt
- authenticatorData
- clientDataHash

Procedure
1. Verify that the attStmt is valid (CBOR) confirming to the syntax defined above and perform CBOR decoding on it to extract the contained fields
2. If x5c presents
2 i. Verify that sig is a valid signature over the concatencation of authenticationData and clientDataHashusing the attestation public key in attestnCert with the alogorithm specified in alg
2ii. Verify that attestnCert meets therequirements in packed attestation statement 
2 iii. if AttestnCert contains an exentsion with OID verify that the value of this exentsion matches the aaguid in authenticationDatea
2 iv. Optionally, inspect x5c and consult externally provided knowledge to determine whether attStmt conveys a Basic or AttCA attestation
2v. If sucessful, return implementation-specific values representation attesttion type Basic, AttCA or uncertainty and attestion trus path
3. If x5c is not present, self attetion is in use
3i. validate that alg matches the algorithm of the credential pulic key in authentation Data
3ii. verify that sig is a valid signature over the concatentation of authentcationData and clientDataHash using the credential public key alg
3 iii if succesful, return implementation-specific values representating attestation type self and an empty attestation trust path.

## Packed Attestation Statement Certificate Requirements
- The attestation certificate must have the following fields/extations
-- Version must be set to 3
-- Subject feild must be set to
Subject-C -- ISO 3166 code specifying the country where the authenticator vendor is incorporated
Subject-O -- Legal name of the authenticator 
Subject-OU -- Literal string "Authentication Attestation"
Subject-CN -- 

