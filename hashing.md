# 🔐 Hashing Algorithms Summary

This document summarizes **cryptographic hashing algorithms**, their **output sizes**, **security properties**, **known weaknesses**, and **recommended uses**.

---

## 🧠 What is a Hash Function?

A **hash function** takes an input of arbitrary length and produces a fixed-length **digest** (hash).

[
h = H(M)
]

Where:

* **H** = hash function
* **M** = message or data
* **h** = fixed-size output (digest)

### 🔒 Cryptographic Hash Functions must satisfy:

1. **Preimage resistance** — Hard to find a message from its hash
2. **Second preimage resistance** — Hard to find another message with the same hash
3. **Collision resistance** — Hard to find any two different messages with the same hash

They are widely used for:

* Digital signatures
* Password storage
* Integrity checks (checksums)
* Blockchain and cryptocurrencies

---

## 🧩 Common Hash Algorithms

| Algorithm                                         | Output Size                 | Family / Design     | Status / Usage      | Weaknesses / Concerns                                                   |
| ------------------------------------------------- | --------------------------- | ------------------- | ------------------- | ----------------------------------------------------------------------- |
| **MD5 (Message Digest 5)**                        | 128 bits                    | Merkle–Damgård      | ❌ Broken            | Collisions easy to generate; insecure for any cryptographic use.        |
| **SHA-1 (Secure Hash Algorithm 1)**               | 160 bits                    | Merkle–Damgård      | ❌ Broken            | Collisions demonstrated in 2017 (SHAttered attack).                     |
| **SHA-2 (SHA-224 / SHA-256 / SHA-384 / SHA-512)** | 224–512 bits                | Merkle–Damgård      | ✅ Secure            | No practical attacks; standard for TLS, digital signatures, etc.        |
| **SHA-3 (Keccak)**                                | 224–512 bits                | Sponge construction | ✅ Modern and secure | New design; slower in hardware but high security margin.                |
| **BLAKE2 (b2s / b2b)**                            | 224–512 bits                | HAIFA + ARX         | ✅ Secure, fast      | Highly efficient alternative to SHA-2; used in libsodium, IPFS.         |
| **BLAKE3**                                        | Variable (default 256 bits) | Merkle tree + ARX   | ✅ Secure, parallel  | Extremely fast, modern replacement; great for integrity verification.   |
| **RIPEMD-160**                                    | 160 bits                    | Merkle–Damgård      | ⚙️ Legacy           | Older but still used in Bitcoin (address hashing); slower than SHA-256. |
| **WHIRLPOOL**                                     | 512 bits                    | AES-based design    | ⚙️ Secure but rare  | Limited adoption.                                                       |
| **Tiger**                                         | 192 bits                    | Custom block cipher | ⚙️ Legacy           | Not widely used; designed for 64-bit platforms.                         |

---

## 🧮 Specialized Hashes

| Algorithm                                             | Purpose                                  | Notes                                                                   |
| ----------------------------------------------------- | ---------------------------------------- | ----------------------------------------------------------------------- |
| **HMAC (Hash-based Message Authentication Code)**     | Authentication using a hash + secret key | Secure if underlying hash (e.g., SHA-256) is secure.                    |
| **PBKDF2 (Password-Based Key Derivation Function 2)** | Password hashing / key derivation        | Standardized but slower than modern options.                            |
| **bcrypt**                                            | Password hashing                         | Uses Blowfish internally; adaptive cost; secure.                        |
| **scrypt**                                            | Password hashing                         | Memory-hard; more resistant to GPU/ASIC attacks.                        |
| **Argon2**                                            | Password hashing                         | 🏆 Winner of PHC (Password Hashing Competition); current best practice. |

---

## 🧱 Hash Function Generations

| Generation          | Algorithms            | Status                    |
| ------------------- | --------------------- | ------------------------- |
| **1st Gen (1990s)** | MD4, MD5              | Broken                    |
| **2nd Gen (2000s)** | SHA-1, RIPEMD-160     | Weak / legacy             |
| **3rd Gen (2010s)** | SHA-2, Whirlpool      | Secure                    |
| **4th Gen (2020s)** | SHA-3, BLAKE2, BLAKE3 | Modern, efficient, secure |

---

## ⚠️ Known Vulnerabilities and Attacks

| Attack Type                 | Description                       | Affects                                          |
| --------------------------- | --------------------------------- | ------------------------------------------------ |
| **Collision attack**        | Two inputs yield the same hash    | MD5, SHA-1                                       |
| **Preimage attack**         | Find input for a given hash       | Theoretical on older hashes                      |
| **Length extension attack** | Exploits Merkle–Damgård structure | SHA-2 (when used incorrectly)                    |
| **Birthday attack**         | Statistical collision shortcut    | All hash functions (theoretical limit: ~2^(n/2)) |

---

## ✅ Recommendations

* Use **SHA-256** or **SHA-3** for general-purpose hashing.
* Prefer **BLAKE2** or **BLAKE3** for performance-critical systems.
* Use **Argon2id** or **scrypt** for password hashing.
* Avoid **MD5** and **SHA-1** — completely insecure.
* Use **HMAC-SHA256** or **HMAC-SHA512** for message authentication.

---

## 📚 References

* **NIST FIPS 180-4** — Secure Hash Standard (SHA-1, SHA-2)
* **NIST FIPS 202** — SHA-3 Standard (Keccak)
* **RFC 7693** — BLAKE2 Specification
* **RFC 9106** — Argon2 Password Hashing Scheme
* **Google Security Blog (2017)** — SHAttered: SHA-1 Collision Attack

---