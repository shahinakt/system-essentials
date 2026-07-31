# Phase 4 — Complete Study Package
## Advanced Cybersecurity Specialization
### Chapter Reading Lists · Weekly Schedules · Graded Problem Sets

---

> **Prerequisites before starting Phase 4:** All Phase 3 milestone assessments passed. You must be fluent in: C and memory management (Module 3.1), x86-64 assembly (Module 3.2), operating system internals including paging, system calls, and filesystems (Module 3.3), concurrency and TOCTOU (Module 3.4), and advanced Linux systems programming (Module 3.5). Phase 4 is where every preceding phase converges. The security researcher is a systems programmer who understands attack and defense simultaneously — each module here assumes you can read assembly, reason about memory layouts, understand kernel data structures, and implement tools from scratch.

---

# MODULE 4.1 — Cryptography: Theory & Practice

**Duration:** 12–14 weeks | **Hours/week:** 12–15 | **Total hours:** ~180

---

## Part A: Chapter-by-Chapter Reading List

### Primary Text: Boneh & Shoup — *A Graduate Course in Applied Cryptography* (free at crypto.stanford.edu)

---

### Chapter 1 — Symmetric Encryption

**Section 1.1 — Shannon Ciphers and Perfect Security**
Focus on: the formal definition of a Shannon cipher (key space K, message space M, ciphertext space C); perfect secrecy: P[M=m | C=c] = P[M=m] for all m, c; the one-time pad; Shannon's theorem: perfect secrecy requires |K| >= |M|. This section proves what "unbreakable" means mathematically.

**Section 1.2 — Computational Ciphers and Semantic Security**
Focus on: the computational adversary (polynomial-time bounded); negligible functions; the semantic security game (IND-EAV); the formal definition using a challenger-adversary experiment. All subsequent security definitions follow this game-based template.

**Section 1.3 — Stream Ciphers**
Focus on: the PRG (Pseudorandom Generator) as the building block; semantic security from a secure PRG (reduction proof); attacks on weak PRGs (linear feedback shift registers).

**Section 1.4 — Block Ciphers**
Focus on: the PRP (Pseudorandom Permutation) definition; modes of operation: ECB (insecure — penguin attack), CBC (IV must be unpredictable), CTR (turns block cipher into stream cipher). The ECB penguin attack is the canonical example of why mode of operation matters.

**Section 1.5 — Chosen Plaintext Attack Security (CPA)**
Focus on: the IND-CPA security game; why ECB fails IND-CPA; why CBC with random IV achieves IND-CPA; nonce-based encryption.

---

### Chapter 2 — Authenticated Encryption

**Section 2.1 — Chosen Ciphertext Security (CCA)**
Focus on: the IND-CCA2 security game; the padding oracle attack: given a decryption oracle that reveals whether CBC padding is valid, an attacker can decrypt any ciphertext one byte at a time. This is the most important concrete attack in symmetric cryptography.

**Section 2.2 — Message Authentication Codes**
Focus on: the MAC security game (EUF-CMA); HMAC construction and its security proof; the length extension attack on hash-based MACs without HMAC (why H(key || message) is insecure).

**Section 2.3 — Authenticated Encryption**
Focus on: AEAD definition; AES-GCM construction (CTR mode encryption + GHASH authentication); the catastrophic nonce reuse attack on AES-GCM; ChaCha20-Poly1305; Encrypt-then-MAC composition (provably secure); why MAC-then-Encrypt (TLS pre-1.3) is vulnerable to padding oracle attacks.

---

### Chapter 3 — Public Key Encryption

**Section 3.1 — Public Key Encryption: Definitions**
Focus on: IND-CPA and IND-CCA2 for public key encryption; the key generation, encryption, decryption algorithms.

**Section 3.2 — RSA**
Focus on: RSA key generation; textbook RSA insecurity (deterministic, malleable); RSA-OAEP for CCA2 security; RSA-PSS for signatures. Attacks: small public exponent (e=3) with cube root; broadcast attack; common modulus attack.

**Section 3.3 — ElGamal Encryption**
Focus on: the Decisional Diffie-Hellman (DDH) assumption; ElGamal malleability (ciphertext (c1,c2) -> (c1, lambda*c2) decrypts to lambda*m).

**Section 3.4 — Hybrid Encryption**
Focus on: the KEM-DEM framework; why hybrid encryption (RSA/ECDH for key, AES-GCM for data) is the standard construction.

---

### Chapter 5 — Cryptographic Hashing

**Section 5.1 — Security Properties**
Focus on: preimage resistance, second preimage resistance, collision resistance and their relationships.

**Section 5.2 — Merkle-Damgard Construction**
Focus on: how MD processes message blocks; length padding; the length extension attack. SHA-1 and SHA-2 are Merkle-Damgard; SHA-3 (Keccak) is a sponge construction that resists length extension.

**Section 5.3 — Cryptographic Randomness**
Focus on: CSPRNG definition; /dev/urandom vs /dev/random; the Dual EC DRBG backdoor (NSA-inserted trapdoor in a NIST-standardized PRNG).

---

### Chapter 7 — Public Key Signatures

**Section 7.1 — Digital Signature Definitions**
Focus on: EUF-CMA (existential unforgeability under chosen message attack); the random oracle model.

**Section 7.2 — RSA Signatures**
Focus on: RSA-PSS; the Bleichenbacher signature forgery against PKCS#1 v1.5 (CVE-2006-4339 — many TLS implementations were vulnerable).

**Section 7.3 — Schnorr Signatures and DSA**
Focus on: the Fiat-Shamir transform; ECDSA; the ECDSA nonce reuse vulnerability: if the same nonce k is reused in two signatures, the private key is immediately recoverable. The PS3 signing key was broken this way.

---

### Chapter 9 — Key Exchange

**Section 9.1 — Diffie-Hellman Key Exchange**
Focus on: CDH and DDH problems; MITM attack on unauthenticated DH.

**Section 9.2 — The SIGMA Protocol**
Focus on: SIGMA as the authenticated key exchange protocol; how TLS 1.3 and IKEv2 are instantiated from SIGMA; forward secrecy, mutual authentication, identity protection.

**Section 9.3 — Elliptic Curve Cryptography**
Focus on: the elliptic curve group law; scalar multiplication as the hard problem (ECDLP); Curve25519; secp256k1; P-256. The small subgroup attack on DH groups that are not prime-order; why Curve25519 prevents this (cofactor clearing).

---

### Chapter 13 — Protocols Using Cryptography

**Section 13.1 — TLS 1.3** (read alongside RFC 8446)
Focus on: the handshake flow (ClientHello, ServerHello, CertificateVerify, Finished); key schedule (HKDF-based derivation); 0-RTT and its replay vulnerability; downgrade attack prevention via transcript hash.

**Section 13.2 — The Signal Protocol**
Focus on: the Double Ratchet algorithm (DH ratchet for forward secrecy + symmetric ratchet for break-in recovery); X3DH for initial key establishment.

---

### Chapter 15 — Post-Quantum Cryptography

**Section 15.1 — Quantum Threats**
Focus on: Shor's algorithm breaks RSA and ECDH; Grover's algorithm halves symmetric security levels; timeline for cryptographically relevant quantum computers.

**Section 15.2 — Lattice-Based Cryptography**
Focus on: the Learning With Errors (LWE) problem; CRYSTALS-Kyber (NIST KEM) and CRYSTALS-Dilithium (NIST signatures).

---

### Supplementary Texts
- Katz & Lindell — *Introduction to Modern Cryptography*, 3rd ed. (alternative proofs)
- Ferguson, Schneier & Kohno — *Cryptography Engineering* (implementation focus)
- **Cryptopals Matasano Crypto Challenges (cryptopals.com) — mandatory: complete all 8 sets**
- RFC 8446 (TLS 1.3) — read the full specification

---

## Part B: Week-by-Week Study Schedule

### Week 1 — Stream Ciphers and Fundamentals
- B&S Ch. 1.1-1.3. Prove perfect secrecy of the one-time pad. Prove Shannon's lower bound.
- **Cryptopals Set 1 (all challenges).** The repeating-key XOR attack (challenge 6) is a rite of passage.
- Implement AES-128 from scratch (S-box, MixColumns, ShiftRows, KeySchedule). No libraries.

### Week 2 — Block Cipher Modes and CPA Security
- B&S 1.4-1.5. ECB penguin attack demonstration. CBC mode implementation.
- Cryptopals Set 2 (challenges 9-12). Byte-at-a-time ECB decryption.
- Implement AES-CBC, AES-CTR. Test with NIST test vectors.

### Week 3 — Authenticated Encryption and Padding Oracle
- B&S Ch. 2. Padding oracle attack — implement the complete attack against CBC decryption.
- Cryptopals Set 2 (challenges 13-16). CBC bitflip attack.
- Implement HMAC-SHA256 from scratch. Implement AES-GCM (GHASH + CTR).
- Nonce reuse attack on AES-GCM: given two ciphertexts encrypted with the same nonce, recover the keystream.

