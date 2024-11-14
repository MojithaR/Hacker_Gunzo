# **🔓 Morse Code CTF Challenge Walkthrough**

Welcome to the **Morse Code** challenge! This CTF task involves decoding an audio file containing Morse code to reveal a hidden flag. Let’s jump in and uncover the solution step-by-step! 🚀

---

## **📜 Challenge Overview**

Our task involves:
1. Downloading and analyzing an audio file containing Morse code.
2. Using an online Morse code decoder to convert the audio into readable text.
3. Formatting the decoded text according to the challenge requirements and submitting the answer.

---

## **🔧 Tools Needed**

1. **Morse Code Adaptive Audio Decoder**  
   - An online tool for decoding Morse code from audio files. [Link to tool](https://morsecode.world/international/decoder/audio-decoder-adaptive.html)

2. **Text Editor (Optional)**  
   - Any editor to help format and edit the decoded text as needed.

---

## **👣 Step-by-Step Guide**

### 1. **Download the Audio File**

First, start by downloading the provided `.wav` file containing the Morse code. Save the file in a convenient location.

- **Link to file:** Provided in the challenge.

### 2. **Upload the File to Morse Code Adaptive Audio Decoder**

Head over to the [Morse Code Adaptive Audio Decoder](https://morsecode.world/international/decoder/audio-decoder-adaptive.html). Upload the `.wav` file you downloaded:

1. Click the **Choose File** button on the website.
2. Select the `.wav` file from your saved location.
3. Start playing the file on the decoder to interpret the Morse code.

### 3. **Decode the Morse Code**

As the audio plays, the decoder will translate the Morse code into text. Here’s the flag in plain text that we obtained from the Morse code:

```plaintext
WH47 H47H 90D W20U9H7
```

### 4. **Format the Flag for Submission**

According to the challenge description, the flag format requires:
- Wrapping the decoded text in `picoCTF{}`
- Replacing spaces with underscores (`_`)
- Using all lowercase letters

With these instructions, format the decoded text as:

```plaintext
picoCTF{wh47_h47h_90d_w20u9h7}
```

🎉 **Flag Ready for Submission:**  
```
picoCTF{wh47_h47h_90d_w20u9h7}
```

---

## **📊 Visual Summary**

Here's a visual overview of the challenge process:

```text
🔍 Morse Code Challenge
 ├── Download the File
 ├── Upload to Decoder
 ├── Decode Audio
 ├── Format Flag
 └── Submit
```

---

## **📷 Demo of the Process**

Here’s a quick look at how we approach this type of challenge:

![Morse Code Decoder Demo](https://media.giphy.com/media/l44rfqXWyreAlJ01P2/giphy.gif?cid=790b7611dvdw28ha9f3aavaoraip4tu58l3rgzscdekdaq97&ep=v1_gifs_search&rid=giphy.gif&ct=g)

And here’s a demonstration of formatting the flag:

![Flag Formatting](https://media.giphy.com/media/pzrayLsEZ9LJAI3CP7/giphy.gif?cid=790b7611dvdw28ha9f3aavaoraip4tu58l3rgzscdekdaq97&ep=v1_gifs_search&rid=giphy.gif&ct=g)

---

## **🔑 Key Takeaways**

This challenge demonstrates how Morse code can be used in CTFs and the importance of using online tools effectively to decode hidden information in audio files. Understanding Morse code and decoding techniques is an essential skill in cryptographic challenges.

**Great work on decoding the Morse code challenge! Happy Hacking!** 😎
