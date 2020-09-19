# Low-Level Reference Code

General Overview of Control Flow Program

## What is Control Flow?

`Control flow` or flow of control is setting the sequence of execution or evaluation of instructions (statements).

## Categories

In general, control-flow can be categorized by effect:

- Pass instructions execution to a different location (unconditional jump)
- Execute a group of instructions when a condition is met (choice or branch)
- Execute a group of instructions zero or more times under certain conditions (loop, modification of conditional jumps).
- Execute a group of instructions as a single action (subroutine, function).
- Stops the program, preventing further execution.

## Primitives

To be able to change the flow of instruction execution, there are at least two components in assembly language (as well as many other low-level code), namely:

- * Jumps *: statement to change positions, either unconditional or conditional.
- * Labels *: names or numbers that are explicitly given to a certain position in the code so that it can be used as a reference to move so that the next execution will start from that position.

## Branch

Branching is the act of changing a location or sequence to a line of instructions at another location as a result of a condition evaluation.

When viewed from a high-level language perspective, there are several branching models, including:

- If-Then- (Else)
- Switch-Case

### If-Then- (Else) Statements

Branching which leads to a group of instructions if the conditions are met. Branching can also consist of several alternative actions, each with complementary conditions.

### Switch-Case Statements

Branching with a variety of alternative conditions based on value. A Jump Table is used to define the target block to be executed when jumping.

## Loops

Loops are a variation of branching. Loop is a series of instructions that are written once but can be executed many times in succession.

When viewed from the side of high-level language, there are several looping models, including:

- For (Count-Controlled Loop)
- While (Condition-Controlled Loop)

### Count-Controlled Loops

The controlled loop uses a counter to execute the block multiple times. The counter value changes over time with each loop step bringing the counter closer to a threshold value.

### Condition-Controlled Loops

Loop controlled by condition evaluation. Repetition occurs when a condition is met. Condition evaluation can be done at the beginning or at the end of the loop block.
