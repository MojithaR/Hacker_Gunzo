# **🔍 PicoCTF Flag Verification Challenge**

Welcome to the **PicoCTF Flag Verification** challenge! In this challenge, our objective is to verify the authenticity of flags by decrypting files and checking their SHA-256 hashes. Let's break down the solution step by step! 🌟

---

## **📜 Challenge Overview**

This challenge provides us with encrypted files and a checksum. We need to:
1. Verify the checksum of the files.
2. Decrypt the files using a provided script.
3. Identify the legitimate flag from the decrypted content.

---

## **🗂️ Step-by-Step Guide**

1. **Connect to the SSH Server:**  
   Begin by connecting to the remote server using SSH:
   ```bash
   ssh -p 60604 ctf-player@rhea.picoctf.net
   ```
   Enter the password `83dcefb7` when prompted.

2. **List Files in the Directory:**  
   Once connected, list the files to find `checksum.txt`, `decrypt.sh`, and the `files` directory:
   ```bash
   ls
   ```
   ```bash
   ls files
   ```

3. **Verify the Checksum:**  
   Calculate the SHA-256 checksum of the files in the `files` directory and compare it with the provided checksum:
   ```bash
   sha256sum files/*
   ```
   Make sure the checksums match the provided checksum `467a10447deb3d4e17634cacc2a68ba6c2bb62a6637dad9145ea673bf0be5e02`.

4. **Decrypt the Files:**  
   Use the `decrypt.sh` script to decrypt each file. Run the following command to iterate through all files and check their content:
   ```bash
   for i in $(find files -type f); do ./decrypt.sh $i | grep pico; done
   ```
   This command decrypts each file and searches for the string "pico" in the output.

5. **Analyze the Output:**  
   Look for the decrypted flag in the output. It should be in the format `picoCTF{...}`.

---

## **📝 Decryption Script Breakdown**

Here’s a look at the `decrypt.sh` script that handles file decryption:

```bash
#!/bin/bash

# Check if the user provided a file name as an argument
if [ $# -eq 0 ]; then
    echo "Expected usage: decrypt.sh <filename>"
    exit 1
fi

# Store the provided filename in a variable
file_name="$1"

# Check if the provided argument is a file and not a folder
if [ ! -f "/home/ctf-player/drop-in/$file_name" ]; then
    echo "Error: '$file_name' is not a valid file. Look inside the 'files' folder with 'ls -R'!"
    exit 1
fi

# If there's an error reading the file, print an error message
if ! openssl enc -d -aes-256-cbc -pbkdf2 -iter 100000 -salt -in "/home/ctf-player/drop-in/$file_name" -k picoCTF; then
    echo "Error: Failed to decrypt '$file_name'. This flag is fake! Keep looking!"
fi
```

- **Checks for Argument**: Ensures a filename is provided.
- **Validates File**: Confirms the file exists.
- **Decrypts File**: Uses `openssl` to decrypt with AES-256-CBC and a password `picoCTF`.

---

## **📊 Process Mind Map**

```text
🔍 PicoCTF Flag Verification Challenge
 ├── Connect to SSH Server (ssh)
 ├── List Files (ls)
 ├── Verify Checksum (sha256sum)
 ├── Decrypt Files (decrypt.sh)
 └── Analyze Output (grep pico)
```

---

## **🧠 Key Insights**

- **File Verification:** Always verify file integrity with checksums to ensure data authenticity.
- **Decryption:** Understanding the decryption process and commands like `openssl` is essential for handling encrypted files.
- **Script Analysis:** Reviewing the provided scripts helps understand how to handle files and extract valuable information.

---

## **🎬 Demo**

![PicoCTF Flag Verification Demo](https://media.giphy.com/media/3LlHVGbZf4qVeYzkSE/giphy.gif?cid=ecf05e47e5bopj385orjw2g48vb9dzhk7w9ay07gbg48zag3&ep=v1_gifs_search&rid=giphy.gif&ct=g)
<!-- Replace with an actual link to your demo GIF -->

---

## **🛠️ Useful Commands**

| Command                           | Description                                |
|-----------------------------------|--------------------------------------------|
| `ssh -p 60604 ctf-player@rhea.picoctf.net` | Connect to the remote server via SSH     |
| `ls`                              | List files in the directory                |
| `sha256sum files/*`                | Calculate SHA-256 checksum                 |
| `for i in $(find files -type f); do ./decrypt.sh $i | grep pico; done` | Decrypt files and search for flag         |
| `grep pico`                        | Search for the flag in the output          |

---

**Happy Hacking!** 😎
