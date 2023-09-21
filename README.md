# Hackintosh: OpenCore EFI for HP Pavilion Aero 13 Laptop

## Table of Contents

*   [Specifications](#specifications)
*   [What Works](#what-works)
*   [What Doesn't Work](#what-doesnt-work)
*   [Bios Options](#bios-options)
*   [Kexts Used](#kexts-used)
*   [SSDTs Used](#ssdts-used)
*   [Credits](#credits)
*   [Screenshots](#screenshots)

## Specifications
| **Component** | **Model** |
| ------------- | --------- |
| CPU | AMD Ryzen™ 7 5800U (8 cores, 16 threads) |
| RAM | 16GB (2 x 8GB) DDR4-3200 MHz (built-in) |
| IGPU | AMD Radeon™ Vega (integrated)	|
| Display | 13.3" (33.8 cm) WQXGA (2560 x 1600), IPS, micro-edge, anti-glare, 400 nits, 100% sRGB |
| NVMe | Intel SSDPEKNW512G8H 512GB |
| Audio | Realtek ACL298 |
| Wireless | ~~Realtek RTL8821CE-M~~ replaced by Intel AX210 (check https://www.youtube.com/watch?v=ZTtJCZHUgnY) |

## What Works
| Item | Status | Notes |
| --- | --- | --- |
| CPU | ✅ | AMD Vanilla Kernel Patches ([Modify according to yours Core Count](https://github.com/AMD-OSX/AMD_Vanilla)) |
| iGPU | ✅⚠️ | **Some OpenGL issues** |
| Fn Keys | ✅ | SSDT & kext needed. |
| HDMI A/V out | ✅ | _Audio not tested_  |
| USB | ✅ | All ports working with **GUX-RyzenXHCIFix** (New fork of GenericUSBXHCI)|
| Keyboard | ✅ | Voodoops2controller Kext + Karabiner-Elements app for mapping |
| Audio | ✅ | AppleALC kext working with layout-id 21 |
| Trackpad | ✅ | VoodooI2C |
| Intel WIFI | ✅ | AirportItlwm Kext |
| Bluetooth | ✅ | Internal Intel combo card with IntelBluetoothFirmware.kext + BlueToolFixup Kext |
| Battery | ✅ | VoodooBatteryStatus Kext |
| Shutdown/Reboot | ✅ | No issues reported |
### OpenCore version: [0.9.4](https://github.com/acidanthera/opencorepkg/releases)
### Compatible macOS versions
 - Monterey (12.6.9)
 - Big Sur (11.7.10)
 
## What Doesn't Work
| Item | Status | Notes |
| --- | --- | --- |
| Fingerprint Reader | ❌ | No kext |
| Sleep/Wake up | ❓ | **_TODO_** |


<a href="https://www.buymeacoffee.com/aleixsr" target="_blank"><img src="https://cdn.buymeacoffee.com/buttons/v2/default-blue.png" alt="Buy Me A Coffee" style="height: 60px !important;width: 217px !important;" ></a>

***
> **You CAN NOT use SMBIOS from this repository, it MUST be unique for every macOS installation**

***

## BIOS Options
*   Secure Boot **Disabled**
*	**_TBC_**: Increase VRAM to 1GB [UMAF Tool] (https://github.com/DavidS95/Smokeless_UMAF/)
*	**_TBC_**: Use [UMAF](https://github.com/DavidS95/Smokeless_UMAF/) tool to enable `Above 4G decoding`
*	Turn off `Secure Boot` and `Fast Boot`
 
> **[!Warning]** Updating EFI may require clearing NVRAM to take full effect.

## Kexts Used

| Kext | Description |
| --- | --- |
| [Lilu.kext](https://github.com/acidanthera/Lilu) | Platform for arbitrary kext, library, and program patching throughout the system |
| [NootedRed.kext](https://github.com/ChefKissInc/NootedRed) | Lilu plugin for AMD Vega iGPUs |
| [AppleMCEReporterDisabler.kext](https://files.amd-osx.com/AppleMCEReporterDisabler.kext.zip) | Disables AppleIntelMCEReporter which causes panics on AMD CPUs |
| ~~[AmdTscSync.kext](https://files.amd-osx.com/AppleMCEReporterDisabler.kext.zip)~~ | Synchronises the TimeStamp Counter (TSC) Useful for AMD APUs that would be horrendously slow without it |
| [RestrictEvents.kext](https://github.com/acidanthera/RestrictEvents) | Blocking unwanted processes causing compatibility issues on different hardware and unlocking the support for certain features restricted to other hardware |
| [ECEnabler.kext](https://github.com/1Revenger1/ECEnabler) | Embedded Controller fields over 1 byte long needed for battery status |
| [BrightnessKeys.kext](https://github.com/acidanthera/BrightnessKeys) | Provides support for ACPI brightness change notifications from Fn keys |
| [AppleALC.kext](https://github.com/acidanthera/AppleALC) | Patches AppleHDA/AppleGFXHDA to allow unsupported audio codecs and HDMI audio |
| [NVMeFix.kext](https://github.com/acidanthera/NVMeFix) | Patches the NVMe stack (IONVMeFamily) to support Autonomous Power State Transition (APST), and to fix timeout kernel panics on some NVMe controllers |
| [GUX-RyzenXHCIFix](https://github.com/RattletraPM/GUX-RyzenXHCIFix) | A fork of GenericUSBXHCI aimed at analyzing and fixing the USB3 |
| ~~[USBToolBox.kext & UTBMap.kext](https://github.com/USBToolBox/kext)~~ | USBToolBox kext is a kext intended to make common actions for USB mapping easier (do not combine with GUX-RyzenXHCIFix.kext) |
| [AirportItlwm.kext](https://github.com/OpenIntelWireless) | Adds Intel WIFI support |
| [AMDRyzenCPUPowerManagement.kext](https://github.com/trulyspinach/SMCAMDProcessor) | Power management and monitoring of AMD processors |
| [RadeonSensor.kext](https://github.com/ChefKissInc/RadeonSensor) | GPU temperature |
| [VirtualSMC.kext](https://github.com/acidanthera/VirtualSMC) | Advanced Apple SMC emulator in the kernel |
| [SMCAMDProcessor.kext](https://github.com/trulyspinach/SMCAMDProcessor) | Power management and monitoring of AMD processors |
| [SMCBatteryManager.kext](https://github.com/acidanthera/VirtualSMC) | Enables battery readings |
| [SMCSuperIO.kext](https://github.com/acidanthera/VirtualSMC) | Monitors fan speeds |
| [SMCLightSensor.kext](https://github.com/acidanthera/VirtualSMC) | Adds support for ACPI Ambient Light Sensor |
| [SMCRadeonGPU.kext](https://github.com/ChefKissInc/RadeonSensor) | Monitors AMD GPU temperatures |
| [VoodooPS2Controller.kext](https://github.com/acidanthera/VoodooPS2) | Fixes keyboard |
| [VoodooI2C.kext & VoodooU2CHID.kext](https://chefkissinc.github.io/Extras/Kexts/VoodooI2C.zip) | Driver for I2C input devices. The one linked is a pre-release version with added support for AMD I2C controllers|
| [IntelBTPatcher.kext & IntelBluetoothFirmware.kext](https://github.com/OpenIntelWireless/IntelBluetoothFirmware) | Intel Bluetooth Kernel Extensions for macOS |
| [BlueToolFixup.kext](https://github.com/acidanthera/BrcmPatchRAM) | Patches Bluetooth stack to allow non-Apple Bluetooth |



## SSDTs Used

Done with [SSDTTime](https://github.com/corpnewt/SSDTTime) in Windows 11

| Table | Description |
| --- | --- |
| [SSDT-ALS0](https://chefkissinc.github.io/Extras/SSDTs/SSDT-ALS0.aml) | Adds a fake Ambient Light Sensor |
| [SSDT-EC](https://github.com/corpnewt/SSDTTime) | Adds a fake Embedded Controller device |
| [SSDT-HPET](https://github.com/corpnewt/SSDTTime) | Fixes IRQ conflicts in the ACPI tables |
| [SSDT-PLUG-ALT](https://github.com/corpnewt/SSDTTime) | Fixes CPU definitions |
| [SSDT-PNLF](https://chefkissinc.github.io/Extras/SSDTs/SSDT-PNLF.aml) | Creates a fake PNLF device to allow for native brightness control on laptops |
| [SSDT-USBX](https://github.com/corpnewt/SSDTTime) | Enables USB Power Management |
| [SSDT-XOSI](https://github.com/corpnewt/SSDTTime) | Spoof macOS to Windows for some ACPI features |

## Credits
* [Noot AMD Hackintosh Guide](https://chefkissinc.github.io/guide)
* [NootedRed Guide](https://chefkissinc.github.io/nred)
* [ChefKiss Telegram Group](https://t.me/+Bx3MO9Hq8whhNzk9)
* <https://github.com/PIut02/ROG-Zephyrus-G14-GA401-Hackintosh> info/references.
* <https://github.com/kalkmann/Legion-5600H-Hackintosh> info/references.