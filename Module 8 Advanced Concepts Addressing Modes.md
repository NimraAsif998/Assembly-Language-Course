# Module 8: Advanced Concepts – Addressing Modes

## Introduction

In Assembly language, an **addressing mode** specifies how an instruction accesses its operands (data). In simple words, addressing modes tell the processor **where the required data is located**.

The 8086 microprocessor supports several addressing modes to access data efficiently.

---

# What is an Addressing Mode?

An addressing mode is a technique used by the CPU to determine the location of an operand.

For example, in the instruction:

```assembly
mov ax, bx
```

the processor knows that the source operand is stored in register `BX`.

Similarly, in:

```assembly
mov al, num
```

the processor accesses the value stored in memory location `num`.

---

# Types of Addressing Modes in 8086

The most commonly used addressing modes are:

1. Immediate Addressing Mode
2. Register Addressing Mode
3. Direct Addressing Mode
4. Register Indirect Addressing Mode
5. Indexed Addressing Mode
6. Based Addressing Mode
7. Based Indexed Addressing Mode

---

# 1. Immediate Addressing Mode

In Immediate Addressing Mode, the actual data (constant value) is directly specified in the instruction.

## Syntax

```assembly
MOV destination, constant
```

## Example

```assembly
mov al, 25
mov bx, 1000h
```

### Explanation

* `25` and `1000h` are immediate values.
* The processor directly loads these values into the registers.

---

# 2. Register Addressing Mode

In Register Addressing Mode, both source and destination operands are registers.

## Example

```assembly
mov ax, bx
add al, bl
```

### Explanation

* The data is transferred from one register to another.
* This addressing mode is very fast because registers are inside the CPU.

---

# 3. Direct Addressing Mode

In Direct Addressing Mode, the memory address of the operand is directly specified.

## Example

```assembly
.data
num db 10

.code
mov al, num
```

### Explanation

* `num` is a memory variable.
* The processor directly accesses the memory location of `num`.

---

# 4. Register Indirect Addressing Mode

In this addressing mode, a register contains the address of the operand.

Registers commonly used:

* `BX`
* `SI`
* `DI`

## Example

```assembly
.data
num db 20

.code
mov bx, offset num
mov al, [bx]
```

### Explanation

* `BX` stores the address of `num`.
* The instruction `mov al, [bx]` accesses the value stored at that address.

---

# 5. Indexed Addressing Mode

In Indexed Addressing Mode, index registers (`SI` or `DI`) are used to access data, especially arrays and strings.

## Example

```assembly
.data
arr db 10,20,30,40

.code
mov si, 2
mov al, arr[si]
```

### Explanation

* `SI` contains the index value.
* `arr[si]` accesses the third element of the array (`30`).

---

# 6. Based Addressing Mode

In Based Addressing Mode, base registers (`BX` or `BP`) are used to access memory.

## Example

```assembly
.data
num db 50

.code
mov bx, offset num
mov al, [bx]
```

### Explanation

* `BX` contains the base address.
* The value stored at that address is loaded into `AL`.

---

# 7. Based Indexed Addressing Mode

In this addressing mode, both a base register and an index register are used together.

## Example

```assembly
mov bx, offset arr
mov si, 2
mov al, [bx + si]
```

### Explanation

* `BX` contains the base address of the array.
* `SI` contains the index.
* The processor adds both values to determine the effective address.

---

# Complete Example

```assembly
.model small
.stack 100h

.data
    arr db 10,20,30,40

.code
main proc

    mov ax, @data
    mov ds, ax

    ; Immediate Addressing
    mov al, 5

    ; Register Addressing
    mov bl, al

    ; Direct Addressing
    mov al, arr

    ; Indexed Addressing
    mov si, 2
    mov al, arr[si]

    ; Program termination
    mov ah, 4Ch
    int 21h

main endp
end main
```

---

# Summary of Addressing Modes

| Addressing Mode   | Example           |
| ----------------- | ----------------- |
| Immediate         | `mov al, 5`       |
| Register          | `mov ax, bx`      |
| Direct            | `mov al, num`     |
| Register Indirect | `mov al, [bx]`    |
| Indexed           | `mov al, arr[si]` |
| Based             | `mov al, [bx]`    |
| Based Indexed     | `mov al, [bx+si]` |

---

**Addressing modes are one of the most important concepts in Assembly language because they determine how data is accessed and manipulated. Understanding addressing modes is essential for writing efficient and optimized Assembly programs.**
