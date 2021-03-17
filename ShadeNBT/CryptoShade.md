# CryptoShade Variant 

In addition to Standard ShadeNBT, Implementations may support CryptoShade to password protect save files. 

These are achieved through extensions to the base specification, detailed below. 

These extensions MAY be provided without in any manner, including supporting loading of encrypted files, but not saving. 

These extensions may be applied to any version of the ShadeNBT Specification.

## The CryptoShade Header

The CryptoShade header consists of a valid ShadeNBT header, except that magic is the bytes `[EC 4E 42 54]` instead of `[AD 4E 42 54]` and that header shall be followed by a ushort numBlocks, a 32-byte salt, and a 16-byte IV. 
Following this, a SHA-256 hash of the password, with the first 8 bytes of the salt appended, appears. When loading with a password this field MUST match.

For version 1.3 or later, the SHA-256 hash for shadeFlag 0x40 appears after the complete CryptoShade Header, before the content of the file, and the hash is of the `TAG_Compound`. 

The Remainder of the file is numBlocks blocks of 16-bytes instead of a `TAG_Compound`. These blocks, when decrypted as below, MUST result in a valid `TAG_Compound` which could exist inside a ShadeNBT File with the same version, and ShadeFlags (if applicable), that are used with this CryptoShade File. 



## Encryption/Decryption

In addition to the IV and Salt, there is additionally a hidden password for the file. This password MAY be user-supplied. 

A Symmetric Encryption Key MUST be generated for the AES-256 Algorithm by appending the salt to the UTF-8 Encoded Password, then taking the SHA-256 Hash of the result. 

The blocks shall be encrypted/decrypted using this Key, with the AES-256 Algorithm, using PKCS5 Padding, and CBC Mode. 

When emitting a new CryptoShade file, first the IV and Salt MUST be generated from a Cryptographically Secure Random Number Source. When emitting an updated file, at least one of these MUST be regenerated, as above, however both SHOULD be regenerated.