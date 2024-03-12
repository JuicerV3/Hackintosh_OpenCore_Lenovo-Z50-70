![Screen Shot 2567-03-12 at 1 08 07 PM](https://github.com/JuicerV3/Opencore-Monterey-Z50-70/assets/156657646/96b9f14f-0e82-442b-b752-4030e62a6657)

# Opencore 0.9.9 Stable - MacOS Monterey 12.7.4 - Lenovo Z50-70 59422137

## Latest changes
* Updated to Monterey 12.7.4 via OTA
* Updated to OpenCore 0.9.9

## Laptop Specs/Details
 * Model: Lenovo Z50-70 59422137
 * Processor: 4th gen Core i7-4510U Haswell
 * CPUID: Intel(R) Core(TM) i7-4510U CPU @ 2.00GHz
 * iGPU: intel HD Graphics 4400
 * dGPU: ~~GeForce GT 840M 4gb~~
 * Ram: 8gb 4x4
 * DRIVE1 SSD: WD Green 240GB SATA 2.5 SSD (WDC WDS240G2G0A-00JH30)
 * DRIVE2 HDD: Samsung 1TB SATA 2.5 HDD (ST1000LM024 HN-M101MBB)
 * Keyboard connection: PS/2
 * Audio: Conexant CX20751/2 @ Intel Lynx Point-LP PCH - High Definition Audio Controller [B2]
 * Ethernet: Realtek RTL8168/8111 PCI-E Gigabit Ethernet Adapter (PHY: Realtek RTL8111)
 * WLAN: ~~Atheros AR9565 802.11b/g/n Wireless Network Adapter~~ / Intel Dual Band Wireless AC 3160

### What works
 * GPU Acceleration
 * WiFi
 * Bluetooth
 * Ethernet
 * Onboard Audio
 * Onboard Microphone
 * Display Brightness
 * Webcam
 * USB 3.0
 * HDMI
 * Battery read-outs
 * Keyboard & Trackpad
 * Sleep Wake

### What not works
 * lid wake/sleep
 * Airdrop 

### Untested
 * VGA Video out
 * 3.5mm Audio out
 * SDcard Reader
 * DVD Drive (SATA hardware should all work)

### Known issues
 * Sleep wake may break on some scenario.
 * Bluetooth hash mismatch problem caused Bluetooth to fail.

## Links/Guides
 * https://github.com/acidanthera/OpenCorePkg (OpenCore Bootloader)
 * https://dortania.github.io/OpenCore-Install-Guide/ (OpenCore Setup,Installation,Troubleshooting)
 * https://dortania.github.io/OpenCore-Post-Install/misc/rtc.html#fixing-rtc-write-issues (Wake restart fix)
 * https://openintelwireless.github.io/itlwm/ (Native Intel WiFi)
 * https://openintelwireless.github.io/IntelBluetoothFirmware/ (Native Intel Bluetooth)
