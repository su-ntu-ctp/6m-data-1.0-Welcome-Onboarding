# 🍎🐧 Installation Guide — Mac (Apple Silicon) & Linux

This guide will walk you through installing all the software you need for this course, **one step at a time**. Each section ends with a **✅ Checkpoint** so you can confirm everything worked before moving on.

> ⚠️ **Intel Mac users:** Unfortunately, Intel-based Macs are no longer supported by this course. Key software packages (including PyTorch and Conda) have ended support for Intel Macs as of 2025. Please contact your instructor for alternatives before proceeding.
>
> **Not sure if you have an Intel or Apple Silicon Mac?** Click the  (Apple logo) in the top-left corner → **About This Mac**. Look at the "Chip" or "Processor" field:
> - **Apple M1 / M2 / M3 / M4** → ✅ You're good to go!
> - **Intel Core i5 / i7 / i9** → ❌ Intel Mac — contact your instructor

> 🐧 **Linux users:** This guide applies to you too! The steps are nearly identical. Where differences exist, they are marked with **[Linux]**.

---

## 📋 Before You Begin — Hardware Check

**Minimum requirements:**
- Mac with Apple Silicon chip (M1, M2, M3, or M4), running macOS Ventura or later
- **[Linux]** Any modern 64-bit Linux distribution (Ubuntu 20.04+, Debian 11+, Fedora 36+, etc.)
- 16 GB RAM recommended
- 50 GB free storage space
- A working webcam and microphone for Zoom sessions

**How to check your macOS version:**
1. Click the  (Apple logo) in the top-left corner of your screen
2. Click **About This Mac**
3. Note the macOS version shown (e.g. "macOS Sonoma 14.x")

> ✅ **Checkpoint 0:** Confirm you see Apple M1/M2/M3/M4 as the chip. If you're on macOS, version 13 (Ventura) or later is recommended. Contact your instructor if you are unsure.

---

## Step 1 — Install Visual Studio Code (VSCode)

VSCode is the text editor we use to write Python and SQL code. Think of it as Microsoft Word, but for code.

**For Mac:**
1. Open Safari or Chrome and go to: **https://code.visualstudio.com/download**
2. Click the **Mac** download button — make sure to select **Apple Silicon** (not Intel)
3. A `.zip` file will download. Once it's done, open your **Downloads** folder
4. **Double-click** the downloaded `.zip` file to unzip it — this creates the "Visual Studio Code" application
5. **Drag** the "Visual Studio Code" app into your **Applications** folder (open Finder → Applications, then drag it across)
6. Open VSCode from your Applications folder by double-clicking it

> ⚠️ If macOS says "Visual Studio Code cannot be opened because Apple cannot check it for malicious software", go to **System Settings → Privacy & Security → scroll down** and click **"Open Anyway"**.

**[Linux]:**
1. Go to **https://code.visualstudio.com/download** and download the `.deb` (Ubuntu/Debian) or `.rpm` (Fedora/RHEL) package
2. Open a terminal and run (for Debian/Ubuntu):
```bash
sudo dpkg -i ~/Downloads/code_*.deb
sudo apt install -f
```
3. Launch VSCode by typing `code` in the terminal, or find it in your application menu

