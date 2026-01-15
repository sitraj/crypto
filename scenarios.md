Here’s a curated list of **Security System Design Scenarios** grouped by **complexity** and **category** — the kind asked during the security engineering interview.

Each scenario tests a different *axis* of your expertise: encryption, authentication, key management, privacy, trust boundaries, or incident response.

---

# 🧩 **I. Authentication & Access Control Systems**

### **1. Passwordless Authentication (FIDO2 / Passkeys)**

**Prompt:** Design a passwordless authentication system for a web and mobile app.
**Key topics:** WebAuthn, device-bound keys, attestation, anti-phishing, sync via platform key vaults.
**Complexity:** Medium-high.
**Challenges:** Credential registration, sync across devices, revocation, key attestation.

---

### **2. OAuth + End-to-End Encryption Integration**

**Prompt:** Design a system that uses OAuth (Google/Apple login) to authenticate users, but all user data is end-to-end encrypted such that the OAuth provider cannot decrypt anything.
**Key topics:** Identity provider trust minimization, token exchange, client-side key derivation, envelope encryption.
**Complexity:** Medium.
**Challenges:** Mapping OAuth user to encrypted storage keys, zero-knowledge recovery.

---

### **3. Just-in-Time Access Control System**

**Prompt:** Design an internal service that issues time-bound credentials for accessing sensitive production data.
**Key topics:** Ephemeral credentials, signed tokens (JWT), KMS, short TTLs, RBAC, audit logging.
**Complexity:** Medium.
**Challenges:** Key rotation, enforcement of TTLs, multi-party approvals.

---

# 🔐 **II. Key Management & Cryptographic Systems**

### **4. Multi-Party Wallet (Threshold Signatures)**

**Prompt:** Design a self-custodial crypto wallet where transactions require 2-of-3 devices to sign, and recovery is possible if one device is lost.
**Key topics:** Threshold signatures (TSS), MPC, Shamir Secret Sharing, backup and recovery, revocation.
**Complexity:** High.
**Challenges:** Device coordination, offline signing, key rotation, recovery UX.

---

### **5. End-to-End Encrypted Cloud Storage (Zero Knowledge)**

**Prompt:** Build a Dropbox-like product where even the provider can’t read files.
**Key topics:** Client-side encryption, key hierarchies, sharing (re-encryption), integrity protection.
**Complexity:** High.
**Challenges:** File chunking, metadata encryption, sharing via key wrapping.

---

### **6. Secure API Key Distribution**

**Prompt:** Design a system that securely distributes and rotates API keys to thousands of microservices.
**Key topics:** Secret distribution, PKI, HSM, identity-based access, mTLS, key rotation automation.
**Complexity:** Medium-high.
**Challenges:** Minimizing blast radius, automated rotation, compromise detection.

---

### **7. Hardware-Backed Key Attestation System**

**Prompt:** Design a service that ensures devices only connect if they’re running verified firmware (attestation).
**Key topics:** TPM, Secure Enclave, signed attestations, challenge-response, hardware root of trust.
**Complexity:** High.
**Challenges:** Attestation freshness, replay protection, root key rotation, privacy of attestation data.

---

# 🧠 **III. Privacy-Preserving & Identity Systems (Tools for Humanity–Style)**

### **8. Anonymous Credential Issuance & Verification**

**Prompt:** Design a system where a user can prove “I’m verified human” without revealing who they are or when they were verified.
**Key topics:** Blind signatures, ZKPs, nullifiers, selective disclosure.
**Complexity:** High.
**Challenges:** Prevent double-use, unlink issuance from presentation, revocation.

---

### **9. Biometric Deduplication Without Exposure**

**Prompt:** Build a service that ensures each person can only register once (e.g., via iris or face), but the biometric data is never exposed to the server.
**Key topics:** Homomorphic encryption, privacy-preserving matching, commitments, ZK proofs.
**Complexity:** Very High.
**Challenges:** Matching under encryption, false positives, privacy leakage mitigation.

---

### **10. Anonymous Payment System**

**Prompt:** Design a payment system where users can send funds using their wallet but the payment can’t be linked to their identity.
**Key topics:** Ring signatures, stealth addresses, confidential transactions, ZK proofs.
**Complexity:** Very High.
**Challenges:** Balance privacy, regulatory compliance, and fraud detection.

