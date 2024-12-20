<h1 align="center"> MSI-Bravo-15 Hackintosh EFI </h1>
/image
<h3 align="center"> MSI Bravo 15 B5DD Ryzen 5 5600H + Rx5500M 15.6inch EFI </h3>

## Intro
:warning: **This is only for educational purposes.**

:warning: **This is not a guide**, please refer to [Dortania](https://dortania.github.io/OpenCore-Install-Guide/prerequisites.html) before doing anything. I am not responsible for any damage. This OpenCore configuration is optimized for my specific hardware, so please use it only as a reference or if you happen to have the same or similar hardware.

:information_source: The EFI's have been tested on Big Sur, Ventura, Sonoma and Sequoia on my [MSI Bravo 15](##specifications).


 <h2> OpenCore EFI For MSI Bravo 15 Ryzen 5 5600H & Radeon RX 5500M</h2>
 OpenCore Ver: 1.0.2</br>
MacOS Supported Ver:</br>
 -   BigSur</br>
-   Monterey<br/>
-   Ventura<br/>
-   Sonomo ( Disable NootedRed.kext and set SecureBootModel to Disabled until installation complete.)<br/>
-   Sequoia ( Disable NootedRed.kext, & set SecureBootModel to Disabled until installation complete.)<br/>



## Specifications
|                 | ‎ ‎ ‎ ‎ ‎ ‎ ‎ ‎ Laptop specifications‎ ‎ ‎ ‎ ‎ ‎ ‎ ‎ ‎ ‎ ‎ ‎ ‎ ‎ ‎ ‎ ‎ ‎ ‎ ‎ ‎ ‎ ‎ ‎ ‎ ‎ ‎ ‎ ‎ ‎ ‎ ‎ ‎ ‎ ‎ ‎ ‎ ‎ ‎ ‎ ‎              |
| ----------------------- | :------------------------------------------------------------------------- |   
| CPU                     | AMD Ryzen™ 5 5600H with Radeon Graphics                                    |
| iGPU                    | Radeon Graphics Cezanne (Vega)                                                   |
| dGPU                    | Radeon RX 5500M [DISABLED]                                     |
| Memory                  | 8GB DDR4 3200MHz                                                          |
| Storage                 |512GB NVMe WD SN350 PCIe Gen4                                                          |
| Network                 | RZ608 802.11ax PCIe Wireless Network Adapter [UNSUPPORTED]                         | 
|| RTL8111 PCI Express Gigabit Ethernet Controller|
| Audio|Realtek ALC256|
|LCD Panel| 15.6" FHD IPS 144Hz|

## What's Working & not working

| Item | Status | Notes |
| --- | --- | --- |
| CPU | ✅ | AMD Vanilla Kernel Patches ([Modify according to yours Core Count](https://github.com/AMD-OSX/AMD_Vanilla)) |
| iGPU | ✅ | NootedRed |
| Brightness Control | ✅ | NootedRed |
| USB | ✅ | All ports working with [USBMap](https://github.com/corpnewt/USBMap "USBMap")|
| Keyboard | ✅ | Voodoops2controller.Kext |
| Audio | ✅ | AppleALC kext working. Best with layout-id 12 |
| Mic | ✅ | Not Working for me, But use the patch [AMDMicrophone](https://github.com/qhuyduong/AMDMicrophone) |
| Trackpad | ✅ | Synaptics Touchpad with AMD I2C Controller |
| Ethernet | ✅ | RealtekRTL8111.kext |
| Battery | ✅ | SMCBatteryManager.kext |
| iServices | ✅ | Message/Facetime tested and working |
| Shutdown/Reboot | ✅ | |
| WIFI  & Bluetooth| ❌ | Unsupported Chipset |
| HDMI A/V out | ❌ | Connected to dGPU  |


## Kext Used

| Kext | Description |
| --- | --- |
| [AMDRyzenCPUPowerManagement.kext](https://github.com/trulyspinach/SMCAMDProcessor) | Power management and monitoring of AMD processors |
| [AppleALC.kext](https://github.com/acidanthera/AppleALC) | Native macOS HD audio for not officially supported codecs |
| [AppleMCEReporterDisabler.kext](https://files.amd-osx.com/AppleMCEReporterDisabler.kext.zip) | Disables AppleIntelMCEReporter which causes panics on AMD CPUs |
| [AmdTscSync](https://github.com/naveenkrdy/AmdTscSync) | Synchronises the TimeStamp Counter (TSC). Generally only useful for AMD APUs (usually laptops) |
| [Lilu.kext](https://github.com/acidanthera/Lilu) | Platform for arbitrary kext, library, and program patching throughout the system |
| [NVMeFix.kext](https://github.com/acidanthera/NVMeFix) | Improve compatibility with non-Apple SSDs |
| [RealtekRTL8111.kext](https://github.com/Mieze/RTL8111_driver_for_OS_X) | Open source driver for the Realtek RTL8111/8168 family |
| [RestrictEvents.kext](https://github.com/acidanthera/RestrictEvents) | Blocking unwanted processes causing compatibility issues on different hardware and unlocking the support for certain features restricted to other hardware |
| [SMCAMDProcessor.kext](https://github.com/trulyspinach/SMCAMDProcessor) | Power management and monitoring of AMD processors |
| [SMCBatteryManager.kext](https://github.com/acidanthera/VirtualSMC) | Enables battery readings |
| [USBMap](https://github.com/corpnewt/USBMap "USBMap") | Python script for mapping USB ports in macOS and creating a custom injector kext |
| [VirtualSMC.kext](https://github.com/acidanthera/VirtualSMC) | Advanced Apple SMC emulator in the kernel |
| [VoodooPS2Controller.kext](https://github.com/acidanthera/VoodooPS2) | Fixes keyboard |
|[BrightnessKeys.kext](https://github.com/acidanthera/BrightnessKeys)|Provides support for ACPI brightness change notifications|
|[ECEnabler](https://github.com/1Revenger1/ECEnabler)|Allows macOS to read EC fields over 8 bits long, removing the need to split them manually. |
|[HoRNDIS.kext](https://github.com/jwise/HoRNDIS)|Driver for macOS that allows you to use your Android phone's native USB tethering mode to get Internet access.|
|[NootedRed.kext](https://github.com/ChefKissInc/NootedRed)|Lilu plugin for AMD Vega iGPUs.|
|[SMCRadeonSensors](https://github.com/ChefKissInc/SMCRadeonSensors)|AMD GPU temperature monitoring on macOS & Install AMDGadget for widget|
|[VoodooI2C.kext](https://chefkissinc.github.io/Extras/Kexts/VoodooI2C.zip)|Driver for I2C input devices.|
|[VoodooRMI.kext](https://github.com/VoodooSMBus/VoodooRMI)|Synaptic Trackpad driver over SMBus/I2C for macOS|
| SMBIOS used  | MacBookPro16,3 (Need to enter your information generated by [GenSMBIOS](http://https://github.com/corpnewt/GenSMBIOS "GenSMBIOS"))  |


## SSDTs Used

Done with [SSDTTime](https://github.com/corpnewt/SSDTTime) in EndeavourOS

| Table |
| --- |
| [SSDT-EC](https://github.com/corpnewt/SSDTTime) |
| [SSDT-PLUG-ALT](https://github.com/corpnewt/SSDTTime) |
| [SSDT-USBX](https://github.com/corpnewt/SSDTTime) |
| [SSDT-XOSI](https://github.com/corpnewt/SSDTTime) |
| [SSDT-ALSO](https://github.com/corpnewt/SSDTTime) |
| [SSDT-HPET](https://github.com/corpnewt/SSDTTime) |
| [SSDT-PMC](https://github.com/corpnewt/SSDTTime) |
| [SSDT-PNLF](https://github.com/corpnewt/SSDTTime) |

Check Dortania's Guide for unsupported hardware like SSD and WLAN cards and replace them with supported ones
Use SSDT-Nvme-DISABLE.aml to disable the Nvme drives that are problematic, else disable it in config.plist


## ⚙️ Important setting for macOS 14.x & 15.x BIOS
- Disable **Secure & Fastboot** Mode from BIOS.
### Default
- <b>SATA Mode</b>: AHCI
### Boot with [Smokeless UMAF](https://github.com/DavidS95/Smokeless_UMAF)'s EFI
- <b>AMD CBS > NBIO Common Options > GFX Configuration > iGPU Configuration</b>: UMA_SPECIFIED (So that the VRAM can be changed)
- <b>AMD CBS > NBIO Common Options > GFX Configuration > UMA Frame buffer Size</b>: 2G (2G Recommended, 1G Minimum)
- <b>AMD CBS > CPU Common Options > Core Performance Boost</b>: <b>Disable</b> ( to Reduce Heat and Power Usage) or <b>Enable</b> (for Gaming Performance)


## Notice
- Sometimes apps stops working or shows an error. Open terminal & run
  `` sudo purge`` it will start working
- When there's a **System update**, disable NootedRed while restarting for update.


## Credits

*   [Dortania](https://dortania.github.io/OpenCore-Install-Guide/) for the guides.
*   [Apple](https://www.apple.com/) for macOS.
*   [Acidanthera](https://github.com/acidanthera) for OpenCore and most Kexts.
*   [Smokeless UMAF](https://github.com/DavidS95/Smokeless_UMAF) for vram.
*   [ExtremeXT](https://github.com/extremext/) for help, corrections, my first EFI and git README info/references.
*   Anyone else that helped to develop and improve hackintoshing.
