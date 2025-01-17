# OpenCore-ASUS-ROG-MAXIMUS-XI-HERO

This repository contains:

- OpenCore configuration for ASUS ROG MAXIMUS XI HERO
- Helper script to create EFI directory
- EFI folder archive

## Table of Contents

- [Hardware list](#hardware-list)
- [macOS](#macos)
- [OpenCore](#opencore)
  - [Known Issues](#known-issues)
  - [ACPI](#acpi)
  - [USB](#usb)
  - [Drivers](#drivers)
  - [Kext](#kext)
  - [Resources](#resources)
  - [Tools](#tools)
- [BIOS Settings](#bios-settings)
- [Installation](#installation)
  - [Download EFI folder archive from repository releases page](#download-efi-folder-archive-from-repository-releases-page)
  - [Create EFI directory and files helper script](#create-efi-directory-and-files-with-helper-script)

## Hardware list

Original hardware selection based on [tonymacx86.com Stork's MyHero II Build](https://www.tonymacx86.com/threads/storks-myhero-ii-build-asus-rog-maximus-z370-hero-x-i7-8700k-amd-rx-580.245074/)

| Type                                    | Item                                                                                                                                                                                                       |
|-----------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Motherboard                             | [Asus ROG MAXIMUS XI HERO ATX LGA1151 Motherboard](https://pcpartpicker.com/product/PGTPxr/asus-rog-maximus-xi-hero-atx-lga1151-motherboard-rog-maximus-xi-hero)                                           |
| CPU                                     | [Intel - Core i9-9900K 3.6 GHz 8-Core Processor](https://pcpartpicker.com/product/jHZFf7/intel-core-i9-9900k-36ghz-8-core-processor-bx80684i99900k)                                                        |
| CPU Cooler                              | [Corsair H60 (2018) 57.2 CFM Liquid CPU Cooler](https://pcpartpicker.com/product/F2rmP6/corsair-h60-2018-572-cfm-liquid-cpu-cooler-cw-9060036-ww)                                                          |
| Thermal paste                           | [ARCTIC MX-4 2019 Edition 4 g Thermal Paste](https://pcpartpicker.com/product/JmYLrH/arctic-mx-4-2019-edition-4-g-thermal-paste-actcp00002b)                                                               |
| Memory                                  | [Ballistix Sport LT 64G DDR4, 2400 MHz CL16, BLS4C16G4D240FSB](https://www.amazon.com/gp/product/B01B4F3MNQ)                                                                                               |
| Video Card                              | [Sapphire Radeon RX 580 8 GB PULSE Video Card](https://pcpartpicker.com/product/y2DzK8/sapphire-radeon-rx-580-8gb-pulse-video-card-11265-05)                                                               |
| Wi-Fi + Bluetooth Adapter PCI-E x1 Card | [Fenvi HB1200 WiFi + Bluetooth 4.0 BCM4360](https://www.amazon.com/gp/product/B07T9JD93Y/)                                                                                                                 |
| HDD 1,2                                 | [Samsung 860 Evo 500 GB 2.5" Solid State Drive](https://pcpartpicker.com/product/6yKcCJ/samsung-860-evo-500gb-25-solid-state-drive-mz-76e500bam)                                                           |
| HDD 3                                   | [Seagate Barracuda 6 TB 3.5" 5400RPM Internal Hard Drive](https://pcpartpicker.com/product/ByL48d/seagate-barracuda-6tb-35-5400rpm-internal-hard-drive-st6000dm003)                                        |
| Firewire                                | [SYBA Low Profile PCI-Express Firewire Card](https://www.amazon.com/gp/product/B002S53IG8)                                                                                                                 |
| Power Supply                            | [Corsair RMx (2018) 750 W 80+ Gold Certified Fully Modular ATX Power Supply](https://pcpartpicker.com/product/79tQzy/corsair-rmx-2018-750w-80-gold-certified-fully-modular-atx-power-supply-cp-9020179-na) |
| Case                                    | [Corsair 450D ATX Mid Tower Case](https://pcpartpicker.com/product/9JvRsY/corsair-case-cc9011049ww)                                                                                                        |
| Monitor                                 | [Dell S2415H 23.8" 1920x1080 60 Hz Monitor](https://pcpartpicker.com/product/gZL7YJ/dell-monitor-s2415h)                                                                                                   |
| Camera                                  | [Logitech C920S HD Pro Webcam](https://www.amazon.com/gp/product/B07K95WFWM)                                                                                                                               |

Other accessories:

| Type     | Item                                                                                                                                        |
|----------|---------------------------------------------------------------------------------------------------------------------------------------------|
| Keyboard | [Magic Keyboard with Numeric Keypad](https://www.apple.com/shop/product/MRMH2LL/A/magic-keyboard-with-numeric-keypad-us-english-space-gray) |
| Trackpad | [Magic Trackpad 2](https://www.apple.com/shop/product/MRMF2/magic-trackpad-2-space-gray)                                                    |

## macOS

macOS Ventura version 13.6 (22G120) with FileVault 2 enabled.

You may find great installation guide [here](https://dortania.github.io/OpenCore-Install-Guide/installer-guide/).

## OpenCore

- [OpenCore 0.9.5](https://github.com/acidanthera/OpenCorePkg/releases/tag/0.9.5)
- [Dortania OpenCore Install Guide](https://dortania.github.io/OpenCore-Install-Guide/)
- [Desktop Coffee Lake](https://dortania.github.io/OpenCore-Install-Guide/config.plist/coffee-lake.html)
- [OpenCanopy](https://dortania.github.io/OpenCore-Post-Install/cosmetic/gui.html)
- [FileVault](https://dortania.github.io/OpenCore-Post-Install/universal/security/filevault.html)

### Known issues

**Open**: None.

**Resolved**:

- [x] [Fenvi T-919 Wi-Fi + Bluetooth 4.0 BCM94360CD](https://pcpartpicker.com/product/BJ97YJ/fenvi-fv-t919-none-wi-fi-adapter-fv-t919) started having issues mid-autumn 2020:

  - After shut down and then powering on PC again, Bluetooth will not work when logged in to macOS. However, it's fine at earlier stages, e.g., when typing password during the boot. Workaround: unplug and plug power cord after the shutdown.
  - Keyboard and trackpad were working unstable from time to time (input garbage, freezes). Workaround: power cycle keyboard and trackpad, reboot.

  **Solution**: (06-Dec-2020) Replaced [Fenvi T-919 Wi-Fi + Bluetooth 4.0 BCM94360CD](https://pcpartpicker.com/product/BJ97YJ/fenvi-fv-t919-none-wi-fi-adapter-fv-t919) with [Fenvi HB1200 Wi-Fi + Bluetooth 4.0 BCM4360](https://www.amazon.com/gp/product/B07T9JD93Y/).

- [x] macOS Catalina version 10.15.7 started rebooting suddenly

  - [MemTest86](https://www.memtest86.com/) revealed one [BLS16G4D240FSB](https://pcpartpicker.com/product/8GJtt6/crucial-ballistix-sport-lt-16gb-1-x-16gb-ddr4-2400-memory-bls16g4d240fsb) UDIMM to be faulty. Workaround: Remove faulty UDIMM.

  **Solution**: (30-Nov-2020) Ordered and replaced faulty UDIMM.

### ACPI

As per [Dortania OpenCore Install Guide](https://dortania.github.io/OpenCore-Install-Guide/config.plist/coffee-lake.html#acpi), compiled SSDTs:

- [SSDT-AWAC.aml](ACPI/SSDT-AWAC.aml)
- [SSDT-EC-USBX.aml](ACPI/SSDT-EC-USBX.aml)
- [SSDT-PLUG.aml](ACPI/SSDT-PLUG.aml)
- [SSDT-PMC.aml](ACPI/SSDT-PMC.aml)

### USB

Based on Dortania [USB Mapping Guide](https://dortania.github.io/OpenCore-Post-Install/usb/) and [Intel USB mapping](https://dortania.github.io/OpenCore-Post-Install/usb/intel-mapping/intel.html).

USB port naming taken from [this great reddit post](https://www.reddit.com/r/hackintosh/comments/agzo9l/i99900k_asus_rog_maximus_xi_hero_64gb_ram/).
![USB port mapping](assets/usb-mapping.png)

Resulting [USBMap.kext](Kexts/USBMap.kext) is used.

### Drivers

- OpenCore - `OpenCanopy.efi`, `OpenRuntime.efi`, `ResetNvramEntry.efi`, `ToggleSipEntry.efi`
- [OcBinaryData](https://github.com/acidanthera/OcBinaryData) - [HfsPlus.efi](https://github.com/acidanthera/OcBinaryData/blob/master/Drivers/HfsPlus.efi)

### Kext

- [AppleALC 1.8.5](https://github.com/acidanthera/AppleALC/releases/tag/1.8.5)
- [IntelMausi 1.0.7](https://github.com/acidanthera/IntelMausi/releases/tag/1.0.7)
- [Lilu 1.6.7](https://github.com/acidanthera/Lilu/releases/tag/1.6.7)
- [VirtualSMC 1.3.2](https://github.com/acidanthera/VirtualSMC/releases/tag/1.3.2) (`SMCProcessor.kext`, `SMCSuperIO.kext`)
- [WhateverGreen 1.6.6](https://github.com/acidanthera/WhateverGreen/releases/tag/1.6.6)

### Resources

- [OpenCanopy](https://dortania.github.io/OpenCore-Post-Install/cosmetic/gui.html) theme - `Acidanthera\GoldenGate`
- [OcBinaryData](https://github.com/acidanthera/OcBinaryData) - [Resources/](https://github.com/acidanthera/OcBinaryData/blob/master/Resources)

### Tools

- OpenCore - `OpenControl.efi`, `OpenShell.efi`, `ResetSystem.efi`
- [PassMark MemTest86](tools/README.md#passmark-memtest86)

## BIOS Settings

BIOS:

- Version [2004](https://dlcdnets.asus.com/pub/ASUS/mb/BIOS/ROG-MAXIMUS-XI-HERO-ASUS-2004.ZIP) from the [download page](https://rog.asus.com/motherboards/rog-maximus/rog-maximus-xi-hero-model/helpdesk_bios/).
- Settings [backup](BIOS/V2004.CMO).

BIOS settings based on Dortania [Coffee Lake Intel BIOS settings](https://dortania.github.io/OpenCore-Install-Guide/config.plist/coffee-lake.html#intel-bios-settings) recommendations:

- Advanced

    | Submenu                         | Key / Value                                      | Comment                                                |
    |---------------------------------|--------------------------------------------------|--------------------------------------------------------|
    | CPU Configuration               | Software Guard Extensions (SGX): `Disabled`      |                                                        |
    | CPU Configuration               | Intel (VMX) Virtualization Technology: `Enabled` | Required for [Docker](https://www.docker.com/)         |
    | System Agent (SA) Configuration | VT-d: `Enabled`                                  | Could be enabled as `DisableIoMapper` is set to `true` |
    | System Agent (SA) Configuration | Above 4G Decoding: `Enabled`                     |                                                        |
    | USB Configuration               | XHCI Hand-off: `Enabled`                         |                                                        |
    | USB Configuration               | Legacy USB Support: `Enabled`                    |                                                        |

- Boot

    | Submenu            | Key / Value                   | Comment                                                                                                                                                                 |
    |--------------------|-------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | Boot Configuration | Fast Boot: `Disabled`         |                                                                                                                                                                         |
    | Boot Configuration | Boot Logo Display: `Disabled` |                                                                                                                                                                         |
    | Boot Configuration | Bootup NumLock State: `Off`   | This is a matter of personal preferences                                                                                                                                |
    | Secure Boot        | OS Type: `Windows UEFI mode`  | Ensure `Secure Boot state` is in `Disabled` state. If this is not the case, navigate to `Boot` -> `Secure Boot` -> `Key Management` and select `Clear Secure Boot Keys` |

## Installation

[![Build Status](https://github.com/vovinacci/OpenCore-ASUS-ROG-MAXIMUS-XI-HERO/workflows/test/badge.svg)](https://github.com/vovinacci/OpenCore-ASUS-ROG-MAXIMUS-XI-HERO/actions?query=workflow%3Atest++branch%3Amaster+) [![Latest Release](https://img.shields.io/github/v/release/vovinacci/OpenCore-ASUS-ROG-MAXIMUS-XI-HERO)](https://github.com/vovinacci/OpenCore-ASUS-ROG-MAXIMUS-XI-HERO/releases)[![Release date](https://img.shields.io/github/release-date/vovinacci/OpenCore-ASUS-ROG-MAXIMUS-XI-HERO.svg?label=)](https://github.com/vovinacci/OpenCore-ASUS-ROG-MAXIMUS-XI-HERO/releases)

There are two options to create `EFI` folder:

- Download `EFI` folder archive from repository [releases page](https://github.com/vovinacci/OpenCore-ASUS-ROG-MAXIMUS-XI-HERO/releases)
- Create EFI directory and files with helper script

### Download EFI folder archive from repository releases page

- Navigate to repository [releases page](https://github.com/vovinacci/OpenCore-ASUS-ROG-MAXIMUS-XI-HERO/releases) and download tarball or zip package.
- Unarchive downloaded file locally
- Replace `{{SERIAL}}`, `{{BOARDSERIAL}}` and `{{SMUUID}}` with actual values in `EFI/OC/config.plist`. If you don't have one, great example on how to do this could be found [here](https://dortania.github.io/OpenCore-Post-Install/universal/iservices.html#generate-a-new-serial).
- Replace `{{MACADDRESS}}` with actual `en0` MAC address value in `EFI/OC/config.plist`. Another great example on how to do it is [here](https://dortania.github.io/OpenCore-Post-Install/universal/iservices.html#fixing-en0).
- Once done, mount EFI partition and copy `EFI` folder there.

### Create EFI directory and files with helper script

Requirements:

- [Bash](https://www.gnu.org/software/bash/) > 4.0
- [Coreutils](https://www.gnu.org/software/coreutils/) > 8.15
- [OpenSSL](https://www.openssl.org/) 1.1 (required for Wget)
- [Wget](https://www.gnu.org/software/wget/)

Should you use [Homebrew](https://brew.sh/) on macOS, install it with

```bash
brew install bash coreutils openssl@1.1 wget
```

To create EFI folder, there's no need to clone this repository, just run

```bash
bash -c "$(curl -fsSL https://raw.githubusercontent.com/vovinacci/OpenCore-ASUS-ROG-MAXIMUS-XI-HERO/master/create-efi.sh)"
```

This should download all necessary packages and extract files to the `EFI` folder in the current directory.

Two things to be done manually before moving everything to actual EFI partition:

- Replace `{{SERIAL}}`, `{{BOARDSERIAL}}` and `{{SMUUID}}` with actual values in `EFI/OC/config.plist`. If you don't have one, great example on how to do this could be found [here](https://dortania.github.io/OpenCore-Post-Install/universal/iservices.html#generate-a-new-serial).
- Replace `{{MACADDRESS}}` with actual `en0` MAC address value in `EFI/OC/config.plist`. Another great example on how to do it is [here](https://dortania.github.io/OpenCore-Post-Install/universal/iservices.html#fixing-en0).

After that, mount EFI partition and copy `EFI` folder there.
