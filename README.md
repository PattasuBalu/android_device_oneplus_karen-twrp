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
   1. `make -j# recoveryimage` (where # is a number of threads, try matching your CPU cores)
