# CS50x: Week 1 - C

> **Note:** These notes were AI-generated and organised from my own raw study scribblings taken while completing the CS50x Week 1 material. They are intended as a learning record rather than a verbatim transcript of the course.

## Overview

Completed **Week 1 of Harvard's CS50x**, moving from visual programming in Scratch into **C**, a text-based programming language.

The week introduced the fundamentals of writing, compiling and executing C programs, as well as variables, data types, conditionals, loops, functions, scope, command-line tools and debugging.

A key theme was learning how to translate the problem-solving concepts introduced in Week 0 into actual code.

---

## 1. Source Code, Machine Code & Compilers

**Source code** is the code written by a programmer. It is designed to be understandable by humans.

Computers ultimately execute **machine code**, which is represented as binary instructions.

A **compiler** translates source code into a form that the computer can execute.

The basic process is:

```text
Source Code
    ↓
Compiler
    ↓
Machine Code
    ↓
Program Execution
```

In CS50, the `make` command is used to compile C programs.

For example:

```bash
make hello
./hello
```

The first command compiles the source code, while `./hello` executes the resulting program.

An important practical point is that if the source code is changed, the program needs to be recompiled before the changes will appear when it is run.

---

## 2. VS Code, GUI & CLI

**VS Code** is a widely used code editor and development environment.

There are two important ways of interacting with a computer:

### Graphical User Interface (GUI)

A GUI allows users to interact with a system using visual elements such as:

* Windows
* Buttons
* Menus
* Icons
* File explorers

### Command Line Interface (CLI)

A CLI allows a user to interact with the computer by entering text commands into a **terminal**.

For example:

```bash
ls
```

The terminal provides a direct way of interacting with the operating system and is an important tool for programmers.

---

## 3. Escape Sequences

C uses **escape sequences** to represent special characters or instructions within strings.

For example:

```c
\n
```

creates a new line.

Other examples include:

```c
\"
\'
\\
```

These allow characters such as quotation marks and backslashes to be included within strings without being interpreted as part of the C syntax.

---

## 4. Header Files & Libraries

C programs can make use of functionality that has already been written by other programmers.

**Header files** generally have a `.h` extension and contain declarations that allow a program to use functions and other functionality provided by libraries.

For example:

```c
#include <stdio.h>
```

allows access to functionality from the standard input/output library, including `printf`.

CS50 also provides:

```c
#include <cs50.h>
```

which provides functions created specifically for the course, such as `get_string` and `get_int`.

The general idea is:

```text
Header File
    ↓
Library Function
    ↓
Use functionality in your program
```

Rather than writing every piece of functionality from scratch, programmers can make use of existing libraries.

---

## 5. Documentation & Manual Pages

An important programming skill is knowing how to find information rather than trying to memorise everything.

C provides **manual pages**, commonly referred to as `man` pages, which document functions and commands.

For example:

```bash
man printf
```

CS50 also provides simplified documentation through **manual.cs50.io**.

This reinforced the importance of being able to research and understand existing documentation when developing software.

---

## 6. Strings, Arguments & Return Values

A **string** is a sequence of characters representing text.

CS50 provides the `get_string` function for obtaining text input from a user.

For example:

```c
string answer = get_string("What's your name? ");
```

The function:

1. Displays a question to the user
2. Receives their input
3. Returns the input
4. Stores the result in the variable `answer`

The general pattern is:

```text
Input
  ↓
Function
  ↓
Return Value
  ↓
Variable
```

The value can then be used elsewhere in the program.

For example:

```c
printf("Hello, %s\n", answer);
```

`%s` is a **format specifier** used to insert a string into the output.

---

## 7. Operating Systems & Linux

An **operating system (OS)** manages the fundamental operations of a computer and provides an interface between software and hardware.

Examples include:

* Windows
* macOS
* Linux
* Android
* iOS

Linux is particularly common within software development and server environments.

The command line provides a way to interact directly with the operating system.

---

## 8. Basic Command Line Commands

I learned several basic Linux terminal commands:

| Command | Purpose                    |
| ------- | -------------------------- |
| `ls`    | List files and directories |
| `mkdir` | Create a directory         |
| `rm`    | Remove a file              |
| `cp`    | Copy a file                |
| `mv`    | Move or rename a file      |
| `cd`    | Change directory           |

For example:

```bash
mkdir hello
```

creates a directory called `hello`.

```bash
mv hello.c hello/
```

moves `hello.c` into the `hello` directory.

```bash
cd hello
```

moves into the `hello` directory.

The `mv` command can also rename files:

```bash
mv oldname.c newname.c
```

And:

```bash
cp hello.c backup.c
```

creates a copy of `hello.c` called `backup.c`.

The following:

```bash
mv hello.c ..
```

