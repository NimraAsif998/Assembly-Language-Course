# Memory Hierarchy

## Introduction

**Memory Hierarchy** is the organization of different storage devices in a computer system according to their **speed, cost, and storage capacity**.

The main purpose of memory hierarchy is to provide the processor with fast access to data while keeping the overall cost of the system low.

The memories that are faster are usually smaller and more expensive, whereas slower memories are larger and cheaper.

---

# Memory Hierarchy Design

The memory hierarchy is designed based on the following principles:

1. **Speed**

   * Frequently used data should be stored in faster memory.

2. **Cost**

   * Fast memory is expensive, so only a small amount is used.

3. **Capacity**

   * Slower memories provide larger storage capacity.

4. **Locality of Reference**

   * Programs tend to access the same data repeatedly.
   * This principle improves memory performance.

---

## Characteristics of Memory Hierarchy

| Memory Type       | Speed     | Cost      | Capacity   |
| ----------------- | --------- | --------- | ---------- |
| Registers         | Very High | Very High | Very Small |
| Cache Memory      | High      | High      | Small      |
| Main Memory (RAM) | Moderate  | Moderate  | Medium     |
| Secondary Memory  | Low       | Low       | Large      |

---

# Types of Memory Hierarchy

Memory hierarchy is generally divided into two major categories:

## 1. Primary Memory

Primary memory is directly accessible by the CPU.

Examples:

* Registers
* Cache Memory
* RAM
* ROM

### Features

* Fast access speed
* Expensive
* Smaller storage capacity

---

## 2. Secondary Memory

Secondary memory is used for permanent storage.

Examples:

* Hard Disk Drive (HDD)
* Solid State Drive (SSD)
* USB Flash Drive
* CD/DVD

### Features

* Large storage capacity
* Low cost
* Slower than primary memory

---

# Levels of Memory Hierarchy

The memory hierarchy consists of multiple levels.

## Level 1: Registers

Registers are located inside the CPU.

### Characteristics

* Fastest memory in the computer.
* Very small storage capacity.
* Used to store immediate data and instructions.

### Examples

```text id="j8chm4"
AX, BX, CX, DX
```

---

## Level 2: Cache Memory

Cache memory is located between the CPU and main memory.

### Characteristics

* Faster than RAM.
* Stores frequently used data.
* Reduces CPU waiting time.

---

## Level 3: Main Memory (RAM)

Main memory stores currently executing programs and data.

### Characteristics

* Volatile memory.
* Directly accessed by CPU.
* Larger than cache memory.

---

## Level 4: Secondary Memory

Secondary memory provides permanent storage.

### Examples

* HDD
* SSD

### Characteristics

* Non-volatile memory.
* Large storage capacity.
* Slower access speed.

---

## Level 5: Tertiary Storage (Optional)

Used for backup and archival purposes.

### Examples

* Magnetic Tapes
* Optical Disks

---

# Memory Hierarchy Diagram

```text id="o3kz1d"
            Fastest
               ▲
               |
        +---------------+
        |   Registers   |
        +---------------+
               |
        +---------------+
        | Cache Memory  |
        +---------------+
               |
        +---------------+
        | Main Memory   |
        |    (RAM)      |
        +---------------+
               |
        +---------------+
        | Secondary     |
        | Memory        |
        +---------------+
               |
        +---------------+
        | Tertiary      |
        | Storage       |
        +---------------+
               |
               ▼
            Slowest
```

---

# Cache Memory

## Introduction

**Cache Memory** is a high-speed memory located between the CPU and the main memory (RAM).

It stores frequently accessed data and instructions so that the CPU can access them quickly.

Because cache memory is much faster than RAM, it significantly improves the overall performance of the computer.

---

## Need for Cache Memory

The CPU operates much faster than main memory. If the CPU has to wait for data from RAM, system performance decreases.

Cache memory solves this problem by storing frequently used information close to the CPU.

---

## Working of Cache Memory

1. CPU requests data.
2. Cache memory checks whether the data is available.

### Cache Hit

If the requested data is found in cache memory, it is called a **Cache Hit**.

```text id="c6z0kn"
CPU → Cache → Data Found
```

The data is immediately sent to the CPU.

---

### Cache Miss

If the data is not found in cache memory, it is called a **Cache Miss**.

```text id="ewtlnh"
CPU → Cache → RAM
```

The data is fetched from RAM and then stored in cache for future use.

---

# Levels of Cache Memory

Modern processors typically contain three levels of cache memory.

## L1 Cache (Level 1)

* Located inside the CPU.
* Fastest cache memory.
* Smallest in size.

---

## L2 Cache (Level 2)

* Larger than L1.
* Slightly slower than L1.

---

## L3 Cache (Level 3)

* Shared among processor cores.
* Larger than L1 and L2.
* Slower than L1 and L2.

---

# Advantages of Cache Memory

* Increases CPU performance.
* Reduces memory access time.
* Minimizes CPU waiting time.
* Improves overall system efficiency.

---

# Disadvantages of Cache Memory

* Expensive compared to RAM.
* Limited storage capacity.

---

# Summary

| Memory Level     | Speed     | Capacity   | Cost      |
| ---------------- | --------- | ---------- | --------- |
| Registers        | Very High | Very Small | Very High |
| Cache Memory     | High      | Small      | High      |
| RAM              | Moderate  | Medium     | Moderate  |
| Secondary Memory | Low       | Large      | Low       |

| Cache Level | Characteristics                |
| ----------- | ------------------------------ |
| L1          | Fastest and smallest           |
| L2          | Larger and slower than L1      |
| L3          | Largest and shared among cores |

**Memory hierarchy is an essential concept in computer architecture because it balances speed, cost, and storage capacity, ensuring efficient system performance.**
