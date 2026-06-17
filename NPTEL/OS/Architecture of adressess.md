========================================
PC HARDWARE ARCHITECTURE - MEMORY NOTES
========================================

BIG IDEA:
CPU talks to everything using ADDRESSES.

Think of a city.

- RAM has addresses.
- Keyboard has addresses.
- Hard disk has addresses.
- Graphics card has addresses.

CPU sends a message to an address.

If the address belongs to a device:
    -> Device responds.

If the address does not belong to a device:
    -> Device ignores it.

Remember:
"Address decides who listens."


========================================
3 TYPES OF ADDRESSING
========================================

1. MEMORY ADDRESSING

CPU talks to RAM.

Think:
House Address -> House Responds

Address = Memory Location


----------------------------------------

2. I/O ADDRESSING

Devices have their own separate address space.

Think:
A separate market outside the city.

CPU uses special instructions to access it.

Advantages:
- Simple
- Compatible with old hardware

Problem:
- Very limited space (64 KB)


----------------------------------------

3. MEMORY-MAPPED I/O (MMIO)

Most important concept.

Devices are placed inside memory space.

CPU thinks:
"I'm talking to memory."

Reality:
"It's actually a device."

Think:
Shop inside a house.

CPU writes to memory address.
Device reacts.

Remember:

I/O Addressing
=
Separate world

Memory-Mapped I/O
=
Everything looks like memory


========================================
MEMORY LAYOUT STORY
========================================

Imagine a building.

Ground Floor
0 - 640 KB
=
Base Memory

Old programs lived here.


----------------------------------------

First Floor
640 - 768 KB
=
VGA / Video Memory

Screen lives here.

Remember:

VGA = Vision


----------------------------------------

Second Floor
768 - 960 KB
=
Expansion ROMs

Old hardware firmware.


----------------------------------------

Top Floor
960 KB - 1 MB
=
BIOS

The computer's starter.

Remember:

BIOS wakes up the computer.


----------------------------------------

Above 1 MB
=
Extended Memory

Modern applications live here.

Stack
Heap
Code
Programs

Everything important today.


========================================
PLUG AND PLAY
========================================

Think of a hotel receptionist.

A new device arrives.

BIOS says:

"Welcome.
Here is your address.
You can stay here."

Device automatically gets configured.

Remember:

Plug in.
Power on.
Works.


========================================
SYSTEM HIERARCHY
========================================

CPU is the Boss.

North Bridge = Fast Manager

Handles:
- RAM
- Fast devices

Remember:

North = Fast


----------------------------------------

South Bridge = Slow Manager

Handles:
- Keyboard
- Mouse
- Legacy devices

Remember:

South = Slow


========================================
PROCESSOR EVOLUTION
========================================

8088
=
1 MB

Small house.


----------------------------------------

80386
=
4 GB

Big apartment.


----------------------------------------

64-bit Processors
=
Huge city

Massive memory space.


========================================
EXAM MEMORY CHAIN
========================================

CPU -> Address

Address Match?
    YES -> Respond
    NO  -> Ignore

Memory Addressing -> RAM

I/O Addressing -> Separate Device Space

Memory-Mapped I/O -> Device Acts Like Memory

North Bridge -> Fast

South Bridge -> Slow

8088 -> 1 MB

80386 -> 4 GB

64-bit -> Huge Memory


========================================
30-SECOND REVISION
========================================

CPU talks using addresses.

Only matching devices respond.

Three methods:
- Memory Addressing
- I/O Addressing
- Memory-Mapped I/O

MMIO = Devices behave like memory.

Memory Map:
Base -> VGA -> BIOS -> Extended

North = Fast
South = Slow

8088 = 1 MB
80386 = 4 GB
64-bit = Huge

ONE GOLDEN SENTENCE:

"The CPU controls memory and devices through addresses; devices may use a separate I/O space or appear as memory through Memory-Mapped I/O."
========================================