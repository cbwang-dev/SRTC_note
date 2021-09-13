0. summary
1. what is it?
	1. files without content, but linked to a device `/dev`
	2. two types of special files
		- block devices (where information is read/written in blocks)
			- disk, tapes
			- system provide caching system to reduce the access of disk
				- first write in buffer cache, then later goes into disk
		- character devices (devices which are not block devices)
			- printer, keyboard, sensors, actuators
			- no storage option, no use of buffer cache
2. what does it do? 
	1. it refers to device
3. how does it work? (use the concept of [[major number and minor number in UNIX]])
	1. It uses a major and a minor number. The major number is a reference for the software of the DD. So each DD has a major number. While the minor number is the reference for a device. Each device has a different minor number. So a DD may control multiple minor numbers or devices. 
	2. You have to know the device, thus the major and minor number. And THEN you can call the right routine by looking it up in the driver table. The device driver ( → major number) determines the row where you have to look.
4. where is it used?
	1. In drivers for contacting devices and by the system to contact driver software.
5. when is it used?
6. what are the potential problems? 
7. what are the pros and cons?
	1. pros: get security for free
	2. cons: complex
8. what are the possible alternatives?