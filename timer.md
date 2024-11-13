# **📱 APK Flag Hunt - CTF Challenge Walkthrough**

Welcome to the **APK Flag Hunt** challenge! In this Capture the Flag (CTF) challenge, we’ll analyze an APK file, `timer.apk`, to locate a hidden flag. The flag is cleverly hidden in the app’s metadata, disguised as a regular version attribute. Let’s break it down and retrieve the flag! 🚀

---

## **📜 Challenge Overview**

Our task is to analyze `timer.apk` and find the hidden flag. By decompiling the APK and inspecting its internal files, we’ll uncover the flag hidden within the `AndroidManifest.xml` file.

---

## **🔧 Tools Needed**

1. **jadx**  
   - `jadx` is an open-source tool used for decompiling APK files. It allows us to convert Dalvik bytecode into readable Java code and extract metadata, such as that in `AndroidManifest.xml`.
   - **Installation**: Download `jadx` from [GitHub](https://github.com/skylot/jadx) and follow the instructions to install it.

2. **Text Editor (Optional)**  
   - Any text editor like VSCode or Notepad++ will help open and inspect the extracted XML files.

---

## **👣 Step-by-Step Guide**

### 1. **Decompile the APK with `jadx`**  
   Start by decompiling the `timer.apk` file using `jadx`. Open a terminal or command prompt and run the following command:

   ```bash
   jadx -d output_folder timer.apk
   ```
   - This command extracts all files and folders from `timer.apk` into the specified `output_folder`.

### 2. **Locate and Open `AndroidManifest.xml`**  
   Navigate to the `output_folder` and find `AndroidManifest.xml`. Open this file to explore its contents, as it often contains valuable metadata about the app.

### 3. **Analyze `AndroidManifest.xml` to Find the Flag**  
   In `AndroidManifest.xml`, look for the `android:versionName` attribute. The flag is cleverly embedded here, formatted similarly to a regular version name:

   ```xml
   <?xml version="1.0" encoding="utf-8"?>
   <manifest xmlns:android="http://schemas.android.com/apk/res/android"
             android:versionCode="1"
             android:versionName="picoCTF{t1m3r_r3v3rs3d_succ355fully_17496}"
             android:compileSdkVersion="32"
             android:compileSdkVersionCodename="12"
             package="com.example.timer">
   ```
   - Here, we see the flag embedded as `picoCTF{t1m3r_r3v3rs3d_succ355fully_17496}` in the `android:versionName` field. 🎉

---

## **🚩 Retrieve the Flag**

Copy the value of `android:versionName`:

```
picoCTF{t1m3r_r3v3rs3d_succ355fully_17496}
```

This is your hidden flag! 🎉

---

## **📊 Visual Summary**

Here’s a quick summary of the steps:

```text
🔍 APK Analysis
 ├── Decompile APK using `jadx`
 ├── Open `AndroidManifest.xml`
 └── Retrieve Flag from `android:versionName`
```

---

## **📷 Demo (GIF)**

Here’s a quick look at how to approach this challenge:

![APK Flag Hunt Demo](https://i.giphy.com/media/v1.Y2lkPTc5MGI3NjExMXJubW9iNWRqM2Y1bGw4MDQ2dmtndHNoczY1d3N1NjRvaHF6N3oweSZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/hTlvdJNvg7vzrkjHtn/giphy.gif)

---

## **🛠️ Useful Tools and Resources**

| Tool        | Description                                                   |
|-------------|---------------------------------------------------------------|
| `jadx`      | Used to decompile APK files into readable Java code           |
| `AndroidManifest.xml` | Contains app metadata like versioning and permissions |

--- 

**Great job analyzing the APK! Good luck with your next CTF challenge! (Mojitha😎)**
