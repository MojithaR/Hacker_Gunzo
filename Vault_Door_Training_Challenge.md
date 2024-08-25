# **🔐 Vault Door Training Challenge**

Welcome to the **Vault Door Training** challenge! In this challenge, we'll reverse-engineer a Java program to uncover the hidden password and gain access to the vault. Let’s dive in! 🌟

---

## **📜 Overview**

This challenge involves analyzing a Java program to understand its logic and extract the correct password to unlock the vault.

---

## **🗂️ Step-by-Step Guide**

1. **Download the Source Code:**  
   Start by downloading the Java source code file:
   ```bash
   wget https://jupiter.challenges.picoctf.org/static/03c960ddcc761e6f7d1722d8e6212db3/VaultDoorTraining.java
   ```

2. **Examine the Code:**
   Open the `VaultDoorTraining.java` file to examine its content. The password validation logic is implemented in the `checkPassword` method.

3. **Compile the Java File:**  
   Compile the Java file using the following command:
   ```bash
   javac VaultDoorTraining.java
   ```

4. **Run the Program:**  
   Execute the compiled Java program:
   ```bash
   java VaultDoorTraining
   ```

5. **Enter the Password:**  
   When prompted, enter the full password to gain access:
   ```text
   picoCTF{w4rm1ng_Up_w1tH_jAv4_3808d338b46}
   ```

6. **Access Granted! 🎉**

---

## **📝 Code Breakdown**

Here’s a snippet of the core logic that handles password validation:

```java
public boolean checkPassword(String password) {
    return password.equals("w4rm1ng_Up_w1tH_jAv4_3808d338b46");
}
```

The program checks if the input password matches the hardcoded string. If it does, access is granted.

---

## **📊 Process Mind Map**

```text
🔐 Vault Door Training Challenge
 ├── Download Java Source Code (wget)
 ├── Examine Source Code (vim/nano)
 ├── Compile Java Code (javac)
 ├── Run Java Program (java)
 └── Enter the Password (picoCTF{...})
```

---

## **🧠 Key Insights**

- **Reverse Engineering:** Understanding the code and how it handles input is crucial for solving challenges like this.
- **Security Concerns:** Hardcoding passwords in source code is a significant security risk. Always consider more secure methods for password handling.
- **Java Fundamentals:** This challenge reinforces basic Java concepts like string manipulation, method invocation, and console input/output.

---

## **🎬 Demo**

![Vault Door Training Demo](https://media.giphy.com/media/3o7aD6flgjhR2FzNSU/giphy.gif)

---

## **🛠️ Useful Commands**

| Command                     | Description                                |
|-----------------------------|--------------------------------------------|
| `wget`                      | Download files from the web                |
| `javac VaultDoorTraining.java` | Compile the Java source file              |
| `java VaultDoorTraining`    | Run the compiled Java class                |
| `vim VaultDoorTraining.java`| Open the Java file for editing/examination |

---

**Happy Hacking!** 😎
