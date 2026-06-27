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
    ; Game text messages
    msg_start db 'Guess the secret number (0-9): $'
    msg_high  db 0dh, 0ah, 'Too high! Try again.$'
    msg_low   db 0dh, 0ah, 'Too low! Try again.$'
    msg_win   db 0dh, 0ah, 'Correct! You win!$'
    
    ; The secret number (ASCII value for '5')
    secret    db '5' 

.code
main proc
    ; Initialize data segment
    mov ax, @data
    mov ds, ax

game_loop:
    ; Print the start message
    mov dx, offset msg_start
    mov ah, 09h
    int 21h

    ; Read a single character from the user (stored in AL)
    mov ah, 01h
    int 21h

    ; --- CMP AND JUMP LOGIC STARTS HERE ---
    
    ; Compare user input (AL) with the secret number
    cmp al, secret
    
    ; Jump if Equal: Go to win section if AL == secret
    je win_game
    
    ; Jump if Less Than: Go to low section if AL < secret
    jl too_low
    
    ; Jump if Greater Than: Go to high section if AL > secret
    jg too_high

too_high:
    ; Print "Too high!" message
    mov dx, offset msg_high
    mov ah, 09h
    int 21h
    jmp next_turn        ; Unconditional jump to reset the loop

too_low:
    ; Print "Too low!" message
    mov dx, offset msg_low
    mov ah, 09h
    int 21h
    jmp next_turn        ; Unconditional jump to reset the loop

next_turn:
    ; Print a newline for spacing
    mov dl, 0dh
    mov ah, 02h
    int 21h
    mov dl, 0ah
    int 21h
    
    jmp game_loop        ; Loop back to let user guess again

win_game:
    ; Print victory message
    mov dx, offset msg_win
    mov ah, 09h
    int 21h

    ; Exit program safely
    mov ah, 4ch
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
