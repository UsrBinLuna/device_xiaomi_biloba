# Device Tree for Xiaomi Redmi Note 8 (2021) (biloba)
## This is a WORK IN PROGRESS. Here be dragons.

The Redmi Note 8 (2021) (codenamed "biloba") is a mid-range handheld from Xiaomi.
It was released in May 2021.

|                   Basic | Spec Sheet                                                    |
| ----------------------: | :------------------------------------------------------------ |
| Chipset                 | Mediatek MT6769Z Helio G85                                    | 
| CPU                     | Octa-core (2x2.0 GHz Cortex-A75 & 6x1.8 GHz Cortex-A55)       |
| GPU                     | Mali-G52 MC2                                                  |
| RAM                     | 3/4 GB                                                        |
| Wireless                | Dual-band WiFi 802.11a/b/g/n/ac, cellular GSM/HSPA/LTE        |
| Storage                 | 64/128 GB, eMMC 5.1                                           |
| Battery                 | Li-Po 4000 mAh, non-removable                                 |
| Dimensions              | 158.3 x 75.3 x 8.4 mm                                         |
| Display                 | IPS LCD, 1080 x 2340 pixels, 6.3" (~409 ppi)                  |
| Rear camera             | Main 48 MP, UW 8 MP, Macro 2 MP, Depth 2 MP                   |
| Front camera            | 13 MP, No flash                                               |
| Shipped Android Version | 11 , upgradable to 12 (MIUI)                                  |


![xiaomi-redmi-note8-2021-0](https://user-images.githubusercontent.com/67978777/190860585-55948bbc-5e02-4fb6-ae48-c3cc5c9f71e6.jpg)
---
# Known issues
- Reboots to FB, must flash vbmeta with --disable-veritication
- Once flashed VBMeta, it'll reboot to Lineage Recovery and complain about MISC and APEX in system_root not existing
---
# How to build
1. Repo sync the manifest for your chosen ROM (So far only tested on Android 12.1 ROMs)
2. Get prebuilt files (vendor) (NOTE: this is temporary, until someone makes vendor trees.)
    1. Get stock firmware (13.0.2.SCUMIXM) from XFU (get Fastboot ROM [from here - XFU link](https://xiaomifirmwareupdater.com/miui/biloba/stable/V13.0.4.0.SCUMIXM/))
    2. Extract the TGZ file
    3. In the `images` folder, extract super.img with [lpunpack](https://github.com/unix3dgforce/lpunpack) (Thanks to UNIX3Dgforce)
    4. Copy the `vendor_a.img` to the `prebuilts` folder of the device tree with the name `vendor.img`.
3. Run `breakfast` and enter lineage_biloba-userdebug
4. If `breakfast` shows no error, run `mka -j#` to build the ROM. (Replace -j# with the amount of threads you want to use. Eg: -j4)
5. Wait. If any errors related to the DT appear, report them in the `Issues` tab of this repository.
