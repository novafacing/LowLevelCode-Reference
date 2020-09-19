# Low-Level Reference Code

Introduction to Assembly.

## Assembly

`Assembly` is the mapping of code instructions of a processor into a representation that is easy for humans to understand.

Each processor offers a variety of technologies that can be used through certain instructions. A group of instructions (Instruction Set) can be very specific and different from other processors.

Assembly is a collection of words, also called `Mnemonic`, which represent processor instructions. There is no set rule that states the naming of a Mnemonic so that the same type of instruction can be represented differently in Assembly for different processors.

In short, assembly is a low-level language specifically designed for a particular processor family that represents instructions with symbolic code.

## Advantages

Understanding assembly language provides advantages, not only for Reverse Engineering but also Development. Mastery of assembly provides understanding of:

- how the processor accesses and executes instructions
- how the instructions access and process data
- how data is represented in memory
- how the program interacts with the OS, processor, and other devices.

Understanding Assembly instructions can assist in complex and tricky code analysis (eg obfuscation).

## Data Size

The processor operates to calculate data with a fixed size. This size is different for each processor. Terms such as `64-bit processor` or` 32-bit processor` refer to the size of data that an operation can operate.

In general, there are several terms to describe chunks of data.

- Byte: 8-bit
- Word: 2-byte, 16-bit
- Dword: double-word, 4-byte, 32-bit
- Qword: quadruple word, 8-byte, 64-bit

## Instruction Length

There is no limit to the length of an instruction. Some architectures have fixed length instructions (the same for every other instruction). While other architectures apply variable-length instructions, where the length of an instruction can consist of one or more bytes.

## Execution Cycle

The execution of an instruction stored in memory requires several stages. This stage is known as the `Execution Cycle`. The implementation of the execution cycle can differ depending on the architecture. There are generally 3 stages to execute an instruction:

- * fetch *: retrieves instructions from memory with a string representation of bytes.
- * decode *: decode translates code as instructions that will be translated by the processor.
- * execute *: execute instructions and give result.

For simple processors, instruction execution is carried out sequentially with one Execution Cycle being executed after the previous Execution Cycle has been completed. In most modern processors, the Execution Cycle is carried out concurrently and even in parallel, via the `Instruction Pipeline`. An Execution Cycle can be started while the previous Execution Cycle is being processed (without waiting for completion).
