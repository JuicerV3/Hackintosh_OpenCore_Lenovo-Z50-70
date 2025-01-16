![Screenshot 2567-09-15 at 8 52 48 AM](https://github.com/user-attachments/assets/d0b4d485-26c0-4e6c-9aa5-9bfe07ebbc7f)

# OCLP 2.0.0 - macOS Sonoma 14 - Lenovo Z50-70 Type 80E7

## Most things are just the same as Ventura-EFI except you'll need a difference SMBIOS and Sonoma specific kexts if avaliable.

Keep in mind macOS 14 Sonoma is **NOT NATIVELY** supported for Haswell system. this modification may cause bug glitches to an operating system.

```
* I am not responsible for any damage done to your device. Use at your own risk.
* Please do some research if you concerns about features included in this EFI.
* Before continuing, you are choosing to make these modifications yourself
* if any thing goes wrong, it is your responsible for the damage that happen next.
```

## Important note
### [!] Don't forget to update your kexts to Sonoma specific version if avaliable.

#### ***Every laptop are difference, even those with the same model number. So use this EFI as a reference and edit accordingly to your own hardware.***

### You need to generate your own SMBIOS to signin with Apple ID
Use CorpNewt's [GENSMBIOS](https://github.com/corpnewt/GenSMBIOS) to generate platforminfo using `MacBookPro15,2` as an SMBIOS for Sonoma. Head to [Dortania's haswell platforminfo guide](https://dortania.github.io/OpenCore-Install-Guide/config-laptop.plist/haswell.html#platforminfo) for in-depth guide.

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

## Known issues (Update 14 September)
Most(every?) issues come from OpenCore itself see [Hackintosh_OpenCore_Lenovo-Z50-70#known-issues](./README.md#known-issues).
* Unable to grant special permissions to apps (ie. Camera Access to Zoom, Discord Microphone) [Workaround: Unable to grant special permissions to apps](https://dortania.github.io/OpenCore-Legacy-Patcher/ACCEL.html#unable-to-grant-special-permissions-to-apps-ie-camera-access-to-zoom)
* [Legacy Metal Graphics issues](https://github.com/dortania/OpenCore-Legacy-Patcher/issues/1008) Even more intense than Ventura
  * GeForce Now app crashing due to Metal acceleration problem.

## Bios/UEFI Settings
**Configuration**
* Graphic Device: `UMA Only` (this fix wake-from-sleep unresponsive blackscreen)
* Intel Virtual Technology: `Enable` (Can be enabled. I already configured in config.plist)

**Boot**
* Boot mode: `Legacy Supported` (this fix screen tearing)
* Boot Prioriy: `UEFI First`

## Step-By-Step Guide
1. Build OpenCore Ventura installer or use my EFI provided.
2. Generate SMBIOS using `MacBook10,1`
3. in config.plist
   * `Misc > Security > SecureBootModel`: set to `Disabled`
   * `boot-args`: add `amfi=0x80`
4. Download latest `OpenCore-Patcher.pkg` from [OpenCore-Legacy-Patcher Repository](https://github.com/dortania/OpenCore-Legacy-Patcher) copy to usb installer or your prefered storage.
5. Boot into installer and install macOS. (you may experience slow graphic caused incompatible gpu we will patch with OCLP when we boot into system.)
6. Once the installation finish. Install `OpenCore-Patcher.pkg` open OpenCore-Patcher app select `Post-Install Root Patch` and click `Start Root Patching`.
7. Restart the system

More info [Hackintosh_OpenCore_Lenovo-Z50-70](./README.md)

## Links/Guides
* https://github.com/acidanthera/OpenCorePkg (OpenCore Bootloader)
* https://dortania.github.io/OpenCore-Install-Guide/ (OpenCore Setup,Installation,Troubleshooting)
* https://dortania.github.io/OpenCore-Post-Install/misc/rtc.html#fixing-rtc-write-issues (Wake restart fix)
* https://github.com/dortania/OpenCore-Legacy-Patcher (OCLP)