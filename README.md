<p align="center">
<img width="250" height="250" alt="rogg14" src="https://github.com/user-attachments/assets/e2c9ebb8-0e6c-4b9b-8431-8e6874056fb1" />
  
<h1 align="center"> ROG Zephyrus G14 GA401QM </h1>
<p align="center"> OpenCore Config for Asus ROG Zephyrus G14 (2021) </p>

---

>[!WARNING]
> ## READ THIS BEFORE
> -   This is an EFI version for the GA401QM, a different variant of the GA401. **It may not work when installed on other GA401 variants.**
> -   SIP has been disabled, AMFI is relaxed.
> -   THIS EFI KIT IS **FOR REFERENCE/RESEARCH PURPOSES ONLY.**
> -   THE AUTHOR IS **NOT RESPONSIBLE FOR ANY LEGAL RISKS OR INCIDENTS ARISING DURING ITS USE.**
> -   Remember to back up your data. **DO NOT USE FOR IMPORTANT DATA WITHOUT BACKUP; NO WARRANTY.**

---

## Overview

macOS on ROG Zephyrus G14 (2021) GA401QM - Ryzen 9 5900HS + RTX 3060 Laptop.

<p align="center">
<img width="1920" height="1080" alt="Screenshot macOS" src="https://github.com/user-attachments/assets/0f717b5d-7038-4cee-8cec-3535b353c618" />


---

## Compatibility

<summary><strong>💻Tested Hardware specifications:</strong></summary>

<br />

| Components        | Name                                               | Brand Links                       |
| ------------------| ---------------------------------------------------| ----------------------------------|
| **CPU**           | AMD Ryzen 9 5900HS                                   | AMD                             |
| **iGPU**          | AMD Radeon RX Vega 8                                     | AMD                             |
| **dGPU**          | Nvidia RTX 3060 Laptop 6GB                         | Nvidia |
| **RAM**           | DDR4 24GB / 3200MHz                   | Micron + Corsair                           |
| **Storage**       | SK Hynix HFM001TD3JX013N 1TB                  | SK Hynix                          |
| **WIFI Card**| MediaTek MT7921 (Recommend change to new card) | MediaTek|

**Worked on macOS 15/26 (Tested)**

>[!NOTE]
>On Tahoe 26, Apple removed AppleHDA so you can't use your internal speaker. You need install this [SimpleHDA](https://github.com/laobamac/SimpleHDA) to fix this issue.

---

## Feature and Hardware

- [X] **Boot / Dual Boot**: Boot with other bootloaders (e.g., Windows). You need to keep microsoft folder if you use windows.
- [X] **CPU**: 8 cores / 16 threads; Boost (All cores) to ~4.0 Ghz, Boost (1 core) to ~4.6 Ghz.
- [X] **iGPU**: AMD Radeon RX Vega 8 4096 MB VRAM. [Nootedred Kext](https://github.com/ChefKissInc/NootedRed) (For 4GB VRAM you need to use [Smokeless UMAF.](https://github.com/DavidS95/Smokeless_UMAF/) Because the VRAM adjustment feature for the integrated GPU is hidden in the stock BIOS.)
- [X] **dGPU**: Nvidia RTX 3060 6144 MB VRAM. [Nullmoth Nvidia](https://github.com/nullmoth/nvidia-macos-driver)
- [X] **USB**: All usb ports and external hub worked.
- [X] **Touchpad**: I2C Worked.
- [X] **Sound**: Working perfectly on Sequoia. Need [SimpleHDA](https://github.com/laobamac/SimpleHDA) for Tahoe.
- [ ] **Fn keys**: Most keys are not mapped.
- [ ] **Sleep / Wake**: Unstable i think. (Not Tested)
- [X] **MT7921 Wifi**: Wifi doesn't work natively; it only connects via the SimpleMTK app. [Download the pre-built SimpleMTK.](https://github.com/Thebinhdx/ga401qm-hackintosh/blob/main/SimpleMTK-v0.1-rz616.zip) It's taken from the original SimpleMTKClient code by [laobamc](https://github.com/laobamac). (Note: I tested on speedtest only get ~40 mbps down and <5 mbps up. The speed is quite slow.)
- [ ] **MT7921 Wifi native**: You can try [airportmtkwlan.kext](https://github.com/mnnobre/AirportMtkWlan) (Only work on Sequoia and it doesn't work perfectly. Not recommended for use.)
- [ ] **MT7921 Bluetooth**: The kext is unstable or has issues, causing Bluetooth to not work.
- [ ] **AirDrop / AWDL / Continuity**: Not working.

>[!WARNING]
> - This version doesn't have a MUX switch. So if you want to use an Nvidia graphics card, you need an external monitor that connects via a Type-C port and is capable of outputting video to the computer and disable iGPU AMD. (Tested)
> - If you're using an AMD integrated GPU instead of an Nvidia GPU, you'll need to use `-wenoegpu` in boot-args to disable the Nvidia GPU. However, when using an AMD integrated GPU, you'll also need to disable hardware acceleration on Chromium that isn't optimized for the Nootedred kext. (If you don't disable it, apps running Chromium will lag and become unusable.) (Tested)
> - (Use dGPU) To upgrade from Sequoia to Tahoe, you need follow the instruction which nullmoth wrote in the instructions to upgrade without broken driver.
> - In boot-args, I made a mistake typing `revpatch=cpuname,sbwm`, please correct it to `revpatch=sbvmm,cpuname`. Doing so will make the Tahoe update appear in the software update.

# Credit
- [Apple](https://apple.com) for macOS
- [ChefKissInc](https://github.com/ChefKissInc) for [NootedRed](https://github.com/ChefKissInc/NootedRed) and VoodooI2C
- [DavidS95](https://github.com/DavidS95) for [UMAF](https://github.com/DavidS95/Smokeless_UMAF/)
- [trulyspinach](https://github.com/trulyspinach) for [SMCAMDProcessor](https://github.com/trulyspinach/SMCAMDProcessor)
- [Nullmoth](https://github.com/nullmoth) for [Nvidia macOS](https://github.com/nullmoth/nvidia-macos-driver)
- [laobamac](https://github.com/laobamac) for [SimpleHDA](https://github.com/laobamac/SimpleHDA) and [SimpleMtkWlan](https://github.com/flxxxxddd/SimpleMtkWlan) fork by [flxxxxddd](https://github.com/flxxxxddd)
- And others who contribute to the community
