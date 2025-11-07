# 🧩 Symmetric Encryption Algorithms Summary

This document summarizes **symmetric encryption algorithms**, their **key sizes**, **security status**, and **known weaknesses**.
It includes both **block ciphers** and **stream ciphers**.

---

## 🔒 What is Symmetric Encryption?

In **symmetric encryption**, the **same key** is used for both **encryption** and **decryption**.

[
Encrypt: C = E_K(M)
]
[
Decrypt: M = D_K(C)
]

Where:

* **K** = shared secret key
* **M** = plaintext
* **C** = ciphertext

Both parties must **already share** the key securely (for example, using DHE/ECDHE in TLS).

---

## 🧱 Block Cipher Algorithms

| Algorithm                              | Block Size    | Key Size(s)          | Status / Usage                        | Weaknesses / Concerns                                               |
| -------------------------------------- | ------------- | -------------------- | ------------------------------------- | ------------------------------------------------------------------- |
| **AES (Advanced Encryption Standard)** | 128 bits      | 128 / 192 / 256 bits | Highly secure, global standard        | None practical; possible side-channel issues if implemented poorly. |
| **DES (Data Encryption Standard)**     | 64 bits       | 56 bits              | Obsolete                              | Brute-force feasible; small block size leaks patterns.              |
| **3DES (Triple DES)**                  | 64 bits       | 112 / 168 bits       | Deprecated (NIST retired 2023)        | Slow; birthday attack after ~32 GB; meet-in-the-middle weakness.    |
| **Blowfish**                           | 64 bits       | Up to 448 bits       | Old but still used in some systems    | 64-bit block size leads to collisions; slow key setup.              |
| **Twofish**                            | 128 bits      | Up to 256 bits       | Secure (AES finalist)                 | No practical attacks; slower than AES.                              |
| **Camellia**                           | 128 bits      | 128 / 192 / 256 bits | Secure, used in TLS (especially Asia) | No practical weaknesses.                                            |
| **IDEA**                               | 64 bits       | 128 bits             | Legacy (old PGP versions)             | Small block size; old design.                                       |
| **Serpent**                            | 128 bits      | Up to 256 bits       | Very secure                           | Slower than AES (conservative design).                              |
| **CAST-128 / 256**                     | 64 / 128 bits | Up to 256 bits       | Older (PGP use)                       | Limited analysis; 64-bit blocks not ideal.                          |

---

## 🌊 Stream Cipher Algorithms

| Algorithm           | Key Size(s)    | Status / Usage                   | Weaknesses / Concerns                                    |
| ------------------- | -------------- | -------------------------------- | -------------------------------------------------------- |
| **RC4**             | 40–2048 bits   | Deprecated (removed from TLS)    | Severe biases in keystream; plaintext recovery possible. |
| **ChaCha20**        | 256 bits       | Modern and secure (TLS 1.3)      | None known; must use unique nonces.                      |
| **Salsa20**         | 256 bits       | Secure (predecessor of ChaCha20) | None practical; replaced by ChaCha20.                    |
| **HC-128 / HC-256** | 128 / 256 bits | Secure but niche                 | Complex implementation; side-channel risks.              |
| **Grain v1 / v2**   | 80 / 128 bits  | Used in IoT                      | Weak initialization phase in early versions.             |
| **Rabbit**          | 128 bits       | Used in eSTREAM suite            | Must use unique IVs; possible related-key issues.        |
| **SEAL**            | 160 bits       | Research cipher                  | Limited adoption; depends on good randomness.            |

---

## ⚙️ Modes of Operation (for Block Ciphers)

| Mode                            | Description                                | Notes                           |
| ------------------------------- | ------------------------------------------ | ------------------------------- |
| **ECB (Electronic Codebook)**   | Encrypts each block independently          | ❌ Insecure; leaks patterns.     |
| **CBC (Cipher Block Chaining)** | Chains each block with previous ciphertext | Secure if used with random IVs. |
| **CTR (Counter Mode)**          | Turns AES into a stream cipher             | Fast and parallelizable.        |
| **GCM (Galois/Counter Mode)**   | Adds authentication (AEAD)                 | Standard in TLS 1.2 / 1.3.      |
| **CCM (Counter + CBC-MAC)**     | AEAD for constrained devices               | Used in WPA3 and IoT.           |

---

## 🧠 Summary and Recommendations

* ✅ **Use AES (preferably AES-GCM)** or **ChaCha20-Poly1305** for modern encryption.
* ❌ **Avoid DES, 3DES, Blowfish, and RC4** — all are insecure or deprecated.
* ⚠️ Always use **unique nonces/IVs** and protect against **side-channel leaks**.
* 🔐 Ensure **secure random number generation** for key creation.
* 🧩 AES-GCM (block cipher) and ChaCha20-Poly1305 (stream cipher + AEAD) are the current standards for **TLS 1.3**, **VPNs**, and **secure messaging**.

---

## 📚 References

* NIST SP 800-38A & SP 800-57 — *Recommendation for Block Cipher Modes*
* RFC 8439 — *ChaCha20 and Poly1305 for IETF Protocols*
* RFC 8446 — *TLS 1.3 Standard*
* NIST Announcement (2023) — *Retirement of 3DES (TDEA)*

---