📹 [Watch: Install VSCode for Mac](https://drive.google.com/file/d/1wQY5fhUb7pCo7nHJwbrIP6UCYFNSOkRd/view?usp=drive_link)

> ✅ **Checkpoint 1:** VSCode opens and you can see the **Welcome** tab with a "Get Started" screen. The window title should say "Visual Studio Code".

---

## Step 2 — Install Git

Git is a tool for saving and tracking changes in your code. Think of it as a very powerful "Track Changes" feature, but for code.

### Part A: Install Git

1. Open **Terminal** on your Mac:
   - Press **⌘ + Space** to open Spotlight Search
   - Type `Terminal` and press **Enter**
   - A black or white window with a command prompt will open

   **[Linux]:** Open your terminal application (usually found in your applications menu, or press Ctrl+Alt+T)

2. In the terminal, type the following and press **Enter**:

```bash
git --version
```

**For Mac:** If Git is not yet installed, macOS will automatically show a pop-up window asking you to install the **Command Line Developer Tools**. Click **Install** and wait for it to complete — this can take 5–15 minutes depending on your internet speed.

**[Linux — Ubuntu/Debian]:** If you see "command not found", run:
```bash
sudo apt update
sudo apt install git
```
Type your password when prompted and type `Y` to confirm.

**[Linux — Fedora]:** If you see "command not found", run:
```bash
sudo dnf install git
```

3. Once installation is complete, run the version check again to confirm:

```bash
git --version
```

> ✅ **Checkpoint 2A:** You should see something like `git version 2.x.x`. If so, Git is installed successfully.

### Part B: Configure Git with your name and email

This tells Git who you are. Use the **same email address you use for GitHub**.

1. In the terminal, type the following (replace `Your Name` with your actual name — keep the quotation marks):

```bash
git config --global user.name "Your Name"
```

Press **Enter**.

2. Now type the following (replace the email with your GitHub account email):

```bash
git config --global user.email "your_github_email@example.com"
```

Press **Enter**.

3. To confirm everything saved correctly, type:

```bash
git config --global --list
```

Press **Enter**.

> ✅ **Checkpoint 2B:** You should see two lines printed:
> ```
> user.name=Your Name
> user.email=your_github_email@example.com
> ```
> If you see your name and email printed correctly, Git is configured. 

**Mac-only optional step** (helps prevent errors when uploading large files):
```bash
git config --global http.postBuffer 524288000
```

📹 [Watch: Install Git for Mac](https://drive.google.com/file/d/1_NdWjc4pqYkuaFqRgYCGI62FoDufK4Bs/view?usp=drive_link)

---

## Step 3 — Install Miniconda

Miniconda manages Python and all the software packages we use in this course. It lets us create isolated "environments" for different projects — like separate workspaces — so software from one project doesn't interfere with another.

### For Mac (Apple Silicon — M1/M2/M3/M4)

1. Open your **Terminal** (press ⌘ + Space, type Terminal, press Enter)
2. Run the following commands **one at a time** — type or paste each line, press Enter, and wait for it to finish before running the next:

**Step 3.1** — Create a folder for Miniconda:
```bash
mkdir -p ~/miniconda3
```

**Step 3.2** — Download Miniconda:
```bash
curl https://repo.anaconda.com/miniconda/Miniconda3-latest-MacOSX-arm64.sh -o ~/miniconda3/miniconda.sh
```

This may take a minute or two. You'll see a progress bar.

**Step 3.3** — Install Miniconda:
```bash
bash ~/miniconda3/miniconda.sh -b -u -p ~/miniconda3
```

Wait for the installation to complete.

**Step 3.4** — Remove the installer file (it's no longer needed):
```bash
rm ~/miniconda3/miniconda.sh
```

**Step 3.5** — Activate Miniconda:
```bash
source ~/miniconda3/bin/activate
```

**Step 3.6** — Initialise Miniconda for all terminal types:
```bash
conda init --all
```

**Step 3.7** — **Close the Terminal window completely** and open a new one.

### For Linux

**Step 3.1** — Download Miniconda:
```bash
wget https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh
```

**Step 3.2** — Run the installer:
```bash
bash ~/Miniconda3-latest-Linux-x86_64.sh
```

Follow the prompts:
- Press **Enter** to read the licence, then **Space** or **Enter** to scroll to the end
- Type `yes` and press **Enter** to accept the licence
- Press **Enter** to confirm the default installation location
- Type `yes` and press **Enter** to initialise conda

**Step 3.3** — Close your terminal and open a new one.

> ✅ **Checkpoint 3:** In the **new** terminal window, your command prompt should now start with **(base)**, like this:
> ```
> (base) your-macbook-name ~ %
> ```
> The `(base)` part means Miniconda is installed and running correctly. If you don't see `(base)`, try closing and reopening the terminal. If it still doesn't appear, run `conda init --all` and try again.

---

## Step 4 — Install VSCode Extensions

Extensions add extra features to VSCode. We need three extensions for this course.

1. Open **VSCode**
2. Look at the **left sidebar**. Click the **Extensions** icon — it looks like four small squares with one square slightly separated from the others
3. A search bar will appear at the top of the sidebar. Search for and install each extension below:

**Extension 1: Python**
- Type `Python` in the search bar
- Click the result that says **Python** by *Microsoft* (it should be the first result)
- Click the blue **Install** button
- Wait for the installation bar to complete

**Extension 2: Jupyter**
- Clear the search bar and type `Jupyter`
- Click the result that says **Jupyter** by *Microsoft*
- Click **Install**

**Extension 3: Colab**
- Clear the search bar and type `Colab`
- Click the result that says **Colab** (Google Colaboratory integration)
- Click **Install**

> ✅ **Checkpoint 4:** Click on each of the three extensions in the panel. You should see an **"Uninstall"** button (which means they are installed). All three — Python, Jupyter, and Colab — should show as installed.

---

## Step 5 — Enable Auto-Save in VSCode

Auto-save means VSCode will automatically save your files as you type. This prevents a very common mistake where code doesn't run because the file wasn't saved.

1. In VSCode, click **File** in the top menu bar (on Mac this is at the very top of the screen)
2. Look for **Auto Save** in the dropdown
3. Click **Auto Save** to enable it — a checkmark ✓ will appear next to it

> ✅ **Checkpoint 5:** Click **File** again and confirm you can see a **✓ checkmark** next to "Auto Save".

---

## Step 6 — Connect VSCode with GitHub

GitHub is the website where your course materials and assignments are stored. We need to link VSCode to your GitHub account so you can download and upload work.

1. Open **VSCode**
2. Click **Help** in the top menu bar, then click **Welcome**
3. On the Welcome page, look for **"Clone Git Repository"** and click it
4. A text box will appear at the top of VSCode — type any GitHub URL (e.g. `https://github.com`) and press **Enter**
5. VSCode will show a prompt asking you to **Sign in with GitHub** — click it
6. Your web browser will open. Log in to your GitHub account if you aren't already
7. Click **Authorize** when GitHub asks if you want to give VSCode access
8. Return to VSCode — it may ask you to confirm the sign-in

📹 [Watch: Configuring Git and Using Git in VSCode](https://drive.google.com/file/d/1kyBHa4G4K5bgTBVrA-doMxuZdfXr8jZp/view?usp=drive_link)

> ✅ **Checkpoint 6:** In VSCode, look at the bottom-left corner of the window. You should see your **GitHub username** displayed. This confirms VSCode is connected to your GitHub account.

---

## Step 7 — Install DBGate

DBGate is a database viewer we use to look at data stored in databases — think of it like Excel but for databases.

1. Open your web browser and go to: **https://www.dbgate.io/download-community/**
2. Click the **Mac** download button (choose the `.dmg` file for Apple Silicon)

   **[Linux]:** Download the `.AppImage` or `.deb` file for your distribution

3. **For Mac:** Once downloaded, double-click the `.dmg` file, then drag the DBGate app into your **Applications** folder. Open DBGate from Applications.

   **[Linux .AppImage]:** Open a terminal and run:
   ```bash
   chmod +x ~/Downloads/dbgate-*.AppImage
   ~/Downloads/dbgate-*.AppImage
   ```

   **[Linux .deb]:**
   ```bash
   sudo dpkg -i ~/Downloads/dbgate-*.deb
   ```

4. Open DBGate — if macOS shows a security warning, go to **System Settings → Privacy & Security** and click **"Open Anyway"**

> ✅ **Checkpoint 7:** DBGate opens and you can see the main window with a sidebar showing "Connections". If the app opens successfully, the installation is complete.

---

## Step 8 — Final Verification

This final check confirms that all the software works together correctly. This is the most important test!

### Part A: Clone the course repository

1. Open **VSCode**
2. Click **Help** → **Welcome**
3. Click **"Clone Git Repository"**
4. Paste the following URL and press **Enter**:

```
https://github.com/su-ntu-ctp/6m-data-1.0-Welcome-Onboarding
```

5. Choose a folder to save it (your home folder or Desktop is fine)
6. Click **Open** when VSCode asks if you want to open the cloned repository

> ✅ If the repository files appear in VSCode's file explorer panel on the left, cloning worked correctly.

### Part B: Create a test database

Follow the full verification steps in the [Verification Guide](run_conda_python.md). This guide walks you through:
- Creating a Python environment with conda
- Running a Python script that creates a test database
- Confirming you can see the data in DBGate

> ✅ **Final Checkpoint:** If you can see **3 records** in DBGate after completing the verification guide, your entire installation is successful! 🎉

---

## 🆘 Troubleshooting

| Problem | What to try |
|---------|------------|
| `(base)` doesn't appear after installing Miniconda | Close and re-open the terminal. If still missing, run `conda init --all` in the terminal, then open a fresh terminal. |
| VSCode says "cannot be opened" (Mac security warning) | Go to System Settings → Privacy & Security → scroll down → click "Open Anyway" |
| Git install pop-up doesn't appear on Mac | Run `xcode-select --install` directly in the terminal |
| `curl: command not found` (Linux) | Install curl first: `sudo apt install curl` |
| DBGate won't open on Mac | Right-click the app and select "Open" instead of double-clicking |
| Extensions don't appear after installing | Restart VSCode and check the Extensions panel again |

If you're still stuck, take a **screenshot** of the error message and share it with your instructor or in the class Discord.

---

## 📚 Additional Resources

- [Google Colab Setup Guide](Google_Colab_Setup.md) — Using Colab as a cloud alternative
- [VSCode Reference](../reference.md#vscode) — More VSCode tips
- [Git & GitHub Reference](../reference.md#git-and-github) — More Git resources
- [Conda/Miniconda Reference](../reference.md#conda-or-miniconda) — More Conda resources
- [Official Miniconda Documentation](https://www.anaconda.com/docs/getting-started/miniconda/main)
