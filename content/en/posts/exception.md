---
title: "Exceptional Control Flow"
date: 2025-03-18T01:22:29+08:00
draft: false
description: "An overview of exceptional control flow mechanisms, covering exceptions, interrupts, traps, system calls, faults, and aborts."
tags: ["Exception", "Interrupt", "Trap", "System Call", "Fault", "Abort"]
categories: ["Exception and Interrupts"]
---

# Exceptional Control Flow

## Control Flow

Processors do only one thing：

From startup to shutdown, each CPU core simply reads and executes(interprets) a sequence of instructions, one at a time *

## Altering the Control Flow

- Jumps and branches
- Call and return

## Insufficient for a useful system: Difficult to react to changes in system state

- Data arrives from a disk or a network adapter
- Instruction divides by zero
- User hits Ctrl-C at the keyboard
- System timer expires

> System needs mechanisms for “exceptional control flow”

## Exceptions

An exception is a transfer of control to the OS kernel in response
to some event (i.e., change in processor state)

- Kernel is the memory-resident part of the OS
- Examples of events: Divide by 0, arithmetic overflow, page fault, I/O request completes, typing Ctrl-C

![image-20250317194307702](https://naasi.oss-cn-shanghai.aliyuncs.com/image-20250317194307702.png)

## Exception Tables

![image-20250317194209075](https://naasi.oss-cn-shanghai.aliyuncs.com/image-20250317194209075.png)

- Each type of event has a unique exception number k
- k = index into exception table (a.k.a. interrupt vector)
- Handler k is called each time exception k occurs

**At system boot time** (when the computer is reset or powered on), the operating system allocates and **initializes a jump table** called an exception table, so that entry k contains the address of the handler for exception k. The exception number is an index into the exceptiontable, whose starting address is contained in a special CPU register called the exception **table base register.**

## Taxonomy of Hardware ECF

![image-20250317195112056](https://naasi.oss-cn-shanghai.aliyuncs.com/image-20250317195112056.png)

## Asynchronous Exceptions (Interrupts)

### Caused by events external to the processor

- Indicated by setting the processor’s interrupt pin
- Handler returns to “next” instruction

### Examples

- Timer interrupt ：Every few ms, an external timer chip triggers an interrupt，Used by the kernel to take back control from user programs
- I/O interrupt from external device ：Hitting Ctrl-C at the keyboard、Arrival of a packet from a network、Arrival of data from a disk.

## Synchronous Exceptions

Caused by events that occur as a result of executing an instruction:
### Traps
- Intentional, set program up to “trip the trap” and do something
- Examples: system calls, gdb breakpoints
- Returns control to “next” instruction

### Faults
- Unintentional but possibly recoverable
- Examples: page faults (recoverable), protection faults (unrecoverable), floating point exceptions
- Either re-executes faulting (“current”) instruction or aborts

### Aborts
- Unintentional and unrecoverable
- Examples: illegal instruction, parity error, machine check
- Aborts current program

## System Calls

Each x86-64 system call has a unique ID number

![image-20250318010540380](https://naasi.oss-cn-shanghai.aliyuncs.com/image-20250318010540380.png)

## Example

### System Call Example: Opening File

![image-20250318011150096](https://naasi.oss-cn-shanghai.aliyuncs.com/image-20250318011150096.png)

Almost like a function call

- Transfer of control
- On return, executes next instruction
- Passes arguments using calling convention
- Gets result in %rax

One Important exception!

- Executed by Kernel
- Different set of privileges
- And other differences: E.g., “address” of “function” is in %rax、Uses errno、Etc.

### Fault Example: Page Fault

![image-20250318011229265](https://naasi.oss-cn-shanghai.aliyuncs.com/image-20250318011229265.png)

### Fault Example: Invalid Memory Reference

![image-20250318011250386](https://naasi.oss-cn-shanghai.aliyuncs.com/image-20250318011250386.png)

## Classes of Exceptions

| Class     | Cause                         | Async/sync | Return behavior                     |
| --------- | ----------------------------- | ---------- | ----------------------------------- |
| Interrupt | Signal from I/O device        | Async      | Always returns to next instruction  |
| Trap      | Intentional exception         | Sync       | Always returns to next instruction  |
| Fault     | Potentially recoverable error | Sync       | Might return to current instruction |
| Abort     | Nonrecoverable error          | Sync       | Never returns                       |

![image-20250318011704471](https://naasi.oss-cn-shanghai.aliyuncs.com/image-20250318011704471.png)

![image-20250318011725837](https://naasi.oss-cn-shanghai.aliyuncs.com/image-20250318011725837.png)

