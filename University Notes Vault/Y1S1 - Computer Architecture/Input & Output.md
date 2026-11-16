Computers do 2 things:

- Computation - Processing Data

- I/O - Exchanging Data with the real world

## Peripherals

Peripherals are components outside the computer's enclosure, they are typically used for allowing a human user to interface with the computer (ie, mouse, monitor, keyboard etc).

I/O takes up a lot of space on the mother board board.

## Busses

>[!Network Topologies]
>
>- Point-To-Point
>	- Pairwise connection between all nodes
>	- Needs lots of wires for lots of nodes
>- Mesh network
>	- E.g the Internet
>	- Pairwise connections between nodes
>	- nodes routing messages using addresses
>	- can get complicated and slow
>- Bus network
>	- Every node has equal access to the same hared bus
>	- Bus can be single or set of multiple wires
>
>Busses are a form of network topology. [[Network Topology]]

- Registers staging data to go in and out of CPU, Present in analytical engine as "ingress/egress axes"
	- MAR: Memory Address Register
		- Holds address of read/write to go on address line
	- MBR: Memory Buffer Register
		- Holds data to go on/retrieved from data line
	- Control Unit connects them temporarily to the bus, and adds the control line signal

Most CPU Pins are used by the Address and Data lines

### Address Line

- Width of address bus determines max possible memory capacity
- Can be same width as word length of CPU
	- e.g 32-bit address bus can address ${}2^{32}{}$ 
	- If these are 1 byte each then memory limit is ${}2^{32} bytes = 4GiB{}$
- But not always,
	- e.g 6502 is 8-bit, has a 16-bit address lines
	- 64 bit is huugeee(16EiB), so PC's don't use it at all

### Data Line

- Data lines provide a path for moving data among system modules
	- Often same width as CPU word length
- But nto always
	- e.g Motorola 68000: 32 bit words, 16 bit data line

### Control Lines

- Control Lines to control access to and use of the bus
	- e.g Control signal determines whether to read or write RAM
	- + Lines for negotiations for who gets to talk when.

### Bus Advantages

- Easy to add new devices: same set of shared wires
- low cost due to shared wires

### Bus Disadvantages

- Bottleneck: performance of the system limited by bus
- busy busses tend to sprout switches and evolve into mesh networks

### Bus Examples

#### Hierarchical Bus Architecture

- Bus can become bottleneck
	- Many devices attached and competing for access
	- Data transfer demand approaches capacity of bus
- Solution: MULTIPLE BUSES, laid out in a hierarchy
	- Secondary address spaces below the primary bus addresses

#### Desktop PC Bus Architecture

- Northbridge: FAST
	- Connects directly the the CPU
		- Via front side BUS (FSB)
	- RAM, PCIe, GPU
	- L2, L3 cache
- Southbridge: slower
	- All other I/O modules
	- Migrated onto single chip

- Both can be speed bottlenecks
	- Don't just look at CPU speed
	- Important for overclocking
	  
- Ongoing race between components wanting to move up the heirarchy vs levels going faster.

Nowadays Northbridge is on the CPU itself, Southbridge also moved lots of functionality onto the CPU

#### PCI express Bus

Peripheral Component Interconnect express
- General purpose for internal peripheral devices
	- Graphical, networking, sound, video
- 1 to 32 lane versions (1-bit each)
- Speed versions
	- 2Gb/s - 64Gb/s per lane
- Is not a bus!
	- Some routing of messages
	- sooo actually a mesh network!

#### Mass Storage Busses

>[!SCSI]
>- Very Ancient/classic from 1990s
>	- Pioneered moving logic and work from CPU into I/O module
>- Very reliable, more expensive
>	- Used today in servers, data centers
>- Originally a true bus
>- Latest update: SAS Serial Attached SCSI (Point to point + hhub)

>[!SATA]
>- Consumer system, fast serial

>[!NVMe]
>- Consumer machine standard
>- Connecting hard discs via PCIe bus

#### Midi Bus

Music Instrument Digital Interface
- Channel messages sent on only one of the 16 channels and monitored only by devices on channel
- system messages that all devices recieve
- e.g. channel, pitch, velocity, duration, params

Has managed to survive as a true bus.

#### Standardised I/O

