# Module 5.6: LEA Instruction

## Introduction

The **LEA (Load Effective Address)** instruction is used to load the **offset address** of a variable or memory location into a register.

Unlike the `MOV` instruction, which transfers the actual data, the `LEA` instruction loads the **address** of the data.

The `LEA` instruction is commonly used when working with **strings**, **arrays**, and memory locations.

---

## Syntax

```assembly
LEA destination, source
```

* **Destination** → A 16-bit register (usually `DX`, `BX`, `SI`, or `DI`).
* **Source** → A memory variable or label.

---

## Example 1: Using LEA with a String

```assembly
.model small
.stack 100h

.data
    msg db 'Hello World!$'

.code
main proc

    mov ax, @data
    mov ds, ax

    ; Load address of msg into DX
    lea dx, msg

    ; Display the string
    mov ah, 09h
    int 21h

    ; Terminate program
    mov ah, 4Ch
    int 21h

main endp
end main
```

### Output

```text
Hello World!
```

### Explanation

* `lea dx, msg` loads the **offset address** of `msg` into register `DX`.
* `mov ah, 09h` selects DOS function `09h` for string output.
* `int 21h` displays the string whose address is stored in `DX`.

---

## Example 2: Difference Between MOV and LEA

```assembly
.data
    num db 10
```

### Using MOV

```assembly
mov al, num
```

* The actual value **10** is copied into `AL`.

### Using LEA

```assembly
lea bx, num
```

* The address (offset) of `num` is loaded into `BX`.

---

## Example 3: Displaying a Message Using LEA

```assembly
.model small
.stack 100h

.data
    msg db 'Welcome to Assembly Language!$'

.code
main proc

    mov ax, @data
    mov ds, ax

    mov ah, 09h
    lea dx, msg
    int 21h

    mov ah, 4Ch
    int 21h

main endp
end main
```

---

## Why Do We Use LEA?

* To load the address of variables into registers.
* To display strings using DOS interrupt `21h`.
* To work with arrays and memory locations.
* To access data indirectly.

---

## Summary

| Instruction | Purpose                            |
| ----------- | ---------------------------------- |
| `MOV`       | Transfers the actual data/value    |
| `LEA`       | Loads the address (offset) of data |

### Example

```assembly
mov al, num    ; AL gets the value stored in num
lea bx, num    ; BX gets the address of num
```

> **Note:** The `LEA` instruction does not load the value stored in memory; it only loads the address of that memory location.

**The `LEA` instruction is one of the most important instructions in Assembly language because it is widely used with strings, arrays, and memory addressing. Practice using `LEA` regularly to become comfortable with memory operations.**
