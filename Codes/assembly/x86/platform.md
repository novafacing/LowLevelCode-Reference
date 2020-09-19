# Low-Level Reference Code

x86 Platform Specific Information

## Data Size

The term used to refer to the size of data that the processor can operate in each cycle.

In general, there are several terms in x86 to describe chunks of data.

- Byte: 8-bit
- Word: 2-byte, 16-bit
- Dword: double-word, 4-byte, 32-bit
- Qword: quadruple word, 8-byte, 64-bit

## Registers

A register is a part of the processor that is used to hold temporary data in the calculation process. The register is a special container and can be accessed very quickly by the processor (more precisely the ALU component in the processor).

x86 has several registers, including:

* General Purposes Register (32-bit and 64-bit)
    - Registers data
        - EAX / RAX: Accumulator
        - EBX / RBX: Base address for memory access
        - ECX / RCX: Counter
        - EDX / RDX: Data
    - Pointer Registers
        - ESP / RSP: Stack Pointer
        - EBP / RBP: Base Pointer
    - Index Registers
        - ESI / RSI: Source Index
        - EDI / RDI: Destination Index
* Segment Registers (limited access)
    - CS: Code
    - DS: Data
    - SS: Stack
    - ES: Extra
    - FS: Extra
    - GS: Extra
* Status / Control Registers
    - Control Registers (limited access): CR0 to CR4
    - Debug Registers (limited access): DR0 to DR3
    - Other Registers (no direct access)
        - EIP: Instruction pointer
        - EFLAGS: Flags
* XMM Registers: XMM0 to XMM15

#### General Purpose Register

The x86 architecture has several registers that are divided into categories. General Purpose Register is a group of registers that can be used to store anything and any purposes. However, each of them initially has a specific purpose / function but becomes imperative to obey. GPR can be divided into three register categories: Data Registers, Pointer Registers, and Index Registers.

`EAX / RAX` is also called the Accumulator. Often used for I / O related operations, math operations, and interrupts. `EBX / RBX` is the Base address which is used as the Base pointer for memory access. `ECX / RCX` is a counter, often used in loops that require counters. `EDX / RDX` is Data, similar to EAX / RAX and is used as an extension when performing math operations.

32-bit registers have the prefix E, for example EAX. While 64-bit registers have the prefix R, for example RAX. For some registers (EAX, EBX, ECX, EDX), we can access the bottom of the register by removing the prefix. So that:

- EAX (32-bit) -> AX (16-bit)
- EBX (32-bit) -> BX (16-bit)
- ECX (32-bit) -> CX (16-bit)
- EDX (32-bit) -> DX (16-bit)

Register start function

Furthermore, we can access the upper half and lower half of AX / BX / CX / DX by replacing X with H (Higher half) or L (Lower half). So that:

- AX (16-bit) = AH (8-bit) | AL (8-bit)
- BX (16-bit) = BH (8-bit) | BL (8-bit)
- CX (16-bit) = CH (8-bit) | CL (8-bit)
- DX (16-bit) = DH (8-bit) | DL (8-bit)

We can illustrate it like this:

``
    RAX EAX AX
    --------------------------------------------
    | | | AH | AL |
    --------------------------------------------
    64 32 16 8 0
``

For x86-64 (or x64), there are additional registers from R8 to R15. Registers R0 through R7 have other identities for existing register names, such as:

- R0 = RAX
- R1 = RCX
- R2 = RDX
- R3 = RBX
- R4 = RSP
- R5 = RBP
- R6 = RSI
- R7 = RDI

To access the lower half (32-bit) of the R- register, we can pass the suffix D (DWord). The lower half again can be accessed with the suffix W (Word). The illustration can be seen below:

``
    R8 R8D R8W R8B
    --------------------------------------------
    | | | | |
    --------------------------------------------
    64 32 16 8 0
``

#### Segment Registers

`Segment Register` is a group of registers that are used to access the memory segment. Segment itself is a part of memory that is a multiple of the Page. Each segment has its own function.

The segment designated by the Segment Register is important as long as the application is running. `CS` contains Code Segment, refers to the location of the code / program instructions. `DS` contains Segment Data, refers to the location of the accessed data. `ES`,` FS`, `GS` are additional Segment Registers commonly used by the OS. For example, `GS` is used by Windows to designate special (OS specific) data structures.

