# 0x19. C - Stacks, Queues - LIFO, FIFO

## Overview

This project focuses on implementing stacks and queues in C, covering the concepts of Last In, First Out (LIFO) and First In, First Out (FIFO). The goal is to create an interpreter for Monty ByteCodes files, a scripting language first compiled into Monty byte codes. The project involves working with doubly linked list representations of stacks and queues and understanding the common implementations and use cases of these data structures.

## Learning Objectives

By the end of this project, you should be able to:

- Understand the concepts of LIFO and FIFO.
- Implement stacks and queues in C using doubly linked lists.
- Work with global variables in a proper way.
- Create an interpreter for Monty ByteCodes files.
- Handle errors and edge cases in file parsing and memory allocation.

## Requirements

### General

- **Allowed editors:** vi, vim, emacs
- **Compiler options:** -Wall -Werror -Wextra -pedantic -std=c89
- A README.md file at the root of the folder is mandatory.
- Code should follow the Betty style, checked using betty-style.pl and betty-doc.pl.
- Allowed to use a maximum of one global variable.
- No more than 5 functions per file.
- Allowed to use the C standard library.
- The prototypes of all functions should be included in the header file called `monty.h`.
- Don’t forget to push your header file.
- All header files should be include guarded.

### Monty Program

- **Usage:** `monty file` where file is the path to the file containing Monty byte code.
- If the user does not provide a file or provides more than one argument, print the error message `USAGE: monty file`, followed by a new line, and exit with status `EXIT_FAILURE`.
- If it's not possible to open the file, print the error message `Error: Can't open file <file>`, followed by a new line, and exit with status `EXIT_FAILURE`.
- If the file contains an invalid instruction, print the error message `L<line_number>: unknown instruction <opcode>`, followed by a new line, and exit with status `EXIT_FAILURE`.
- Line numbers always start at 1.
- If malloc fails, print the error message `Error: malloc failed`, followed by a new line, and exit with status `EXIT_FAILURE`.
- Use only malloc and free; do not use any other functions from `man malloc` (realloc, calloc, …).

## Data Structures

Please use the following data structures for this project. Include them in your header file:

```c
/**
 * struct stack_s - doubly linked list representation of a stack (or queue)
 * @n: integer
 * @prev: points to the previous element of the stack (or queue)
 * @next: points to the next element of the stack (or queue)
 *
 * Description: doubly linked list node structure
 * for stack, queues, LIFO, FIFO
 */
typedef struct stack_s
{
        int n;
        struct stack_s *prev;
        struct stack_s *next;
} stack_t;

/**
 * struct instruction_s - opcode and its function
 * @opcode: the opcode
 * @f: function to handle the opcode
 *
 * Description: opcode and its function
 * for stack, queues, LIFO, FIFO
 */
typedef struct instruction_s
{
        char *opcode;
        void (*f)(stack_t **stack, unsigned int line_number);
} instruction_t;

