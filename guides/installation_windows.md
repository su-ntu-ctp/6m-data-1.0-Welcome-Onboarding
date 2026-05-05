# 🪟 Installation Guide — Windows

This guide will walk you through installing all the software you need for this course, **one step at a time**. Each section ends with a **✅ Checkpoint** so you can confirm everything worked before moving on.

> ⚠️ **Windows ARM users (e.g. Snapdragon X laptops):** This guide works for you too, but pay attention to the notes marked **[ARM]** — a few download links and commands are slightly different.

---

## 📋 Before You Begin — Hardware & OS Check

**Minimum requirements:**
- Windows 10 (version 2004 or later) or Windows 11
- 16 GB RAM recommended
- 50 GB free storage space
- A working webcam and microphone for Zoom sessions

**How to check your Windows version:**
1. Press the **Windows key** on your keyboard (the key with the Windows logo ⊞)
2. Type `winver` and press **Enter**
3. A small window will pop up showing your Windows version

> ✅ **Checkpoint 0:** You should see "Windows 10" or "Windows 11" and a build number of **2004 or higher** (e.g. 22H2, 23H2, 24H2). If your version is older, please contact your instructor before continuing.

---

## Step 1 — Install WSL (Windows Subsystem for Linux)

WSL lets you run Linux (a different operating system) inside Windows. Most data science tools were originally built for Linux, so we install WSL to get the best experience.

**This step has two parts: first we install the WSL system, then we reboot and install Ubuntu (a type of Linux).**

### Part A: Install WSL

1. Click the **Windows search bar** at the bottom of your screen (or press ⊞ + S)
2. Type `PowerShell`
3. You will see **Windows PowerShell** in the results — **right-click** on it
4. Click **"Run as administrator"**
5. A blue/dark window will open — this is PowerShell. Click **Yes** if Windows asks for permission
6. Type the following command exactly and press **Enter**:

```
wsl --install
```

7. You will see text scrolling on the screen as WSL installs. This may take 2–5 minutes. Wait until it stops and you see a message saying installation is complete.

> ⚠️ You may see a message saying **"Virtual Machine Platform"** is being installed. This is normal.

8. When the installation finishes, **restart your computer** (Start menu → Power → Restart)

### Part B: Install Ubuntu (after rebooting)

1. After your computer restarts, open **PowerShell as administrator** again (same steps as above)
2. Type the following and press **Enter**:

```
wsl --install
```

3. This time, Ubuntu (a version of Linux) will begin installing. You will be asked to:
   - **Create a username** — choose something simple with no spaces (e.g. `john` or `myname`)
   - **Create a password** — type a password and press Enter. **Note: you won't see any characters appear as you type — this is normal for security reasons.** Type it carefully and press Enter.
   - **Confirm the password** — type it again and press Enter

> ✅ **Checkpoint 1:** After setting your username and password, you should see a command prompt that looks like this:
> ```
> username@COMPUTERNAME:~$
> ```
> This green or white text prompt means Ubuntu is running successfully inside Windows. 🎉
>
> If you see an error instead, refer to the [WSL Troubleshooting Guide](install_wsl.md) or contact your instructor.

---

## Step 2 — Update Ubuntu

Just like Windows Update, Linux needs to be kept up to date. Let's do that now.

1. In the Ubuntu/WSL window that is open (the one showing `username@COMPUTERNAME:~$`), type the following and press **Enter**:

```bash
sudo apt update
```

2. It will ask for your **Linux password** (the one you just created). Type it and press Enter — again, you won't see any characters appear. Press Enter when done.

3. Text will scroll by showing a list of updates. Wait for it to finish.

4. Now type the following and press **Enter**:

```bash
sudo apt upgrade
```

5. It may ask `Do you want to continue? [Y/n]` — type `Y` and press **Enter**
6. Wait for the upgrade to complete (this can take a few minutes)

