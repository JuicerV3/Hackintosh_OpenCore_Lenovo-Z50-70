![Screen Shot 2567-05-28 at 22 16 02](https://github.com/JuicerV3/Opencore-Monterey-Z50-70/assets/156657646/ec3ab25c-1342-410f-b5d7-33fb29c11272)

# OpenCore 1.0.1 Stable - macOS Monterey 12.7.5 - Lenovo Z50-70 Type 80E7 59422137

macOS 12 Monterey is the lastest supported macOS for Haswell system (2013 Intel 4th-gen core cpu) for macOS 13 Ventura or newer please refer to [OpenCore Legacy Patcher](https://dortania.github.io/OpenCore-Legacy-Patcher/).

```
* I am not responsible for any damage done to your device. Use at your own risk.
* Please do some research if you concerns about features included in this EFI.
* Before continuing, you are choosing to make these modifications yourself
* if any thing goes wrong, it is your responsible for the damage that happen next.
```

* I will continue to update this EFI _periodically_ as long as im using it. This repo will be archived if im no longer using this OS.

### **Note:** From now you need to generate your own SMBIOS to signin with Apple ID
Use CorpNewt's [GENSMBIOS](https://github.com/corpnewt/GenSMBIOS) to generate platforminfo with **MacBookPro11,4** as an SMBIOS for Monterey. Head to [Dortania's haswell platforminfo guide](https://dortania.github.io/OpenCore-Install-Guide/config-laptop.plist/haswell.html#platforminfo) for in-depth guide.

## latest changes (30 Aug)
* Update to OpenCore 1.0.1

## Previous changes (5 June)
* Native OTA Monterey 12.7.5
* Update to OpenCore 1.0.0
* Update AppleALC to 1.9.0
* Update IntelBluetoothFirmware to 2.4.0
* Added GoldenGate Boot picker GUI (3s timeout)
* Fixed boot chime audio output
* Need your own SMBIOS
* Fixed Bluetooth hash mismatch 
* Wake to blackscreen likely to be fixed

### Known issues
* Screen flickering/blinking (Frequently happens while performing graphics intensive tasks and also happens randomly sometimes.)
* ~~Bluetooth hash mismatch problem caused Bluetooth to fail. (Happens randomly, bluetooth will back to work after sometime)~~
* Laptop will not respond to USB input while in sleep mode but still provide power to USB devices. (Use build-in keyboard/touchpad or power button to wake it up)
* Sleep wake may break in some scenarios. (If laptop somehow wakes during lid close, it will wake to an unresponsive blackscreen and need to force restart)
* Only Volume control keys work natively.
* Only buildin keyboard input work in Bootpicker and login screen.

### What works
* Native OTA Updates
* Metal GPU Acceleration
* WiFi & Bluetooth
* Ethernet
* Onboard Audio & Microphone
* Display Brightness Control
* Webcam
* USB 2.0 & 3.0
* HDMI Output
* Battery read-out (Battery percentage)
* Keyboard & Trackpad
* Volume keys
* Sleep & Wake

### What not works
* lid wake & sleep (Laptop will not enter sleep or wake when open/close the lid. Display will still turn off when lid closed its handle by BIOS/UEFI)
* Airdrop & Continuity Features
* Brightness control keys
* Build-in Windows control keys: Close window, Refresh, Airplane mode, Task switch, Display toggle (Some can be remapped)

### Untested
* VGA Video out
* 3.5mm Audio out
* SDcard Reader

## Laptop Specs/Details
* Model: Lenovo Z50-70 Type 80E7/20354/59422137
* Processor: 4th gen Core i7-4510U Haswell
* CPUID: Intel(R) Core(TM) i7-4510U CPU @ 2.00GHz
* iGPU: intel HD Graphics 4400
* dGPU: ~~GeForce GT 840M 4gb~~
* Ram: 8gb 4x2
* DRIVE1 SSD: WD Green 240GB SATA 2.5 SSD (WDC WDS240G2G0A-00JH30)
* DRIVE2 HDD: Samsung 1TB SATA 2.5 HDD (ST1000LM024 HN-M101MBB)
* Keyboard connection type: PS/2
* Audio: Conexant CX20751/2 @ Intel Lynx Point-LP PCH - High Definition Audio Controller [B2]
* Ethernet: Realtek RTL8168/8111 PCI-E Gigabit Ethernet Adapter (PHY: Realtek RTL8111)
* WLAN: ~~Atheros AR9565 802.11b/g/n Wireless Network Adapter~~ / Intel Dual Band Wireless AC 3160

**Before continue:** If you have difference **Wlan card** other than Intel (Intel Dual Band Wireless AC 3160 compatible kexts were used) **removes/excludes: _AirportItlwm.kext, BlueToolFixup.kext, IntelBTPatcher.kext, IntelBluetoothFirmware.kext_** from **EFI/OC/Kexts** folder and **config.plist** and replace with one that work for your modem. otherwise Wifi&Bluetooth will not work properly or will not boot at all.

## Bios/UEFI Settings
**Configuration**
* Graphic Device: UMA Only
* Intel Virtual Technology: Enable (Can be enabled. Already configured in config.plist)

**Boot**
* Boot mode: Legacy Supported
* Boot Prioriy: UEFI First

## How to check laptop model
* To check **laptop model** head to [Lenovo Z50-70 support](https://pcsupport.lenovo.com/us/en/products/laptops-and-netbooks/lenovo-z-series-laptops/lenovo-z50-70) page. then enter your serial number in the box (S/N number located under your laptop) and then check your laptop name and type (E.g. Z50-70 Laptop (Lenovo) - Type 80E7)
* Laptop **model name** located under your laptop (E.g. 20354)
* If your type/modelname match my laptop then you can use my EFI with little/without issue if not then grab what work build&test it yourself. **Laptop model:(80E7 / 20354 / 59422137)**

## Links/Guides
* https://github.com/acidanthera/OpenCorePkg (OpenCore Bootloader)
* https://dortania.github.io/OpenCore-Install-Guide/ (OpenCore Setup,Installation,Troubleshooting)
* https://dortania.github.io/OpenCore-Post-Install/misc/rtc.html#fixing-rtc-write-issues (Wake restart fix)
* https://openintelwireless.github.io/itlwm/ (Native Intel WiFi)
* https://openintelwireless.github.io/IntelBluetoothFirmware/ (Native Intel Bluetooth)
