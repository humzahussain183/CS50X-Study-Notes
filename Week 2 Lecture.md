# CS50x: Week 2 - Arrays

> **Note:** These notes were AI-generated and organised from my own raw study scribblings taken while completing the CS50x Week 2 material. They are intended as a learning record rather than a verbatim transcript of the course.

## Overview

Lecture 2 introduced **arrays**, building on the foundations of C covered in Week 1. The lecture explored debugging, memory, data types, strings, command-line arguments, exit statuses and the fundamentals of cryptography.

A key theme was understanding how data is stored in memory and how C allows programmers to access and manipulate it.

---

## 1. Syntax Errors & Logic Errors

Programming errors can generally be divided into different categories.

### Syntax Errors

A **syntax error** occurs when code does not follow the rules of the programming language. These errors can prevent a program from compiling.

### Logic Errors

A **logic error** occurs when a program runs but does not produce the intended result.

For example, a calculation might use the wrong operator or a condition might be written incorrectly.

Logic errors can be harder to identify because the program may compile and run without displaying an obvious error.

---

## 2. Debugging

**Debugging** is the process of identifying, investigating and fixing errors in a program.

### Using `printf` for Debugging

One simple debugging technique is to insert `printf` statements throughout a program to display the values of variables at different stages.

For example:

```c
printf("Score: %i\n", score);
```

This helps reveal whether variables contain the expected values as the program executes.

### Using a Debugger

A **debugger** is a tool that allows a programmer to inspect a program while it is running.

CS50 provides `debug50`, which can be used to investigate how code executes and identify the cause of errors.

Useful debugger controls include:

- **Step Over:** Executes the current line and moves to the next line without stepping through the internal execution of a function.
- **Step Into:** Enters a function so its execution can be inspected line by line.

Debugging makes it easier to follow the flow of a program and understand where its behaviour differs from what was expected.

---

## 3. Garbage Values

A **garbage value** is an unpredictable value that may be present in a variable when it has not been properly initialised.

For example:

```c
int score;
printf("%i\n", score);
```

In C, reading an uninitialised local variable like `score` results in undefined behaviour. It should not be assumed to contain zero or a reliable default value.

To avoid this, variables should be initialised before their values are used.

```c
int score = 0;
```

This ensures that `score` begins with a known value.

---

## 4. Compilation in C

The `make` command is commonly used in CS50 to compile C programs.

For example:

```bash
make hello
```

This compiles the source file `hello.c` into an executable named `hello`, assuming the source file and compilation environment are set up correctly.

C programs can also be compiled directly using **Clang**, the compiler used in CS50.

A basic example is:

```bash
clang hello.c -o hello
```

The `-o hello` option specifies the name of the output executable.

When a program uses CS50 library functions, the CS50 library must also be linked:

```bash
clang hello.c -o hello -lcs50
```

The compiler may also need to be told where to find the relevant header files and libraries, depending on the environment.

### Command-Line Arguments

The commands entered into a terminal can contain arguments that tell a program or command what to do.

For example:

```bash
make hello
```

Here, `hello` is an argument passed to `make`.

When compiling directly, options such as `-o` and `-lcs50` are also command-line arguments.

---

## 5. The Four Stages of Compilation

Compiling a C program involves several stages.

### 1. Preprocessing

The preprocessor handles directives such as:

```c
#include <stdio.h>
```

It processes header inclusions and macros before the main compilation stage. Header files provide declarations that allow the program to use functions and other features.

### 2. Compiling

The compiler translates the preprocessed C code into assembly language.

### 3. Assembling

The assembler converts the assembly language into machine code, typically stored in object files.

### 4. Linking

The linker combines the necessary object files and libraries to produce an executable program.

For example, the linker resolves references to functions such as `printf` and, when used, functions provided by the CS50 library.

The process can be summarised as:

```text
C Source Code
      ↓
Preprocessing
      ↓
Compilation
      ↓
Assembly
      ↓
Linking
      ↓
Executable Program
```

Understanding these stages helps explain what happens behind the scenes when a program is compiled.

### Decompiling

**Decompiling** is the process of attempting to reconstruct higher-level source code from compiled software.

The result may not match the original source code exactly because compilation can remove information and transform the program.

---

## 6. Data Types & Memory

Variables require memory to store their values.

The amount of memory used depends on the data type and the system. The following are common sizes on many modern systems, but C does not guarantee every size to be the same across all platforms.

