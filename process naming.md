direct naming and indirect naming  
symmetrical naming and asymmetrical naming

---

- direct naming and indirect naming
	- direct naming:  process that sends to a specific process
		- `send <message> to <process_name>`
	- indirect naming: process that sends to an intermediate entity (port, channel, mailbox)
		- `send <message> to <mailbox>` or `send <message> to <interface_name>`
		- more general than direct naming
			- a process can receive from multiple mailboxes without sender is aware of this
			- a mailbox is an interface of a program
		- further possibilities
			- multiple-to-one sending model (client-server model)
				- can be done with direct naming
			- one-to-multiple sending model (broadcast)
- symmetrical naming and asymmetrical naming
	- symmetrical naming: receive message from a designated process
		- `send <message> to <process_name>` + `wait <message> from <process_name>`
	- asymmetrical naming: receive message from anybody
		- `wait <message>`