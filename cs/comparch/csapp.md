# CSAPP

*Computer Systems: A Programmer's Perspective, 3/E (CS:APP3e) [link](https://csapp.cs.cmu.edu/)*

## CH1: Tour of Computer Systems

**1.6 Storage Devices Form a Hierarchy**

* Memory Hierarchy:
  * L0 (CPU Register): CPU registers holds words retrieved from cache memory
  * L1 cache (SRAM): holds cache lines retrieved from L2 cache
  * L2 cache (SRAM): holds cache lines retrieved from L3 cache
  * L3 cache (SRAM): holds cache lines retrieved from memory
  * L4 main memory (DRAM): holds disck blocks retrieved from local disks
  * L5 local secondary storage (local disks): holds files retreived from disks on remote network server
  * L6 remote secondary storage (distributed file systems, web servers)
* Storage devices in every computer system are organized in a memory hierarchy
  * Devcies become slower, larger, and cheaper per byte as it moves from top to bottom of the memory hierarchy
* Main lesson: storage at one level serves as a cache for storage at the next lower level which can be utilized to improve performance

**1.7 The operating system manages the hardware**

* Operating System (OS) can be viewed as a layer of software interposed between the application program and the hardware
* All software attempting to manipulate hardware (ex: printing message, accessing keyboard, etc) must do this through the OS
* Two primary purposes of OS:
  1. protect the hardware from misuse by software
  2. Provide software with simple and uniform mechanisms (API) for manipulating hardware that varies from system to system
* OS is able to fulfull its purpose by abstracting the hardware processor, main memory, and I/O devices with processes, virtual memory, and files (respectively)
  *  Note: Process is the representation of the combination of processor, main memory, and i/o devices


*Process*
* OS's abstraction for running a program, which may include the use of multiple abstractions such as virtual memory and files and allows programs to have (the illusion of) exclusive use of the hardware 
* Concurrently running processes is where multiple processes are (appear to be) executed at the same time 
* A single CPU can appaear to execute multiple processes concurrently by having the processor switch among the processors (via mechanism called context switching)
* Context: state the OS keeps track of inorder for processors to run
  * Context state information includes things like: current values of the PC, register file, and contents of the main memory
  * Context switching is done by the OS saving the context of the current process and restoring the context of the new process and passing control to it
* Kernel: portion of the OS that is always present in memory and is responsible for managing processes
  * when an app program requires some action by the OS (such as reading a file), it executes a system call instruction that transfers control to the kernel which performs the requested operation and then returns control back to the app 


*Threads*
* Threads are multiple execution units in a process that run the context of the process and share the same code and global data
* It is easier to share data between multiple threads than between multiple processes
* Threads are more efficient than processes

*Virtual Memory*
* an abstraction that provides each process with the illusion that it has exclusive use of the main memory
* Virtual address space: same uniform view of memory that each process has
  * Consists of things like space for kernel virtual memory and user stack, run-time heap, read/write data, region for shared libraries, etc
* Areas of virtual address space (bottom to top):
  * Program code and data 
  * Heap
  * Shared libraries
  * Stack
  * Kernel virtual memory

*Files*
* Sequence of bytes
* Every I/O device (disks, keyboards, displays, networks, etc) is modeled as a file
* All I/O is performed by reading and writing files with a a system known as Unix I/O
* File is a useful abstraction that gives uniform view of varied I/O devices

**Misc**

*Amdahl's law*
* States that the effect of speeding up one part of a system depends on how signifigant this part was and how much it sped up
* Speedup = 1/ (1-fractionOfComponentsSignifigance) + fractionOfComponentsSignfigance/factorOfImprovement = TimeBeforeChange/ TimeAterChange
* To signficantly speed up an entire system, a large fraction of the overall system's speed must be improved 
  * even if an improvement was made to a component to the point where it requires no time at all, speedup will not be that significant unless it makes up a large fraction of the overall system


## CH2: Representing and Manipulating Information

**2.1 Information Storage**

* 1 byte (8 bits) is the smallest addresable unit of memory computers use
* Virtual memtory - large array of bytes where each byte is identified by an address (an unique number)
  * Virtal address space - set of all possible addresses
  * Machine-lvel programs interacts with the virtual memory
  * virtual memory is an abstraction for a combination of dynamic random access memory (DRAM), flash memory, disk storage, etc that provides programs with the illusion of a monolithic byte array

**2.1.2 Data Sizes**

* Word size - size of pointer data
  * Virtaul address is encoded by word size
  * determined by max size of virtual address space
  * Older computers use to be 32bit word size...now they are 64bit word size
  * 32bit word size limits virtual address space to 4 GB (64bit word size leads to a virtaul address of 16 exabytes, or 1.85X10^19)

**2.1.3 Addressing and Byte Ordering**

* a multi-byte object is stored as contiguous sequence of bytes, with the address of the object given by the smallest address of the bytes used
  * so if `int x` has an address of `0x100` and ints take up 4 bytes of memory, then the memory locations of x will be 0x100, 0x101, 0x102, and 0x103
