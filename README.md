*This project has been created as part of the 42 curriculum by khhammou, rmsaed*

# Description

Push_swap is a stack-based sorting program developed as part of the 42 Beirut curriculum. The goal of this project is to sort a list of integers using the smallest possible number of operations. The sorting must be done using only two stacks and a limited set of allowed operations (swap, push, rotate, and reverse rotate).

## Project Challenge

The main challenge of this project is to design efficient sorting algorithms while respecting strict constraints.

- We cannot use standard sorting functions
- We must minimize the number of operations to meet the evaluation criteria.

##  Program Workflow

The program starts by parsing and validating the input arguments.

- All numbers are checked for errors, duplicates, and overflow.
- After validation, the numbers are stored in a linked-list.
- Each number is assigned a rank, which simplifies comparisons and helps the algorithms work more efficiently.

## Supported Strategies

The program supports four different strategies:

1. Simple strategy

Used for small input sizes. It handles already sorted cases, two-element swaps, all possible cases of three numbers, and small reductions for slightly larger sets.

2. Medium strategy

Based on chunk sorting.
The numbers are divided into calculated chunks depending on the stack size.
Elements are moved between stacks according to their ranks to reduce unnecessary operations.

3. Complex strategy

Based on radix sort.
After ranking the numbers, the algorithm processes them bit by bit using their binary representation.
This strategy works efficiently for large input sizes.

4. Adaptive strategy

This mode automatically selects the best strategy based on the stack size and a calculated disorder value. The disorder metric helps estimate how unsorted the stack is before sorting begins.

## Additional Mode

Benchmark mode: prints useful information such as the disorder value, the selected strategy,complexity, and the total number of operations.

# Implementation Focus

This implementation focuses on efficiency, clear structure, modular design, and full respect of the push_swap project constraints.

## Algorithm Explanation & Justification

The goal of this project is to minimize the number of operations while respecting the strict push_swap constraints. Since input sizes vary, I implemented multiple strategies and an adaptive system instead of relying on a single algorithm.

## Rank Assignment

Before sorting, all numbers are converted into ranks based on their sorted order. This simplifies comparisons, avoids issues with large or negative values, and allows the radix algorithm to work efficiently.

1. Simple Strategy

This strategy is used for small input sizes.

It directly handles trivial cases (already sorted, two elements, three elements) and reduces slightly larger small sets by isolating minimum values before final sorting.

This approach guarantees minimal operations for small datasets and avoids unnecessary complexity.

2. Medium Strategy (Chunk-Based)

For medium-sized inputs, the stack is divided into calculated chunks based on its size. Elements are moved between stacks according to their rank ranges.

This reduces unnecessary rotations and improves operation count compared to basic selection-based approaches. It provides balanced performance for mid-range inputs.

3. Complex Strategy (Radix Sort)

For large inputs, I implemented a radix sort based on the binary representation of ranks. The algorithm processes numbers bit by bit and distributes them between the two stacks accordingly.

Radix sort was chosen because it provides predictable performance and scales efficiently for large datasets while respecting push_swap constraints.

4. Adaptive Strategy

The adaptive mode selects the most suitable algorithm automatically. The decision is based on stack size and a calculated disorder metric that estimates how unsorted the input is.

# Instructions

This project is written in C and designed to run on Unix-based systems. To compile the program, a standard C compiler such as cc or gcc is required. The project also uses an included libft library for utility functions.

##  Compilation

To compile the program, use the following commands in the project root:
1. make – Compile the push_swap program
2. make clean – Remove object files
3. make fclean – Remove object files and the executable
4. make re – Recompile after cleaning

## Usage

The program is executed from the command line by providing a list of integers:

./push_swap 2 1 3
./push_swap "3 2 1 5 4"

Both separate arguments and a single quoted string are accepted.

Available Flags

The program supports several optional flags:

### Strategy selection – Choose a specific sorting strategy:

./push_swap -simple 3 2 1
./push_swap -medium 5 2 4 1 3
./push_swap -complex 10 3 8 5 1

Adaptive mode – Automatically selects the best strategy based on stack size and disorder:

./push_swap -adaptive 5 4 3 2 1

Benchmark mode – Prints the disorder value, selected strategy, and total number of operations:

./push_swap -bench 5 1 4 2 3

# Resources

- C standard library documentation (man pages)
- 42 Libft project functions
- Radix sort algorithm references: https://en.wikipedia.org/wiki/Radix_sort
- Stack-based sorting tutorials
- AI assistance was used for planning algorithm explanations and improving README clarity.

