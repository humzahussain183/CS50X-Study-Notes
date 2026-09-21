# CS50x: Week 0 - Computational Thinking & Scratch

> **Note:** These notes were AI-generated and organised from my own raw study scribblings taken while completing the CS50x Week 0 material. They are intended as a learning record rather than a verbatim transcript of the course.

## Overview

Completed **Week 0 of Harvard's CS50x**, introducing the foundations of computer science and programming through computational thinking and **Scratch**, a visual programming language.

The week focused on how computers represent information using binary, how algorithms provide structured solutions to problems, and how fundamental programming concepts such as functions, conditionals, loops, variables, and abstraction can be combined to build more complex solutions.

---

## 1. Computers & Artificial Intelligence

### Development Environment

* **VS Code**: A text editor and development environment used to write and manage code.
* **API (Application Programming Interface)**: A defined way for different software components to communicate with each other.
* **Client**: A program or device that requests a service or resource from another system.

A key takeaway was that **computer science is fundamentally about problem solving**. Programming languages and tools are ways of expressing solutions to problems rather than the problem-solving process itself.

---

## 2. Binary & How Computers Represent Information

Computers ultimately represent information using **binary**, a base-2 number system consisting of:

* `0`
* `1`

A **bit** is a single binary digit and can therefore have one of two possible states.

### Bits, Bytes & Transistors

* **Bit**: A single `0` or `1`
* **Byte**: 8 bits
* 8 bits can represent **256 different combinations**, from `00000000` to `11111111`, representing values from 0 to 255
* A **transistor** acts as a tiny electronic switch and is fundamental to digital computing.

Increasing the number of bits allows computers to represent increasingly large numbers and more complex information.

---

## 3. Representing Text with ASCII & Unicode

Computers do not inherently understand letters such as `A` or `B`. Instead, characters can be represented by assigning them numerical values, which can then be represented in binary.

### ASCII

**ASCII (American Standard Code for Information Interchange)** provides a standard mapping between characters and numerical values.

For example:

```text
A = 65 = 01000001
B = 66 = 01000010
a = 97 = 01100001
```

Uppercase and lowercase letters have a difference of **32** in their ASCII values.

ASCII is limited in the number of characters it can represent, so modern computing predominantly relies on **Unicode**, which provides a much larger standardised character set.

### Unicode

Unicode allows computers to represent a huge range of characters, including:

* Different writing systems
* Symbols
* Mathematical characters
* Emojis

The same Unicode value for an emoji can be interpreted consistently across different devices, while the actual graphical appearance can vary between platforms such as Apple and Android.

---

## 4. Representing Images, Video & Sound

Binary is not limited to text. The same fundamental concept can be used to represent virtually any type of digital information.

### Images

Digital images are constructed from individual **pixels**.

Using the RGB colour model, each pixel can be represented using three colour channels:

```text
Red   = 0 to 255
Green = 0 to 255
Blue  = 0 to 255
```

Each colour channel requires one byte, meaning an RGB pixel requires **3 bytes** of colour information.

Combining millions of these pixels produces a digital image.

### Video

A video can be represented as a sequence of individual images, or **frames**, displayed rapidly enough to create the perception of movement.

This is conceptually similar to a digital flipbook.

### Audio

Sound can also be converted into digital information. Notes can be described using characteristics such as:

* **Pitch**
* **Duration**
* **Loudness**

These characteristics can then be represented digitally using binary data.

### Key Principle

The same underlying representation, **binary**, can be used to represent very different types of information.

The **context and encoding system** determine whether a particular sequence of bits represents a number, character, colour, image, sound, or something else.

---

## 5. Algorithms & Computational Thinking

An **algorithm** is a defined sequence of steps used to solve a problem.

One of the most important concepts from the lecture was that writing a program that produces the correct answer is not necessarily enough. A good solution should also consider **efficiency**.

For example, searching for a name in a telephone book could involve checking every entry individually. A more efficient approach is to repeatedly divide the problem in half.

This introduced the idea that **algorithmic efficiency matters**, particularly as the size of a problem increases.

