
# Module 2: Computer Architecture Basics

##  Course Overview
This module covers the fundamental concepts of computer architecture, focusing on how processors work at the hardware level. Students will understand CPU design, memory organization, and how components communicate through buses.

---

## 📖 Table of Contents
1. [CPU Architecture](#cpu-architecture)
2. [Registers](#registers)
3. [Memory Organization](#memory-organization)
4. [Data Bus, Address Bus, and Control Bus](#buses)
5. [Practical Examples](#practical-examples)
6. [Summary](#summary)

---

## CPU Architecture

### What is a CPU?
The **CPU (Central Processing Unit)** is the brain of the computer. It:
- Executes instructions from memory
- Processes and manipulates data
- Controls all other components of the system

### Basic CPU Structure

```
┌─────────────────────────────────────────┐
│          CPU Architecture               │
├─────────────────────────────────────────┤
│  ┌──────────────┐  ┌──────────────┐    │
│  │  Control     │  │   ALU        │    │
│  │  Unit        │  │ (Arithmetic  │    │
│  │  (CU)        │  │  Logic Unit) │    │
│  └──────────────┘  └──────────────┘    │
│         │                  │             │
│  ┌──────────────────────────────────┐  │
│  │      Registers (Fast Memory)     │  │
│  ├──────────────────────────────────┤  │
│  │ EAX, EBX, ECX, EDX, ESP, etc.   │  │
│  └──────────────────────────────────┘  │
│         │                               │
│  ┌──────────────────────────────────┐  │
│  │  Buses (Data, Address, Control)  │  │
│  └──────────────────────────────────┘  │
└─────────────────────────────────────────┘
```

### Key CPU Components

| Component | Function |
|-----------|----------|
| **Control Unit (CU)** | Decodes instructions and controls the execution flow |
| **ALU** | Performs arithmetic (+, -, *, /) and logical (AND, OR, NOT) operations |
| **Registers** | Ultra-fast temporary storage within the CPU |
| **Cache** | High-speed memory located close to the CPU (L1, L2, L3) |

### CPU Execution Cycle
The CPU follows a **Fetch-Decode-Execute** cycle:

```
1. FETCH   → Retrieve instruction from memory
           ↓
2. DECODE  → Interpret the instruction
           ↓
3. EXECUTE → Perform the operation
           ↓
4. STORE   → Save the result back to memory/register
```

---

## Registers

### What are Registers?
**Registers** are the fastest storage locations in the CPU. They hold data that the CPU is actively working on. Modern CPUs have different register sizes:

- **8-bit**: AL, BL, CL, DL (parts of larger registers)
- **16-bit**: AX, BX, CX, DX, SI, DI, BP, SP
- **32-bit**: EAX, EBX, ECX, EDX, ESI, EDI, EBP, ESP
- **64-bit**: RAX, RBX, RCX, RDX, RSI, RDI, RBP, RSP

### x86/x64 General Purpose Registers

```
64-bit (x64)          32-bit (x86)
┌──────────────────┐  ┌──────────────────┐
│ RAX              │  │ EAX              │
│ RBX              │  │ EBX              │
│ RCX              │  │ ECX              │
│ RDX              │  │ EDX              │
│ RSI              │  │ ESI              │
│ RDI              │  │ EDI              │
│ RBP              │  │ EBP              │
│ RSP              │  │ ESP              │
└──────────────────┘  └──────────────────┘
```

### Register Details and Purpose

| Register | Purpose | Common Use |
|----------|---------|-----------|
| **RAX/EAX** | Accumulator | Return values, main calculations |
| **RBX/EBX** | Base Register | Base address for data structures |
| **RCX/ECX** | Counter Register | Loop counters, repeat operations |
| **RDX/EDX** | Data Register | I/O operations, division remainder |
| **RSI/ESI** | Source Index | String operations, source pointer |
| **RDI/EDI** | Destination Index | String operations, destination pointer |
| **RBP/EBP** | Base Pointer | Stack frame management |
| **RSP/ESP** | Stack Pointer | Top of the stack |

### Special Purpose Registers

#### Instruction Pointer (IP/RIP)
```
Contains the memory address of the next instruction to execute
Examples: EIP (32-bit), RIP (64-bit)
```

#### Flags Register (EFLAGS/RFLAGS)
```
Stores status flags from the last operation:

Zero Flag (ZF)      → Set if result is zero
Carry Flag (CF)     → Set if overflow occurred
Sign Flag (SF)      → Set if result is negative
Overflow Flag (OF)  → Set if signed overflow
Parity Flag (PF)    → Set if even number of 1-bits
```

### Assembly Examples with Registers

```asm
; Example 1: Basic arithmetic
mov eax, 10         ; Move 10 into EAX
mov ebx, 5          ; Move 5 into EBX
add eax, ebx        ; EAX = EAX + EBX (result: 15)

; Example 2: Loop with ECX
mov ecx, 5          ; Set loop counter to 5
loop_start:
    ; do something
    dec ecx          ; Decrement counter
    jnz loop_start   ; Jump if not zero

; Example 3: Working with memory addresses
mov esi, offset array   ; Load array address into ESI
mov al, [esi]          ; Load first byte of array
mov ah, [esi + 1]      ; Load second byte
```

---

## Memory Organization

### Memory Layout

```
┌─────────────────────────────────────────┐
│   Highest Memory Address (0xFFFFFFFF)   │
├─────────────────────────────────────────┤
│                                         │
│        STACK (grows downward)           │
│   (Local variables, return addresses)   │
│                                         │
├─────────────────────────────────────────┤
│                                         │
│        HEAP (grows upward)              │
│   (Dynamic memory allocation)           │
│                                         │
├─────────────────────────────────────────┤
│                                         │
│   DATA SEGMENT (.data, .bss)           │
│   (Global and static variables)         │
│                                         │
├─────────────────────────────────────────┤
│                                         │
│   CODE SEGMENT (.text)                  │
│   (Program instructions)                │
│                                         │
├─────────────────────────────────────────┤
│   Lowest Memory Address (0x00000000)    │
└─────────────────────────────────────────┘
```

### Memory Segments Explained

#### 1. Code Segment (.text)
Contains all executable instructions of the program.

```asm
section .text
    global _start
    _start:
        mov eax, 1
        mov ebx, 0
        int 0x80        ; System call
```

#### 2. Data Segment (.data)
Contains initialized global and static variables.

```asm
section .data
    counter dd 0        ; 4-byte integer, initialized to 0
    message db "Hello", 0   ; String with null terminator
    pi dd 3.14          ; Floating point number
```

#### 3. BSS Segment (.bss)
Contains uninitialized global and static variables. These consume no space in the executable file.

```asm
section .bss
    buffer resb 1024    ; Reserve 1024 bytes
    array resd 100      ; Reserve 100 4-byte integers
```

#### 4. Stack
**LIFO (Last In First Out)** data structure used for:
- Function parameters
- Local variables
- Return addresses
- Automatic storage

```
Stack Operations:

PUSH (add to top):      PUSH EAX   →  Stack grows downward
PUSH EBX               →
PUSH ECX               →

POP (remove from top):  POP ECX    →  ECX = top of stack
POP EBX                →  EBX = second item
POP EAX                →  EAX = third item (last one pushed)
```

#### 5. Heap
Used for dynamic memory allocation at runtime. Memory is allocated on demand.

```asm
; Heap allocation (varies by OS/language)
; malloc() in C
; new in C++
```

### Memory Addressing Modes

```asm
; 1. Direct Addressing
mov eax, [0x1000]           ; Access memory at address 0x1000

; 2. Register Indirect
mov esi, offset array       ; ESI holds array address
mov eax, [esi]              ; Access first element

; 3. Indexed Addressing
mov eax, [esi + 4]          ; Access element at offset 4

; 4. Based Indexed Addressing
mov eax, [ebx + esi + 8]    ; Combination of base and index
```

---

## Buses

The **Bus** is a communication pathway that connects CPU, Memory, and I/O devices. There are three main types:

### 1. Data Bus (Data Transfer)

**Purpose**: Transfer actual data between CPU and Memory/IO devices

**Characteristics**:
- **Width**: Determines how much data can be transferred simultaneously
  - 8-bit bus: 1 byte per cycle
  - 16-bit bus: 2 bytes per cycle
  - 32-bit bus: 4 bytes per cycle
  - 64-bit bus: 8 bytes per cycle
- **Bidirectional**: Data flows both directions (read/write)

```
CPU ← → Memory
  ↑
  └─ Data Bus (32 or 64 wires)
```

**Assembly Example**:
```asm
mov eax, [0x1000]       ; Read 4 bytes from address 0x1000
                        ; Data Bus transfers data to EAX

mov [0x2000], ebx       ; Write 4 bytes from EBX to address 0x2000
                        ; Data Bus transfers data from CPU to Memory
```

### 2. Address Bus (Location Selection)

**Purpose**: Specify which memory location to access

**Characteristics**:
- **Unidirectional**: Always from CPU to Memory/IO
- **Width determines addressable memory**:
  - 16-bit address bus: 2^16 = 64 KB
  - 20-bit address bus: 2^20 = 1 MB
  - 32-bit address bus: 2^32 = 4 GB
  - 64-bit address bus: 2^64 = 16 EB (exabytes)

```
CPU → Memory
  ↑
  └─ Address Bus (32 or 64 wires)
     Carries address of memory location to access
```

**Memory Addressing Example**:
```asm
; 32-bit address bus can access:
; Addresses from 0x00000000 to 0xFFFFFFFF

mov eax, [0x1000]       ; Address bus carries 0x1000
mov ebx, [0xFFFFFFFF]   ; Address bus carries 0xFFFFFFFF
```

### 3. Control Bus (Signals and Commands)

**Purpose**: Carry control signals to coordinate and manage data transfers

**Control Signals**:

| Signal | Function | Active When |
|--------|----------|------------|
| **Read (RD)** | Instruct memory to output data | Reading from memory |
| **Write (WR)** | Instruct memory to store data | Writing to memory |
| **Clock (CLK)** | Synchronize all operations | Every clock cycle |
| **Reset** | Initialize CPU to known state | On power-up/reset |
| **Interrupt (INT)** | Pause execution for urgent task | External event occurs |
| **Memory Enable (ME)** | Enable/disable memory access | Need to access memory |

```
CPU → Components
  ↑
  └─ Control Bus (multiple signal lines)
     Carries control signals
```

### Bus Operation: Read Cycle

```
Timeline of a Memory Read Operation:

Clock:   ┌───┐   ┌───┐   ┌───┐   ┌───┐
         │   │   │   │   │   │   │   │
    ─────┘   └───┘   └───┘   └───┘   └─────

Address: ┌────────────────────────┐
    ─────┤ 0x1000                 │─────────
         └────────────────────────┘

RD:      ┌─────────────────────────┐
    ─────┤ (LOW = Read Active)     │───────── (LOW = Read)
         └─────────────────────────┘

Data:                    ┌────────────────┐
    ────────────────────┤ 0x12345678     │────── (Value retrieved)
                        └────────────────┘
```

### Bus Operation: Write Cycle

```
Timeline of a Memory Write Operation:

Clock:   ┌───┐   ┌───┐   ┌───┐   ┌───┐
         │   │   │   │   │   │   │   │
    ─────┘   └───┘   └───┘   └───┘   └─────

Address: ┌────────────────────────┐
    ─────┤ 0x2000                 │─────────
         └────────────────────────┘

WR:      ┌──────────────────────────┐
    ─────┤ (LOW = Write Active)     │─────── (LOW = Write)
         └──────────────────────────┘

Data:    ┌────────────────────────┐
    ─────┤ 0xABCDEF00              │─────────
         └────────────────────────┘
```

---

## Practical Examples

### Example 1: Adding Two Numbers

This program demonstrates register usage and basic arithmetic.

```asm
section .data
    num1 dd 15              ; First number
    num2 dd 25              ; Second number

section .bss
    result resd 1           ; Storage for result

section .text
    global _start

    _start:
        ; Load num1 into EAX (Address Bus carries address, Data Bus carries value)
        mov eax, [num1]     
        
        ; Load num2 into EBX
        mov ebx, [num2]     
        
        ; Add them together (ALU operation)
        add eax, ebx        ; EAX now contains 40 (15 + 25)
        
        ; Store result in memory
        mov [result], eax   
        
        ; Exit program
        mov eax, 1          ; sys_exit syscall
        mov ebx, 0          ; exit code 0
        int 0x80            ; Make syscall
```

**Analysis**:
- **Line `mov eax, [num1]`**: Address Bus sends address of num1, Data Bus returns its value (15)
- **Line `add eax, ebx`**: ALU performs: 15 + 25 = 40
- **Line `mov [result], eax`**: Address Bus sends result's address, Data Bus sends value (40)

### Example 2: Array Iteration and Sum

This program demonstrates loop control with registers and indexed memory access.

```asm
section .data
    numbers db 10, 20, 30, 40, 50   ; Array of 5 numbers
    array_size equ 5                 ; Array size constant

section .bss
    sum resd 1                       ; Storage for sum

section .text
    global _start

    _start:
        xor eax, eax                ; EAX = 0 (accumulator for sum)
        lea esi, [numbers]          ; ESI = address of array
        mov ecx, array_size         ; ECX = loop counter (5)
        
    loop_start:
        movzx ebx, byte [esi]       ; Load one byte from array
        add eax, ebx                ; Add to sum
        inc esi                     ; Move to next element
        dec ecx                     ; Decrement counter
        jnz loop_start              ; Jump if counter ≠ 0
        
        ; Store result
        mov [sum], eax              ; sum = 10+20+30+40+50 = 150
        
        ; Exit
        mov eax, 1
        mov ebx, 0
        int 0x80
```

**Register Usage**:
- **EAX**: Accumulator (holds running sum)
- **ESI**: Source Index (points to current array element)
- **ECX**: Counter (counts iterations)
- **EBX**: Temporary storage (holds current element)

### Example 3: Using Stack

This demonstrates stack operations for storing values.

```asm
section .text
    global _start

    _start:
        mov eax, 10         ; EAX = 10
        mov ebx, 20         ; EBX = 20
        mov ecx, 30         ; ECX = 30
        
        ; Push values onto stack
        push eax            ; Stack: [10]
        push ebx            ; Stack: [10, 20]
        push ecx            ; Stack: [10, 20, 30]
        
        ; Pop values back (LIFO order)
        pop eax             ; EAX = 30 (last pushed)
        pop ebx             ; EBX = 20
        pop ecx             ; ECX = 10 (first pushed)
        
        ; Exit
        mov eax, 1
        mov ebx, 0
        int 0x80
```

---

## Summary

### Key Concepts

| Concept | Key Points |
|---------|-----------|
| **CPU Architecture** | Brain of computer; contains CU, ALU, Registers, Cache |
| **Registers** | Fastest storage; EAX, EBX, ECX, EDX, ESI, EDI, EBP, ESP |
| **Memory Segments** | Code, Data, BSS, Heap, Stack |
| **Addressing Modes** | Direct, Indirect, Indexed, Based Indexed |
| **Data Bus** | Transfers actual data; bidirectional |
| **Address Bus** | Specifies memory location; unidirectional |
| **Control Bus** | Sends control signals; Read, Write, Clock, Reset, etc. |

### Learning Objectives Checklist

-  Understand CPU architecture and main components
-  Learn purpose and usage of all general-purpose registers
-  Understand memory organization (segments and layout)
-  Comprehend addressing modes for memory access
-  Know the role of three bus types
-  Apply concepts in assembly language programs
-  Understand Fetch-Decode-Execute cycle
-  Work with stack and heap operations

---

## 🎓 Practice Questions

1. **What is the difference between registers and memory?**

2. **Why do we need different addressing modes?**
 
3. **How many different addresses can a 32-bit address bus handle?**
  
4. **What is LIFO and why is it important for the stack?**
 
5. **What happens during a memory write operation?**
   

---





 
**Written by**:Nimra Asif  
**Course**: Assembly Language Programming - Module 2
