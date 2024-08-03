# 🖥️ New Laptop Setup Guide

This guide will help you set up your new Windows installation with performance optimization, de-bloating, and privacy-first tools.

---

## 📋 Table of Contents

1. [Initial Setup](#initial-setup)
2. [Essential Tools](#essential-tools)
3. [System Tweaks](#system-tweaks)
    - [Power Optimization](#power-optimization)
    - [Registry Tweaks](#registry-tweaks)
    - [PowerShell Scripts](#powershell-scripts)
4. [De-bloat and Privacy Tools](#de-bloat-and-privacy-tools)
5. [ROG Laptop Optimization](#rog-laptop-optimization)
6. [Additional Resources](#additional-resources)
7. [Notes](#notes)
8. [Conclusion](#conclusion)

---

## Initial Setup

1. **Offline Install**: Because I don't like to tie MS account to my laptop.
2. **Update Windows**: Ensure your Windows installation is up to date by checking for updates.

---

## Essential Tools

1. **Nvidia Drivers**: Download and install the latest Nvidia drivers from the [official website](https://www.nvidia.com/Download/index.aspx).
2. **Winaero Tweaker**: A powerful tool to customize and tweak Windows. Download from [here](https://winaero.com/winaero-tweaker/).
3. **Optimizer**: A comprehensive tool to enhance performance and privacy. Get it from [Optimizer](https://github.com/hellzerg/optimizer/releases).
4. **WPD (Windows Privacy Dashboard)**: Use WPD to control Windows privacy settings. Available at [WPD](https://wpd.app).

---

## System Tweaks

### Power Optimization

1. **Modify Power Settings**: Open `Control Panel > Hardware and Sound > Power Options`.
2. **Customize Advanced Power Settings**:
    - Set hard disk to turn off after 0 minutes.
    - (optional for desktops or if you don't move around too much )Set sleep options to Never.
    - Adjust processor power management to 100% while plugged in.

### Registry Tweaks

#### Modify Existing Registry Entries

1. **Enable Additional Power Settings**
    ```reg
    HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Power\PowerSettings\54533251-82be-4824-96c1-47b60b740d00\be337238-0d82-4146-a960-4f3749d470c7
    ```
    Modify the value of "Attributes" from `1` to `2`. Data should read `0x00000002 (2)`.

2. **Enable Processor Idle Demote**
    ```reg
    HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Power\PowerSettings\54533251-82be-4824-96c1-47b60b740d00\75b0ae3f-bce0-45a7-8c89-c9611c25e100
    ```
    Modify the value of "Attributes" from `1` to `2`. Data should read `0x00000002 (2)`.

#### Add New Registry Entries

```reg
HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Power\PowerSettings

## 📋 **References**
1.https://www.reddit.com/r/OptimizedGaming/comments/su6cq7/windows_1011_optimization_guide/
