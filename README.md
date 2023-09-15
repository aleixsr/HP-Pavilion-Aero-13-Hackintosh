# Hackintosh
OpenCore EFI for HP Pavilion Aero 13 - be0006ns Laptop ¡¡¡ WORK IN PROGRESS !!!

## Specification
| **Component** | **Model** |
| ------------- | --------- |
| CPU | AMD Ryzen™ 7 5800U (8 cores, 16 threads) |
| RAM | 16GB (2 x 8GB) DDR4-3200 MHz (built-in) |
| IGPU | AMD Radeon™ Graphics integrated	|
| Display | 13.3" (33.8 cm) WQXGA (2560 x 1600), IPS, micro-edge, anti-glare, 400 nits, 100% sRGB |
| NVMe | Intel 512GB |
| Audio | Realtek ACL298 |
| Wireless | Realtek replaced by Intel AX210 (check https://www.youtube.com/watch?v=ZTtJCZHUgnY) |


**OpenCore version**: [0.9.4](https://github.com/acidanthera/opencorepkg/releases)

## Compatible macOS versions
 - Monterey (12.6.8)
 - Big Sur (11.7.10)

## What Works
 - Wi-Fi : Intel AX210
 - Bluetooth
 - HDMI
 - Internal/External audio jacks
 
## What Doesn't Work
 - Fingerprint Reader 
 - Sleep/Wake up

<a href="https://www.buymeacoffee.com/aleixsr" target="_blank"><img src="https://cdn.buymeacoffee.com/buttons/v2/default-blue.png" alt="Buy Me A Coffee" style="height: 60px !important;width: 217px !important;" ></a>

**You CAN NOT use SMBIOS from this repository, it MUST be unique for every macOS installation**

## Steps
 - BIOS:
 	- Turn off Secure Boot
