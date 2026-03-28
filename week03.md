Week 3 — Encryption and Attacks
Unit: COIT13240 Applied Cryptography
Term: T1 2025 | Campus: Brisbane
Date: Week 3



KPA, CPA, CCA

KPA (Known Plaintext Attack) = attacker knows some plaintext AND its corresponding ciphertext
CPA (Chosen Plaintext Attack) = attacker can choose any plaintext and get its encryption
CCA (Chosen Ciphertext Attack) = attacker can choose any ciphertext and get its decryption

Modes of Operation

Modes of operation are needed because block ciphers like DES and AES encrypt fixed-size blocks only (64 bits for DES, 128 bits for AES). Real messages are almost always longer than one block, so a method is needed to apply the block cipher across multiple blocks securely.
Without a mode of operation, the default behaviour is ECB (Electronic Code Book) each block is encrypted independently with the same key.

Attack on AES-128

Calculation:
AES-128 key space = 2¹²⁸ ≈ 3.4 × 10³⁸ possible keys
With attack speedup of 10⁶:
Effective keys to search = 2¹²⁸ / 10⁶ = 2¹²⁸ / 2²⁰ = 2¹⁰⁸
Assuming $10,000,000 budget at ~$1,000 per machine, each doing ~10⁹ decryptions/second:
Number of machines = 10,000
Combined speed     = 10,000 × 10⁹ = 10¹³ keys/second
Time required      = 2¹⁰⁸ / 10¹³ ≈ 3.2 × 10¹⁸ seconds
                   ≈ 100 billion years

                   

DES in OpenSSL.

I created a 24-byte plaintext file containing repeating pattern "AAAAAAAABBBBBBBBCCCCCCCC" and encrypted it using DES-ECB with OpenSSL

<img width="590" height="113" alt="Screenshot 2026-03-28 at 3 19 59 pm" src="https://github.com/user-attachments/assets/08fd34b1-3f70-45b1-a492-eb9a2e43a4cf" />

<img width="637" height="122" alt="Screenshot 2026-03-28 at 3 22 10 pm" src="https://github.com/user-attachments/assets/55122345-18b0-4966-b485-21b49a6aa8b7" />

DES in OpenSSL

<img width="644" height="207" alt="Screenshot 2026-03-28 at 3 24 07 pm" src="https://github.com/user-attachments/assets/0d37519f-4ef8-48e3-9461-9baaf6b848a8" />



 DES without padding and with ECB

 I encrypted the same file using an explicit key with no padding, then modified one character and compared
 
<img width="638" height="141" alt="Screenshot 2026-03-28 at 3 24 35 pm" src="https://github.com/user-attachments/assets/95a4ea28-342f-4f87-88c2-2f1642d054ea" />


 AES in OpenSSL

 I encrypted the same plaintext file using AES-128-CBC

<img width="642" height="388" alt="Screenshot 2026-03-28 at 3 30 29 pm" src="https://github.com/user-attachments/assets/0350bd92-2465-4525-b66a-5779f88f8659" />

 Performance of Ciphers 

 I ran the OpenSSL speed test for AES-128-CBC
 
<img width="649" height="345" alt="Screenshot 2026-03-28 at 3 33 46 pm" src="https://github.com/user-attachments/assets/e3adca5b-6fdb-49f8-a87d-4b1f2a98b354" />


Reflection

This week introduced attack models and cipher modes. Understanding KPA, CPA and CCA was initially confusing as they seemed similar, but the key difference is the level of attacker control — from passive observation in KPA to full decryption oracle access in CCA.

The most effective task was the ECB demonstration. By changing just one character in plain2.txt, I could see that Block 1 and Block 2 ciphertext remained identical across both files, visually proving the ECB weakness. The OpenSSL speed test showed my ARM64 VM can perform approximately 97.9 million AES decryptions per second — yet this would still take 10²³ years to brute force AES-128, connecting directly to the Task 3 calculation.

Compared to Week 2's Caesar cipher with only 26 keys, AES-128's 2¹²⁸ key space shows how dramatically key size affects security.


Novel Insight: ECB Mode and the Penguin Problem

A famous demonstration of ECB's weakness is the "ECB penguin" when a bitmap image is encrypted with AES-ECB, the outline remains visible because identical pixel blocks encrypt to identical ciphertext blocks. This shows ECB leaks structural information even without revealing content.

This is why CBC, CTR and GCM modes were developed — the IV in CBC randomises the first block, cascading through all subsequent blocks via chaining, ensuring identical plaintexts produce different ciphertexts.

Referance 
https://en.wikipedia.org/wiki/Block_cipher_mode_of_operation
