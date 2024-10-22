# 🖥️ New Laptop Setup Guide

This guide will help you set up your new Windows installation with performance optimization, de-bloating, and privacy-first tools.

---

## 📋 Table of Contents

1. [Initial Setup](#initial-setup)
2. [Essential Tools](#essential-tools)
3. [System Tweaks](#system-tweaks)
4. [De-bloat and Privacy Tools](#de-bloat-and-privacy-tools)
5. [Obtain IoT Enterprise License](#obtain-iot-enterprise-license)
6. [Additional Resources](#additional-resources)
7. [Notes](#notes)
8. [Conclusion](#conclusion)

---

## Initial Setup

1. **Offline Install**: Avoid using an MS account by doing an offline installation.
2. **Update Windows**: Ensure your Windows installation is up to date by checking for updates.

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

## Obtain IoT Enterprise License

To upgrade your Windows to an IoT Enterprise edition, follow the instructions to obtain a license using [massgrave.dev](https://massgrave.dev/windows_ltsc_links).

1. Visit the website [massgrave.dev](https://massgrave.dev/windows_ltsc_links).
2. Choose the IoT Enterprise edition of Windows.
3. Follow the instructions on the page to obtain a valid IoT license key.

This license will give you better control over updates and privacy settings compared to the standard editions of Windows.

---

## Additional Resources

For further customization and optimizations, explore these tools:

- **O&O ShutUp10++**: A free tool to manage Windows privacy settings. Download from [here](https://www.oo-software.com/en/shutup10).
- **GlassWire**: A network monitoring tool to detect suspicious activity. Get it [here](https://www.glasswire.com).
  
---

## Notes

- Keep your system regularly updated for security improvements.
- Always create restore points before applying significant changes to your system.

---

