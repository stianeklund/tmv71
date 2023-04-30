# Documenting the Kenwood TM-V71A/E control head protocol


This repo contains some findings from sniffing the uart data from the Kenwood TM-V71A; should apply to the TM-V71E as well, possibly the DM710.

The data is 57600 Baud UART, 8 bit, no parity.

Pin out (RJ11) control head:

Pin Note Color
1   10v  Black
2   Gnd  Red
3   RX?  Green
4   TX   Yellow


Documentation is broken into separate files:

* [Display](Display.md) display data to and from the display
* [Buttons](Buttons.md) button presses on the control head unit

