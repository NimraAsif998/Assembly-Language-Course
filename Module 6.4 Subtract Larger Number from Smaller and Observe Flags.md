# Module 6.4: Subtract Larger Number from Smaller and Observe Flags

## Introduction

When a larger number is subtracted from a smaller number, the result becomes negative. In Assembly language, the processor automatically updates the **Flag Register** to indicate the status of the result.

In this module, we will subtract a larger number from a smaller number and observe the affected flags.

---

## Program: Subtract a Larger Number from a Smaller Number

```assembly id="n9it1w"
.model small
.stack 100h

.code
main proc

    mov al, 5      ; Load first number
    sub al, 10     ; Subtract larger number

    ; After execution:
    ; AL = FBh (-5 in signed form)
    ; CF = 1
    ; SF = 1

    mov ah, 4Ch
    int 21h

main endp
end main
```

---

## Explanation

1. The instruction `mov al, 5` loads the value **5** into register **AL**.
2. The instruction `sub al, 10` subtracts **10** from **5**.
3. Since `5` is smaller than `10`, the result becomes **-5**.
4. In 8086, negative numbers are represented using **2's complement** notation.
5. Therefore, the value stored in `AL` becomes `FBh`, which represents **-5**.

---

## Flags Affected

### Carry Flag (CF)

The **Carry Flag** is set because a borrow is required during subtraction.

```text id="7m6a2f"
CF = 1
```

### Sign Flag (SF)

The **Sign Flag** is set because the result is negative.

```text id="0g2k72"
SF = 1
```

### Zero Flag (ZF)

The **Zero Flag** remains cleared because the result is not zero.

```text id="nbo7nf"
ZF = 0
```

---

## Observing Flags in EMU8086

1. Load the program in **EMU8086**.
2. Execute the instructions using **Single Step (F8)**.
3. Observe the values of the flags after the `SUB` instruction.
4. Notice that:

   * `CF = 1`
   * `SF = 1`
   * `ZF = 0`

---

## Another Example

```assembly id="a93b8n"
.model small
.stack 100h

.code
main proc

    mov al, 3
    sub al, 8

    ; Result:
    ; AL = FBh (-5)
    ; CF = 1
    ; SF = 1

    mov ah, 4Ch
    int 21h

main endp
end main
```

### Explanation

* `3 - 8 = -5`
* Since the result is negative:

  * **CF = 1** (borrow occurred)
  * **SF = 1** (negative result)
  * **ZF = 0** (result is not zero)

---

## Summary of Observed Flags

| Flag   | Value | Reason                             |
| ------ | ----- | ---------------------------------- |
| **CF** | 1     | Borrow occurred during subtraction |
| **SF** | 1     | Result is negative                 |
| **ZF** | 0     | Result is not zero                 |

### Sample Observation

```text id="ag5i6z"
5 - 10 = -5

AL = FBh
CF = 1
SF = 1
ZF = 0
```

**Subtracting a larger number from a smaller number helps us understand how negative numbers and flags work in Assembly language. Practice these examples in EMU8086 to observe the behavior of flags.**
