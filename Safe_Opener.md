# 🔓 **Safe Opener Challenge**

In this challenge, our goal is to crack the code and open the safe! Let’s break it down step by step. 🚀

---

## **🛠️ Step-by-Step Guide**

1. **Download the SafeOpener File:**  
   Start by downloading the Java file using the `wget` command:
   ```bash
   wget https://artifacts.picoctf.net/c/83/SafeOpener.java
   ```

2. **Open the Java File:**  
   Since Sublime Text isn’t working for this file, open it using VS Code:
   ```bash
   code SafeOpener.java
   ```

3. **Give Execution Permission:**  
   Before running the Java file, ensure it has the necessary permissions:
   ```bash
   chmod +x SafeOpener.java
   ```

4. **Analyze the Java Code:**  
   The Java code provides an encoded key using `Base64`:
   ```java
   String encodedKey = "cGwzYXMzX2wzdF9tM18xbnQwX3RoM19zYWYz";
   ```
   This key needs to be decoded to reveal the secret code.

5. **Experiment with Base64 Encoding & Decoding:**  
   To understand how Base64 works, let's try encoding and decoding some sample data.

   **Encoding:**
   ```bash
   echo 'Tiyhira mojitha ranasingha' | base64
   ```
   Output:
   ```text
   VGl5aGlyYSBtb2ppdGhhIHJhbmFzaW5naGEK
   ```

   ```bash
   echo 'we can do this!' | base64
   ```
   Output:
   ```text
   d2UgY2FuIGRvIHRoaXMhCg==
   ```

   **Decoding:**
   ```bash
   echo 'cGxlYXNlIHN1bnNjcmliZQo=' | base64 -d
   ```
   Output:
   ```text
   please subscribe
   ```

   ```bash
   echo 'd2UgY2FuIGRvIHRoaXMhCg==' | base64 -d
   ```
   Output:
   ```text
   we can do this!
   ```

6. **Decode the Provided Key:**  
   Now, decode the provided `encodedKey` using the same Base64 decoding method:
   ```bash
   echo 'cGwzYXMzX2wzdF9tM18xbnQwX3RoM19zYWYz' | base64 -d
   ```
   Output:
   ```text
   pl3as3_l3t_m3_1nt0_th3_saf3
   ```

7. **Format the Decoded Key:**  
   For convenience, format the decoded key into the final flag format:
   ```bash
   echo "picoCTF{$(echo 'cGwzYXMzX2wzdF9tM18xbnQwX3RoM19zYWYz' | base64 -d ) } "
   ```
   Output:
   ```text
   picoCTF{pl3as3_l3t_m3_1nt0_th3_saf3}
   ```

---

## **📝 Mind Map of the Process**

```text
🔓 Safe Opener Challenge
 ├── Download Java File (wget)
 ├── Open File in VS Code (code)
 ├── Set Permissions (chmod +x)
 ├── Analyze Java Code (Base64 encoded key)
 ├── Experiment with Base64 Encoding/Decoding
 │    ├── Encode Samples
 │    ├── Decode Samples
 ├── Decode Provided Key (Base64 -d)
 ├── Format Final Flag (picoCTF{...})
 └── Display Flag (picoCTF{pl3as3_l3t_m3_1nt0_th3_saf3})
```

---

## **🔑 Key Takeaways**

This challenge highlights the process of decoding Base64 encoded strings, understanding Java code, and constructing the final flag format. It's a great example of applying basic encoding knowledge in a practical scenario. 🧠

---

**Happy Cracking!** 🔓
