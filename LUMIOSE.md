# Lumiose Online integration

This fork (`mitch030504/PokeZ-ARecomp-Online`) is based directly on
**[Hexveil404/PokeZ-ARecomp](https://github.com/Hexveil404/PokeZ-ARecomp)** and adds the Lumiose Online integration,
native PC keyboard/mouse controls ([docs/PC-CONTROLS.md](docs/PC-CONTROLS.md)), launcher artwork, and the bundled
Lumiose mod module. It does not contain Pokémon game files, extracted game assets, saves, or game code generated from
a player's copy. Each player must provide and extract their own Pokémon Legends: Z-A game, update and DLC.

The launcher checks releases from `mitch030504/PokeZ-ARecomp-Online`. The artwork is embedded into the launcher
executable during its build. Upstream ZA Recomp features—including code mods (`exefs/subsdk` and `.pchtxt`), P2P Link
Play, Mystery Gift, `F1 > Content`, 21:9 widescreen, and full-detail/draw-distance options—remain available alongside
Lumiose Online.

## Windows integration from a source checkout

For packaged Windows and Linux releases, see [LUMIOSE-RELEASE.md](LUMIOSE-RELEASE.md) and [CHANGELOG.md](CHANGELOG.md).
To build or work on the integration from a source checkout on Windows, build the launcher with the Windows instructions
(`docs/BUILD-windows.md`), and use ZA Recomp's normal setup to make `extracted/` and its game library from your own
game files. The game must be version 2.0.2. A `.nup` whose update tree is 2.0.2 works the same and needs no keys; put
the Mega Dimension DLC 2 `.nsp` next to it (with your `prod.keys` / `title.keys`) if you want the DLC.
The integration scripts require Python 3.12 with `unicorn`, `capstone` and `lz4`, the built `build/lasrecomp.dll.a`,
and ZA Recomp's Zig distribution.

From the repository root, with that Python environment active, run:

```
python tools/lumiose/setup.py --install "PATH_TO_RECOMP_INSTALL" --zig "PATH_TO_ZIG_DIRECTORY" --server "RELAY_HOST:PORT"
```

## Linux package from a source checkout

To build the portable Linux release (`Lumiose-Online-linux-experimental.zip`) in a clean Ubuntu 22.04 container
matching CI:

```bash
docker build -t za-linux-build -f tools/linux/Containerfile tools/linux
docker run --rm -v "$PWD:/src" -w /src za-linux-build bash -euo pipefail -c '
  git config --global --add safe.directory /src
  apt-get update -qq && apt-get install -y --no-install-recommends dotnet-sdk-8.0 python3-venv zip
  PYTHON=python3.12 ZIP=0 DEB=0 tools/za/dist-linux.sh
  bash tools/lumiose/package_linux.sh
'
```

## Preparation & mod updates

Preparation uses only the local player's game files to build the matching mod and game libraries in their installation.
The scripts write their work files into the installation, not this repository. Do not commit that output.

When the mod downloads an update, close the game as directed and use the same start command. The updater prepares the
matching libraries and tests startup before activating them. It blocks startup and reports an error if an update is
older or its compatibility signatures no longer match; a future mod version may require integration changes. The
launcher release check is separate from the mod's own update mechanism.
