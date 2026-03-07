<h1 align="center">
  <br>
  <img src="https://framerusercontent.com/images/RFK4vs0kn8pRMuOO58JeyoemXA.png?scale-down-to=256" alt="GGNotch" width="150">
  <br>
  GGNotch
  <br>
</h1>

> **Based on [boring.notch](https://github.com/TheBoredTeam/boring.notch) by TheBoredTeam, licensed under [GPL v3](./LICENSE). This is a modified fork.**

<p align="center">
  <img src="https://github.com/Ruchikon-M/GGNotch/actions/workflows/cicd.yml/badge.svg" alt="GGNotch Build & Test" style="margin-right: 10px;" />
</p>

Say hello to **GGNotch**, the coolest way to make your MacBook's notch the star of the show! Say goodbye to boring status bars: with GGNotch, your notch transforms into a dynamic music control center, complete with a vibrant visualizer and all the essential music controls you need. But that's just the start! GGNotch also offers calendar integration, a handy file shelf with AirDrop support, a complete MacOS OSD replacement and more!

<p align="center">
  <img src="https://github.com/user-attachments/assets/2d5f69c1-6e7b-4bc2-a6f1-bb9e27cf88a8" alt="Demo GIF" />
</p>

---

## Installation

**System Requirements:**
- macOS **14 Sonoma** or later
- Apple Silicon or Intel Mac

---

### Option 1: Download and Install Manually

Once downloaded, open the `.dmg` and move **GGNotch** to your `/Applications` folder.

> [!IMPORTANT]
> We don't have an Apple Developer account (yet 👀), so macOS will warn you that GGNotch is from an unidentified developer on first launch. This is expected behavior.
>
> You'll need to bypass this before the app will open. You only need to do this once. Use one of the methods below.

---

#### Recommended: Terminal (Always Works)

After moving GGNotch to your Applications folder, run:

```bash
xattr -dr com.apple.quarantine /Applications/GGNotch.app
```

Then open the app normally.

---

#### Alternative: System Settings

> [!NOTE]
> This method doesn't work for all users. If this doesn't work, use the Terminal method above.

1. Try to open the app — you'll see a security warning.
2. Click **OK** to dismiss it.
3. Open **System Settings** > **Privacy & Security**.
4. Scroll to the bottom and click **Open Anyway** next to the GGNotch warning.
5. Confirm if prompted.

---

### Option 2: Install via Homebrew

You can also install using [Homebrew](https://brew.sh). The `--no-quarantine` flag is included to automatically bypass the same macOS security warning described above.

```bash
brew install --cask Ruchikon-M/ggnotch/ggnotch --no-quarantine
```

## Usage

- Launch the app, and voilà—your notch is now the coolest part of your screen.
- Hover over the notch to see it expand and reveal all its secrets.
- Use the controls to manage your music like a rockstar.
- Click the star in your menu bar to customize your notch to your heart's content.

## 📋 Roadmap
- [x] Playback live activity 🎧
- [x] Calendar integration 📆
- [x] Reminders integration ☑️
- [x] Mirror 📷
- [x] Charging indicator and current percentage 🔋
- [x] Customizable gesture control 👆🏻
- [x] Shelf functionality with AirDrop 📚
- [x] Notch sizing customization, finetuning on different display sizes 🖥️
- [x] System OSD replacements (volume, brightness, backlight) 🎚️💡⌨️
- [ ] Bluetooth Live Activity (connect/disconnect for bluetooth devices)
- [ ] Weather integration ⛅️
- [ ] Customizable Layout options 🛠️
- [ ] Lock Screen Widgets 🔒
- [ ] Extension system 🧩
- [ ] Notifications (under consideration) 🔔

## Building from Source

### Prerequisites

- **macOS 14 or later**
- **Xcode 16 or later**

### Installation

1. **Clone the Repository**:
   ```bash
   git clone https://github.com/Ruchikon-M/GGNotch.git
   cd GGNotch
   ```

2. **Open the Project in Xcode**:
   ```bash
   open GGNotch.xcodeproj
   ```

3. **Build and Run**:
    - Click the "Run" button or press `Cmd + R`.

## 🤝 Contributing

Read [CONTRIBUTING.md](CONTRIBUTING.md) to learn how you can contribute!

## 🎉 Acknowledgments

We would like to express our gratitude to the authors and maintainers of the open-source projects that made this possible.

## Notable Projects
- **[boring.notch](https://github.com/TheBoredTeam/boring.notch)** – The original project this fork is based on, by TheBoredTeam.
- **[MediaRemoteAdapter](https://github.com/ungive/mediaremote-adapter)** – An open-source project that allowed us to use the Now Playing source in macOS 15.4+
- **[NotchDrop](https://github.com/Lakr233/NotchDrop)** – An open-source project that has been instrumental in developing the first version of the "Shelf" feature.

For a full list of licenses and attributions, please see the [Third-Party Licenses](./THIRD_PARTY_LICENSES.md) file.

- **SwiftUI**: For making us look like coding wizards.
- **You**: For being awesome and checking out **GGNotch**!
