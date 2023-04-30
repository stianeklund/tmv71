# Kenwood TM-V71A/E Display


Bootup (display to radio):

Text shown with `{}` brackets is hexadecimal


Similar to the TS-480 it reads out the encoder values on bootup:

```
{FF}

0

A
¿ÿÿÿ
Â08
Ã04
À00
Á00
Â08
Ã04
À00
Á00
Â08
Ã04
```

```hexdump
80 41 0D
BF FF FF FF 0D
C2 30 38 0D
C3 30 34 0D
C0 30 30 0D
C1 30 30 0D
C2 30 38 0D
C3 30 34 0D
C0 30 30 0D
C1 30 30 0D
C2 30 38 0D
C3 30 34 0D
```

---

This is data sent to the display from the radio, (pin 3, green)
Keep alive, when panel is on

FF 0D


Power up sequence (dumped using hercules and a cheap uart to usb adapter):

init / power on is probably 01.

```
00



01
7
20
38
4HELLO 
7
@…€
Z 13LA2FTA €„€€€€€€€€€€€€€
[  3LA5TR{FF} €‚ƒ€€€€€€€€€€€€
J€00
K€00
A€€€€€€€€
C €
J00
```

```hexdump
30 31 0D
37 0D
32 30 0D
33 38 0D
34 48 45 4C 4C 4F 20 0D 37 0D
40 8A 80 0D
5A 20 20 20 31 34 34 35 38 35 4F 84 91 84 81 80 80 80 80 80 80 80 80 80 80 80 80 0D
5B 20 20 20 31 36 35 36 4F 4F 4F 84 80 81 83 80 80 80 80 80 80 80 80 80 80 80 80 0D
4A 80 30 30 0D 4B 80 30 30 0D 41 80 80 80 80 80 80 80 80 0D
43 A0 80 0D
4A 81 30 30 0D
FF 0D
```

Changing vfo's / switching between A/B:
```
@…€ <-- A
@Š€ <-- B
```

Seems somewhat similar to the TS-480 :)

### VFO A / left segment


Changing stored memories using the left menu button:
Not sure what Z is but 14 is the number displayed indicating which memory number it is

Memory:
```
Z 14LA8VRR €„€€€€€€€€€€€€€
```

Changing from memory to vfo, mode, updating VFO A:

```
Z   144585O„‘„€€€€€€€€€€€€
```

hex:
```
5B 20 20 33 4C 41 35 54 52 FF 20 80 90 82 83 80 80 80 80 80 80 80 80 80 80 80 80 0D FF
```

Similar for VFO B:
```
[   432975O„€‚ƒ€€€€€€€€€€€€
```
hex:
```
5B 20 20 20 34 33 32 39 37 35 4F 84 80 82 83 80 80 80 80 80 80 80 80 80 80 80 80 0D FF
```
vfo to memory vfo B:
```
[  3LA5TR{FF} €‚ƒ€€€€€€€€€€€€
```

Function button, turning the function mode on:

```hexdump
5B 20 20 33 4C 41 35 54 52 FF 20 80 90 82 A3 33 80 80 80 80 80 80 80 80 80 80 80 0D
41 80 80 80 81 80 80 80 80 0D
```
function mode on:
```
[  3LA5TR{FF} €‚£3€€€€€€€€€€€
```

function mode off:
```
[  3LA5TR{FF} €‚ƒ€€€€€€€€€€€€
```

Tone selections, T button:
```
[  3LA5TR{FF} €‚ƒ€€€€€€€€€€€€  <-- Off
[  3LA5TR{FF} €‘‚ƒ€€€€€€€€€€€€ <-- T
[  3LA5TR{FF} €’‚ƒ€€€€€€€€€€€€ <-- CT
[  3LA5TR{FF} €”‚ƒ€€€€€€€€€€€€ <-- DCS
```

Call frequency:
```
[  C1457OOO„‘‚ƒ€€€€€€€€€€€€{0D}
```


TODO need to document this where the hex data is diffed, might be easier

Power level change, VFO B:
```
[  C1457OOO„‘„ƒ€€€€€€€€€€€€
[  C1457OOO„‘ƒ€€€€€€€€€€€€
[  C1457OOO„‘‚ƒ€€€€€€€€€€€€
[  C1457OOO„‘„ƒ€€€€€€€€€€€€
[  C1457OOO„‘ƒ€€€€€€€€€€€€
[  C1457OOO„‘‚ƒ€€€€€€€€€€€€
[  C1457OOO„‘„ƒ€€€€€€€€€€€€
```

Power level change, note hex 81, 82 84
```
5B 20 20 43 31 34 35 37 4F 4F 4F 84 91 81 83 80 80 80 80 80 80 80 80 80 80 80 80 0D FF 0D
5B 20 20 43 31 34 35 37 4F 4F 4F 84 91 82 83 80 80 80 80 80 80 80 80 80 80 80 80 0D FF 0D
5B 20 20 43 31 34 35 37 4F 4F 4F 84 91 84 83 80 80 80 80 80 80 80 80 80 80 80 80 0D FF 0D
```


Clear VFO A:
```
Z   ------ „‘„€€€€€€€€€€€€
```
