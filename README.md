# Documenting the Kenwood TM-V71A/E control head protocol


This repo contains some findings from sniffing the uart data from the Kenwood TM-V71A; should apply to the TM-V71E as well, possibly the DM710.

The data is 57600 Baud UART, 8 bit, no parity.

Pin out (RJ11) control head:

Pin Note Color
1   10v  Black
2   Gnd  Red
3   RX?  Green
4   TX   Yellow



TODO put this in separate file:
## Display data

This is data sent to the display from the radio, (pin 3, green)
Keep alive, when panel is on

FF 0D


Power up sequence (dumped using hercules and a cheap uart to usb adapter):

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
{5B}{20}{20}{33}{4C}{41}{35}{54}{52}{FF}{20}{80}{90}{82}{83}{80}{80}{80}{80}{80}{80}{80}{80}{80}{80}{80}{80}{0D}{FF}
```

Similar for VFO B:
```
[   432975O„€‚ƒ€€€€€€€€€€€€
```
hex:
```
{5B}{20}{20}{20}{34}{33}{32}{39}{37}{35}{4F}{84}{80}{82}{83}{80}{80}{80}{80}{80}{80}{80}{80}{80}{80}{80}{80}{0D}{FF}
```
vfo to memory vfo B:
```
[  3LA5TR{FF} €‚ƒ€€€€€€€€€€€€
```

Function button, turning the function mode on:

```hexdump
{5B}{20}{20}{33}{4C}{41}{35}{54}{52}{FF}{20}{80}{90}{82}{A3}{33}{80}{80}{80}{80}{80}{80}{80}{80}{80}{80}{80}{0D}{41}{80}{80}{80}{81}{80}{80}{80}{80}{0D}
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
