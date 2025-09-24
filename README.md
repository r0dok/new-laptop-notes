# 🖥️ Windows Optimization Guide
> Advanced optimization for ASUS Zephyrus G14 (2021, R9 5900HS + RTX 3060)

## 📋 Table of Contents
1. [Store Apps on LTSC](#store-apps-on-ltsc)
2. [Advanced Power Management](#advanced-power-management)
3. [ROG Hardware Optimization](#rog-hardware-optimization)
4. [System Tweaks](#system-tweaks)
5. [Performance Validation](#performance-validation)
6. [Configuration Files](#configuration-files)

---

## Store Apps on LTSC

### PowerShell Method
```powershell
# Run as Administrator
wsreset -i
```
**Note**: On Windows 10 2021 LTSC, cliprenew.exe errors can be ignored.

### App Installer (WinGet)
Essential for package management. Install from:
```
https://apps.microsoft.com/detail/9nblggh4nns1
```

### Fallback Method
If PowerShell fails, use community package:
```
https://github.com/stdin82/htfx/releases/tag/v0.0.24
```

---

## Advanced Power Management

### Unlock Hidden Power Options
```powershell
# Expose CPU performance boost mode
powercfg -attributes SUB_PROCESSOR 893dee8e-2bef-41e0-89c6-b55d0929964c -ATTRIB_HIDE

# Expose processor performance core parking min cores
powercfg -attributes SUB_PROCESSOR 75b0ae3f-bce0-45a7-8c89-c9611c25e100 -ATTRIB_HIDE
```

### Optimal Performance Settings
```powershell
# Set minimum processor state to 1% (allows deeper C-states)
powercfg /setacvalueindex SCHEME_CURRENT SUB_PROCESSOR PROCTHROTTLEMIN 1

# Cap maximum processor state at 99% (prevents boost clock instability)
powercfg /setacvalueindex SCHEME_CURRENT SUB_PROCESSOR PROCTHROTTLEMAX 99

# Disable CPU performance boost (reduces heat and improves consistency)
powercfg /setacvalueindex SCHEME_CURRENT SUB_PROCESSOR PERFBOOSTMODE 0

# Apply changes
powercfg /setactive SCHEME_CURRENT
```

### Performance Boost Mode Values
- **0** = Disabled (Best thermals, recommended for G14)
- **1** = Enabled (Default)
- **2** = Aggressive (High performance, high heat)
- **3** = Efficient Enabled
- **4** = Efficient Aggressive

---

## ROG Hardware Optimization

### Remove Armoury Crate Completely
```powershell
# Uninstall Armoury Crate components
Get-AppxPackage *ArmouryCrate* | Remove-AppxPackage
Get-AppxPackage *ROG* | Remove-AppxPackage

# Stop and disable services
Stop-Service "ArmouryCrateService" -Force
Set-Service "ArmouryCrateService" -StartupType Disabled
Stop-Service "ArmouryCrateControlInterface" -Force  
Set-Service "ArmouryCrateControlInterface" -StartupType Disabled
```

### G-Helper Configuration
Download: [github.com/seerge/g-helper](https://github.com/seerge/g-helper)

![G-Helper Settings](References/GHelper1.png)

**Recommended Settings**:
- Performance Mode: **Balanced**
- CPU Boost: **Efficient** (Mode 3)
- GPU Mode: **Eco** (for battery) / **Standard** (plugged in)
- Screen refresh: **60Hz** (battery) / **144Hz** (plugged in)

### NVIDIA Driver Optimization
```powershell
# Install only driver, skip GeForce Experience
# Use Studio drivers for stability over Game Ready
```

**NVIDIA Control Panel Settings**:
- Power Management: **Prefer Maximum Performance** (when plugged in)
- Texture Filtering - Quality: **High Performance**
- Threaded Optimization: **On**

---

## System Tweaks

### Essential Registry Modifications
```powershell
# Disable Windows Defender real-time protection (if using alternative)
Set-ItemProperty -Path "HKLM:\SOFTWARE\Policies\Microsoft\Windows Defender\Real-Time Protection" -Name "DisableRealtimeMonitoring" -Value 1

# Disable mouse acceleration
Set-ItemProperty -Path "HKCU:\Control Panel\Mouse" -Name "MouseSpeed" -Value "0"
Set-ItemProperty -Path "HKCU:\Control Panel\Mouse" -Name "MouseThreshold1" -Value "0"
Set-ItemProperty -Path "HKCU:\Control Panel\Mouse" -Name "MouseThreshold2" -Value "0"

# Disable fullscreen optimizations globally
Set-ItemProperty -Path "HKCU:\System\GameConfigStore" -Name "GameDVR_FSEBehavior" -Value "2"
```

### Advanced System Cleanup
```powershell
# Remove OneDrive completely
winget uninstall Microsoft.OneDrive
Remove-Item -Path "$env:USERPROFILE\OneDrive" -Force -Recurse -ErrorAction SilentlyContinue

# Run comprehensive debloat script
iwr -useb https://git.io/debloat | iex
```

### Winaero Tweaker Optimization
Download: [winaero.com/winaero-tweaker/](https://winaero.com/winaero-tweaker/)

**Configuration File**: [References/WinaeroTweaker.ini](References/WinaeroTweaker.ini)

Key Settings:
```ini
# Critical optimizations from WinaeroTweaker.ini
UnwantedAppsDisabled=1
FileExplorerAdsDisabled=1  
LockScreenAdsDisabled=1
StartSuggestionsDisabled=1
TipsAboutWindowsDisabled=1
WelcomePageDisabled=1
SettingsAdsDisabled=1
```

### Optimizer Tool
Download: [github.com/hellzerg/optimizer/releases](https://github.com/hellzerg/optimizer/releases)

<details>
<summary>View recommended settings</summary>

![Optimizer Settings 1](References/Optimizer1.png)
![Optimizer Settings 2](References/Optimizer2.png)

**Configuration Package**: [References/Optimizer.zip](References/Optimizer.zip)
</details>

---

## Performance Validation

### CPU Performance Check
```powershell
# Verify power plan settings
powercfg /query SCHEME_CURRENT SUB_PROCESSOR

# Check CPU boost mode
powercfg /query SCHEME_CURRENT SUB_PROCESSOR PERFBOOSTMODE
```

### Thermal Monitoring
- **HWiNFO64**: Monitor CPU/GPU temps under load
- **Target temps**: CPU <85°C, GPU <80°C during gaming
- **Fan curves**: Custom curves via G-Helper for optimal noise/performance

### Memory Optimization
```powershell
# Enable XMP/DOCP in BIOS for rated RAM speeds
# Verify RAM is running at rated speed (3200MHz for G14 2021)
```

---

## Configuration Files

### Reference Materials
All configuration files and screenshots are available in the `References/` folder:

#### Configuration Files
- **[WinaeroTweaker.ini](References/WinaeroTweaker.ini)** - Complete Winaero Tweaker settings
- **[Optimizer.zip](References/Optimizer.zip)** - Pre-configured Optimizer settings

#### Visual Guides
- **[GHelper1.png](References/GHelper1.png)** - G-Helper recommended configuration
- **[Optimizer1.png](References/Optimizer1.png)** - Optimizer settings page 1
- **[Optimizer2.png](References/Optimizer2.png)** - Optimizer settings page 2

### Power Plan Export
```powershell
# Export optimized power plan
powercfg /export "G14_Optimized.pow"
```

### Startup Optimization
```powershell
# Disable unnecessary startup programs
Get-CimInstance Win32_StartupCommand | Where-Object {$_.Name -like "*Adobe*" -or $_.Name -like "*Steam*"} | ForEach-Object {
    Set-ItemProperty -Path "HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion\Run" -Name $_.Name -Value $null
}
```

### G-Helper Auto-start
- Add G-Helper to startup programs
- Set to start minimized to system tray
- Enable "Matrix display" auto-off to save battery

---

## Advanced Notes

- **Memory**: Enable XMP Profile 1 in BIOS for optimal RAM performance
- **Storage**: Enable TRIM for SSDs, disable indexing on game drives
- **Network**: Disable "Allow the computer to turn off this device" for network adapters
- **Display**: Use 144Hz only when plugged in to preserve battery life
- **Audio**: ROG G14 benefits from EqualizerAPO with custom profiles for better audio

### Critical Don'ts
- Don't disable Windows Update completely (security risk)
- Don't set CPU max to 100% (causes thermal throttling)
- Don't use aggressive CPU boost modes (Mode 2/4) without adequate cooling
- Don't disable all telemetry (breaks some Windows features)# 🖥️ Windows Optimization Guide
> Advanced optimization for ASUS Zephyrus G14 (2021, R9 5900HS + RTX 3060)

## 📋 Table of Contents
1. [Store Apps on LTSC](#store-apps-on-ltsc)
2. [Advanced Power Management](#advanced-power-management)
3. [ROG Hardware Optimization](#rog-hardware-optimization)
4. [System Tweaks](#system-tweaks)
5. [Performance Validation](#performance-validation)
6. [Configuration Files](#configuration-files)

---

## Store Apps on LTSC

### PowerShell Method
```powershell
# Run as Administrator
wsreset -i
```
**Note**: On Windows 10 2021 LTSC, cliprenew.exe errors can be ignored.

### App Installer (WinGet)
Essential for package management. Install from:
```
https://apps.microsoft.com/detail/9nblggh4nns1
```

### Fallback Method
If PowerShell fails, use community package:
```
https://github.com/stdin82/htfx/releases/tag/v0.0.24
```

---

## Advanced Power Management

### Unlock Hidden Power Options
```powershell
# Expose CPU performance boost mode
powercfg -attributes SUB_PROCESSOR 893dee8e-2bef-41e0-89c6-b55d0929964c -ATTRIB_HIDE

# Expose processor performance core parking min cores
powercfg -attributes SUB_PROCESSOR 75b0ae3f-bce0-45a7-8c89-c9611c25e100 -ATTRIB_HIDE
```

### Optimal Performance Settings
```powershell
# Set minimum processor state to 1% (allows deeper C-states)
powercfg /setacvalueindex SCHEME_CURRENT SUB_PROCESSOR PROCTHROTTLEMIN 1

# Cap maximum processor state at 99% (prevents boost clock instability)
powercfg /setacvalueindex SCHEME_CURRENT SUB_PROCESSOR PROCTHROTTLEMAX 99

# Disable CPU performance boost (reduces heat and improves consistency)
powercfg /setacvalueindex SCHEME_CURRENT SUB_PROCESSOR PERFBOOSTMODE 0

# Apply changes
powercfg /setactive SCHEME_CURRENT
```

### Performance Boost Mode Values
- **0** = Disabled (Best thermals, recommended for G14)
- **1** = Enabled (Default)
- **2** = Aggressive (High performance, high heat)
- **3** = Efficient Enabled
- **4** = Efficient Aggressive

---

## ROG Hardware Optimization

### Remove Armoury Crate Completely
```powershell
# Uninstall Armoury Crate components
Get-AppxPackage *ArmouryCrate* | Remove-AppxPackage
Get-AppxPackage *ROG* | Remove-AppxPackage

# Stop and disable services
Stop-Service "ArmouryCrateService" -Force
Set-Service "ArmouryCrateService" -StartupType Disabled
Stop-Service "ArmouryCrateControlInterface" -Force  
Set-Service "ArmouryCrateControlInterface" -StartupType Disabled
```

### G-Helper Configuration
Download: [github.com/seerge/g-helper](https://github.com/seerge/g-helper)

![G-Helper Settings](References/GHelper1.png)

**Recommended Settings**:
- Performance Mode: **Balanced**
- CPU Boost: **Efficient** (Mode 3)
- GPU Mode: **Eco** (for battery) / **Standard** (plugged in)
- Screen refresh: **60Hz** (battery) / **144Hz** (plugged in)

### NVIDIA Driver Optimization
```powershell
# Install only driver, skip GeForce Experience
# Use Studio drivers for stability over Game Ready
```

**NVIDIA Control Panel Settings**:
- Power Management: **Prefer Maximum Performance** (when plugged in)
- Texture Filtering - Quality: **High Performance**
- Threaded Optimization: **On**

---

## System Tweaks

### Essential Registry Modifications
```powershell
# Disable Windows Defender real-time protection (if using alternative)
Set-ItemProperty -Path "HKLM:\SOFTWARE\Policies\Microsoft\Windows Defender\Real-Time Protection" -Name "DisableRealtimeMonitoring" -Value 1

# Disable mouse acceleration
Set-ItemProperty -Path "HKCU:\Control Panel\Mouse" -Name "MouseSpeed" -Value "0"
Set-ItemProperty -Path "HKCU:\Control Panel\Mouse" -Name "MouseThreshold1" -Value "0"
Set-ItemProperty -Path "HKCU:\Control Panel\Mouse" -Name "MouseThreshold2" -Value "0"

# Disable fullscreen optimizations globally
Set-ItemProperty -Path "HKCU:\System\GameConfigStore" -Name "GameDVR_FSEBehavior" -Value "2"
```

### Advanced System Cleanup
```powershell
# Remove OneDrive completely
winget uninstall Microsoft.OneDrive
Remove-Item -Path "$env:USERPROFILE\OneDrive" -Force -Recurse -ErrorAction SilentlyContinue

# Run comprehensive debloat script
iwr -useb https://git.io/debloat | iex
```

### Winaero Tweaker Optimization
Download: [winaero.com/winaero-tweaker/](https://winaero.com/winaero-tweaker/)

**Configuration File**: [References/WinaeroTweaker.ini](References/WinaeroTweaker.ini)

Key Settings:
```ini
# Critical optimizations from WinaeroTweaker.ini
UnwantedAppsDisabled=1
FileExplorerAdsDisabled=1  
LockScreenAdsDisabled=1
StartSuggestionsDisabled=1
TipsAboutWindowsDisabled=1
WelcomePageDisabled=1
SettingsAdsDisabled=1
```

### Optimizer Tool
Download: [github.com/hellzerg/optimizer/releases](https://github.com/hellzerg/optimizer/releases)

<details>
<summary>View recommended settings</summary>

![Optimizer Settings 1](References/Optimizer1.png)
![Optimizer Settings 2](References/Optimizer2.png)

**Configuration Package**: [References/Optimizer.zip](References/Optimizer.zip)
</details>

---

## Performance Validation

### CPU Performance Check
```powershell
# Verify power plan settings
powercfg /query SCHEME_CURRENT SUB_PROCESSOR

# Check CPU boost mode
powercfg /query SCHEME_CURRENT SUB_PROCESSOR PERFBOOSTMODE
```

### Thermal Monitoring
- **HWiNFO64**: Monitor CPU/GPU temps under load
- **Target temps**: CPU <85°C, GPU <80°C during gaming
- **Fan curves**: Custom curves via G-Helper for optimal noise/performance

### Memory Optimization
```powershell
# Enable XMP/DOCP in BIOS for rated RAM speeds
# Verify RAM is running at rated speed (3200MHz for G14 2021)
```

---

## Configuration Files

### Reference Materials
All configuration files and screenshots are available in the `References/` folder:

#### Configuration Files
- **[WinaeroTweaker.ini](References/WinaeroTweaker.ini)** - Complete Winaero Tweaker settings
- **[Optimizer.zip](References/Optimizer.zip)** - Pre-configured Optimizer settings

#### Visual Guides
- **[GHelper1.png](References/GHelper1.png)** - G-Helper recommended configuration
- **[Optimizer1.png](References/Optimizer1.png)** - Optimizer settings page 1
- **[Optimizer2.png](References/Optimizer2.png)** - Optimizer settings page 2

### Power Plan Export
```powershell
# Export optimized power plan
powercfg /export "G14_Optimized.pow"
```

### Startup Optimization
```powershell
# Disable unnecessary startup programs
Get-CimInstance Win32_StartupCommand | Where-Object {$_.Name -like "*Adobe*" -or $_.Name -like "*Steam*"} | ForEach-Object {
    Set-ItemProperty -Path "HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion\Run" -Name $_.Name -Value $null
}
```

### G-Helper Auto-start
- Add G-Helper to startup programs
- Set to start minimized to system tray
- Enable "Matrix display" auto-off to save battery

---

## Advanced Notes

- **Memory**: Enable XMP Profile 1 in BIOS for optimal RAM performance
- **Storage**: Enable TRIM for SSDs, disable indexing on game drives
- **Network**: Disable "Allow the computer to turn off this device" for network adapters
- **Display**: Use 144Hz only when plugged in to preserve battery life
- **Audio**: ROG G14 benefits from EqualizerAPO with custom profiles for better audio

### Critical Don'ts
- Don't disable Windows Update completely (security risk)
- Don't set CPU max to 100% (causes thermal throttling)
- Don't use aggressive CPU boost modes (Mode 2/4) without adequate cooling
- Don't disable all telemetry (breaks some Windows features)
