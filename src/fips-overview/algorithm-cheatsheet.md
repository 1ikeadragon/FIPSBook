# Algorithm Cheatsheet
**FIPS-Compliant Cryptographic Algorithms**

|Algorithm Category|Algorithm Name|Variants|Minimum Key Length|Maximum Key Length|Approved Uses|FIPS Status|FIPS Reference|Notes/Restrictions|
|---|---|---|---|---|---|---|---|---|
|**Block Cipher**|**AES** (Advanced Encryption Standard)|AES-128, AES-192, AES-256|128 bits|256 bits|Encryption, decryption, key wrapping, CMAC, GCM, XTS|**Current**|FIPS 197, SP 800-38A, SP 800-38B, SP 800-38C, SP 800-38D, SP 800-38F, SP 800-38G|Used in various modes of operation, key wrapping, CMAC and other protocols. XTS-AES requires a 256- or 512-bit key, which is parsed into two AES keys.|
|**Block Cipher**|**TDEA** (Triple Data Encryption Algorithm)|Two-key TDEA, Three-key TDEA|112 bits|168 bits|Decryption and unwrapping of legacy data, CMAC verification|**Legacy** (Two-key) **Deprecated** through 2023, **Disallowed** after 2023 (Three-key)|SP 800-67|Two-key TDEA is allowed for legacy use only for decryption and unwrapping but is disallowed for encryption. Three-key TDEA is deprecated for encryption through 2023, disallowed after 2023.|
|**Block Cipher**|**SKIPJACK**||||Decryption/Unwrapping|**Legacy**|||
|**Hash Function**|**SHA-1** (Secure Hash Algorithm 1)||||Non-digital signature applications, verification of digital signatures on legacy data|**Legacy** for digital signature verification; **Disallowed** for digital signature generation|FIPS 180-4|SHA-1 is disallowed for digital signature generation except where specifically allowed by NIST protocol-specific guidance. Legacy use is allowed for digital signature verification.|
|**Hash Function**|**SHA-2** Family|SHA-224, SHA-256, SHA-384, SHA-512, SHA-512/224, SHA-512/256|||All hash function applications|**Current**|FIPS 180-4||
|**Hash Function**|**SHA-3** Family|SHA3-224, SHA3-256, SHA3-384, SHA3-512, SHAKE128, SHAKE256|||All hash function applications|**Current**|FIPS 202|Also includes extendable-output functions SHAKE128 and SHAKE256.|
|**Message Authentication Code (MAC)**|**CMAC** (Cipher-based MAC)|Two-key TDEA, Three-key TDEA, AES-128, AES-192, AES-256|112 bits|256 bits|MAC verification, message authentication|**Legacy** (Two-key and Three-key TDEA), **Current** (AES)|SP 800-38B|Two-key and three-key TDEA are legacy for CMAC verification only. AES is acceptable for CMAC verification. Requires the use of a block cipher.|
|**Message Authentication Code (MAC)**|**HMAC** (Keyed-Hash MAC)||112 bits||Message authentication, HMAC verification|**Current** (key lengths ≥ 112 bits), **Legacy** (key lengths < 112 bits)|FIPS 198-1|Requires a hash function; key lengths less than 112 bits are disallowed for generation, but allowed for legacy verification.|
|**Message Authentication Code (MAC)**|**GMAC** (Galois/Counter Mode MAC)|AES-128, AES-192, AES-256|128 bits|256 bits|MAC generation and verification|**Current**|SP 800-38D||
|**Message Authentication Code (MAC)**|**KMAC** (Keyed Message Authentication Code)||112 bits||MAC generation and verification|**Current**||Key lengths less than 112 bits are disallowed for generation|
|**Key Derivation Function (KDF)**|**PBKDF** (Password-Based KDF)||||Key derivation|**Current**||PBKDF is an approved KDF|
|**Key Derivation Function (KDF)**|**KDF** (from SP 800-135rev1)|IKEv1, IKEv2, TLS 1.0, 1.1, 1.2, SSHv2, SRTP, SNMPv3, TPMv1.2, ANSI X9.63-2001, ANSI X9.42-2001|||Key derivation for protocols|**Current**|SP 800-135rev1|The KDFs from these protocols are considered algorithms. Validation testing is available.|
|**Key Derivation Function (KDF)**|**KDF** (from SP 800-56C)||||Key derivation for key agreement schemes|**Current**|SP 800-56C|Used for key agreement schemes. A one-step KDF without a counter is also approved.|
|**Key Agreement Scheme**|**Diffie-Hellman (DH)** and **Menezes-Qu-Vanstone (MQV)**|FFC DH and ECC CDH|||Key agreement|**Current** (if using safe-prime groups or FIPS 186-type domain parameters with minimum security strength of 112 bits)|FIPS 186, SP 800-56A|Security strength less than 112 bits is disallowed.|
|**Key Transport Scheme**|**RSA** (Rivest-Shamir-Adleman)||2048 bits||Key transport|**Current**|SP 800-56B|RSA key transport must comply with SP 800-56B, with the exception of PKCS#1-v1.5 padding, which is deprecated through 2023 and disallowed after 2023. 1024-bit RSA modulus may be used for legacy verification, but not generation.|
|**Key Transport Scheme**|**KTS** (Key Transport Scheme)||||Key transport, key wrapping|**Current**||Symmetric key based key transport (e.g. AES key wrap), or assymetric key based key transport schemes such as KTS-IFC may be used.|
|**Digital Signature Algorithm**|**RSA** (Rivest-Shamir-Adleman)|RSASSA-PKCS1-v1.5, RSASSA-PSS|2048 bits||Digital signature generation and verification|**Current** (2048 and 3072 bits), **Legacy** (1024 bit modulus for verification)|FIPS 186-4, FIPS 186-5|1024-bit RSA modulus is allowed for legacy verification purposes only.|
|**Digital Signature Algorithm**|**DSA** (Digital Signature Algorithm)||||Digital signature generation and verification|**Legacy**|FIPS 186-2, FIPS 186-4|DSA signature verification is allowed for legacy use.|
|**Digital Signature Algorithm**|**ECDSA** (Elliptic Curve Digital Signature Algorithm)|Deterministic ECDSA signature generation|||Digital signature generation and verification|**Current**|FIPS 186-4, FIPS 186-5, SP 800-186|Uses approved elliptic curves|
|**Digital Signature Algorithm**|**EdDSA** (Edwards-curve Digital Signature Algorithm)||||Digital signature generation and verification|**Current**|FIPS 186-5||
|**Digital Signature Algorithm**|**Hash-based Signature Schemes** (LMS, XMSS, HSS)||||Digital signature generation and verification|**Current**|SP 800-208|Stateful hash-based signature schemes. Key generation and signature generation must be implemented for a given parameter set. Implementations must be within a hardware module and be FIPS 140-2 or FIPS 140-3 Level 3 or higher.|
|**Post-Quantum Algorithm**|**ML-KEM** (Module-Lattice-based Key-Encapsulation Mechanism)||||Key encapsulation|**Current**|FIPS 203|ML-KEM encapsulation algorithm must be tested for KAT.|
|**Post-Quantum Algorithm**|**ML-DSA** (Module-Lattice-based Digital Signature Algorithm)||||Digital signature generation and verification|**Current**|FIPS 204||
|**Post-Quantum Algorithm**|**SLH-DSA** (StateLess Hash-based Digital Signature Algorithm)||||Digital signature generation and verification|**Current**|FIPS 205||

