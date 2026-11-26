# XOR Cryptography Lab

A four-bit hardware encryption and cryptanalysis chip designed using just four XOR gates.

## What I built

I wanted to explore the connection between transistor-level chip design, digital logic and cryptography by building a minimal encryption circuit.

The chip accepts a four-bit message and a four-bit secret key, producing a four-bit ciphertext. The same circuit can perform decryption using the original key.

The design is entirely combinational: no processor, software, memory or clock is required.

## From simulation to physical hardware

Once I receive the manufactured chip from Tiny Tapeout, I intend to wire it up with physical switches, LEDs and the necessary supporting components to create an interactive hardware cryptography demonstrator.

The aim is to allow anyone, including those without a technical background, to physically interact with the chip and experiment with encryption, decryption and basic cryptographic attacks.

Rather than running encryption software on a general-purpose computer, users will be interacting directly with dedicated silicon implementing the cryptographic operation.

## How to use it

- Switches 1–4: Plaintext or ciphertext.
- Switches 5–8: Secret key.
- LEDs 1–4: Result (illuminated = 1).

Start the Wokwi simulation and toggle the switches to experiment with different messages and keys.

## Experiments

### 1. Encrypt a message

- Plaintext: `1011`
- Secret key: `0110`
- Expected ciphertext: `1101`

### 2. Decrypt a message

- Ciphertext: `1101`
- Secret key: `0110`
- Expected plaintext: `1011`

XOR is self-inverting. The same physical circuit performs both encryption and decryption.

### 3. Brute-force a secret key

Enter ciphertext `1101` and try all 16 possible keys. Observe that every possible four-bit plaintext can be produced. Without additional information, an attacker cannot identify the original message from these candidates alone.

### 4. Attack key reuse

Encrypt two different messages using the same secret key:

| Plaintext | Key | Ciphertext |
|---|---|---|
| 1011 | 0110 | 1101 |
| 0011 | 0110 | 0101 |

Now XOR the two ciphertexts together using the chip.

The result is `1000`. The secret key cancels out, revealing which bits differ between the original messages.

If an attacker knows either plaintext, they can recover the other without knowing the key.

## Why XOR?

XOR is reversible, computationally inexpensive and easy to implement in hardware. It is a fundamental operation in modern cryptographic algorithms, including AES and ChaCha20.

Under the strict conditions of a one-time pad, XOR-based encryption can even provide information-theoretic secrecy.

## Design specification

- 8 binary inputs
- 4 XOR gates
- 4 ciphertext outputs
- Combinational logic
- No clock required

## Security disclaimer

This chip is an educational demonstration, not a secure encryption product. It does not implement secure key generation, key storage or message authentication.

## Project background and resources

Designed during the November 2026 Tiny Tapeout workshop in Singapore.

Tiny Tapeout makes semiconductor design and fabrication accessible to individuals, including those without prior chip design experience.

- [Tiny Tapeout](https://tinytapeout.com/)
- [Tiny Tapeout Workshop](https://tinytapeout.com/guides/workshop/)
- [SiliWiz — learn how transistors work](https://tinytapeout.com/siliwiz/)
- [Draw your own MOSFET](https://tinytapeout.com/guides/workshop/draw-a-mosfet-faster/)
- [Simulate a logic gate](https://tinytapeout.com/guides/workshop/simulate-a-gate/)
- [Try this encryption chip in Wokwi](https://wokwi.com/projects/481737597825402881)
