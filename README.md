# PolyCalc
## Technical Specifications
### 1. Overview
The goal is to implement a command-line calculator that uses Reverse Polish Notation (RPN). In this notation, operators follow their operands (e.g., 3 4 + instead of 3 + 4). This eliminates the need for parentheses and simplifies parsing.

### 2. Core Logic (The Stack)
The calculator must be built around a LIFO (Last-In, First-Out) Stack.
* Operands (numbers): When a number is encountered, it is pushed onto the stack.
* Operators (+, -, , /): When an operator is encountered:
  1. Pop the two most recent values from the stack.
  2. Apply the operation.
  3. Push the result back onto the stack.

### 3. Data Structure Requirements (C Implementation)
To master memory management, the C core must follow these rules:
* Dynamic Memory: The stack must not have a fixed size. It should start with an initial capacity (e.g., 4) and double its size using realloc when full.
* Precision: Use double for all calculations to support floating-point numbers.
* Memory Safety: Every malloc/realloc must have a corresponding free. No memory leaks allowed.
### 4. Supported Operations & Edge Cases
#### Operators:
* \+ : Addition 
* \- : Subtraction
* \* : Multiplication
* \/ : Division (must handle division by zero)
#### Error Handling:
* Stack Underflow: Occurs if an operator is called but there are fewer than two numbers on the stack (e.g., the user types 5 +).
* Division by Zero: The program should print an error message and maintain the stack's integrity.
* Invalid Input: Handle cases where the user enters text that is neither a number nor a valid operator.

### 5. User Interface (CLI)
The program should run in a loop (REPL - Read-Eval-Print Loop):
* Input: Read a line from the user.
* Processing: Tokenize the line (split by spaces).
* Output: After processing the line, print the value at the top of the stack (the result).

### 6. Project Roadmap
| Phase | Task             | Focus                                    |
| ----- | ---------------- | -----------------------------------------|
| 1     | Stack Engine (C) | malloc, realloc, free, pointers.         |
| 2     | Parser (C)       | strtok, atof, string manipulation.       |
| 3     | C++ Porting      | Templates, std::vector, RAII.            |
| 4     | Python Wrapper   | subprocess or ctypes to call the C core. |
| 5     | Web Interface    | FastAPI (Python) to expose the logic.    |
