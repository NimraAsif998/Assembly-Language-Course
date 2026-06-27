# Module 9.3: Vowel or Consonant Checker

## Introduction

The **Vowel or Consonant Checker** is a simple Assembly language project that takes a character as input from the user and determines whether it is a **vowel** or a **consonant**.

This project helps students understand:

* Character input from the keyboard.
* Conditional statements and comparisons.
* Multiple `CMP` instructions.
* Conditional jumps (`JE`, `JMP`).
* DOS interrupts for input and output.

---

## Learning Objectives

After completing this project, students will be able to:

* Take character input from the user.
* Compare characters using the `CMP` instruction.
* Use conditional jumps for decision making.
* Display appropriate messages on the screen.

---

## Algorithm

### Step 1

Display a message asking the user to enter an alphabet.

### Step 2

Take a character as input.

### Step 3

Compare the entered character with all vowels:

```text id="j2d57s"
A, E, I, O, U
a, e, i, o, u
```

### Step 4

If the character matches any vowel:

```text id="3m2rdm"
Display "It is a Vowel"
```

Otherwise:

```text id="k9x2t4"
Display "It is a Consonant"
```

---

## EMU8086 Program

```assembly id="v8q3p6"
.model small
.stack 100h

.data
    msg1 db 13,10,'Enter an alphabet: $'
    vowelMsg db 13,10,'It is a Vowel.$'
    consonantMsg db 13,10,'It is a Consonant.$'

.code
main proc

    mov ax, @data
    mov ds, ax

    ; Display message
    lea dx, msg1
    mov ah, 09h
    int 21h

    ; Take character input
    mov ah, 01h
    int 21h

    ; Check for vowels
    cmp al, 'A'
    je Vowel

    cmp al, 'E'
    je Vowel

    cmp al, 'I'
    je Vowel

    cmp al, 'O'
    je Vowel

    cmp al, 'U'
    je Vowel

    cmp al, 'a'
    je Vowel

    cmp al, 'e'
    je Vowel

    cmp al, 'i'
    je Vowel

    cmp al, 'o'
    je Vowel

    cmp al, 'u'
    je Vowel

    ; If no match found
    jmp Consonant

Vowel:
    lea dx, vowelMsg
    mov ah, 09h
    int 21h
    jmp ExitProgram

Consonant:
    lea dx, consonantMsg
    mov ah, 09h
    int 21h

ExitProgram:
    mov ah, 4Ch
    int 21h

main endp
end main
```

---

## Sample Run 1

```text id="hgl3wn"
Enter an alphabet: a

It is a Vowel.
```

---

## Sample Run 2

```text id="igfxyo"
Enter an alphabet: z

It is a Consonant.
```

---

## Explanation of Important Instructions

| Instruction | Purpose                     |
| ----------- | --------------------------- |
| `CMP`       | Compares two values         |
| `JE`        | Jumps if values are equal   |
| `JMP`       | Performs unconditional jump |
| `INT 21H`   | Calls DOS services          |
| `AH = 01H`  | Takes keyboard input        |
| `AH = 09H`  | Displays a string           |

---

## Flowchart

```text id="3t8r4f"
Start
   |
Display Message
   |
Take Character Input
   |
Compare with Vowels
   |
+-------------------+
| Match Found?      |
+-------------------+
      | Yes
      v
Display "Vowel"
      |
      v
     End

      No
      |
      v
Display "Consonant"
      |
      v
     End
```

---

**This mini-project is useful for understanding character comparison and conditional jumps in Assembly language. It provides practical experience in implementing decision-making logic using the `CMP` and `JE` instructions.**
