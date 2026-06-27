# Module 5.2: Taking Input and Adding Numbers

## Introduction

In Assembly language, we often need to take input from the user and perform arithmetic operations on that input. In this module, we will learn how to take two numbers from the user, add them, and display the result.

Since keyboard input is received in **ASCII format**, we must convert it into a numeric value before performing addition.

---

## Step 1: Taking Input from the User

To take a single character as input from the keyboard, we use **Function 01h** of interrupt `21h`.

### Syntax

```assembly id="2nblb5"
mov ah, 01h
int 21h
```

### Explanation

* `mov ah, 01h` selects the keyboard input function.
* `int 21h` waits for the user to press a key.
* The entered character is stored in the **AL** register.

---

## Step 2: Converting ASCII to Number

When the user enters a digit such as **5**, the computer stores it as its ASCII code (**35h**), not as the actual numeric value.

To convert an ASCII digit into a number, subtract **30h**.

### Example

```assembly id="tnjlwm"
sub al, 30h
```

If the user enters:

```text id="fvs24s"
5
```

ASCII value:

```text id="x7b6n0"
35h
```

After subtraction:

```text id="if5el6"
35h - 30h = 05h
```

---

## Program: Take Two Numbers and Add Them

```assembly id="0ozh78"
.model small
.stack 100h

.data
    msg1 db 'Enter first number: $'
    msg2 db 0Dh,0Ah,'Enter second number: $'
    msg3 db 0Dh,0Ah,'Sum = $'

.code
main proc

    mov ax, @data
    mov ds, ax

    ; Display first message
    mov ah, 09h
    lea dx, msg1
    int 21h

    ; Take first input
    mov ah, 01h
    int 21h

    sub al, 30h        ; Convert ASCII to number
    mov bl, al         ; Store first number

    ; Display second message
    mov ah, 09h
    lea dx, msg2
    int 21h

    ; Take second input
    mov ah, 01h
    int 21h

    sub al, 30h        ; Convert ASCII to number

    ; Add both numbers
    add al, bl

    ; Convert result back to ASCII
    add al, 30h

    ; Display result message
    mov ah, 09h
    lea dx, msg3
    int 21h

    ; Print result
    mov dl, al
    mov ah, 02h
    int 21h

    ; Terminate program
    mov ah, 4Ch
    int 21h

main endp
end main
```

## Sample Output

```text id="8hwdl4"
Enter first number: 4
Enter second number: 3
Sum = 7
```

## Explanation

1. The program first asks the user to enter the first number.
2. The entered digit is stored in the **AL** register.
3. Since input is in ASCII form, `30h` is subtracted to convert it into a numeric value.
4. The first number is stored in register **BL**.
5. The program then takes the second number and converts it into numeric form.
6. Both numbers are added using the `ADD` instruction.
7. The result is converted back to ASCII by adding `30h`.
8. Finally, the result is displayed on the screen.

> **Note:** This program works correctly for single-digit numbers (0–9) only.

**Practice this program regularly because taking input and performing arithmetic operations are essential skills in Assembly language programming.**
* Written by: Nimra ASif*