moves the file into the parent directory.

These commands provide a foundation for navigating and managing files from the command line.

---

## 9. Conditionals

C uses conditional statements to allow programs to make decisions.

For example:

```c
if (x < y)
{
    printf("x is less than y\n");
}
```

Additional conditions can be added using `else` and `else if`.

```c
if (x < y)
{
    printf("x is less than y\n");
}
else if (x > y)
{
    printf("x is greater than y\n");
}
else
{
    printf("x is equal to y\n");
}
```

### Comparison vs Assignment

An important distinction in C is the difference between:

```c
x = y;
```

and:

```c
x == y;
```

`=` is the **assignment operator**, which assigns a value.

`==` is the **equality operator**, which checks whether two values are equal.

Other comparison operators include:

```text
!=    Not equal
<     Less than
>     Greater than
<=    Less than or equal to
>=    Greater than or equal to
```

---

## 10. Data Types

C requires variables to have a defined **data type**.

Some common types include:

| Type     | Purpose                                  |
| -------- | ---------------------------------------- |
| `bool`   | Boolean values such as `true` or `false` |
| `char`   | A single character                       |
| `float`  | Floating-point number                    |
| `double` | Double-precision floating-point number   |
| `int`    | Integer                                  |
| `long`   | Larger integer                           |
| `string` | Sequence of characters, provided by CS50 |

The amount of memory available to a variable depends on its type and the system being used.

---

## 11. Format Specifiers

When using `printf`, format specifiers tell C what type of value should be inserted into the output.

Common examples include:

```text
%c     Character
%f     Floating-point number
%i     Integer
%li    Long integer
%s     String
```

For example:

```c
printf("Hello, %s\n", answer);
```

The `%s` is replaced with the value stored in `answer`.

---

## 12. Characters & Strings

Characters and strings are represented differently in C.

A **character** uses single quotation marks:

```c
char answer = 'y';
```

A **string** uses double quotation marks:

```c
string answer = "yes";
```

For example:

```c
if (c == 'y')
{
    printf("Yes\n");
}
```

This distinction is important when writing comparisons and handling text.

---

## 13. Logical Operators

C provides logical operators for combining conditions.

### OR

```c
||
```

The condition is true if either expression is true.

### AND

```c
&&
```

The condition is true only if both expressions are true.

For example:

```c
if (x > 0 && x < 10)
{
    printf("x is between 1 and 9\n");
}
```

---

## 14. Variables & Incrementing

Variables can be updated throughout a program.

For example:

```c
counter = counter + 1;
```

can also be written more concisely as:

```c
counter += 1;
```

or:

```c
counter++;
```

These all increase `counter` by 1.

The `++` operator is a common shorthand used in C.

---

## 15. Loops

Loops allow a program to repeatedly execute a block of code.

### While Loop

For example:

```c
int i = 3;

while (i > 0)
{
    printf("meow\n");
    i--;
}
```

This prints `meow` three times.

### For Loop

The same behaviour can be written using a `for` loop:

```c
for (int i = 0; i < 3; i++)
{
    printf("meow\n");
}
```

A `for` loop combines the initialisation, condition and increment into one statement.

### Infinite Loops

A loop can continue indefinitely:

```c
while (true)
{
    printf("meow\n");
}
```

In the terminal, `Ctrl-C` can be used to interrupt a running program.

---

## 16. `break` & `continue`

Two keywords can be used to control the behaviour of loops.

### `continue`

Skips the remainder of the current iteration and moves to the next iteration of the loop.

### `break`

Immediately exits the loop and continues execution with the code following the loop.

---

## 17. Scope

**Scope** determines where a variable can be accessed within a program.

For example, a variable declared inside a loop generally cannot be accessed outside that loop.

This means that variables need to be declared at an appropriate level of scope depending on where they are required.

Understanding scope is important for writing predictable and maintainable code.

---

## 18. Do While Loops

A `do while` loop guarantees that the code inside the loop runs **at least once** before the condition is checked.

For example:

```c
do
{
    n = get_int("What's n? ");
}
while (n < 0);
```

The user is asked for a value once, and the loop continues if the value is invalid.

This differs from a standard `while` loop because the condition is checked **after** the first execution.

---

## 19. Creating Functions

C allows programmers to create their own functions rather than putting all of the program's logic into `main`.

For example:

```c
void meow(void)
{
    printf("meow\n");
}
```

The function can then be called from elsewhere in the program.

Functions can also accept inputs.

For example:

```c
void meow(int n)
{
    for (int i = 0; i < n; i++)
    {
        printf("meow\n");
    }
}
```

Calling:

```c
meow(3);
```

would cause the function to print `meow` three times.

This reinforces the concept introduced in Week 0 of building larger solutions from smaller, reusable components.

