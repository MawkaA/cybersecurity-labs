#Lab report: Installing and setting up Kali Linux and Windows 11  Virtual Machines on MacOS / Apple Silicon host (arm64).
**Date:**2025-08-16
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

---

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

## 5 Kali Linux 

### 5.1 Create a new VM Kali Linux
1. In UTM, click **Create a New Virtual Machine**.
2. Select **Virtualize** → **Linux**.
3. Choose the downloaded **Kali ARM64 ISO** as the boot medium.
4. Set resources:
   - CPU Cores: `4`
   - RAM: `4 GB` (4096 MB)
   - Storage: `40 GB`
5. Enable **Network** with Bridged or Shared mode.
6. The **shared directory** browse 'desktop' or create a folder that the Kali Linux VM (guest) could access on the Mac (host).
7. Finish setup.

### 5.2 Boot & Install Kali Linux
1. Start the VM.
2. Select **Install Kali** from the boot menu.
3. select **edit** then *new* then *serial* and click *save*. That will open the terminal.
4. Follow the installation prompts on the terminal:
   - Set up language, timezone, and keyboard layout.
   - Create a domain name.
   - Create username and password.
   - Partition disk (use guided- entire disk setup).
   - All files on one partition
5. Wait for installation to complete.
6. Click exit. Close windows. Clear ISO image. (CD/DVD option clear). Restart.

## 5.3 Verification
###5.1 Kali Linux
Run the following commands in the Kali terminal to confirm installation:
```bash
uname -m # Should return arm64 or aarch64
lsb_release -a
```
<img width="1728" height="1117" alt="Screenshot 2025-08-16 at 4 58 05 PM" src="https://github.com/user-attachments/assets/91f337ae-0ffe-4c5f-9377-a1dfea917d79" />

---

## 6 Windows 11

### 6.1 Create a new VM Windows 11
1. In UTM, click **`+ Create a New Virtual Machine`**.
2. Choose **Virtualize** (if running Apple Silicon and using ARM Windows ISO) or **Emulate** (for x86_64 ISO).
   - For **Windows 11 ISO 64-bit (x86)**, select **Emulate**.
3. Image file type: choose `Windows 10 or higher`, and boot ISO image file by *browse* `Windows 11 ISO`  file we downloaded earlier. Click *continue*.

---

*Note:* On the Windows download page, the ISO img file is supposed to be for ARM64 devices, but instead it was for x64(Intel/AMD version), which is not compatible with my Silicon (ARM64/ aarch64) architecture.
Tried to  *Emulate*. Failed.
Downloaded an ARM version from the Microsoft Insider page.
Choose *Windows 11 client  ARM64 insider Preview(Dev)  - Build 26100.1150* option.
Downloaded File is .VHDH 
Going back to start at 6.1. Choose option *Virtulize* . Uncheck `install drivers and SPICE tools`. installation.

---
### 6.2 Configure VM settings
- **Hardware**:
  - CPU Cores: `4`
  - RAM: `8 GB` (8192 MB)
  - Storage: `64 GB`
- **Shared Directory** *(optional)*:
  - Add a folder on your host machine for file sharing.
- **Summary**
  - Change name to `Windows 11`.
- **Networking**:
  - Default: NAT.
  - If you want the VM to appear as a device on your network, choose **Bridged**.


### 6.3 Installation of Windows 11
1. Start the VM.
2. Windows 11 installer will boot.
3. Follow installation steps:
   - Choose language, time, and keyboard layout.
   - To set up without internet press fn+shift+f10 to open terminal. Enter `oobe\bypassnro`
   - Network choose `I don't have internet`.
   - Proceed with installation (this can take a while).
<img width="802" height="637" alt="Screenshot 2025-08-17 at 3 35 43 PM" src="https://github.com/user-attachments/assets/003737f9-4487-4799-93ee-aec7983f2750" />




