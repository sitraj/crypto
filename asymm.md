# 🧩 Asymmetric Encryption Algorithms Summary

This document summarizes **asymmetric (public-key) encryption algorithms**, their **key sizes**, **use cases**, and **known weaknesses**.

---

## 🔐 What is Asymmetric Encryption?

In **asymmetric encryption**, two keys are used:

* A **public key** for encryption (shared with others)
* A **private key** for decryption (kept secret)

[
Encrypt: C = E(PublicKey, M)
]
[
Decrypt: M = D(PrivateKey, C)
]

This allows **secure key exchange**, **digital signatures**, and **authentication** without sharing a secret key.

---

## 🔑 Common Asymmetric Algorithms

| Algorithm                                        | Key Type               | Typical Key Size | Primary Use                          | Weaknesses / Concerns                                                                           |
| ------------------------------------------------ | ---------------------- | ---------------- | ------------------------------------ | ----------------------------------------------------------------------------------------------- |
| **RSA (Rivest–Shamir–Adleman)**                  | Integer factorization  | 2048–4096 bits   | Encryption, signatures, TLS          | Slow; large keys; vulnerable to poor random generation; no forward secrecy in RSA key exchange. |
| **DSA (Digital Signature Algorithm)**            | Discrete log (mod p)   | 1024–3072 bits   | Digital signatures                   | Deprecated below 2048 bits; replaced by ECDSA/EdDSA.                                            |
| **Diffie–Hellman (DH)**                          | Discrete log (mod p)   | 2048–4096 bits   | Key exchange                         | No authentication by itself; weak if parameters reused; replaced by ECDHE.                      |
| **ElGamal**                                      | Discrete log (mod p)   | 2048–4096 bits   | Encryption                           | Rarely used; ciphertext expansion; probabilistic but slower than RSA.                           |
| **Elliptic Curve Cryptography (ECC)**            | Elliptic curve math    | 256–521 bits     | Encryption, signatures, key exchange | Requires careful curve selection; older curves (e.g., P-192) considered weak.                   |
| **ECDSA (Elliptic Curve DSA)**                   | ECC-based signatures   | 256–521 bits     | Digital signatures (TLS, blockchain) | Sensitive to nonce reuse; requires strong RNG.                                                  |
| **ECDH / ECDHE (Elliptic Curve Diffie–Hellman)** | ECC key exchange       | 256–521 bits     | TLS, VPN, secure messaging           | Secure and efficient; provides forward secrecy.                                                 |
| **EdDSA (Ed25519 / Ed448)**                      | Twisted Edwards curves | 255 / 448 bits   | Signatures (modern systems)          | None known; fast, secure, and deterministic.                                                    |
| **RSA-PSS**                                      | Integer factorization  | 2048–4096 bits   | Modern RSA signatures                | Secure padding (PSS) prevents signature forgeries.                                              |

---

## 🧮 Post-Quantum Algorithms (Next-Generation)

| Algorithm              | Type                      | Key Size      | Status / Usage       | Notes                                               |
| ---------------------- | ------------------------- | ------------- | -------------------- | --------------------------------------------------- |
| **CRYSTALS-Kyber**     | Lattice-based (KEM)       | ~3KB          | NIST PQC standard    | Replacement for ECDH/ECDHE; used in hybrid TLS.     |
| **CRYSTALS-Dilithium** | Lattice-based (Signature) | ~2–5KB        | NIST PQC standard    | Replacement for RSA/ECDSA.                          |
| **Falcon**             | Lattice-based (Signature) | ~1–3KB        | NIST PQC alternative | More compact signatures but complex implementation. |
| **SPHINCS+**           | Hash-based (Signature)    | Large (~40KB) | NIST PQC standard    | Very secure but slow; used for long-term archiving. |

---

## ⚙️ Key Exchange and Digital Signature Roles

| Function               | Common Algorithms            | Notes                               |
| ---------------------- | ---------------------------- | ----------------------------------- |
| **Key Exchange**       | DH, DHE, ECDH, ECDHE, Kyber  | Establish shared symmetric keys.    |
| **Digital Signatures** | RSA, ECDSA, EdDSA, Dilithium | Authenticate parties and data.      |
| **Encryption**         | RSA, ElGamal, ECC (ECIES)    | Encrypt session keys or small data. |

---

## ✅ Summary and Recommendations

* Use **ECDHE** for key exchange and **Ed25519** or **ECDSA** for digital signatures.
* Use **RSA-2048 or higher** only when ECC/EdDSA is unavailable.
* Adopt **hybrid post-quantum algorithms** (e.g., ECDHE + Kyber) for long-term security.
* Avoid **RSA key exchange**, **DSA**, and **static DH** — they lack forward secrecy.
* Always use **strong randomness** for key generation and signature nonces.

---

## 📚 References

* **NIST FIPS 186-5** — Digital Signature Standard (DSS)
* **RFC 8446** — TLS 1.3 Key Exchange Mechanisms
* **NIST PQC Project (2024)** — Post-Quantum Cryptography Standardization
* **RFC 8032** — Edwards-Curve Digital Signature Algorithm (EdDSA)

---