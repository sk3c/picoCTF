# HASHCRACK

**Description**
A company stored a secret message on a server which got breached due to the admin using weakly hashed passwords. Can you gain access to the secret stored within the server?

**Vulnerability**
Cryptography

## Solution

**Step 1**
After connecting to the server using netcat, you are presented with a hashed string.
The first task is to identify the hashing algorithm used.
This can be done either by recognizing the format visually (if you are familiar with common hash types) or by using an online hash identification tool.
Once the algorithm is identified, use an online decoder or a terminal-based tool to decrypt the hash and obtain the plaintext value.

**Step 2**
Upon submitting the decrypted value, the server responds with two more hashes. Decrypt those hash same as before.
After successfully decoding this final hash and submitting the correct plaintext, the server reveals the flag for the challenge.
