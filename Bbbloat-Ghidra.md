# **🛠️ Bbbloat-Ghidra CTF Challenge**

In this CTF challenge, worth 300 points, we dive into a tough reverse engineering task using the powerful tool, **Ghidra**.

---

## **🔍 Challenge Overview**
To tackle this challenge, follow these steps:

1. **Download the file:**  
   Use `wget <link of the file>` to download the challenge file.

2. **Grant Execution Permission:**  
   Make the file executable using `chmod +x bbbbloat` and confirm using `ls -l`.

3. **Run the File:**  
   Execute the file with `./bbbbloat`. The program will prompt, _"What is my favorite number?"_ Entering random values won’t work, as the answer is hidden within the binary.

---

## **⚙️ Setting Up Ghidra**

### **📥 Download Ghidra**

1. **Search & Download:**  
   Find the latest version of Ghidra and download it using:  
   ```bash
   wget <ghidra git hub link>
   ```

2. **Install Unzip:**  
   Install the unzip utility if not already installed:  
   ```bash
   sudo apt install unzip
   ```

3. **Unzip Ghidra:**  
   Unzip the Ghidra archive:  
   ```bash
   unzip ghidra_9.2.2_PUBLIC_20201229.zip
   ```

4. **Rename for Convenience:**  
   Rename the directory for easier command usage:  
   ```bash
   mv ghidra_9.2.2_PUBLIC_20201229 ghidra
   ```

5. **Run Ghidra:**  
   Attempt to run Ghidra:  
   ```bash
   ./ghidraRun
   ```
   If it prompts for JDK, install it with:  
   ```bash
   sudo apt install openjdk-17-jdk
   ```

---

## **🔧 Using Ghidra to Analyze the Binary**

### **1. Import the Binary**
   Open Ghidra and import the `bbbbloat` file to start inspecting the binary.

### **2. Define Strings**
   Navigate to **Window > Defined Strings** to locate familiar text such as the prompt, _"What’s your favorite number?"_  
   You'll see something like:  
   ```text
   What's_my_favorite_number?_00102004           XREF[1]:     FUN_00101307:001013cb(*)
   00102004 57 68 61        ds         "What's my favorite number? "
                74 27 73 
                20 
   ```

### **3. Examine the Function**
   Right-click the function to explore its code. The function looks something like this:

   ```c
   undefined8 FUN_00101307(void)
   {
     long in_FS_OFFSET;
     int local_48;
     undefined4 local_44;
     char *local_40;
     undefined8 local_38;
     undefined8 local_30;
     undefined8 local_28;
     undefined8 local_20;
     long local_10;

     local_10 = *(long *)(in_FS_OFFSET + 0x28);
     local_38 = 0x4c75257240343a41;
     local_30 = 0x3062396630664634;
     local_28 = 0x63633066635f3d33;
     local_20 = 0x4e5f6532636637;
     local_44 = 0xd2c49;
     printf("What's my favorite number? ");
     local_44 = 0xd2c49;
     __isoc99_scanf(&DAT_00102020,&local_48);
     local_44 = 0xd2c49;
     if (local_48 == 0x86187) {
       local_44 = 0xd2c49;
       local_40 = (char *)FUN_00101249(0,&local_38);
       fputs(local_40,stdout);
       putchar(10);
       free(local_40);
     } else {
       puts("Sorry, that's not it!");
     }
     if (local_10 != *(long *)(in_FS_OFFSET + 0x28)) {
                       /* WARNING: Subroutine does not return */
       __stack_chk_fail();
     }
     return 0;
   }
   ```

---

## **🚩 The Final Battle: Cracking the Code**

### **Extracting the Key**
Within the function, the critical value is `0x86187`. We need to convert this hexadecimal value to decimal.

- **Open Python in Ubuntu**:  
  Run `python3` and use the following to convert:
  ```python
  >>> print(0x86187)
  548231
  ```

### **Entering the Code**
Enter `548231` when prompted by the program, and you’ll receive the flag:  
`picoCTF{cu7_7h3_bl047_44f74a60}` 🎉

---

## **📌 Mind Map of the Process**

```text
📁 Bbbloat-Ghidra CTF Challenge
 ├── 🔍 Challenge Overview
 │   └── Download file, set permissions, run
 ├── ⚙️ Setting Up Ghidra
 │   ├── Download Ghidra
 │   ├── Install Unzip
 │   ├── Unzip Ghidra
 │   ├── Rename Directory
 │   └── Run Ghidra
 ├── 🔧 Using Ghidra
 │   ├── Import Binary
 │   ├── Define Strings
 │   └── Examine Function
 └── 🚩 Final Battle
     ├── Extract Key (Hex to Dec)
     └── Enter Code (Get Flag)
```

---

This guide provides a detailed and visually appealing walkthrough of the Bbbloat-Ghidra CTF challenge. Good luck with your reverse engineering journey! 🚀
```
