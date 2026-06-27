

### **Question 1**

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

### **Question 2**

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
