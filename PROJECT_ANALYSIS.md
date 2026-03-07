# GGNotch — Project Analysis

> Based on **boring.notch** by TheBoredTeam (GPL v3)
> Branch: `dev` — synced with upstream `TheBoredTeam/boring.notch@dev` (2026-03-07)

## ภาพรวม (Overview)

**GGNotch** คือ macOS application แบบ open-source ที่ fork มาจาก boring.notch ซึ่งเปลี่ยน notch ของ MacBook ให้กลายเป็น interactive hub แสดงข้อมูลต่าง ๆ แทนที่จะเป็นพื้นที่ดำ ๆ ธรรมดา

- **Upstream Repo**: `TheBoredTeam/boring.notch` (branch: `dev`)
- **System Requirement**: macOS 14 Sonoma ขึ้นไป, Apple Silicon หรือ Intel
- **Build Tool**: Xcode 16+, Swift Package Manager
- **License**: GPL v3

---

## โครงสร้าง Project (Project Structure)

```
GGNotch/
├── ggNotch/                  # Main app target
│   ├── ggNotchApp.swift      # App entry point + AppDelegate
│   ├── GGNotchViewCoordinator.swift
│   ├── ContentView.swift
│   ├── components/               # SwiftUI views
│   │   ├── Notch/                # หน้าต่าง notch หลัก
│   │   │   ├── GGNotchWindow.swift
│   │   │   ├── GGNotchSkyLightWindow.swift
│   │   │   ├── GGNotchHeader.swift
│   │   │   ├── GGNotchExtrasMenu.swift
│   │   │   ├── NotchHomeView.swift
│   │   │   └── NotchShape.swift
│   │   ├── OSD/                  # ★ NEW: OSD system (เปลี่ยนจาก "Live activities")
│   │   │   ├── Managers/
│   │   │   │   ├── BetterDisplayManager.swift   # รับ OSD event จาก BetterDisplay app
│   │   │   │   ├── LunarManager.swift           # รับ OSD event จาก Lunar app
│   │   │   │   └── XPC/
│   │   │   │       ├── BrightnessManager.swift  # (ย้ายมาจาก managers/)
│   │   │   │       └── VolumeManager.swift      # (ย้ายมาจาก managers/)
│   │   │   ├── Models/
│   │   │   │   └── BetterDisplayNotificationModels.swift
│   │   │   └── Views/
│   │   │       ├── InlineOSD.swift              # (เปลี่ยนชื่อจาก InlineHUD.swift)
│   │   │       ├── OpenNotchOSD.swift           # (เปลี่ยนชื่อจาก OpenNotchHUD.swift)
│   │   │       ├── OSDIconView.swift
│   │   │       ├── DraggableProgressBar.swift
│   │   │       └── SystemEventIndicatorModifier.swift
│   │   ├── Live activities/      # ยังมีบางส่วน (Battery, Download, Marquee)
│   │   │   ├── GGNotchBattery.swift
│   │   │   ├── DownloadView.swift
│   │   │   ├── LiveActivityModifier.swift
│   │   │   └── MarqueeTextView.swift
│   │   ├── Music/
│   │   │   ├── MusicVisualizer.swift
│   │   │   └── LottieAnimationView.swift
│   │   ├── Settings/
│   │   │   ├── SettingsView.swift               # Entry point / container
│   │   │   ├── SettingsWindowController.swift
│   │   │   ├── SoftwareUpdater.swift
│   │   │   ├── EditPanelView.swift
│   │   │   ├── ListItemPopover.swift
│   │   │   ├── MusicSlotConfigurationView.swift
│   │   │   └── Views/                           # ★ NEW: แตกจาก SettingsView ใหญ่
│   │   │       ├── GeneralSettingsView.swift
│   │   │       ├── AppearanceSettingsView.swift
│   │   │       ├── MediaSettingsView.swift
│   │   │       ├── BatterySettingsView.swift
│   │   │       ├── CalendarSettingsView.swift
│   │   │       ├── OSDSettingsView.swift
│   │   │       ├── ShelfSettingsView.swift
│   │   │       ├── ShortcutsSettingsView.swift
│   │   │       ├── AdvancedSettingsView.swift
│   │   │       ├── AboutView.swift
│   │   │       └── SettingsHelpers.swift
│   │   ├── Shelf/                # File shelf + AirDrop
│   │   │   ├── Models/
│   │   │   ├── Services/
│   │   │   ├── ViewModels/
│   │   │   └── Views/
│   │   ├── Calendar/
│   │   │   └── GGNotchCalendar.swift
│   │   ├── Onboarding/
│   │   ├── Webcam/
│   │   │   └── WebcamView.swift
│   │   └── Tabs/
│   ├── managers/                 # Business logic managers
│   │   ├── MusicManager.swift
│   │   ├── CalendarManager.swift
│   │   ├── BatteryActivityManager.swift
│   │   ├── LyricsService.swift              # ★ NEW: แยก lyrics logic ออกจาก MusicManager
│   │   ├── WebcamManager.swift
│   │   ├── NotchSpaceManager.swift
│   │   └── ImageService.swift
│   ├── MediaControllers/         # Music source abstraction
│   │   ├── MediaControllerProtocol.swift
│   │   ├── NowPlayingController.swift
│   │   ├── AppleMusicController.swift
│   │   ├── SpotifyController.swift
│   │   └── YouTube Music Controller/
│   ├── models/                   # Data models & ViewModels
│   │   ├── GGNotchViewModel.swift
│   │   ├── BatteryStatusViewModel.swift
│   │   ├── PlaybackState.swift
│   │   ├── Constants.swift
│   │   ├── CalendarModel.swift
│   │   ├── EventModel.swift
│   │   ├── MusicControlButton.swift
│   │   └── SharingStateManager.swift
│   ├── menu/
│   │   └── StatusBarMenu.swift
│   ├── observers/                # System event observers
│   │   ├── MediaKeyInterceptor.swift
│   │   ├── FullscreenMediaDetection.swift
│   │   └── DragDetector.swift
│   ├── XPCHelperClient/
│   ├── Providers/
│   │   └── CalendarServiceProviding.swift
│   ├── Shortcuts/
│   │   └── ShortcutConstants.swift
│   ├── private/
│   │   └── CGSSpace.swift
│   ├── sizing/
│   │   └── matters.swift
│   ├── utils/
│   │   └── Logger.swift
│   ├── enums/, extensions/, helpers/, animations/
│   └── (ไม่มี metal/visualizer.metal แล้ว — ถูกลบออก)
│
├── GGNotchXPCHelper/         # XPC Helper target (privileged process)
│   ├── GGNotchXPCHelper.swift
│   ├── GGNotchXPCHelperProtocol.swift
│   └── main.swift
│
├── mediaremote-adapter/          # Binary framework สำหรับ macOS 15.4+
│
├── Configuration/
│   ├── dmg/
│   └── sparkle/
│
└── .github/
    └── workflows/                # CI/CD GitHub Actions
```

