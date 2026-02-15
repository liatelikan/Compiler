# Compiler
Scheme to x86-64 Compiler
A fully functional, multi-stage compiler that translates Scheme source code into executable x86-64 Assembly. Developed in OCaml, this project covers the entire compilation pipeline, from lexical analysis to code generation.

Features:
Lexical Analysis & Parsing: Robust scanner and parser built using a custom Parser Combinators library (pc.ml).
Semantic Analysis: Implements Macro Expansion, Lexical Addressing (Distinguishing between local, bound, and free variables), and Boxing of mutated variables.
Optimization: Includes Constant Folding and Tail-Call Optimization (TCO) to ensure efficient execution.
Code Generation: Generates Linux-compatible x86-64 Assembly code, including a custom runtime system for memory management and garbage collection.
Built-in Library: Support for standard Scheme primitives (lists, math, strings) integrated via init.scm.

Project Structure:
compiler.ml: The core logic of the compiler, orchestrating the different compilation phases.
pc.ml: A powerful Parser Combinator library used for building the language's grammar.
prologue.asm / epilogue.asm: Low-level Assembly templates providing the runtime environment and primitive operations.
init.scm: The standard library of the language, written in Scheme itself and compiled into every binary.

Tech Stack
Language: OCaml (Functional Programming)
Target: x86-64 Assembly (NASM)
Build Tool: Makefile

Usage
To compile a Scheme file (input.scm) into an executable:
Compile the Scheme source:
Bash
make
./compiler input.scm > output.asm
Assemble and Link:

Bash
nasm -f elf64 output.asm -o output.o
gcc -m64 output.o -o output
Run:

Bash
./output
