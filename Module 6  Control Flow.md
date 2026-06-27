

# Module 6: Control Flow

Control flow determines the order in which instructions are executed in a program. By default, Assembly language executes instructions sequentially, one after another. However, using comparison and jump instructions, we can alter the normal flow of execution and make decisions in our programs.

---

# 1. CMP Instruction

The **CMP (Compare)** instruction is used to compare two operands. It performs subtraction internally but does not store the result. Instead, it updates the status flags, which are then used by conditional jump instructions.

## Syntax

```assembly
CMP destination, source
```

## How It Works

The CMP instruction performs:

```assembly
destination - source
```

The result is not saved anywhere; only the flags are affected.

### Example

```assembly
mov al, 10
cmp al, 5
```

In this example, `10` is compared with `5`. Since `10` is greater than `5`, the processor updates the flags accordingly.

### Another Example

```assembly
mov al, 5
cmp al, 5
```

Since both values are equal, the **Zero Flag (ZF)** becomes set.

---

# 2. Jump Instructions

Jump instructions are used to transfer control from one part of the program to another. They allow the program to skip certain instructions or repeat a block of code.

There are two types of jump instructions:

1. **Conditional Jump Instructions**
2. **Unconditional Jump Instructions**

---

# 3. Conditional Statements

Conditional statements execute only when a specific condition is true. They are usually used after the `CMP` instruction.

## Common Conditional Jump Instructions

| Instruction    | Meaning                  |
| -------------- | ------------------------ |
| `JE` or `JZ`   | Jump if Equal / Zero     |
| `JNE` or `JNZ` | Jump if Not Equal        |
| `JG`           | Jump if Greater          |
| `JL`           | Jump if Less             |
| `JGE`          | Jump if Greater or Equal |
| `JLE`          | Jump if Less or Equal    |

---

## Example: Jump if Equal

```assembly
.model small
.stack 100h

.code
main proc

    mov al, 5
    cmp al, 5

    je equal_label

    mov bl, 0

equal_label:
    mov bl, 1

    mov ah, 4Ch
    int 21h

main endp
end main
```

### Explanation

* The program compares `AL` with `5`.
* Since both values are equal, the `JE` instruction transfers control to `equal_label`.
* Register `BL` is assigned the value `1`.

---

## Example: Check Greater Number

```assembly
.model small
.stack 100h

.code
main proc

    mov al, 9
    mov bl, 4

    cmp al, bl

    jg greater

    mov cl, 0
    jmp exit

greater:
    mov cl, 1

exit:
    mov ah, 4Ch
    int 21h

main endp
end main
```

In this example, since `9` is greater than `4`, the program jumps to the `greater` label.

---

# 4. Unconditional Statements

An unconditional statement transfers control without checking any condition. The most commonly used unconditional jump instruction is **JMP**.

## JMP Instruction

The `JMP` instruction immediately transfers control to a specified label.

### Syntax

```assembly
JMP label_name
```

### Example

```assembly
.model small
.stack 100h

.code
main proc

    mov al, 10

    jmp skip

    mov al, 20      ; This instruction will not execute

skip:
    mov bl, al

    mov ah, 4Ch
    int 21h

main endp
end main
```

### Explanation

* The `JMP` instruction transfers control directly to the `skip` label.
* The instruction `mov al, 20` is skipped and never executes.

---

# Complete Example: Conditional and Unconditional Jumps

```assembly
.model small
.stack 100h

.code
main proc

    mov al, 8
    mov bl, 5

    cmp al, bl

    jg greater

    mov dl, 'N'
    jmp display

greater:
    mov dl, 'Y'

display:
    mov ah, 02h
    int 21h

    mov ah, 4Ch
    int 21h

main endp
end main
```

### Output

```text
Y
```

The output is `Y` because `8` is greater than `5`.

---

**Control flow instructions are essential in Assembly language because they allow programs to make decisions, repeat tasks, and execute different blocks of code based on specific conditions. Practice these concepts regularly to build strong programming logic.**
