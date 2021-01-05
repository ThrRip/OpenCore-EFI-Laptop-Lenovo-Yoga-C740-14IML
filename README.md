# OpenCore-EFI-Laptop-Lenovo-YOGA-C740-14IML
 Stable and self-use OpenCore EFI files for Lenovo YOGA C740-14IML.



## Details of the PC Used in Debugging
| Items       | Model               |
| ----------- | ------------------- |
| Laptop      | Lenovo YOGA C740-14IML |
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
  > It's able to update if you set DVMT pre-allocated by PATCHING BIOS (not set in OpenCore's config.plist). See [here](https://zhuanlan.zhihu.com/p/266400995) for the instructions and **thanks @MJYINMC**
- Built-in microphone failed to drive
- Wi-Fi cannot run at full speed

## Author
ThrRip  
Website (Chinese only): [ThrRip's Personal Homepage](https://thrrip.space)