#### Control Registers

`Control Register` is a group of registers that can change or control the behavior of the processor (core). Each control register has a specific purpose.

#### Debug Registers

The `Debug Register` is a group of registers used by the processor for hardware debugging. There are actually six debug registers: DR0, DR1, DR2, DR3, DR4 / DR6, DR5 / DR7. The debug register will contain addresses that are watched as breakpoints on the hardware side.

#### Instruction Pointer

The `Instruction Pointer Register` is a register that points to the memory address where the next instruction will be executed. Also called the `` Program Counter (PC) '' on several other architectures. There is only one register for this which is EIP (or RIP for 64-bit).

EIP (or RIP) cannot be modified directly. There are no instructions that can replace the EIP.

#### EFLAGS

`EFLAGS` is a register which is a collection of big-bit flags. Lots of instructions. like comparisons and math calculations, have side effects. The side effects of each of these operations are represented by flag bits. Changes in these bits can affect other instructions such as conditional tests as a reference for performing control-flow.

Common flags include:

``
    Flag: O D I T S Z A P C
                -------------------------------------------------- -------------------------------
    Bit Flag | 31 | 30 | 29 | 28 | 27 | 26 | 25 | 24 | 23 | 22 | 21 | 20 | 19 | 18 | 17 | 16 |
                -------------------------------------------------- -------------------------------

    Flag: O D I T S Z A P C
                -------------------------------------------------- -------------------------------
    Bit Flag | 15 | 14 | 13 | 12 | 11 | 10 | 9 | 8 | 7 | 6 | 5 | 4 | 3 | 2 | 1 | 0 |
                -------------------------------------------------- -------------------------------
``

| -------- | -------- | ------------------------------ |
| Bit | FLAG | Description |
| -------- | -------- | ------------------------------ |
| 0 | CF | Carry Flag |
| 2 | PF | Parity Flag |
| 4 | AF | Auxiliary Carry Flag |
| 6 | ZF | Zero Flag |
| 7 | SF | Sign Flag |
| 8 | TF | Trap Flag |
| 9 | IF | Interrupt Flag |
| 10 | DF | Direction Flag |
| 11 | OF | Overflow Flag |
| 12-13 | IOPL | I / O Priviledge Level |
| 14 | NT | Nested Task Flag |
| 16 | RF | Resume Flag |
| 17 | VM | Virtual 8086-mode Flag |
| 18 | AC | Algignment Check |
| 19 | VIF | Virtual Interrupt Flag |
| 20 | VIP | Virtual Interrupt Pending |
| 21 | ID | ID Flag |
| -------- | -------- | ------------------------------ |

#### MMX

Included in an additional Instruction Set not present in the early x86 generation. Most of the instructions are SIMD (Single Instruction Multiple Data), which means that one instruction can work with several data in parallel.

There are 8 MM of 64-bit registers, from MM0 to MM7. The eight registers overlap with the FPU register. This means that MMX and FPU instructions cannot be used simultaneously.

Each register is 64-bit in size but can be broken down into several, namely:

* 2x 32-bit value
* 4x 16-bit value
* 8x 8-bit value

MMX implements the * Saturation Arithmetic * technique. In this technique, the register value never exceeds 0 if an overflow occurs. The value will also not change to MAX value if an underflow occurs. In other words, this situation will occur:

``
255 | 100 = 255
200 | 100 = 255
0 - 100 = 0
99 - 100 = 0
``

This may seem strange to some people who are accustomed to using the General Purpose Register. But in certain cases, it is useful. For example, to make the color lighter, the overflow should not occur so that it can change the light color to dark instantly.

#### SSE (Streaming SIMD Extensions)

`SSE` is a register for floating point operations. The size of this register is 128-bit. But this register is not only used for fractional operations but can also be used for various data sizes and different types.

There are 8 128-bit SSE registers, from XMM0 to XMM7. Unlike MMX, SSE does not overlap the floating point stack.

The 128-bit register can be broken down into several parts, namely:

* 2x 64-bit floating points (double-precision)
* 2x 64-bit integers
* 4x 32-bit floating points (single-precision)
* 4x 32-bit integers
* 8x 16-bit integers
* 16x 8-bit characters (bytes)
