
# Module 6.5: Increment Until Overflow Happens

## Introduction

The **INC (Increment)** instruction is used to increase the value of an operand by **1**. When the value exceeds the maximum capacity of the register, an **overflow** occurs.

In this module, we will continuously increment a register until overflow happens and observe the affected flags.

---

## INC Instruction

The `INC` instruction adds **1** to the destination operand.

### Syntax

```assembly
INC destination
```

### Example

```assembly
mov al, 5
inc al      ; AL = 6
```

---

## Program: Increment Until Overflow Occurs

```assembly
.model small
.stack 100h

.code
main proc

    mov al, 127     ; Maximum positive value for signed 8-bit number

    inc al          ; AL becomes 80h (-128)

    ; After execution:
    ; AL = 80h
    ; OF = 1

    mov ah, 4Ch
    int 21h

main endp
end main
```

---

## Explanation

1. The instruction `mov al, 127` loads the value **127** into register `AL`.
2. In an **8-bit signed register**, the maximum positive value is **127**.
3. The instruction `inc al` increases the value by **1**.
4. Since `127 + 1 = 128` cannot be represented as a signed 8-bit number, an **overflow** occurs.
5. The value stored in `AL` becomes `80h`, which represents **-128** in signed form.
6. Therefore, the **Overflow Flag (OF)** is set.

---

## Observing Flags in EMU8086

1. Load the program into **EMU8086**.
2. Execute the instructions using **Single Step (F8)**.
3. After executing `INC AL`, observe the flags window.
4. Notice that:

```text
AL = 80h
OF = 1
SF = 1
ZF = 0
```

---

## Another Example

```assembly
.model small
.stack 100h

.code
main proc

    mov al, 255

    inc al          ; AL = 00h

    ; Result:
    ; AL = 00h
    ; ZF = 1

    mov ah, 4Ch
    int 21h

main endp
end main
```

### Explanation

* `255 + 1` causes the register to wrap around to `00h`.
* Since the result is zero, the **Zero Flag (ZF)** becomes set.

---

## Flags Affected by INC Instruction

| Flag   | Description                             |
| ------ | --------------------------------------- |
| **OF** | Set if signed overflow occurs           |
| **ZF** | Set if the result becomes zero          |
| **SF** | Set if the result is negative           |
| **PF** | Set if the result has even parity       |
| **AF** | Set if carry occurs from bit 3 to bit 4 |

> **Note:** The `INC` instruction does **not** affect the Carry Flag (CF).

---

### Sample Observation

```text
Before Increment:
AL = 127

After Increment:
AL = 80h (-128)

OF = 1
SF = 1
ZF = 0
```

**The `INC` instruction is useful for counters and loops. Understanding overflow behavior is essential for writing efficient Assembly language programs.**
