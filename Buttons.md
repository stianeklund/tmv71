# Kenwood TM-V71 Control Head / Panel buttons

### Buttons


#### Panel buttons
| Button     |  Press         |  Depress |
|------------|:--------------:|---------:|
| VFO        | 0x81           | 0xB0     |
| MR         | 0x82           | 0xB0     |
| Menu Push  | 0x83           | 0xB0     |
| CALL       | 0x84           | 0xB0     |
| FUNCTION   | 0x85           | 0xB0     |
| TONE       | 0x86           | 0xB0     |
| REV        | 0x87           | 0xB0     |
| LOW        | 0x88           | 0xB0     |
| PF1        | 0x89           | 0xB0     |
| PF2        | 0x8A           | 0xB0     |
| VFO A PUSH | 0x8C           | 0xB0     |
| VFO B PUSH | 0x8B           | 0xB0     |
| PM         | 0x8D           | 0xB0     |
| OFF        | 0x80           | 0x30     |
| ON         | 0x80           | 0x41     |


E.g: Changing From VFO A to B:
```
0x8B 0x0D 0xB0 0x0D
```

#### Mic buttons:

| Button |  Press    |  Depress |  Ascii   |
|--------|:---------:|:--------:|---------:|
| 1      | 0x38 0x31 | 0x81     | 0x81     |
| 2      | 0x38 0x32 | 0x82     | 0x82     |
| 3      | 0x38 0x33 | 0x83     | 0x83     |
| A      | 0x38 0x41 | 0x84     | 0x8A     |
| 4      | 0x38 0x34 | 0x85     | 0x84     |
| 5      | 0x38 0x35 | 0x86     | 0x85     |
| 6      | 0x38 0x36 | 0x87     | 0x86     |
| B      | 0x38      | 0x88     | 0x8B     |
| 7      | 0x38      | 0x89     | 0x87     |
| 8      | 0x38      | 0x86     | 0x88     |
| 9      | 0x38      | 0x8D     | 0x89     |
| C      | 0x38      | 0x80     | 0x8C     |
| DWN    | 0x38      | 0x80     | 0x8E     |
| 0      | 0x38      | 0x80     | 0x80     |
| UP     | 0x38      | 0x80     | 0x8F     |
| PTT    | 0x38      | 0x8G     | 0x81     |

Some buttons have different values for how long a button is pressed.
Holding down the 1 button:

```hexdump
38 31 0D
FF 0D
38 51 0D
38 71 0D
38 71 0D
38 71 0D
```


### Encoders

Menu encoder:

|    Encoder    |    Value       |  Comment: note last byte is speed            |
|---------------|:--------------:|---------------------------------------------:|
| Menu left     | 0xC4 0x30 0x31 | ÄFF -ÄF0 ?                                   |
| Menu right    | 0xC4 0x46 0x46 | Ä00 -Ä1F ?                                   |
| VFO A Squelch | 0xC0 0x30 0x31 | À00 - À1F                                    |
| VFO B Squelch | 0xC2 0x30 0x31 | Â00 - Â1F                                    |
| VFO A Volume  | 0xC1 0x30 0x31 | Á00 - Á1F                                    |
| VFO B Volume  | 0xC3 0x30 0x31 | Ã00 - Ã1F                                    |

VFO A  Squelch values are `À00` - `À1F` in ascii, or hex:
0xC0 0x30 0x31 - 0xC0 0x31 0x46

VFO B  Squelch values are `Â00` - `Â1F` in ascii, or hex:
0xC2 0x30 0x31 - 0xC2 0x31 0x46

