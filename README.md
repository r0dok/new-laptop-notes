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

1. **Offline Install**: Avoid using an MS account by doing an offline installation. Use **Rufus** for easier installation.
2. **Update Windows**: Ensure your Windows installation is up to date by checking for updates.

---

## Essential Tools

1. **Nvidia Drivers**: Download and install the latest Nvidia drivers from the [official website](https://www.nvidia.com/Download/index.aspx).
2. **Winaero Tweaker**: A powerful tool to customize and tweak Windows. Download from [here](https://winaero.com/winaero-tweaker/).
3. **Optimizer**: A comprehensive tool to enhance performance and privacy. Get it from [Optimizer](https://github.com/hellzerg/optimizer/releases).
4. **WPD (Windows Privacy Dashboard)**: Use WPD to control Windows privacy settings. Available at [WPD](https://wpd.app).
5. **GlassWire**: A network monitoring tool to detect suspicious activity. Get it [here](https://www.glasswire.com).

---

## System Tweaks

1. **Adjust Power Settings**: Modify power plans for performance or battery longevity.
2. **Remove Unnecessary Startup Items**: Disable startup programs via `Task Manager > Startup` for a faster boot.

---

## Advanced Power Tweaks for Zephyrus G14 (2021, R9 + 3060)

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

1. **O&O ShutUp10++**: A free tool to manage Windows privacy settings. Download from [here](https://www.oo-software.com/en/shutup10).
2. **Debloat Windows using PowerShell**: Run the following command in PowerShell to remove unnecessary apps and features:
    ```powershell
    iwr -useb https://git.io/debloat|iex
    ```
    This script will prompt you with options for de-bloating your system.
3. **Remove OneDrive**: If you don't need OneDrive, uninstall it using PowerShell:
    ```powershell
    winget uninstall Microsoft.OneDrive
    ```

---

## ROG Laptop Optimization with G-Helper

ROG laptops often come with **Armoury Crate**, which can be resource-heavy and intrusive. You can switch to **G-Helper** for better control and efficiency without the bloat.

1. **Download G-Helper**: Get it from the [official G-Helper GitHub page](https://github.com/seerge/g-helper).
2. **Install G-Helper**: Follow the instructions on the GitHub page to replace Armoury Crate and take control of your laptop’s performance settings.
3. **Optimize Performance Profiles**:
   - Use G-Helper to switch between performance, balanced, and silent modes.
   - Control fan speed and monitor CPU/GPU temperatures more efficiently.
4. **Disable Armoury Crate Services**:
   - Go to `Services.msc` and disable any Armoury Crate-related services to prevent conflicts with G-Helper.

G-Helper offers a lightweight alternative to manage your ROG laptop’s performance without unnecessary overhead.

---

## Obtain IoT Enterprise License

To upgrade your Windows to an IoT Enterprise edition, follow the instructions to obtain a license using [massgrave.dev](https://massgrave.dev/windows_ltsc_links).

1. Visit the website [massgrave.dev](https://massgrave.dev/windows_ltsc_links).
2. Choose the IoT Enterprise edition of Windows.
3. Follow the instructions on the page to obtain a valid IoT license key.

---

## Additional Resources

For further customization and optimizations, explore these tools:

- **O&O ShutUp10++**: A free tool to manage Windows privacy settings. Download from [here](https://www.oo-software.com/en/shutup10).
- **GlassWire**: A network monitoring tool to detect suspicious activity. Get it [here](https://www.glasswire.com).

---

## Notes

- FFS - keep your stuff updates

---