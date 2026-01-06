# Rust Fixme 3
Have you heard of Rust? Fix the syntax errors in this Rust file to print the flag!

## Solution

### **Step 1**
In this challenge, everything we need is already provided. The only requirement is to understand what `unsafe` means in Rust and how unsafe code is used.

In Rust, `unsafe` allows us to perform operations that the compiler cannot guarantee are memory-safe. These operations are still valid Rust, but the responsibility for safety is shifted from the compiler to the developer. To call an unsafe function or use unsafe features, the code must be wrapped inside an `unsafe` block.

### **Step 2**
To solve the challenge, simply uncomment the existing `unsafe` block inside the `decrypt` function.

Once the `unsafe` block is enabled:
1. The code will compile successfully.
2. You can build and execute the program.
3. The decrypted output will be printed, revealing the flag.

No additional code changes are required—just enabling the unsafe block allows the program to run as intended.

