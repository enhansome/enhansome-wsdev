# Awesome WonderSwan Development with stars

A curated list of awesome WonderSwan/WonderSwan Color development resources and tools. Inspired by the [awesome](https://github.com/sindresorhus/awesome) ⭐ 498,335 | 🐛 105 | 📅 2026-08-18 list.

## Contents

* [Introduction](#introduction)
  * [Getting started](#getting-started)
* [Documentation](#documentation)
  * [Datasheets](#datasheets)
  * [Other documentation](#other-documentation)
* [Emulators](#emulators)
  * [Peripheral emulators](#peripheral-emulators)
  * [Test ROMs](#test-roms)
* [Software development](#software-development)
  * [Libraries](#libraries)
    * [Music drivers](#music-drivers)
  * [Tools](#tools)
    * [Graphics utilities](#graphics-utilities)
* [Source code](#source-code)
  * [Boilerplate](#boilerplate)
  * [Demos](#demos)
  * [Games](#games)
  * [Other programs](#other-programs)
  * [Miscellaneous](#miscellaneous)
* [WonderWitch](#wonderwitch)
  * [WW tools](#ww-tools)
  * [WW documentation](#ww-documentation)
  * [Open source WW programs](#open-source-ww-programs)
* [Open source hardware](#open-source-hardware)
  * [Cartridges](#cartridges)
  * [Peripherals](#peripherals)
  * [Screen capture](#screen-capture)
  * [Other hardware development](#other-hardware-development)
* [Historical](#historical)

## Introduction

The Bandai WonderSwan is a handheld game console released and supported by Bandai from 1999 to 2003 in Japan,
with later follow-ups in the form of the 2000 WonderSwan Color and 2002 SwanCrystal. It is the last piece of
hardware with design input from the legendary Gunpei Yokoi, as well as [Asuka Langley's handheld of choice](https://img.asie.pl/t9zJ.jpg).

While this list focuses on "bare metal" WonderSwan development (cartridge ROM as output), note that there exists
an official homebrew SDK for the console called the [WonderWitch](http://wonderwitch.qute.co.jp/) created by Qute Corporation,
which requires different targetting (custom .fx file format, FreyaBIOS hardware abstraction layer, FreyaOS libraries,
more restrictive IRAM/SRAM layout). Tools and examples for the WonderWitch are present in their own section; however,
many other entries (such as hardware documentation or graphics converters) are applicable to both environments.

### Getting started

For native WonderSwan development, I personally recommend the following sources:

* [Wonderful Toolchain Wiki](https://wonderful.asie.pl/wiki/doku.php?id=wswan:index) - documentation for the open-source WonderSwan/WonderWitch homebrew toolchain,
* [WSdev Wiki](https://ws.nesdev.org/wiki/Main_Page) - hardware documentation.

For native WonderSwan and WonderWitch development alike, you may find a serial port adapter useful. The [ConsoleMods Wiki](https://consolemods.org/wiki/WonderSwan:RS-232_Serial_Cable_Mod)
provides a list of both purchaseable adapters and DIY building projects.

## Documentation

* **[WSdev Wiki](https://ws.nesdev.org/wiki/Main_Page)** - the most recent and actively developed documentation source, hosted by nesdev.org.
* [STSWS](http://perfectkiosk.net/stsws.html) - contains some information not yet on the WSdev wiki.
* [WSMan](http://daifukkat.su/docs/wsman/) - older documentation source.

### Datasheets

#### NEC V30MZ CPU

The NEC V30MZ is an 80186-compatible CPU for low-power platforms with an efficient pipeline design. It should not be confused with the
NEC V20/V30 line of CPUs, which provide additional opcodes and features on top of the 8086 architecture.

For a variety of reasons, NEC's documentation (and some WonderSwan documentation) uses unique NEC opcode names, while other sources
and assemblers typically use Intel opcode names. A translation map between the two is available [as part of STSWS](http://perfectkiosk.net/stsws.html#cpu_8086_translation_map).

* [NEC V30MZ Preliminary User's Manual](https://www.renesas.com/us/en/document/lbr/v30mztm-hardware-preliminary)

#### Other

* [Seiko S-3511A](http://perfectkiosk.net/S-3511A.pdf) - cartridge RTC.
* [Fujitsu MBM29DL400TC](https://github.com/up-n-atom/WonderWitch/blob/main/Datasheets/MBM29DL400BC-12PFTN_to_MBM29DL400TC-90PFTN.pdf) ⭐ 13 | 🐛 0 | 📅 2021-10-05 - WonderWitch NOR flash.

### Other documentation

* [Retail cartridges](https://github.com/RSDuck/nileswan/blob/main/docs/retail_cartridges.md) ⭐ 82 | 🐛 3 | 🌐 HTML | 📅 2026-06-24 - cartridge logic analyzer and requirement documentation.
* [splashbuilder readme](https://github.com/Godzil/splashbuilder/blob/master/README.md) ⭐ 14 | 🐛 2 | 🌐 Python | 📅 2021-04-13 - WonderSwan Color custom boot splash format.
* [Everything You Never Wanted to Know about the WonderSwan RTC](https://forums.nesdev.org/viewtopic.php?t=21513)
* [.WSR file format documentation](archive/in_wsr.txt) (Japanese) - popular WonderSwan standalone/emulated music file format.

## Emulators

* **[Mesen 2](https://github.com/SourMesen/Mesen2/) ⚠️ Archived** (GPL-3.0) - high accuracy, extensive built-in debugger and profiler, recommended for development.
* [NitroSwan](https://github.com/FluBBaOfWard/NitroSwan) ⭐ 76 | 🐛 13 | 🌐 C | 📅 2026-08-12 - WonderSwan emulator for Nintendo DS/DSi, user friendly WonderWitch support.
  * [SwanGBA](https://github.com/FluBBaOfWard/SwanGBA/) ⭐ 48 | 🐛 3 | 🌐 Assembly | 📅 2026-08-12 - GBA version of the above, does not run at full speed.
* [StoicGoose](https://github.com/xdanieldzd/StoicGoose) ⭐ 48 | 🐛 10 | 🌐 C# | 📅 2026-01-11 (MIT) - C# WonderSwan emulator.
* [ares](https://ares-emu.net/) (ISC) - high accuracy.
* [Mednafen](https://mednafen.github.io/) (GPL-2.0) - serial port emulation, built-in debugger.
  * [BizHawk](https://tasvideos.org/Bizhawk) - WonderSwan core based on Mednafen, features Lua scripting and rewind/movie support.
  * [wf-mednafen](https://codeberg.org/WonderfulToolchain/wf-mednafen/releases/) - fork of Mednafen with emulation fixes and debugger UI/UX improvements, based on mednafenPceDev's work.
  * [WonderDroid Ultra](https://f-droid.org/packages/com.atelieryl.wonderdroid/) - fork of Mednafen, Android port.
* [Oswan](sourceforge.jp/projects/oswan/devel) (GPL-2.0) - legacy WonderSwan emulator with a built-in debugger.

### Peripheral emulators

These emulators are currently only supported by Mednafen by editing its `wswan.excomm` configuration option.

* [WonderFence](https://bitbucket.org/trap15/wonderfence/src/master/) (MIT) - MobileWonderGate internet adapter emulator.

## Test ROMs

* [Robert Peip's test ROMs](https://github.com/MiSTer-devel/WonderSwan_MiSTer/tree/main/testroms) ⭐ 15 | 🐛 11 | 🌐 VHDL | 📅 2026-08-15 - sprite priority/window testing tool
* [ws-test-suite](https://github.com/asiekierka/ws-test-suite) ⭐ 5 | 🐛 0 | 🌐 C | 📅 2025-11-08 (MIT) - assorted hardware tests and testing tools
* [WSTimingTest](https://github.com/FluBBaOfWard/WSTimingTest) ⭐ 4 | 🐛 0 | 🌐 Assembly | 📅 2023-09-10 - V30MZ CPU timing
* [WSCPUTest](https://github.com/FluBBaOfWard/WSCPUTest) ⭐ 3 | 🐛 3 | 🌐 Assembly | 📅 2025-05-19 - V30MZ CPU behaviour
* [WSHWTest](https://github.com/FluBBaOfWard/WSHWTest) ⭐ 3 | 🐛 0 | 🌐 Assembly | 📅 2025-08-04 - SoC interrupt/PPU timer handling
* [KarnakTest](https://github.com/FluBBaOfWard/KarnakTest) ⭐ 1 | 🐛 0 | 🌐 Assembly | 📅 2025-07-09 - PCv2 KARNAK timer/ADPCM mapper testing
* [rtctest](https://forums.nesdev.org/viewtopic.php?t=21513) - "2003 mapper + S-3511" RTC protocol and behaviour

## Software development

* **[Wonderful](https://wonderful.asie.pl/)** - gcc-ia16 based C/ASM toolchain for WonderSwan and WonderWitch.
* [owswan](https://github.com/jounikor/owswan) ⭐ 11 | 🐛 0 | 🌐 C | 📅 2022-10-08 - OpenWatcom-based WonderSwan toolchain.
* [Kyoui](https://asie.pl/files/kyoui_2004_11_02.zip) - (mirror) tools for compiling WonderSwan binaries using OpenWatcom.
* [WSLink](https://bitbucket.org/trap15/wonder/src/master/) (MIT) - NASM linker outputting WonderSwan and WonderWitch compatible binaries.

### Libraries

* [libws](https://codeberg.org/WonderfulToolchain/target-wswan-syslibs/tree/main/libws) (zlib) - hardware abstraction functions
* [libwsx](https://codeberg.org/WonderfulToolchain/target-wswan-syslibs/tree/main/libwsx) (zlib) - decompressors and other useful functions
* [LZSS decompression routine](archive/orion-lzss-decompression-routine.asm) (public domain)

#### Music drivers

* [Cygnals](github.com/joffb/cygnals) (MIT) - partially Furnace compatible audio driver.
* [WonderSwan Total Sound Driver](https://github.com/Shaw02/WTD) ⭐ 12 | 🐛 1 | 🌐 Assembly | 📅 2019-07-18

### Tools

* [Dekadence WonderSwan Tools](https://github.com/superjohan/wonderswan-tools) ⭐ 15 | 🐛 4 | 🌐 Python | 📅 2022-12-15 (MIT) - assorted Python scripts.
* [splashbuilder](https://github.com/Godzil/splashbuilder) ⭐ 14 | 🐛 2 | 🌐 Python | 📅 2021-04-13 (BSD-3-Clause) - toolchain for creating custom WonderSwan Color boot splashes.

#### Graphics utilities

* **[SuperFamiconv](https://github.com/Optiroc/SuperFamiconv) ⭐ 189 | 🐛 22 | 🌐 C++ | 📅 2026-07-03** (MIT) - tile/map converter with flexible palette/optimization options and mostly-complete WS/WSC support.
* [bmp2swan](http://onorisoft.free.fr/retro.htm?ws/ws.htm) - simple bitmap converter.

## Source code

### Boilerplate

* [wonder/template](https://bitbucket.org/trap15/wonder/src/master/samples/template/) - NASM-based template.

### Demos

* [Bad Apple!! for WSwan](https://github.com/asiekierka/bad-apple-for-wswan) ⭐ 14 | 🐛 0 | 🌐 Java | 📅 2022-06-25 (MIT)
* [#wonderwitch IRC channel promo](https://github.com/tslanina/Retro-WonderSwanColor-Promo) ⭐ 0 | 🐛 0 | 🌐 Assembly | 📅 2023-11-22 (MIT)
* [HBlank Cylinder Effect](https://github.com/joffb/wsc-witch-cylinder) ⭐ 0 | 🐛 0 | 🌐 C | 📅 2023-12-17

### Games

* [Inufuto's games](http://inufuto.web.fc2.com/8bit/) - written using a custom C-like toolchain.
* [SwanDriving](http://sebastianmihai.com/swan-driving.html) ([Mono](http://sebastianmihai.com/swan-driving-bw.html)) - tech demo written with NASM.
* [WonderSnake](https://github.com/tslanina/Retro-WonderSwanColor-Wondersnake) ⭐ 9 | 🐛 0 | 🌐 Assembly | 📅 2017-04-24 (GPL-3.0) - Snake game written with Borland TASM.

### Other programs

* [ELKS](https://github.com/ghaerr/elks) ⭐ 1,690 | 🐛 27 | 🌐 C | 📅 2026-08-13 (GPL-2.0 + others) - Embedded Linux Kernel Subset kernel/operating system.
* [CartFriend](https://github.com/WonderfulToolchain/ws-cartfriend) ⭐ 43 | 🐛 6 | 🌐 C | 📅 2026-01-06 (GPL-3.0) - WonderSwan cartridge menu/launcher
* [144p Test Suite for WS](https://github.com/asiekierka/240p-test-ws) ⭐ 7 | 🐛 1 | 🌐 C | 📅 2026-06-14 (GPL-3.0) - 240p Test Suite-inspired user-side testing tool
* [Chips1](https://github.com/asiekierka/chips1) ⭐ 4 | 🐛 0 | 🌐 Roff | 📅 2026-03-25 (MIT) - CHIP-8/SuperCHIP emulator.
* [ieepview](https://github.com/asiekierka/ws-ieepview) ⭐ 4 | 🐛 1 | 🌐 C | 📅 2025-03-09 (MIT) - internal EEPROM viewer/editor.
* [ws-backup-tool](https://github.com/asiekierka/ws-backup-tool) ⭐ 3 | 🐛 1 | 🌐 C | 📅 2025-10-31 (GPL-3.0) - cartridge backup/restore/flash tool and IPL dumper for BootFriend.
* [BootFriend](https://wonderful.asie.pl/ws/bootfriend) (GPL-3.0) - WonderSwan custom "firmware"/splash screen patch - XMODEM software load to RAM and more!
* [wsmonitor](https://bitbucket.org/trap15/wsmonitor/) (MIT) - 80186 debug monitor.

### Miscellaneous

* [vgmswan](https://github.com/asiekierka/vgmswan) ⭐ 1 | 🐛 0 | 🌐 C | 📅 2024-03-29 (MIT/zlib) - .VGM playback and conversion tools.

## WonderWitch

* [AthenaOS](https://github.com/OpenWitch/AthenaOS) ⚠️ Archived - FreyaBIOS/FreyaOS re-implementation project.
* [ow-libs](https://github.com/OpenWitch/ow-libs) ⚠️ Archived - WonderWitch standard library re-implementation project.
* [wonderwitchvc15](https://github.com/autumn009/wonderwitchvc15) ⭐ 1 | 🐛 0 | 🌐 Assembly | 📅 2020-07-24 - example of using Visual C++ 1.5 for compiling WonderWitch binaries.

### WW tools

* [MiracleMage](https://github.com/Godzil/MiracleMage) ⭐ 4 | 🐛 0 | 🌐 C | 📅 2019-06-19 (GPL-2.0) - high-level WonderWitch emulator, only supports "mono" software, does not require a WonderWitch ROM.
* [exe2fbin](https://github.com/OpenWitch/exe2fbin) ⚠️ Archived (PD) - reconstruction of the official exe2fbin binary.
* [romwitch](https://bitbucket.org/trap15/romwitch/) (GPL-2.0) - utility to inject executables into "static" WonderWitch software ROMs.

### WW documentation

* [Don Walizer Jr's tutorials](https://www.donwalizerjr.com/tags/wonderswan) ([source code](https://github.com/dwalizer/wonderwitch) ⭐ 5 | 🐛 1 | 🌐 C | 📅 2020-10-02).
* [Wonder Witch Technical Manual](http://shaw.la.coocan.jp/wwtm/)
* [WSdev Wiki](https://ws.nesdev.org/wiki/Main_Page) - also contains a WonderWitch section.
* [wonder/doc/freya](https://bitbucket.org/trap15/wonder/src/master/doc/freya/)

### Open source WW programs

This section only lists programs whose source code is explicitly listed under open source licenses.

#### Games

* [FallingTower mini](http://www.fenix.ne.jp/~cdrtk/soft/wwjump.html) (BSD-2-Clause)
* [Nametry](https://www.asahi-net.or.jp/~cs8k-cyu/ww/nametry.html) (BSD-2-Clause)
* [Noiz](https://www.asahi-net.or.jp/~cs8k-cyu/ww/noiz.html) (GPL-2.0-or-later)
* [PutiPati](https://www.asahi-net.or.jp/~cs8k-cyu/ww/putipati.html) (BSD-2-Clause)
* [Soari-san](http://www.fenix.ne.jp/~cdrtk/soft/soari.html) (BSD-2-Clause)
* [SpeedMac](https://kozos.jp/ww/) (BSD-2-Clause)
* [yoppa](https://github.com/WonderfulToolchain/yoppa/tree/original) ⚠️ Archived (BSD-3-Clause)

#### Applications

* [dumpipl](https://github.com/up-n-atom/wwsoft/tree/master/dumpipl) ⭐ 5 | 🐛 0 | 🌐 Assembly | 📅 2024-09-17 (MIT) - WS/WSC initial program loader dumping tool (as "Soft" image).
* [WWTerm](https://github.com/WonderfulToolchain/WWTerm/tree/original) ⚠️ Archived (GPL-2.0) - terminal emulator.
* [vgmwitch](https://bitbucket.org/trap15/vgmwitch) (MIT) - SN76489 music player.
* [米七note](http://www.fenix.ne.jp/~cdrtk/soft/ksnote.html) (BSD-2-Clause)

#### Libraries

* [HummingCat](https://github.com/molety/HummingCat/) (MIT) - work-in-progress sound driver.

## Open source hardware

### Cartridges

* [nileswan](https://github.com/RSDuck/nileswan/) ⭐ 82 | 🐛 3 | 🌐 HTML | 📅 2026-06-24 (GPLv3) - open-source flash cartridge.
* [Bandai2003](https://github.com/up-n-atom/Bandai2003) ⭐ 6 | 🐛 0 | 🌐 Verilog | 📅 2023-02-05 (MIT) - Verilog "2003" mapper implementation.
* [mbc-unlock](https://bitbucket.org/trap15/mbc-unlock) (CC0) - VHDL boot handshake implementation.

### Peripherals

* [wsheadphone](https://github.com/zwenergy/wsheadphone) ⭐ 38 | 🐛 0 | 📅 2022-04-23 (CC-BY-NC-SA-4.0) - headphone DAC adapter.
* [WSMtool](https://github.com/zwenergy/WSMtool) ⭐ 25 | 🐛 0 | 📅 2025-08-03 (CC-BY-NC-SA-4.0) - multitool adapter for the WonderSwan; headphone, serial and link cable adapter in one.
* [ExtFriend](https://github.com/WonderfulToolchain/ws-extfriend) ⭐ 24 | 🐛 1 | 🌐 C | 📅 2025-06-17 (GPL-3.0) - WonderSwan EXT<->USB adapter with digital audio capture.
* [WS-LinkC](https://github.com/zwenergy/WS-LinkC) ⭐ 15 | 🐛 0 | 📅 2022-12-29 (CC-BY-NC-SA-4.0) - cheap, DIY-friendly link cable alternative.

### Screen capture

* [swancolorHD](https://github.com/zwenergy/swancolorHD) ⭐ 62 | 🐛 3 | 🌐 GLSL | 📅 2024-08-04 (GPL-3.0) - FPGA-based screen capture solution.
  * [swantroller](https://github.com/zwenergy/swantroller) ⭐ 10 | 🐛 1 | 🌐 C | 📅 2024-07-16 (GPL-3.0) - WonderSwan Color-based controller PCB for the swancolorHD.
* [nisetro\_wsc](https://github.com/splash5/nisetro_wsc) ⭐ 16 | 🐛 0 | 🌐 C++ | 📅 2023-02-23 (MIT) - FPGA-based screen capture solution.

### Other hardware development

* [WonderSwan for MiSTer](https://github.com/MiSTer-devel/WonderSwan_MiSTer) ⭐ 15 | 🐛 11 | 🌐 VHDL | 📅 2026-08-15 (GPL-2.0)
* [USB WonderSwan Cartridge Utility](https://github.com/up-n-atom/WonderSwanCartTap) ⭐ 6 | 🐛 0 | 🌐 C | 📅 2022-02-24 (MIT) - cartridge dumper and programmer.

## Historical

These are links to files and sources which are noteworthy from a historical perspective, but have been superseded.

* [WSTech 2.4](https://github.com/OpenEmu/Mednafen-Core/blob/master/mednafen/wswan/wstech24.txt) ⭐ 33 | 🐛 13 | 🌐 C | 📅 2024-04-09 - outdated document, incorrect in places.

***

> _Enhansomed by [enhansome](https://github.com/enhansome) on 2026-08-21._
