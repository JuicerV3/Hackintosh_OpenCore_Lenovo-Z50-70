![Screen Shot 2567-05-28 at 22 16 02](https://github.com/JuicerV3/Opencore-Monterey-Z50-70/assets/156657646/ec3ab25c-1342-410f-b5d7-33fb29c11272)

# OpenCore 1.0.3 Stable - macOS Monterey 12 - Lenovo Z50-70 (Type 80E7)

**Haswell** system (2013 Intel 4th-gen core cpu) support up to **macOS 12 Monterey**.
macOS 13 Ventura and newer you need [OpenCore Legacy Patcher](https://dortania.github.io/OpenCore-Legacy-Patcher/). check below.
* [[OCLP] Ventura 13 Lenovo Z5070](./README_VT.md)
* [[OCLP] Sonoma 14 Lenovo Z5070](./README_SN.md)

```
* I am not responsible for any damage done to your device. Use at your own risk.
* Please do some research if you concerns about features included in this EFI.
* Before continuing, you are choosing to make these modifications yourself
* if any thing goes wrong, it is your responsible for the damage that happen next.
```

## Important note

#### ***Every laptop are difference, even those with the same model number. So use this EFI as a reference and edit accordingly to your own hardware.***

### You need to generate your own SMBIOS to signin with Apple ID
Use CorpNewt's [GENSMBIOS](https://github.com/corpnewt/GenSMBIOS) to generate platforminfo using `MacBookPro11,4` as an SMBIOS for Monterey. Head to [Dortania's haswell platforminfo guide](https://dortania.github.io/OpenCore-Install-Guide/config-laptop.plist/haswell.html#platforminfo) for in-depth guide.

### What works
* Native OTA Updates
* Full Metal GPU Acceleration
* WiFi & Bluetooth connection
* Ethernet connection
* Onboard Audio & Microphone
* Display Brightness Control
* Webcam
* USB 2.0 & 3.0
* HDMI Output
* Battery read-out
* Keyboard & Trackpad
* Volume keys
* Sleep & Wake

### What not works
* lid wake & sleep
* Airdrop & Continuity Features (Need native wificard & [Bios whitelist removal](https://www.tonymacx86.com/threads/guide-lenovo-g50-70-and-z50-70-bios-whitelist-removal.187340/))
* Brightness control keys (From built-in keyboard)
* Build-in Windows control keys: Close window, Refresh, Airplane mode, Task switch, Display toggle (Some can be remapped idk)

### Untested
* VGA Video out
* 3.5mm Audio out
* SDcard Reader

## Known issues
* Screen flickering/blinking (Frequently happens while performing graphics intensive tasks)
* Sleep wake may break in some scenarios. (If laptop somehow wakes during lid close, it will wake to an unresponsive blackscreen and need force restart)

## Wlan Related kext
If you have difference **Wlan card** other than Intel ([OpenIntelWireless](https://openintelwireless.github.io/) kexts were used for both WiFi and Bluetooth in this EFI)
#### **removes/excludes:**
* `AirportItlwm.kext`
* `BlueToolFixup.kext`
* `IntelBTPatcher.kext`
* `IntelBluetoothFirmware.kext`

from `EFI/OC/Kexts` folder and `config.plist` then replace with one that work for your card. otherwise Wifi&Bluetooth will not work properly or will not boot at all.

## Bios/UEFI Settings
**Configuration**
* Graphic Device: `UMA Only` (this fix wake-from-sleep unresponsive blackscreen)
* Intel Virtual Technology: `Enable` (Can be enabled as its already configured in config.plist)

**Boot**
* Boot mode: `Legacy Supported` (fix [Scrambled Screen on laptops](https://dortania.github.io/OpenCore-Install-Guide/troubleshooting/extended/kernel-issues.html#scrambled-screen-on-laptops))
* Boot Prioriy: `UEFI First`

## Laptop Specs/Details
* Model: `Lenovo Z50-70 Type 80E7/20354`
* Processor: `4th gen Core i7-4510U Haswell`
* CPUID: `Intel(R) Core(TM) i7-4510U CPU @ 2.00GHz`
* iGPU: `intel HD Graphics 4400`
* dGPU: ~~`GeForce GT 840M 4gb`~~
* Ram: `8gb 4x2`
* DRIVE1 SSD: `WD Green 240GB SATA 2.5 SSD (WDC WDS240G2G0A-00JH30)`
* DRIVE2 HDD: `Samsung 1TB SATA 2.5 HDD (ST1000LM024 HN-M101MBB)`
* Keyboard&Trackpad connection type: `PS/2`
* Audio: `Conexant CX20751/2 @ Intel Lynx Point-LP PCH - High Definition Audio Controller [B2]`
* Ethernet: `Realtek RTL8168/8111 PCI-E Gigabit Ethernet Adapter (PHY: Realtek RTL8111)`
* WLAN: ~~`Qualcomm Atheros AR9565 802.11b/g/n Wireless Network Adapter`~~ `Intel Dual Band Wireless AC 3160`

## How to check laptop model
* To check **laptop model** head to [Lenovo Z50-70 support](https://pcsupport.lenovo.com/us/en/products/laptops-and-netbooks/lenovo-z-series-laptops/lenovo-z50-70) page. then enter your serial number in the box (S/N number located under your laptop) and then check your laptop name and type (E.g. `Z50-70 Laptop (Lenovo) - Type 80E7`)
* Laptop **model name** located under your laptop (E.g. `20354`)
* If your type/modelname match this **laptop:(`80E7 / 20354`)** then you can use my EFI with little to no issue. if not then you need to grab what work and build/test it yourself.

## Links/Guides
* https://github.com/acidanthera/OpenCorePkg (OpenCore Bootloader)
* https://dortania.github.io/OpenCore-Install-Guide/ (OpenCore Setup,Installation,Troubleshooting)
* https://dortania.github.io/OpenCore-Post-Install/misc/rtc.html#fixing-rtc-write-issues (Wake restart fix)
* https://openintelwireless.github.io/itlwm/ (Native Intel WiFi)
* https://openintelwireless.github.io/IntelBluetoothFirmware/ (Native Intel Bluetooth)
