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

Supported cartridge chips: no MBC, MBC1, MBC2, MBC3 (RTC clock included), and all MBC5
variants (types `0x19`–`0x1E`, with or without RAM / battery / rumble) — nearly every
GB/GBC game ever sold, including GTA, GTA 2, Spider-Man, Pokémon, Tetris, Zelda, Mario
Land and Wario Land. Limits:

- Cartridge save RAM must fit 32 KB (all commercial games do)
- Games needing MBC7 (Kirby Tilt 'n' Tumble, Command Master), MBC6, the Game Boy Camera,
  or IR link features (Robopon, Pocket Pikachu) will not start
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
| Grand Theft Auto 2 (GBC) | ✅ works (MBC5, no save RAM) |
| Legend of Zelda - Link's Awakening DX (GBC) | ✅ works (MBC5, 32K battery save) |
| Mortal Kombat Trilogy (NES) | ✅ works (mapper 4) |
| Prince of Persia (NES) | ✅ works (mapper 2) |
| Spider-Man (GBC) | ✅ works (MBC5, no save RAM) |
| Super Mario Bros. 3 (NES) | ✅ works (mapper 4) |

### Game-specific notes

- **Grand Theft Auto (GBC):** hold **SELECT + A** together to enter a vehicle, press
  **SELECT** to exit, B fires (needs a weapon), SELECT on foot changes weapon. The game
  never tells you this — it was only in the printed manual.
- **Grand Theft Auto 2 (GBC):** same idea — hold **SELECT + A** to enter a vehicle and
  press **SELECT** to get out. No save file (the cartridge has no save RAM).
- **Spider-Man (GBC):** A jumps (and swings on webs in mid-air), B attacks with webs.
  The Web Ball is a quick **B → A** roll of the thumb.

## How to play each game

START pauses in almost every game. X and Y do nothing in NES/GB/GBC games. To leave any
game, hold SELECT + START for one second.

| Game | Controls | Guide |
|---|---|---|
| Asteroids (Atari) | LEFT/RIGHT rotate, UP thrust, DOWN special move (hyperspace / shields / flip, per variation), A or B fire. START = start game, SELECT = pick a game variation | [Manual scans](https://archive.org/details/atari_2600_asteroids) |
| Batman - The Animated Series (GB) | A jump (UP + A fires the grapple), B punch / kick / Batarang, SELECT toggles Batarang | [Manual PDF](https://www.thegameisafootarcade.com/wp-content/uploads/2017/03/Batman-The-Animated-Series-Game-Manual.pdf) |
| Castlevania - The Adventure (GB) | A jump, B whip, UP climbs ropes, DOWN crouches | [Gameplay guide](https://strategywiki.org/wiki/Castlevania:_The_Adventure/Gameplay) |
| Castlevania II - Belmont's Revenge (GB) | A jump, B whip, UP + B sub-weapon (axe / holy water) | [CastleVania Dungeon](http://hardcoregaming101.net/cvbackup/cv2br.htm) |
| Contra (NES) | A jump, B shoot, D-pad move/aim (hold UP to aim up, DOWN crouches, DOWN + A drops through platforms). 30 lives: UP UP DOWN DOWN LEFT RIGHT LEFT RIGHT B A START | [FAQ PDF](https://www.video-games-museum.com/en/faqs/Nes/6355-Contra.pdf) |
| Contra Force (NES) | A jump, B shoot, START = pause menu (characters + battle plans), SELECT switches weapon when powered up | [Manual text](http://www.atarihq.com/tsr/manuals/contraf.txt), [Walkthrough](https://www.ign.com/articles/2007/04/30/contra-force-walkthrough-784592) |
| Double Dragon (NES) | A punch, B kick, A + B jump, double-tap LEFT/RIGHT head butt | [Manual text](https://www.atarihq.com/tsr/manuals/dbldragn.txt) |
| Grand Theft Auto (GBC) | On foot: D-pad move, **hold SELECT + A** to enter a car, SELECT exit / change weapon, B fire. In a car: A accelerate, D-pad steers | [Controls](https://en.wikigta.org/en-wiki/wiki/Controls_(Grand_Theft_Auto)), [How to drive](https://www.gta-growth.com/gta/controles) |
| Grand Theft Auto 2 (GBC) | Same vehicle combo: **hold SELECT + A** to enter, SELECT to exit. D-pad moves; B changes weapon | [Controls](https://gta.fandom.com/wiki/Controls_for_GTA_2) |
| Legend of Zelda - Link's Awakening DX (GBC) | A sword (default), B assigned item, START inventory, SELECT map, A + B + START + SELECT = save | [Controls](https://strategywiki.org/wiki/The_Legend_of_Zelda:_Link%27s_Awakening/Controls) |
| Mortal Kombat Trilogy (NES) | A punch, B kick, D-pad move (back = block, UP jump, DOWN crouch), specials = direction sequence + A or B | [Move list (unlicensed port, approximate)](https://icemantraveler.github.io/mkksg/fan_made/mk1ae_default.htm) |
| Prince of Persia (NES) | A jump / sword attack, B careful step / block, UP jump up / climb, DOWN crouch, UP + A long jump | [General FAQ](https://www.ign.com/articles/2004/09/23/prince-of-persia-1989-general-faq-550561) |
| Spider-Man (GBC) | A jump / web-swing, B web attack, Web Ball = roll B → A, D-pad move | [IGN guide](https://guidesarchive.ign.com/guides/14631/basics.html) |
| Super Mario Bros. 3 (NES) | A jump / swim, B run / fireball, DOWN crouch / slide, START pause, SELECT uses item on the map screen | [Manual text](https://patpend.net/manuals/nes/super_mario_bros._3.txt) |

## Where games go

| System | Path on the console |
|---|---|
| Game Boy | `/roms/gb/*.gb` |
| Game Boy Color | `/roms/gbc/*.gbc` |
| NES | `/roms/nes/*.nes` |
| Atari 2600 | `/roms/atari/*.a26` |

Saves live in `/saves/`. Copy games with `pikolink put <file> <path>` (see the README).
