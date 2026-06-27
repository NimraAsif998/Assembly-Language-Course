# Module 3.3: Expression Notation

## Introduction

Expression notation refers to different ways of writing arithmetic expressions. In computer science, expressions can be represented in three forms:

1. **Infix Notation**
2. **Prefix Notation**
3. **Postfix Notation**

These notations are widely used in compilers, interpreters, and expression evaluation.

---

# 1. Infix Notation

In **Infix notation**, the operator is written **between operands**.

## General Form

```text
Operand Operator Operand
```

## Examples

```text
A + B
X - Y
P * Q
(A + B) * C
```

### Characteristics

* Most commonly used by humans.
* Parentheses are often required to specify precedence.

---

# 2. Prefix Notation (Polish Notation)

In **Prefix notation**, the operator is written **before operands**.

## General Form

```text
Operator Operand Operand
```

## Examples

```text
+ A B
- X Y
* + A B C
```

### Example

Infix:

```text
(A + B) * C
```

Prefix:

```text
* + A B C
```

### Characteristics

* No parentheses are required.
* Evaluation is performed from **right to left**.

---

# 3. Postfix Notation (Reverse Polish Notation)

In **Postfix notation**, the operator is written **after operands**.

## General Form

```text
Operand Operand Operator
```

## Examples

```text
A B +
X Y -
A B + C *
```

### Example

Infix:

```text
(A + B) * C
```

Postfix:

```text
A B + C *
```

### Characteristics

* No parentheses are required.
* Evaluation is performed from **left to right**.
* Widely used in stack-based systems.

---

# Comparison of Notations

| Infix       | Prefix    | Postfix   |
| ----------- | --------- | --------- |
| A + B       | + A B     | A B +     |
| A - B       | - A B     | A B -     |
| A * B       | * A B     | A B *     |
| (A + B) * C | * + A B C | A B + C * |

---

# Conversion Rules

## Infix to Prefix

### Steps

1. Reverse the infix expression.
2. Replace `(` with `)` and vice versa.
3. Convert the expression into postfix.
4. Reverse the obtained postfix expression.

### Example

Convert:

```text
(A + B) * C
```

Step 1:

```text
C * (B + A)
```

Step 2:

```text
C * (B + A)
```

Step 3 (Postfix):

```text
C B A + *
```

Step 4 (Reverse):

```text
* + A B C
```

---

## Infix to Postfix

### Rules

* If the symbol is an operand, add it to the output.
* If the symbol is `(`, push it onto the stack.
* If the symbol is `)`, pop until `(` is encountered.
* If the symbol is an operator, pop operators with higher or equal precedence.

### Example

Convert:

```text
(A + B) * C
```

Postfix:

```text
A B + C *
```

---

# Solved Questions

## Question 1

Convert the following expression into Prefix and Postfix:

```text
A + B * C
```

### Prefix

```text
+ A * B C
```

### Postfix

```text
A B C * +
```

---

## Question 2

Convert the following expression:

```text
(A + B) * (C - D)
```

### Prefix

```text
* + A B - C D
```

### Postfix

```text
A B + C D - *
```

---

## Question 3

Convert the following expression:

```text
A + B - C * D
```

### Prefix

```text
- + A B * C D
```

### Postfix

```text
A B + C D * -
```

---

## Question 4

Convert the following expression:

```text
(A + B + C) * D
```

### Prefix

```text
* + + A B C D
```

### Postfix

```text
A B + C + D *
```

---

## Question 5

Convert the following expression:

```text
(A - B) * (C + D)
```

### Prefix

```text
* - A B + C D
```

### Postfix

```text
A B - C D + *
```

---

# Practice Questions

1. Convert `A * B + C` into Prefix and Postfix.
2. Convert `(A + B) / (C - D)` into Prefix and Postfix.
3. Convert `A + B * C - D` into Prefix and Postfix.
4. Convert `(A - B + C) * D` into Prefix and Postfix.
5. Convert `(A + B) * (C + D)` into Prefix and Postfix.

---

## Summary

| Notation | Operator Position | Example |
| -------- | ----------------- | ------- |
| Infix    | Between operands  | A + B   |
| Prefix   | Before operands   | + A B   |
| Postfix  | After operands    | A B +   |

**Expression notation is an important concept in compiler design and data structures because it simplifies expression evaluation and conversion processes.**
