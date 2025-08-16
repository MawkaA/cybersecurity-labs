#Lab report: installing and setting up a Virtual Machine on MacOS / Apple Silicon host (arm64)
**Date:**2025-08-15
**Lab Objective:**
Set up a virtual machine on MacOS to run a cybersecurity lab environment.

---

##1 Overview
This document the process of installing and configuring a VM on MacBook for cybersecurity training.
The goal is to create  an isolated environment without affecting the main systems.

##2 System information
**host machine:** MacBook pro (Apple M1)
**host OS:** Sequoia 15.6
**RAM:** 16 GB
**Storage:** 1tb SSD 

##3 Tools & resourses
1[UTM Virtual Machine Software](https://mac.getutm.app/)– Free, supports ARM-based VMs.
2[Kali Linux ARM64 ISO ](https://www.kali.org/get-kali/#kali-arm)
3[Windows 11 ISO for ARM64](https://www.microsoft.com/en-us/software-download/windows11)
4Internet connection

## 4. Installation Steps

### 4.1 Download & Install UTM
1. Visit the [UTM website](https://mac.getutm.app/).
2. Download the latest macOS version.
3. Open the `.dmg` file and drag **UTM** into the **Applications** folder.
4. Launch UTM.

---

### 4.2 Download Kali Linux ARM ISO
1. Go to [Kali Linux ARM Images](https://www.kali.org/get-kali/#kali-arm).
2. Download the **ARM64 ISO** file.
3. Save it to your Downloads folder.

---

### 4.3 Download Windows 11 ISO
1. Go to [Windows 11 ISO for ARM64](https://www.microsoft.com/en-us/software-download/windows11)
2. Download the file.
3. Save it to your Downloads folder.
---

### 4.4 Create a New Virtual Machine
1. In UTM, click **Create a New Virtual Machine**.
2. Select **Virtualize** → **Linux**.
3. Choose the downloaded **Kali ARM64 ISO** as the boot medium.
4. Set resources:
   - CPU Cores: `4`
   - RAM: `4 GB` (4096 MB)
   - Storage: `40 GB`
5. Enable **Network** with Bridged or Shared mode.
6. Finish setup.

---

### 4.5 Boot & Install Kali Linux
1. Start the VM.
2. Select **Install Kali** from the boot menu.
3. Follow the installation prompts:
   - Set up language, timezone, and keyboard layout.
   - Create a username and password.
   - Partition disk (use guided setup).
4. Wait for installation to complete and reboot.

## 5. Verification
###5.1 Kali Linux
Run the following commands in the Kali terminal to confirm installation:
```bash
uname -m # Should return arm64 or aarch64
lsb_release -a
```
---

###5.2 Windows 11
Run the following commands in the terminal:
```bash
1 winver  -> verify version and edition
2 systeminfo
3 ipconfig/ping --> check network