### Week 4 — Hash Functions and MACs
- B&S Ch. 5. SHA-256 from scratch (implement the full round function).
- Length extension attack: implement against naive H(key || message) MAC.
- Cryptopals Set 4 (challenges 28-31). HMAC timing attack (challenge 31): recover HMAC byte-by-byte via timing.

### Week 5 — RSA and Attacks
- B&S Ch. 3.1-3.2. RSA key generation and all attacks: small exponent, broadcast, common modulus, Bleichenbacher.
- Cryptopals Set 6 (challenges 41-42): unpadded RSA recovery, RSA parity oracle, Bleichenbacher e=3 attack.
- Implement RSA-OAEP encryption/decryption. Verify against PKCS#1 v2.1 test vectors.

### Week 6 — Elliptic Curves and ECDH
- B&S 9.3. Implement point addition, doubling, scalar multiplication on secp256k1.
- Implement ECDH key exchange. Verify shared secret.
- Cryptopals Set 5 (challenges 33-40): DH, MITM attack, malicious g-value.
- Cryptopals Set 8 (challenge 59): invalid curve attack on ECDH.

### Week 7 — Digital Signatures
- B&S Ch. 7. ECDSA implementation. ECDSA nonce reuse attack: given two signatures with same nonce k, recover k and private key.
- Cryptopals Set 6 (challenges 43-44): DSA nonce recovery.

### Week 8 — TLS 1.3 and Signal Protocol
- RFC 8446 full read. Trace a TLS 1.3 handshake in Wireshark with SSLKEYLOGFILE.
- Implement Signal Protocol's X3DH key agreement from scratch.
- Double Ratchet: implement symmetric ratchet (chain key + message key via HKDF) and DH ratchet step.

