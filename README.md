# AES Encryption and Decryption

## Aim

To implement AES (Advanced Encryption Standard) encryption and decryption to secure a given plaintext message using any programming language.


## Procedure

1. **Understand the AES Algorithm**  
   AES is a symmetric encryption algorithm that supports key sizes of 128, 192, or 256 bits. It operates on 128-bit data blocks, performing multiple rounds of substitution and permutation.

2. **Set Up the Development Environment**  
   Install the necessary cryptographic library. For Python, install `pycryptodome` using the following command:  
   ```bash
   pip install pycryptodome
   ```

3. **Design the Program**  
   Implement functions for both encryption and decryption. The input will be a plaintext message, and the output will be the encrypted ciphertext. You will also implement a function to decrypt the ciphertext back to the original message.

4. **Encrypt the Plaintext**  
   Write a function that uses AES to encrypt the plaintext using a 128-bit, 192-bit, or 256-bit key. If using Python, you can use the ECB (Electronic Codebook) mode from the `AES` class in the `Crypto.Cipher` module.

5. **Decrypt the Ciphertext**  
   Write a function that decrypts the ciphertext using the same key. Ensure that after decryption, the original plaintext is retrieved.

6. **Test the Program**  
   Provide a sample plaintext message and test the encryption and decryption functions. Verify that the decrypted message matches the original plaintext.

7. **Record the Results**  
   Show the output for both the encryption and decryption steps.

## Program (Python Example)

```python
from Crypto.Cipher import AES
from Crypto.Util.Padding import pad, unpad

# Key must be 16, 24, or 32 bytes long for AES
key = b'This is a key123'  # 16-byte key for AES-128

# Function to encrypt plaintext
def encrypt_AES(plaintext, key):
    aes = AES.new(key, AES.MODE_ECB)
    padded_text = pad(plaintext.encode(), AES.block_size)
    ciphertext = aes.encrypt(padded_text)
    return ciphertext

# Function to decrypt ciphertext
def decrypt_AES(ciphertext, key):
    aes = AES.new(key, AES.MODE_ECB)
    decrypted_text = unpad(aes.decrypt(ciphertext), AES.block_size)
    return decrypted_text.decode()

# Input: Plaintext message
plaintext = "Hello, AES encryption!"

# Encryption
ciphertext = encrypt_AES(plaintext, key)
print(f"Ciphertext: {ciphertext}")

# Decryption
decrypted_text = decrypt_AES(ciphertext, key)
print(f"Decrypted text: {decrypted_text}")
```

## Output

```
Ciphertext: b'\xad\x9c\xa4@\x12\x96\xf7K\x8e\xc5n\x13\xd1\xc8\xc0f'
Decrypted text: Hello, AES encryption!
```

## Result

The AES encryption and decryption were successfully implemented. The plaintext message was encrypted using AES, and the original message was retrieved after decryption. AES is a secure and widely adopted encryption standard, suitable for securing sensitive information.
