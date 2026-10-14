# Alex Kidd in Miracle World for the ZX Spectrum Next: changelog

## 1.5.1 (2026-10-14)

A fix to the conversion; the game plays exactly as 1.5.

- Fixed a rare black screen after a screen change. On the Next, the frame interrupt could arrive
  halfway through the conversion's handling of one of the game's video writes, which a real
  Master System never allows. At the moment the game turns the display back on (after a death,
  a level or a room change) that could lose the write and leave the screen black, with the game
  still running, until the next screen change. The interrupt now waits until the write is done,
  as on the Master System. Found while porting another game with the same layer; measured in
  MAME across every level and game state, with odds of very roughly one in a few thousand
  screen changes.
- The title credit and the start menu say 1.5.1.
- SD saves made by 1.5 are refused by 1.5.1 (each build only loads its own); quick saves in memory
  are unaffected.

## 1.5 (2026-10-13)

The first release. Made from the Master System cartridge, Rev 1.

**Running on the Next**
- The game's own code runs on the Next at full speed, with the picture checked frame by frame
  against the Master System original.
- No sprite flicker and tear-free scrolling.
- Music and sound on the Next's AY chips, in stereo or mono.
- Background drawn in front of sprites, as on the Master System (the dialogue boxes hide the
  bosses).

**New**
- A start menu: starting level, lives, infinite lives, janken help, 50 or 60 Hz, palette and
  sound options.
- Redefinable keys, Kempston joystick and Mega Drive pad support.
- Quick save and load in memory, and save and load to the SD card.
- A credit on the title screen, in the border below the picture.

**Gameplay (version 1.5)**
- Tighter controls: Alex stops in half the distance and drifts far less after a jump.
- Coyote time: a jump pressed just after walking off a ledge still works.
- A longer punch, so hits that look like they connect do.
- No gotcha ghosts from "?" boxes, skull boxes or the King of Nibana.
- Igul's letter is in Radaxian Castle from the start.
- The crown puzzle ignores wrong glyphs instead of trapping you with the Grim Reaper.
- A free continue at GAME OVER: one press, keeping your money.
- Janken can be learned and read: fixed patterns per boss, and by default his hand flashes in
  his thought bubble when it changes.
- Tidier dialogue.

The attract-mode demos still play the original game, which their recorded inputs need.
