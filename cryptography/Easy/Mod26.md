# MOD 26

**Description**
Cryptography can be easy, do you know what ROT13 is?

**Vulnerability**
Cryptography

## Solution

**Step 1**
The file contains the flag, but it is currently in an unreadable (gibberish) form due to encryption.
Based on the challenge description, we know which encryption method was used.

**Step 2**
The encryption is ROT13, which works by rotating each alphabetical character 13 positions forward.
To decrypt the flag, use any online ROT13 tool or write a simple script that applies a 13-character rotation to each letter in the string.


