<div align="center">

# GGNotch

**Your MacBook's notch, finally useful.**

[![Build](https://github.com/GGNotch/GGNotch/actions/workflows/cicd.yml/badge.svg)](https://github.com/GGNotch/GGNotch/actions/workflows/cicd.yml)
[![License: GPL v3](https://img.shields.io/badge/License-GPLv3-blue.svg)](./LICENSE)
[![macOS](https://img.shields.io/badge/macOS-14%2B-black)](https://www.apple.com/macos/)
[![Release](https://img.shields.io/github/v/release/GGNotch/GGNotch)](https://github.com/GGNotch/GGNotch/releases/latest)

</div>

---

GGNotch transforms the black bar at the top of your MacBook into a live, interactive hub. Music controls, calendar, file shelf, system OSD, and more — all hidden inside the notch until you need them.

---

## Features

| Feature | Description |
|---------|-------------|
| 🎧 **Music Player** | Album art, playback controls, seek bar, lyrics, and a live audio visualizer |
| 📆 **Calendar** | Upcoming events and reminders at a glance |
| 📚 **File Shelf** | Drop files into the notch — with AirDrop and Quick Share support |
| 📷 **Mirror** | Live webcam preview inside the notch |
| 🔋 **Battery** | Charging indicator with percentage |
| 🎚️ **System OSD** | Replaces macOS volume, brightness, and keyboard backlight HUDs |
| 👆 **Gestures** | Customizable hover, swipe, and click controls |

---

## Installation

**Requirements:** macOS 14 Sonoma or later · MacBook with a notch

### Homebrew (Recommended)

```bash
brew install --cask GGNotch/ggnotch/ggnotch --no-quarantine
```

### Manual

<a href="https://github.com/GGNotch/GGNotch/releases/latest/download/GGNotch.dmg" target="_self"><img width="200" src="https://github.com/user-attachments/assets/e3179be1-8416-4b8a-b417-743e1ecc67d6" alt="Download for macOS" /></a>

1. Open the `.dmg` and drag **GGNotch** to `/Applications`
2. Run once to bypass Gatekeeper:

```bash
xattr -dr com.apple.quarantine /Applications/GGNotch.app
```

> [!NOTE]
> GGNotch is not signed with an Apple Developer certificate. The `xattr` command removes the quarantine flag — you only need to run it once.

---

## Usage

- **Hover** over the notch to expand it
- **Click the star** (★) in the menu bar to open Settings
- **Drag files** near the notch to open the shelf
- **Media keys** trigger the OSD overlay automatically

---

## Roadmap

- [x] Music playback with visualizer
- [x] Calendar & Reminders
- [x] File shelf with AirDrop
- [x] Mirror (webcam)
- [x] Battery indicator
- [x] System OSD replacement
- [x] Gesture controls
- [ ] Bluetooth device live activity
- [ ] Weather integration
- [ ] Custom layout editor
- [ ] Lock screen widgets
- [ ] Extension system

---

## Building from Source

```bash
git clone https://github.com/GGNotch/GGNotch.git
cd GGNotch
open GGNotch.xcodeproj
```

Requires **Xcode 16+** and **macOS 14+**. Press `Cmd + R` to build and run.

---

## Acknowledgments

GGNotch is a fork of **[boring.notch](https://github.com/TheBoredTeam/boring.notch)** by TheBoredTeam, licensed under [GPL v3](./LICENSE).

- [MediaRemoteAdapter](https://github.com/ungive/mediaremote-adapter) — Now Playing support on macOS 15.4+
- [NotchDrop](https://github.com/Lakr233/NotchDrop) — Shelf feature inspiration

Full license info: [THIRD_PARTY_LICENSES.md](./THIRD_PARTY_LICENSES.md)
