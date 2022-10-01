TWRP device tree for OnePlus Nord 2T 5G (karen)
===============================================

| Basic                   | Spec Sheet                                                                                                                     |
| -----------------------:|:------------------------------------------------------------------------------------------------------------------------------ |
| Codename                | `karen`                                                                                                                        |
| Device name             | `OP557AL1` (OnePlus Nord 2T 5G)                                                                                                |
| Model names             | `CPH2399` "EU" global model<br/>`CPH2401` India model                                                                          |
| CPU                     | Octa-core                                                                                                                      |
| Chipset                 | MediaTek MT6893 Dimensity 1300 5G (6 nm)                                                                                       |
| GPU                     | Mali-G77 MC9                                                                                                                   |
| Memory                  | 8/12 GB RAM                                                                                                                    |
| Shipped Android Version | Android 12.1 (OxygenOS 12.1)                                                                                                   |
| Storage                 | 128/256 GB                                                                                                                     |
| Battery                 | Li-Po 4500 mAh, non-removable                                                                                                  |
| Display                 | AMOLED, 90Hz, HDR10+ 1080 x 2400 pixels, 20:9 ratio (~409 ppi density)                                                         |
| Camera (Back)(Main)     | 50 MP, f/1.8, 24mm (wide), 1/1.56", 1.0µm, PDAF, OIS<br/>8 MP, f/2.2, 120˚ (ultrawide)<br/>2 MP, f/2.2, (monochrome)           |
| Camera (Front)          | 32 MP, f/2.4, (wide), 1/2.8", 0.8µm                                                                                            |

![image](https://fdn2.gsmarena.com/vv/pics/oneplus/oneplus-nord-2t-5g-1.jpg)

### BOARD_USES_RECOVERY_AS_BOOT

Keep in mind, `karen` has NO `recovery` partition.
Recovery is part of the boot partition, so it takes care of normal boot and recovery.

WIP: currently you can *replace* the boot partition with the below build information, but it **WILL NOT BOOT NORMALLY**.
To go back to your normal OS, you'll have to flash your stock (/rooted) boot.img.

**SO MAKE SURE YOU HAVE A BACKUP `boot.img`**

### Building

Basic instructions. From there you'll need to research.

1. Get started with https://github.com/minimal-manifest-twrp/platform_manifest_twrp_aosp/tree/twrp-12.1
   1. `repo init -u https://github.com/minimal-manifest-twrp/platform_manifest_twrp_aosp.git -b twrp-12.1`
   1. `repo sync`
      Or try a bit faster sync: `repo sync --force-sync -j5 --current-branch --no-clone-bundle --no-tags`)

1. Add this device tree to `device/oneplus/karen`.
   1. `mkdir -p device/oneplus && cd device/oneplus`
   1. `git clone https://github.com/oneplus-karen-roms/android_device_oneplus_karen-twrp.git karen`
   1. `cd ../..`

1. Try an `eng` build.
   1. `export ALLOW_MISSING_DEPENDENCIES=true; . build/envsetup.sh; lunch twrp_karen-eng `
   1. `make -j# bootimage` (where # is a number of threads, try matching your CPU cores)

1. You should now be able to flash `out/target/product/karen/boot.img`
   1. `cd out/target/product/karen`
   1. `fastboot flash boot boot.img`

### Experimental builds

https://github.com/oneplus-karen-roms/android_device_oneplus_karen-twrp/releases

Find the `.img` files under a releases' assets.
And flash like normal.
`fastboot flash boot twrp-boot-xxx.img`
