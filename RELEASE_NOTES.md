# Dell Latitude 3570 - OpenCore Initial Release (macOS Monterey & Ventura)

Initial release of the OpenCore EFI configuration tailored for the **Dell Latitude 3570** (Intel Core i5-6200U / Skylake GT2).

### 🖥 Hardware Specifications
- **Model:** Dell Latitude 3570
- **CPU:** Intel Core i5-6200U @ 2.30 GHz (Skylake-U, 2C/4T)
- **iGPU:** Intel HD Graphics 520 (AAPL,ig-platform-id: `00001619`, 1536 MB)
- **Display:** 15.6" HD (1366x768 @ 60Hz)
- **RAM:** 8 GB DDR3L (2x 4GB @ 1600 MHz)
- **dGPU:** NVIDIA GeForce 920M (Disabled via `SSDT-Disable_GPU_RP01.aml`)
- **Audio:** Realtek ALC3246 / ALC256 (`alcid=13`)
- **Wi-Fi:** Intel Dual Band Wireless-AC 8260 (`AirportItlwm.kext`)
- **Bluetooth:** Intel Bluetooth Wireless Interface (`8087:0a2b`)
- **Touchpad:** Synaptics I2C (`DLL06F3:00 06CB:75DA`) with multi-touch gestures
- **Ethernet:** Realtek RTL8168/8111 PCI Express Gigabit
- **Webcam:** Realtek Integrated HD Webcam

---

### 📦 Key Features & Verification Status
- [x] Verified on **macOS Monterey (12.7.6)** & **macOS Ventura (13.7.8)**
- [x] Full QE/CI Graphics Acceleration on Intel HD 520 & Brightness Control (OCLP used on Ventura)
- [x] Internal Audio, Microphone, and 3.5mm Headphone Jack
- [x] Wi-Fi (Intel AC 8260)
- [x] Synaptics I2C Touchpad with gestures (`-vi2c-force-polling`)
- [x] Sleep, Wake, and Lid detection
- [x] Battery readouts and charging indicators
- [x] Integrated HD Webcam
- [!] Bluetooth: Hardware functions properly, but current EFI release lacks the updated kexts; you will need to patch/fix it yourself
- [x] OpenCanopy graphical boot picker with NVRAM reset
- [?] Realtek Gigabit Ethernet (untested)
- [?] HDMI Video & Audio Out (untested)

---

### ⚠️ IMPORTANT: Post-Download Setup (SMBIOS Injection)
This release is completely sanitized to prevent Apple ID collisions and serial blacklist. **You must generate your own SMBIOS data before booting:**

1. Download [GenSMBIOS](https://github.com/corpnewt/GenSMBIOS).
2. Choose `Generate SMBIOS` and enter model:
   - `MacBookPro13,1` (for macOS Monterey 12.x)
   - `MacBookPro14,1` (for macOS Ventura 13.x)
3. Open `EFI/OC/config.plist` using ProperTree or OCAuxiliaryTools.
4. Navigate to `PlatformInfo -> Generic` and fill in:
   - `SystemProductName`: `MacBookPro13,1` (or `MacBookPro14,1` for Ventura)
   - `SystemSerialNumber`: *(your generated serial)*
   - `MLB`: *(your generated Board Serial)*
   - `SystemUUID`: *(your generated UUID)*
   - `ROM`: *(Your Ethernet/Wi-Fi MAC address)*
5. Save the file and copy the `EFI` folder to your USB drive or ESP partition.

---

### 📥 Release Assets
Download `EFI-Dell-Latitude-3570-OpenCore.zip` below, unzip it, and copy the root `EFI` folder to your boot disk.
