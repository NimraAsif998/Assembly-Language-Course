

### **Question **

[
a = (b + c) \times (d - e)
]

Using **Direct Addressing Mode**:

```text
MOV AL, b      ; Direct Addressing
ADD AL, c      ; Direct Addressing

MOV BL, d      ; Direct Addressing
SUB BL, e      ; Direct Addressing

MUL BL         ; Register Addressing

MOV a, AL      ; Direct Addressing
```

### Addressing Modes Used

| Instruction | Addressing Mode     |
| ----------- | ------------------- |
| MOV AL, b   | Direct Addressing   |
| ADD AL, c   | Direct Addressing   |
| MOV BL, d   | Direct Addressing   |
| SUB BL, e   | Direct Addressing   |
| MUL BL      | Register Addressing |
| MOV a, AL   | Direct Addressing   |

---

### **Question **

[
x = (a + b) \times c + d
]

Using **Direct Addressing Mode**:

```text
MOV AL, a      ; Direct Addressing
ADD AL, b      ; Direct Addressing

MOV BL, c      ; Direct Addressing
MUL BL         ; Register Addressing

ADD AL, d      ; Direct Addressing

MOV x, AL      ; Direct Addressing
```

### Addressing Modes Used

| Instruction | Addressing Mode     |
| ----------- | ------------------- |
| MOV AL, a   | Direct Addressing   |
| ADD AL, b   | Direct Addressing   |
| MOV BL, c   | Direct Addressing   |
| MUL BL      | Register Addressing |
| ADD AL, d   | Direct Addressing   |
| MOV x, AL   | Direct Addressing   |

These expressions are primarily solved using **Direct Addressing Mode** because variables (`a`, `b`, `c`, `d`, `e`, `x`) are accessed directly from memory, while `MUL BL` uses **Register Addressing Mode**.

## Question 

### Expression

[
y = (p - q) \times (r + s)
]

### Solution Using Addressing Modes

```text id="r3m9jg"
MOV AL, p      ; Direct Addressing
SUB AL, q      ; Direct Addressing

MOV BL, r      ; Direct Addressing
ADD BL, s      ; Direct Addressing

MUL BL         ; Register Addressing

MOV y, AL      ; Direct Addressing
```

### Addressing Modes Used

| Instruction | Addressing Mode     |
| ----------- | ------------------- |
| MOV AL, p   | Direct Addressing   |
| SUB AL, q   | Direct Addressing   |
| MOV BL, r   | Direct Addressing   |
| ADD BL, s   | Direct Addressing   |
| MUL BL      | Register Addressing |
| MOV y, AL   | Direct Addressing   |

---

## Question 

### Expression

[
z = (a + b + c) \times d
]

### Solution Using Addressing Modes

```text id="2o1czf"
MOV AL, a      ; Direct Addressing
ADD AL, b      ; Direct Addressing
ADD AL, c      ; Direct Addressing

MOV BL, d      ; Direct Addressing
MUL BL         ; Register Addressing

MOV z, AL      ; Direct Addressing
```

### Addressing Modes Used

| Instruction | Addressing Mode     |
| ----------- | ------------------- |
| MOV AL, a   | Direct Addressing   |
| ADD AL, b   | Direct Addressing   |
| ADD AL, c   | Direct Addressing   |
| MOV BL, d   | Direct Addressing   |
| MUL BL      | Register Addressing |
| MOV z, AL   | Direct Addressing   |

---

## Question 

### Expression

[
w = (a + b) \times c - (d + e)
]

### Solution Using Addressing Modes

```text id="8r6x4l"
MOV AL, a      ; Direct Addressing
ADD AL, b      ; Direct Addressing

MOV BL, c      ; Direct Addressing
MUL BL         ; Register Addressing

MOV CL, d      ; Direct Addressing
ADD CL, e      ; Direct Addressing

SUB AL, CL     ; Register Addressing

MOV w, AL      ; Direct Addressing
```

### Addressing Modes Used

| Instruction | Addressing Mode     |
| ----------- | ------------------- |
| MOV AL, a   | Direct Addressing   |
| ADD AL, b   | Direct Addressing   |
| MOV BL, c   | Direct Addressing   |
| MUL BL      | Register Addressing |
| MOV CL, d   | Direct Addressing   |
| ADD CL, e   | Direct Addressing   |
| SUB AL, CL  | Register Addressing |
| MOV w, AL   | Direct Addressing   |

These expressions mainly use **Direct Addressing Mode** for accessing variables and **Register Addressing Mode** for arithmetic operations between registers.

