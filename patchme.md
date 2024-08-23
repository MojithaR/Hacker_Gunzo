# **🔧 Patchme Challenge**

In this guide, we will explore how to decrypt an encoded file by analyzing and modifying a Python script. Let’s patch it up! 🛠️

---

## **🛠️ Step-by-Step Guide**

1. **Download the Files:**  
   First, download the required files using `wget`:
   ```bash
   wget https://artifacts.picoctf.net/c/202/patchme.flag.py
   wget https://artifacts.picoctf.net/c/202/flag.txt.enc
   ```

2. **Analyze the Files:**  
   Understand that we have a Python script and an encrypted text file. Use Sublime Text to open both files and get a better idea:
   ```bash
   subl .
   ```

3. **Examine the Encrypted File:**  
   The `flag.txt.enc` file is full of random characters and symbols, indicating it's encrypted. Let's focus on the Python code to decrypt it.

4. **Understand the Python Code:**  
   The script contains a function for XOR encryption, a password checker, and a decryption process. Here’s the critical part of the script:

   ```python
   def str_xor(secret, key):
       new_key = key
       i = 0
       while len(new_key) < len(secret):
           new_key = new_key + key[i]
           i = (i + 1) % len(key)
       return "".join([chr(ord(secret_c) ^ ord(new_key_c)) for (secret_c,new_key_c) in zip(secret,new_key)])

   flag_enc = open('flag.txt.enc', 'rb').read()

   def level_1_pw_check():
       user_pw = input("Please enter correct password for flag: ")
       if user_pw == "ak98-=90adfjhgj321sleuth9000":
           print("Welcome back... your flag, user:")
           decryption = str_xor(flag_enc.decode(), "utilitarian")
           print(decryption)
           return
       print("That password is incorrect")

   level_1_pw_check()
   ```

5. **Identify the Password:**  
   The password is hidden in the code. From the script, we can see the password is:  
   ```text
   ak98-=90adfjhgj321sleuth9000
   ```

6. **Run the Python Script:**  
   Execute the Python script with the identified password to reveal the flag:
   ```bash
   python3 patchme.flag.py
   ```
   Enter the password when prompted, and the script will display the flag:
   ```text
   picoCTF{p47ch1ng_l1f3_h4ck_21d62e33}
   ```

7. **Modify the Script for Direct Decryption (Optional):**  
   Alternatively, you can bypass the password check by directly decrypting the file with the following code modification:
   ```python
   flag_enc = open('flag.txt.enc', 'rb').read()
   decryption = str_xor(flag_enc.decode(), "utilitarian")
   print(decryption)
   ```
   This simplifies the process by removing the password check and immediately decrypting the flag.

---

## **📝 Mind Map of the Process**

```text
🔧 Patchme Challenge
 ├── Download Files (wget)
 ├── Analyze Files (subl)
 ├── Examine Encrypted File (flag.txt.enc)
 ├── Understand Python Code
 │    ├── XOR Function (str_xor)
 │    ├── Password Check (level_1_pw_check)
 ├── Identify Password (ak98-=90adfjhgj321sleuth9000)
 ├── Run Python Script (python3 patchme.flag.py)
 ├── Display Flag (picoCTF{p47ch1ng_l1f3_h4ck_21d62e33})
 └── Modify Script for Direct Decryption (Optional)
```

---

## **🔑 Key Takeaways**

This challenge teaches you how to analyze a Python script, identify key functions and values, and decrypt an encoded file. Understanding these concepts is crucial in reverse engineering and cybersecurity. 🚀

---

**Happy Hacking!** 🔓
