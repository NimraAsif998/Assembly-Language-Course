# Module 6: All About Loops in Assembly Language

## Introduction

A **loop** is a programming structure that repeatedly executes a block of instructions until a specific condition becomes false.

Loops are used when we need to perform the same task multiple times, such as printing numbers, processing arrays, or repeating calculations.

In Assembly language, loops are commonly implemented using:

* `LOOP` instruction
* Conditional jumps (`JNZ`, `JZ`, `JE`, `JNE`)
* Counter registers (usually `CX`)

---

# Why Do We Use Loops?

Loops help us:

* Avoid writing the same instructions repeatedly.
* Reduce program size.
* Improve code readability.
* Execute tasks efficiently.

---

# Loop Counter Register

In 8086 Assembly language, the **CX register** is commonly used as a loop counter.

Example:

```assembly id="1"
mov cx, 5
```

This means the loop will execute **5 times**.

---

# 1. LOOP Instruction

The `LOOP` instruction automatically:

1. Decrements the `CX` register by 1.
2. Checks whether `CX = 0`.
3. If `CX` is not zero, control jumps to the specified label.

## Syntax

```assembly id="2"
LOOP label
```

---

## Example: Print Character 5 Times

```assembly id="3"
.model small
.stack 100h

.code
main proc

    mov cx, 5

PrintAgain:

    mov dl, '*'
    mov ah, 02h
    int 21h

    loop PrintAgain

    mov ah, 4Ch
    int 21h

main endp
end main
```

### Output

```text id="4"
*****
```

---

# How LOOP Works

Suppose:

```assembly id="5"
mov cx, 3
```

Execution:

| Iteration | CX Before LOOP | CX After LOOP |
| --------- | -------------- | ------------- |
| 1         | 3              | 2             |
| 2         | 2              | 1             |
| 3         | 1              | 0             |

When `CX = 0`, the loop stops.

---

# 2. Using Conditional Jumps as Loops

Loops can also be created using:

* `CMP`
* `JNZ`
* `JZ`
* `JE`
* `JNE`

---

## Example: Print Numbers 1 to 5

```assembly id="6"
.model small
.stack 100h

.code
main proc

    mov cl, 1

Again:

    mov dl, cl
    add dl, 48

    mov ah, 02h
    int 21h

    inc cl

    cmp cl, 6
    jne Again

    mov ah, 4Ch
    int 21h

main endp
end main
```

### Output

```text id="7"
12345
```

---

# 3. Nested Loops

A loop inside another loop is called a **Nested Loop**.

Nested loops are commonly used for:

* Printing patterns.
* Matrix operations.
* Processing multidimensional arrays.

---

## Example: Print a Square Pattern

```assembly id="8"
.model small
.stack 100h

.code
main proc

    mov cx, 3

OuterLoop:

    push cx

    mov cx, 5

InnerLoop:

    mov dl, '*'
    mov ah, 02h
    int 21h

    loop InnerLoop

    mov dl, 10
    mov ah, 02h
    int 21h

    mov dl, 13
    int 21h

    pop cx

    loop OuterLoop

    mov ah, 4Ch
    int 21h

main endp
end main
```

### Output

```text id="9"
*****
*****
*****
```

---

# 4. Infinite Loop

An **Infinite Loop** continues forever because no terminating condition exists.

Example:

```assembly id="10"
Again:
    jmp Again
```

This program never stops.

---

# 5. Breaking a Loop

Sometimes we need to exit a loop before it finishes.

This can be done using:

```assembly id="11"
JMP ExitLabel
```

Example:

```assembly id="12"
cmp al, 'q'
je ExitProgram
```

---

# Common Loop Instructions

| Instruction | Purpose                       |
| ----------- | ----------------------------- |
| `LOOP`      | Repeats until CX becomes zero |
| `JMP`       | Unconditional jump            |
| `JE`        | Jump if equal                 |
| `JNE`       | Jump if not equal             |
| `JZ`        | Jump if zero                  |
| `JNZ`       | Jump if not zero              |

---

# Flowchart of a Loop

```text id="13"
Initialize Counter
        |
        v
Execute Statements
        |
        v
Decrease Counter
        |
        v
Counter = 0 ?
   |            |
  No           Yes
   |            |
   +----> Repeat
                |
                v
               End
```

---

# Complete Example: Print Numbers 1 to 9 Using LOOP

```assembly id="14"
.model small
.stack 100h

.code
main proc

    mov cx, 9
    mov dl, '1'

Again:

    mov ah, 02h
    int 21h

    inc dl

    loop Again

    mov ah, 4Ch
    int 21h

main endp
end main
```

### Output

```text id="15"
123456789:
```

> **Note:** The above example works correctly only up to single-digit ASCII values. For printing multi-digit numbers, additional conversion logic is required.

---

# Summary

| Concept          | Description                    |
| ---------------- | ------------------------------ |
| Loop             | Repeats a set of instructions  |
| CX Register      | Commonly used loop counter     |
| LOOP             | Automatically decrements CX    |
| Nested Loop      | Loop inside another loop       |
| Infinite Loop    | Executes forever               |
| Conditional Loop | Uses CMP and jump instructions |

**Loops are one of the most important control structures in Assembly language. They help execute repetitive tasks efficiently and are widely used in real-world programs.**
