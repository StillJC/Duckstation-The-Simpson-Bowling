# Simpsons Bowling DuckStation

A custom DuckStation fork built specifically for **The Simpsons Bowling** arcade.

This is **not** intended to be a current, general-purpose DuckStation replacement. It is a specialized, trimmed, outdated-by-design fork used to boot and run one game cleanly in an arcade cabinet-style environment.

## Original Project Credit

This project is forked from DuckStation.

> “DuckStation is an simulator/emulator of the Sony PlayStation(TM) console, focusing on playability, speed, and long-term maintainability.”

Original DuckStation repository:
https://github.com/stenzek/duckstation

The Simpsons Bowling Arcade1Up repository:
https://github.com/Arcade1Up/duckstation-sb

T-Dollaz macOS centered build that I forked from:
https://github.com/t-dollaz/simpsons-bowling-baby-phoenix-duckstation

All credit for the original emulator work goes to the DuckStation developers and contributors. This fork only contains project-specific changes needed for Simpsons Bowling in Windows.

## Purpose

This fork exists to run **The Simpsons Bowling** from a local cabinet/emulator folder with fewer frontend requirements and a setup focused around trackball play.

It is meant for:

* Simpsons Bowling only
* Local Windows arcade cabinet use
* Trackball/mouse input
* Fullscreen launching
* Simplified game setup
* Native bezel overlay support

It is not meant for:

* General PS1 emulation
* Current DuckStation compatibility
* Multi-game library management
* Modern upstream DuckStation features
* Cross-platform release builds

## Project Changes

Major changes and updates made in this fork:

* Added native bezel overlay support
* Added right-click Qt menu option to set a game bezel image
* Added fullscreen launch support for cabinet use
* Added project-specific Simpsons Bowling folder layout
* Added support for booting `arcade.iso` from the local `simpsons` subfolder
* Adjusted mouse/trackball axis behavior
* Added cabinet-oriented launch workflow
* Updated project assets and branding
* Reduced focus on normal DuckStation frontend/library usage
* Cleaned up behavior for one-game dedicated use

Required Original Files

This repository does not include any copyrighted game, BIOS, EEPROM, Flash, APK, or disc image files.

To run the game, you must supply your own dumped original files.

The setup used for this fork was based on the Arcade1Up Simpsons Bowling Android APK, specifically:

Arcade1Up_1.43.apk

From that original APK/game dump, the required files are:

999a01.7e       PlayStation/Konami GV BIOS, 512 KB
eeprom          128 bytes
flash0          2 MB
flash1          2 MB
flash2          2 MB
flash3          2 MB
arcade.iso      Simpsons Bowling disc image

Recommended folder layout:

DuckStation Folder/
├─ duckstation-qt-x64-Release.exe
├─ portable.txt
├─ bios/
│  └─ 999a01.7e
└─ simpsons/
   ├─ arcade.iso
   ├─ eeprom.bin
   ├─ flash0.bin
   ├─ flash1.bin
   └─ flash3.bin

The game must be run from the ISO image:

simpsons/arcade.iso

## MAME romset files are untested with this fork.

These files must come from your own legally obtained original Arcade1Up APK source. They are not included in this repository and will not be committed to GitHub.

## Running the Game

Recommended command:

```cmd
duckstation-qt-x64-Release.exe -fullscreen -batch ".\simpsons\arcade.iso"
```

## Hidden Launch Script

Use this as the launcher batch file:

```cmd
@echo off
cd /d "%~dp0"
start "" "duckstation-qt-x64-Release.exe" -fullscreen -batch ".\simpsons\arcade.iso"
exit
```

Suggested filename:

```text
Simpsons Bowling.bat
```

Place it in the main emulator folder next to the DuckStation executables.

## Controls

Recommended in-game setting:

```text
Easy Controls
```

Easy Controls works best with a trackball or mouse-style input.

### Basic Controls

### Controls

Set **Port 1** controller type to **Analog Controller (DualShock)** in Settings → Controllers.

| Input | Binding |
|---|---|
| Trackball | Mouse (USB trackball works automatically) |
| Throw button | Cross or Circle |
| Start | Start |

## Bezel Overlay

This fork includes native bezel overlay support.

Bezel-related changes include:

* Core settings support
* Frontend settings support
* Runtime bezel loading
* Per-game bezel image assignment through the Qt game list context menu
* Fullscreen overlay rendering

The bezel is intended for cabinet display use and should be placed outside the active game window area.

## Building on Windows with Visual Studio 2026

This fork was built using **Visual Studio 2026** on Windows.

### Required Visual Studio Components

Install the following through the Visual Studio Installer:

* Desktop development with C++
* MSVC v145 or current VS2026 C++ build tools
* Windows 11 SDK
* C++ CMake tools for Windows
* Git for Windows, if not already installed
* C++ ATL/MFC components if required by your local configuration

### Required External Tools

Also install:

* Python 3
* CMake
* Qt 6 for MSVC 64-bit
* Git

Qt must match the MSVC toolchain being used.

### Clone

```cmd
cd /d S:\repos
git clone https://github.com/StillJC/simpsons-bowling-duckstation.git
cd simpsons-bowling-duckstation
```

### Open in Visual Studio

Open the solution/project in Visual Studio 2026.

Use:

```text
Release x64
```

Recommended build targets:

```text
duckstation-qt
```

### Build Output

Expected output folder:

```text
bin\x64
```

The main executable used for cabinet launching is:

```text
duckstation-qt-x64-Release.exe
```

## BIOS

A valid Konami GV BIOS is required.

Place BIOS files in:

```text
bios/
```

BIOS files are not included with this project.

## Known Limitations

* This is not current DuckStation.
* This is not intended for normal multi-game PS1 use.
* This fork is only maintained for Simpsons Bowling.
* Some standard DuckStation features may be broken, removed, outdated, or untested.
* No guarantee is made for Linux, macOS, Android, or general emulator use.
* The no-GUI executable may not behave as cleanly in fullscreen cabinet mode as the Qt executable.

## License

This project remains under the applicable license terms of the original DuckStation source it was forked from.

Original project credit belongs to the DuckStation developers and contributors.

This fork only contains Simpsons Bowling-specific changes, fixes, and cabinet-use improvements.