| Data Type | Typical Size |
|---|---:|
| `bool` | 1 byte |
| `char` | 1 byte |
| `int` | 4 bytes |
| `long` | 8 bytes on many 64-bit systems |
| `float` | 4 bytes |
| `double` | 8 bytes |

A `string` in CS50 is a type provided by the CS50 library that represents text. It is not a built-in primitive type in C, and its memory requirements depend on the text and how it is stored.

### Memory and Binary

Computer memory stores information in binary form, using bits represented as `0` and `1`.

When a variable is stored in memory, the computer allocates space for its value according to the requirements of the type and implementation.

Variables also have memory addresses, which identify where their data is stored.

---

## 7. Type Casting

**Type casting** converts a value from one data type to another.

For example:

```c
(float) 3
```

converts the integer value `3` to a floating-point value.

This is useful when a calculation needs to produce a decimal result.

For example:

```c
int x = 5;
int y = 2;

printf("%f\n", (float) x / y);
```

The cast converts `x` to a `float`, so the division produces a floating-point result rather than performing integer division.

The output is:

```text
2.500000
```

---

## 8. Arrays

An **array** is a collection of elements of the same data type stored in contiguous memory locations.

Arrays allow related values to be stored under one variable name instead of declaring a separate variable for every value.

For example:

```c
int scores[3];

scores[0] = 72;
scores[1] = 73;
scores[2] = 33;
```

This creates an array capable of storing three integers.

The values can be accessed using **indexing**.

```c
printf("%i\n", scores[0]);
```

This prints the first value, `72`.

### Array Indexing

In C, array indexing starts at **zero**, not one.

For an array containing three elements:

| Index | Value |
|---:|---:|
| `scores[0]` | `72` |
| `scores[1]` | `73` |
| `scores[2]` | `33` |

The final valid index is one less than the number of elements in the array.

Attempting to access an index outside the array's bounds can cause undefined behaviour.

### Contiguous Memory

Array elements are stored consecutively in memory.

For an integer array, each element occupies the amount of memory required by an `int`, so the elements can be accessed efficiently using their index.

Arrays are particularly useful when working with collections of related data, such as scores, temperatures or measurements.

---

## 9. Strings as Arrays of Characters

In C, a string is represented as a sequence of characters terminated by a **null character**, written as `'\0'`.

For example:

```c
string name = "Sam";
```

Conceptually, the characters are stored as:

```text
'S'  'a'  'm'  '\0'
```

The null character marks the end of the string. It has a value of zero and is distinct from the character `'0'`.

The null character occupies one byte in C.

Because a string is represented by characters, it is possible to access individual characters using array indexing.

For example:

```c
string name = "Sam";

printf("%c\n", name[0]);
```

This prints:

```text
S
```

### Arrays of Strings

It is also possible to create an array containing multiple strings.

For example, a program could store several names in an array and access each name using its index.

This is useful when working with lists of text rather than a single string.

---

## 10. The `string.h` Header File

The standard C header file:

```c
#include <string.h>
```

provides functions for working with strings and memory.

One useful function is `strlen()`, which returns the length of a string.

For example:

```c
string name = "Humza";
printf("%zu\n", strlen(name));
```

The output is:

```text
5
```

`strlen()` counts the characters before the terminating null character. It does not include the null character in the returned length.

The `%zu` format specifier is used to print a value of type `size_t`, which is the type returned by `strlen()`.

---

## 11. The `ctype.h` Header File

The standard C header file:

```c
#include <ctype.h>
```

provides functions for classifying and converting characters.

Examples include:

- `toupper()` converts a lowercase letter to uppercase.
- `tolower()` converts an uppercase letter to lowercase.
- `isalpha()` checks whether a character is an alphabetic letter.
- `isdigit()` checks whether a character is a decimal digit.

For example:

```c
char letter = 'a';

printf("%c\n", toupper(letter));
```

The output is:

```text
A
```

These functions are useful when processing text and working with characters.

---

## 12. The `main` Function

The `main` function is the entry point of a C program. Program execution begins there.

A simple program often uses:

```c
int main(void)
{
    printf("Hello\n");
}
```

### Understanding `int main(void)`

- `int` means the function returns an integer value, commonly used as the program's exit status.
- `main` is the function where execution begins.
- `void` inside the parentheses indicates that the function takes no parameters.

This form is suitable when the program does not need to receive command-line arguments.

---

## 13. Command-Line Arguments: `argc` and `argv`

C programs can accept information directly from the command line when they are launched.

The `main` function can be written as:

```c
int main(int argc, string argv[])
{
    // Program code
}
```

Here:

