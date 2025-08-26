# OpenCore Install Guide: A Quick Start

This document provides a high-level overview for installing OpenCore on your system. It is meant to be a companion to the official guide, not a replacement.

**WARNING:** An OpenCore configuration is unique to your specific hardware. Using an EFI folder from another user, even if their system seems similar, is highly likely to result in boot failures, kernel panics, and other issues.

**You must build your own EFI folder by carefully following the official guide.**

---

### System Specifications

| Component | Details |
| :--- | :--- |
| Model | Lenovo T470s |
| CPU | Intel i7 6600U |
| GPU | Intel UHD Graphics 620 |
| Storage | Apacer 512GB |
| RAM | 12 GB |
| Audio | ALC298 |
| Wireless | Intel Wireless |
| Keyboard | PS2 |
| Touchpad | Synaptics |
| Target OS | macOS Monterey |

---

### Tested Features

| Status | Feature |
| :--- | :--- |
| Works | Keyboard, Trackpad, Wi-Fi, LAN, Microphone, Speaker |
| Issue | Bluetooth, Webcam |

---

### Official Guide

The definitive source of information for this process is the Dortania OpenCore Install Guide. You **must** follow it for detailed, step-by-step instructions for your specific hardware.

* **Official Guide:** [https://dortania.github.io/OpenCore-Install-Guide/](https://dortania.github.io/OpenCore-Install-Guide/)

### Required Tools

You will need the following tools to create and configure your OpenCore EFI folder.

* **ProperTree:** A cross-platform plist editor. You will use this tool to edit the core configuration file, `config.plist`. ProperTree is essential for managing your kexts, drivers, and all other OpenCore settings.

* **SMBIOS Tools:** You will need to generate unique system information (like `ProductName` and `SerialNumber`) for your build. The official guide recommends using a tool like **MacInfo.py** or a similar utility to get this information.

### High-Level Steps

1.  **Gather Your Files:** Download the latest release of OpenCore, along with the necessary kexts (kernel extensions) and drivers for your hardware. The official guide provides a comprehensive list of recommended files.

2.  **Mount the EFI Partition:** Mount the EFI partition on your USB installer. This is where you will place your OpenCore files.

3.  **Place OpenCore Files:** Copy the essential OpenCore files into the EFI partition's `EFI/OC` folder.

4.  **Edit `config.plist` with ProperTree:** Open your `EFI/OC/config.plist` file using ProperTree. This is the main configuration file that controls how OpenCore works.

5.  **Configure `PlatformInfo`:** Use the SMBIOS tool you selected to generate a unique SMBIOS for your virtual Mac. Use ProperTree to copy this information into the `PlatformInfo` section of your `config.plist`.

6.  **Add Kexts and Drivers:** Place your downloaded kexts and drivers into their respective folders inside the `EFI/OC` directory. Then, use ProperTree to properly "snapshot" these files. This process automatically adds them to your `config.plist`, making them available during boot.

7.  **Finalize Configuration:** Continue following the official guide to complete the rest of the `config.plist` configuration, which includes settings for your CPU, GPU, and other peripherals.

---

### A Critical Warning

**DO NOT DOWNLOAD AND USE SOMEONE ELSE'S EFI FOLDER.**

Your computer's hardware, down to the specific revision and microcode of your motherboard, is different from anyone else's. An EFI designed for another machine can be incompatible and cause critical failures. Following the official guide and building your own EFI from scratch is the only reliable and safe way to ensure a successful and stable installation.
