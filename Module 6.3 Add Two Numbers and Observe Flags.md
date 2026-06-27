# Module 6.3: Add Two Numbers and Observe Flags

## Introduction

In Assembly language, whenever an arithmetic operation is performed, the processor automatically updates the **Flag Register**. These flags indicate information about the result, such as whether the result is zero, negative, or if a carry or overflow has occurred.

In this module, we will add two numbers and observe how different flags are affected.

---

## Program: Add Two Numbers

```assembly
.model small
.stack 100h

.code
main proc

    mov al, 255     ; Load first number
    add al, 1       ; Add second number

    ; After execution:
    ; AL = 00h
    ; CF = 1
    ; ZF = 1

    mov ah, 4Ch
    int 21h

main endp
end main
```

---

## Explanation

1. The instruction `mov al, 255` loads the value **255** into register **AL**.
2. The instruction `add al, 1` adds **1** to the value stored in `AL`.
3. Since `AL` is an 8-bit register, it can store values only from **0 to 255**.
4. Adding `255 + 1` produces `256`, which cannot fit in an 8-bit register.
5. Therefore:

   * The result stored in `AL` becomes `00h`.
   * The **Carry Flag (CF)** is set because a carry is generated.
   * The **Zero Flag (ZF)** is also set because the final result is zero.

---

## Observing Flags in EMU8086

After running the program in **EMU8086**:

1. Click on **Single Step (F8)** to execute instructions one by one.
2. Observe the **Flags window** on the right side.
3. Notice how the values of **CF**, **ZF**, and other flags change after the `ADD` instruction.

---

## Another Example

```assembly
.model small
.stack 100h

.code
main proc

    mov al, 5
    add al, 5

    ; Result:
    ; AL = 10
    ; CF = 0
    ; ZF = 0

    mov ah, 4Ch
    int 21h

main endp
end main
```

### Explanation

* `5 + 5 = 10`
* No carry is generated, so **CF = 0**.
* The result is not zero, so **ZF = 0**.

---

## Example Producing Overflow

```assembly
.model small
.stack 100h

.code
main proc

    mov al, 127
    add al, 1

    ; Result:
    ; AL = 80h
    ; OF = 1

    mov ah, 4Ch
    int 21h

main endp
end main
```

### Explanation

* In signed arithmetic, the maximum value that can be stored in an 8-bit register is **127**.
* Adding `1` to `127` causes an **overflow**.
* Therefore, the **Overflow Flag (OF)** becomes set.

---

## Common Flags Affected by ADD Instruction

| Flag   | Description                                       |
| ------ | ------------------------------------------------- |
| **CF** | Set if a carry is generated.                      |
| **ZF** | Set if the result is zero.                        |
| **SF** | Set if the result is negative.                    |
| **OF** | Set if signed overflow occurs.                    |
| **PF** | Set if the result contains an even number of 1's. |
| **AF** | Set if carry occurs from bit 3 to bit 4.          |

---

### Sample Observation

```text
255 + 1 = 00h

CF = 1
ZF = 1
SF = 0
OF = 0
```

**Understanding flags is essential because they are widely used in comparison and decision-making instructions in Assembly language. Practice observing flags in EMU8086 after every arithmetic operation.**
