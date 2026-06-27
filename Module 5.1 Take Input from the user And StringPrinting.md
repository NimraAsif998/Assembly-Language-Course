

# Module 5.1: Taking Input from the User and String Printing

## 1. Taking Input from the User

In Assembly language, programs often need to receive input from the user during execution. In **EMU8086**, DOS interrupt `21h` is commonly used for keyboard input.

To take a single character as input, we use **Function 01h** of interrupt `21h`.

### Syntax

```assembly
mov ah, 01h
int 21h
```

### Explanation

* `mov ah, 01h` → Selects DOS function **01h** for keyboard input.
* `int 21h` → Waits for the user to press a key.
* The entered character is automatically stored in the **AL** register.

### Example

```assembly
.model small
.stack 100h

.data

.code
main proc

    mov ax, @data
    mov ds, ax

    ; Take input from user
    mov ah, 01h
    int 21h

    ; Terminate program
    mov ah, 4Ch
    int 21h

main endp
end main
```

---

## 2. String Printing

A string is a sequence of characters enclosed within quotation marks. In Assembly language, strings are declared in the `.data` section.

To display a string on the screen, we use **Function 09h** of interrupt `21h`.

### Syntax

```assembly
mov ah, 09h
lea dx, string_name
int 21h
```

### Example

```assembly
.model small
.stack 100h

.data
    msg db 'Hello World!$'

.code
main proc

    mov ax, @data
    mov ds, ax

    ; Print string
    mov ah, 09h
    lea dx, msg
    int 21h

    ; Terminate program
    mov ah, 4Ch
    int 21h

main endp
end main
```

### Output

```text
Hello World!
```

---

# 3. Taking Input and Printing It Back

Sometimes we need to take input from the user and display the same input on the screen. This process is known as **echoing input**.

To print a single character, we use **Function 02h** of interrupt `21h`.

### Syntax

```assembly
mov ah, 02h
mov dl, character
int 21h
```

### Program Example

```assembly
.model small
.stack 100h

.data
    msg1 db 'Enter a character: $'
    msg2 db 0Dh,0Ah,'You entered: $'

.code
main proc

    mov ax, @data
    mov ds, ax

    ; Display first message
    mov ah, 09h
    lea dx, msg1
    int 21h

    ; Take input from user
    mov ah, 01h
    int 21h

    ; Save input in BL
    mov bl, al

    ; Print second message
    mov ah, 09h
    lea dx, msg2
    int 21h

    ; Display entered character
    mov ah, 02h
    mov dl, bl
    int 21h

    ; Terminate program
    mov ah, 4Ch
    int 21h

main endp
end main
```

### Sample Output

```text
Enter a character: A
You entered: A
```

### Explanation

1. The program first displays the message **"Enter a character:"**.
2. The user enters a character from the keyboard.
3. The character is stored in register **AL**.
4. The value is copied into **BL** for temporary storage.
5. The program prints **"You entered:"**.
6. Finally, the entered character is displayed on the screen using DOS interrupt `21h` function `02h`.

**Input and output operations are fundamental concepts in Assembly language. Practice these programs regularly to strengthen your understanding.**
