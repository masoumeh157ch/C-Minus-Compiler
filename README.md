# C-Minus Compiler

**University Compiler Design Project | Python | Lexical Analysis, Syntax Analysis & Intermediate Code Generation**

## Overview

This project explores the design and implementation of a **one-pass compiler for C-minus**, a simplified version of the C programming language, as part of a university Compiler Design course.

The project is organized into three interconnected phases covering the fundamental stages of compilation: **lexical analysis, syntax analysis, and intermediate code generation**.

The compiler is designed around a single-pass architecture in which the scanner, parser, and code generator cooperate to process source code without requiring multiple passes over the input.

The project specifications also introduce an optional semantic analysis component for detecting semantic errors.

## Technologies & Concepts

- **Programming Language:** Python
- **Source Language:** C-minus (Simplified C)
- **Compiler Architecture:** One-Pass Compilation
- **Lexical Analysis:** Deterministic Finite Automata (DFA), Tokenization
- **Syntax Analysis:** Predictive Top-Down Parsing, FIRST and FOLLOW Sets
- **Error Handling:** Lexical Error Detection, Syntax Error Recovery (Panic Mode)
- **Code Generation:** Intermediate Representation (IR), Three-Address Code (TAC)
- **Core Concepts:** Context-Free Grammars, Symbol Tables, Semantic Actions

## Project Phases

### Phase 1 — Lexical Analysis (Scanner)

The first phase focuses on designing a lexical analyzer that reads C-minus source code and identifies valid tokens based on the language's lexical rules.

The scanner specification covers:

- Recognition of keywords, identifiers, numbers, and language symbols.
- Processing of whitespace and comments.
- Identification and reporting of invalid tokens and lexical errors.
- Construction and maintenance of a symbol table.
- Token generation for subsequent compiler phases.
- Token recognition using deterministic finite automata.

**Expected output files:**

| File | Description |
|---|---|
| `tokens.txt` | Recognized tokens grouped by source line |
| `lexical_errors.txt` | Detected lexical errors |
| `symbol_table.txt` | Keywords and identified symbols |

### Phase 2 — Syntax Analysis (Parser)

The second phase focuses on a **predictive top-down parser** for analyzing the grammatical structure of C-minus programs.

The parser specification includes:

- Parsing source programs according to a predefined context-free grammar.
- Using FIRST and FOLLOW sets to guide predictive parsing.
- Performing syntax analysis without backtracking.
- Integrating with the scanner through sequential token retrieval.
- Constructing a hierarchical parse tree.
- Detecting syntax errors and applying Panic Mode recovery.

**Expected output files:**

| File | Description |
|---|---|
| `parse_tree.txt` | Hierarchical representation of the parsed program |
| `syntax_errors.txt` | Detected syntax errors |

### Phase 3 — Intermediate Code Generation

The third phase extends the compiler with intermediate code generation for a supported subset of C-minus.

The design uses **syntax-directed translation**, where semantic actions are associated with grammar productions and invoked during parsing.

The code generation specification covers:

- Generating three-address intermediate code.
- Managing intermediate values through a semantic stack.
- Handling variable declarations, assignments, and arithmetic expressions.
- Translating relational expressions and supported control-flow statements.
- Managing memory addresses and temporary values.
- Generating instructions compatible with the project's provided interpreter.

The required intermediate representation uses instructions such as `ASSIGN`, `ADD`, `MULT`, `LT`, `JP`, `JPF`, and `PRINT`.

**Expected output file:**

| File | Description |
|---|---|
| `output.txt` | Generated three-address intermediate code |

The third-phase specification also describes an **optional semantic analyzer** for static semantic checks. Its implementation should be considered separately from the required code generation component.

## Compiler Architecture

The intended compilation pipeline is:

```text
C-minus Source Code
        |
        v
  Lexical Analyzer
     (Scanner)
        |
        v
   Syntax Analyzer
      (Parser)
        |
        v
  Semantic Actions
        |
        v
Intermediate Code Generator
        |
        v
 Three-Address Code
```

The components are designed to cooperate during a single pass through the input program.

## Supported Language Constructs

The C-minus grammar used in the project includes:

- Integer and void type declarations.
- Scalar variables and arrays.
- Arithmetic and relational expressions.
- Assignment statements.
- Conditional statements (`if` / `else`).
- Iteration statements (`repeat` / `until`).
- Function declarations and parameter lists.
- Function calls and return statements.
- `break` statements.

**Implementation scope:** The code generation phase targets a restricted subset of the language. In particular, the initial required code generation specification excludes general function calls and return statements. Therefore, support for a construct in the grammar does not necessarily imply support in generated intermediate code.

## Input and Output

The compiler specifications use a text file named `input.txt` containing a C-minus source program.

A simple example of C-minus input is:

```c
void main(void) {
    int a;
    int b;

    a = 5;
    b = a + 3;

    output(b);
}
```

The compiler pipeline is intended to analyze the input and generate the corresponding lexical, syntactic, and intermediate-code outputs, depending on the phase being executed.

## Learning Objectives

This project provides practical experience with:

- Understanding the internal architecture of compilers.
- Translating formal language specifications into program logic.
- Applying finite automata to lexical analysis.
- Implementing predictive parsing based on context-free grammars.
- Designing structured error detection and recovery mechanisms.
- Connecting syntax analysis with code generation through semantic actions.
- Representing source-level operations using three-address intermediate code.

## Project Context

**Type:** University Coursework — Compiler Design  
**Academic Term:** Spring 2025  
**Implementation Language:** Python  
**Target Language:** C-minus

The project follows a three-phase educational compiler specification and is intended to demonstrate core principles of compiler construction rather than provide a production-ready C compiler.
