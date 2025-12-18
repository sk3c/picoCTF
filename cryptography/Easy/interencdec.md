# INTERENCDEC

**Description**
Can you get the real meaning from this file.

**Vulnerability**
Cryptography

## Solution

**Step 1**
The file contains an encrypted version of the flag. With basic knowledge of common encodings, we can recognize it as Base64.
Alternatively, online detection tools can be used to identify the encoding.
After decoding it once, the output is still Base64-encoded, so we decode it a second time to obtain the next layer.

**Step 2**
The final decoded text appears to use a rotation (Caesar) cipher.
Since picoCTF flags typically begin with pico, we can compare the first character of the ciphertext with p.
The shift required is ROT19, which can then be applied to the entire string to successfully decode the flag.
