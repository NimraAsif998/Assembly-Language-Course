# Module 5.4: Taking Input and Multiplying Numbers

## Introduction

In Assembly language, we can perform multiplication using the **MUL** instruction. In this module, we will learn how to take two numbers from the user, multiply them, and display the result.

Since keyboard input is received in **ASCII format**, we must first convert it into numeric form before performing multiplication.

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

When a user enters a digit, it is stored as an ASCII code.

For example:

```text
Character: 4
ASCII Code: 34h
```

To convert the ASCII digit into its actual numeric value, subtract **30h**.

```assembly
sub al, 30h
```

---

## Program: Take Two Numbers and Multiply Them

```assembly
.model small
.stack 100h

.data
    msg1 db 'Enter first number: $'
    msg2 db 0Dh,0Ah,'Enter second number: $'
    msg3 db 0Dh,0Ah,'Product = $'

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

    ; Multiply both numbers
    mul bl             ; AL × BL → AX

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
Enter first number: 3
Enter second number: 2
Product = 6
```

## Explanation

1. The program first asks the user to enter the first number.
2. The entered digit is converted from ASCII to numeric form and stored in register **BL**.
3. The program then asks for the second number and converts it into numeric form.
4. The `MUL` instruction multiplies the contents of **AL** with **BL**.
5. The result is stored in register **AX**.
6. The result is converted back to ASCII by adding `30h`.
7. Finally, the product is displayed on the screen.

> **Note:** This program works correctly for single-digit inputs and single-digit results only. For larger results (for example, `9 × 9 = 81`), additional logic is required to display both digits.

**Practice these programs regularly because arithmetic operations are fundamental concepts in Assembly language programming.**
