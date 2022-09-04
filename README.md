# Steps
 - offline install
 - latest nvidia drivers
 - winaero tweaker
 - https://github.com/hellzerg/optimizer/releases
 - https://wpd.app
 - power optimisation 
 - bind left shift

# References
 - https://www.reddit.com/r/OptimizedGaming/comments/su6cq7/windows_1011_optimization_guide/
 
# Power registry
 - HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Contro l\Power\PowerSettings\54533251-82be-4824-96c1-47b60b740d00\be337238-0d82-4146-a960-4f3749d470c7 and select Attributes. Modify the value of "Attributes" from 1 to 2. Data should read “0x00000002 (2)
 
 - HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Power\PowerSettings\54533251-82be-4824-96c1-47b60b740d00\75b0ae3f-bce0-45a7-8c89-c9611c25e100 and select Attributes. Modify the value of "Attributes" from 1 to 2. Data should read “0x00000002 (2)
 
# Add Power registry
 - HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Power\PowerSettings and create Attributes. Modify the value of "Attributes" from 1 to 2. Data should read “0x00000002 (2)
 
 # Power powershell
  - REG ADD HKLM\SYSTEM\CurrentControlSet\Control\Power\PowerSettings\54533251-82be-4824-96c1-47b60b740d00\893dee8e-2bef-41e0-89c6-b55d0929964c /v Attributes /t REG_DWORD /d 2 /f
  
  - REG ADD HKLM\SYSTEM\CurrentControlSet\Control\Power\PowerSettings\54533251-82be-4824-96c1-47b60b740d00\bc5038f7-23e0-4960-96da-33abaf5935ec /v Attributes /t REG_DWORD /d 2 /f
  
# Notes
Powershell 
 - make .ps1 files openable with powershell
  - - https://www.top-password.com/blog/set-ps1-script-to-open-with-powershell-by-default/
 - allow scripts: Set-ExecutionPolicy -ExecutionPolicy Unrestricted
   
