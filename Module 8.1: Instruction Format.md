# Module 8.1: Instruction Format

## Introduction

An **instruction** is a command given to the processor to perform a specific task. Every Assembly language program consists of a sequence of instructions.

The **Instruction Format** defines how an instruction is written and how its different parts are arranged.

A typical Assembly language instruction consists of the following components:

1. **Label (Optional)**
2. **Opcode**
3. **Operand(s)**
4. **Comment (Optional)**

---

## General Format of an Instruction

```assembly id="eod4eb"
Label: Opcode Operand(s) ; Comment
```

Not all instructions contain all four components. Some parts, such as labels and comments, are optional.

---

## Components of an Instruction

### 1. Label

A **label** is a symbolic name given to a memory location or a group of instructions. Labels make programs easier to read and are commonly used with jump instructions.

### Example

```assembly id="9k8jzg"
start:
    mov ax, bx
```

In this example, `start` is a label.

---

### 2. Opcode

The **Opcode (Operation Code)** specifies the operation that the processor has to perform.

Examples of opcodes include:

* `MOV`
* `ADD`
* `SUB`
* `MUL`
* `DIV`
* `JMP`

### Example

```assembly id="0u7kv1"
mov ax, bx
```

Here:

```text id="0n5vzo"
MOV → Opcode
```

The `MOV` instruction tells the processor to transfer data.

---

### 3. Operands

Operands specify the data on which the operation is performed.

Operands can be:

* Registers
* Memory locations
* Constants (Immediate values)

### Example

```assembly id="m0axd0"
mov ax, bx
```

In this instruction:

```text id="hf0kpi"
AX → Destination Operand
BX → Source Operand
```

Another example:

```assembly id="qv5f1u"
add al, 5
```

Here:

* `AL` is the destination operand.
* `5` is an immediate operand.

---

### 4. Comment

Comments are explanatory notes written by programmers to improve code readability. The assembler ignores comments during program execution.

Comments begin with a semicolon (`;`).

### Example

```assembly id="37n94c"
mov ax, bx      ; Copy BX into AX
```

---

## Examples of Instruction Formats

### Example 1

```assembly id="pj5hl4"
mov ax, bx
```

| Component | Value |
| --------- | ----- |
| Label     | None  |
| Opcode    | MOV   |
| Operand 1 | AX    |
| Operand 2 | BX    |
| Comment   | None  |

---

### Example 2

```assembly id="70tkru"
loop1:
    add al, 5      ; Add 5 to AL
```

| Component | Value       |
| --------- | ----------- |
| Label     | loop1       |
| Opcode    | ADD         |
| Operand 1 | AL          |
| Operand 2 | 5           |
| Comment   | Add 5 to AL |

---

## Complete Program Example

```assembly id="2n2r4e"
.model small
.stack 100h

.code
main proc

start:
    mov al, 10     ; Load value 10 into AL
    add al, 5      ; Add 5 to AL

    mov ah, 4Ch    ; Terminate program
    int 21h

main endp
end main
```

### Explanation

* `start` is a label.
* `MOV` and `ADD` are opcodes.
* `AL`, `10`, and `5` are operands.
* Text after `;` represents comments.

---

## Types of Instructions Based on Operands

### Zero-Operand Instruction

```assembly id="g9gd9v"
CLC
```

This instruction does not require any operand.

---

### One-Operand Instruction

```assembly id="mgkl6h"
INC AL
```

This instruction uses only one operand.

---

### Two-Operand Instruction

```assembly id="h08oij"
MOV AX, BX
```

This instruction uses two operands.

---

## Summary

| Component | Purpose                              |
| --------- | ------------------------------------ |
| Label     | Identifies a memory location         |
| Opcode    | Specifies the operation to perform   |
| Operand   | Data on which operation is performed |
| Comment   | Improves readability                 |

---

**Understanding instruction format is essential because every Assembly language program is built using instructions. A clear understanding of instruction components helps in writing, reading, and debugging Assembly programs effectively.**
