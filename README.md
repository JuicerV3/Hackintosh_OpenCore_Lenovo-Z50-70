![Screen Shot 2567-03-12 at 1 08 07 PM](https://github.com/JuicerV3/Opencore-Monterey-Z50-70/assets/156657646/96b9f14f-0e82-442b-b752-4030e62a6657)

# Opencore 0.9.9 Stable - macOS Monterey 12.7.4 - Lenovo Z50-70 59422137

macOS 12 Monterey is the last supported macOS for Haswell system (Intel 4th-gen core cpu 2013) to install macOS 13 Ventura or newer please refer to [OpenCore Legacy Patcher](https://dortania.github.io/OpenCore-Legacy-Patcher/).

**Before continue:** If you have difference **Wlan card** other than Intel (Intel Dual Band Wireless AC 3160 compatible kexts were used) **removes/excludes: _AirportItlwm.kext, BlueToolFixup.kext, IntelBTPatcher.kext, IntelBluetoothFirmware.kext_** from **EFI/OC/Kexts** folder and **config.plist** and replace with one that work with your modem. otherwise Wifi&Bluetooth will not work properly or will not boot at all.

## Latest changes (12 march)
* Tested OTA Update Monterey 12.7.4
* Update to OpenCore 0.9.9
* Update AirportItlwm to v2.3.0-alpha
* Update IntelBluetoothFirmware to v2.4.0
* Add back IntelBTPatcher v2.4.0
* Update AppleALC to 1.8.9

### Known issues
* Bluetooth hash mismatch problem caused Bluetooth to fail. (This happened randomly)
* Laptop will not respond to USB input while in sleep mode but still provide power to USB devices. (Use build-in keyboard/touchpad or power button to wake it up)
* Sleep wake may break in some scenarios. (If laptop wakes during lid close, it will cause an unresponsive blackscreen and need to force restart) (Shutdown before packing it in your bag. plastic frame can easily trigger keyboard input and cause it to wake up to blackscreen and heat up inside your bag)


### What works
* Native OTA Updates
* Metal GPU Acceleration
* WiFi & Bluetooth
* Ethernet
* Onboard Audio & Microphone
* Display Brightness
* Webcam
* USB 2.0 & 3.0
* HDMI (HDMI audio-out not tested yet. Video-out tested and working)
* Battery read-out (Battery percentage)
* Keyboard & Trackpad
* Sleep & Wake

### What not works
* lid wake & sleep (Laptop will not enter sleep or wake when open/close the lid. Display will still turn off when lid closed its handle by BIOS/UEFI)
* Airdrop

### Untested
* VGA Video out
* 3.5mm Audio out
* SDcard Reader
* DVD Drive (I swapped to HDD caddy for dual hard drives setup. SATA devices should all work including DVD Drive.)

## Laptop Specs/Details
* Model: Lenovo Z50-70 59422137
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

## Links/Guides
* https://github.com/acidanthera/OpenCorePkg (OpenCore Bootloader)
* https://dortania.github.io/OpenCore-Install-Guide/ (OpenCore Setup,Installation,Troubleshooting)
* https://dortania.github.io/OpenCore-Post-Install/misc/rtc.html#fixing-rtc-write-issues (Wake restart fix)
* https://openintelwireless.github.io/itlwm/ (Native Intel WiFi)
* https://openintelwireless.github.io/IntelBluetoothFirmware/ (Native Intel Bluetooth)
