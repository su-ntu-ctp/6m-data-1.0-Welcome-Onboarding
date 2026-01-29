# Install Miniconda in WSL (Windows user)

Please note that we will be installing Miniconda in WSL. **Launch `WSL` or `Ubuntu` first.**

Step 0: Identify which CPU you are using.

- Majority of you will be using Intel CPU, however, we notice some Windows laptop uses ARM. 

Step 1: Using the following code to download the software:


**Intel CPU**
```bash
wget https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh
```

**Windows Laptop that uses ARM CPU**
```bash
wget https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-aarch64.sh
```

![assets/wsl_miniconda/miniconda1.png](../assets/wsl_miniconda/miniconda1.png)


Step 2: Using the following code to install the software:

**Intel CPU**
```bash
bash ~/Miniconda3-latest-Linux-x86_64.sh
```

**ARM CPU**
```bash
bash ~/Miniconda3-latest-Linux-aarch64.sh
```

![assets/wsl_miniconda/miniconda2.png](../assets/wsl_miniconda/miniconda2.png)

- Press *Enter* to continue
- It will show the service agreement

![assets/wsl_miniconda/miniconda3.png](../assets/wsl_miniconda/miniconda3.png)

- Press *Enter* or *Space* to continue

![assets/wsl_miniconda/miniconda4.png](../assets/wsl_miniconda/miniconda4.png)

- type `yes` to continue

![assets/wsl_miniconda/miniconda5.png](../assets/wsl_miniconda/miniconda5.png)

- press *Enter* to confirm location

![assets/wsl_miniconda/miniconda6.png](../assets/wsl_miniconda/miniconda6.png)

- type `yes` to configure miniconda

![assets/wsl_miniconda/miniconda7.png](../assets/wsl_miniconda/miniconda7.png)

- The setup is complete. Close WSL.

Step 3: Open WSL to confirm, it should be similar to the screen below.

![assets/wsl_miniconda/miniconda8.png](../assets/wsl_miniconda/miniconda8.png)