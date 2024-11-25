# Producer-Consumer-Synchronization-Problem

This repository demonstrates solutions to process synchronization problems, focusing on the **Producer-Consumer Problem** and the **Critical Section Problem**. The implementation is written in C# and showcases both race condition scenarios and thread-safe solutions using mutex locks.

## Overview

Process synchronization is a critical aspect of operating systems where processes share data or resources. Improper synchronization can lead to **data inconsistency** and other issues. This repository provides examples and explanations of:

- **Producer-Consumer Problem**
- **Critical Section Problem**
- **Synchronization using Mutex Locks**

### Data Inconsistency
- Concurrent processes may lead to inconsistent data if access to shared resources is unsynchronized.
- The CPU scheduler rapidly switches between processes, increasing the risk of race conditions.

## Producer-Consumer Problem

The producer-consumer problem, also known as the bounded-buffer problem, involves two processes sharing a fixed-size buffer. The producer generates data and places it in the buffer, while the consumer removes data from the buffer.

### Challenges
- Ensuring the producer does not add data to a full buffer.
- Ensuring the consumer does not remove data from an empty buffer.

### Solutions Provided
1. **Without Synchronization**  
   Demonstrates race conditions and the issues caused by unsynchronized access to shared data.

2. **With Synchronization**  
   Uses a **mutex lock** to synchronize access to the shared resource, ensuring thread-safe operations.

## Critical Section Problem

A critical section is a portion of code where a process accesses shared resources. Proper synchronization is necessary to ensure:

- **Mutual Exclusion**: Only one process executes in its critical section at any time.
- **Progress**: If no process is in its critical section, other processes waiting for execution are not indefinitely delayed.
- **Bounded Waiting**: Processes do not wait indefinitely to enter their critical section.

## Code Description

### Without Synchronization
The `count` variable, shared between producer and consumer threads, is updated without synchronization, leading to potential race conditions.

### With Synchronization
A **mutex lock** is used to enforce mutual exclusion, ensuring consistent and thread-safe updates to the shared resource.

## Race Condition Illustration  

The following image demonstrates a race condition scenario where the producer and consumer threads access the shared resource (`count`) without synchronization:  

![image](https://github.com/user-attachments/assets/0da87eed-60d0-439b-8ad6-fe50c9c70276)


### Key Explanation:  
1. At `T0`, the producer reads `count` (initially `5`) into `register1`.
2. At `T2`, the consumer also reads `count` (`5`) into `register2`.
3. The producer increments `register1` to `6`, but before updating `count`, the consumer decrements `register2` to `4`.
4. Finally, at `T4` and `T5`, both threads write their respective values (`6` and `4`) back to `count`, overwriting each other's results.

This behavior demonstrates the need for synchronization to avoid such inconsistencies.

## Concepts Highlighted  

### Mutex Locks  
Mutex locks are Boolean variables that enforce mutual exclusion.  
- `Acquire()`: Ensures a thread gains exclusive access to the critical section.  
- `Release()`: Frees the lock after the critical section is executed.  

## Notes  
This repository is part of my studies on **Operating Systems** to understand and simulate process synchronization mechanisms.  

## Author  
Created by **Ziad Ghoraba** as part of studying **Operating Systems** concepts to simulate and understand process synchronization and critical sections.  
