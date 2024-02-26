### TWRP device tree for POCO X6 PRO (duchamp)

=========================================

The POCO X6 PRO / REDMI K70E (codenamed _"duchamp"_) is a high-end, mid-range smartphone from Xiaomi.

It was released in jan 2024.

## Device specifications

Basic   | Spec Sheet
-------:|:-------------------------
CPU     | Octa-core CPU with 4x Arm Cortex-A715 and 4x Arm Cortex-A510 up to 3.35GHz
Chipset | Mediatek Dimensity 8300
GPU     | Mali-G615 MC6
Memory  | 8/12 GB RAM (LPDDR5 6400Mbps)
Shipped Android Version | 14
Storage | 256/512 GB (UFS 4.0)
Battery | Li-Po 5500 mAh, non-removable
Display | 1440 x 3200 pixels, 6.67 inches, 60/120 hz



## Features

Works:

- [X] ADB
- [X] Decryption (Android 14)
- [X] Display
- [X] Fasbootd
- [X] Flashing
- [X] MTP
- [X] Sideload
- [X] USB OTG
- [X] Vibrator

## Compile

First checkout minimal twrp with aosp tree:

```
repo init --depth=1 -u https://github.com/minimal-manifest-twrp/platform_manifest_twrp_aosp.git -b twrp-12.1
repo sync -j$(nproc --all)
```

Then add these projects to .repo/manifest.xml:

```xml
<project path="device/xiaomi/duchamp" name="device_xiaomi_duchamp" remote="github" revision="twrp-13" />
```

Finally execute these:

```
source build/envsetup.sh
repopick <needed patch>
lunch twrp_duchamp-eng
mka vendorbootimage -j$(nproc --all)
```
## To use it:

```
fastboot flash vendor_boot out/target/product/duchamp/vendor_boot.img
```