---

## สถาปัตยกรรม (Architecture)

### Two-Target Design

| Target | Bundle ID | บทบาท |
|--------|-----------|--------|
| `ggNotch` | `theboringteam.boringnotch` | Main UI app |
| `GGNotchXPCHelper` | `theboringteam.boringnotch.GGNotchXPCHelper` | Privileged XPC service |

### Window Management

```
AppDelegate
├── window: NSWindow              # Single-screen mode
└── windows: [UUID: NSWindow]     # Multi-screen mode (showOnAllDisplays)
    └── GGNotchSkyLightWindow (NSPanel subclass)
        ├── .borderless
        ├── .nonactivatingPanel
        └── SkyLightWindow (แสดงบน lock screen ได้)
```

### State Management

```
GGNotchViewModel (per-screen @EnvironmentObject)
├── notchState: .open / .closed
├── contentType, dragTargeting, cameraExpanded
└── ผูกกับ GGNotchViewCoordinator.shared

GGNotchViewCoordinator (singleton @MainActor)
├── currentView: .home / .shelf
├── sneakPeek: { show, type, value }    # HUD overlay ขนาดเล็ก
├── expandingView: { show, type, value } # HUD แบบ expanding
└── selectedScreenUUID
```

---

## ฟีเจอร์หลัก (Core Features)

### 1. Music Player (Notch Home View)

แสดงข้อมูลเพลงที่กำลังเล่น พร้อม:
- Album art (พร้อม flip animation เมื่อเปลี่ยนเพลง)
- Playback controls (Play/Pause, Next, Prev, Shuffle, Repeat, Favorite)
- Seek slider (อัปเดต smooth ด้วย `TimelineView`)
- Volume control แบบ slide-out
- Lyrics — ดึงจาก Apple Music native หรือ LRCLIB API ผ่าน **`LyricsService`** (★ แยกออกมาจาก MusicManager)
- Colored spectrogram (สีจาก album art)
- Music visualizer

**Media Controllers** รองรับ 4 source:
- `NowPlayingController` — macOS system-wide now playing (deprecated บน 15.4+)
- `AppleMusicController` — ผ่าน AppleScript
- `SpotifyController` — ผ่าน AppleScript
- `YouTubeMusicController` — HTTP polling (YouTube Music desktop app)

### 2. OSD System (★ เปลี่ยนจาก "System HUD Replacement")

แทนที่ HUD ของ macOS ด้วย sneak peek ใน notch รองรับ 3 แหล่ง:

- **`MediaKeyInterceptor`** — ดักจับ media key events ผ่าน `CGEvent.tapCreate`
- **`BetterDisplayManager`** (★ ใหม่) — รับ OSD notification จาก BetterDisplay app ผ่าน NSDistributedNotificationCenter
- **`LunarManager`** (★ ใหม่) — รับ OSD notification จาก Lunar app

รองรับ: volume, brightness, keyboard backlight, mute

### 3. Calendar Integration

- `EventKit` ดึง Calendar events และ Reminders ของวันปัจจุบัน
- เลือก/ซ่อน calendar แต่ละอันได้

### 4. File Shelf + AirDrop

