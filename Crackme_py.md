# **🔐 Crackme_py CTF Challenge**

In this CTF challenge, we need to decrypt a Python script to unveil the hidden key. Let's break it down step by step! 🚀

---

## **🗂️ Setting Up the Environment**

1. **Create a Working Directory:**  
   Start by creating a dedicated folder to keep everything organized:  
   ```bash
   mkdir crackme_py
   ```

2. **Download the Encrypted Python Program:**  
   Use the following command to download the encrypted script:  
   ```bash
   wget <link of the py program>
   ```

3. **Run the Program:**  
   Attempt to run the script with Python 3:  
   ```bash
   python3 crackme.py
   ```
   You will see prompts similar to:
   ```bash
   What's your first number? 7
   What's your second number? 4
   The number with the largest positive magnitude is 7
   ```

---

## **🔍 Analyzing the Python Script**

### **Searching for the Encrypted Key**
While exploring the code, you find the following string, which appears to be an encrypted secret:
```python
bezos_cc_secret = "A:4@r%uL`M-^M0c0AbcM-MFE02fh3e4a5N"
```

### **Identifying the Encryption Method**
Upon reviewing the code, you determine that the encryption method used is **Rot47**. This knowledge is key to decoding the secret.

---

## **🔓 Decoding the Secret**

### **Using CyberChef to Decode**

1. **Visit CyberChef:**  
   The easiest way to decode Rot47 encryption is by using [CyberChef](https://gchq.github.io/CyberChef/), a web-based tool for various encoding/decoding tasks.

2. **Enter the Encrypted Key:**  
   Paste the encrypted string into CyberChef's input field.

3. **Apply the Rot47 Operation:**  
   In CyberChef, select the **Rot47** operation to decode the key.

4. **Retrieve the Decoded Key:**  
   The decoded key will be displayed as:
   ```text
   picoCTF{1|\/|_4_p34|\|ut_a79b6c2d}
   ```

---

## **📝 Mind Map of the Process**

```text
📁 Crackme_py CTF Challenge
 ├── 🗂️ Setup
 │   ├── Create Folder
 │   └── Download Program
 ├── 🔍 Analyze Script
 │   ├── Search for Encrypted Key
 │   └── Identify Encryption Method (Rot47)
 └── 🔓 Decode Secret
     ├── Use CyberChef
     ├── Enter Key
     ├── Apply Rot47
     └── Retrieve Decoded Key (picoCTF{1|\/|_4_p34|\|ut_a79b6c2d})
```

---

## **🎉 Final Thoughts**

By following these steps, you successfully cracked the code and retrieved the hidden key. Understanding how to identify and apply the correct decryption method, such as Rot47, is crucial in solving challenges like this. Well done! 🥳

---
```
