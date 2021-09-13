 There are two ways to communicate with the devices: Directly from the application. High level languages that allow I/O communication or languages that allow assembly language. Or by system calls, hereby using the OS interface. (device driver is part of the OS).

There are two general methods. One with a bus for the memory and for the devices (port mapped) and one with a bus for both (memory mapped). This will be important for the naming.

Then you have 2 communication modes with the input/output of the devices. The first is interupt driven and has three submodes. You can either use DMA which is something between the device driver and the device. You can use a channel which is a DMA but then extended, it sort of has its own processor. The second option is to use status info driven communication. Here you just check the status of the devices to see whether data is available. A last option is just to use no DMA but to communicate directly with the device driver by means of asynchronous events or interrupts.

End information: In order to know when a device has finished the request of the driver a driver can start polling or the device can send an interrupt. Knowing which device caused the interrupt can be done by an interrupt vector (vector of addresses with interrupt routines), polling (checking every device and asking who did it) or status info (general interrupt routine is called, in status info it can be seen which device did it).

You also have one level and two level drivers.In the one level driver it’s simple there’s direct communication with the device. In the two level driver there’s an upper level that accepts requests from the OS and the lower level actually sends the commands. If the lower level tells the upper level that the device is still busy than the upper level puts the request in a queue. There might be priority scheduling in the upper level if a queue arises.

Second attempt:

Okay softwarewise: there are two ways. By means of systems calls, using the OS as an interface. Or by directly communicating from the language (the OS needs to allow this) with the I/O devices.

Sending data to the device can be done by the devices registers or by using DMA. In this case the cpu tells the device where it should start reading and how much it should read. 

Sending commands can be done by the command register or by a channel. In the case of a channel a program is uploaded to the DMA and this is read out by the intelligent device.

When the device is done executing it creates an interrupt. The device driver saves its state and starts looking what device caused the interrupt. Can be done by an interrupt vector with adresses, by status info or by polling. The driver recovers its state and continues.