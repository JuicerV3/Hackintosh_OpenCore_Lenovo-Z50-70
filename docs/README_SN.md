![Screenshot 2567-09-15 at 8 52 48 AM](https://github.com/user-attachments/assets/d0b4d485-26c0-4e6c-9aa5-9bfe07ebbc7f)

# OCLP 2.0.0 - macOS Sonoma 14 - Lenovo Z50-70 Type 80E7

## Most things are just the same as Ventura except you'll need a difference SMBIOS and Sonoma specific kexts if avaliable.

Keep in mind macOS 14 Sonoma is **NOT NATIVELY** supported for Haswell system. this modification may cause bug glitches to an operating system.

```
* I am not responsible for any damage done to your device. Use at your own risk.
* Please do some research if you concerns about features included in this EFI.
* Before continuing, you are choosing to make these modifications yourself
* if any thing goes wrong, it is your responsible for the damage that happen next.
```

## Important note
### [!] Don't forget to update your kexts to Sonoma specific version if avaliable.

### From now you need to generate your own SMBIOS to signin with Apple ID
Use CorpNewt's [GENSMBIOS](https://github.com/corpnewt/GenSMBIOS) to generate platforminfo using **MacBookPro15,2** as an SMBIOS for Sonoma. Head to [Dortania's haswell platforminfo guide](https://dortania.github.io/OpenCore-Install-Guide/config-laptop.plist/haswell.html#platforminfo) for in-depth guide.

### Wlan Related kext
If you have difference **Wlan card** other than Intel ([OpenIntelWireless](https://openintelwireless.github.io/) kexts were used for both WiFi and Bluetooth)
#### **removes/excludes:**
* AirportItlwm.kext
* BlueToolFixup.kext
* IntelBTPatcher.kext
* IntelBluetoothFirmware.kext

from **EFI/OC/Kexts** folder and **config.plist** then replace with one that work for your card.

## latest changes (Update 15 September)
* Updated to OpenCore Legacy Patcher 2.0.0 patch

## Step-By-Step Guide
* Build OpenCore Sonoma installer or use my EFI provided
* Generate SMBIOS using **MacBookPro15,2**
* in config.plist
  * Misc > Security > SecureBootModel: set to "Disabled"
  * boot-args: amfi=0x80)**.
* Download latest OpenCore-Patcher.pkg from [OpenCore-Legacy-Patcher Repository](https://github.com/dortania/OpenCore-Legacy-Patcher) copy to usb installer or your prefered storage.
* Boot into installer you may experience slow graphic caused incompatible gpu (low gpu vram. patch with OCLP)
* Once the installation finish. Install **OpenCore-Patcher.pkg** open OpenCore-Patcher app select Post-Install Root Patch and click Start Root Patching.
* Restart

## Known issues (Update 14 September)
Most(every?) issues come from OpenCore itself see [Hackintosh_OpenCore_Lenovo-Z50-70#known-issues](https://github.com/JuicerV3/Hackintosh_OpenCore_Lenovo-Z50-70#known-issues).
* Unable to grant special permissions to apps (ie. Camera Access to Zoom, Discord Microphone) [Workaround click here](https://dortania.github.io/OpenCore-Legacy-Patcher/ACCEL.html#unable-to-grant-special-permissions-to-apps-ie-camera-access-to-zoom)
* [Legacy Metal Graphics issues](https://github.com/dortania/OpenCore-Legacy-Patcher/issues/1008) Even more intense than Ventura
* GeForce Now app crashing due to Metal acceleration problem.

### What works (Update 14 September)
Most things is handle by OpenCore we only use OCLP for GPU Acceleration
* Partial Metal GPU Acceleration
* WiFi & Bluetooth connection
* Ethernet connection
* Onboard Audio & Microphone
* Display Brightness Control
* Webcam
* USB 2.0 & 3.0
* Battery read-out (Battery percentage)
* Keyboard & Trackpad
* Volume keys
* Sleep & Wake (Set "Graphic Device: UMA Only" in bios)

### What not works
* lid wake & sleep
* Airdrop & Continuity Features (Need native wificard & [Bios whitelist removal](https://www.tonymacx86.com/threads/guide-lenovo-g50-70-and-z50-70-bios-whitelist-removal.187340/))
* Brightness control keys (From built-in keyboard)
* Build-in Windows control keys: Close window, Refresh, Airplane mode, Task switch, Display toggle (Some can be remapped idk)

More info [Hackintosh_OpenCore_Lenovo-Z50-70](https://github.com/JuicerV3/Hackintosh_OpenCore_Lenovo-Z50-70)

## Links/Guides
* https://github.com/JuicerV3/Hackintosh_OpenCore_Lenovo-Z50-70 (Native OpenCore Monterey repository)
* https://github.com/dortania/OpenCore-Legacy-Patcher (OCLP)
* https://openintelwireless.github.io/itlwm/ (Native Intel WiFi)
* https://openintelwireless.github.io/IntelBluetoothFirmware/ (Native Intel Bluetooth)
