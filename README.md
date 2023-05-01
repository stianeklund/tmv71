# Documenting the Kenwood TM-V71A/E control head protocol


This repo contains some findings from sniffing the uart data from the Kenwood TM-V71A; should apply to the TM-V71E as well, possibly the DM710.

The data is 57600 Baud UART, 8 bit, no parity.

RJ11 wiring pinout (male POV):

| Pin | Comment | Wire Color |
|-----|:-------:|:----------:|
|  1  |   10v   | Black      |
|  2  |   Gnd   | Red        |
|  3  |   RXD   | Green      |
|  4  |   TXD   | Yellow     |


RJ45 (Radio side), note this pinout is from the female RJ45 connector's POV.
If you need to make a cable, make sure to mirror the pinout.

| Pin | Comment                                             |
|-----|:---------------------------------------------------:|
|  1  |  PR                                                 |
|  2  |  PB (10V)                                           |
|  3  |  GND                                                |
|  4  |  TXD                                                |
|  5  |  PKS Packet (audio) input                           |
|  6  |  PKD Packet Audio signal for packet  transmission   |
|  7  |  RXD                                                |
|  8  |  SQC    Squelch control                             |

Serial data (also present in on the back din conector is also present on the front), probably for the DM710 or TNC addon?

In general most of these findings should be fairly similar to the DM710 as the control head is interchangable with the TMV71.

Documentation is broken into separate files:

* [Display](Display.md) display data to and from the display
* [Buttons](Buttons.md) button presses on the control head unit

