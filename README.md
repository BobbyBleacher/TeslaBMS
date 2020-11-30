forked from BobbyBleacher.  In order to compile you will need the following libraries which I downloaded from Collin's repository:

due_can.h
due_wire.h
Wire_EEPROM.h
MemoryFree.h

Planned changes include serial communication with an Electric Imp for internet connectivity and browser display of data.

My take on Collin's BMS. Changes listed below:

- Now balances to the lowest cell between two packs connected together in series.
- CSV output for those that might use it.
- Cells balance for 30s and then update again, turning the balancers off momentarily to get accurate readings.
- Baud set 612500 (I have older Tesla packs)
 
Known Bugs:

- System hangs once a day and must be restarted. Reason unknown.


Arduino compatible project to interface with the BMS slave 
board on Tesla Model S modules.

The modules are daisy-chained together with a TTL interface.
The interface uses a Molex 15-97-5101 connector and runs at
612500 baud. This can be a difficult baud rate to match with
arduino compatible processors. The Arduino Due and Teensy
3.5/3.6 boards are confirmed to be able to generate a suitably
close baud rate. The factory wiring to each module is comprised
of two sets of 5 differently colored wires:

* Red = 5V input to the module
* Green = Gnd for power and signal
* Gray = Fault output
* Yellow = UART Wire
* Blue = UART Wire

The fault output is active low. Use your own pull up to the fault line and if the line is pulled low then a fault has occurred.

Here is a PDF that explains how the wiring between modules and the master board is supposed to be:
https://cdn.hackaday.io/files/10098432032832/wiring.pdf