---

## 20. Function Prototypes

A **function prototype** allows a function to be declared before its full implementation.

For example:

```c
void meow(int n);
```

The function can then be defined later in the program.

This allows the compiler to know about the function before it encounters the code that defines it.

---

## 21. Comments

Comments allow programmers to leave notes within their code that are ignored by the compiler.

A single-line comment begins with:

```c
//
```

For example:

```c
// Ask the user for their name
string answer = get_string("What's your name? ");
```

Comments are useful for explaining reasoning, documenting code and making programs easier for other developers to understand.

---

## 22. Correctness, Design & Style

CS50 introduced three useful ways of thinking about code quality.

### Correctness

Does the program actually do what it is supposed to do?

### Design

How well is the problem solved?

This includes considerations such as efficiency, simplicity, avoiding unnecessary duplication and structuring the program effectively.

### Style

Is the code readable and consistently formatted?

This includes:

* Indentation
* Naming variables clearly
* Consistent formatting
* Sensible organisation

Good code is therefore not simply code that works. It should also be **well designed and understandable**.

---

## 23. CS50 Development Tools

CS50 provides tools to help assess code.

### Check50

`check50` provides automated checks to help determine whether a program meets the required functionality.

### Design50

`design50` provides feedback on aspects of the design of a solution.

### Style50

`style50` provides feedback on code formatting and style.

These tools provide quick feedback during development and help identify areas for improvement.

---

## 24. Constants

Sometimes a value should remain unchanged throughout a program.

C provides the `const` keyword for declaring a value that should not be modified.

For example:

```c
const int n = 3;
```

This communicates the intention that `n` should remain constant.

Using constants can make code clearer and reduce the risk of accidentally changing important values.

---

## 25. Integer Overflow

A computer has a finite amount of memory available to represent numbers.

If a program attempts to store an integer that is larger than the maximum value that the data type can represent, **integer overflow** can occur.

This can result in unexpected values and demonstrates why understanding data types and their limitations is important.

Using a larger integer type, such as `long`, can provide a larger range of values where appropriate.

---

## 26. Integer Truncation

When performing calculations using integers, the decimal portion of a result can be discarded.

For example:

```c
5 / 2
```

using integer arithmetic results in:

```text
2
```

rather than:

```text
2.5
```

If decimal values are required, a floating-point type such as `float` or `double` should be used.

---

## 27. Floating-Point Imprecision

Floating-point numbers are not always represented exactly in computer memory.

This can lead to **floating-point imprecision**, where calculations involving decimal values produce results that are slightly different from what might be expected mathematically.

This is an important reminder that computers represent numbers within finite technical constraints and that numerical data types need to be chosen appropriately.

---

# Practical Learning

During Week 1, I began applying the concepts from the lecture by writing and running programs in **C** rather than using the visual programming environment from Week 0.

This provided practical experience with:

* Writing C source code
* Compiling programs
* Running programs from the command line
* Using variables and different data types
* Receiving user input
* Producing formatted output
* Using conditionals
* Creating loops
* Writing reusable functions
* Working with command-line tools
* Testing and debugging programs

The practical work reinforced the transition from **problem solving in Scratch to writing structured, text-based programs in C**.

I had to think about how information should be stored, how the program should make decisions, how repetitive tasks could be handled efficiently, and how individual functions could be combined into a complete solution.

This also introduced the practical development cycle:

```text
Problem
   ↓
Plan / Algorithm
   ↓
Write Source Code
   ↓
Compile
   ↓
Run
   ↓
Test & Debug
   ↓
Improve
```

---

# Key Takeaways

By the end of Week 1, I had developed an introductory understanding of:

* Source code and machine code
* The role of a compiler
* Compiling and executing C programs
* Using VS Code and the command line
* Linux terminal commands
* Header files and libraries
* Using documentation and manual pages
* Variables and data types
* Strings and characters
* Format specifiers
* User input and return values
* Conditionals and logical operators
* `for`, `while` and `do while` loops
* `break` and `continue`
* Functions and function prototypes
* Variable scope
* Comments
* Constants
* Integer overflow
* Integer truncation
* Floating-point imprecision
* Code correctness, design and style
* Testing and automated feedback

## Reflection

Week 1 was a significant step from understanding programming concepts to actually implementing them in a text-based programming language.

The biggest shift was moving from Scratch's visual blocks to having to understand syntax, data types, compilation and the command line. This made the relationship between the problem-solving process and the final implementation much clearer.

I also began to appreciate that writing working code is only one part of software development. **Correctness, design, readability and the ability to test and improve a solution are equally important.**

## Next Step

**Week 2: Arrays**

Moving further into C and exploring arrays, strings, command-line arguments, searching, sorting and memory.
