# Low-Level Reference Code

Open repository for low-level code learning.

### Overview

This repository collects low-level code learning information (assembly, bytecode, immediate representation, etc.) for various architectures, platforms, and dialects. The scope of this repository is not only limited to the processor (hardware), but also extends to include various virtual machine processes such as JVM (Java Bytecode), CLR (.Net CIL), LLVM IR, etc.

All code included in this reposiotry provides instructions for compiling.

### About Low-Level Code

`Low-level code` (low-level code) is an abstraction of a group of instructions from a processor to give orders and process data according to the capabilities given by each processor. The word "low" refers to a minimalistic level of abstraction between the language and the processor's native instructions.

The term `processor` in this repository refers to a general term for hardware (microprocessor, microcontroller) or software (interpreter, process virtual machine, p-code machine) that executes certain code to process data.

The instructions discussed are low-level instructions that are understood by each processor with a scope of instructions for performing data transfers, arithmetic operations, checking conditions, etc.

Low-Level Code (Assembly, IR, IL etc.) is a key language in Reverse Engineering.

### Disclaimer

This repository is an initiative of the Reversing.ID community to introduce and explore low-level code.

Reversing.ID is not affiliated with any device vendor or manufacturer. This repository has the main purpose of learning materials for low-level code and assembly.

### Structure and Content

The repository is divided into sections with different directories.

- Codes
- References
- Tools

_Codes_ is a collection of code snippets specific to each low-level code. This directory provides a bottom-up view of assembly language where assemblies are viewed as building blocks. The distribution of directory code is based on the platform (processor, VM, etc.). Each platform will have one or more variants or dialects to compile.

_References_ is a set of references in the form of articles, writings, journals, etc. which provide an understanding of a low-level code. This directory generally contains the main references issued by each vendor.

_Tools_ is a section that specifically summarizes a list of tools used for low-level code analysis or utilizing low-level code for other analyzes. Although it doesn't cover the details of using each tool, this directory outlines the capabilities and potential of each tool.

### How to Download?

The repository can be downloaded in its entirety or the code can be downloaded separately.

### How to Contribute?

This is an open project.

You can contribute code for unregistered architectures, add or modify existing code to provide better information.

What you have to do:

- do a pull request.
- send an email to the management [at] reversing.id
- notified on telegram @ReversingID