> ✅ **Checkpoint 2:** When the update finishes, you will be returned to the command prompt (`username@COMPUTERNAME:~$`) with no error messages. If you see errors in red, take a screenshot and contact your instructor.

---

## Step 3 — Install Miniconda

Miniconda manages Python and all the software packages we use in this course. It lets us create separate "environments" for different projects so they don't interfere with each other.

> ⚠️ We install Miniconda **inside WSL (Ubuntu)**, NOT in Windows. Keep the Ubuntu window open from the previous step — you will type the commands there.

**First, you need to find out which type of processor (CPU) your Windows computer has:**

### How to check your CPU type

1. Press **⊞ + R** on your keyboard (hold the Windows key and press R)
2. Type `msinfo32` and press **Enter**
3. A System Information window opens. Look for the **"System Type"** row:
   - If it says something with **"x64"** or **"Intel"** or **"AMD"** → you have an **Intel/AMD (x86-64) CPU**
   - If it says something with **"ARM"** → you have an **ARM CPU**
4. Close the System Information window when done

### Download Miniconda

Go back to the **Ubuntu** window (the command prompt showing `username@COMPUTERNAME:~$`).

**If you have an Intel or AMD (x86-64) CPU**, type this and press **Enter**:

```bash
wget https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh
```

**If you have an ARM CPU**, type this and press **Enter** instead:

```bash
wget https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-aarch64.sh
```

Wait for the download to finish — you will see a progress bar. This may take 1–3 minutes depending on your internet speed.

### Run the Miniconda installer

**If you have an Intel/AMD CPU**, type this and press **Enter**:

```bash
bash ~/Miniconda3-latest-Linux-x86_64.sh
```

**If you have an ARM CPU**, type this and press **Enter**:

```bash
bash ~/Miniconda3-latest-Linux-aarch64.sh
```

The installer will start. Follow these prompts carefully:

1. Press **Enter** to begin reading the licence agreement
2. Press **Space** or **Enter** repeatedly to scroll through the agreement until you reach the end
3. Type `yes` and press **Enter** to accept the licence
4. Press **Enter** to confirm the default installation location
5. Type `yes` and press **Enter** when asked whether to initialise Miniconda

6. **Close the Ubuntu window completely** (click the X button to close it)
7. **Reopen Ubuntu** — search for "Ubuntu" in the Windows Start menu and click it to open a new window

