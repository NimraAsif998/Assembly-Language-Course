# Module 6.1: Flag Registers

## Introduction

The **Flag Register** is a special register in the **8086 microprocessor** that stores information about the current state of the processor and the result of arithmetic and logical operations.

Whenever an instruction is executed, some flags are automatically updated. These flags help the processor make decisions and control the flow of a program.

The 8086 Flag Register consists of **16 bits**, out of which **9 bits are active flags**.

---

## Types of Flags in 8086

The flags in 8086 are divided into two categories:

1. **Status Flags**
2. **Control Flags**

---

## 1. Status Flags

Status flags indicate the result of arithmetic and logical operations.

### a) Carry Flag (CF)

The **Carry Flag** is set when an arithmetic operation generates a carry or borrow.

### Example

```assembly id="d5iwgk"
mov al, 255
add al, 1
```

After execution:

```text id="ewh0zs"
AL = 00h
CF = 1
```

This happens because adding `255 + 1` produces a carry.

---

### b) Zero Flag (ZF)

The **Zero Flag** is set when the result of an operation is zero.

### Example

```assembly id="igkgc7"
mov al, 5
sub al, 5
```

After execution:

```text id="9ntk3d"
AL = 0
ZF = 1
```

---

### c) Sign Flag (SF)

The **Sign Flag** indicates whether the result is positive or negative.

* `SF = 0` → Positive result
* `SF = 1` → Negative result

### Example

```assembly id="6vk4he"
mov al, 5
sub al, 10
```

Since the result is negative, the Sign Flag becomes set.

---

### d) Overflow Flag (OF)

The **Overflow Flag** is set when the result of a signed operation exceeds the capacity of the destination register.

### Example

```assembly id="m5jlwm"
mov al, 127
add al, 1
```

The result cannot be represented in an 8-bit signed number, so:

```text id="nyjlwq"
OF = 1
```

---

### e) Parity Flag (PF)

The **Parity Flag** is set if the result contains an even number of 1's.

* Even number of 1's → `PF = 1`
* Odd number of 1's → `PF = 0`

### Example

```assembly id="8pw2z0"
mov al, 3      ; Binary: 00000011
```

Since there are two 1's (even parity):

```text id="jvhvcz"
PF = 1
```

---

### f) Auxiliary Carry Flag (AF)

The **Auxiliary Carry Flag** is set when a carry is generated from bit 3 to bit 4 during arithmetic operations.

This flag is mainly used in **BCD (Binary Coded Decimal)** operations.

---

## 2. Control Flags

Control flags control the operation of the processor.

### a) Direction Flag (DF)

The **Direction Flag** controls the direction of string operations.

* `DF = 0` → Process strings from left to right.
* `DF = 1` → Process strings from right to left.

### Example

```assembly id="0u0w7w"
cld     ; Clear Direction Flag
std     ; Set Direction Flag
```

---

### b) Interrupt Flag (IF)

The **Interrupt Flag** controls the handling of external interrupts.

* `IF = 1` → Interrupts are enabled.
* `IF = 0` → Interrupts are disabled.

### Example

```assembly id="b8vsl5"
sti     ; Enable interrupts
cli     ; Disable interrupts
```

---

### c) Trap Flag (TF)

The **Trap Flag** is used for debugging purposes.

When `TF = 1`, the processor executes one instruction at a time and then generates an interrupt.

---

## Summary of Flag Registers

| Flag | Full Name            | Purpose                      |
| ---- | -------------------- | ---------------------------- |
| CF   | Carry Flag           | Indicates carry or borrow    |
| ZF   | Zero Flag            | Indicates zero result        |
| SF   | Sign Flag            | Indicates sign of result     |
| OF   | Overflow Flag        | Indicates overflow           |
| PF   | Parity Flag          | Indicates even or odd parity |
| AF   | Auxiliary Carry Flag | Used in BCD operations       |
| DF   | Direction Flag       | Controls string direction    |
| IF   | Interrupt Flag       | Enables/disables interrupts  |
| TF   | Trap Flag            | Used for debugging           |

---

## Example Program Using Flags

```assembly id="zjltmu"
.model small
.stack 100h

.code
main proc

    mov al, 5
    sub al, 5      ; ZF will be set

    mov ah, 4Ch
    int 21h

main endp
end main
```

### Explanation

In this program:

* `5 - 5 = 0`
* Since the result is zero, the **Zero Flag (ZF)** becomes set.

**Flag registers play a vital role in decision-making and control flow in Assembly language. Understanding flags is essential for writing efficient and logical Assembly programs.**
