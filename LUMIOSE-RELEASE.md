# Lumiose Online for ZA Recomp — v0.1.34 (Windows & Linux)

Based on **[Hexveil404/PokeZ-ARecomp](https://github.com/Hexveil404/PokeZ-ARecomp)** (through v0.1.27+). See
[CHANGELOG.md](CHANGELOG.md) for the complete list of changes in this release.

## Install or update

### Windows (`ZA-Recomp-windows.zip`)
- **New installation**: extract the complete **ZA Recomp** folder into a writable
  location and open **Lumiose Online.exe**. Supply your own Pokémon Legends:
  Z-A game files, update 2.0.2 and DLC. A 2.0.2 `.nup` works too and needs no
  keys; add the DLC 2 `.nsp` with your `prod.keys` / `title.keys` if you want the
  DLC. Bundled mod setup is included.
- **Existing installation**: close the game and use **Update now**, or copy the
  complete archive over the existing installation, merging folders. Keep your
  saves, settings, locally generated game code and installed mod data.

### Linux (`Lumiose-Online-linux-experimental.zip`)
- **New installation**: extract the complete **Lumiose Online Linux** folder into
  a writable location (including an SD card) and run **Lumiose Online**.
- **Existing installation**: close the game and use **Update now**, or extract
  over your existing installation while preserving `usr/bin/extracted`,
  `usr/bin/save`, `usr/bin/larecomp.ini`, and `usr/bin/lumiose`.

### First launch after updating to v0.1.34
- Keep the preparation window open. Because v0.1.34 integrates upstream ZA Recomp
  v0.1.19–v0.1.27+ (code-mod entry pads, Oodle retry, FPCR/FTZ fixes), game code
  and control glyphs refresh once on first launch. Your saves, settings, and
  customized bindings remain intact; **Restore default controls** in
  **Settings > Controls** adopts the default layout.

## What's new in v0.1.34

- **Synced with Hexveil404/PokeZ-ARecomp through v0.1.27+**: code mods
  (`exefs/subsdk` and `.pchtxt`), P2P Link Play (`F1 > Online`), Mystery Gift,
  `F1 > Content` (Ranked Mega Stones & trade evolutions without trading), 21:9+
  widescreen, Full-detail models, Draw distance scaling, DLAA object motion,
  `zaimport` integrity checks, Oodle `oodec` fallback, and GPU/frame-pacing fixes.
- **Switch 2 Edition & Linux GPU**: `.nup` support with 1 GB guest-window import,
  Mesa 27 RADV RDNA4 crash fix, RADV discrete-GPU black-world fix, and optional
  Linux AMD FSR 4.1.2 upscaling.
- **Maintained fork**: Update checks and release downloads now point to
  `mitch030504/PokeZ-ARecomp-Online`.

## Native PC controls

WASD movement; mouse camera; E interact; Shift sprint; Space dodge; Ctrl crouch.
Tab toggles a valid lock-on and releases when its target is lost. Hold RMB to
aim a Poké Ball, LMB to throw, and release RMB to put the ball away. Wheel cycles
balls while aiming, or party members otherwise. Middle-click sends/switches or
recalls the selected Pokémon. Moves use 1/2/3/4; Q is Mega Evolution; R is Plus.

Esc opens the main menu or goes back. I opens Satchel, B Boxes, P Pokédex,
O Mable's Research, and M the map. Map: wheel zoom, WASD pan, E interact.
Satchel tabs: A/D. Menu up/down: W/S. Hover and click to select in menus.
Drag Pokémon between Box/party slots, and eligible items onto party members.
Shop and clothing clicks remain tied to the displayed item after scrolling or
changing tabs. Click outside a context menu to close it.

Prompts follow keyboard/mouse, Xbox or generic-controller input and configured
bindings. With a controller connected the cursor stays visible: click mod icons
and menus directly. Keyboard-only players can hold Left Alt for overworld UI.
See **docs/PC-CONTROLS.md** for the complete guide.

## Support

Please report fork/launcher bugs on
[GitHub Issues](https://github.com/mitch030504/PokeZ-ARecomp-Online/issues) (or in
the **LumioseOnline Discord** for online-mod issues), including the affected
screen, the action, and `logs/play.log`. Game ROMs, extracted game assets,
generated game libraries, saves, settings and caches are not distributed.
