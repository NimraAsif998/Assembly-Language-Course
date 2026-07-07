# Number Systems - Quick Reference Cheat Sheet

## Visual Conversion Method

```
        ┌─────────────────────────────────────┐
        │      START WITH DECIMAL            │
        └─────────────────────────────────────┘
                    ↓
        ┌─────────────────────────────────────┐
        │  Repeated Division by Base          │
        │  Write Remainders Bottom to Top     │
        └─────────────────────────────────────┘
                    ↓
        ┌─────────────────────────────────────┐
        │  Binary / Octal / Hexadecimal       │
        └─────────────────────────────────────┘
```

## 1-Minute Conversion Guide

###  Decimal → Binary
```
Divide by 2, collect remainders
13 ÷ 2 = 6 R 1
6 ÷ 2 = 3 R 0
3 ÷ 2 = 1 R 1
1 ÷ 2 = 0 R 1
Answer: 1101₂ (read from bottom)
```

###  Binary → Decimal
```
Multiply each digit by its power of 2, then add
1101₂ = 1(8) + 1(4) + 0(2) + 1(1) = 13₁₀
```

###  Decimal → Hexadecimal
```
Divide by 16, collect remainders (remember A-F)
255 ÷ 16 = 15 R 15
15 ÷ 16 = 0 R 15
Answer: FF₁₆ (F = 15)
```

###  Hexadecimal → Decimal
```
Multiply each digit by its power of 16, then add
FF₁₆ = 15(16) + 15(1) = 240 + 15 = 255₁₀
```

## Binary ↔ Hexadecimal Quick Conversion

```
Hex Digit → 4-bit Binary (and vice versa)

0=0000  4=0100  8=1000  C=1100
1=0001  5=0101  9=1001  D=1101
2=0010  6=0110  A=1010  E=1110
3=0011  7=0111  B=1011  F=1111
```

**Example**: 1A₁₆ → ?₂
- 1 = 0001
- A = 1010
- Answer: 00011010₂

## Binary ↔ Octal Quick Conversion

```
Octal Digit → 3-bit Binary (and vice versa)

0=000  2=010  4=100  6=110
1=001  3=011  5=101  7=111
```

**Example**: 56₈ → ?₂
- 5 = 101
- 6 = 110
- Answer: 101110₂

## All Number Systems at a Glance

| Decimal | Binary | Octal | Hexadecimal |
|---------|--------|-------|-------------|
| 0       | 0      | 0     | 0           |
| 1       | 1      | 1     | 1           |
| 2       | 10     | 2     | 2           |
| 3       | 11     | 3     | 3           |
| 4       | 100    | 4     | 4           |
| 5       | 101    | 5     | 5           |
| 6       | 110    | 6     | 6           |
| 7       | 111    | 7     | 7           |
| 8       | 1000   | 10    | 8           |
| 9       | 1001   | 11    | 9           |
| 10      | 1010   | 12    | A           |
| 11      | 1011   | 13    | B           |
| 12      | 1100   | 14    | C           |
| 13      | 1101   | 15    | D           |
| 14      | 1110   | 16    | E           |
| 15      | 1111   | 17    | F           |
| 16      | 10000  | 20    | 10          |
| 32      | 100000 | 40    | 20          |
| 64      | 1000000| 100   | 40          |
| 128     | 10000000| 200  | 80          |
| 255     | 11111111| 377  | FF          |
| 256     | 100000000| 400 | 100         |

## Key Powers to Remember

### Powers of 2 (Binary)
```
2⁰ = 1        2⁵ = 32
2¹ = 2        2⁶ = 64
2² = 4        2⁷ = 128
2³ = 8        2⁸ = 256
2⁴ = 16       2¹⁰ = 1024
```

### Powers of 8 (Octal)
```
8⁰ = 1
8¹ = 8
8² = 64
8³ = 512
8⁴ = 4096
```

