# Module 8.2: Program Instructions, Program Compilation, Primary Instruction Cycle, and Types of Instructions in an Instruction Set

## 1. Program Instruction

A **program instruction** is a command given to the processor to perform a specific task. An Assembly language program consists of a sequence of instructions executed one after another by the CPU.

Each instruction tells the processor what operation to perform, such as transferring data, performing arithmetic operations, or controlling program execution.

### General Format of an Instruction

```assembly id="6ek0zi"
Opcode Operand1, Operand2
```

### Examples

```assembly id="cq5v3z"
MOV AX, BX
ADD AL, 5
SUB BL, CL
```

### Explanation

* `MOV AX, BX` transfers the contents of `BX` into `AX`.
* `ADD AL, 5` adds `5` to register `AL`.
* `SUB BL, CL` subtracts the contents of `CL` from `BL`.

---

## 2. Program Compilation

A program written in Assembly language cannot be executed directly by the computer. It must first be translated into machine language.

This translation process is called **Program Compilation** or **Assembly Process**.

The software that performs this translation is known as an **Assembler**.

### Steps in Program Compilation

1. **Writing the Source Program**

   * The programmer writes the Assembly language code.

2. **Assembly**

   * The assembler translates the source code into object code.

3. **Linking**

   * The linker combines object files and creates an executable file.

4. **Execution**

   * The executable file is loaded into memory and executed by the CPU.

### Compilation Process

```text id="s0y6z5"
Source Program → Assembler → Object Code → Linker → Executable File
```

### Example

```assembly id="r9ef6h"
mov al, 5
add al, 3
```

The assembler converts these instructions into machine code that the processor can understand.

---

## 3. Primary Instruction Cycle

The **Instruction Cycle** is the sequence of steps performed by the CPU to execute an instruction.

The CPU repeatedly performs these steps for every instruction.

### Stages of the Instruction Cycle

### a) Fetch Cycle

The CPU fetches the instruction from memory.

### b) Decode Cycle

The control unit decodes the instruction to determine the required operation.

### c) Execute Cycle

The CPU performs the specified operation.

### d) Store Cycle

The result is stored in a register or memory location.

### Diagram of Instruction Cycle

```text id="tw0b4a"
Fetch → Decode → Execute → Store
```

### Example

Consider the instruction:

```assembly id="b8u04c"
ADD AL, BL
```

The CPU performs the following steps:

1. Fetch the instruction from memory.
2. Decode the instruction.
3. Add the contents of `BL` to `AL`.
4. Store the result in `AL`.

---

## 4. Types of Instructions in an Instruction Set

An **Instruction Set** is a collection of all instructions that a processor can execute.

The instructions in 8086 are divided into different categories.

---

### 1. Data Transfer Instructions

These instructions transfer data from one location to another.

#### Examples

```assembly id="r3vh9m"
MOV AX, BX
PUSH AX
POP BX
XCHG AX, BX
```

---

### 2. Arithmetic Instructions

These instructions perform mathematical operations.

#### Examples

```assembly id="z4pwsl"
ADD AX, BX
SUB AX, BX
MUL BL
DIV CL
INC AX
DEC BX
```

---

### 3. Logical Instructions

These instructions perform logical operations.

#### Examples

```assembly id="gk0e3w"
AND AL, BL
OR AL, BL
XOR AL, BL
NOT AL
```

---

### 4. Control Transfer Instructions

These instructions change the normal sequence of program execution.

#### Examples

```assembly id="h6nlwv"
JMP LABEL
JE LABEL
JNE LABEL
CALL PROC
RET
```

---

### 5. String Instructions

These instructions operate on strings or arrays.

#### Examples

```assembly id="q5e80g"
MOVSB
LODSB
STOSB
CMPSB
```

---

### 6. Input and Output Instructions

These instructions perform communication with input and output devices.

#### Examples

```assembly id="f7sviv"
IN AL, 60H
OUT 20H, AL
```

---

### 7. Processor Control Instructions

These instructions control processor operations.

#### Examples

```assembly id="h3lgrr"
CLC
STC
NOP
HLT
```

---

## Summary

| Instruction Type  | Purpose                  | Examples       |
| ----------------- | ------------------------ | -------------- |
| Data Transfer     | Transfer data            | MOV, PUSH, POP |
| Arithmetic        | Mathematical operations  | ADD, SUB, MUL  |
| Logical           | Logical operations       | AND, OR, XOR   |
| Control Transfer  | Change execution flow    | JMP, JE, CALL  |
| String            | Operate on strings       | MOVSB, STOSB   |
| Input/Output      | Communicate with devices | IN, OUT        |
| Processor Control | Control CPU operations   | CLC, HLT       |

---

**Understanding program instructions, compilation, and the instruction cycle is essential because these concepts form the foundation of how Assembly language programs are executed by the processor.**
# Components of an Instruction

An **instruction** is a command given to the processor to perform a specific operation. Every Assembly language instruction consists of different components that define what operation is to be performed and on which data.

The basic components of an instruction are:

1. **Label (Optional)**
2. **Opcode**
3. **Operand(s)**
4. **Comment (Optional)**

## General Format

```assembly
Label: Opcode Operand(s) ; Comment
```

---

## 1. Label

A **label** is a symbolic name assigned to an instruction or memory location. It is used to identify a specific location in a program and is commonly used with jump instructions.

### Example

```assembly
start:
    mov ax, bx
```

Here, `start` is a label.

### Purpose of Labels

* Makes programs easier to read.
* Used for branching and looping.
* Identifies memory locations.

---

## 2. Opcode

The **Opcode (Operation Code)** specifies the operation that the processor has to perform.

### Examples of Opcodes

```assembly
MOV
ADD
SUB
MUL
DIV
JMP
```

### Example

```assembly
mov ax, bx
```

In this instruction:

```text
MOV → Opcode
```

The opcode tells the processor to move data.

---

## 3. Operand(s)

Operands are the data items on which the operation is performed. An instruction may have zero, one, or two operands.

Operands can be:

* **Registers**
* **Memory locations**
* **Immediate values (constants)**

### Example

```assembly
mov ax, bx
```

* `AX` → Destination Operand
* `BX` → Source Operand

Another example:

```assembly
add al, 5
```

* `AL` → Destination Operand
* `5` → Immediate Operand

---

## 4. Comment

A **comment** is an explanatory note added by the programmer to improve readability. Comments are ignored by the assembler and are not executed.

Comments begin with a semicolon (`;`).

### Example

```assembly
mov ax, bx      ; Copy BX into AX
```

---

## Complete Example

```assembly
loop1:
    add al, 5      ; Add 5 to AL
```

| Component | Value         |
| --------- | ------------- |
| Label     | `loop1`       |
| Opcode    | `ADD`         |
| Operand 1 | `AL`          |
| Operand 2 | `5`           |
| Comment   | `Add 5 to AL` |

---

## Summary

| Component      | Description                                 |
| -------------- | ------------------------------------------- |
| **Label**      | Identifies a memory location or instruction |
| **Opcode**     | Specifies the operation to perform          |
| **Operand(s)** | Data on which operation is performed        |
| **Comment**    | Improves code readability                   |

**Understanding the components of an instruction is essential because every Assembly language program is built using instructions.**

