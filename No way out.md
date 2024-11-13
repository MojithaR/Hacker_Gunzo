# **🕹️ No Way Out - PicoCTF Challenge Walkthrough**

Welcome to the **No Way Out** challenge! In this PicoCTF challenge, our goal is to locate and retrieve the hidden flag from within a Windows game environment. We’ll utilize advanced tools to bypass the game’s restrictions, allowing us to reach otherwise inaccessible areas. Ready to break some walls? Let’s dive in! 🚀

---

## **📜 Challenge Overview**

This challenge provides a Windows game where we can see a flag on a high pole outside the playable area. However, invisible walls prevent us from reaching it directly. Our task is to locate and modify game code to bypass these limitations and access the flag.

### **Challenge Steps**:
1. Download the game and unzip it using the password: `picoctf`.
2. Run the game to analyze the layout and observe the restrictions.
3. Use DnSpy, a tool for inspecting and modifying .NET code, to adjust the game files and overcome its limitations.

---

## **🔧 Tools Needed**

1. **DnSpy**  
   - DnSpy is an open-source debugger and .NET assembly editor. We’ll use it to modify the game code and allow unrestricted movement.
   - **Installation**: Download DnSpy from [GitHub](https://github.com/dnSpyEx/dnSpy/releases).
   - Once installed, open DnSpy and load the game’s `.dll` files to locate the code sections we want to modify.

---

## **👣 Step-by-Step Guide**

1. **Analyze the Game**:  
   Start the game and explore the environment. Observe any barriers that block movement toward the flag. In this challenge, we note that the flag is on a high pole, outside of the accessible play area.

2. **Locate the Relevant Code with DnSpy**:  
   Open DnSpy and load the game’s `.dll` files. Navigate to `Assembly-Csharp` > `Evolve Games` > `PlayerControls` > `Update`.

3. **Code Modifications to Bypass Limitations**:

    ### Original Code and Modifications
    
    #### 1. **Gravity and Movement Restrictions**
    
    **Original Code**:
    ```csharp
    if (!this.characterController.isGrounded && !this.isClimbing)
    {
        this.moveDirection.y = this.moveDirection.y - this.gravity * Time.deltaTime;
    }
    ```
    
    **Explanation**:
   - This original code creates a gravity effect when the character is in the air. Gravity pulls the player down, making it harder to jump high enough to reach the flag.
   
    **New Code**:
    ```csharp
    if (Input.GetKeyDown(KeyCode.E))
    {
        this.moveDirection.y = 0f; // Instantly stop downward movement
    }
    if (Input.GetKeyDown(KeyCode.R))
    {
        this.moveDirection.y = -this.jumpSpeed; // Quickly move downward
    }
    ```
    
    **Explanation**:
   - **`Input.GetKeyDown(KeyCode.E)`** stops gravity by setting `moveDirection.y` to 0.
   - **`Input.GetKeyDown(KeyCode.R)`** allows controlled descent with `moveDirection.y = -this.jumpSpeed`.
   - With these controls, you can pause in mid-air and control descent, making it easier to reach the flag.

    #### 2. **Unrestricted Jumping**

    **Original Code**:
    ```csharp
    if (Input.GetButton("Jump") && this.canMove && this.characterController.isGrounded && !this.isClimbing)
    {
        this.moveDirection.y = this.jumpSpeed;
    }
    else
    {
        this.moveDirection.y = y;
    }
    ```
    
    **Explanation**:
   - This code allows jumping only when on the ground, preventing us from jumping over obstacles.
   
    **New Code**:
    ```csharp
    if (Input.GetButton("Jump"))
    {
        this.moveDirection.y = this.jumpSpeed;
    }
    ```
    
    **Explanation**:
   - By removing restrictions, this code enables jumping even in mid-air. This allows us to jump over invisible walls, making it easier to reach the target.

---

## **🚩 Finding the Flag**

After making these modifications, load the game and try the new jump and gravity controls. Using these controls, you should be able to reach the area where the flag is displayed. Once you access the flag, you’ll see the following:

   **Flag**: `picoCTF{WELCOME_TO_UNITY!!}`

---

## **📊 Visual Summary**

Here’s a visual representation of the steps and logic:

```text
🎮 Game Analysis
 ├── Observe Boundaries (Flag inaccessible)
 ├── Use DnSpy to Modify Code
 ├── Implement Gravity Control (Key E/R)
 ├── Enable Mid-Air Jump (Remove Jump Conditions)
 └── Reach the Flag and Retrieve Flag Code
```

 **🎬 Demo (GIFs)**

### **Gravity Control with `E` and `R`**:
![Gravity Control]([https://example.com/path-to-gravity-gif](https://media.giphy.com/media/goKgmdgnBfbYhsZFy9/giphy.gif?cid=790b7611d1n2cuhmxcqnows76i3jhcyot92a6v028zqgxphu&ep=v1_gifs_search&rid=giphy.gif&ct=g))

### **Unrestricted Jump Over Boundaries**:
![Unrestricted Jump](https://example.com/path-to-jump-gif)

---

## **🛠️ Useful Commands and Resources**

| Tool            | Description                                      |
|-----------------|--------------------------------------------------|
| `DnSpy`         | Used to inspect and modify the game’s code files |
| `Input.GetKeyDown` | Detects specific key presses for precise control |

---

**Enjoy exploring the reverse engoo! Good luck, and happy hacking! (Mojitha😎)**

