# Module 1 First-Time Software Installation

## ⚠️ Important — Read This First

> **Intel Mac users:** Intel-based Macs are no longer supported. Please contact your instructor before proceeding.
>
> **Not sure which Mac you have?** Click the  (Apple menu) → **About This Mac**. If "Chip" shows **Apple M1/M2/M3/M4/M5**, you're on Apple Silicon. If "Processor" shows **Intel**, contact your instructor.

## 👇 Choose Your Operating System

Go directly to the guide for your computer's operating system:

| My computer runs... | Go to this guide |
|---|---|
| 🪟 **Windows** (any laptop or desktop running Windows 10 or 11) | **[→ Windows Installation Guide](guides/installation_windows.md)** |
| 🍎 **Mac with Apple Silicon** (M1, M2, M3, M4 or M5 chip) | **[→ Mac / Linux Installation Guide](guides/installation_mac_linux.md)** |
| 🐧 **Linux** (Ubuntu, Fedora, Debian, etc.) | **[→ Mac / Linux Installation Guide](guides/installation_mac_linux.md)** |

Each guide includes step-by-step instructions with checkpoints after every step so you can confirm each tool is working before moving on.

---

## Hardware Requirements

- Desktop/laptop computer running the latest version of macOS/Linux/Windows
- Recommended 16 GB onboard memory (RAM)
- Recommended 50 GB available storage space (HDD/SSD)
- Webcam and microphone for online Zoom sessions

## Software You Will Install

Each platform guide will walk you through installing all of the following:

| Software | Description | Platform |
|----------|-------------|----------|
| WSL | Windows Subsystem for Linux | Windows only |
| Git CLI | Command-line tool for version control | All platforms |
| Conda/Miniconda | Python package and environment manager | All platforms |
| Visual Studio Code (VSCode) | Source code editor | All platforms |
| DBGate | Database viewer | All platforms |

---

## FAQ

**1. What Operating System is recommended for this course?**
We support Windows 10/11, Apple Silicon Mac, and Linux. Windows users will need to install WSL (covered in the Windows guide). Intel Mac is not supported — please contact your instructor.

**2. What Python version is required?**
You don't need to worry about the Python version during installation. We use `conda` to manage different versions of Python, ensuring compatibility as needed.

**3. I have Anaconda installed — do I need to install Miniconda?**
For Mac users, no — if Anaconda is already installed, you can use it from VSCode. For Windows users, yes — since we develop inside WSL, you need to install Miniconda within the WSL Ubuntu environment specifically.

**4. Can I use Anaconda instead of VSCode?**
VSCode is the preferred option because it integrates seamlessly with GitHub, WSL, Colab, and Docker. It is also more lightweight. Other AI-focused IDEs such as Cursor also use the VSCode interface, so learning VSCode is transferable.

**5. I have GitHub Desktop installed — do I still need to install Git?**
Git is included when you install GitHub Desktop, so no separate Git installation is needed. However, you still need to connect VSCode to your GitHub account — this is covered in your platform guide.

**6. Can I use GitHub Desktop instead of the VSCode Git integration?**
We recommend sticking with VSCode, as it has built-in GitHub integration. Note that repositories cloned through VSCode will not appear in GitHub Desktop.

**7. Why can't I use my Intel-based MacBook?**
From August 2025, Anaconda stopped building conda packages for Intel Mac, and PyTorch ended Intel Mac support in 2022. You will not be able to run neural-network-based software on Intel Mac. Please consult your instructor for alternatives.
