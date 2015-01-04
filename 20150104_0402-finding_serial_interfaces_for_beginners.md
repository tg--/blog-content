date: 2015-01-04 04:02:38
title: Finding serial interfaces for beginners
category: tricks
tags: other

What I'm describing here probably isn't news for a lot of people, but I think some might find it useful anyway.
If you're tinkering with any embedded device and don't really know how to get started, it always makes sense to look for a UART interface where you might be able to get a console interface to the device.

But how to find it?
Turns out this is usually really easy!

# Needed:

- Device
- Multimeter with 2 probes

# How?
Usually the UART interfaces are extremely simple and operate at 3.3 V.
Basically you need only 3 contact points on the board for a full console.

- TxD: This is where the board sends data
- RxD: This is where it receives
- GND: Just a grounded connection  

Usually the boards have a connector or some pads with 4-8 connections, best look for a connector with 4 Pins first. Additionally this will include a *VCC* connection, this is a connection directly to the boards power. Usually this will be 3.3 V and you should find this pin, but not touch it (as we don't need it).  

1. Set your multimeter to continuity testing (or if not available to low Ohm measurement)
2. Find the GND pin. To do so, just touch your probe to a known grounding point, which might be a pad on the board labeled GND, or if there is no marked one, use a metal shielding of some component or the metallic border of a drill hole.
3. Turn on your device.
4. Set your multimeter to single digit voltage scale (x.yz V).
5. Find the VCC pin. This one will have consistent 3.3 Volts - measure against GND.
6. Find the TxD pin. Here you will see changing voltage. It will change between 1.5 V and 3.3 V.
7. Find the RxD pin. It is probably next to the TxD pin and will show no voltage.

If the steps are successfull you very likely have found your UART interface!

# Moving on
Now to find out if it really is an UART and to access the interface, you'll to connect via a serial console program. It's however not as easy as just attaching your RS232 adapter, because it operates at 5 Volts.  
Instead you'll either need a level shifter, or easier, a integrated device that does this for you.
I'm using a [bus pirate](http://dangerousprototypes.com/docs/Bus_Pirate), a inexpensive and really nifty device that is useful in a lot of other situations.  

Just connect the TxD, RxD and GND pins to the devices appropriate connectors. Again, you won't need VCC, so don't connect it.
To find out the baud rate, its easiest just to guess try. Fast devices will often use 115200 bauds, other than that 9600 and 38400 bauds are very common.

I've made a little sketch that shows you what this will look like on many devices.
The black dot would be a GND point, below the 2 drill holes.
<img src="//gstaedtner.net/images/sonstiges/uart.jpg" alt="UART" width="100%"/>
