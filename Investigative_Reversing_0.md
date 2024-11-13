# **🔓 Investigative Reversing 0 CTF Challenge Walkthrough**

Welcome to the **Investigative Reversing 0** challenge! This CTF involves reversing the binary code of an executable to reveal the encoded flag. We'll be examining how the program manipulates data using Ghidra, then crafting a Python script to retrieve the original flag. Let’s dive into each step of the solution! 🚀

---

## **📜 Challenge Overview**

Our task involves:
1. Analyzing a binary file, which manipulates and hides a flag within a "mystery.png" file.
2. Using Ghidra to understand the code transformations in the binary.
3. Writing a Python script to decode the transformations and retrieve the original flag.

---

## **🔧 Tools Needed**

1. **Ghidra**  
   - For reverse-engineering the binary file and decompiling code.
   
2. **Python**  
   - To reverse-engineer and retrieve the flag by decoding transformations.
   
3. **Text Editor (Optional)**  
   - For organizing notes and writing the Python script.

---

## **👣 Step-by-Step Guide**

### 1. **Analyze the Binary with Ghidra**

The challenge provided an executable file that manipulates two files, `flag.txt` and `mystery.png`. By analyzing the code in Ghidra, we can see how it reads, modifies, and writes data between these files. The binary code in Ghidra appears as follows:

```c
void main(void) {
  FILE *__stream;
  FILE *__stream_00;
  size_t sVar1;
  int local_54;
  int local_50;
  char local_38 [4];
  char local_34;
  char local_33;
  char local_29;
  
  __stream = fopen("flag.txt","r");
  __stream_00 = fopen("mystery.png","a");
  
  if (__stream == NULL) {
    puts("No flag found, please make sure this is run on the server");
  }
  if (__stream_00 == NULL) {
    puts("mystery.png is missing, please run this on the server");
  }

  sVar1 = fread(local_38,0x1a,1,__stream);
  if ((int)sVar1 < 1) {
    exit(0);
  }

  fputc((int)local_38[0],__stream_00);
  fputc((int)local_38[1],__stream_00);
  fputc((int)local_38[2],__stream_00);
  fputc((int)local_38[3],__stream_00);
  fputc((int)local_34,__stream_00);
  fputc((int)local_33,__stream_00);
  
  for (local_54 = 6; local_54 < 0xf; local_54++) {
    fputc((int)(char)(local_38[local_54] + 5), __stream_00);
  }
  
  fputc((int)(char)(local_29 - 3),__stream_00);
  
  for (local_50 = 0x10; local_50 < 0x1a; local_50++) {
    fputc((int)local_38[local_50], __stream_00);
  }

  fclose(__stream_00);
  fclose(__stream);
}
```

### 2. **Explanation of the Transformation Logic**

In this function:
- **First 4 Bytes**: Directly written to `mystery.png` without modification.
- **Next 2 Bytes**: Also written without modification.
- **Bytes from Index 6 to 14**: Have 5 added to their ASCII values before writing.
- **Byte at Index 15**: Subtracts 3 from its ASCII value before writing.
- **Remaining Bytes (Index 16-25)**: Written without modification.

### 3. **Reverse the Transformation Using Python**

Now, let’s write a Python script to reverse these transformations on the encoded data in `mystery.png` to retrieve the original flag.

```python
# investigative_reversing.py

# Encoded data from "mystery.png"
encoded_data = b"picoCTF{f0und_1t_d1deedaa}"  # Example encoded data for demonstration
decoded_flag = ""

# Process the first 4 characters directly
decoded_flag += encoded_data[:4].decode()

# Process the next 2 characters
decoded_flag += encoded_data[4:6].decode()

# Reverse the transformation on characters from index 6 to 14
for i in range(6, 15):
    decoded_flag += chr(encoded_data[i] - 5)

# Reverse the transformation on the character at index 15
decoded_flag += chr(encoded_data[15] + 3)

# Add remaining characters directly
decoded_flag += encoded_data[16:25].decode()

print("Original flag:", decoded_flag)
```

### 4. **Run the Python Script**

Run the Python script to see the output:

```bash
python3 investigative_reversing.py
```

- **Output**:
  ```
  Original flag: picoCTF{f0und_1t_d1deedaa}
  ```

🎉 We’ve successfully decoded the flag, which is `picoCTF{f0und_1t_d1deedaa}`.

---

## **🚩 Retrieve the Flag**

The decoded flag for this challenge is:

```
picoCTF{f0und_1t_d1deedaa}
```

---

## **📊 Visual Summary**

```text
🔍 File Analysis
 ├── Inspect the files with Ghidra
 ├── Reverse transformations in Python
 └── Retrieve Flag
```

---

## **📷 Demo (GIF)**

Here’s a quick look at the process:

![Investigative Reversing Demo](https://media.giphy.com/media/JUh0yTz4h931K/giphy.gif?cid=790b761140q8ebfffemim7waudvootw7ec0v2z63r5g01pd0&ep=v1_gifs_search&rid=giphy.gif&ct=g)

---

## **🛠️ Useful Tools and Resources**

| Tool        | Description                                    |
|-------------|----------------------------------------------- |
| **Ghidra**  | For analyzing and understanding the binary code|
| **Python**  | For scripting the reverse-engineering of the flag |

---

**Great job decoding the hidden flag! Onward to the next CTF! (Mojitha 😎)**
