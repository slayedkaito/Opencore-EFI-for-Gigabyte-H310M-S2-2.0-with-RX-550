# 🍏 Hackintosh EFI - macOS Ventura on H310M S2 2.0 + RX550 + i5-8400

⚠️ This EFI was tested on **macOS Ventura 13.x** and may need adjustments for newer or older versions.  
Last working config before Hackintosh support started declining on Intel systems (post macOS 26 "Tahoe").

---

## 🧠 Specs

| Component       | Model                            |
|----------------|-----------------------------------|
| Motherboard     | Gigabyte H310M S2 2.0              |
| Processor       | Intel Core i5-8400 (UHD 630 iGPU)  |
| Graphics        | AMD RX 550 2GB (Lexa core)         |
| RAM             | 16GB DDR4                          |
| Storage         | SSD 120GB (Windows), HDD 500GB (macOS) |
| Network         | USB WiFi 802.11n                   |
| Bootloader      | OpenCore 0.9.x                     |

---

## 🧩 What Works

✅ Boot to macOS Ventura  
✅ USB Ports (after mapping via Hackintool)  
✅ Graphics acceleration (after RX550 patch)  
✅ Dual boot with Windows 11  
✅ Audio (after AppleALC and layout injection)  
✅ USB WiFi (some chipsets)  
✅ LAN Internet (tested via LAN-to-LAN from laptop)

---

## ❌ What Doesn’t Work

🚫 Native WiFi (no supported chip)  
🚫 iGPU acceleration (not used — RX550 only)  
🚫 USB tethering (unless patched with HoRNDIS)  
🚫 Bluetooth (no compatible device)  
🚫 AirDrop, Handoff, etc (no native Broadcom)

---

## 🔧 Setup Notes

- BIOS settings:
  - VT-d: Disabled
  - Secure Boot: Disabled
  - Above 4G Decoding: Enabled
  - OS Type: Other OS
  - XHCI Handoff: Enabled
  - Serial Port: Disabled

- GPU Patch (RX550 Lexa):
  - `WhateverGreen.kext` + `agdpmod=pikera` boot arg
  - No iGPU injection needed
  - `Display` will show 7MB until fixed

- SMBIOS: `iMac19,1`
- OpenCore Picker: Enabled
- Boot entry preserved using `bootmgfw.efi` trick

---

## 📦 Kexts Used

- `Lilu.kext`
- `WhateverGreen.kext`
- `AppleALC.kext`
- `USBInjectAll.kext` / or custom USBMap.kext
- `VirtualSMC.kext`
- `SMCProcessor.kext`
- `SMCBatteryManager.kext` (optional)
- `RealtekRTL8111.kext` (if using onboard LAN)

---

## 🪛 Tips

- If OpenCore not showing in BIOS, use fallback `BOOTx64.efi` or rename `bootmgfw.efi` (replace original bootmgfw with the opencore bootx64.efi(rename to bootmgfw.efi)
- Windows won’t show in OpenCore if NVRAM broken → Reset NVRAM at boot
- Avoid Windows Update overwriting EFI
- Use **OCAuxiliaryTools** on macOS or **EasyUEFI** on Windows to manage entries (replace opencore bootmgfw with the original one)
- Don’t forget to backup your EFI folder!

---

## 📝 Credits

- OpenCore Team
- Dortania Guide (https://dortania.github.io/)
- Reddit r/Hackintosh
- And me, Kaito (@amia4k60 on tiktok)

