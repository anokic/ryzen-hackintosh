# OpenCore EFI for AMD Ryzen Hackintosh (macOS 10.13 - 11.0) RYZEN 2600X B450M VEGA 64

## Specification
| **Component** | **Model** |
| ------------- | --------- |
| CPU | AMD Ryzen 5 2600x @ 3.6GHz |
| Motherboard | MSI B450 Tomahawk Max| 
| RAM | 32GB Kingston DIMM @ 2400Mhz |
| Audio Chipset | ALC892 |
| GPU | MSI RX Vega 64 |
| OS Disk (NVMe) | Kingston A400 480GB |

**macOS version**: 10.14.6 (20B50)  
**OpenCore version**: 0.6.3 

## Compatability macOS versions
 - High Sierra (10.13.x)
 - Mojave (10.14.x)
 - Catalina (10.15.x)
 - Big Sur (10.16/11.0)

## Instructions
  1. Make your USB installer with [**this guide**](https://dortania.github.io/OpenCore-Install-Guide/installer-guide/)
  2. Clone the repository and paste "BOOT" and "OC" directories into your's pendrive "EFI" folder
  3. Download [**GenSMBIOS**](https://github.com/corpnewt/GenSMBIOS) to generate unique SMBIOS information. Run it and select **Generate SMBIOS**, as the model select **iMacPro1,1** or **iMac19,1**.
  4. Open config.plist with [**ProperTree**](https://github.com/corpnewt/ProperTree) and go to PlatformInfo > Generic. Set MLB (Board Serial), SystemSerialNumber (Serial) and SystemUUID (SmUUID) to generated values. Change ROM to your network card's MAC address without the `:` character. [**How to get MAC Address?**](https://www.wikihow.com/Find-the-MAC-Address-of-Your-Computer)
  5. Boot it!  

**You CAN NOT use SMBIOS from this repository, it MUST be unique for every macOS installation**

**DONT FORGET THE NOTE ABOVE**

## Dual monitor / External monitor / Multi Monitor setup issues
I have came upon a sudden and a restless problem only when more then one monitor is plugged in. 
I have two monitors `LG 32"` and `Philips 27"` both `DisplayPort`. 
When my computer boots up inside `login screen` first monitors screen starts blinking. The second monitor is black but blinking trying to connect. 
fter some time the second monitor goes offline or like in few casses it sorts itself out and the monitors work. 
If i unplug and plug back the cables bunch of times i can resolve.

In the issue was resolved by installing [**RDM**](https://github.com/avibrazil/RDM)  
Then tinkering with both displays resolution and refresh rate the problem was solved and blinking/trying to connect stopped. Maybe he needed a saved configuration for the monitors. I'm not sure anymore. I'm glad if this helped you.

To switch to another patch search for `mtrr_update_action` in `config.plist`. Then set `Enabled` to `true` for patch which you want to use. Remember to set `Enabled` to `false` for second PAT patch.  
Don't try to use them both at the same time, it won't work.

****ISSUE WAS RESOLVED BY CHANGING THE MONITOR -- Second monitor didn't like multi monitor setup on MacOS - Monitor was the problem****

## Don't Update the BIOS MacOS Boot Loop
It seems that the new BIOS update for the motherboard B450 Tomahawk Max causes a forever apple logo loop when booting into system.
I downgraded a few updates BIOS updates and voila it worked. Don't update to the latest update of BIOS causes you to be stuck to Apple Logo when trying to boot.

## Audio Fix
I had to change the boot argument from alcid=11 to alcid=1. You can find all the information how to fix it here https://dortania.github.io/OpenCore-Post-Install/universal/audio.html#making-layout-id-more-permanent

## Adobe problems fix
Adobe applications crash on AMD Hackintoshes due to missing intel_fast_memset instructions. Follow [**this guide**](https://gist.github.com/mikigal/8e1f804fcd7dbafbded2f236653be7c8) to get it working!  

## Guides


## All rights go to:
**Software:**
 - [[Bootloader] OpenCore](https://github.com/acidanthera/OpenCorePkg)
 - [[Resources] Picker GUI](https://github.com/acidanthera/OcBinaryData/tree/master/Resources)
 - [[Patch] AMD_Vanilla](https://github.com/AMD-OSX/AMD_Vanilla)
 - [[SSDT] EC-USBX-DESKTOP](https://github.com/dortania/Getting-Started-With-ACPI/blob/master/extra-files/compiled/SSDT-EC-USBX-DESKTOP.aml)
 - [[SSDT] SLEEP-PTXH](./OC/ACPI/SSDT-SLEEP-PTXH.aml)
 - [[Driver] OpenRuntime](https://github.com/acidanthera/OpenCorePkg)
 - [[Driver] OpenCanopy](https://github.com/acidanthera/OpenCorePkg)
 - [[Driver] HFSPlus](https://github.com/acidanthera/OcBinaryData/blob/master/Drivers/HfsPlus.efi)
 - [[Kext] Lilu](https://github.com/acidanthera/Lilu)
 - [[Kext] VirtualSMC](https://github.com/acidanthera/VirtualSMC)
 - [[Kext] WhateverGreen](https://github.com/acidanthera/WhateverGreen)
 - [[Kext] AppleALC](https://github.com/acidanthera/AppleALC)
 - [[Kext] RealtekRTL8111](https://github.com/Mieze/RTL8111_driver_for_OS_X)
 - [[Kext] AMDRyzenCPUPowerManagement](https://github.com/trulyspinach/SMCAMDProcessor)
 - [[Kext] SMCAMDProcessor](https://github.com/trulyspinach/SMCAMDProcessor)
 - [[Kext] NVMeFix](https://github.com/acidanthera/NVMeFix)
 - [[Kext] AppleMCEReporterDisabler](https://github.com/AMD-OSX/AMD_Vanilla/blob/experimental-opencore/Extra/AppleMCEReporterDisabler.kext.zip)  

 **People:**
 - [Apple](https://apple.com) for macOS
 - [AMD-OSX Developers](https://github.com/AMD-OSX) for kernel patches for AMD CPUs
 - [Acidanthera](https://github.com/acidanthera) for OpenCore and most of used kexts
 - [Trulyspinach](https://github.com/trulyspinach) for Ryzen power management and monitoring kexts
 - [Mieze](https://github.com/Mieze) for RealtekRTL8111 kext
 - [Dortania](https://github.com/dortania) for OpenCore configuration guides
 - [XLNC](https://github.com/naveenkrdy) for Adobe patches for AMD CPUs
 - [AMD-OSX Community](https://amd-osx.com) for support while making my Hackintosh
<br>

![Screenshot](/macOS.png?raw=true)