---

## 6. Pseudocode

Before writing actual code, a problem can be broken down into **pseudocode**, which is a structured, human-readable description of how a solution should work.

For example:

```text
1. Pick up the phone book
2. Open to the middle
3. Look at the page
4. If the person is on the page
       Call the person
5. Else if the person's name comes earlier in the book
       Open to the middle of the left half
       Go back to step 3
6. Else
       Open to the middle of the right half
       Go back to step 3
```

This demonstrates an important programming principle:

> **Break a large problem into a series of smaller, well-defined steps.**

---

## 7. Fundamental Programming Concepts

CS50 introduced several concepts that form the building blocks of programming.

### Functions

Functions represent **actions** that a program can perform.

They can also accept **arguments or parameters**, allowing the same function to behave differently depending on the input.

For example:

```text
say("Hello, world!")
```

The text `"Hello, world!"` is passed into the function as an argument.

### Conditionals

Conditionals allow a program to make decisions based on whether something is true or false.

```text
IF condition is true
    perform action A
ELSE
    perform action B
```

They can be thought of as **forks in the road** within an algorithm.

### Loops

Loops allow instructions to be repeated.

Rather than writing the same instructions multiple times, a loop can perform the same operation repeatedly until a particular condition is met.

### Boolean Expressions

Boolean expressions evaluate to one of two states:

```text
TRUE
FALSE
```

These provide the logical basis for decision-making within programs.

### Variables

Variables allow programs to **store values** so that they can be used and manipulated later.

---

## 8. Abstraction

One of the broader concepts introduced was **abstraction**.

Rather than requiring a programmer to understand every underlying detail of a system, abstraction allows complex functionality to be represented through simpler interfaces.

For example, a programmer can use:

```text
print("Hello")
```

without needing to understand every underlying operation required by the computer to display those characters.

This allows increasingly complex systems to be built by combining simpler components.

---

## 9. Inputs, Outputs & Side Effects

A useful distinction was made between **return values** and **side effects**.

### Return Value

A return value is information produced by a function that can be used by the program.

### Side Effect

A side effect is an observable consequence of running a function, such as:

* Displaying something on screen
* Playing a sound
* Moving an object

Conceptually:

```text
Input
  ↓
"Hello, world!"
  ↓
say() function
  ↓
Cat displays "Hello, world!"
```

The input influences the function's behaviour, while the visible result is a side effect.

---

## 10. Composition & Reusable Solutions

A major theme throughout the week was **composing larger solutions from smaller components**.

Functions can be combined and nested to perform increasingly complex operations.

For example, in Scratch:

```text
say(join("Hello, ", answer))
```

Instead of creating one large block of logic, smaller pieces of functionality can be combined.

This leads to an important software engineering principle:

> **Solve complex problems by composing simple, reusable solutions.**

Common functionality can also be factored out into reusable functions or loops, reducing duplication and keeping programs easier to understand and maintain.

---

## Key Takeaways

By the end of Week 0, I had developed an introductory understanding of:

* Binary representation and how computers encode information
* Bits, bytes and the role of transistors
* ASCII and Unicode character encoding
* Digital image representation using RGB
* How video and audio can be represented digitally
* Algorithmic thinking and efficiency
* Writing pseudocode before implementing a solution
* Functions and arguments
* Conditionals and Boolean logic
* Loops and repetition
* Variables and data storage
* Abstraction
* Inputs, outputs, return values and side effects
* Composing smaller functions into larger solutions
* The importance of reusable and maintainable logic

## Reflection

The main takeaway from Week 0 is that **programming is fundamentally an exercise in structured problem solving**.

The syntax of a particular programming language is only one part of the process. The more important skill is being able to break a problem down into manageable components, develop an efficient algorithm, and then express that solution using appropriate programming constructs.

This provides the foundation for the more technical programming work covered in the following weeks of CS50x.

## Next Step

**Week 1: C**

Moving from visual programming with Scratch into a text-based programming language, focusing on C, syntax, data types, variables, conditionals, loops, and compiling and executing programs.