📹 [Watch: Install Miniconda on WSL for Windows](https://drive.google.com/file/d/1M6ioKVQ47084fMlXO03U2Aj2z910IFBR/view?usp=drive_link)

> ✅ **Checkpoint 3:** In the new Ubuntu window, your prompt should now start with **(base)**, like this:
> ```
> (base) username@COMPUTERNAME:~$
> ```
> The `(base)` part means Miniconda is installed and active. If you don't see `(base)`, close and reopen the Ubuntu window one more time. If it still doesn't appear, contact your instructor.

---

## Step 4 — Install and Configure Git

Git is a tool for saving and tracking changes to your code. Think of it like a very powerful "Track Changes" feature in Word, but for code files.

### Part A: Install Git

1. In the **Ubuntu** window that is still open (the one showing `(base) username@COMPUTERNAME:~$`), run the following command:

```bash
sudo apt install git
```

2. It will ask for your Linux password — type it and press **Enter** (no characters will appear as you type)
3. If asked `Do you want to continue? [Y/n]` — type `Y` and press **Enter**
4. Wait for the installation to finish, then confirm Git installed correctly:

```bash
git --version
```

> ✅ You should see something like `git version 2.x.x`. If so, Git is installed successfully.

### Part B: Configure Git with your name and email

This tells Git who you are. Use the **same email address you use for GitHub**.

1. In the Ubuntu window, type the following (replace `Your Name` with your actual name, keep the quotes):

```bash
git config --global user.name "Your Name"
```

Press **Enter**.

2. Now type the following (replace the email with your GitHub email address):

```bash
git config --global user.email "your_github_email@example.com"
```

Press **Enter**.

3. To confirm the settings saved correctly, type:

```bash
git config --global --list
```

Press **Enter**.

> ✅ **Checkpoint 4:** You should see two lines printed:
> ```
> user.name=Your Name
> user.email=your_github_email@example.com
> ```
> If you see your name and email printed correctly, Git is configured. 

---

## Step 5 — Install Visual Studio Code (VSCode)

VSCode is the text editor we use to write Python and SQL code. Think of it as Microsoft Word, but for code.

1. Open your regular web browser (Chrome, Edge, Firefox)
2. Go to: **https://code.visualstudio.com/download**
3. Click the **Windows** download button (the large blue button)
4. Once the file downloads, **open it** (it will be in your Downloads folder, named something like `VSCodeSetup-x64-1.xx.x.exe`)
5. Follow the installer:
   - Click **Next** through the first screens
   - On the screen that says **"Select Additional Tasks"**, tick the box **"Add to PATH"** and also **"Open with Code"** if you see them
   - Click **Next**, then **Install**
   - Click **Finish** when done (leave "Launch Visual Studio Code" ticked)

VSCode should open automatically when installation completes.

📹 [Watch: Install VSCode for Windows](https://drive.google.com/file/d/15s22OloEAY3SMtiFE_uSjCiM73cZD9nW/view?usp=drive_link)

> ✅ **Checkpoint 5:** VSCode opens and you can see the **Welcome** tab with a "Get Started" screen. If VSCode did not open, try finding it in the Start menu by searching for "Visual Studio Code".

---

## Step 6 — Connect VSCode to WSL

Now we connect VSCode to the Ubuntu/Linux environment you installed in Steps 1–4. This is important — from this point forward, all coding will happen inside WSL.

1. In VSCode, look at the **bottom-left corner** of the screen. You will see a small blue icon that looks like `><`
2. Click that **blue `><` icon**
3. A menu will appear at the top of the screen. Click **"Connect to WSL"**
4. VSCode will reload and install the WSL extension automatically. Wait about 30 seconds.

📹 [Watch: Connect VSCode to WSL](https://drive.google.com/file/d/1BbKKiy_VsBnEd8Y8Ar89zBSHpC_3w-4V/view?usp=drive_link)

> ✅ **Checkpoint 6:** After connecting, the bottom-left corner of VSCode should now show **"WSL: Ubuntu"** (instead of the `><` symbol). This means VSCode is now running inside Linux.

---

## Step 7 — Install VSCode Extensions

Extensions add extra features to VSCode. We need three extensions for this course.

> ⚠️ **Important:** Make sure you completed Step 6 first. The bottom-left corner of VSCode must show **"WSL: Ubuntu"** before you install these extensions, so they install in the correct place.

1. In VSCode, look at the left sidebar. Click the **Extensions** icon (it looks like four small squares, with one square slightly separated)
2. A search bar will appear at the top. Search for and install each of the following extensions:

**Extension 1: Python**
- Type `Python` in the search bar
- Click the result that says **Python** by *Microsoft*
- Click the blue **Install** button
- Wait for the installation to complete

**Extension 2: Jupyter**
- Clear the search bar and type `Jupyter`
- Click the result that says **Jupyter** by *Microsoft*
- Click **Install**

**Extension 3: Colab**
- Clear the search bar and type `Colab`
- Click the result that says **Colab** (by Google or similar)
- Click **Install**

> ✅ **Checkpoint 7:** For each of the three extensions, click on them in the Extensions panel. You should see **"Installed"** (or an "Uninstall" button, which means it's already installed). You should also see them listed under **"WSL: UBUNTU — INSTALLED"** rather than under "LOCAL". If they appear under LOCAL, please contact your instructor.

---

## Step 8 — Enable Auto-Save in VSCode

Auto-save means VSCode will automatically save your files as you type. This prevents a lot of common errors where code doesn't run because you forgot to save.

1. In VSCode, click on **File** in the top menu bar
2. Look for **Auto Save** in the dropdown menu
3. Click **Auto Save** to enable it (a checkmark will appear next to it)

> ✅ **Checkpoint 8:** Click on **File** again and confirm there is a **✓ checkmark** next to "Auto Save".

---

## Step 9 — Connect VSCode with GitHub

GitHub is the website where your course materials and assignments are stored. We need to connect VSCode to your GitHub account so you can download and upload your work.

1. In VSCode, click **Help** in the top menu bar, then click **Welcome**
2. On the Welcome page, click **"Clone Git Repository"**
3. A text box will appear at the top — type any GitHub URL (e.g. `https://github.com`) and press **Enter**
4. VSCode will ask you to **Sign in with GitHub** — click the button and follow the prompts in your browser to log in to your GitHub account
5. Once signed in, close the browser tab and return to VSCode

📹 [Watch: Configuring Git and Using Git in VSCode](https://drive.google.com/file/d/1kyBHa4G4K5bgTBVrA-doMxuZdfXr8jZp/view?usp=drive_link)

> ✅ **Checkpoint 9:** In VSCode, look at the bottom-left corner. You should see your **GitHub username** displayed. You are now connected to GitHub.

---

## Step 10 — Install DBGate

DBGate is a database viewer we use to look at data stored in databases. Think of it like Excel but for databases.

1. Open your web browser and go to: **https://www.dbgate.io/download-community/**
2. Download the **Windows installer** (the `.exe` file)
3. Once downloaded, open the file and follow the installation steps (click Next → Install → Finish)
4. After installing, open DBGate from your Start menu (search for "DBGate")

> ✅ **Checkpoint 10:** DBGate opens and you see the application window with a left sidebar showing "Connections". If DBGate opens successfully, the installation is complete.

---

## Step 11 — Final Verification

This final check confirms that all the software works together correctly. This is the most important test!

### Part A: Clone the course repository

1. In VSCode, click **Help** → **Welcome**
2. Click **"Clone Git Repository"**
3. Paste the following URL and press **Enter**:

```
https://github.com/su-ntu-ctp/6m-data-1.0-Welcome-Onboarding
```

4. Choose a folder to save it in (your home folder is fine)
5. Click **Open** when VSCode asks if you want to open the cloned repository

> ✅ If the repository appears in VSCode's file explorer on the left side, cloning worked correctly.

### Part B: Create a test database

Follow the full verification steps in the [Verification Guide](run_conda_python.md). This guide will walk you through:
- Creating a Python environment with conda
- Running a Python script that creates a test database
- Confirming you can see the data in DBGate

> ✅ **Final Checkpoint:** If you can see **3 records** in DBGate after completing the verification guide, your entire installation is successful! 🎉

---

## 🆘 Troubleshooting

| Problem | What to try |
|---------|------------|
| WSL won't install | See [WSL Troubleshooting Guide](install_wsl.md) |
| `(base)` doesn't appear in terminal | Close and re-open the Ubuntu window; if still missing, re-run `conda init --all` and open a fresh window |
| VSCode doesn't show "WSL: Ubuntu" | Click the blue `><` icon in the bottom-left corner and select "Connect to WSL" |
| Extensions installed under "LOCAL" instead of "WSL: UBUNTU" | Make sure you're connected to WSL first, then uninstall and reinstall the extensions |
| Git shows "command not found" | Run `sudo apt install git` in the Ubuntu window |

If you're still stuck, take a **screenshot** of the error message and share it with your instructor or in the class Discord.

---

## 📚 Additional Resources

- [WSL Basics Guide](wsl_linux_basics.md) — Learn basic Linux commands
- [VSCode Reference](../reference.md#vscode) — More VSCode tips
- [Git & GitHub Reference](../reference.md#git-and-github) — More Git resources
- [Official WSL Documentation](https://learn.microsoft.com/en-us/windows/wsl/install)
