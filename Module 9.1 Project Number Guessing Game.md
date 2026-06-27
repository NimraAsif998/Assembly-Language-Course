# Module 9.1: Number Guessing Game

## Introduction

The **Number Guessing Game** is a simple Assembly language program in which the computer selects a number (either pre-set or pseudo-random) and asks the user to guess it.

The program compares the user's guess with the actual number and displays one of the following messages:

* **"Too High"** → if the guessed number is greater than the actual number.
* **"Too Low"** → if the guessed number is smaller than the actual number.
* **"Correct Guess!"** → if the guessed number matches the actual number.

This project helps students understand:

* User input using DOS interrupts.
* Conditional jumps (`JE`, `JG`, `JL`).
* Comparison using `CMP`.
* Program control flow.

---

## Learning Objectives

After completing this module, students will be able to:

* Take input from the user.
* Compare two values using the `CMP` instruction.
* Use conditional jump instructions.
* Display messages on the screen.
* Implement simple game logic in Assembly language.

---

## Algorithm

### Step 1

Store a secret number.

```text id="6ydyep"
Secret Number = 7
```

### Step 2

Display a message asking the user to guess the number.

### Step 3

Take input from the keyboard.

### Step 4

Convert ASCII input into an integer.

```text id="awj4w7"
Number = ASCII - 48
```

### Step 5

Compare the guessed number with the secret number.

```text id="v6oz4q"
If Guess > Secret Number
       Display "Too High"

If Guess < Secret Number
       Display "Too Low"

If Guess = Secret Number
       Display "Correct Guess"
```

---

## EMU8086 Program

```assembly id="0cqz6t"
.model small
.stack 100h

.data
    msg1 db 13,10,'Guess a number between 0 and 9: $'
    highMsg db 13,10,'Too High!$'
    lowMsg db 13,10,'Too Low!$'
    correctMsg db 13,10,'Correct Guess!$'

    secret db 7

.code
main proc

    mov ax,@data
    mov ds,ax

    ; Display message
    lea dx,msg1
    mov ah,09h
    int 21h

    ; Take input
    mov ah,01h
    int 21h

    ; Convert ASCII to integer
    sub al,48

    ; Compare with secret number
    cmp al,secret

    je Correct
    jg TooHigh
    jl TooLow

TooHigh:
    lea dx,highMsg
    mov ah,09h
    int 21h
    jmp ExitProgram

TooLow:
    lea dx,lowMsg
    mov ah,09h
    int 21h
    jmp ExitProgram

Correct:
    lea dx,correctMsg
    mov ah,09h
    int 21h

ExitProgram:
    mov ah,4Ch
    int 21h

main endp
end main
```

---

## Sample Run 1

```text id="7a9tct"
Guess a number between 0 and 9: 3

Too Low!
```

---

## Sample Run 2

```text id="5alsh0"
Guess a number between 0 and 9: 9

Too High!
```

---

## Sample Run 3

```text id="79m2lh"
Guess a number between 0 and 9: 7

Correct Guess!
```

---

## Explanation of Important Instructions

| Instruction | Purpose                         |
| ----------- | ------------------------------- |
| `CMP`       | Compares two values             |
| `JE`        | Jumps if values are equal       |
| `JG`        | Jumps if first value is greater |
| `JL`        | Jumps if first value is smaller |
| `INT 21H`   | Performs DOS services           |
| `AH = 01H`  | Takes keyboard input            |
| `AH = 09H`  | Displays a string               |

---

## Flowchart

```text id="jggxsi"
Start
   |
Display Message
   |
Take User Input
   |
Convert ASCII to Integer
   |
Compare with Secret Number
   |
+-------------+-------------+
|             |             |
Equal      Greater      Smaller
|             |             |
Correct   Too High     Too Low
|             |             |
+-------------+-------------+
              |
             End
```

---

**This mini-project demonstrates the practical use of conditional jumps and user input interrupts, making it an excellent exercise for beginners learning Assembly language.**
