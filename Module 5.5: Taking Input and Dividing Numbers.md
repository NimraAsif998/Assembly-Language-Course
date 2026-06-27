# Module 5.5: Taking Input and Dividing Numbers

## Introduction

In Assembly language, division is performed using the **DIV** instruction. In this module, we will learn how to take two numbers from the user, divide them, and display the result.

Since keyboard input is received in **ASCII format**, we must first convert it into numeric form before performing division.

---

## Step 1: Taking Input from the User

To take a single character as input from the keyboard, we use **Function 01h** of interrupt `21h`.

### Syntax

```assembly
mov ah, 01h
int 21h
```

### Explanation

* `mov ah, 01h` selects the keyboard input function.
* `int 21h` waits for the user to press a key.
* The entered character is stored in the **AL** register.

---

## Step 2: Converting ASCII to Number

When the user enters a digit, it is stored as an ASCII code.

For example:

```text
Character: 8
ASCII Code: 38h
```

To convert the ASCII digit into its actual numeric value, subtract **30h**.

```assembly
sub al, 30h
```

---

## Program: Take Two Numbers and Divide Them

```assembly
.model small
.stack 100h

.data
    msg1 db 'Enter dividend: $'
    msg2 db 0Dh,0Ah,'Enter divisor: $'
    msg3 db 0Dh,0Ah,'Quotient = $'

.code
main proc

    mov ax, @data
    mov ds, ax

    ; Display first message
    mov ah, 09h
    lea dx, msg1
    int 21h

    ; Take dividend input
    mov ah, 01h
    int 21h

    sub al, 30h        ; Convert ASCII to number
    mov bl, al         ; Store dividend

    ; Display second message
    mov ah, 09h
    lea dx, msg2
    int 21h

    ; Take divisor input
    mov ah, 01h
    int 21h

    sub al, 30h        ; Convert ASCII to number
    mov cl, al         ; Store divisor

    ; Prepare for division
    mov al, bl
    mov ah, 00h

    ; Divide AL by CL
    div cl             ; Quotient -> AL, Remainder -> AH

    ; Convert quotient to ASCII
    add al, 30h

    ; Display result message
    mov ah, 09h
    lea dx, msg3
    int 21h

    ; Print quotient
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

```text
Enter dividend: 8
Enter divisor: 2
Quotient = 4
```

## Explanation

1. The program first asks the user to enter the **dividend** (number to be divided).
2. The entered digit is converted from ASCII to numeric form and stored in register **BL**.
3. The program then asks for the **divisor** and stores it in register **CL**.
4. Before division, `AH` is cleared because the `DIV` instruction uses the register pair `AX`.
5. The instruction `div cl` divides the value in `AX` by `CL`.
6. After division:

   * **AL** contains the quotient.
   * **AH** contains the remainder.
7. The quotient is converted back to ASCII by adding `30h`.
8. Finally, the quotient is displayed on the screen.

> **Note:** This program works correctly for single-digit inputs and displays only the quotient. Also, the divisor must not be zero because division by zero causes an error.

**Practice these programs regularly because arithmetic operations and user input handling are essential concepts in Assembly language programming.**