---

### **11. Private Age Verification**

**Prompt:** Build a system where a user can prove they’re over 18 without revealing their birth date.
**Key topics:** Selective disclosure credentials, ZK range proofs.
**Complexity:** Medium-high.
**Challenges:** Efficient proofs, revocation, UX for verifiers.

---

# 🛡️ **IV. Infrastructure & Product Security**

### **12. Secrets Management Platform**

**Prompt:** Design a secrets management system like HashiCorp Vault.
**Key topics:** Secret lifecycle, encryption at rest, access control, audit logs, dynamic secrets.
**Complexity:** Medium.
**Challenges:** Distributed trust, HA setup, token authentication, encryption keys rotation.

---

### **13. Secure Software Update System**

**Prompt:** Design an update system for devices that ensures only authentic firmware is installed.
**Key topics:** Code signing, root of trust, rollback protection, transparency logs.
**Complexity:** High.
**Challenges:** Key management, revocation, offline verification.

---

### **14. Data Tokenization / De-identification Pipeline**

**Prompt:** Design a pipeline that de-identifies personal data while allowing analytical queries.
**Key topics:** Tokenization, differential privacy, format-preserving encryption.
**Complexity:** Medium-high.
**Challenges:** Linkage attacks, re-identification risk, auditability.

---

### **15. Insider Threat–Resilient Data Access**

**Prompt:** Build a data access architecture such that even admins cannot exfiltrate sensitive customer data.
**Key topics:** Just-in-time encryption keys, split trust, audit logs, proxy re-encryption.
**Complexity:** Very High.
**Challenges:** Balancing operational needs, auditing overhead, encrypted search.

---

# ⚙️ **V. Detection, Incident Response & Abuse Prevention**

### **16. Key Compromise Recovery Plan**

**Prompt:** Design how your company would detect, contain, and recover from a key compromise in production.
**Key topics:** Rotation, revocation, transparency logs, backup recovery.
**Complexity:** Medium.
**Challenges:** Fast detection, communication, revocation cascades.

---

### **17. Abuse Prevention Without Identity**

**Prompt:** You have an anonymous network (like Tor or Worldcoin). How do you prevent abuse (spam, Sybil attacks) while preserving anonymity?
**Key topics:** Rate-limiting via nullifiers, proof-of-personhood, zero-knowledge proof of stake, per-RP limits.
**Complexity:** High.
**Challenges:** Balance privacy vs accountability.

---

### **18. Secure Telemetry System**

**Prompt:** Design a telemetry collection system where sensitive metrics are aggregated but no individual data point is exposed.
**Key topics:** Local differential privacy, secure aggregation, homomorphic addition.
**Complexity:** High.
**Challenges:** Noise calibration, collusion, dropouts.

---

# 🌐 **VI. Advanced Cloud + Crypto Systems**

### **19. E2E Encrypted File Sharing with Delegation**

**Prompt:** Build a file-sharing system where users can delegate read access to others without re-uploading files.
**Key topics:** Key wrapping, re-encryption (Proxy Re-Encryption, PRE), per-user access control.
**Complexity:** High.
**Challenges:** Revocation, metadata leakage, auditability.

---

### **20. Confidential Computing Deployment**

**Prompt:** Design a service that processes encrypted data inside enclaves (SGX/SEV) to maintain confidentiality even from the host cloud.
**Key topics:** Enclave attestation, remote key provisioning, sealing keys, threat model.
**Complexity:** Very High.
**Challenges:** Side-channel risks, sealing key rotation, measurement verification.

---

# 🧠 **How to Practice for Each Scenario**

For each:

1. **Start with goals & threat model** — confidentiality, integrity, authenticity, availability, privacy.
2. **Define trust boundaries** — who can see what?
3. **Choose primitives** — AEAD, HKDF, Argon2id, ZK, PRE, etc.
4. **Map data flow** — generation → storage → access → deletion.
5. **List mitigations** — key rotation, rate limiting, attestation, monitoring.
6. **Explain trade-offs** — usability vs. privacy vs. performance.
7. **Summarize crisply** — a 1-minute executive summary.

---

