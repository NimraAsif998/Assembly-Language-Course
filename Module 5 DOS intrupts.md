# DOS Interrupts (8086 Assembly) 

## What is a DOS Interrupt?

A **DOS Interrupt** is a way for an Assembly program to ask the DOS operating system to do a task.

For example:

* Print something on the screen.
* Take input from the keyboard.
* Open or save a file.
* Exit the program.

Instead of doing these tasks itself, the program asks DOS for help.

The most commonly used DOS interrupt is:

```emu 8086
INT 21H
```

---

# How Does It Work?

There are only **2 simple steps**:

### Step 1: Tell DOS what you want to do.

Store the function number in the **AH** register.

```asm
MOV AH, Function_Number
```

### Step 2: Call DOS.

```asm
INT 21H
```

That's it! DOS performs the requested task.

---

# Common INT 21H Functions

## 1. Read One Character

```asm
MOV AH, 01H
INT 21H
```

**What happens?**

* User types one character.
* That character is saved in the **AL** register.

Example:

If the user types:

```text
A
```

Then:

```text
AL = A
```

---

## 2. Display One Character

```asm
MOV AH, 02H
MOV DL, 'A'
INT 21H
```

**What happens?**

The character stored in **DL** is displayed.

Output:

```text
A
```

---

## 3. Display a String

```asm
MSG DB "Hello World!$"

MOV AH, 09H
LEA DX, MSG
INT 21H
```

**Important:** The string **must end with `$`**.

Output:

```text
Hello World!
```

---

## 4. Read a String

```asm
MOV AH, 0AH
INT 21H
```

This is used to take **more than one character** as input (a word or a sentence).

---

## 5. Exit the Program

```asm
MOV AH, 4CH
INT 21H
```

This ends the program and returns control to DOS.

---

# Easy Memory Trick

| AH Value | What It Does          |
| -------- | --------------------- |
| **01H**  | Read one character    |
| **02H**  | Display one character |
| **09H**  | Display a string      |
| **0AH**  | Read a string         |
| **4CH**  | Exit the program      |

---

# Example 

Think of DOS as your **helper**.

Your program says:

> "DOS, please print this text."

or

> "DOS, please take input from the keyboard."

DOS does the work and then gives control back to your program.

---


