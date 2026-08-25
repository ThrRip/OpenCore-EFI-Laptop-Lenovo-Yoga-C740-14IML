# OpenCore-EFI-Laptop-Lenovo-Yoga-C740-14IML

Stable and well-tested OpenCore EFI files for Lenovo Yoga C740-14IML.

## Choosing the right files for your macOS version

The EFI files in the [`main` branch](https://github.com/ThrRip/OpenCore-EFI-Laptop-Lenovo-Yoga-C740-14IML/tree/main) and the [latest release](https://github.com/ThrRip/OpenCore-EFI-Laptop-Lenovo-Yoga-C740-14IML/releases/latest) of this repository was only tested against **macOS Tahoe 26**. If you are on a previous macOS version, download an earlier release or checkout the branches named `archive/macos-<major version>`.

## Machine specs

| Component | Model |
| --------- | ----- |
| CPU       | Intel Core i5-10210U |
| RAM       | SK Hynix 8G\*2 2667 MHz |
| Storage   | WDC PC SN730 SDBPNTY-512G-1101 512G M.2 NVMe SSD |
| GPU       | Intel Graphics UHD 630 |
| Audio     | Realtek ALC285 & Intel SST |
| Wireless  | Intel Wi-Fi 6 AX201 160MHz |
| Display   | Lenovo Display FHD |

## Problems

- Built-in audio (speaker and micrphone) doesn't work
- [HeliPort](https://github.com/OpenIntelWireless/HeliPort) is required for Wi-Fi to work
- Bluetooth Low Energy (BLE) doesn't work
- Touch screen doesn't work
