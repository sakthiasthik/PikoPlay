# PikoPlay Controls

Button layout: a D-pad (UP, DOWN, LEFT, RIGHT), four face buttons (A, B, X, Y), START and
SELECT. Every system maps its own controls onto these.

## General (menus)

| Action | Buttons |
|---|---|
| Pick a system / item | LEFT / RIGHT (lists also accept UP / DOWN) |
| Open / confirm / start | A (only A starts things) |
| Go back | B |
| Settings: choose a row | UP / DOWN |
| Settings: change a value | LEFT / RIGHT (A also cycles) |
| Leave a game | hold SELECT + START for 1 second (saves are written) |
| Leave USB gamepad mode | hold SELECT + START for 1 second |

A *tap* of SELECT+START is game input; only a one-second hold leaves the game.

## NES

| NES pad | PikoPlay |
|---|---|
| Up / Down / Left / Right | D-pad |
| A | A |
| B | B |
| Start | START |
| Select | SELECT |
| — | X and Y are not used |

Mapper 2 (UNROM, e.g. Contra) and other mappers in InfoNES' table work; mapper 235 and 19
are unsupported. No battery in the ROM header means no save file.

## Game Boy / Game Boy Color

| Game Boy | PikoPlay |
|---|---|
| Up / Down / Left / Right | D-pad |
| A | A |
| B | B |
| Start | START |
| Select | SELECT |
| — | X and Y are not used |

## Atari 2600

| Atari 2600 | PikoPlay |
|---|---|
| Joystick directions | D-pad |
| Fire button | A or B |
| Console Reset switch | START |
| Console Select switch | SELECT |

## Built-in arcade games

Common to all four: START pauses and resumes; A or START starts from the ready / game-over
screen.

| Game | Controls |
|---|---|
| Pong | UP / DOWN moves your paddle. At the ready screen, any D-pad press toggles 1 player / 2 players. In 2-player, player 2 uses Y (up) and A (down). |
| Snake | D-pad steers. |
| Flappy | A, UP or B to flap. |
| Breakout | LEFT / RIGHT moves the paddle; A or UP launches the ball. |

## NEKO (the cat)

LEFT / RIGHT choose an action, A confirms it. The actions are Feed, Pet, Play, Bath and
Sleep. Press A to wake the cat from sleep.

## USB gamepad mode

The console becomes a standard USB HID gamepad for a PC:

| Gamepad button | PikoPlay |
|---|---|
| South (A) | A |
| East (B) | B |
| North (Y) | Y |
| West (X) | X |
| Select | SELECT |
| Start | START |
| D-pad / hat | D-pad |

## Which games work

No emulator runs everything, so pick games by these rules.

### NES

Supported mappers: 0–4, 7–11, 13, 15–18, 21–26, 32–34, 40–51, 57–62, 64–83, 86–90 —
essentially every mapper commercial NES games used. Known examples that work:

- Contra (mapper 2) — tested on the console
- Super Mario Bros. 1 / 2 / 3 (0 / 1 / 4), Zelda I / II (1), Mega Man 1–6 (1 / 4),
  Tetris (0), Metroid (1), Kirby's Adventure (4), DuckTales (2), Batman (4)

Games that will **not** work:

- Castlevania III: Dracula's Curse, Just Breed, Metal Slader Glory (mapper 5, MMC5)
- Lagrange Point (mapper 85, VRC7)
- Namco 163 games such as Mappy Kids (mapper 19, mostly Japan-only)
- Unlicensed multicarts (mappers 6 / 235, e.g. Golden Game 150-in-1)

### Game Boy / Game Boy Color

Supported cartridge chips: no MBC, MBC1, MBC2, MBC3 (RTC clock included), MBC5 — this is
nearly every GB/GBC game ever sold, including GTA, Pokémon (MBC3/MBC5), Tetris, Zelda
games, Mario Land, Wario Land. Limits:

- Cartridge save RAM must fit 32 KB (all commercial games do)
- Games needing MBC7 (Kirby Tilt 'n' Tumble, Command Master), MBC6, the Game Boy Camera,
  or IR link features (Robopon, Pocket Pikachu) will not start
- Dumps whose header declares **plain MBC5 with no RAM** (cartridge type `0x19`) are
  rejected, e.g. some GTA 2 and Spider-Man dumps. MBC5+RAM (`0x1A` / `0x1B`) works fine.
- A bad header checksum (patched/corrupted dumps) is rejected with "BAD ROM CHECKSUM"

### Atari 2600

ROM sizes 2 KB, 4 KB, 8 KB, 12 KB, 16 KB and 32 KB with standard bankswitching
(F8, FA, F6, F4) are supported — that covers most commercial cartridges. Games using
extra chips, such as Pitfall II (DPC), will not start.

### Checked against the console (games_lib/)

Every file below was run through the same checks the firmware performs.

| Game | Result |
|---|---|
| Asteroids (Atari 2600) | ✅ works (8K, F8 bankswitch) |
| Batman - The Animated Series (GB) | ✅ works (MBC1) |
| Castlevania - The Adventure (GB) | ✅ works (MBC1) |
| Castlevania II - Belmont's Revenge (GB) | ✅ works (MBC1) |
| Contra (NES) | ✅ works (mapper 2, tested on the console) |
| Contra Force (NES) | ✅ works (mapper 4) |
| Double Dragon (NES) | ✅ works (mapper 1) |
| Grand Theft Auto (GBC) | ✅ works (MBC5, 8K battery save) |
| Grand Theft Auto 2 (GBC) | ❌ cart type `0x19` (plain MBC5) not supported |
| Legend of Zelda - Link's Awakening DX (GBC) | ✅ works (MBC5, 32K battery save) |
| Mortal Kombat Trilogy (NES) | ✅ works (mapper 4) |
| Prince of Persia (NES) | ✅ works (mapper 2) |
| Spider-Man (GBC) | ❌ cart type `0x19` (plain MBC5) not supported |
| Super Mario Bros. 3 (NES) | ✅ works (mapper 4) |

### Game-specific notes

- **Grand Theft Auto (GBC):** hold **SELECT + A** together to enter a vehicle, press
  **SELECT** to exit, B fires (needs a weapon), SELECT on foot changes weapon. The game
  never tells you this — it was only in the printed manual.

## Where games go

| System | Path on the console |
|---|---|
| Game Boy | `/roms/gb/*.gb` |
| Game Boy Color | `/roms/gbc/*.gbc` |
| NES | `/roms/nes/*.nes` |
| Atari 2600 | `/roms/atari/*.a26` |

Saves live in `/saves/`. Copy games with `pikolink put <file> <path>` (see the README).
