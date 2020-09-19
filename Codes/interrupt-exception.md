# Low-Level Reference Code

Introduction to Interrupt & Exception

## Interrupt

An interrupt is a signal from an external device (generally I / O) to the processor as a sign that there is an event that must be handled by the processor.

The occurrence of an interrupt does not change the execution flow of a program.

When the processor gets an Interrupt, the processor will pause all the ongoing execution then look for the appropriate handler in the Interrupt Table to handle the Interrupt. Furthermore, normal execution will continue.

## Exception

Exceptions are signals that are generated when an error or anomalous condition occurs during instruction execution. Some of the common errors or anomalies include zero division, illegal memory access, etc.

The occurrence of an exception has the possibility to change the execution flow of a program.

Exceptions are of three types: Fault, Trap, and Abort.
