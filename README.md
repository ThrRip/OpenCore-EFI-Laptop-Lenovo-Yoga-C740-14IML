# OpenCore-EFI-Laptop-Lenovo-Yoga-C740-14IML
Stable and self-use OpenCore EFI files for Lenovo Yoga C740-14IML.

## About macOS Monterey 12
The [main](https://github.com/ThrRip/OpenCore-EFI-Laptop-Lenovo-Yoga-C740-14IML/tree/main) branch of this repository has added the support for macOS Monterey 12. Since this version is still new, there could be some problems waiting for resolving for the EFI files. Feel free to download the preview version of my EFI files from the [Releases](https://github.com/ThrRip/OpenCore-EFI-Laptop-Lenovo-Yoga-C740-14IML/releases) page, test them, and create issues.
> If you still want to use macOS Big Sur 11, check out the [macos-11](https://github.com/ThrRip/OpenCore-EFI-Laptop-Lenovo-Yoga-C740-14IML/tree/macos-11) branch as the files in this branch will likely not work on a version other that macOS Monterey 12.

## Details of the PC used in debugging
| Items       | Model               |
| ----------- | ------------------- |
| Laptop      | Lenovo Yoga C740-14IML |
| Motherboard | Lenovo (Unknown)    |
| CPU         | Intel Core i5-10210U |
| RAM         | SK Hynix 8G*2 2667 MHz |
| Hard Disk   | WDC PC SN730 SDBPNTY-512G-1101 512G M.2 NVMe SSD |
| GPU         | Intel Graphics UHD 630 |
| Sound Card  | Realtek ALC285 & Intel SST |
| Ethernet    | Realtek USB GbE Family Controller |
| WLAN        | Intel Wi-Fi 6 AX201 160MHz |
| Monitor     | Lenovo Display FHD  |

## Problems still exist
- ~~Stuck on `[ PCI configuration end, bridges 2, devices 20 ]`~~
  > Resolved after making the SSDTs in right order.
- ~~Stuck on `apfs_module_start... Previous shutdown cause...`~~
  > Not problems of EFI, resolved after reflash the USB Installer.
- ~~Stuck on `IOG flags ... Generation from SMC report as ... IOPPF ...`~~
  > Resolved after fixing SSDTs, adding some kernel extensions, etc.
- The touch screen ~~failed to drive~~ is not stable during using
  > Resolved after switching to SSDT-XOSI, adding patching of XOSI, patching VoodooI2CPCIController.cpp **(thanks @MJYINMC)**, but touch screen ~~still doesn't work~~ only work after a sleeping.
- ~~Sound Card failed to drive~~
  > AppleALC.kext with layout-id 61 is OK.
- ~~Unable to enter macOS 11.0.1 Installer (Whether it is in-system upgrade or USB upgrade)~~
  > It's able to update if you set DVMT pre-allocated by PATCHING BIOS (not set in OpenCore's config.plist). See [here](https://zhuanlan.zhihu.com/p/266400995) for the instructions and **thanks @MJYINMC**.
- Built-in microphone failed to drive
- ~~Wi-Fi cannot run at full speed~~
  >  Fixed in [4c4d302](https://github.com/ThrRip/OpenCore-EFI-Laptop-Lenovo-Yoga-C740-14IML/commit/4c4d3026d4b51bca91da50043d3b8b2e989215af) with macOS Monterey 12.
- System Preferences app crash (or freeze or throw an "Could not load ... preference pane" error) when trying to open the following panes:
  - Siri
  - Accessibility
  - Network
  - Bluetooth
  - Mouse
- Extremely low OS startup speed

## Author
ThrRip  
Website (Chinese only): [ThrRip's Personal Homepage](https://thrrip.space)
