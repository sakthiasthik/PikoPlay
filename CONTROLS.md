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

## Where games go

| System | Path on the console |
|---|---|
| Game Boy | `/roms/gb/*.gb` |
| Game Boy Color | `/roms/gbc/*.gbc` |
| NES | `/roms/nes/*.nes` |
| Atari 2600 | `/roms/atari/*.a26` |

Saves live in `/saves/`. Copy games with `pikolink put <file> <path>` (see the README).
