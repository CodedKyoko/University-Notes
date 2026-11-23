## Memory Hierarchy

Trade off between speed of access and capacity

In order of *descending* speed of access, and *ascending* capacity.

- Primary (System)
	- Lives in bus address space
	- Directly accessible by the CPUaccesible
- Secondary (Online)
	- Spinning hard-drives; Solid State Drives
	- Data must first be transferred to Primary storage via I/O before CPU use
- Tertiary (Near-Line)
	- Recent robotic versions of offline storage, e.g. disc/ tape jukeboxes
- Off-Line
	- Connect to I/O via manual insertion, for backups or transportation
	- e.g. optical disc, flash drive, external SSD etc


## Big Numbers

SI Units

| Name  | Symbol | Value         |
| ----- | ------ | ------------- |
| kilo  | k      | ${}10^3{}$    |
| mega  | M      | ${}10^6{}$    |
| giga  | G      | ${}10^9{}$    |
| tera  | T      | ${}10^{12}$   |
| peta  | P      | ${}10^{16}{}$ |
| exa   | E      | ${}10^{18}{}$ |
| zetta | Z      | ${}10^{21}{}$ |
Base 2 Units

| Name | Symbol | Value          |
| ---- | ------ | -------------- |
| kibi | ki     | ${}2^{10}{}$   |
| mebi | Mi     | ${}2^{20}{}$   |
| gibi | Gi     | ${}2^{30}{}$   |
| tebi | Ti     | ${}2^{40}{}$   |
| pebi | Pi     | ${}2^{50}{}$   |
| exbi | Ei     | ${}2^{{60}}{}$ |
| zebi | Zi     | ${}2^{70}{}$   |
## Memory Adressing

Each Location has a numerical address; Single address space across RAM, ROM< I/O modules. Usually written in hex e.g. 0x72cf99e079b0; Each location holds on word

Would be cleanest to match 64 bit word length to CPU, but many current systems (e.g. x86., RISC-V) still use 8 bit (byte) memory words for historical compatibility. So one 64 bit load actually reads from eight numbered addresses.

## RAM

- Originally stood for "Random Access Memory"
	- Means equal speed to access any location in any order
- Modern RAM is misnamed to mean:
	- Primary - directly accessed by the CPU
	- Writeable by CPU - via store instructions
	- Volatile - state is lost when power removed

### SRAM

Static RAM

- Bits stored in transistors (flip flops)
- Fast (high speed switching)
- Retains state (data remanence)
- Complex Construction
- High cost (per bit)

Used for registers, cache, buffers in I/O devices, RAM in embedded systems

### DRAM

Dynamic RAM

- Bits stored as charge in capacitors
- Slower performance
- Discharges after sometime (charge leak), needs refreshing (dynamic)
- Structurally simple
- Low cost (per bit)

Used for bulk of PC memory, large memory units.

### ECC RAM

- For some applications we need high confidence in RAM error rates, e.g.
	- Servers
	- In memory databases
	- High value systems (goverment, finance)
	- Space computers
- ECC RAM has extra chips on the DIMM
	- Stores extra copies or checksums of the data
- Not commonly used as regular DRAM is so good.

### LP-DDR

- For use in phones and other mobile devices
- LP = Low power.
	- Run on reduced voltage, e.g. 1.8V
	- Refresh rate as function of temperature
	- Only refresh used regions
	- Deep sleep mode
	- Slower and smaller than regular DRAM
	- Many standard versions, current LP-DDR5

## Memory Controllers

- Individual RAM chips usually provide addresses from 0 - MAX.
- When we put lots on a module, they all have the same addreses
- Memory Controllers take system addresses as input, and maps them to adresses of one chip on one module.

## ROM

- Originally stood for "Read Only Memory"
- Modern ROMs are misnamed to mean:
	- Primary readable (CPU loads)
	- Non-volatile (persists during power off)
	- They are Random Access
	- They are usually writable
		- But not directly by the CPU
		- Used to store *firm*ware
			- BIOS

### MROM

Mask ROM; Contents programmed using photo lithography by manufacturers

### PROM

Programmable ROM: Empty of data when the chip is manufactured; can be programmed by the user. Once programmed the data cannot be erased

### EPROM

Erasable PROM: Like PROM only the chip can be removed from the computer and the program erased and another stored in its place using UV light

### EEPROM

Electrically ERPOM; Data can be erased using electricity

### Flash Memory

Just Flash Memory.

## Cache

Cache is a (relatively) small amount of Fast Memory placed between big slow memory and its consumer

- Stores fast copies of most heavily used memory content
- Checks if the required data is in cache
- Refer to main memory otherwise

