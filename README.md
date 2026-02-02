# 🔐 XOR CTF Decryption Script
```
     __   __  
\_/ /  \ |__) 
/ \ \__/ |  \

          ~ Md Haisam Hoque
              
```
This repository contains a simple **Python-based XOR decryption script** used to solve a common **CTF (Capture The Flag)** cryptography challenge.

The encrypted flag is stored using `chr(0x..) + chr(0x..)` format, and a repeating XOR key is applied to decrypt it.

---

## 📌 Challenge Overview

* Encryption Type: **XOR Cipher (Repeating Key)**
* Encrypted Format: `chr(0x..) + chr(0x..)`
* Key Used: `enkidu`
* Language: **Python 3**

XOR encryption is **symmetric**, meaning the same function can be used for both encryption and decryption.

---

## 🧠 How XOR Decryption Works

1. The key is repeated until it matches the length of the encrypted string.
2. Each character of the encrypted string is XORed with the corresponding key character.
3. The resulting characters form the decrypted flag.

---

## 🧪 Python Decryption Code

```python
def str_xor(secret, key):
    new_key = key
    i = 0
    while len(new_key) < len(secret):
        new_key += key[i]
        i = (i + 1) % len(key)
    return "".join(chr(ord(s) ^ ord(k)) for s, k in zip(secret, new_key))


flag_enc = (
    chr(0x15) + chr(0x07) + chr(0x08) + chr(0x06) + chr(0x27) +
    chr(0x21) + chr(0x23) + chr(0x15) + chr(0x58) + chr(0x18) +
    chr(0x11) + chr(0x41) + chr(0x09) + chr(0x5f) + chr(0x1f) +
    chr(0x10) + chr(0x3b) + chr(0x1b) + chr(0x55) + chr(0x1a) +
    chr(0x34) + chr(0x5d) + chr(0x51) + chr(0x40) + chr(0x54) +
    chr(0x09) + chr(0x05) + chr(0x04) + chr(0x57) + chr(0x1b) +
    chr(0x11) + chr(0x31) + chr(0x0d) + chr(0x5f) + chr(0x05) +
    chr(0x40) + chr(0x04) + chr(0x0b) + chr(0x0d) + chr(0x0a) +
    chr(0x19)
)

key = "enkidu"

flag = str_xor(flag_enc, key)
print("Decrypted Flag:", flag)
```

---

## ✅ Output

```
picoCTF{3qu4l1ty_n0t_4551gnm3nt_f6a5aefc}
```

---

## 🚩 CTF Lesson Learned

* XOR encryption is reversible
* Be careful with `=` vs `==` in condition checks
* Always inspect how keys are repeated in XOR-based challenges

---

## 📜 License

This project is for **educational and CTF practice purposes only**.

---

Happy Hacking 🏴‍☠️
