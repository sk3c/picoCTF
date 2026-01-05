# Rust Fixme 1

Have you heard of Rust? Fix the syntax errors in this Rust file to print the flag!

## Solution

### **Step 1**

Download the source code provided in the challenge and unzip it.
Before running the program, make sure that **Rust** is installed on your system.

To build the project, use the following command:

```bash
cargo build
```

When you try to build the project, Cargo returns multiple syntax errors. These errors indicate what needs to be fixed in the source code.

### **Step 2**
The file contains several comments that hint at the issues, such as how to end statements, how to return from a function, and how to print variables in Rust. These can be resolved with basic Rust knowledge or a quick search.

After fixing the syntax errors, the corrected code looks like this:

```rust
use xor_cryptor::XORCryptor;

fn main() {
    // Key for decryption
    let key = String::from("CSUCKS");

    // Encrypted flag values
    let hex_values = [
        "41", "30", "20", "63", "4a", "45", "54", "76",
        "01", "1c", "7e", "59", "63", "e1", "61", "25",
        "7f", "5a", "60", "50", "11", "38", "1f", "3a",
        "60", "e9", "62", "20", "0c", "e6", "50", "d3",
        "35"
    ];

    // Convert the hexadecimal strings into bytes
    let encrypted_buffer: Vec<u8> = hex_values
        .iter()
        .map(|&hex| u8::from_str_radix(hex, 16).unwrap())
        .collect();

    // Create the decryption object
    let res = XORCryptor::new(&key);
    if res.is_err() {
        return;
    }
    let xrc = res.unwrap();

    // Decrypt the flag and print it
    let decrypted_buffer = xrc.decrypt_vec(encrypted_buffer);
    println!(
        "{}",
        String::from_utf8_lossy(&decrypted_buffer)
    );
}

```

After fixing the syntax errors and successfully building the project, running the program prints the decrypted flag.
