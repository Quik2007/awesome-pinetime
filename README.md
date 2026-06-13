# Awesome PineTime [![Awesome](https://awesome.re/badge.svg)](https://awesome.re)

> A curated list of awesome projects, tools, documentation and resources for the
> [PineTime](https://pine64.org/devices/pinetime/) - Pine64's open-source,
> hackable smartwatch built around the Nordic **nRF52832** (ARM Cortex-M4F).

The PineTime is a fully open development platform: open firmware, open schematics,
and an active community building operating systems, emulators and companion apps.
This list collects the most useful starting points for hacking on it.

## Contents

- [News](#news)
- [Hardware](#hardware)
- [Operating Systems & Firmware](#operating-systems--firmware)
- [Emulators & Simulators](#emulators--simulators)
- [Companion Apps](#companion-apps)
- [Flashing & Bootloaders](#flashing--bootloaders)
- [Watchfaces & Tools](#watchfaces--tools)
- [Documentation & Wikis](#documentation--wikis)
- [Where to Buy](#where-to-buy)
- [Contributing](#contributing)
- [License](#license)

## News

- [PineTime Pro - March 2026 announcement](https://pine64.org/2026/03/28/pinetime_march_2026/) - Pine64 announced the **PineTime Pro**: dual-core ARM Cortex-M33, 800 KB SRAM + 8 MB PSRAM, a larger AMOLED touchscreen, GPS, blood-oxygen (SpO₂) monitoring and a 6D IMU.

## Hardware

- [PineTime device page](https://pine64.org/devices/pinetime/) - Official product overview: specs, features and ecosystem.
- [Datasheets, schematics & certifications](https://pine64.org/documentation/PineTime/Further_information/Datasheets_schematics_and_certifications/) - Official hardware reference: MCU and peripheral datasheets, board schematics and regulatory certifications.
- [PineTime40](https://github.com/joaquimorg/PineTime40) - Community hardware mod: a drop-in **nRF52840** replacement mainboard for the PineTime (more flash/RAM and USB).

## Operating Systems & Firmware

- [InfiniTime](https://github.com/InfiniTimeOrg/InfiniTime) - The flagship community firmware. Fast, feature-rich, written in modern **C/C++** on **FreeRTOS** with the **LVGL** GUI library and the **NimBLE** Bluetooth stack. Ships on new PineTime units. `GPL-3.0+`
- [wasp-os](https://github.com/wasp-os/wasp-os) - Hackable **MicroPython** firmware for nRF52 watches (PineTime, Colmi P8, Senbono K9) with heart-rate, step counting, watch faces, stopwatch, alarms, timer, calculator and games. `GPL-3.0 / LGPL-3.0`
- [pinetime-os](https://github.com/Weichwolf/pinetime-os) - A compact **bare-metal** operating system in **C** that replaces InfiniTime, featuring a custom BLE stack, tile-based renderer and anti-aliased fonts. `MIT`
- [watchful](https://github.com/lulf/watchful) - PineTime firmware written in **Rust** on the **Embassy** async embedded framework. `Apache-2.0`
- [pinetime-zephyr](https://github.com/najnesnaj/pinetime-zephyr) - PineTime firmware built on the **Zephyr RTOS** for the nRF52. `Apache-2.0`

## Emulators & Simulators

- [InfiniEmu](https://github.com/pipe01/InfiniEmu) - Full hardware emulator of the **nRF52832** (Cortex-M4 + peripherals: accelerometer, touch, heart-rate sensor, SPI display) that boots real **InfiniTime** firmware. Written in **C** with a Go/TypeScript/Vue web front-end. `GPL-3.0`
- [InfiniSim](https://github.com/InfiniTimeOrg/InfiniSim) - Official desktop **simulator** that builds and runs the real InfiniTime UI on your computer (no hardware needed), ideal for developing watch faces and screens. `GPL-3.0`
- [pinetime-emu](https://github.com/Weichwolf/pinetime-emu) - A **Cortex-M4F** emulator that boots PineTime firmware without hardware, simulating nRF52832 peripherals (UART, SPI, I²C, BLE radio) with **SDL2** display rendering and touch input. Written in **C++**.

## Companion Apps

Phone- and desktop-side apps that pair with the watch over Bluetooth LE to push
notifications, control media, sync activity data and flash firmware. Feature
support: ✅ yes · ➖ partial / version-dependent / unconfirmed · ❌ no.

| App | Platforms | License | Firmware | Notif. | Media | Weather | OTA flash | [Resources](https://github.com/InfiniTimeOrg/InfiniTime/blob/main/doc/gettingStarted/updating-software.md#updating-resources) | Activity² | Maintained |
|-----|-----------|---------|----------|:------:|:-----:|:-------:|:---------:|:----------:|:--------:|:----------:|
| [Gadgetbridge](https://codeberg.org/Freeyourgadget/Gadgetbridge) | Android | `AGPL-3.0` | InfiniTime (+ many) | ✅ | ✅ | ➖¹ | ✅ | ✅ | ✅ | ✅ |
| [Amazfish](https://github.com/piggz/harbour-amazfish) | Sailfish OS · Linux · Ubuntu Touch | `GPL-3.0` | InfiniTime (+ Huami) | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ |
| [WatchMate](https://github.com/azymohliad/watchmate) | Linux (GTK4) | `GPL-3.0` | InfiniTime | ✅ | ✅ | ❌ | ✅ | ✅ | ➖ | ➖ |
| [itd](https://git.elara.ws/Elara6331/itd) | Linux (daemon + `itctl` + `itgui`) | `GPL-3.0` | InfiniTime | ✅ | ✅ | ✅ | ✅ | ➖ | ➖ | ✅ |
| [InfiniLink](https://github.com/InfiniTimeOrg/InfiniLink) | iOS · macOS | `GPL-3.0` | InfiniTime | ➖ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ |
| [Siglo](https://github.com/theironrobin/siglo) | Linux (GTK) | `MPL-2.0` | InfiniTime | ➖ | ❌ | ❌ | ✅ | ❌ | ❌ | ❌ |
| [InfiniWindows](https://github.com/TailyFair/InfiniWindows) | Windows | `none`³ | InfiniTime | ❌ | ❌ | ❌ | ✅ | ❌ | ❌ | ❌ |
| [PinePartner](https://github.com/pipe01/PinePartner)⁴ | Android | `AGPL-3.0` | InfiniTime | ✅ | ✅ | ✅ | ✅ | ✅ | ❌ | ✅ |
| [wasptool](https://github.com/wasp-os/wasp-os) | Linux (CLI) | `GPL-3.0 / LGPL-3.0` | wasp-os | ✅ | ❌ | ❌ | ✅ | ✅ | ❌ | ✅ |
| [wasp-companion](https://github.com/Siroj42/wasp-companion) | Linux (GTK) | `MIT` | wasp-os | ✅ | ✅ | ❌ | ➖ | ➖ | ➖ | ❌ |
| [wasp-os-companion](https://github.com/taitberlette/wasp-os-companion) | Android (Flutter) | `none`³ | wasp-os | ✅ | ✅ | ❌ | ✅ | ✅ | ➖ | ❌ |

¹ Gadgetbridge doesn't fetch weather itself; it relays it from a separate provider app (e.g. Breezy Weather).
² Activity = syncs/logs step and heart-rate history off the watch. Apps that only read live values for on-screen display (WatchMate, itd) or list it as planned (wasp-companion) are marked ➖.
³ `none` = no license file published, so the code is effectively all-rights-reserved.
⁴ PinePartner is pre-alpha (v0.0.6) and built around a JavaScript plugin system - its notifications and media control are themselves built-in plugins.

## Flashing & Bootloaders

- [pinetime-mcuboot-bootloader](https://github.com/InfiniTimeOrg/pinetime-mcuboot-bootloader) - The open-source **bootloader** the PineTime ships with (MyNewt + **MCUBoot**), enabling safe over-the-air firmware updates and rollback. `Apache-2.0`
- [nRFConnect](https://www.nordicsemi.com/Products/Development-tools/nRF-Connect-for-mobile) - Nordic's closed-source BLE tool, usable as a bare DFU flasher (Android · iOS; recent iOS builds reportedly no longer flash PineTime). `proprietary`
- [pinetime-flasher](https://github.com/arteeh/pinetime-flasher) - Linux Flatpak/GTK flasher for InfiniTime, RIOT or custom binaries from a URL or file. `Apache-2.0`
- [pinetime-updater](https://github.com/lupyuen/pinetime-updater) - Flash firmware over a **wired SWD** connection with OpenOCD - the reliable recovery path when BLE OTA isn't possible. `Apache-2.0`
- [PinetimeFlasher](https://github.com/ZephyrLabs/PinetimeFlasher) - Windows firmware-flashing helper for InfiniTime. *(license unverified)*
- [WebBLEWatch](https://github.com/hubmartin/WebBLEWatch) - Web Bluetooth proof-of-concept that sets the InfiniTime clock from a browser (time-set only, not a flasher). *(no license file)*

## Watchfaces & Tools

- [GTKWatchFace](https://codeberg.org/MorsMortium/GTKWatchFace) - A themeable **GTK3** watchface generator (Python/C/C++, Linux) that renders designs and converts them into C++ code and font files to compile into **InfiniTime**. `GPL-3.0`
- [ZephyrLabs/Watchfaces](https://github.com/ZephyrLabs/Watchfaces) - A community collection of ready-made watchfaces for the PineTime. `GPL-3.0`
- [InfinitimeExplorer](https://github.com/joaquimorg/InfinitimeExplorer) - A file explorer for browsing the InfiniTime on-device filesystem. *(no license file)*
- [bluetooth-clocks](https://github.com/koenvervloesem/bluetooth-clocks) - Python library and CLI to read and set the time on Bluetooth LE clocks, including InfiniTime/PineTime. `MIT`

## Documentation & Wikis

- [PineTime documentation (pine64.org)](https://pine64.org/documentation/PineTime/) - Official documentation hub for the PineTime.
- [PineTime wiki (wiki.pine64.org)](https://wiki.pine64.org/wiki/PineTime) - Community wiki: overview, hardware details and ecosystem links.
- [PineTime development wiki](https://wiki.pine64.org/wiki/PineTime_Development) - Getting started with firmware development, flashing, bootloaders and tooling.

## Where to Buy

- [Pine64 Store - Global](https://pine64.com/product-category/pinetime-smartwatch/) - Official worldwide store.
- [Pine64 EU Store](https://pine64eu.com/product/pinetime-smartwatch-sealed/) - European store (sealed/dev editions).

## Contributing

Contributions are very welcome! If you know of an awesome PineTime project, tool,
or resource that belongs here, please open a [pull request](https://github.com/Quik2007/awesome-pinetime/pulls).

Read the [contribution guidelines](CONTRIBUTING.md) first, and please follow our
[code of conduct](CODE_OF_CONDUCT.md).

## License

[![CC0-1.0](https://licensebuttons.net/p/zero/1.0/88x31.png)](LICENSE)

To the extent possible under law, the contributors to this list have waived all
copyright and related or neighboring rights to this work. See [LICENSE](LICENSE)
([CC0 1.0 Universal](https://creativecommons.org/publicdomain/zero/1.0/)).
