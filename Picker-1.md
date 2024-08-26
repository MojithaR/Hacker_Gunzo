# 🔓 **Picker I Reverse Engineering Challenge**

In this challenge, we are tasked with reverse engineering a service that provides a random number. However, the service offers additional functionalities that can be unlocked with the right input. Let's walk through the steps to solve this challenge! 🕵️‍♂️

---

## **🛠️ Step-by-Step Guide**

1. **Connect to the Service:**  
   Start by connecting to the provided service using `nc` (netcat):
   ```bash
   nc saturn.picoctf.net 52363
   ```

2. **Interact with the Service:**  
   Upon connection, the service will prompt you to enter a command. The primary function, `getRandomNumber`, returns the number `4`. Try entering:
   ```text
   getRandomNumber
   ```

3. **Discover Additional Functions:**  
   To explore other available functions, try the following commands:
   ```text
   win
   esoteric1
   esoteric2
   ```

   - The `win` function reveals a flag in hexadecimal format.
   - The `esoteric1` and `esoteric2` functions display some esoteric C code which is not directly relevant to the challenge but adds context.

4. **Decode the Flag:**  
   After running the `win` function, you'll receive a hexadecimal string. To decode this string into a readable format:
   - Copy the output:
     ```text
     0x70 0x69 0x63 0x6f 0x43 0x54 0x46 0x7b 0x34 0x5f 0x64 0x31 0x34 0x6d 0x30 0x6e 0x64 0x5f 0x31 0x6e 0x5f 0x37 0x68 0x33 0x5f 0x72 0x30 0x75 0x67 0x68 0x5f 0x62 0x35 0x32 0x33 0x62 0x32 0x61 0x31 0x7d
     ```
   - Use an online hex-to-text converter or tools like CyberChef to convert the hexadecimal string:
     - **CyberChef:** [CyberChef](https://gchq.github.io/CyberChef/)
     - Select "From Hex" to decode the flag.

5. **Retrieve the Flag:**  
   The decoded flag will be:
   ```text
   picoCTF{4_d14m0nd_1n_7h3_r0ugh_b523b2a1}
   ```

---

## **📝 Mind Map of the Process**

```text
🔓 Picker I Reverse Engineering Challenge
 ├── Connect to Service (nc)
 ├── Interact with Service (getRandomNumber, win, esoteric1, esoteric2)
 ├── Decode Hexadecimal Flag (CyberChef or similar tool)
 └── Retrieve Flag (picoCTF{4_d14m0nd_1n_7h3_r0ugh_b523b2a1})
```

---

## **🔑 Key Takeaways**

This challenge highlights the importance of exploring and interacting with different functions in a service. Understanding how to decode data and utilize tools for conversion are crucial skills in reverse engineering. 🛠️

---

**Happy Hacking!** 🚀
