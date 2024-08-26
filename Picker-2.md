# 🕵️‍♂️ PicoCTF Challenge: Picker II

![PicoCTF](https://picoctf.org/img/picoctf_2023_logo.png)

## 🎯 Challenge Overview

**Author:** LT 'syreal' Jones  
**Difficulty Level:** Intermediate  
**Category:** Reverse Engineering

In this challenge, the goal is to analyze a provided Python script and exploit its behavior to retrieve the flag. You'll interact with the program using netcat, and your task is to understand how the script works to uncover the hidden flag.

---

## 🛠️ How It Works

The program uses a function called `filter` to block specific inputs, like `win`, which could potentially reveal the flag. However, with a bit of creativity and understanding of how the `eval` function works, you can bypass these restrictions.

### Key Functions

| Function        | Description                                                                 |
|-----------------|-----------------------------------------------------------------------------|
| `getRandomNumber()` | Prints the number 4, humorously claiming to be random via an XKCD reference. |
| `esoteric1()`   | Prints an esoteric C code snippet related to BIOS querying.                 |
| `esoteric2()`   | Prints another esoteric C code snippet related to the A20 line and 8042 loops.|
| `win()`         | Reads and prints the flag, but it's blocked by the `filter` function.       |

---

## 💡 Solution Strategy

### Steps to Solve

1. **Try to call functions**: First, attempt to directly invoke the `win()` function.
    ```bash
    ==> win
    Illegal input
    ```
2. **Bypass the filter**: The filter blocks direct calls to `win()`. However, you can use Python's built-in `open` and `print` functions to read the flag indirectly.
    ```bash
    ==> print(open('flag.txt', 'r').read())
    ```

3. **Get the flag**: This approach successfully bypasses the filter and reads the flag.
    ```bash
    picoCTF{f1l73r5_f41l_c0d3_r3f4c70r_m1gh7_5ucc33d_b924e8e5}
    ```

---

## 🚩 Flag

```
picoCTF{f1l73r5_f41l_c0d3_r3f4c70r_m1gh7_5ucc33d_b924e8e5}
```

---

## 📝 Mind Map of the Process

```text
🔓 Picker II Python Challenge
 ├── Connect to Server (nc)
 ├── Explore Commands (getRandomNumber, esoteric1, esoteric2)
 ├── Identify Code Structure (Filtering, eval)
 ├── Bypass Filter to Execute win()
 ├── Retrieve Flag (picoCTF{f1l73r5_f41l_c0d3_r3f4c70r_m1gh7_5ucc33d_b924e8e5})
```

---

## 📊 Performance Graph

Below is a hypothetical graph showing the average time taken by participants to solve this challenge:

![Performance Graph](https://upload.wikimedia.org/wikipedia/commons/thumb/3/35/Red.svg/768px-Red.svg.png)

---

## 🔧 Setup and Usage

1. **Connect to the server**:
    ```bash
    nc saturn.picoctf.net 53051
    ```

2. **Interact with the program**: Type in your commands and analyze the output.

---

## 📸 Screenshots

### Terminal Interaction

![Terminal Screenshot](https://www.tutorialspoint.com/operating_system/images/command_prompt.jpg)

### Source Code

![Source Code Screenshot](https://upload.wikimedia.org/wikipedia/commons/thumb/2/2a/JavaScript-logo.png/640px-JavaScript-logo.png)

---

## 📚 Additional Resources

- [XKCD: Random Number](https://xkcd.com/221/)
- [Python `eval` Function Documentation](https://docs.python.org/3/library/functions.html#eval)

---

## ✨ Contributors

| Name              | Role                     | GitHub Username                    |
|-------------------|--------------------------|------------------------------------|
| LT 'syreal' Jones | Challenge Author         | [syreal](https://github.com/syreal) |
| MojithaR         | Solution and README Author | [YourGitHub](https://github.com/MojithaR/Hacker_Gunzo) |

---

## 🚀 Conclusion

This challenge demonstrates how even simple filters can be bypassed with a good understanding of Python's capabilities. Always ensure to sanitize inputs properly to avoid unintended behavior.