- `argc` is the argument count, representing the number of command-line arguments.
- `argv` is an array of strings containing the arguments.

In the conventional C argument layout, `argv[0]` contains the program name or invocation path, and additional arguments begin at `argv[1]`.

For example, if a program is run as:

```bash
./greet Humza
```

then the arguments are conceptually:

| Expression | Value |
|---|---|
| `argc` | `2` |
| `argv[0]` | `./greet` |
| `argv[1]` | `Humza` |

The count is two because it includes the program name and the supplied name.

### Example: Greeting a User

```c
#include <cs50.h>
#include <stdio.h>

int main(int argc, string argv[])
{
    if (argc == 2)
    {
        printf("Hello, %s\n", argv[1]);
    }
    else
    {
        printf("Usage: ./greet name\n");
        return 1;
    }
}
```

Running:

```bash
./greet Humza
```

produces:

```text
Hello, Humza
```

The `argc == 2` condition checks that exactly one additional argument has been provided alongside the program name.

This is useful when a program needs information at launch rather than prompting the user for input after it starts.

---

## 14. Exit Statuses

The integer returned by `main` is commonly used to communicate whether a program completed successfully.

For example:

```c
int main(void)
{
    return 0;
}
```

A return value of `0` conventionally indicates success.

A non-zero value generally indicates that an error or other non-standard condition occurred.

In a terminal, the following command displays the exit status of the most recently executed command:

```bash
echo $?
```

For example, if a program returns `1`, running `echo $?` immediately afterwards will display:

```text
1
```

Exit statuses allow programs and scripts to communicate results to the operating system and to other commands.

---

## 15. Introduction to Cryptography

**Cryptography** involves techniques for protecting information, including transforming readable information into a form that is difficult to understand without the appropriate key.

The basic process can be represented as:

```text
Plaintext
    ↓
Encryption Algorithm + Key
    ↓
Ciphertext
```

- **Plaintext:** The original readable information.
- **Encryption algorithm (cipher):** The method used to transform the information.
- **Key:** Information used by the algorithm to determine how the transformation is performed.
- **Ciphertext:** The transformed information.

Decryption uses the appropriate algorithm and key to recover the original plaintext.

### Caesar Cipher

The **Caesar cipher** is a simple substitution cipher that shifts each letter by a fixed number of positions through the alphabet.

For example, with a shift of three:

```text
Plaintext:  HELLO
Ciphertext: KHOOR
```

Each letter moves three positions forward in the alphabet, with the sequence wrapping around at the end.

The Caesar cipher demonstrates how an algorithm and a key can be used to transform information. However, it is not secure for modern use because its small number of possible shifts makes it easy to break.

---

# Practical Learning

Lecture 2 developed my understanding of how C programs behave during execution and how data is represented and accessed in memory.

The key areas covered included:

- Identifying syntax errors and logic errors
- Using `printf` to investigate program behaviour
- Using a debugger to step through code
- Understanding the compilation process
- Working with data types and memory
- Casting values between data types
- Creating and accessing arrays
- Understanding strings as arrays of characters
- Using standard library functions
- Passing information to a program through command-line arguments
- Understanding program exit statuses
- Exploring the basic principles of encryption

The lecture also highlighted the importance of understanding what happens behind the scenes. Rather than treating variables, strings and arrays as abstract concepts, I began to understand how they relate to memory and how a program accesses stored information.

---

# Key Takeaways

By the end of Lecture 2, I had developed an introductory understanding of:

- Syntax errors and logic errors
- Debugging techniques and `debug50`
- Garbage values and variable initialisation
- Clang and the compilation process
- Preprocessing, compiling, assembling and linking
- Data types and memory requirements
- Type casting
- Arrays and zero-based indexing
- Contiguous memory
- Strings and null termination
- The `string.h` and `ctype.h` header files
- The `main` function
- Command-line arguments using `argc` and `argv`
- Exit statuses and `echo $?`
- Plaintext, ciphertext, keys and encryption algorithms
- The Caesar cipher

## Reflection

Lecture 2 built on the fundamentals of C by introducing more detail about how data is stored, accessed and processed.

Arrays provide a way to organise related values, while understanding strings as sequences of characters helps explain how text is represented in C. Command-line arguments also showed how programs can receive information when they are launched, rather than relying entirely on interactive input.

Debugging was another important theme. Being able to inspect variables, follow program execution and investigate unexpected behaviour is an essential part of developing reliable software.

## Next Step

**Continue developing C fundamentals**, with further practice using arrays, strings, algorithms and problem-solving techniques.
