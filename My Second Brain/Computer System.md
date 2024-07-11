---
aliases:
  - Computer
  - Computers
tags:
  - cs
  - os
Created: 2023-07-22T21:45:12+10:00
Modified: 2024-07-03T19:35:33+10:00
---
A Computer System is the combination of [[Hardware]], [[Software]], user and data.

## Computer System Structure 
Computer systems can be divided into four main components:
1. **Hardware**: These items provide basic computing resources, i.e. CPU, memory, [[Input & Output|I/O]] devices.
2. [[Operating Systems|Operating System]]: Controls the hardware and coordinates its use among the various application programs for the various users.
3. **Application Programs**: These items define the ways in which the system resources are used to solve users' computing problems, i.e. word processors, spreadsheets, compilers and web browsers
4. **Users**: People, machines or other computers

## Computer Startup
Bootstrap program is loaded at power-up or reboot. Typically stored in ROM or EPROM, generally known as firmware. It initialises all aspects of a system and loads operating system kernel and starts execution.

## Computer Organisation
- I/O devices and the CPU can execute concurrently.
- Each device controller is in charge of a particular device type and has a local buffer.
- The CPU moves data from/to the main memory to/from local buffers.
- I/O is from the device to the local buffer of a particular controller.
- The device controller informs the CPU that it has finished its operation by causing an [[Interrupts|Interrupt]].

## Direct Memory Access Structure 
Direct memory access (DMA) is a feature of computer systems that allows certain hardware subsystems to access main system memory independently of the CPU. It is commonly used for high speed [[Input & Output|I/O]] devices able to transmit information at close to memory speed (hard drives). Device controllers transfer blocks of data from buffer storage directly to main memory without CPU intervention. Only one interrupt is generated per block, rather than the one interrupt per byte.

# Storage Structure
**Main memory**: Only large storage media that the CPU can access directly 
- Random access
- Typically volatile
**Secondary storage**: Extension of main memory that provides large nonvolatile (permanent) storage capacity.
**Magnetic disks**: rigid metal or glass platters covered with magnetic recording material
- Disk surface is logically divided into tracks, which are subdivided into sectors 
- The disk controller determines the logical interaction between the device and the computer
**Solid-state disks (SSD)**: Faster than magnetic disks, nonvolatile
- Various technologies 
- Becoming more popular

## Storage Hierarchy 
![[Pasted image 20230725213627.png|centre|300]]
In this hierarchy all the storage devices are arranged according to speed, cost and volatility. The higher levels are expensive, but faster and as we move down, the cost per bit generally decreases, where all the access time generally increases.

### Caching
The cache is a smaller and faster memory that stores copies of the data from frequently used main memory locations. Caching is the term when coping information into a faster storage system. Main memory can be viewed as a cache for secondary storage.
![[Pasted image 20230725214142.png]]

