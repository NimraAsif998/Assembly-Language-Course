![NumberSystem](./NumberSystem.png)

# Module 3: Number Systems

## Table of Contents
1. [Introduction](#introduction)
2. [Binary Number System](#binary-number-system)
3. [Decimal Number System](#decimal-number-system)
4. [Octal Number System](#octal-number-system)
5. [Hexadecimal Number System](#hexadecimal-number-system)
6. [Number System Conversions](#number-system-conversions)
7. [Practice Problems](#practice-problems)
8. [Quick Reference](#quick-reference)

---

## Introduction

A **number system** is a method of representing numbers using a set of digits or symbols. Different number systems are used in computing and digital electronics. The four main number systems are:

| System | Base | Digits Used | Used In |
|--------|------|-------------|---------|
| Binary | 2 | 0, 1 | Computer Memory, Logic |
| Decimal | 10 | 0-9 | Everyday Life |
| Octal | 8 | 0-7 | Unix/Linux File Permissions |
| Hexadecimal | 16 | 0-9, A-F | Memory Addresses, Colors |

### Why Different Number Systems?

- **Binary**: Computers only understand 0s and 1s (on/off states)
- **Decimal**: Humans naturally use base-10
- **Octal & Hexadecimal**: Compact representation of binary data

---

## Binary Number System

### Definition
The **Binary Number System** uses base 2 with only two digits: **0 and 1**.

### Position Values
Each position represents a power of 2:

```
2^7  2^6  2^5  2^4  2^3  2^2  2^1  2^0
128  64   32   16   8    4    2    1
```

### Example: Binary to Decimal
```
Binary: 1101₂

Position:  2³   2²   2¹   2⁰
Value:     1    1    0    1
Power:     8  + 4  + 0  + 1  = 13₁₀
```

### Key Points
- Used in computer systems for data storage
- Each binary digit is called a **bit**
- 8 bits = 1 **byte**
- Very important for understanding computer architecture

### Examples
| Binary | Decimal |
|--------|---------|
| 1₂ | 1₁₀ |
| 10₂ | 2₁₀ |
| 11₂ | 3₁₀ |
| 100₂ | 4₁₀ |
| 1111₂ | 15₁₀ |
| 10000₂ | 16₁₀ |
| 11111111₂ | 255₁₀ |

---

## Decimal Number System

### Definition
The **Decimal Number System** uses base 10 with digits **0 through 9**. This is the number system we use in our daily life.

### Position Values
Each position represents a power of 10:

```
10⁴   10³   10²   10¹   10⁰
10000 1000  100   10    1
```

### Example: Understanding Decimal
```
Decimal: 5347₁₀

Position:  10³   10²   10¹   10⁰
Value:     5   + 3   + 4   + 7
Equals:    5000 + 300 + 40 + 7 = 5347₁₀
```

### Key Points
- Most widely used number system in the world
- Also called the **denary system**
- Base 10 because we have 10 fingers (historical origin)
- Standard for human communication of quantities

### Why Base 10?
The decimal system's widespread use is partly historical (humans have 10 fingers), making it natural for counting and commerce.

---

## Octal Number System

### Definition
The **Octal Number System** uses base 8 with digits **0 through 7**.

### Position Values
Each position represents a power of 8:

```
8⁴    8³    8²    8¹    8⁰
4096  512   64    8     1
```

### Example: Octal to Decimal
```
Octal: 345₈

Position:  8²   8¹   8⁰
Value:     3  + 4  + 5
Equals:    3(64) + 4(8) + 5(1)
         = 192 + 32 + 5 = 229₁₀
```

### Key Points
- Used in Unix/Linux systems (file permissions)
- Each octal digit represents 3 binary digits
- Also called **octonary**
- Rarely used in modern computing compared to hexadecimal

### Examples
| Octal | Decimal | Binary |
|-------|---------|--------|
| 0₈ | 0₁₀ | 000₂ |
| 1₈ | 1₁₀ | 001₂ |
| 2₈ | 2₁₀ | 010₂ |
| 7₈ | 7₁₀ | 111₂ |
| 10₈ | 8₁₀ | 1000₂ |
| 77₈ | 63₁₀ | 111111₂ |

### Octal in File Permissions
```
chmod 755 filename
- 7 = rwx (owner)
- 5 = r-x (group)
- 5 = r-x (others)
```

---

## Hexadecimal Number System

### Definition
The **Hexadecimal Number System** uses base 16 with digits **0-9 and letters A-F** (representing 10-15).

### Hex Digits
```
0, 1, 2, 3, 4, 5, 6, 7, 8, 9, A(10), B(11), C(12), D(13), E(14), F(15)
```

### Position Values
Each position represents a power of 16:

```
16⁴    16³    16²    16¹    16⁰
65536  4096   256    16     1
```

### Example: Hexadecimal to Decimal
```
Hex: 2AF₁₆

Position:  16²   16¹   16⁰
Value:     2   + A   + F
Equals:    2(256) + 10(16) + 15(1)
         = 512 + 160 + 15 = 687₁₀
```

### Key Points
- Each hex digit represents 4 binary digits
- Widely used in computing (memory addresses, color codes, Unicode)
- Case insensitive (2AF = 2af)
- Denoted with 0x prefix (0x2AF) or H suffix (2AFH)

### Common Uses
1. **Memory Addresses**: 0xDEADBEEF
2. **Color Codes**: #FF5733 (Red: FF, Green: 57, Blue: 33)
3. **Unicode Characters**: U+0041 (A)
4. **Machine Code**: Assembly language

### Examples
| Hex | Decimal | Binary |
|-----|---------|--------|
| A₁₆ | 10₁₀ | 1010₂ |
| F₁₆ | 15₁₀ | 1111₂ |
| 10₁₆ | 16₁₀ | 10000₂ |
| FF₁₆ | 255₁₀ | 11111111₂ |
| 100₁₆ | 256₁₀ | 100000000₂ |

---

## Number System Conversions

### 1. Decimal to Binary

#### Method: Repeated Division by 2
Divide the decimal number by 2 repeatedly and note remainders.

```
Example: Convert 13₁₀ to Binary

13 ÷ 2 = 6  remainder 1
6  ÷ 2 = 3  remainder 0
3  ÷ 2 = 1  remainder 1
1  ÷ 2 = 0  remainder 1

Read remainders from bottom to top: 1101₂

Verification: 1(8) + 1(4) + 0(2) + 1(1) = 13₁₀ ✓
```

#### Step-by-Step Algorithm
1. Divide the number by 2
2. Write down the remainder (0 or 1)
3. Divide the quotient by 2 again
4. Repeat until quotient is 0
5. Read remainders from bottom to top

---

### 2. Binary to Decimal

#### Method: Positional Notation
Multiply each digit by its position value and sum.

```
Example: Convert 1010₂ to Decimal

Position:  2³   2²   2¹   2⁰
Value:     1    0    1    0
Calculate: 1(8) + 0(4) + 1(2) + 0(1) = 8 + 0 + 2 + 0 = 10₁₀
```

---

### 3. Decimal to Octal

#### Method: Repeated Division by 8
```
Example: Convert 493₁₀ to Octal

493 ÷ 8 = 61  remainder 5
61  ÷ 8 = 7   remainder 5
7   ÷ 8 = 0   remainder 7

Read remainders from bottom to top: 755₈

Verification: 7(64) + 5(8) + 5(1) = 448 + 40 + 5 = 493₁₀ ✓
```

---

### 4. Octal to Decimal

#### Method: Positional Notation
```
Example: Convert 755₈ to Decimal

Position:  8²   8¹   8⁰
Value:     7    5    5
Calculate: 7(64) + 5(8) + 5(1) = 448 + 40 + 5 = 493₁₀
```

---

### 5. Decimal to Hexadecimal

#### Method: Repeated Division by 16
```
Example: Convert 687₁₀ to Hexadecimal

687 ÷ 16 = 42  remainder 15 (F)
42  ÷ 16 = 2   remainder 10 (A)
2   ÷ 16 = 0   remainder 2

Read remainders from bottom to top: 2AF₁₆

Verification: 2(256) + 10(16) + 15(1) = 512 + 160 + 15 = 687₁₀ ✓
```

---

### 6. Hexadecimal to Decimal

#### Method: Positional Notation
```
Example: Convert 2AF₁₆ to Decimal

Position:  16²  16¹  16⁰
Value:     2    A(10) F(15)
Calculate: 2(256) + 10(16) + 15(1) = 512 + 160 + 15 = 687₁₀
```

---

### 7. Binary to Octal

#### Method: Group Binary Digits in Sets of 3
Binary to Octal conversion (right to left):
```
Example: Convert 101110₂ to Octal

Group into 3s from right: 101 | 110
Convert each group:
  101₂ = 5₈
  110₂ = 6₈

Result: 56₈
```

---

### 8. Octal to Binary

#### Method: Convert Each Digit to 3-bit Binary
```
Example: Convert 56₈ to Binary

5₈ = 101₂
6₈ = 110₂

Result: 101110₂
```

---

### 9. Binary to Hexadecimal

#### Method: Group Binary Digits in Sets of 4
```
Example: Convert 11010110₂ to Hexadecimal

Group into 4s from right: 1101 | 0110
Convert each group:
  1101₂ = D₁₆
  0110₂ = 6₁₆

Result: D6₁₆
```

---

### 10. Hexadecimal to Binary

#### Method: Convert Each Digit to 4-bit Binary
```
Example: Convert D6₁₆ to Binary

D₁₆ = 1101₂
6₁₆ = 0110₂

Result: 11010110₂
```

---

### 11. Octal to Hexadecimal

#### Method: Convert through Decimal or Binary
**Best Approach**: Octal → Binary → Hexadecimal

```
Example: Convert 56₈ to Hexadecimal

Step 1: Octal to Binary
5₈ = 101₂, 6₈ = 110₂
Result: 101110₂

Step 2: Binary to Hexadecimal (group by 4)
0010 | 1110
2₁₆  |  E₁₆

Result: 2E₁₆
```

---

### 12. Hexadecimal to Octal

#### Method: Convert through Binary
**Best Approach**: Hexadecimal → Binary → Octal

```
Example: Convert 2E₁₆ to Octal

Step 1: Hexadecimal to Binary
2₁₆ = 0010₂, E₁₆ = 1110₂
Result: 00101110₂ or 101110₂

Step 2: Binary to Octal (group by 3)
101 | 110
5₈  | 6₈

Result: 56₈
```

---

## Conversion Quick Reference Table

```
Decimal | Binary    | Octal | Hexadecimal
--------|-----------|-------|-------------
0       | 0000      | 0     | 0
1       | 0001      | 1     | 1
2       | 0010      | 2     | 2
3       | 0011      | 3     | 3
4       | 0100      | 4     | 4
5       | 0101      | 5     | 5
6       | 0110      | 6     | 6
7       | 0111      | 7     | 7
8       | 1000      | 10    | 8
9       | 1001      | 11    | 9
10      | 1010      | 12    | A
11      | 1011      | 13    | B
12      | 1100      | 14    | C
13      | 1101      | 15    | D
14      | 1110      | 16    | E
15      | 1111      | 17    | F
16      | 10000     | 20    | 10
32      | 100000    | 40    | 20
64      | 1000000   | 100   | 40
128     | 10000000  | 200   | 80
255     | 11111111  | 377   | FF
256     | 100000000 | 400   | 100
```

---

## Practice Problems

### Level 1: Basic (Beginner)

#### Binary Problems
1. Convert 5₁₀ to binary
2. Convert 1001₂ to decimal
3. Convert 11₂ to decimal
4. Convert 8₁₀ to binary
5. Convert 111₂ to decimal

#### Decimal-Octal Problems
6. Convert 64₁₀ to octal
7. Convert 25₈ to decimal
8. Convert 100₁₀ to octal
9. Convert 17₈ to decimal

#### Decimal-Hexadecimal Problems
10. Convert 255₁₀ to hexadecimal
11. Convert FF₁₆ to decimal
12. Convert 100₁₀ to hexadecimal
13. Convert A5₁₆ to decimal

---

### Level 2: Intermediate

#### Binary Conversions
1. Convert 156₁₀ to binary
2. Convert 10101010₂ to decimal
3. Convert 11110000₂ to decimal
4. Convert 255₁₀ to binary

#### Octal-Hexadecimal via Binary
5. Convert 345₈ to hexadecimal
6. Convert AB₁₆ to octal
7. Convert 7777₈ to hexadecimal
8. Convert FF₁₆ to octal

#### Mixed Conversions
9. Convert 500₁₀ to binary, octal, and hexadecimal
10. Convert 101010₂ to decimal, octal, and hexadecimal

---

### Level 3: Advanced

1. Convert 2048₁₀ to all three bases (binary, octal, hexadecimal)
2. Convert 11111111111111111111₂ to decimal
3. Convert DEADBEEF₁₆ to decimal
4. Find the largest value that can be represented with:
   - 8-bit binary
   - 3-digit octal
   - 2-digit hexadecimal
5. If a color code is #FF00FF (hexadecimal), what is the decimal value for each component?

---

## Answer Key (Level 1)

### Binary
1. 5₁₀ = **101₂**
2. 1001₂ = **9₁₀**
3. 11₂ = **3₁₀**
4. 8₁₀ = **1000₂**
5. 111₂ = **7₁₀**

### Octal
6. 64₁₀ = **100₈**
7. 25₈ = **21₁₀**
8. 100₁₀ = **144₈**
9. 17₈ = **15₁₀**

### Hexadecimal
10. 255₁₀ = **FF₁₆**
11. FF₁₆ = **255₁₀**
12. 100₁₀ = **64₁₆**
13. A5₁₆ = **165₁₀**

---

## Quick Reference

### Conversion Methods Summary

| From | To | Method |
|------|----|-----------:|
| Any | Decimal | Positional notation |
| Decimal | Any | Repeated division |
| Binary | Octal | Group by 3 |
| Octal | Binary | Convert each digit |
| Binary | Hex | Group by 4 |
| Hex | Binary | Convert each digit |
| Octal | Hex | Via binary |
| Hex | Octal | Via binary |

### Key Formulas

**Positional Notation Formula:**
```
Decimal Value = d_n × b^n + d_(n-1) × b^(n-1) + ... + d_1 × b¹ + d_0 × b⁰

Where:
- d = digit value
- b = base
- n = position (from right, starting at 0)
```

### Powers Reference

**Powers of 2** (for Binary)
2⁰=1, 2¹=2, 2²=4, 2³=8, 2⁴=16, 2⁵=32, 2⁶=64, 2⁷=128, 2⁸=256, 2⁹=512, 2¹⁰=1024

**Powers of 8** (for Octal)
8⁰=1, 8¹=8, 8²=64, 8³=512, 8⁴=4096, 8⁵=32768

**Powers of 16** (for Hexadecimal)
16⁰=1, 16¹=16, 16²=256, 16³=4096, 16⁴=65536

---

## Real-World Applications

### Binary
- Computer memory and storage
- Digital circuits and logic gates
- Data transmission (bits and bytes)
- Boolean logic in programming

### Octal
- Unix/Linux file permissions (chmod)
- Older computer systems
- Some assembly language code

### Hexadecimal
- Memory addresses in programming
- Color codes in web design (#RGB format)
- Unicode and character encoding
- Machine code and assembly language
- Network MAC addresses

### Decimal
- Human communication
- Financial transactions
- General mathematics
- Most programming at high level

---

## Common Mistakes to Avoid

1.  Forgetting to read binary remainders from **bottom to top**
2.  Confusing hexadecimal letters (A=10, B=11, etc.)
3.  Not grouping binary correctly (by 3 for octal, by 4 for hex)
4.  Forgetting leading zeros when grouping
5. Assuming 1+1=2 in binary (it's 10₂)
6.  Mixing up position values (not using correct powers)



## Summary

| System | Base | Digits | Use Case | Example |
|--------|------|--------|----------|---------|
| **Binary** | 2 | 0, 1 | Computing, Digital | 1010₂ = 10₁₀ |
| **Decimal** | 10 | 0-9 | Everyday | 42₁₀ |
| **Octal** | 8 | 0-7 | Unix Permissions | 755₈ = 493₁₀ |
| **Hexadecimal** | 16 | 0-9, A-F | Memory, Color | FF₁₆ = 255₁₀ |

**Master Conversions**: Practice converting between these systems regularly. Start with decimal as your reference point, then convert to others.

---

*Written by: Nimra Asif*
*Created for Educational Purposes*
