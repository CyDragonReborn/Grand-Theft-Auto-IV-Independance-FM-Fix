# Grand-Theft-Auto-IV-Independance-FM-Fix
This basically aides the game can work the custom music of Independance without WMP. it uses Bass audio more about it all in the README.

I have been experimenting with Opencode and the bigpickle ai bot and It got me thinking if it COULD assistance of making a mod that overrides any need for GTA 4 to use windows media player. I asked if it's possible and it began quickly researching. turns out it definitely was possible so I selected the option for it to make an asi mod that'd do it instead of some wmp.dll. I gave it some testing so far and indeed  the game can work the music without WMP. it's using BASS audio... so far though the usual mp3 and wav will work and I am still testing that it works Flac and Opus since the AI ensured to make a bassflac.dll and bassopus.dll... I also put in a command arguement to ensure each dll gets loaded. obviously it did ensure it works with Ultimate asi loader AND Fusionfix. 

# IV Independence Fix

An ASI plugin for Grand Theft Auto IV: The Complete Edition that replaces the Windows Media Player dependency for Independence FM with BASS audio library, adding native MP3, FLAC, and Opus support that works on both Windows and Proton/Linux.

## Features

- **No WMP required** — Independence FM no longer needs Windows Media Player
- **Supports MP3, FLAC, Opus, OGG, WAV, WMA, M4A** — any audio file in your User Music folder
- **Works under Proton** — fully functional on Steam Deck and Linux
- **Hotkey controls** — play/pause, next/prev track, volume up/down
- **Shuffle mode** — random track selection
- **BASS audio engine** — high-quality, low-latency audio playback

## How it works

The plugin loads alongside the game via Ultimate ASI Loader. It scans your User Music folder, builds a track list, and plays audio through BASS directly to your audio device (bypassing WMP entirely). Control playback with configurable hotkeys.

## Installation

### Prerequisites

- **Ultimate ASI Loader** — [Download here](https://github.com/ThirteenAG/Ultimate-ASI-Loader/releases/latest)
- GTA IV: The Complete Edition (any version)
- FusionFix recommended (optional, but provides the `dinput8.dll` ASI loader)

### Windows

1. Install **Ultimate ASI Loader**: copy `dinput8.dll` (or `xlive.dll` for GFWL version) to your GTA IV root directory
2. Copy `IVIndependenceFix.asi`, `bass.dll`, `bassflac.dll`, and `bassopus.dll` to the same directory
3. Optionally edit `IVIndependenceFix.ini` to configure hotkeys
4. If you already have FusionFix, the ASI loader is already installed — just copy the plugin files

### Proton / Linux (Steam Deck)

1. Install **FusionFix** (recommended), which includes the ASI loader:
   - [Download FusionFix](https://github.com/ThirteenAG/GTAIV.EFLC.FusionFix/releases/latest)
   - Extract to your GTA IV game directory
   - If using Proton Experimental, it loads `dinput8.dll` automatically
   - For other Proton versions, add this launch option:
     ```
     WINEDLLOVERRIDES="dinput8=n,b" %command%
     ```
2. Copy `IVIndependenceFix.asi`, `bass.dll`, `bassflac.dll`, and `bassopus.dll` to:
   ```
   ~/.steam/steam/steamapps/common/Grand Theft Auto IV/
   ```
3. Place your music files in the User Music folder:
   ```
   ~/.steam/steam/steamapps/compatdata/12210/pfx/drive_c/users/steamuser/My Documents/Rockstar Games/GTA IV/User Music/
   ```
4. Configure hotkeys in `IVIndependenceFix.ini`

### Building from source

Requirements: MinGW-w64 (via Wine or native) + CMake.

```bash
git clone <repo>
cd IVIndependenceFix
./build.sh
```

Output: `build/IVIndependenceFix.asi`

## Usage

1. Put your MP3, FLAC, Opus, and other audio files in the User Music folder
2. Launch GTA IV
3. Tune to **Independence FM** on the radio
4. Use hotkeys to control playback:

| Default Key | Function |
|-------------|----------|
| F10 | Play / Pause |
| F11 | Next Track |
| F12 | Previous Track |
| =/+ | Volume Up |
| -/_ | Volume Down |

## Configuration

Edit `IVIndependenceFix.ini` in your GTA IV root directory:

```ini
[Settings]
UserMusicPath=                ; Custom music folder path (empty = default Documents location)
Volume=80                     ; Initial volume (0-100)
Shuffle=1                     ; 1 = shuffle, 0 = sequential
AutoPlay=0                    ; Auto-start when plugin loads

[Hotkeys]
PlayPause=121                 ; F10
NextTrack=122                 ; F11
PrevTrack=123                 ; F12
VolumeUp=187                  ; =/+
VolumeDown=189                ; -/_
```

For hotkey values, see: [Virtual-Key Codes](https://docs.microsoft.com/en-us/windows/win32/inputdev/virtual-key-codes)

## How it differs from other mods

- **IV Radio Editor** — Replaces radio station songs in-game (replaces existing tracks)
- **IVIndependenceFix** — Makes Independence FM work with any audio format without WMP (plays YOUR music folder)

## Credits

- BASS audio library by Un4seen Developments
- MinHook by Tsuda Kageyu
- Ultimate ASI Loader by ThirteenAG
- FusionFix by ThirteenAG and contributors
