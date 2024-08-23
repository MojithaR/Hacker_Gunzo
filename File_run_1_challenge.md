# **🚀 File Run 1 Challenge**

In this challenge, we’ll execute a series of steps to extract a hidden flag from a file. Let’s dive right in! 🎯

---

## **🗂️ Step-by-Step Guide**

1. **Download the File:**  
   Start by downloading the required file using the `wget` command:  
   ```bash
   wget <link to the file>
   ```

2. **Create a New Directory:**  
   Organize your workspace by creating a new directory and moving the downloaded file into it:  
   ```bash
   mkdir file_run1
   mv <Txt file name> file_run1/
   ```

3. **Set File Permissions:**  
   To execute the file, you need to make it executable. Grant the necessary permissions using the `chmod` command:  
   ```bash
   chmod +x file_run1/<filename>
   ```

4. **Run the File:**  
   Now, execute the file with the following command:  
   ```bash
   ./file_run1/<filename>
   ```

5. **Extract the Flag:**  
   After running the file, extract the flag using a `grep` command to search for the specific pattern:  
   ```bash
   ./file_run1/<filename> | grep -oE 'picoCTF{.*}'
   ```
   **Flag Found:**  
   The flag revealed is:  
   ```text
   picoCTF{U51N6_Y0Ur_F1r57_F113_9bc52b6b}
   ```

---

## **📝 Mind Map of the Process**

```text
📁 File Run 1 Challenge
 ├── Download the File (wget)
 ├── Create Directory (mkdir)
 ├── Move File to Directory (mv)
 ├── Set Permissions (chmod +x)
 ├── Run the File (./run)
 └── Extract the Flag (grep -oE)
```

---

## **🔑 Key Takeaways**

This challenge demonstrates how to work with files in a terminal environment, including setting permissions and extracting specific data using commands like `grep`. Understanding these fundamental operations is essential in cybersecurity and reverse engineering. 🛠️

---

**Happy Hacking!** 😎
```
