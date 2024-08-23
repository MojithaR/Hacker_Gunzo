# **🚀 File Run 2 Challenge**

In this challenge, we will explore how to execute a file with specific command-line arguments to uncover a hidden flag. Let’s get started! 🎯

---

## **🗂️ Step-by-Step Guide**

1. **Download the File:**  
   Begin by downloading the required file using the `wget` command:  
   ```bash
   wget https://artifacts.picoctf.net/c/156/run
   ```

2. **Create a New Directory:**  
   For better organization, create a new directory and move the downloaded file into it:  
   ```bash
   mkdir file_run2
   mv run file_run2/
   ```

3. **Set File Permissions:**  
   Make the file executable by granting it the necessary permissions using the `chmod` command:  
   ```bash
   chmod +x file_run2/run
   ```

4. **Run the File with a Special Command:**  
   To execute the file, it requires a special command-line argument `"Hello!"`. Run the file as follows:  
   ```bash
   ./file_run2/run Hello!
   ```

5. **Extract the Flag:**  
   After running the file, extract the hidden flag using `grep` to search for the specific pattern:  
   ```bash
   ./file_run2/run 'Hello!' | grep -oE 'picoCTF{.*}'
   ```
   **Flag Found:**  
   The flag revealed is:  
   ```text
   picoCTF{F1r57_4rgum3n7_96f2195f}
   ```

---

## **📝 Mind Map of the Process**

```text
📁 File Run 2 Challenge
 ├── Download the File (wget)
 ├── Create Directory (mkdir)
 ├── Move File to Directory (mv)
 ├── Set Permissions (chmod +x)
 ├── Run the File with Argument (./run Hello!)
 └── Extract the Flag (grep -oE)
```

---

## **🔑 Key Takeaways**

This challenge highlights the importance of command-line arguments in executing programs and demonstrates how to manipulate files and extract crucial data in a terminal environment. Mastering these techniques is essential for reverse engineering and cybersecurity. 🛡️

---

**Happy Hacking!** 😎
