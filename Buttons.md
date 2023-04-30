# Kenwood TM-V71 Control Head / Panel buttons

### Buttons

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
| PF2        | 0x86           | 0xB0     |


### Encoders

Menu encoder:

|    Encoder    |    Value       |  Comment: note last byte is speed            |
|---------------|:--------------:|---------------------------------------------:|
| Menu left     | 0xC4 0x30 0x31 | Last byte is speed, can be 0x36 for example  |
| Menu right    | 0xC4 0x46 0x46 | -                                            |
| VFO A Squelch | 0xC0 0x30 0x31 | À00 - À1F                                    |
| VFO B Squelch | 0xC4 0x46 0x46 | Â00 - Â1F                                    |
| VFO A Volume  | 0xC1 0x30 0x31 | Á00 - Á1F                                    |
| VFO B Volume  | 0xC3 0x30 0x31 | Ã00 - Ã1F                                    |

VFO A  Squelch values are `À00` - `À1F` in ascii, or hex:
0xC0 0x30 0x31 - 0xC0 0x31 0x46

VFO B  Squelch values are `Â00` - `Â1F` in ascii, or hex:
0xC2 0x30 0x31 - 0xC2 0x31 0x46

