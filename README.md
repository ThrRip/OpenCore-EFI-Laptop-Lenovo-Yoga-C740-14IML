# OpenCore-EFI-Laptop-Lenovo-Yoga-C740-14IML

Stable and well-tested OpenCore EFI files for Lenovo Yoga C740-14IML.

## Choosing the right files for your macOS version

The EFI files in the [`main` branch](https://github.com/ThrRip/OpenCore-EFI-Laptop-Lenovo-Yoga-C740-14IML/tree/main) and the [latest release](https://github.com/ThrRip/OpenCore-EFI-Laptop-Lenovo-Yoga-C740-14IML/releases/latest) of this repository only supports the **latest major version of macOS**. If you are on a previous macOS version, you should checkout the branch named `archive/macos-<major version>` depending on your situation. Please note that you will not get any support using files from those branches.

## Details of the machine used in debugging

| Device      | Model               |
| ----------- | ------------------- |
| Laptop      | Lenovo Yoga C740-14IML |
| Motherboard | Lenovo (Unknown)    |
| CPU         | Intel Core i5-10210U |
| RAM         | SK Hynix 8G\*2 2667 MHz |
| Storage     | WDC PC SN730 SDBPNTY-512G-1101 512G M.2 NVMe SSD |
| GPU         | Intel Graphics UHD 630 |
| Audio Chip  | Realtek ALC285 & Intel SST |
| Wireless    | Intel Wi-Fi 6 AX201 160MHz |
| Display     | Lenovo Display FHD  |

## Problems

### Still exist

- The touch screen doesn't work
  > It worked in macOS versions prior to macOS Monterey by switching to `SSDT-XOSI` from `SSDT-GPI0`, adding XOSI patches, patching `VoodooI2CPCIController.cpp` **(thanks @MJYINMC)** and after a sleep.
- The built-in microphone doesn't work

### Solved

<details>
<summary>Expand/Collapse</summary>

_Sorted by date discovered, latest to oldest._

- System Preferences app crashes (or freeze or throw a "Could not load ... preference pane" error) when trying to open the following panes:
  - Siri
  - Accessibility
  - Network
  - Bluetooth
  - Mouse
  > Fixed by removing `IntelBluetoothInjector.kext` and adding `BlueToolFixup.kext`, credit to [extra instructions for Monterey users](https://openintelwireless.github.io/IntelBluetoothFirmware/FAQ.html#what-additional-steps-should-i-do-to-make-bluetooth-work-on-macos-monterey-and-newer) by [OpenIntelWireless](https://github.com/OpenIntelWireless).
- OS start-up takes too long
  > Same cause and solution as the crash of System Preferences.
- Built-in audio output doesn't work
  > `AppleALC.kext` with `layout-id` `61` works.
- Unable to boot into macOS 11.0.1 Installer (Neither download and prepare within the OS, nor through a USB drive)
  > You have to set the value of DVMT pre-allocated by **patching the BIOS** (configuring related entries in the `config.plist` for OpenCore doesn't work on this device). See [here](https://zhuanlan.zhihu.com/p/266400995) for the instructions and **thanks @MJYINMC**.
- Stuck on `apfs_module_start... Previous shutdown cause...` while booting into the installer
  > Not problems with EFI files, solved after reflashing the USB Installer.
- Stuck on `IOG flags ... Generation from SMC report as ... IOPPF ...` while booting into the installer
  > Solved after fixing SSDTs, adding some kernel extensions, etc.
- Stuck on `[ PCI configuration end, bridges 2, devices 20 ]` while booting into the installer
  > Solved after reordering the SSDTs.

</details>