- Drop zone สำหรับวางไฟล์
- `DragDetector` ตรวจจับการลาก file เข้ามาใกล้ notch แล้ว auto-open
- รองรับ AirDrop และ Quick share service

### 5. Battery Indicator

- `BatteryActivityManager` monitor ผ่าน IOKit `IOPSNotificationCreateRunLoopSource`
- รองรับ Low Power Mode detection

### 6. Mirror (Webcam Preview)

- `WebcamManager` (AVFoundation) แสดง live camera feed ใน notch

### 7. Settings Panel (★ Refactored)

Settings ถูกแตกออกจากไฟล์เดียวเป็น 11 view แยกตาม category:
General, Appearance, Media, Battery, Calendar, OSD, Shelf, Shortcuts, Advanced, About

---

## XPC Architecture

```
Main App (ggNotch)
    └── XPCHelperClient.shared
            │  (AsyncXPCConnection + NSXPCConnection)
            ▼
XPC Service (GGNotchXPCHelper)
    ├── isAccessibilityAuthorized()
    ├── requestAccessibilityAuthorization()
    ├── isKeyboardBrightnessAvailable()
    ├── currentKeyboardBrightness()    → CoreBrightness private framework
    ├── setKeyboardBrightness()
    ├── isScreenBrightnessAvailable()
    ├── currentScreenBrightness()      → DisplayServices / IOKit
    └── setScreenBrightness()
```

---

## Third-Party Dependencies

| Package | บทบาท |
|---------|--------|
| `AsyncXPCConnection` (ChimeHQ) | Async/await wrapper สำหรับ NSXPCConnection |
| `Defaults` (sindresorhus) | Type-safe UserDefaults wrapper |
| `KeyboardShortcuts` (sindresorhus) | Custom keyboard shortcut registration |
| `LaunchAtLogin-Modern` (sindresorhus) | Launch at login support |
| `Lottie` (Airbnb) | JSON-based animation |
| `MacroVisionKit` (TheBoredTeam) | Camera/vision integration |
| `Pow` (EmergeTools) | Extra SwiftUI animation effects |
| `SkyLightWindow` (Lakr233) | Render on lock screen (private API wrapper) |
| `Sparkle` | Auto-update framework |
| `swift-collections` (Apple) | Data structures (OrderedSet, etc.) |
| `SwiftUI-Introspect` | Access AppKit views จาก SwiftUI |

---

## CI/CD Pipeline

| Workflow | Trigger | บทบาท |
|----------|---------|--------|
| `cicd.yml` | Push/PR to main | Build & Test |
| `build_reusable.yml` | reusable | Shared build steps |
| `manual_build.yml` | Manual dispatch | Build on demand |
| `release.yml` | Tag push | Build + Create GitHub Release + DMG |

---

## Key Design Patterns

### Singleton Managers
`MusicManager.shared`, `BatteryActivityManager.shared`, `CalendarManager.shared`, `LyricsService.shared`, `BetterDisplayManager.shared`, `LunarManager.shared`

### Protocol-based Media Controller
`MediaControllerProtocol` + `MusicManager` เป็น facade expose ผ่าน `@Published` properties

### Combine + SwiftUI
- `AnyPublisher<PlaybackState, Never>` จาก media controllers
- `@Published` properties bind กับ SwiftUI views โดยตรง

### Notification-based OSD
- `BetterDisplayManager` และ `LunarManager` รับ `NSDistributedNotificationCenter` แล้วแปลงเป็น OSD events

---

## Data Flow Diagram

```
[System Events]                [User Interaction]
   IOKit (battery)                Hover mouse
   AVFoundation (audio)           Keyboard shortcuts
   EventKit (calendar)            Drag & drop
   CGEventTap (media keys)
   NSDistributedNotification      ← BetterDisplay / Lunar (★ ใหม่)
         │                              │
         ▼                              ▼
   [Managers / Observers]      [GGNotchViewModel]
   MusicManager.shared              open() / close()
   BatteryActivityManager           notchState
   CalendarManager
   LyricsService (★)
   BetterDisplayManager (★)
   LunarManager (★)
         │                              │
         ▼                              ▼
   [GGNotchViewCoordinator]     [ContentView]
   currentView (.home/.shelf)       NotchHomeView
   sneakPeek                        ShelfView
   expandingView
         │
         ▼
   [SwiftUI Views update via @Published / @EnvironmentObject]
```

---

## ข้อสังเกตด้าน Security & Permission

- **Accessibility** (required สำหรับ OSD replacement) — ผ่าน XPC helper
- **Camera** (optional สำหรับ Mirror feature)
- **Calendar** (optional)
- **Reminders** (optional)

การใช้ private frameworks (`CoreBrightness`, `DisplayServices`) ใน XPC helper เป็นเรื่องปกติสำหรับ system utility apps บน macOS

---

## Git Remote Setup

```
origin    → https://github.com/Ruchikon-M/GGNotch.git
upstream  → https://github.com/TheBoredTeam/boring.notch.git
```

**Branches:**
- `main` — based on upstream/main
- `dev` — synced กับ upstream/dev (current)

To sync ในอนาคต:
```bash
git fetch upstream
git checkout dev
git merge upstream/dev
```
