# 🖥️ New Laptop Setup Guide

---

## 📋 Table of Contents

1. [Initial Setup](#initial-setup)
2. [Essential Tools](#essential-tools)
3. [System Tweaks](#system-tweaks)
4. [De-bloat and Privacy Tools](#de-bloat-and-privacy-tools)
5. [ROG Laptop Optimization with G-Helper](#rog-laptop-optimization-with-g-helper)
6. [Obtain IoT Enterprise License](#obtain-iot-enterprise-license)
7. [Additional Resources](#additional-resources)
8. [Notes](#notes)
9. [Conclusion](#conclusion)

---

## Initial Setup

1. **Offline Install**: Avoid using an MS account by doing an offline installation. Also use Rufus for easier installation
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

- For the love of God, please keep your stuff upgraded

---

## Conclusion
