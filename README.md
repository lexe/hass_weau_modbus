# Hardware

Any RS485 kit should work, in this example I used:
- W'eau 7.6 kW heat pump WFI-007
- M5Stack Atom S3 Lite
- M5Stack RS485 Base

I'm a big fan of the Atom's because of the fact you can power it in most cases from the device you're trying to integrate. It's also small so you can easily & safely leave it in the devices housing without having to worry about additional cable management.

# Connection

I connected the 4-wires using a JST XH 4 pin connector to the PCB. There's a second RS485 port but I couldn't get it to work so i used the primary interface of the wired controller. If you're not comfortable opening up the heatpump's casing, you could wire it to the wired controllers connector instead.

# Reverse engineering the registers

I've received some modbus documentation from the supplier but this was worthless, so I decided to guess the registers based on the wired controllers info & the official heat pump manual. 

I started reading out registers starting from 0 & I quickly noticed the parameters named in the manual are in the same order of the registers. So C01 in the manual corresponds to register address 0, C10 equals address 9 and so on. 

After the last sensor (C30 in my case) the registers would continue with the mode of the heatpump. In my case: 0=off, 1=eco, 2=boost. I didn't bother the cooling modes.

The settings (P01-P05) were the next registers.

# Notes

This is still a work in progress. Some registers do not correspond with the official manual so I'm trying to decifer some more stuff but it's a start.
