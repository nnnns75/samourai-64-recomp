<div align="center">

# SamuRecomp

**Samurai Shodown 64 (Samurai Spirits 64), rebuilt as a native program.**<br>
An unofficial port of SNK's 1997 Hyper Neo Geo 64 arcade fighter, built from the arcade ROMs you own.

[Français](README.fr.md) · [Build guide](docs/BUILD.md) · [Status](#status) · [Credits](#credits-and-licences)

</div>

> [!IMPORTANT]
> SamuRecomp does **not** include the game, and it never will. You need your own legally obtained copies of two
> arcade ROM sets, as MAME names them: `sams64.zip` (Samurai Shodown 64) and `hng64.zip` (the Hyper Neo Geo 64
> system ROMs). The build steps translate the game's program on **your** machine. This repository holds only
> project code and open-source tools. Please do not upload the built program, `recomp/generated/`, `work/` or
> any ROM anywhere: they are made from SNK's game (the `.gitignore` already excludes them).

## What it is

Not an emulator: the arcade's MIPS program is translated to C with
[N64Recomp](https://github.com/N64Recomp/N64Recomp) and compiled together with a hand-written model of the
Hyper Neo Geo 64 hardware (video, 3D, sound, I/O board). It is the same approach as
[ReBuriki](https://github.com/QuietClubGames/ReBuriki) for Buriki One, which this project is based on.

## Status

Early but playable. Tested so far (Wine on a Steam Deck, with a window and headless):

| Works | To check / not done |
|---|---|
| Boot, logos, attract mode, title screen | Sound: the sound CPU runs, but listening tests are still needed |
| Coin, start, mode and fighter select | Widescreen and the high-resolution 3D option (inherited from ReBuriki) are untested on this game |
| Full fights in colour (2D layers, textured 3D fighters and stages, HUD, combos) | Arcade settings (difficulty, free play, blood...): need this game's save-memory addresses |
| Window / borderless / full screen, scaling and filters, keyboard and controller menus | Online play and "Unlock Silber" are Buriki One features: disabled (greyed out) |
| | Windows `Setup.exe` installer is not adapted yet; building is done with the scripts in `tools/sams64` |

Only the `sams64` set (Samurai Shodown 64, MAME revision) is supported for now. `sams64_2` (Warriors Rage), Fatal
Fury: Wild Ambition, Beast Busters, Xtreme Rally and Roads Edge are not.

## Build it

See **[docs/BUILD.md](docs/BUILD.md)**. In short: unpack your ROMs with `tools/sams64/unpack_roms_sams64.py`, translate
with `translate_sams64.py`, compile with `build_sams64_linux.py` (Linux, cross-compiling a Windows program, tested
under Ubuntu 22.04), then run it with Wine or on Windows.

## Controls (defaults)

Player 1: arrows, `Z X C V` = A B C D, `1` start, `5` coin. Player 2: `R F D G`, `A S Q W`, `2`, `6`.
`Esc` / `Tab` menu, `F11` full screen, `F2` arcade Test menu, `9` Service. Xbox-style controllers work (remap in the menu).

## How it was ported

[docs/BOOT_PLAN.md](docs/BOOT_PLAN.md) records the boot layout, each problem met and how it was found (including the
vblank status register that kept the game from ever loading its palettes), and
[docs/PORTING_MAP.md](docs/PORTING_MAP.md) lists what in ReBuriki is specific to Buriki One. The diagnostic tools in
`tools/sams64/` (`diag*_sams64.py`, `autodiag*_sams64.py`, `whynot_sams64.py`) are the method that worked; they are
meant to be reused for the other Hyper Neo Geo 64 games.

## Credits and licences

- [ReBuriki](https://github.com/QuietClubGames/ReBuriki) by QuietClubGames (MIT): the runtime, front end and build
  chain this project adapts.
- [MAME](https://www.mamedev.org/) (`hng64` driver and I/O board firmware wiring): LGPL-2.1+ / BSD-3-Clause parts
  ported to the runtime, see [LICENSE.md](LICENSE.md) and `licenses/`.
- [N64Recomp](https://github.com/N64Recomp/N64Recomp) (MIT) translates the MIPS code.
- ReLayer (MIT): front-end pieces used by ReBuriki.

Everything is unofficial and not affiliated with SNK. Samurai Shodown, Samurai Spirits and Hyper Neo Geo 64 belong
to their owners.
