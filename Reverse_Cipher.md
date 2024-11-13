# **🔓 Reverse Cipher CTF Challenge Walkthrough**

Welcome to the **Reverse Cipher** challenge! This CTF involves analyzing a binary file `rev` and a text file `rev_this`. By examining the binary code with a tool like Ghidra, we can uncover the cryptographic transformations applied to the flag and reverse them to obtain the original text. Let’s dive into each step of the solution! 🚀

---

## **📜 Challenge Overview**

Our task involves:
1. Examining the files `rev` (executable) and `rev_this` (containing an encoded flag).
2. Using Ghidra to analyze the cryptographic transformations applied within the binary.
3. Writing a Python script to reverse these transformations and obtain the original flag.

---

## **🔧 Tools Needed**

1. **Ghidra**  
   - A powerful reverse-engineering tool for disassembling and analyzing executable files.
   
2. **Python**  
   - For decoding the flag by reversing the cryptographic transformations.
   
3. **Text Editor (Optional)**  
   - Any editor for writing and organizing code snippets.

---

## **👣 Step-by-Step Guide**

### 1. **Inspect Files with Ghidra**

First, we try to understand the files provided:

- **rev**: an executable file. Running it returns a segmentation fault if it doesn’t detect a flag.
- **rev_this**: a text file with an encoded string resembling a flag format.

Using Ghidra, we disassembled `rev` to understand the transformations in the flag’s encoding. The `main` function in Ghidra contained the following logic:

```c
void main(void) {
  size_t sVar1;
  char local_58 [23];
  char local_41;
  int local_2c;
  FILE *local_28;
  FILE *local_20;
  uint local_14;
  int local_10;
  char local_9;
  
  // Open "flag.txt" for reading and "rev_this" for appending
  local_20 = fopen("flag.txt","r");
  local_28 = fopen("rev_this","a");

  // Error handling if the files can't be opened
  if (local_20 == (FILE *)0x0) {
    puts("No flag found, please make sure this is run on the server");
  }
  if (local_28 == (FILE *)0x0) {
    puts("please run this on the server");
  }

  // Read 0x18 (24) bytes from "flag.txt" into local_58 buffer
  sVar1 = fread(local_58,0x18,1,local_20);
  local_2c = (int)sVar1;

  // If less than 1 byte read, exit
  if ((int)sVar1 < 1) {
    exit(0);
  }

  // Process the first 8 characters directly
  for (local_10 = 0; local_10 < 8; local_10 = local_10 + 1) {
    local_9 = local_58[local_10];
    fputc((int)local_9,local_28);
  }

  // Process the remaining characters
  for (local_14 = 8; (int)local_14 < 0x17; local_14 = local_14 + 1) {
    if ((local_14 & 1) == 0) {
      local_9 = local_58[(int)local_14] + '\x05';  // Add 5 to even indices
    } else {
      local_9 = local_58[(int)local_14] - 2;       // Subtract 2 from odd indices
    }
    fputc((int)local_9,local_28);
  }

  // Append the last character
  local_9 = local_41;
  fputc((int)local_41,local_28);

  fclose(local_28);
  fclose(local_20);
  return;
}
```

### 2. **Explanation of the Transformation Logic**

The code applies specific transformations to characters in the `flag.txt` file:

- **First 8 Characters**: Written to `rev_this` without any modification.
- **Remaining Characters**: Each character is altered as follows:
  - If the character index is even, it adds 5 to the ASCII value.
  - If the character index is odd, it subtracts 2 from the ASCII value.
- **Last Character**: Appended without modification.

### 3. **Reverse the Transformation Using Python**

Now that we understand the transformation, let’s write a Python script to reverse it. This will allow us to decode the scrambled flag in `rev_this`.

```python
# Reverse_cipher.py

# Encoded flag from "rev_this" file
encoded_flag = "picoCTF{w1{1wq85jc=2i0<}"
decoded_flag = ""

# Loop over each character in the encoded flag
for i, char in enumerate(encoded_flag):
    if i < 8:  # First 8 characters remain the same
        decoded_flag += char
    else:
        # Reverse the encoding logic
        if i % 2 == 0:
            decoded_flag += chr(ord(char) - 5)  # Subtract 5 from even indices
        else:
            decoded_flag += chr(ord(char) + 2)  # Add 2 to odd indices

# Print the decoded flag
print("Original flag:", decoded_flag)
```

### 4. **Run the Python Script**

Run the Python script to see the output:

```bash
python3 Reverse_cipher.py
```

- **Output**:
  ```
  Original flag: picoCTF{r3v3rs37ee84d27}
  ```

🎉 The original flag is successfully decoded as `picoCTF{r3v3rs37ee84d27}`.

---

## **🚩 Retrieve the Flag**

The decoded flag for this challenge is:

```
picoCTF{r3v3rs37ee84d27}
```

---

## **📊 Visual Summary**

Here's a quick summary of the steps:

```text
🔍 File Analysis
 ├── Inspect the files with Ghidra
 ├── Reverse transformations in Python
 └── Retrieve Flag
```

---

## **📷 Demo (GIF)**

Here’s a quick look at how to approach this challenge:

![Reverse Cipher Demo](https://media.giphy.com/media/v1.Y2lkPTc5MGI3NjExM2U3cmloZ2lyc3N0ejRhZ3Y4ZGtueDMyZDBjc3ozZjA5aDZpaHZmdiZlcD12MV9naWZzX3NlYXJjaCZjdD1n/DkBg9APfhI6X4Jhtlu/giphy.gif)

---

## **🛠️ Useful Tools and Resources**

| Tool        | Description                                    |
|-------------|----------------------------------------------- |
| **Ghidra**  | Used to disassemble and understand binary code |
| **Python**  | Scripted to reverse-engineer the flag’s encoding|

---

**Excellent work decoding the Reverse Cipher! Best of luck with your next CTF challenge! (Mojitha 😎)**