Classic Examples:
- SRAM cache
- Between CPU and DRAM memory
- Hardware managed
But also occurs at all levels of memory hierarchy.

>[!Principle of Locality]
>
>Only a small amount of entire memory space is being accessed at any given time, and values in that space are being accessed repeatedly:
>- Temporal Locality: Same address repeated at nearby times
>- Sequential Locality: Address sequences re-accessed in same orders
>- Spatial Locality: Nearby addresses tend to be accessed together
>  
>Applies to both instructions and data (e.g. due to loops)
>So copy accessed values and their spatial and sequence neighbours from larger-slower to smaller-faster memory for a while.

- Cache memory is made of many cache lines:

| Tag   | Block                      | Dirty Bit |
| ----- | -------------------------- | --------- |
| $08F4 | 01101100 01101100 10011010 | 1         |
| $2AD5 | 10010101 11100110 00110110 | 0         |

- block of copies of several contiguous words from memory
- tag address or other ID describing which memory is copied
- dirty big logging whether the block data is modified

Hit/Miss: requested data is found/ not found

- Hit/Miss rate: Factor of time data is found/not found (max 1)
- Hit time: time required to access requested daa
- Miss penalty: time required to process a miss

Victim: cached data be thrown out to make room for new data

Has function: maps a big datum to a smaller one:

- e.g. Take last two hex digits: has(9A8E) = 8E
- e.g. Boolean AND all binary digits together: has(01101001) = 0
- It is not usually possible to recover originals from the hash

### Direct Caching Algorithm

Always read and/or store address and block starting 08f4 in line 1;

Advantages: easy, fast cheap.
Drawbacks: can't keep multiple in use addressed in cache if they share the same hash.

### Associative Caching Algorithm

Store 08f4 at any available line (un-used or under-used victim line)
Then use extra hardware (Content Addressable Memory) to parallel search for address tags to lookup

Advantages: can cache all best addresses at once
Drawbacks: Cost/complexity of CAM digital logic

### Hybrid Caching Algorithm

"Set Associative" - Hybrid of directy and associative architectures:
- Hash address to a subset of lines in cache memory
- Then use associative rules inside these subsets

### Cache Writes

- So far we've looked at cache reads
- But CPU also needs to write data quickly

- We can write to to cache in a similar way to reads.
- But unlike reads, we can't just throw written victim lines away
- Need to ensure they are written to main memory at some point
- Use *dirty bit* to track what has been updated:
	- Write-though: Copy to ram and unset dirty bit shortly after cache write (uses lots of bus bandwidth)
	- Write-back: Write the RAM only when victimized (slower at the time)

>[!Note]
>Modern machines are likely to have 3 levels of Cache (caching the cache) as you go up the levels, they get smaller and faster.
>L1 Cache is typically split into 2 by things like Instructions, vs Data


## Secondary Storage

>[!Historical]
>
>- Punched tape/ cards
>	- Jaquard Loom
>	- Analytical Engine
>	- IBM Hollerith Machines
>	- Colossus
>	- Used u to 1980s!
>- Discs

### HDD

- Capacity, performance, non volatile
- One or more rigid "hard" discs (platters), coated with magnetic material
- Magnetic heads, mounted on moving arm, to read and write  data to platter surface.
- Platter spins veryy fast

>[!Disc Data Layout]
>- Each surface is divided into a number of concentric tracks
>	- Each track has a number of Sectors
>		- Smallest unit of data transfer (e.g. 512 Byte)
>- Forms a secondary address space
>- Memory is *almost* random access
>	- Sectors can be accessed in any order
>	- But angular neihbours are faster
>	- and radial neighbors are slower
>- Fragmentation (Data being split across the disc) will slow access down.

### RAID

Redundant Array of Independent Discs

- Method to make hard discs more resilient to failure

- Use multiple discs as redundant backup and or speedup

- Various architectures including:
  
	- RAID1
		- Simple Backup of complete disc
	- RAID5
		- File striping allows access to many parts of a file A,B,C at the the same time
		- Distributed parity bits as checksums

### Solid State Drive (SSD)

- Solution to slow HDD: replace it with non-volatile flash ROM
- No moving components
	- Fast reliable robus
	- Low poer, silent
- Unlike primary memory ROM, as secondary storage
	- Connected via I//O
	- own internal address space

#### Virtual Memory

- space space/ page file - part of secondary storage used as virtual primary memory

- Physical primary memory then used as a cache over the larger virual address space

- Useful when not enough RAM to store the entire program and its data

- Memory controller architecture can provide hardware support for Operating systems managing this; see [[Y1S2 - Operating Systems]]