>[!Old Days (1990's)]
>- Each device had its own I/O module
>- Which required its own IQR lines
>- and Required its own I/O level drivers
>- This was painful!!!
>- e.g. PCI sound cards

>[!Today]
>- Standard lower level bus has a single I/O moduke
>	- e.g. USB, FireWire etc
>- Which has a single IRQ
>- And a single I/O level driver
>	- High-level drivers talk to devices over this
>	- "Plug and Play"
>- e.g. USB sound card has no direct IRQ line to CPU

#### Universal Serial Bus (USB)

- Standard for connecting peripheral devices (1996)
	- Replaced a variety of earlier interfaces
		- Such as serial and parallel ports, as well as seperate power ports for portable devices
		- Protocol includes device ID and config info used to download device drivers automatically
		- nice features: IQR only needed for USB controller itself, not for devices hanging off it.
	- Not really a bus! Modern versions are point to point links w/ hubs
- Different versions/speeds:
	- USB1: 12 Mb/s - USB4: 80 Gb/s
- Manager/ worker protocol
	- Hence different connectors
	- On the go protocol turns workers into managers
- Standardisation has been difficult
	- Especially regarding Power

#### Parallel to Serial trend

Parallel busses evolve to meshes of fast serial point2points

- USB, SAS
- Small differences in delays on out of box parallel wires
	- Re-syncing is hard >16Gb/s
	- Faster to just have one wire and not have to re-sync errors
- the "even of a lifetime" for bus engineers (Xilinx)



## I/O Modules

>[!Storing to I/O]
>- Transmit commands to the module/ device
>	- Write assembly-like instructions specific to the module
>- Send data to the module/ device

>[!Loading from I/O]
>- Read data captured by moduke/ device
>- Read status information from the module/ device

>[!I/O modules vs device drivers]
>Are different
>
>- I/O modules are hardware connected tot he bus
>- A device Driver is a piece of software which takes sole responsibility for all communication with the I/O Module
>	- Wraps the loads and stores to the modules
>	- Provides higher level (e.g. C++. OS apps) API's
>	- See [[Y1S2 - Operating Systems]]

>[!Control and Timing]
>I/O modules must be able to co-ordinate the flow of data between the internal resources and external devices
>- Devices may be slow
>- So I/O modules manage them independent of the CPU
>- This allows the CPU to go and do other things at the same tme
>- Ongoing trend is moving more work to I/O modules
>	- This is a form of parallelism

>[!Data Buffering]
>- Transfer rate into and out of main memory or CPU is quite high
>- Rate is orders of mangitude lower for many peripheral devices and cover a wide range
>- Data coming from main memory are sent to an I/O module in a rapid burst
>- Data is buffered in the I/O module and then sent to peripheral devices at its data rate

>[!Error Detection]
>- Mechanical or electrical malfunctions reported by device (e.g. paper jam in a printer)
>- Communication errors - unintentional changes to bit pattern on wires from devices to I/O module
>- Handle or report errors o CPU



1. CPU asks I/O module to check status of device
2. I/O module returns device status
3. If device ready, CPU requests transfer of data
4. I/O module obtains a unit of data from device 
5. Data transferred from I/O module to CPU

>[!Delays]
>I/O is Sloowww
>- Waiting for things in the real world
>- We want CPU's to be busy doing other things
>
>Three common techniques to compensate:
>>[!Polling]
>>- CPU is executing a program and encounters an instruction relating to I/O operation
>>- CPU executes that instruction by issuing a command to appropriate I/O module
>>- I/O module performs requested action base on I/O command issued by CPU (R/W)
>>- I/O module sets appropriate bits ini I/O status register
>>- CPU periodically checks (polls) status of I/O module until it finds that operation is complete
>
>>[!Interrupt-driven I/O]
>>-Write a data handler routine
>>Set CPU IRQ register to it
>>CPU issues read command
>>I/O module gets data from peripheral whilst CPU does other work
>>I/O module interrupts CPU with IRQ
>>Data handler loop requests data
>>I/O module transfers data
>>CPU returns to previous task
>
>>[!Direct Memory Access]
>>- Requires DMA controller hardware on system bus
>>- In one instruction, CPU asks DMA to perform a large transfer between address ranges
>>- DMA manages comms and delays wiith the addresses
>>- DMA sends an IRQ to CPU when task is complete
>>- Relieves CPU to do other things
>>- Also used for RAM-RAM transfers e.g. split blitting

## I/O without modules

### Memory Mapped I/O

- Assigned dedicated specialist RAM to represent  devices (E.g Video RAM)
- Devices or interfaces read direct from this RAM themselves - from extra wires coming out of the back of this specialist RAM
- For Video RAM screen modes define representations used; addresses could represent:
	- ASCII Chars
	- RGB pixel colors
- For keyboard input RAM:
	- e.g. One address per key

### CPU I/O pins and instructions

- Dedicated pins, instructions and logic for I/O
- Frees up address space for more general memory
- e.g MOS 6510 (Commodore 64)
