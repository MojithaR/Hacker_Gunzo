# **🔍 GDB Test Drive**

In this guide, we'll explore how to use the GNU Debugger (GDB) to analyze and manipulate a binary program, ultimately uncovering a hidden CTF flag. Let’s dive in! 🚀

---

## **🛠️ Step-by-Step Guide**

1. **List Files and Directories:**  
   Start by listing the files and directories in the current location:  
   ```bash
   ls
   ```

2. **Navigate to the Correct Directory:**  
   Use the `cd` command to move to the `GDB_test-drive` directory:  
   ```bash
   cd reverse_engineering
   cd GDB_test-drive
   ```

3. **List Files Again:**  
   Confirm the contents of the directory by listing the files:  
   ```bash
   ls
   ```

4. **View Detailed File Information:**  
   Get detailed information about the files, including permissions, owner, size, and modification time:  
   ```bash
   ls -l
   ```
   Example output:  
   ```text
   -rwxr-xr-x 1 ubuntu ubuntu 17048 Aug  5 01:55 gdbme
   ```

5. **Attempt to Execute the Program:**  
   Try running the `gdbme` program:  
   ```bash
   ./gdbme
   ```
   If the program seems to hang, it's time to debug it.

6. **Install GDB:**  
   If GDB is not installed, do so using the following commands:  
   ```bash
   sudo apt install -y gdb
   sudo apt update
   ```
   **GDB** is a powerful debugger that allows us to inspect the program's execution.

7. **Start GDB and Load the Program:**  
   Begin debugging by loading the `gdbme` program into GDB:  
   ```bash
   gdb ./gdbme
   ```

8. **Configure GDB Interface:**  
   Use the `layout asm` command to display the assembly code interface in GDB:  
   ```bash
   (gdb) layout asm
   ```

9. **Identify the Sleep Function:**  
   Notice that the program is likely hanging at the `sleep` function, indicated by the line `(main+99)`.

10. **Set a Breakpoint:**  
    Stop the program at the sleep function by setting a breakpoint:  
    ```bash
    (gdb) break *(main+99)
    ```

11. **Run the Program:**  
    Execute the program again from the beginning:  
    ```bash
    (gdb) run
    ```

12. **Jump Past the Sleep Function:**  
    Since no flag is shown, the issue may lie in the program's later part. Skip the sleep function and jump to the next location:  
    ```bash
    (gdb) jump *(main+104)
    ```

13. **Reveal the Flag:**  
    The program now runs the latter part, revealing the CTF flag.

---

## **📝 Mind Map of the Process**

```text
🔍 GDB Test Drive
 ├── List Files and Directories (ls)
 ├── Navigate to the Directory (cd)
 ├── List Files Again (ls)
 ├── View Detailed Information (ls -l)
 ├── Attempt to Execute (./gdbme)
 ├── Install GDB (sudo apt install -y gdb)
 ├── Start GDB (gdb ./gdbme)
 ├── Configure GDB Interface (layout asm)
 ├── Identify Sleep Function (main+99)
 ├── Set a Breakpoint (break *(main+99))
 ├── Run the Program (run)
 ├── Jump Past Sleep (jump *(main+104))
 └── Reveal the Flag (grep -oE 'picoCTF{.*}')
```

---

## **🔑 Key Takeaways**

This challenge demonstrates how to effectively use GDB to debug a binary program, manipulate its execution flow, and extract crucial information like a CTF flag. Understanding these techniques is essential for anyone interested in reverse engineering and cybersecurity. 🛡️

---

**Happy Debugging!** 🐞
