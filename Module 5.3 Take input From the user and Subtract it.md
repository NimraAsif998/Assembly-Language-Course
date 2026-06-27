# Module 5.3: Taking Input and Subtracting Numbers

## Introduction

In Assembly language, we can take input from the user and perform arithmetic operations such as subtraction. In this module, we will learn how to take two numbers from the user, subtract them, and display the result.

Since keyboard input is received in **ASCII format**, we must first convert it into a numeric value before performing subtraction.

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

When the user enters a digit, it is stored as an ASCII code. For example, if the user enters **8**, its ASCII value is **38h**.

To convert the ASCII digit into its actual numeric value, subtract **30h**.

### Example

```assembly
sub al, 30h
```

---

## Program: Take Two Numbers and Subtract Them

```assembly
.model small
.stack 100h

.data
    msg1 db 'Enter first number: $'
    msg2 db 0Dh,0Ah,'Enter second number: $'
    msg3 db 0Dh,0Ah,'Difference = $'

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

    ; Subtract second number from first number
    mov cl, al
    mov al, bl
    sub al, cl

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

```text
Enter first number: 9
Enter second number: 4
Difference = 5
```

## Explanation

1. The program asks the user to enter the first number.
2. The entered digit is converted from ASCII to its numeric value and stored in register **BL**.
3. The program then asks for the second number and converts it into numeric form.
4. The second number is stored in register **CL**.
5. The `SUB` instruction subtracts the second number from the first number.
6. The result is converted back to ASCII by adding `30h`.
7. Finally, the result is displayed on the screen.

> **Note:** This program works correctly only for single-digit numbers where the first number is greater than or equal to the second number.

**Practice these programs regularly because input handling and arithmetic operations are fundamental concepts in Assembly language programming.**
