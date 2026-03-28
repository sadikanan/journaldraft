Task 2 - Caesar Decrypt

Decrypt "pjhigpaxp" using Caesar cipher with key 15.

how Caesar decryption works?
Each letter shifts back by 15 positions in the alphabet
Formula i use : plaintext = (ciphertext_position - 15) mod 26

Emplement 

p = 15 → 15 - 15 = 0  → a
j = 9  → 9  - 15 = -6 → -6 + 26 = 20 → u
h = 7  → 7  - 15 = -8 → -8 + 26 = 18 → s
i = 8  → 8  - 15 = -7 → -7 + 26 = 19 → t
g = 6  → 6  - 15 = -9 → -9 + 26 = 17 → r
p = 15 → 15 - 15 = 0  → a
a = 0  → 0  - 15 = -15 → -15 + 26 = 11 → l
x = 23 → 23 - 15 = 8  → i
p = 15 → 15 - 15 = 0  → a

Plaintext = "australia" |


Caesar Decrypt

<img width="598" height="316" alt="Screenshot 2026-03-28 at 1 32 48 pm" src="https://github.com/user-attachments/assets/8396a18c-d878-40ab-8c46-85447623010d" />

This confirmed the manual working was correct. 


 Caesar Decrypt without Key

Decrypt "knuprdv" with unknown key.
Since the key is unknown, I applied a brute force approach 
 
 <img width="355" height="555" alt="Screenshot 2026-03-28 at 1 34 26 pm" src="https://github.com/user-attachments/assets/49a1629d-0090-4767-b65e-94a9cb5a3617" />

<img width="384" height="556" alt="Screenshot 2026-03-28 at 1 43 35 pm" src="https://github.com/user-attachments/assets/705f6a6c-64eb-448f-bee4-4d731d4664d9" />

Key 9 gives "BELGIUM" — the only meaningful English word in all 26 results, confirming the key is 9.


 Implement Caesar Cipher in Python

 I implemented Caesar cipher from scratch in Python without using pycipher

 <img width="290" height="154" alt="Screenshot 2026-03-28 at 1 47 14 pm" src="https://github.com/user-attachments/assets/3c88ed6f-648d-4d4b-9f82-5f93315e382a" />

Output:
Plaintext:  AUSTRALIA
Key:        15
Ciphertext: PJHIGPAXP
Decrypted:  AUSTRALIA
This matches the manual working from Task 2, which confirms the implementation is correct.


 Brute Force of Caesar in Python

 I extended the Caesar implementation to perform a brute force attack, saved as bruteforce.py

 <img width="361" height="523" alt="Screenshot 2026-03-28 at 1 49 14 pm" src="https://github.com/user-attachments/assets/bc894c56-8049-4344-935a-b4741ab82560" />

Output confirmed Key 9 = BELGIUM, consistent with Task 4.
 
Playfair Decrypt
Decrypt "rpopizuliz" using Playfair cipher with keyword "program".
I attempted to use pycipher for this task but encountered an error related to the I/J substitution in the Playfair matrix:
ValueError: 'I' is not in list

<img width="599" height="256" alt="Screenshot 2026-03-28 at 2 29 46 pm" src="https://github.com/user-attachments/assets/2d2a5b49-39dc-498d-8346-85530b5c231a" />

Rail Fence Decrypt

Decrypt "irtngapconentehooisnapiaintecledlts" using Rail Fence cipher with key 3.

<img width="388" height="151" alt="Screenshot 2026-03-28 at 2 17 52 pm" src="https://github.com/user-attachments/assets/2bc40616-b234-4e5d-9afd-8232a12888d7" />

Decrypted: INTERNETTECHNOLOGIESANDAPPLICATIONS

Reflection
This week introduced classical ciphers the historical foundation of modern cryptography. The most important insight was understanding why these ciphers are weak, not just how they work.The Caesar cipher has a key space of only 26, making brute force trivial. The Playfair cipher is more complex (using digraphs rather than single letters), which significantly increases resistance to simple frequency analysis. 
I found the manual Caesar decryption straightforward since I had covered modular arithmetic in previous mathematics units. The most challenging part was the Playfair cipher
 
Connecting to the lecture: the concept of key space size was emphasised as a primary measure of cipher strength. Caesar's 26-key space is trivially small, while the One Time Pad (covered in Task 10) has a theoretically infinite key space which is why it is the only provably unbreakable cipher.

Novel Insight: Why Classical Ciphers Still Matter

Although Caesar and Playfair ciphers are completely insecure by modern standards, studying them is not merely historical. Several important cryptographic concepts originate from classical cipher analysis:

Frequency analysis — developed to break substitution ciphers, it laid the groundwork for statistical cryptanalysis used against modern stream ciphers.

Kerckhoffs's principle — the idea that a cipher should be secure even if everything about the system except the key is public knowledge. Caesar fails this because knowing the algorithm immediately reveals the key space.

Confusion and diffusion — concepts introduced by Claude Shannon that evolved directly from the weaknesses of classical ciphers. Substitution provides confusion; transposition provides diffusion. Modern ciphers like AES combine both in multiple rounds.

reference : https://pages.cs.wisc.edu/~rist/642-spring-2014/shannon-secrecy.pdf
