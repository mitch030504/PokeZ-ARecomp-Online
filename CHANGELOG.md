# Changelog

All notable changes to **ZA Recomp – Lumiose Online** (`mitch030504/PokeZ-ARecomp-Online`), a fork of [Hexveil404/PokeZ-ARecomp](https://github.com/Hexveil404/PokeZ-ARecomp) with Lumiose Online and native PC controls, are documented in this file.

## [v0.1.34] - 2026-11-24

> **Game code rebuild notice:** This release changes `GAMELIB_ID` (upstream generator, code-mod entry pads, Oodle retry, and FPCR/FTZ updates). Existing installations will automatically recompile the game code once on first launch; saves, settings, and installed mods are preserved.

### Fork & Release Infrastructure
- Reparented and synchronized directly with [Hexveil404/PokeZ-ARecomp](https://github.com/Hexveil404/PokeZ-ARecomp) (`pokemon-za` through `d446462`, bringing in 187 upstream commits spanning v0.1.19 through v0.1.27+).
- Updated in-app update checks, Linux launcher updater, and documentation download/issue links to `mitch030504/PokeZ-ARecomp-Online`.
- Added automated GitHub Actions release builds for Windows (`ZA-Recomp-windows.zip`) and Linux (`Lumiose-Online-linux-experimental.zip`) with SHA-256 checksums and the launcher's game-code rebuild marker.
- Bumped Lumiose `GAME_CODE_REVISION` to `upstream-0.1.27-v1` so existing Lumiose installations refresh compiled game code and control glyphs once.

### Switch 2 Edition & Linux GPU / Upscaling
- **Switch 2 Edition (`.nup`) support**: Import and set up games directly from `.nup` packages (no `prod.keys` needed for `.nup`, with add-on content ID ordering and full 1 GB guest-window import).
- **AMD RDNA4 / Mesa 27.0-devel RADV fix**: Enabled the promoted `VK_EXT_extended_dynamic_state` feature on RADV Vulkan 1.3 devices so `radv_shader_part_cache_get()` initializes its PS epilog cache instead of crashing at first draw.
- **AMD discrete GPU RADV fix (Linux)**: Stopped replacing Pokémon Z-A's guest memory with the empty heap mapping and applied the 256 MB guest-memory import window on all Linux AMD GPUs.
- **Optional AMD FSR 4.1.2 (Linux)**: Added `F1 > Video > Temporal anti-aliasing > AMD FSR 4.1.2` with a user-supplied FidelityFX Vulkan provider (`libamd_fidelityfx_upscaler_vk.so`), compute shader derivatives, and automatic fallback to FSR 2/3.

### Upstream ZA Recomp Highlights (v0.1.19 – v0.1.27+)
- **Code mods (`exefs/subsdk0-9` & `.pchtxt`)**: Run exlaunch / Hakkun code mods and `.pchtxt` patches toggled per mod on the Mods page, coexisting cleanly with Lumiose Online (`LUMIOSE_TEST_MODULE`) and deduplicated `nn::socket`/`nn::nifm` HLE bindings.
- **P2P Link Play (`F1 > Online`)**: Serverless emulated local-wireless link trades and private battles over LAN or internet (STUN/NTP hole punching with HMAC-SHA1 signed packets).
- **Mystery Gift (`F1 > Online > Mystery Gift`)**: Offline-capable Mystery Gift via Project Pokémon's EventsGallery and local wonder cards (`mystery_gift/bcat/normal/`).
- **Online-only content (`F1 > Content`)**: Optional Ranked Battle Mega Stones in Quasartico Inc.'s Mega Shard exchange and trade evolutions without trading (including Inkay at level 30).
- **Widescreen & Visuals**: 21:9+ unlocked aspect ratio with wider menus/HUD width options, Full-detail models (`F1 > Full-detail models`), Draw distance scaling (1.5× / 2× / 3×), DLAA per-object motion vectors for skinned characters, outfit/appearance previews rendered whole at any render scale, and Intel/AMD compute and water-reflection fixes.
- **Controls & Text Input**: First-start Xbox-letters face-button preset for Xbox/PlayStation/Steam Deck controllers plus `F1 > Controls` Nintendo/Xbox presets, left/right stick dead zone and full-speed threshold sliders, multi-gamepad auto-switching, battle moves by position disabled while holding ZR to cancel ball throws, on-screen keyboard for any connected controller (with UTF-8 typing), and text-entry recovery after window focus loss.
- **Integrity, Performance & Stability**:
  - `zaimport` block-level integrity verification (`ErrorOnInvalid`) and start-screen pack verification naming damaged files.
  - Whole-file `lasgame` library fingerprinting, automatic rebuild of damaged libraries, and safe replacement when an older DLL is in use on Windows.
  - Separate `oodec` Oodle retry decoder on failed archive decodes.
  - Constant game speed fixes (roll/dash below 60 fps, channel-0 ladders above 40 fps), smooth distant animation across all four update policies, and host FTZ/DAZ tracking on FPCR writes.
  - Multi-threaded shader preparation with boot progress and low-RAM release (< 12 GB RAM), pipeline compiler-crash survival, AMD GPU write/hang reporting, and recordable bug-report zips (`F8` mark).
  - DLC hidden on game 1.0.0 (avoids 2002-6065 crash), shop applet closed-by-player answer without DLC, and accurate `GetDisplayVersion`.

### Lumiose Online & Native PC Controls
- Retained bundled Lumiose Online (`lumiose/subsdk9`), native PC keyboard/mouse controls, camera distance slider, native Lumiose chat & scroll bridge, Discord Rich Presence, and local icon/model UI compatibility.
- Updated Lumiose and upstream C/Python test suites to match `g_modules[6]` and combined runtime stubs (all Linux and Windows CI checks passing).

---

## Previous Releases (Lumiose Online Lineage)

### [v0.1.33] - 2026-11-14
- Kept mouse cursor visible and clickable for Lumiose overworld icons and mod menus while a controller is connected without requiring Left Alt.
- Preserved mouse-camera isolation in controller mode and keyboard-only Left Alt cursor release.

### [v0.1.32] - 2026-11-13
- Added native PC keyboard/mouse controls (see [docs/PC-CONTROLS.md](docs/PC-CONTROLS.md)), SDK native keyboard-font selector patches, and full Windows launcher packaging.

### [v0.1.28] – [v0.1.31] - 2026-11-08 to 2026-11-11
- Added local UI icon/model preview compatibility ([docs/MOD-UI-COMPATIBILITY.md](docs/MOD-UI-COMPATIBILITY.md)), Discord Rich Presence ABI fixes, Linux UI overlay packaging fixes, and bundled mod setup repairs.

### [v0.1.24] – [v0.1.27] - 2026-11-02 to 2026-11-07
- Added native Lumiose chat and menu input, camera distance setting, Alt touch mode, portable setup completion marker, PT-BR translation setup docs, and bundled Lumiose 1.4.0.

### [v0.1.19] – [v0.1.23] - 2026-10-28 to 2026-11-01
- Initial Lumiose Online integration with ZA Recomp, microphone noise suppression (`rnnoise`), Linux packaging/updater support, and AMD startup fallback fixes.