**Notes:**

- **Security Strengths:** The security strength of an algorithm is measured in bits and represents the estimated computational effort required to break the algorithm. The table lists the security strength in bits as described in SP 800-57.
- **Legacy Algorithms:** Legacy algorithms are those that are no longer approved for new applications but are allowed for processing already protected information (e.g., decryption or signature verification).
- **Deprecated Algorithms:** Deprecated algorithms are those that are still allowed for a limited time but should be replaced by stronger alternatives as soon as possible.
- **Disallowed Algorithms:** Disallowed algorithms are those that are no longer approved for any use.
- **Key Sizes**: The key lengths specified are minimums for FIPS compliance. Implementations should use the largest approved key size appropriate for the required security strength and application.
- **Transition Dates:** Some algorithms have specific transition dates. After these dates, the use of those algorithms may be restricted or disallowed.
- **SP 800-131A:** SP 800-131A provides guidance on transitioning to stronger cryptographic keys and algorithms, and it defines the terms "acceptable", "deprecated", "legacy use", and "disallowed" for cryptographic algorithms.
- **Self-Tests:** Cryptographic modules must perform self-tests on all implemented cryptographic algorithms before the first operational use. These tests are called Cryptographic Algorithm Self-Tests (CASTs). The algorithms must be tested using the smallest approved key length or modulus size.
- **Component Validation List (CVL):** The CAVP and CMVP have identified several components of approved algorithms that can be used in an approved mode of operation. These components are listed as "CVL" in the CMVP documentation.
- **Vendor Affirmation:** For some algorithms, if CAVP testing is not available, vendor affirmation may be allowed. In this case, the vendor must provide clear documentation and reasoning as to why the algorithm can be used in the approved mode and must meet the requirements set out in the relevant IGs.
- **Non-Approved Security Functions:** Non-approved security functions, such as non-approved algorithms, may be used in an approved mode of operation if certain requirements are met. They should not be used to meet the requirements of FIPS 140-3 sections 6 and 7. Non-approved algorithms are not to access or share CSPs in a way that counters the requirements.
- **FIPS 186-5:** FIPS 186-5 specifies the approved elliptic curves for ECDSA.

**Additional Notes:**

- **FIPS 140-2 vs FIPS 140-3:** FIPS 140-2 is still valid, but as of March 31, 2022, cryptographic modules are no longer tested for FIPS 140-2 certifications. FIPS 140-3 is the current standard and incorporates ISO/IEC 19790:2012 and ISO/IEC 24759:2017.
- **CMVP:** The Cryptographic Module Validation Program (CMVP) is a joint effort between NIST and the Canadian Centre for Cyber Security (CCCS) that validates cryptographic modules.
- **Key Derivation:** Key derivation functions (KDFs) are used to generate keys from a secret value. Approved KDFs are listed in SP 800-135 and SP 800-56C.
- **Key Agreement:** Key agreement schemes, like Diffie-Hellman (DH) and Menezes-Qu-Vanstone (MQV), are used to establish shared secrets between two parties.
- **Digital Signatures:** Digital signatures, such as RSA, DSA, and ECDSA, provide authentication and non-repudiation.
- **Hash Functions**: Hash functions like SHA-1, SHA-2, and SHA-3 are used to create message digests or checksums of data. SHA-1 is disallowed for digital signature generation.
- **Message Authentication Codes (MACs)**: MACs like HMAC, CMAC, and GMAC provide integrity and authenticity.
