# Balatro Portrait Mobile

🎴 A portrait mode mod for Balatro on Android - optimized for mobile gaming!

<img width="587" height="1290" alt="image" src="https://github.com/user-attachments/assets/1d12d7e3-aa3b-4c34-ad18-14e0c554cfb2" />

## Features

- **Portrait Mode**: Fully optimized vertical layout for mobile devices
- **Redesigned HUD**: Score, buttons, and info panels repositioned for portrait
- **Touch-Optimized**: Works perfectly with touchscreen controls
- **Full Game Support**: All features work in portrait mode

## Requirements

- **Balatro** - You must own a legal copy of the game
- **Python 3.6+** - For build scripts
- **Android device** - Android 5.0+ recommended

> ✅ **Cross-Platform:** Works on Windows, MacOS and Linux!

## Quick Start

### Step 1: Clone the Repository

```
git clone https://github.com/ShaggyLorean/balatro-portrait-mobile.git
cd balatro-portrait-mobile
```

### Step 2: Get Balatro

⚠️ **You must own a legal copy of Balatro!**

1. Purchase from [Steam](https://store.steampowered.com/app/2379780/Balatro/)
2. Find your Balatro.exe location:
   - **Steam**: Right-click Balatro → Manage → Browse Local Files
   - Default: `C:\Program Files\Steam\steamapps\common\Balatro\Balatro.exe`

### Step 3: Run Setup

```
python setup.py "C:\path\to\Balatro.exe"
```

This will automatically:

- Extract game files from Balatro.exe
- Copy resources to the src folder

### Step 4: Build the APK

```
python rebuild_game.py
python build_apk.py
```

During the build, you will be asked about the **CRT Shader Patch**:

- If you see a **black ellipse** covering part of the screen, answer **yes** to disable CRT
- If your game works fine, answer **no** to keep the CRT visual effects

The final APK will be at:

```
balatro-mobile-maker/balatro-aligned-debugSigned.apk
```

### Step 5: Install on Android

Transfer the APK to your phone and install it.

Or if you have ADB:

```
adb install balatro-mobile-maker/balatro-aligned-debugSigned.apk
```

## Project Structure

```
balatro-portrait-mobile/
├── src/                    # Modified source files (portrait mode)
├── game_original_files/    # Extracted game files (created by setup.py)
├── setup.py                # Setup script (extracts & copies files)
├── rebuild_game.py         # Creates Game.love
└── build_apk.py            # Builds the APK
```

## Troubleshooting

### "Game won't start"

- Make sure setup.py completed successfully
- Check that `src/resources/` and `src/localization/` exist

### "Build fails"

- Ensure Python 3.6+ is installed: `python --version`
- JDK is downloaded automatically during build

### "Black ellipse covering part of the screen"

This is caused by the CRT shader not rendering correctly in portrait mode on some devices.

**Solution**: Rebuild with CRT patch enabled:

```
python rebuild_game.py
```

When asked "Apply CRT disable patch?", answer **yes**.

## Changelog

### v1.5.0

#### UI & Accessibility Overhaul

    New Vertical HUD: Stats and action buttons are now anchored at the top of the screen for constant visibility without scrolling.

    Optimized Layout: Deck and consumables now share a horizontal line. Tags are permanently visible next to Jokers with tooltips adjusted to prevent clipping.

    Upgraded Controls: Play/Discard buttons are larger for touch screens and strictly uniform in size.

    One-Handed Mode: Added a Left/Right-handed setting that shifts tags, consumables, and the deck for better ergonomics.

    Customizable HUD: Players can now change the order and alignment (left/center/right) of the Run Info and Options buttons.

#### Portrait Mode Screen Adaptations

    Menus & Overlays: Fully adapted the Card Inventory, Main Menu (scaling title, larger buttons, global version display), Win, and Game Over screens.

    Stats & Challenges: Restructured into readable single-column vertical layouts.

    Collections: Tarot and Planet cards are now cleanly formatted into 3 rows.

#### Bug Fixes

    Blind Selection: Fixed a major logic bug in Portrait mode where future blinds were accessible early and skipped blinds could be endlessly replayed. The active blind is now properly locked and visually highlighted.

#### System & Compatibility

    Added MacOS cross-platform support.
    Removed the 7-zip requirement.

### v1.4.0

- Fixed Game Over screen layout for portrait mode
- Fixed black bar issue when locking/unlocking device (Issue #1)
- Jimbo repositioned to bottom with stats at top
- Improved resize handling for Android

### v1.3.0

- Added CRT shader disable option during build
- Fixed black ellipse visual artifact on some devices (Issue #3)
- Build script now asks user about CRT patch preference

### v1.2.0

- Windows compatibility
- Cross-platform build scripts

### v1.0.0

- Initial release
- Portrait mode support

## Credits

- **LocalThunk** - Original Balatro game
- **LÖVE** - 2D game framework
- **Contributors** - Portrait mode modifications

## Disclaimer

This is an unofficial mod. You must own a legal copy of Balatro to use this.
The original game files are NOT included in this repository.

## License

This mod is provided as-is for personal use. All rights to Balatro belong to LocalThunk.
