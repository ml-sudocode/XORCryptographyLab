<!---

This file is used to generate your project datasheet. Please fill in the information below and delete any unused
sections.

You can also include images in this folder and reference them in the markdown. Each image must be less than
512 kb in size, and the combined size of all images must be less than 1 MB.
-->

## How it works

A four-bit hardware encryption and cryptanalysis chip implemented using four XOR gates.

The circuit combines a four-bit message with a four-bit secret key to produce ciphertext. The same circuit performs decryption using the original key.

The design is entirely combinational and requires no clock, processor, memory or software.

It demonstrates symmetric encryption, the principles of a one-time pad and the vulnerabilities introduced by key reuse.

## How to test

- IN0–IN3: Plaintext or ciphertext.
- IN4–IN7: Secret key.
- OUT0–OUT3: Result.

### Encryption

Enter plaintext 1011 and key 0110.

Expected output: 1101.

### Decryption

Enter ciphertext 1101 and key 0110.

Expected output: 1011.

### Key reuse attack

Encrypt two messages, 1011 and 0011, using the same key, 0110.

The resulting ciphertexts are 1101 and 0101.

XOR the two ciphertexts together to obtain 1000, revealing the difference between the original messages.

## External hardware

Once the manufactured chip is received, it will be connected to physical switches, LEDs and appropriate supporting components to create an interactive hardware cryptography demonstrator.

This is an educational project, not a secure encryption product.
