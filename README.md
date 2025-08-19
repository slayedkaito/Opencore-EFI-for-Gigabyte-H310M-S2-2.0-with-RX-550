# Opencore-EFI-for-Gigabyte-H310M-S2-2.0-with-RX-550

EFI folder for running macOS on Gigabyte H310M S2 2.0 motherboard paired with AMD Radeon RX 550 (Lexa, patched).
This repository provides a working OpenCore EFI setup for Hackintosh enthusiasts.

📋 Specifications

Hardware tested:

Motherboard: Gigabyte H310M S2 2.0

CPU: Intel Core i3/i5/i7 8th/9th Gen (Coffee Lake)

iGPU: Intel UHD Graphics 630 (disabled, using dGPU)

dGPU: AMD Radeon RX 550 Lexa (patched to work on macOS)

RAM: DDR4 16GB (2×8GB)

Storage: SATA SSD / HDD

Audio: Realtek ALC887

Ethernet: Realtek RTL8111

Software:

Bootloader: OpenCore

macOS Version Tested: Ventura

✅ Working

Boot macOS installer and system

RX 550 2Gb (Lexa) fully accelerated with patch (spoofed to RX550 Baffin)

Audio output (ALC887 with AppleALC)

Ethernet (RTL8111 with RealtekRTL8111.kext)

USB ports (with USB map)

Shutdown / Restart / Sleep

⚠️ Not Working / Notes

Intel iGPU disabled (not needed, RX 550 used as primary)

DRM content (Apple TV+, Netflix in Safari) may not work

Always generate your own SMBIOS (don’t use the included one!)

📂 Folder Structure
EFI/
├── BOOT
│   └── BOOTx64.efi
└── OC
    ├── ACPI
    ├── Drivers
    ├── Kexts
    ├── OpenCore.efi
    ├── config.plist
    └── Resources

🔧 Installation

Prepare USB with macOS installer (use gibMacOS
 or macrecovery.py
).

Copy this EFI folder into EFI partition.

Edit config.plist with ProperTree
.

Set your SMBIOS (recommend: iMac19,1 for Coffee Lake).

Adjust Serial Number, Board Serial, MLB, and UUID with GenSMBIOS
.

Boot macOS installer and install macOS.

After successful installation, mount system disk’s EFI and copy EFI folder from USB to system disk.

📖 References

OpenCore Install Guide

WhateverGreen

AppleALC

RealtekRTL8111

⚡ Disclaimer

This EFI is provided as-is. Use at your own risk.
Always generate your own SMBIOS and make necessary adjustments according to your hardware.
