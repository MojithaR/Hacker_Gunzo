# 🔓 **Unpackme Python Challenge**

In this challenge, we are tasked with unpacking a Python file to retrieve a flag. Let's break down the process step by step! 🕵️‍♂️

---

## **🛠️ Step-by-Step Guide**

1. **Download the Python File:**  
   Begin by downloading the provided Python code using the `wget` command:
   ```bash
   wget https://artifacts.picoctf.net/c/49/unpackme.flag.py
   ```

2. **Check and Set Permissions:**  
   Inspect the file permissions using:
   ```bash
   ls -l
   ```
   Then, grant full permissions to the file:
   ```bash
   chmod +x unpackme.flag.py
   ```

3. **Open the File:**  
   Initially, I tried using Sublime Text (`subl`), but it crashed. Instead, I switched to [Visual Studio Code](https://code.visualstudio.com/) for editing.

4. **Identify and Modify the Code:**  
   In the code, I encountered an unusual function:
   ```python
   exec(plain.decode())
   ```
   To better understand the code, I modified it by commenting out the `exec` line and added a `print` statement to reveal the decrypted message:
   ```python
   # exec(plain.decode())
   print(plain.decode())
   ```

5. **Run the Modified Code:**  
   After running the modified code, it prompts for a password. I used the following code snippet:
   ```python
   pw = input('What\'s the password? ')
   
   if pw == 'batteryhorse':
       print('picoCTF{175_chr157m45_cd82f94c}')
   else:
       print('That password is incorrect.')
   ```

6. **Retrieve the Flag:**  
   With the correct password, you’ll get the flag:
   ```text
   picoCTF{175_chr157m45_cd82f94c}
   ```

   Without modification, the script continually prompts for the password without decrypting the message.

---

## **📝 Mind Map of the Process**

```text
🔓 Unpackme Python Challenge
 ├── Download Python File (wget)
 ├── Check and Set Permissions (ls -l, chmod +x)
 ├── Open and Edit File (VS Code)
 ├── Modify Code to Reveal Flag (Replace exec with print)
 ├── Run Modified Code and Enter Password
 ├── Retrieve Flag (picoCTF{175_chr157m45_cd82f94c})
```

---

## **🔑 Key Takeaways**

This challenge emphasizes the importance of understanding code execution and modifying it to reveal hidden information. Mastery of file permissions and the ability to troubleshoot code are crucial skills in reverse engineering. 🔧

---

**Happy Unpacking!** 🚀
