# Alex Kidd in Miracle World for the ZX Spectrum Next

Sega's 1986 Master System game, running on the ZX Spectrum Next as an improved "version 1.5".
The game's own Z80 code runs on the Next; a small hardware layer written for this project
stands in for the Master System's video chip, sound chip, joypad and cartridge banking.

**No game data is included.** You make the `.nex` from your own cartridge dump with the patch,
`alexkidd.bps`.

## What you need

The **Rev 1** cartridge dump, exactly this file:

| | |
| --- | --- |
| No-Intro name | Alex Kidd in Miracle World (USA, Europe, Brazil) (En) (Rev 1) |
| Usual file name | `Alex Kidd in Miracle World (USA, Europe) (Rev 1).sms` |
| Size | 131,072 bytes |
| CRC32 | `AED9AAC4` |
| MD5 | `f43e74ffec58ddf62f0b8667d31f22c0` |
| SHA-1 | `6d052e0cca3f2712434efd856f733c03011be41c` |

The patch checks the dump and refuse any other revision or a bad copy.

## Making the .nex

Any BPS patcher works. The result is a ZX Spectrum Next program: **name it `alexkidd.nex`**.
Patchers name the output after the ROM, so it will end in `.sms` until you rename it.

- **In a browser:** Rom Patcher JS (https://www.marcrobledo.com/RomPatcher.js/). Choose the
  `.sms` as the ROM file and `alexkidd.bps` as the patch, apply, save, and rename the saved file
  to `alexkidd.nex`.
- **Floating IPS (Flips):** Windows, Linux or macOS. "Apply Patch", and save as `alexkidd.nex`.

The finished file is 180,736 bytes, SHA-256
`f5ada509cec3c2e6c02f298bbe7efbd39e3c1d630327355aeab957cf1d943424`.

## Play

- **Spectrum Next:** copy `alexkidd.nex` to the SD card and open it from the Browser. It needs
  a core recent enough to place the tilemap in bank 7 (the `.nex` asks for 3.1.5); the game
  switches the machine to 28 MHz and 60 Hz itself.
- **ZEsarUX** (tested with 13.0): `zesarux --machine TBBlue --snap alexkidd.nex`

The game starts at a menu: 1 (or joystick fire) plays, 2 opens the options, 3 the controls.

| Options (0 goes back) | |
| --- | --- |
| 1 | Starting level, 1-17 |
| 2 | Starting lives, 1-9 |
| 3 | Infinite lives |
| 4 | Janken (the rock-paper-scissors duels): tells (the default: the boss's hand flashes in his thought bubble when it changes during the chant), mind read (his hand always shown, as with the Telepathy Ball), or normal (no clue) |
| 5 | Video 60 Hz (the speed the game was made for) or 50 Hz (as a PAL Master System: about 17% slower) |
| 6 | Palette: original, or soft (lifted darks, gentler whites) |
| 7 | Sound: stereo (tones left / centre / right, noise centre) or mono |

| Controls (0 goes back) | |
| --- | --- |
| 1 | Redefine keys: press a key for Up, Down, Left, Right, Jump, Punch and Pause in turn |
| 2 | Kempston joystick on / off |

Controls while playing:

| Master System | Next |
| --- | --- |
| D-pad | Q/A/O/P or the cursor keys (5-8), or a Kempston joystick |
| Button 1 (jump) | Z or SPACE, joystick fire, Mega Drive pad A or B |
| Button 2 (punch) | X or M, joystick fire 2, Mega Drive pad C |
| Pause | ENTER, or START on a Mega Drive pad |
| Quick save / load | SYMBOL SHIFT + S / SYMBOL SHIFT + L (in memory, any moment of play) |
| Save to SD / load from SD | SYMBOL SHIFT + W / SYMBOL SHIFT + R (`AKSAVE.BIN`, the quick save, in the current directory) |

Redefined keys replace the defaults for that action (the cursor keys stop working for it).
Menu settings last until the Next is reset. An SD save made by a different build of this
conversion is refused rather than loaded.

## Version 1.5: what plays differently

The version history is in `CHANGELOG.md`.

This is the original game with its best-known annoyances fixed, in place (there is no "classic"
switch). The attract-mode demos still run the original game, because their recorded inputs need
it.

- **Movement:** Alex stops in half the distance when you let go (8 px instead of 16 from full
  speed), and drifts far less after a jump (22 px instead of 62 when you let go in the air).
  Acceleration, top speed and jump height are unchanged.
- **Coyote time:** a jump pressed up to 5 frames after walking off a ledge still works (the
  original allows none).
- **Punch:** reaches 4 px further (27 px in front of Alex instead of 23) and is 2 px taller, so a
  punch that looks like it touched an enemy does.
- **No gotcha ghosts:** "?" boxes give a ring where they used to release the Grim Reaper; the pink
  skull boxes no longer summon it; nor does visiting the King of Nibana without the letter.
  Breaking a skull box freezes Alex for a quarter of a second instead of a whole one.
- **Key items:** Igul's letter is in Radaxian Castle from the start. In the original it appears
  only after you free him, so a player who searched its room first found nothing.
- **The crown puzzle:** a wrong glyph is ignored instead of summoning the Reaper in a room you
  can't leave; right glyphs still chime, so the order can be found. The King of Nibana now says
  how to read the stone slab.
- **Continue:** at GAME OVER, press jump or punch once to carry on from the start of the level
  with 3 lives and your money. (The original wanted Up held with eight presses, and 400 Baums.)
- **Janken:** learnable and readable instead of luck. Each boss now throws the same sequence
  every time you meet him (the original's depended on everything that happened before), and he
  no longer changes his mind while you choose. By default his hand flashes in his thought bubble
  each time it changes during the chant: catch the last one and you know his throw. Options, 4
  also offers mind read (always shown) and normal (no clue, patterns still fixed).
- **Dialogue:** the translation tidied within each line's length (no stray quotation marks,
  missing spaces fixed, the duels described as best of three, which they are).

## What to expect

- The picture is the Master System's 256x192, centred, with the game's own palette, framed in
  the game's border colour as on the Master System.
- Sprites never flicker: the Master System's 8-sprites-per-line limit doesn't exist on the Next,
  so the game's flicker workaround is undone.
- The title screen carries a credit in the border below the picture ("ZX SPECTRUM NEXT
  ENHANCED V1.5" and the website). The game's own title, PUSH START BUTTON and Sega copyright are
  untouched.
- Background that sits in front of sprites on the Master System does so here too: the dialogue
  boxes hide the bosses behind them, for example.
- Scrolling is tear-free: the scroll and the sprites change between frames, never part-way down
  the screen.
- Sound: the Master System's three tone channels play on the Next's first AY chip and the noise
  channel on the second, converted to the AY's clock. It is close, not identical.

## How it was checked

Frames from the Next build (ZEsarUX 13.0) were compared pixel by pixel with the same frames of
the Master System game running in MAME 0.289: all 7 frames compared across the four attract
demos are identical. Keys, redefined
keys, the Kempston joystick and pause were checked against the game's own joypad state. The
version 1.5 movement, coyote time, punch reach, continue and letter changes were measured in MAME
on a Master System ROM with the same changes, against the original; the attract demos still
match MAME after them.

## Tested on

- ZEsarUX 13.0 (TBBlue): the comparison above and the project's play tests.
- A Tang Nano 20K FPGA board running the NextNano core (a ZX Spectrum Next core), 2026-10-13:
  plays well. That test was of the build just before the title-screen credit was added.
- Not yet tried on a ZX Spectrum Next itself or a Nextcade cabinet.
- The patch was applied with Rom Patcher JS's own library (github.com/marcrobledo/RomPatcher.js,
  as of 2026-08-28, the code its web page runs) with checksum validation on: the result is
  identical to the tested `.nex`, and a dump altered by one byte is refused ("Invalid input ROM
  checksum"). Flips hasn't been tried.

## Credits

- *Alex Kidd in Miracle World* © Sega 1986.
- ZX Spectrum Next conversion and version 1.5 by Jon Attree: https://jonattree.com