### Week 9 — Post-Quantum Cryptography
- B&S Ch. 15. LWE problem. Implement basic LWE encryption (Regev's scheme) for small parameters.
- Study CRYSTALS-Kyber specification. Understand Module-LWE; implement key generation for toy parameters.

### Week 10 — Protocol Attacks
- Bleichenbacher 1998 paper. Implement the adaptive chosen-ciphertext attack: PKCS#1 v1.5 oracle recovering plaintext.
- Lucky 13 attack (Al Fardan & Paterson, 2013) — timing attack against TLS CBC decryption.

### Weeks 11-12 — Cryptopals Sets 7-8, Audit Capstone, Milestone
- Complete Cryptopals Sets 7-8.
- Audit an open-source cryptographic library (mbedTLS or WolfSSL). Identify deviations from secure coding practices.
- Milestone assessment.

---

## Part C: Graded Problem Sets

### Tier 1 — Foundational

**Problem 1.** Prove that the one-time pad achieves perfect secrecy. Then prove Shannon's theorem: perfect secrecy requires |K| >= |M|.

**Problem 2.** The following Python code uses AES-CBC. Identify every cryptographic mistake and explain the attack each enables:
```python
key = b"mysecretpassword"   # 16 bytes
iv  = b"\x00" * 16          # fixed IV
cipher = AES.new(key, AES.MODE_CBC, iv)
ct = cipher.encrypt(pad(plaintext, 16))
```

**Problem 3.** Implement the CBC padding oracle attack. Given: an AES-CBC ciphertext and a decryption oracle that returns True if PKCS#7 padding is valid, decrypt the entire ciphertext one byte at a time. Demonstrate on a 48-byte ciphertext.

**Problem 4.** Explain the AES-GCM nonce reuse attack. If two messages m1 and m2 are encrypted with the same key and nonce, what does an attacker learn? Write the equations showing keystream recovery and authentication key recovery.

**Problem 5.** RSA broadcast attack: three recipients have (n1, e=3), (n2, e=3), (n3, e=3). The same message m is encrypted as ci = m^e mod ni. Implement the CRT-based attack to recover m. Test on a 128-bit message.

**Problem 6.** ECDSA nonce reuse: given (r, s1) on message hash h1 and (r, s2) on h2 (same r = same nonce k), derive the formulas to recover k and private key d. Implement the recovery.

**Problem 7.** Implement HMAC-SHA256 from scratch. Then implement the length extension attack against H(secret || message). Show you can compute H(secret || message || padding || extension) knowing only H(secret || message) and len(secret).

**Problem 8.** Trace the TLS 1.3 handshake key schedule step by step. Given the DH shared secret Z, compute Early Secret, Handshake Secret, and Master Secret using HKDF-Extract and HKDF-Expand. Show which keys derive for client/server handshake traffic and client/server application traffic.

**Problem 9.** Explain the Dual EC DRBG backdoor. What mathematical relationship between P and Q allows the holder to predict PRNG output? How was it discovered? What does this imply about trusting standardized algorithms?

**Problem 10.** Implement Diffie-Hellman key exchange in a prime-order group. Then implement the small subgroup attack: send a crafted public key that forces the shared secret into a small subgroup, leaking bits of the private key. Explain how Curve25519 prevents this.

---

### Tier 2 — Intermediate

**Problem 1.** Implement the complete Bleichenbacher 1998 PKCS#1 v1.5 RSA CCA attack. Given an oracle returning whether the first two plaintext bytes are 0x00 0x02, recover an encrypted 128-byte message. Count oracle queries.

**Problem 2.** Implement a complete certificate chain validator in Python: parse an X.509 certificate (DER), verify the signature on each certificate using the issuer's public key, check validity periods, and check the leaf certificate CN/SAN against a hostname. Handle self-signed roots, intermediate CAs, and expired certs.

**Problem 3.** Implement the Signal Protocol's Double Ratchet from scratch. Support X3DH initial key establishment, symmetric ratchet, DH ratchet, out-of-order message handling. Verify that compromise of a session key does not compromise past or future keys.

**Problem 4.** Lucky 13: implement the timing attack against AES-CBC-HMAC-SHA1. The oracle leaks one bit of timing: whether padding failed before or after MAC check. Decrypt one byte using the Vaudenay-style oracle.

---

### Tier 3 — Advanced

**Problem 1.** Prove the security of HMAC in the random oracle model: given a PRF-secure compression function, HMAC achieves EUF-CMA. Follow the proof in Bellare (2006). Identify the key steps.

**Problem 2.** Implement a chosen-ciphertext attack on ElGamal exploiting malleability: given ciphertext (c1, c2) encrypting m, produce a valid ciphertext for 2m without knowing m or the secret key. Verify by decrypting both.

**Problem 3.** (Capstone) Audit the WolfSSL TLS 1.3 implementation: verify the key schedule matches RFC 8446 §7.1; check for timing side-channels in HMAC comparison; verify certificate validation against CT logs. Write a professional audit report.

---

---

# MODULE 4.2 — Network Security & Protocol Attacks

**Duration:** 10–12 weeks | **Hours/week:** 12 | **Total hours:** ~135

---

## Part A: Chapter-by-Chapter Reading List

### Primary Text: Forshaw — *Attacking Network Protocols* (No Starch Press)

**Chapter 1** — Networking basics from attacker perspective.
**Chapter 2** — Capturing traffic: Wireshark, tshark, tcpdump, libpcap, AF_PACKET raw sockets, promiscuous mode, monitor mode.
**Chapter 3** — Protocol dissection methodology; identifying protocol boundaries; correlating captures with source or binary.
**Chapter 4** — HTTP proxying with Burp Suite; binary protocol analysis; custom protocol grammar recovery.
**Chapter 5** — Root causes of network vulnerabilities: authentication failures, insufficient encryption, injection, state machine bugs, replay attacks.
**Chapter 6** — Protocol fuzzing: generation-based vs mutation-based; coverage-guided fuzzing for network targets.

### Required Reading: Papers and RFCs
- RFC 8446 (TLS 1.3) — focus on §6 (Alert Protocol), §9 (Compliance), Appendix C (Implementation Notes).
- RFC 4301 (IPsec Architecture) — §4 (Security Associations), §5 (IP Traffic Processing).
- RFC 1035 (DNS) — §3 (Domain Name Space), §4 (Messages).
- DNSSEC: RFC 4033-4035 — trust anchor model, NSEC records, RRSIG.
- Kaminsky, "It's the End of the Internet As We Know It" (2008 DNS poisoning talk).
- IETF RPKI documentation on BGP route origin validation.

---

## Part B: Week-by-Week Study Schedule

### Week 1 — Packet Capture and Protocol Analysis
- Set up: Wireshark, tshark, Scapy, Burp Suite.
- Capture and fully annotate: a TLS 1.3 handshake (with SSLKEYLOGFILE), a full DNS resolution chain, an ARP exchange, an HTTP/2 negotiation.
- Write Scapy scripts to: craft an ICMP ping, send a raw TCP SYN, forge an ARP reply.

### Week 2 — Layer 2 and Layer 3 Attacks
- ARP cache poisoning: implement with Scapy. Two-VM lab. Verify MITM position with Wireshark.
- Dynamic ARP inspection (DAI): implement in software — monitor ARP traffic, alert on unsolicited replies.
- ICMP redirect attack: forge an ICMP redirect to change victim's routing table entry.

### Week 3 — DNS Attacks
- Kaminsky attack: implement DNS cache poisoning against a lab bind9 resolver. Flood with forged responses during outstanding query.
- DNS rebinding: implement attack bypassing Same-Origin Policy. Hostname initially resolves to attacker IP, then to internal IP.
- DNSSEC validation: implement a validator checking RRSIG signatures using the trust anchor.

### Week 4 — TLS Attacks
- SSL stripping: implement a proxy that downgrades HTTPS to HTTP. Observe HSTS as defense.
- Certificate validation testing: use openssl s_client to test chains. Write tool checking: expired cert, wrong hostname, self-signed cert, weak signature algorithm.
- TLS fingerprinting: implement JA3 fingerprinting — hash TLS ClientHello fields to identify TLS library and version.

### Week 5 — Wireless Attacks
- WPA2 4-way handshake capture: airmon-ng + airodump-ng on a dedicated lab WiFi network.
- Offline cracking: hashcat mode 22000 (WPA-PBKDF2-PMKID) for weak passphrase.
- PMKID attack: hcxdumptool to capture PMKID without a connected client.
- Evil twin AP: rogue access point with hostapd mimicking a target SSID.

### Week 6 — Protocol Fuzzing
- Mutation-based fuzzer: mutate valid packet captures, send to target, monitor for crashes.
- Generation-based fuzzer: use a protocol grammar. Target: FTP or SMTP server.
- AFL++ network fuzzing setup.

### Week 7 — BGP and Routing Security
- BGP hijacking: reproduce 2008 YouTube incident in GNS3 (3-AS topology). Advertise more-specific prefix; observe traffic redirection.
- RPKI: implement route origin validation using routinator. Verify invalid origins are rejected.

### Weeks 8-10 — IDS and Capstone
- Suricata rule writing: 20 rules (port scan, DNS tunneling, ARP spoofing, HTTP SQLi).
- Network monitoring pipeline: Suricata -> JSON -> Elasticsearch -> Kibana.
- Capstone: ARP poisoning MITM tool, DNS poisoning demo, network monitoring pipeline.
- Milestone assessment.

---

## Part C: Graded Problem Sets

### Tier 1 — Foundational

**Problem 1.** Implement an ARP cache poisoning tool in Python using Scapy: send gratuitous ARP replies to victim and gateway at 1-second intervals; enable IP forwarding; restore original ARP entries on exit. Verify MITM by capturing HTTP traffic.

**Problem 2.** Explain the Kaminsky DNS cache poisoning attack step by step: what the attacker sends; why the birthday paradox applies (Transaction ID + source port = 32 bits of entropy); how a successful poisoning is confirmed; what DNSSEC prevents.

**Problem 3.** Write a Suricata rule detecting DNS queries for DGA-generated domains: longer than 20 characters, no real English words (entropy heuristic), ending in .com or .net. Explain its limitations and evasion techniques.

**Problem 4.** Capture a TLS 1.3 handshake. Using SSLKEYLOGFILE, decrypt it in Wireshark. Identify: the client's key share, server's key share, derived handshake keys, application data keys. Explain why decrypting TLS 1.3 without the key log is infeasible.

**Problem 5.** Implement a network port scanner using raw sockets: SYN scanning, service banner grabbing, CIDR range targets, 100 concurrent probes, JSON output.

---

### Tier 2 — Intermediate

**Problem 1.** Implement a DNS tunneling tool: encode data as DNS queries (base32 subdomains of a controlled domain); server-side decoder; bidirectional channel. Measure throughput. Write a Suricata rule detecting this implementation.

**Problem 2.** Implement a TLS certificate transparency log monitor: query CRT.SH for all certificates for a target domain in the last 24 hours. Alert on: unexpected CAs, wildcard certificates, unexpected SANs.

**Problem 3.** Implement a BGP hijacking simulation in GNS3 with 3 ASes. AS300 advertises a more-specific prefix for AS100's subnet. Observe traffic redirection from AS200. Implement RPKI validation to prevent it.

---

---

# MODULE 4.3 — Web Security & Application Exploitation

**Duration:** 10–12 weeks | **Hours/week:** 12 | **Total hours:** ~135

---

## Part A: Chapter-by-Chapter Reading List

### Primary Text: Stuttard & Pinto — *The Web Application Hacker's Handbook*, 2nd ed.

**Ch. 1** — Web application attack surface; HTTP request/response from attacker perspective; browser security model.
**Ch. 2** — Core defense mechanisms: authentication, session management, access control failures; allowlist vs denylist.
**Ch. 3** — Web technologies: HTTP, frameworks, server-side scripting, client-side JS execution model.
**Ch. 4** — Mapping the application: content discovery (directory brute-forcing, robots.txt, GitHub dorking); technology fingerprinting.
**Ch. 5** — Bypassing client-side controls: intercepting with Burp Suite; hidden form fields; JavaScript obfuscation.
**Ch. 6** — Authentication attacks: brute force (rate limiting bypass); username enumeration via timing; password reset flaws; MFA bypass; credential stuffing.
**Ch. 7** — Session management: JWT attacks; session fixation; CSRF; SameSite cookie attribute.
**Ch. 8** — Access control: IDOR; horizontal vs vertical privilege escalation; forced browsing; mass assignment.
**Ch. 9** — SQL injection: in-band (UNION-based), error-based, blind (boolean-based, time-based), out-of-band; second-order SQLi; NoSQL injection.
**Ch. 10** — Back-end components: OS command injection; path traversal; LFI -> RCE via log poisoning; SSRF to cloud metadata.
**Ch. 11** — Application logic: race conditions (bypass single-use token); numeric edge cases; workflow bypass.
**Ch. 12** — XSS: reflected, stored, DOM-based; CSP and bypass techniques; payload toolkit (cookie theft, keylogger, BeEF).
**Ch. 13** — Other user attacks: clickjacking; CSRF; open redirect; CRLF injection; web cache poisoning.

### Required: PortSwigger Web Security Academy (portswigger.net)
**Complete all labs in:** SQL Injection (18), Authentication (14), Path Traversal (6), Command Injection (5), Business Logic (12), Access Control (13), File Upload (7), SSRF (7), XXE (9), XSS (30), CSRF (8), CORS (4), Insecure Deserialization (10), SSTI (7), Web Cache Poisoning (13), HTTP Host Header (7), OAuth 2.0 (6), JWT (8), HTTP/2 request smuggling (12), GraphQL (5).

### Required: OWASP Testing Guide v4.2
Use as a systematic methodology reference alongside PortSwigger labs.

---

## Part B: Week-by-Week Study Schedule

### Weeks 1-2 — SQL Injection and Authentication
- WAHH Ch. 9 (SQLi). All PortSwigger SQLi labs. Implement a SQLi scanner detecting boolean-based blind SQLi.
- WAHH Ch. 6. All PortSwigger authentication labs.

### Weeks 3-4 — XSS and CSRF
- WAHH Ch. 12-13. All 30 PortSwigger XSS labs. Build stored XSS payload: steal cookies, capture keystrokes, exfiltrate via DNS or HTTP.
- CSP bypass lab: given CSP "default-src 'self'", find bypass using same-origin JSONP endpoint.
- All PortSwigger CSRF labs.

### Weeks 5-6 — SSRF, XXE, and Deserialization
- WAHH Ch. 10. All PortSwigger SSRF and XXE labs.
- SSRF chain: SSRF -> AWS metadata (169.254.169.254) -> IMDSv1 credential exfiltration -> S3 access.
- Java deserialization: ysoserial gadget chain payload -> RCE.

### Weeks 7-8 — JWT, OAuth, and Template Injection
- All PortSwigger JWT and OAuth labs. JWT: alg:none attack, RS256->HS256 confusion, weak HMAC secret cracking.
- SSTI: identify template engine from errors; exploit Jinja2 SSTI to RCE via __import__('os').system('id').

### Week 9 — HTTP Request Smuggling
- All PortSwigger HTTP request smuggling labs. Implement CL.TE and TE.CL smuggling manually (no Burp extensions).

### Week 10 — Cache Poisoning and Advanced
- All PortSwigger cache poisoning labs. Host header injection, unkeyed params, fat GET.
- GraphQL: introspection enumeration, IDOR, batch query DoS.
- Build a Burp Suite extension (Python, MontoyaAPI) that auto-detects reflected parameters and tests for XSS.

### Weeks 11-12 — CTF Practice and Milestone
- HackTheBox web challenges: complete 20 web machines.
- Build the automated SQLi detection tool.
- Milestone assessment.

---

## Part C: Graded Problem Sets

### Tier 1 — Foundational

**Problem 1.** Given vulnerable login query: SELECT * FROM users WHERE username='$user' AND password='$pass'. Write 5 different SQLi payloads bypassing authentication. Then write the parameterized query equivalent in Python (sqlite3) immune to all 5. Explain the mechanism.

**Problem 2.** Implement time-based blind SQL injection extracting a users table (id, username, password_hash) from a target returning only boolean responses. Extract one character at a time using binary search.

**Problem 3.** Design a stored XSS payload that: steals all cookies; sends to attacker server via hidden image request; bypasses CSP "default-src 'self'; script-src 'self' https://cdn.example.com". Identify what additional directive prevents exfiltration.

**Problem 4.** Explain JWT attacks. Show the crafted token for: (a) alg:none; (b) RS256->HS256 confusion with hardcoded public key; (c) crack a weak HS256 secret using hashcat mode 16500.

**Problem 5.** SSRF to RCE chain: web app makes requests to ?url= parameter; server runs on EC2. Describe: (a) probe internal network; (b) access IMDSv1; (c) extract IAM credentials; (d) call AWS APIs. Write payloads for each step.

**Problem 6.** Implement a Burp Suite extension that: intercepts all responses; extracts all parameter names; sends reflected XSS probe for each; flags responses reflecting the probe unencoded.

**Problem 7.** Explain HTTP request smuggling. Given a frontend using Content-Length and backend using Transfer-Encoding: chunked, demonstrate a CL.TE attack that poisons the request queue to capture another user's Cookie header.

**Problem 8.** SSTI: identify the template engine from error output showing "jinja2.exceptions.TemplateSyntaxError". Write the payload executing 'id' on the server and returning output in the response.

---

### Tier 2 — Intermediate

**Problem 1.** Implement an OAuth 2.0 authorization code flow attack: exploit an open redirect in redirect_uri to steal the authorization code; exchange it for an access token; call the API as the victim. Document each step with HTTP requests/responses.

**Problem 2.** Implement a web cache poisoning attack: identify an unkeyed HTTP header (e.g., X-Forwarded-Host) that is reflected in the response; poison the cache so subsequent users receive a response reflecting your attacker-controlled header; use this to inject a malicious script tag into the cached response.

**Problem 3.** Prototype pollution: given a JavaScript application that merges user-supplied JSON into an object using deep merge without sanitization, demonstrate: (a) polluting Object.prototype.isAdmin = true to bypass an authorization check; (b) polluting Object.prototype.outputFunctionName to achieve RCE in a server-side Node.js application using pug templating.

---

---

# MODULE 4.4 — Reverse Engineering

**Duration:** 12–14 weeks | **Hours/week:** 15 | **Total hours:** ~195

---

## Part A: Chapter-by-Chapter Reading List

### Primary Text: Sikorski & Honig — *Practical Malware Analysis* (No Starch Press)

**Ch. 1 — Basic Static Analysis:** hashing (MD5, SHA-256, imphash, ssdeep); string extraction; packer detection; import analysis; PE file format (DOS header, PE header, sections, import/export tables, resources).

**Ch. 2 — Malware Analysis in VMs:** snapshot workflow; INetSim/FakeNet-NG; process isolation; evading sandbox detection.

**Ch. 3 — Basic Dynamic Analysis:** Process Monitor (ProcMon); Process Hacker; Regshot (registry snapshot diffing); Wireshark; ApateDNS/INetSim.

**Ch. 4 — x86 Disassembly Crash Course:** Review Module 3.2. Focus on RE perspective.

**Ch. 5 — IDA Pro:** IDA workflow: auto-analysis, function identification, cross-references (xrefs), renaming, commenting; graph view vs linear view; FLIRT signatures; IDAPython scripting; Hex-Rays decompiler.

**Ch. 6 — Recognizing C Code Constructs in Assembly (critical pattern recognition):**
- if/else: cmp followed by jcc; branching structure.
- for/while loops: counter init, condition at top, body, increment, back-edge jump.
- do-while: body first, condition at bottom, single back-edge jump.
- switch/case: jump tables (jmp [rax*8 + table_base]); compare chains for sparse switch.
- Function calls: argument setup in registers, call instruction, accessing args from callee.
- Arrays: base + index*stride addressing.
- Structs: base pointer + constant offsets for field access.
- Linked lists: following pointer at fixed offset to reach next node.
- C++ objects: this pointer as first argument; vtable pointer at offset 0; virtual dispatch via [vtable + offset].

**Ch. 7 — Analyzing Malicious Windows Programs:** Windows API families: file ops (CreateFile, ReadFile, WriteFile); process injection (OpenProcess, VirtualAllocEx, WriteProcessMemory, CreateRemoteThread); registry (RegOpenKey, RegSetValue); network (WSAStartup, socket, connect); LoadLibrary/GetProcAddress to hide imports.

**Ch. 8 — Debugging:** OllyDbg/x64dbg workflow; hardware breakpoints; conditional breakpoints; anti-debugging defeat: IsDebuggerPresent (patch return); timing checks (GetTickCount, rdtsc); exception-based anti-debugging.

**Ch. 10 — Kernel Debugging with WinDbg:** KDNET setup; !process, !thread, dt, !pte, bp/ba; kernel module listing.

**Ch. 11 — Malware Behavior:** persistence (registry run keys, scheduled tasks, services, WMI event subscriptions); privilege escalation; defense evasion; lateral movement; C2 communication.

**Ch. 12 — Covert Malware Launching:** DLL injection (CreateRemoteThread + LoadLibrary); reflective DLL injection; process hollowing (create suspended process, unmap, map malicious PE); early bird injection (queue APC before thread starts).

**Ch. 13 — Data Encoding:** XOR encoding (single-byte, multi-byte key); base64; stack string obfuscation; RC4 key schedule and PRGA (recognize for malware decryption).

**Ch. 14 — Network Signatures:** HTTP User-Agent anomalies; beaconing patterns; hardcoded C2 indicators; DGA patterns (high-entropy domains predictable from seed and date).

**Ch. 15 — Anti-Disassembly:** rogue bytes after conditional jump; overlapping instructions; function pointer obfuscation; jump-to-register obfuscation.

**Ch. 16 — Anti-Debugging:** RDTSC timing; NtQueryInformationProcess (ProcessDebugPort); OutputDebugString error code; Parent PID check; heap flag checks.

**Ch. 17 — Anti-VM Tricks:** CPUID hypervisor bit; VMware/VirtualBox registry artifacts; time-based VM detection; WMI-based VM detection (BIOS version, system manufacturer); mouse movement detection.

**Ch. 18 — Packers and Unpacking:** packer stub patterns; OEP finding via ESP trick; IAT reconstruction after dump; manual unpacking workflow in x64dbg.

---

### Supplementary Texts
- Dang, Gazet & Bachaalany — *The IDA Pro Book*, 2nd ed. (Ch. 1-2, 8, 13: IDAPython automation)
- Eagle — *The Ghidra Book* (Ch. 1, 5, 9, 12)
- **FLARE-ON Challenges (fireeye.com)** — solve last 3 years; these are the gold standard RE CTF challenges

---

## Part B: Week-by-Week Study Schedule

### Week 1 — Static Analysis Fundamentals
- Set up: Ghidra, x64dbg (Windows VM), Binary Ninja trial or IDA Free. REMnux Linux.
- Static analysis of 3 binaries: file, strings, objdump, readelf, Ghidra auto-analysis.
- PE format: write a Python PE parser printing DOS header, PE header, section headers, import table, export table.

### Week 2 — Dynamic Analysis
- Set up: FlareVM, INetSim, FakeNet-NG, ProcMon, Process Hacker.
- Dynamic analysis of 3 benign programs: correlate ProcMon events with Ghidra disassembly.
- Crackme series: crackmes.one — solve 10 crackmes of increasing difficulty.

### Week 3 — Assembly Pattern Recognition
- PMA Ch. 6. Annotate 20 compiler-generated functions: identify all C constructs.
- Decompiler comparison: same function in Ghidra vs IDA Hex-Rays vs Binary Ninja HLIL.
- C++ RE: recover a class hierarchy from a binary with vtables.

### Week 4 — Anti-Analysis Techniques
- PMA Ch. 15-17. Implement each anti-analysis technique in a test binary, then defeat each.
- Anti-debugging: patch IsDebuggerPresent via x64dbg script. Defeat RDTSC timing via ScyllaHide.
- VM detection: set VM vendor strings to match a real machine.

### Week 5 — Packing and Unpacking
- PMA Ch. 18. Manual unpacking: UPX-packed binary (trivial), custom packer (harder).
- IAT reconstruction: Scylla to rebuild import table after dump.
- Python script to detect packing by measuring section entropy (> 7.0 bits/byte = likely packed).

### Week 6 — Windows Internals for RE
- PMA Ch. 7. Windows API internals; PEB structure in memory; InLoadOrderModuleList for loaded modules.
- Write assembly finding kernel32.dll base via PEB walk (classic shellcode technique).
- PE loading: trace LoadLibrary -> MapViewOfSection -> relocation -> TLS callbacks -> DllMain.

### Week 7 — Protocol Reverse Engineering
- Capture network traffic from a binary with custom binary protocol. Identify message boundaries, field types, state machine from traffic alone.
- Cross-correlate with Ghidra analysis of the network receive function to confirm protocol model.

### Week 8 — ARM and .NET RE
- ARM: analyze an Android APK — extract classes.dex with apktool, decompile with jadx.
- .NET: analyze a .NET binary with dnSpy. Modify a string literal and recompile (patch).
- Write Ghidra script that auto-renames functions with a specific prefix.

### Weeks 9-12 — FLARE-ON Challenges and Capstone
- FLARE-ON 2022 or 2023: solve challenges 1-8 minimum.
- Capstone: reverse engineer a real-world open-source stripped binary. Produce a professional analysis report: all functions documented, data structures defined, protocol specification, vulnerabilities identified.
- Milestone assessment.

---

## Part C: Graded Problem Sets

### Tier 1 — Foundational

**Problem 1.** Analyze the following x86-64 assembly. Reconstruct the C source. Identify all local variables, their types, and the function's purpose:
```asm
<func>:
  push   rbp
  mov    rbp, rsp
  sub    rsp, 0x20
  mov    DWORD PTR [rbp-0x14], edi
  mov    DWORD PTR [rbp-0x18], esi
  mov    DWORD PTR [rbp-0x4], 0x0
  jmp    .cond
.loop:
  mov    eax, DWORD PTR [rbp-0x18]
  mov    edx, DWORD PTR [rbp-0x4]
  imul   eax, edx
  add    DWORD PTR [rbp-0x14], eax
  add    DWORD PTR [rbp-0x4], 0x1
.cond:
  mov    eax, DWORD PTR [rbp-0x4]
  cmp    eax, DWORD PTR [rbp-0x18]
  jl     .loop
  mov    eax, DWORD PTR [rbp-0x14]
  leave
  ret
```

**Problem 2.** A binary uses this PEB walk to find kernel32.dll base. Annotate each instruction and explain what it accesses in the PEB/TEB/LDR_DATA_TABLE_ENTRY structures:
```asm
mov rax, gs:[0x60]
mov rax, [rax + 0x18]
mov rax, [rax + 0x20]
mov rax, [rax]
mov rax, [rax]
mov rax, [rax + 0x20]
```

**Problem 3.** Identify the anti-debugging technique in the following code and explain how to defeat it in x64dbg:
```c
DWORD t1 = GetTickCount();
do_nothing_loop(1000000);
DWORD t2 = GetTickCount();
if (t2 - t1 > 1000) ExitProcess(0);
```

**Problem 4.** A malware sample encodes its C2 domain with XOR key 0x41. Encoded bytes: 0x26, 0x28, 0x2E, 0x2B, 0x2A, 0x55, 0x24, 0x2A, 0x28, 0x30. Decode the domain. Write a YARA rule matching these specific encoded bytes.

**Problem 5.** Write a Ghidra Python script that: iterates over all functions; identifies functions calling GetProcAddress; for each, lists the string arguments passed to it. This identifies dynamically resolved APIs — a key malware analysis task.

---

### Tier 2 — Intermediate

**Problem 1.** Manually unpack a UPX-packed binary using x64dbg: identify the packer stub; set hardware breakpoint on ESP after stack pivot; run to OEP; dump unpacked binary; reconstruct import table using Scylla. Verify functional equivalence.

**Problem 2.** Reverse engineer a binary implementing a custom RC4-like stream cipher: identify KSA, identify PRGA, extract hardcoded key, decrypt an embedded encrypted string. Produce the decryption tool in Python.

**Problem 3.** Identify and document 5 distinct anti-VM checks in a provided malware sample. For each: explain the detection mechanism, the artifact being checked, and how to defeat it (in the VM or by patching the binary).

---

---

# MODULE 4.5 — Exploit Development & Vulnerability Research

**Duration:** 14–16 weeks | **Hours/week:** 15+ | **Total hours:** ~230

---

## Part A: Reading List

### Primary: pwn.college (pwn.college) — Complete Dojo
Complete all modules in order: Program Misuse, Assembly Crash Course, Debugging Refresher, Computer Architecture, Reverse Engineering, Memory Errors, Shellcoding, Sandboxing, ROP, Heap Exploitation, Kernel Exploitation.

### Primary: Erickson — *Hacking: The Art of Exploitation*, 2nd ed.
**Ch. 3 — Exploitation:** Buffer overflow step by step; format string exploitation (%n write primitive); heap overflows.
**Ch. 5 — Shellcode:** syscall shellcode; socket shellcode; encoded shellcode; polymorphic shellcode.

### Supplementary
- Nightmare Binary Exploitation Course (guyinatuxedo.github.io) — complete all challenges.
- Aleph One, "Smashing The Stack For Fun And Profit" (Phrack #49, 1996) — original stack overflow paper.
- Roemer et al., "Return-Oriented Programming: Systems, Languages, and Applications" (CCS 2012).
- Phrack Magazine: #64 articles on Linux kernel exploitation and heap spray.

---

## Part B: Week-by-Week Study Schedule

### Week 1 — Stack Fundamentals
- Set up: Ubuntu 22.04 VM, pwntools, pwndbg, ROPgadget, ropper, one_gadget, checksec.
- checksec: understand each mitigation (NX, CANARY, RELRO, PIE, ASLR) and what it prevents.
- Classic stack buffer overflow: all mitigations disabled. Exploit — control rip, execute shellcode on stack.

### Week 2 — Shellcode Under Constraints
- pwn.college Shellcoding module (all levels).
- Write shellcode that is: (a) null-byte free; (b) alphanumeric only; (c) under seccomp orw; (d) <=25 bytes.
- XOR-encode shellcode, prepend decoder stub.

### Week 3 — Stack Canary and NX Bypass
- Stack canary bypass: brute force on fork() server; info leak via format string; partial overwrite.
- NX bypass: ret2libc — return to system() with /bin/sh argument. Find libc addresses without ASLR.

### Week 4 — ASLR and PIE Bypass
- ASLR bypass: info leak (read a libc address, compute base); brute force (32-bit only); partial overwrite.
- PIE bypass: info leak to determine binary load address; relative offsets from leaked address.

### Week 5 — Return Oriented Programming
- pwn.college ROP module (all levels).
- Build ROP chains: call system("/bin/sh") via gadgets; execve via syscall gadgets; open bind shell.
- ret2plt: call puts@plt to leak libc address; compute libc base; ret2libc.
- SROP: use a single syscall; ret gadget + sigreturn to set all registers via fake sigcontext frame.

### Week 6 — Format String Exploitation
- Format string read: leak stack values (%p.%p.%p...), leak canary, leak return address.
- Format string write: overwrite return address using multiple %n writes with positional parameters.
- fmt_write4 / fmt_write8: write 4-byte or 8-byte value to arbitrary address using short writes.

### Week 7 — Heap Exploitation: Fundamentals
- ptmalloc internals: chunk header (prev_size, size, fd, bk); bin types (fast bins, unsorted bin, tcache); chunk flags.
- pwn.college Heap module (all levels).
- Tcache poisoning: double-free with tcache; control fd pointer; allocate chunk at arbitrary address.

### Week 8 — Heap Exploitation: Advanced
- House of Spirit: forge fake chunk in controllable buffer; free it; allocate it overlapping a target.
- Unsorted bin attack: corrupt bk; trigger malloc to write large libc address to arbitrary location.
- Safe-linking bypass: tcache XOR-mangling (ptr ^ (stored_addr >> 12)); leak heap address; bypass.
- Fastbin dup: allocate A, free A, free B, free A; modify fd; allocate to get chunk at target.

### Week 9 — Multi-Mitigation Exploit
- Given binary with NX + CANARY + FULL RELRO + PIE + ASLR: format string leak (canary, PIE base, libc base) -> ROP chain to execve("/bin/sh").
- GOT overwrite under Partial RELRO: overwrite GOT entry with system address.

### Week 10 — Kernel Exploitation
- Setup: QEMU-based kernel debug environment.
- pwn.college Kernel module (all levels).
- Kernel LPE via stack overflow: overflow kernel stack buffer; overwrite return address; execute commit_creds(prepare_kernel_cred(0)).
- ret2usr: execute user-space shellcode from kernel context (SMEP disabled).
- KASLR bypass: info leak to determine kernel base address.
- modprobe_path overwrite: overwrite modprobe_path to point to attacker script; trigger via unknown magic number binary.

### Week 11 — CVE Exploitation
- Select a real CVE from last 3 years (kernel LPE or user-space heap UAF). Read the patch. Reconstruct vulnerability from diff. Write an N-day exploit.
- Write a fuzzer using AFL++; triage crashes with ASan.

### Weeks 12-14 — CTF, Capstone, and Milestone
- CTF: participate in a real CTF; solve at least 3 pwn challenges.
- Capstone: discover or exploit a real CVE; write a full disclosure advisory.
- Milestone assessment.

---

## Part C: Graded Problem Sets

### Tier 1 — Foundational

**Problem 1.** Explain at the assembly level what happens when a buffer overflow overwrites the return address. Draw the stack frame before and after. Which mitigation prevents which exploit class?

**Problem 2.** Given a binary compiled with -fno-stack-protector -no-pie -z execstack, write a complete pwntools exploit: identify offset to rip via cyclic pattern; place shellcode in buffer; overwrite return address; spawn a shell.

**Problem 3.** Implement a format string exploit: (a) leak stack canary via %p; (b) leak a return address to bypass PIE; (c) overwrite return address with one-gadget libc address. Write the pwntools exploit script.

**Problem 4.** Explain tcache poisoning step by step: (a) tcache structure; (b) how double-free creates a corrupted entry; (c) how safe-linking protects against this in glibc >= 2.32; (d) how safe-linking is bypassed with a heap address leak.

**Problem 5.** Write a ROP chain calling execve("/bin/sh", NULL, NULL) using only gadgets from binary and libc: set rdi = address of "/bin/sh" in libc; rsi = 0; rdx = 0; rax = 59; execute syscall. Use ROPgadget to find gadgets. Write pwntools exploit.

**Problem 6.** Explain the kernel privilege escalation technique using commit_creds(prepare_kernel_cred(0)). What does each function do? What kernel data structure does it modify? Why does calling this from kernel context result in a root shell when returning to userspace?

**Problem 7.** KASLR bypass: explain how reading /proc/kallsyms leaks kernel base address (when permitted), and how a kernel info-leak vulnerability achieves the same without permissions. Given a leaked kernel address at offset 0x123456 from base, compute the kernel base.

---

### Tier 2 — Intermediate

**Problem 1.** Write a complete exploit for a heap use-after-free vulnerability: program allocates an object with a function pointer, frees it but retains the pointer, then calls the function pointer. Exploit to: redirect function pointer to system; pass "/bin/sh" as argument. Use tcache spraying to control freed memory.

**Problem 2.** Implement a kernel module with a deliberate stack buffer overflow. Write the kernel exploit that: loads the vulnerable module; triggers overflow from userspace; overwrites kernel return address; executes commit_creds(prepare_kernel_cred(0)) in kernel context; returns as root shell. Test in QEMU with SMEP disabled.

**Problem 3.** Write a coverage-guided fuzzer using AFL++ for a binary parsing a custom binary file format. Create a seed corpus of 10 valid files. Run AFL++ for 24 hours. Triage crashes with ASan. For the most interesting crash, write a minimal PoC. Determine if the crash is exploitable.

---

---

# MODULES 4.6 — 4.10 (Condensed Complete Form)

---

# MODULE 4.6 — Malware Analysis

**Duration:** 10–12 weeks | **Hours/week:** 12–15 | **Total hours:** ~150

## Part A: Key Reading

- **Sikorski & Honig** — PMA (advanced chapters 10-12, 19-21 re-read with deeper context)
- **MITRE ATT&CK Framework** (attack.mitre.org) — Enterprise matrix; map every malware behavior to ATT&CK ID
- **MalwareBazaar** (bazaar.abuse.ch) — download and analyze 10 real samples
- **Didier Stevens' Blog** (blog.didierstevens.com) — oledump.py, pdf-tools, rtfdump.py, XORSearch.py

## Part B: Weekly Schedule

**Weeks 1-2:** Set up FlareVM, REMnux, Cuckoo/CAPE sandbox. Triage 5 samples (hash, strings, entropy, packer detection, import analysis). Static analysis of Emotet or similar loader in Ghidra. Write YARA rule.

**Week 3:** Dynamic analysis of 3 samples using ProcMon, Process Hacker, Wireshark, Regshot. Compare to ANY.RUN automated results.

**Week 4:** Advanced techniques: DLL injection detection (hook CreateRemoteThread); process hollowing detection (suspicious section mappings); reflective DLL injection detection (PE headers in non-file-backed memory). Volatility analysis to detect process hollowing in a memory dump.

**Weeks 5-6:** Ransomware analysis (file enumeration, AES file encryption, RSA key management, ransom note). Banking trojan analysis (TrickBot or Dridex: web injection, form grabbing, credential theft).

**Weeks 7-8:** C2 analysis: extract C2 configuration from 3 samples (Cobalt Strike beacon, Metasploit stager, custom RAT). DGA reverse engineering: implement DGA emulator in Python, predict domains for next 30 days. Cobalt Strike beacon config extraction: C2 URL, user agent, sleep time, jitter, public key.

**Weeks 9-10:** Detection engineering: 20 YARA rules across different families. 10 Sigma rules for SIEM detection. Write Volatility3 plugin scanning all processes for injected PE headers in non-file-backed memory.

**Weeks 11-12:** Analyze 5 MalwareBazaar samples from scratch. Produce professional analysis reports. Milestone assessment.

## Part C: Graded Problem Sets (Selected)

**Problem 1.** A malware sample creates HKCU\Software\Microsoft\Windows\CurrentVersion\Run\WindowsUpdater. (a) What ATT&CK technique is this? (b) Write a Sigma rule detecting this persistence mechanism. (c) Write the Volatility3 command to detect this in a memory image.

**Problem 2.** Describe the Cobalt Strike beacon communication model: (a) what is a beacon; (b) HTTP/HTTPS beaconing pattern, timing, jitter; (c) how C2 communication is encrypted; (d) how defenders detect Cobalt Strike (JA3 fingerprints, HTTP patterns, certificate anomalies).

**Problem 3.** Implement a DGA emulator: domain for day d of year y is computed as seed = (d * y * 31337) % 65536; domain = base36encode(seed) + ".com". Predict all domains for current year. Write a Suricata rule alerting on DNS queries for any predicted domain.

**Problem 4.** Walk through Volatility3 commands to: (a) list all processes; (b) find injected PE using malfind; (c) dump the injected PE from memory; (d) analyze the dump statically.

**Problem 5.** Write a YARA rule detecting the RC4 KSA in a binary — recognize the 256-byte S-box initialization loop pattern using byte sequence matching and structure constraints.

---

---

# MODULE 4.7 — Digital Forensics & Incident Response

**Duration:** 10–12 weeks | **Hours/week:** 12 | **Total hours:** ~130

## Part A: Key Reading

- **Ligh, Case, Levy & Walters** — *The Art of Memory Forensics* (Wiley): Ch. 1 (systems overview), Ch. 5 (Windows memory acquisition), Ch. 6 (processes and DLLs — EPROCESS, DKOM detection via pslist vs psscan), Ch. 9 (network artifacts), Ch. 16 (kernel forensics and rootkits — SSDT/IDT hook detection).
- **Carvey** — *Windows Forensic Analysis Toolkit*, 4th ed.: Ch. 2 (NTFS — MFT, MACE timestamps, ADS, VSS), Ch. 3 (registry artifacts — ShellBags, UserAssist, Amcache, Shimcache), Ch. 4 (Event Log analysis — key event IDs: 4624, 4625, 4688, 4698, 4720, 4732 and Sysmon IDs 1, 3, 7, 10, 11, 13), Ch. 5 (prefetch analysis — execution evidence), Ch. 6 (browser and user activity artifacts).
- **NIST SP 800-86** — *Guide to Integrating Forensic Techniques into Incident Response*: §4-7.
- **Volatility3 Documentation** (volatilityfoundation.org) — all Windows plugins.
- **MemLabs** (github.com/stuxnet999/MemLabs) — complete all 6 challenges.
- **SANS DFIR Blog** (digital-forensics.sans.org) — current artifact analysis techniques.

## Part B: Weekly Schedule

**Weeks 1-2:** Disk forensics setup (Autopsy, Sleuth Kit, FTK Imager). Acquire forensic image of VM disk; verify hash. NTFS analysis: fls, icat, fsstat — list deleted files, recover content, parse MFT records manually. Windows artifacts: ShellBags, prefetch, UserAssist, Amcache via RegRipper.

**Weeks 3-4:** Memory forensics — MemLabs (all 6). Volatility3 deep-dive. Detect DKOM rootkit: cross-reference pslist vs psscan. Extract credentials from LSASS. Extract network connections, injected DLLs, clipboard contents.

**Week 5:** Network forensics: analyze provided PCAP of multi-stage intrusion. Identify initial compromise, C2, lateral movement, data exfiltration. Zeek analysis: conn.log, dns.log, http.log, ssl.log, files.log.

**Week 6:** Log analysis: Windows Event Log via evtx_dump. Timeline: plaso (log2timeline) building super timeline; analyze in Timesketch. Sysmon deployment with SwiftOnSecurity config; analyze in Splunk or ELK.

**Weeks 7-8:** Full IR exercise: compromised VM image (disk + memory), reconstruct complete attack timeline. Document initial access, persistence, lateral movement, exfiltration. Write IR report. Apply NIST SP 800-61 process.

**Weeks 9-10:** IOC extraction from Module 4.6 malware analysis. Encode in STIX 2.1 format; share via TAXII server; import into MISP. Threat hunting in Sysmon data for ATT&CK techniques documented in Module 4.6.

**Weeks 11-12:** Full forensic case: NIST CFReDS project disk image. Produce professional forensic report. Milestone assessment.

## Part C: Graded Problem Sets (Selected)

**Problem 1.** Explain the difference between NTFS $STANDARD_INFORMATION and $FILE_NAME timestamps. Why can an attacker easily modify $STANDARD_INFORMATION (timestomping) but not $FILE_NAME? Write a Volatility3 command sequence detecting timestomping artifacts.

**Problem 2.** Volatility3 pslist shows 45 processes; psscan shows 47. Explain the discrepancy. What is DKOM? What forensic artifact (pool tag) does psscan use to find hidden processes?

**Problem 3.** Write the complete Volatility3 command sequence to: (a) identify all running processes; (b) find network connections and owning PIDs; (c) detect injected DLLs; (d) dump suspicious process memory; (e) extract strings from the dump.

**Problem 4.** Build a Super Timeline: use log2timeline.py to parse NTFS MFT, Windows Event Logs, Prefetch files, registry hives, browser history, LNK files, and jump lists from a Windows forensic disk image. Load into Timesketch. Document all artifacts for the 2-hour window around the suspected compromise time.

**Problem 5.** Write a Python script parsing Windows EVTX files extracting all Event ID 4688 (process creation) events. Output: timestamp, parent PID, parent process name, child PID, child process name, command line. Flag cmd.exe or powershell.exe spawned from winword.exe, excel.exe, or iexplore.exe.

---

---

# MODULE 4.8 — Penetration Testing & Red Team Operations

**Duration:** 10–12 weeks | **Hours/week:** 15+ | **Total hours:** ~165

## Part A: Key Reading

- **Weidman** — *Penetration Testing* (No Starch Press): methodology framework.
- **SpecterOps Research** (posts.specterops.io): AD attack paths, ADCS (ESC1-ESC8), BloodHound methodology.
- **Harmj0y's Blog** (harmj0y.net): Kerberoasting, AS-REP roasting, Pass-the-Hash, DCSync, Golden/Silver Tickets, ACL abuse.
- **HackTheBox Pro Labs**: complete Offshore or RastaLabs (mandatory).

## Part B: Weekly Schedule

**Week 1:** Recon and scanning. OSINT: theHarvester, Shodan, crt.sh, GitHub dorking, LinkedIn. Scanning: nmap, masscan, Nessus/OpenVAS.

**Week 2:** Active Directory enumeration. Set up Windows AD lab (Server 2019 eval, 2-3 joined workstations). BloodHound/SharpHound: collect all methods, import, find paths to Domain Admin. PowerView enumeration: users, groups, GPOs, trusts, SPNs, ACLs.

**Weeks 3-4:** AD attacks. Kerberoasting: GetUserSPNs.py; hashcat mode 13100. AS-REP roasting: enumerate no-preauth accounts; hashcat mode 18200. Pass-the-Hash: Mimikatz sekurlsa::logonpasswords; crackmapexec. DCSync: secretsdump.py with replication privileges. Golden Ticket: forge TGT using krbtgt hash. ADCS ESC1: certipy to request certificate for DA; PKINIT authentication.

**Week 5:** Defense evasion and C2. AMSI bypass: script-based (amsiInitFailed), memory patching. ETW unhooking: patch EtwEventWrite to return immediately. Process injection: shellcode injection via VirtualAllocEx + WriteProcessMemory + CreateRemoteThread; early bird APC injection. Sliver C2: set up server, generate MTLS implant, use post-exploitation modules.

**Week 6:** Post-exploitation and persistence. Credential harvesting: Mimikatz, secretsdump, LSASS dump. Persistence: scheduled tasks, WMI event subscriptions, DLL hijacking. Lateral movement: PsExec, WMI exec, WinRM (evil-winrm), DCOM.

**Weeks 7-10:** HackTheBox Pro Labs (Offshore or RastaLabs): complete full lab environment. Document every step in a detailed lab journal.

**Weeks 11-12:** Write a professional penetration test report for your AD lab campaign: executive summary, methodology, findings (CVSS scores), evidence, remediation recommendations. Milestone assessment.

## Part C: Graded Problem Sets (Selected)

**Problem 1.** Explain Kerberoasting: (a) what is an SPN; (b) what ticket does the attacker request and why it contains the service account's password hash; (c) why offline cracking is possible; (d) what defensive controls prevent or mitigate it?

**Problem 2.** ADCS ESC1 attack: (a) what makes a certificate template exploitable (CT_FLAG_ENROLLEE_SUPPLIES_SUBJECT + low-privilege enrollment rights); (b) what certipy commands request a certificate as domain admin; (c) how the certificate is used for authentication (PKINIT); (d) what is the defensive fix?

**Problem 3.** Design a red team operation plan for a fictional financial institution: (a) objectives (crown jewels: core banking system); (b) attack phases; (c) rules of engagement; (d) detection avoidance strategy; (e) success criteria.

**Problem 4.** Write a custom C2 implant in C: (a) connects to HTTPS server via WinINet; (b) beacons every 60 seconds with +-30 second jitter; (c) receives commands encoded in HTTP response body (base64 + AES-256 encrypted); (d) executes via CreateProcess and returns output; (e) exits cleanly on termination command.

---

---

# MODULE 4.9 — Cloud Security

**Duration:** 10–12 weeks | **Hours/week:** 12 | **Total hours:** ~130

## Part A: Key Reading

- **AWS Security Documentation** (docs.aws.amazon.com/security): IAM, SCP, VPC, KMS, CloudTrail, GuardDuty, Security Hub.
- **Rhino Security Labs Blog** (rhinosecuritylabs.com): AWS IAM privilege escalation, S3 misconfigurations, Lambda security.
- **CloudGoat** (github.com/RhinoSecurityLabs/cloudgoat): complete all scenarios.
- **KubeGoat** (github.com/ksoclabs/kubegoat): complete all Kubernetes scenarios.
- **flaws.cloud** and **flaws2.cloud**: complete both.
- **CIS Benchmarks for AWS/Azure/GCP** (cisecurity.org).
- **Kubernetes Security Documentation**: RBAC, Pod Security Standards, Network Policies, Secrets management.

## Part B: Weekly Schedule

**Weeks 1-2:** AWS IAM deep-dive: users, roles, policies, permission boundaries, SCPs, condition keys. IAM privilege escalation paths: PassRole, CreatePolicyVersion, sts:AssumeRole abuse, lambda:CreateFunction + lambda:InvokeFunction. Use cloudsplaining. Complete flaws.cloud (all 6 levels).

**Weeks 3-4:** CloudGoat all scenarios. SSRF to IMDSv1 chain: SSRF -> metadata endpoint -> IAM credential theft. CloudTrail evasion: understand unlogged API calls; detection avoidance while enumerating.

**Weeks 5-6:** Container and Kubernetes security. Docker: privileged container escape; Docker socket exposure; --cap-add SYS_ADMIN abuse. KubeGoat all scenarios. Kubernetes attack paths: anonymous API server; token theft; kubelet unauthenticated access; etcd exposure. Falco: deploy and write rules detecting shell spawned in container, privileged container creation, sensitive host path mounts.

**Weeks 7-8:** Defensive architecture: 3-tier AWS web app with defense-in-depth (VPC, NACLs, WAF, ALB, ECS Fargate, RDS encryption, Secrets Manager, KMS CMK, CloudTrail, GuardDuty, Security Hub, S3 Block Public Access). Write a CSPM tool using Boto3 checking 20 security controls.

**Weeks 9-10:** Serverless security: Lambda function policy vs execution role; event injection via API Gateway; environment variable exfiltration. Supply chain: container image scanning (Trivy); SBOM generation (Syft); image signing (Cosign); SLSA framework level 2.

**Weeks 11-12:** Complete all CloudGoat and KubeGoat scenarios. Design and document full cloud security architecture. Milestone assessment.

## Part C: Graded Problem Sets (Selected)

**Problem 1.** An EC2 instance role has: Allow iam:PassRole, lambda:CreateFunction, lambda:InvokeFunction, iam:ListRoles on *. Identify every privilege escalation path available to an attacker who has compromised this instance.

**Problem 2.** Explain IMDSv1 vs IMDSv2 difference. Why is IMDSv1 vulnerable to SSRF? What additional step does IMDSv2 require (PUT request for token) and why does it prevent most SSRF attacks?

**Problem 3.** Implement a Kubernetes RBAC misconfiguration: create a ServiceAccount with ClusterAdmin privileges, mount into a pod, demonstrate full cluster control via the mounted token. Fix using minimum-privilege RBAC.

**Problem 4.** Write a Boto3 security audit script reporting: (a) all S3 buckets with public read/write; (b) all security groups with 0.0.0.0/0 on port 22 or 3389; (c) all IAM users without MFA; (d) whether CloudTrail is enabled in all regions; (e) whether root account access keys exist.

---

---

# MODULE 4.10 — Security Engineering & Secure Systems Design

**Duration:** 8–10 weeks | **Hours/week:** 12 | **Total hours:** ~105

## Part A: Key Reading

- **Anderson** — *Security Engineering*, 3rd ed.: Ch. 2 (Psychology and Usability), Ch. 4 (Access Controls — Bell-LaPadula, Biba, Clark-Wilson, RBAC, ABAC, reference monitor), Ch. 5 (Cryptography — key management, HSMs), Ch. 13 (Network Attack and Defense), Ch. 21 (Security Economics).
- **Shostack** — *Threat Modeling: Designing for Security*: Ch. 1 (four-question framework), Ch. 2 (strategies), Ch. 4 (STRIDE per element), Ch. 6 (attack trees).
- **NIST SP 800-207** — *Zero Trust Architecture*: 7 tenets, logical components, migration strategies.
- **ProVerif Manual** (prosecco.gforge.inria.fr): introduction and first 3 tutorials. Model DH key exchange. Verify: shared secret is secret; authentication holds with pre-shared identity keys.

## Part B: Weekly Schedule

**Weeks 1-2:** Threat modeling. Shostack Ch. 1-6. Complete STRIDE threat model for your Module 3.5 HTTP server: DFD, minimum 20 threats, mitigations for each. Attack tree for gaining admin access to a web application (3 levels deep, cost-annotated).

**Weeks 3-4:** Access control and formal models. Anderson Ch. 4. Implement Bell-LaPadula in Python: labels (TS, S, C, U), subjects and objects, can_read and can_write enforcement. Write 15 test cases. Implement a reference monitor as a Linux LSM module or LD_PRELOAD interposer enforcing a policy file.

**Weeks 5-6:** Formal verification. ProVerif: model simplified TLS 1.3 handshake (2-message SIGMA). Verify secrecy of session key and mutual authentication. TLA+: specify a two-phase commit protocol; check agreement and validity using TLC model checker.

**Week 7:** Hardware security and TPM. Set up swtpm (software TPM). Implement: TPM key generation; sealing data to PCR state; remote attestation (quote over PCRs, verify with endorsement key). Document the boot sequence from UEFI secure boot through shim, GRUB, and kernel with measured boot.

**Weeks 8-9:** Zero Trust design. Design a Zero Trust architecture for 100-person engineering org: identity provider (SAML/OIDC), device trust (certificate enrollment, MDM), micro-segmentation, continuous verification (UEBA, anomaly detection). S-SDLC: implement a security-gated CI/CD pipeline for your HTTP server: SAST (Semgrep), SCA (Trivy), secrets scanning (Gitleaks), DAST (OWASP ZAP). All gates must pass before merge.

**Week 10:** Capstone threat model for a real open-source application (>5000 GitHub stars). Milestone assessment.

## Part C: Graded Problem Sets (Selected)

**Problem 1.** Apply STRIDE per-element to: web application (process) reading user data from database (data store) making API calls to payment processor (external entity). For each element and each STRIDE category, identify one specific threat and one mitigation.

**Problem 2.** Prove the following property of Bell-LaPadula: if all subjects and objects are initialized with valid labels, and all operations are mediated by the reference monitor enforcing BLP rules, then no information can flow from high to low security labels. Use induction on the number of operations.

**Problem 3.** Design a key management architecture for a SaaS application encrypting customer data at rest: (a) key hierarchy (master key -> DEK -> KEK); (b) where each key is stored and how protected; (c) key rotation policy; (d) procedure for key compromise response; (e) HSM usage to protect the root.

**Problem 4.** Model the following simplified protocol in ProVerif and verify the session key is secret: Alice generates (a, g^a); Bob generates (b, g^b); Alice sends g^a to Bob; Bob sends g^b to Alice; both compute K = g^ab; both derive SK = H(K, g^a, g^b). Show the model and verification output. Then show that without authentication the protocol is vulnerable to MITM.

---

---

# MODULE 4.11 — Capstone: Comprehensive Security Research Project

**Duration:** 12–16 weeks | **Hours/week:** 20+ | **Total hours:** ~280

---

## Project Tracks

### Track A — Vulnerability Research and Exploit Development
Discover a 0-day or N-day vulnerability in a widely deployed target. Develop a working end-to-end exploit.

**Deliverables:** (1) Working proof-of-concept exploit. (2) Technical advisory in CVE format: vulnerability description, affected versions, root cause analysis, PoC, CVSS score, remediation guidance. (3) Technical paper (15+ pages): discovery methodology, root cause analysis with code references, exploit development process (each mitigation bypass), potential generalizations of the vulnerability class. (4) Responsible disclosure: 90-day timeline to vendor for 0-days; attribution credit for N-days.

**Target selection:** focus on attack surface from Phases 2-3 — kernel drivers, file system parsers, network protocol implementations, embedded firmware. Good targets: obscure but widely deployed network equipment firmware, industrial control system software, PDF/image parsers.

---

### Track B — Defensive Tool Development
Design, implement, and rigorously evaluate a novel defensive security tool.

**Deliverables:** (1) Production-quality open-source tool with documentation, build instructions, reproducible tests. (2) Evaluation paper (15+ pages): motivation, design (architecture, algorithms, decisions), implementation, evaluation (benchmarks, detection rates, false positive rates vs baselines). (3) Public GitHub repository with code, README, CI/CD, contribution guide.

**Example directions:** hybrid static-dynamic vulnerability detector using symbolic execution; eBPF-based anomaly detection with formal detection guarantees; post-quantum TLS library competitive with classical TLS; DGA detector with provably low false positive rate using information-theoretic bounds.

---

### Track C — Cryptographic Research
Prove a new attack on an existing protocol, or design and formally verify a new protocol.

**Deliverables:** (1) Formal proof (attack or security proof) at the standard of a cryptography research paper. (2) ProVerif or Tamarin model verifying key security properties (secrecy, authentication, forward secrecy). (3) Reference implementation (or attack code). (4) 15+ page paper: motivation, related work, construction/attack, security analysis, performance evaluation.

---

### Track D — Threat Intelligence and Malware Analysis
Original, in-depth analysis of a malware campaign or threat actor revealing something not previously published.

**Deliverables:** (1) Threat intelligence report (20+ pages) at Mandiant/CrowdStrike standard: threat actor assessment, malware technical analysis, infrastructure analysis, ATT&CK mapping, IOC set, detection rules (YARA + Sigma), attribution assessment. (2) All analysis artifacts: annotated Ghidra databases, decrypted configurations, protocol specifications, network traffic analysis. (3) IOC sharing: submit to MISP, VirusTotal, MalwareBazaar.

---

## Research Process Schedule

### Weeks 1-2 — Topic Selection and Literature Review
- Select track and specific target/topic.
- Literature review: Google Scholar, USENIX Security, IEEE S&P, ACM CCS, NDSS, Black Hat, DEF CON proceedings.
- Define your specific, novel contribution and how it differs from all prior work.
- Write a 2-page research proposal: problem statement, approach, expected contribution, timeline.

### Weeks 3-6 — Primary Research Phase
- Execute: fuzzing, manual audit, protocol analysis, malware analysis, or tool implementation.
- Keep a daily research log with findings, dead ends, and hypotheses.
- Weekly review: is the contribution still novel and significant?

### Weeks 7-10 — Artifact Development
- Develop the primary artifact: working exploit, functional tool, formal proof, or analysis report.
- Iterate on: reliability (exploits work >80%), generality (applies to multiple targets), completeness (tool covers claimed scope).

### Weeks 11-13 — Evaluation and Paper Writing
- Evaluation: benchmark tool; test exploit against all claimed targets; peer-review proof.
- Write the paper: introduction, background, design/discovery, implementation, evaluation, related work, conclusion.
- Get feedback from a trusted technical peer.

### Weeks 14-16 — Polish, Disclosure, and Public Release
- Responsible disclosure (Track A) or public release (Tracks B-D).
- Finalize paper to publication quality.
- Prepare a 30-minute technical presentation.
- Submit to a venue: security conference, blog post series, or bug bounty program.

---

## Deliverable Rubric

**Technical Quality (40%):** Work is technically correct and rigorous. Claims are backed by evidence. Methodology is reproducible.

**Novelty and Contribution (25%):** Advances the state of knowledge. Differentiated from prior work.

**Communication (20%):** Paper is clear, precise, and well-organized. Presentation conveys core ideas effectively.

**Impact Potential (15%):** Vulnerability is in a widely-deployed system. Tool addresses a real defensive gap. IOCs/detections are actionable.

---

## Final Portfolio

Upon completion of all 11 modules, compile:

1. **Portfolio:** all projects, exploits, tools, and analysis reports from Modules 4.1-4.11 on GitHub + personal site.
2. **CVE/Advisory Collection:** any CVEs discovered or N-day advisories written.
3. **Publication:** Module 4.11 capstone paper submitted to a venue.
4. **CTF Record:** CTFtime.org profile documenting all competitions, ranked challenges, top-3 finishes.
5. **Certifications (recommended after relevant modules):** OSCP (after 4.8), OSED (after 4.5), GREM (after 4.6), AWS Security Specialty (after 4.9).

---

## Final Milestone Assessment — Phase 4 Complete

*3-hour cumulative technical assessment, oral examination format:*

**Section 1 — Cryptography (30 min):** Explain the padding oracle attack against AES-CBC. Prove security of HMAC given a secure compression function. Trace the TLS 1.3 key schedule.

**Section 2 — Exploitation (60 min):** Given a binary with NX + PIE + ASLR + Full RELRO + Stack Canary, describe an exploit strategy. Write pwntools exploit code. Explain tcache poisoning and safe-linking bypass.

**Section 3 — Reverse Engineering (30 min):** Given a disassembled function, identify the algorithm. Identify anti-analysis techniques and describe how to defeat each.

**Section 4 — Forensics and Incident Response (30 min):** Given Volatility3 output, identify indicators of compromise. Build a timeline from event log fragments.

**Section 5 — Security Architecture (30 min):** Design a secure web application architecture from scratch. Produce a STRIDE threat model. Identify the top 5 threats and their mitigations.

---

*End of Phase 4 Complete Study Package*
*Curriculum Complete — Phases 0 through 4*
