# 🖥️ New Laptop Setup Guide

---

## 📋 Table of Contents

1. [Initial Setup](#initial-setup)  
2. [Essential Tools](#essential-tools)  
3. [System Tweaks](#system-tweaks)  
4. [Advanced Power Tweaks for Zephyrus G14](#advanced-power-tweaks-for-zephyrus-g14-2021-r9--3060)  
5. [De-bloat and Privacy Tools](#de-bloat-and-privacy-tools)  
6. [ROG Laptop Optimization with G-Helper](#rog-laptop-optimization-with-g-helper)  
7. [Obtain IoT Enterprise License](#obtain-iot-enterprise-license)  
8. [Additional Resources](#additional-resources)  
9. [Notes](#notes)  
10. [Conclusion](#conclusion)  

---

## Initial Setup

### Create a Windows Installer (IoT LTSC via massgrave & Rufus)

1. **Download Windows IoT LTSC ISO**:  
   - Go to [massgrave.dev/windows_ltsc_links](https://massgrave.dev/windows_ltsc_links).
   - Download the latest Windows 10/11 IoT Enterprise LTSC ISO.

2. **Download Rufus**:  
   - Get Rufus from [rufus.ie](https://rufus.ie/).

3. **Prepare a USB Drive**:  
   - Insert a USB drive (at least 8GB).

4. **Create Bootable USB**:  
   - Open Rufus.
   - Select your USB drive.
   - Select the downloaded IoT LTSC ISO.
   - Choose "GPT" for partition scheme (for most modern laptops).
   - Click "Start" and wait for completion.

5. **Boot from USB**:  
   - Insert the USB into your laptop.
   - Power on and enter the boot menu (usually by pressing `Esc`, `F2`, or `F12`).
   - Select the USB drive to start Windows installation.

6. **Offline Install**:  
   - During setup, choose "Offline Account" or "Limited Experience" to avoid using a Microsoft account.

7. **Update Windows**:  
   - Once installed, ensure your Windows installation is up to date by checking for updates.

---

## Essential Tools

1. **Nvidia Drivers**: Download and install the latest Nvidia drivers from the [official website](https://www.nvidia.com/Download/index.aspx).
2. **Winaero Tweaker**: A powerful tool to customize and tweak Windows. Download from [here](https://winaero.com/winaero-tweaker/).
3. **Optimizer**: A comprehensive tool to enhance performance and privacy. Get it from [Optimizer](https://github.com/hellzerg/optimizer/releases).
4. **WPD (Windows Privacy Dashboard)**: Use WPD to control Windows privacy settings. Available at [WPD](https://wpd.app).

---

## System Tweaks

1. **Adjust Power Settings**: Modify power plans for performance or battery longevity.
2. **Remove Unnecessary Startup Items**: Disable startup programs via `Task Manager > Startup` for a faster boot.

---

## Advanced Power Tweaks for Zephyrus G14 (mine is 2021, R9 + 3060)

Fine-tune your laptop’s power and thermal behavior for better battery life, lower temps, or maximum performance.

### Show Advanced Processor Power Options

Open PowerShell as Administrator and run:
```powershell
powercfg -attributes SUB_PROCESSOR 893dee8e-2bef-41e0-89c6-b55d0929964c -ATTRIB_HIDE
powercfg -attributes SUB_PROCESSOR 75b0ae3f-bce0-45a7-8c89-c9611c25e100 -ATTRIB_HIDE
```
This reveals **Minimum/Maximum processor state** and **Processor performance boost mode** in your power plan’s advanced settings.

### Set Minimal/Maximum Processor Power State

To set minimum to 5% and maximum to 99% (which also disables boost):
```powershell
powercfg /setacvalueindex SCHEME_CURRENT SUB_PROCESSOR PROCTHROTTLEMIN 5
powercfg /setacvalueindex SCHEME_CURRENT SUB_PROCESSOR PROCTHROTTLEMAX 99
powercfg /setactive SCHEME_CURRENT
```

### Disable CPU Boost (for lower temps and noise)

To fully disable CPU boost:
```powershell
powercfg /setacvalueindex SCHEME_CURRENT SUB_PROCESSOR PERFBOOSTMODE 0
powercfg /setactive SCHEME_CURRENT
```
- **0 = Disabled**, **1 = Enabled**, **2 = Aggressive**, **3 = Efficient Enabled**, **4 = Efficient Aggressive**

You can create multiple power plans (e.g., "Silent", "Performance") and switch as needed.

---

## De-bloat and Privacy Tools

To remove bloatware and enhance privacy, use the following tools:

1. **Debloat Windows using PowerShell**: Run the following command in PowerShell to remove unnecessary apps and features:
    ```powershell
    iwr -useb https://git.io/debloat|iex
    ```
    This script will prompt you with options for de-bloating your system.
2. **Remove OneDrive**: If you don't need OneDrive, uninstall it using PowerShell:
    ```powershell
    winget uninstall Microsoft.OneDrive
    ```

---

## ROG Laptop Optimization with G-Helper

ROG laptops often come with **Armoury Crate**, which can be resource-heavy and intrusive. You can switch to **G-Helper** for better control and efficiency without the bloat.

1. **Download G-Helper**: Get it from the [official G-Helper GitHub page](https://github.com/seerge/g-helper).
2. **Install G-Helper**: Follow the instructions on the GitHub page to replace Armoury Crate and take control of your laptop’s performance settings.
3. **Optimize Performance Profiles**:
   - Use G-Helper to switch between performance, balanced, and silent modes (I run always balanced + optimized).
   - Control fan speed and monitor CPU/GPU temperatures more efficiently.
4. **Disable Armoury Crate Services**:
   - Go to `Services.msc` and disable any Armoury Crate-related services to prevent conflicts with G-Helper.

G-Helper offers a lightweight alternative to manage your ROG laptop’s performance without unnecessary overhead.

---

## Notes

- FFS - keep your stuff updates

---