### Powers of 16 (Hexadecimal)
```
16⁰ = 1
16¹ = 16
16² = 256
16³ = 4096
16⁴ = 65536
```

## Color Codes in Hexadecimal

```
#RRGGBB where R=Red, G=Green, B=Blue

#FF0000 = Pure Red
#00FF00 = Pure Green
#0000FF = Pure Blue
#FFFFFF = White
#000000 = Black
#FFFF00 = Yellow (Red + Green)
#FF00FF = Magenta (Red + Blue)
#00FFFF = Cyan (Green + Blue)
```

## File Permissions in Octal

```
chmod 755 filename

7 = 4+2+1 = rwx (Read + Write + Execute)
5 = 4+0+1 = r-x (Read + Execute)
5 = 4+0+1 = r-x (Read + Execute)

First digit = Owner permissions
Second digit = Group permissions
Third digit = Others permissions
```

## Common Mistakes & Fixes

|  Wrong |  Correct | Why |
|---------|-----------|-----|
| Reading remainders top→bottom | Read remainders bottom→top | Positional value increases downward |
| 1₂ + 1₂ = 2₂ | 1₂ + 1₂ = 10₂ | Binary only has 0 and 1 |
| Hex A = 11 | Hex A = 10 | A starts at 10, not 11 |
| 1111₂ = 15₂ | 1111₂ = 15₁₀ | Result is decimal, not binary |
| 8₈ valid | 8₈ invalid | Octal only uses 0-7 |
| G₁₆ valid | G₁₆ invalid | Hex only uses 0-9, A-F |

## Conversion Decision Tree

```
I have a Decimal number:
├─ To convert to Binary? → Divide by 2 repeatedly
├─ To convert to Octal? → Divide by 8 repeatedly
└─ To convert to Hex? → Divide by 16 repeatedly

I have a Binary number:
├─ To convert to Decimal? → Multiply by powers of 2
├─ To convert to Octal? → Group 3 binary digits
└─ To convert to Hex? → Group 4 binary digits

I have an Octal number:
├─ To convert to Decimal? → Multiply by powers of 8
├─ To convert to Binary? → Convert each digit to 3 bits
└─ To convert to Hex? → Convert to binary first, then to hex

I have a Hex number:
├─ To convert to Decimal? → Multiply by powers of 16
├─ To convert to Binary? → Convert each digit to 4 bits
└─ To convert to Octal? → Convert to binary first, then to octal
```

## Pro Tips for Students

1. **Always use decimal as your reference point** - If unsure, convert to decimal first
2. **Learn powers of 2** - They're the foundation of binary
3. **Binary ↔ Hex shortcut** - 4 bits = 1 hex digit (memorize the table)
4. **Binary ↔ Octal shortcut** - 3 bits = 1 octal digit (memorize the table)
5. **Practice online converters** - Verify your answers at converters first, then solve by hand
6. **Write positions clearly** - Label your position values to avoid mistakes
7. **Double-check remainders** - Most errors come from division mistakes

## Real-World Applications Summary

| System | Real-World Use |
|--------|----------------|
| **Binary** | RAM, disk storage, data transmission |
| **Decimal** | Counting, money, everyday life |
| **Octal** | Unix file permissions (chmod) |
| **Hexadecimal** | Memory addresses, colors, Unicode |

## Need More Help?

### Common Questions

**Q: Why do we need different number systems?**
A: Different systems are optimal for different purposes. Binary matches computer hardware, hex is compact for humans reading computer data.

**Q: Do I need to memorize all conversions?**
A: No, but learn the method and practice powers of bases. A calculator can help verify.

**Q: What's the largest number in 8 bits?**
A: 11111111₂ = 255₁₀ = 377₈ = FF₁₆

**Q: Why is hex used for memory addresses?**
A: Because it's more compact than binary and easier to read than long strings of 0s and 1s.

---

**Keep this sheet handy while practicing!**

*Created for quick reference during problem-solving*
* Written by: NimraAsif*
