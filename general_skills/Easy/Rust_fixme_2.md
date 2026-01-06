# Rust Fixme 2
*The Rust saga continues! I ask you: can I borrow that… pleeeeeaaaasseeeee?*

## Solution

### **Step 1**
Just like in **Rust Fixme 1**, we need to make changes to the source code.
This time, the key issue is that we are passing a variable into a function and trying to modify it inside that function.

In Rust, values are immutable by default. If we want a function to modify a value that it borrows, we must:
- Pass the value as a **mutable reference**
- Declare the variable itself as **mutable** at the call site

A quick search (or a look at Rust’s ownership and borrowing rules) shows that this is done using `&mut`.

### **Step 2**
First, we update the `decrypt` function so it accepts a mutable reference to a `String`.
We do this by changing the parameter from `&String` to `&mut String`.

After making this change, the compiler will report additional errors. These happen because:
- The variable being passed (`party_foul`) is not declared as mutable
- The function call does not pass a mutable reference

To fix this:
1. Declare `party_foul` as `mut`
2. Pass it to `decrypt` using `&mut party_foul`

Once these changes are applied, the function can safely modify the string.

```rust
use xor_cryptor::XORCryptor;

fn decrypt(encrypted_buffer: Vec<u8>, borrowed_string: &mut String) {
    // Key for decryption
    let key = String::from("CSUCKS");

    // Modify the borrowed value
    borrowed_string.push_str("PARTY FOUL! Here is your flag: ");

    // Create decryption object
    let res = XORCryptor::new(&key);
    if res.is_err() {
        return;
    }
    let xrc = res.unwrap();

    // Decrypt flag and append it to the string
    let decrypted_buffer = xrc.decrypt_vec(encrypted_buffer);
    borrowed_string.push_str(&String::from_utf8_lossy(&decrypted_buffer));
    println!("{}", borrowed_string);
}

fn main() {
    // Encrypted flag values
    let hex_values = [
        "41", "30", "20", "63", "4a", "45", "54", "76",
        "01", "1c", "7e", "59", "63", "e1", "61", "25",
        "0d", "c4", "60", "f2", "12", "a0", "18", "03",
        "51", "03", "36", "05", "0e", "f9", "42", "5b"
    ];

    // Convert hexadecimal strings to bytes
    let encrypted_buffer: Vec<u8> = hex_values.iter()
        .map(|&hex| u8::from_str_radix(hex, 16).unwrap())
        .collect();

    // Declare the variable as mutable
    let mut party_foul = String::from("Using memory unsafe languages is a: ");

    // Pass a mutable reference so it can be modified
    decrypt(encrypted_buffer, &mut party_foul);
}
```
