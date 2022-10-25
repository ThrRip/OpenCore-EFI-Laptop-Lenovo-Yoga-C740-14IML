# OpenCore-EFI-Laptop-Lenovo-Yoga-C740-14IML

Stable and well-tested OpenCore EFI files for Lenovo Yoga C740-14IML.

## Details of the PC used in debugging

| Device      | Model               |
| ----------- | ------------------- |
| Laptop      | Lenovo Yoga C740-14IML |
| Motherboard | Lenovo (Unknown)    |
| CPU         | Intel Core i5-10210U |
| RAM         | SK Hynix 8G\*2 2667 MHz |
| Storage     | WDC PC SN730 SDBPNTY-512G-1101 512G M.2 NVMe SSD |
| GPU         | Intel Graphics UHD 630 |
| Audio Chip  | Realtek ALC285 & Intel SST |
| Ethernet (External) | Realtek USB GbE Family Controller |
| Wireless    | Intel Wi-Fi 6 AX201 160MHz |
| Display     | Lenovo Display FHD  |

## Problems

### Still exist

- Touch screen doesn't work
  > It worked in macOS versions prior to macOS Monterey by switching to `SSDT-XOSI` from `SSDT-GPI0`, adding patching of XOSI, patching VoodooI2CPCIController.cpp **(thanks @MJYINMC)** and after a sleeping.
- Built-in microphone doesn't work

### Solved

<details>
<summary>Expand/Collapse</summary>

_Sorted by discovered date, newer to older._

- System Preferences app crash (or freeze or throw a "Could not load ... preference pane" error) when trying to open the following panes:
  - Siri
  - Accessibility
  - Network
  - Bluetooth
  - Mouse
  > Fixed by removing `IntelBluetoothInjector.kext` and adding `BlueToolFixup.kext`, credit to [extra instructions for Monterey users](https://openintelwireless.github.io/IntelBluetoothFirmware/FAQ.html#what-additional-steps-should-i-do-to-make-bluetooth-work-on-macos-monterey-and-newer) by [OpenIntelWireless](https://github.com/OpenIntelWireless).
- Extremely slow OS starting-up
  > Same cause and solution as the crashing of System Preferences.
- The audio chip failed to drive
  > AppleALC.kext with `layout-id` 61 is OK.
- Unable to enter macOS 11.0.1 Installer (Whether it is in-system upgrade or USB upgrade)
  > You have to set the value of DVMT pre-allocated by **patching BIOS** (setting it in the `config.plist` for OpenCore won't work). See [here](https://zhuanlan.zhihu.com/p/266400995) for the instructions and **thanks @MJYINMC**.
- Stuck on `apfs_module_start... Previous shutdown cause...` while booting into the installer
  > Not problems with EFI files, solved after reflash the USB Installer.
- Stuck on `IOG flags ... Generation from SMC report as ... IOPPF ...` while booting into the installer
  > Solved after fixing SSDTs, adding some kernel extensions, etc.
- Stuck on `[ PCI configuration end, bridges 2, devices 20 ]` while booting into the installer
  > Solved after reordering the SSDTs.

</details>

## Author

ThrRip  
Website (Chinese only): [ThrRip's Personal Homepage](https://thrrip.space)
