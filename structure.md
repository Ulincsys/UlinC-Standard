# UlinC Language Structure

The UlinC language is a [C-Type language](https://en.wikipedia.org/wiki/List_of_C-family_programming_languages) structured to be as simple and effective as possible. The UlinC language is composed of many parts, each of which build upon one another to achieve this goal. Because of this, it is similar to many other languages such as Java and C.

## Introduction

This introduction is intended to serve as a basic overview of the structure of the UlinC language. Each section is explained simply, with an emphasis on common English, in the hopes that it may serve not only as an overview of the UlinC language, but also as an introduction to programming languages for someone with no computer science experience.

All of the sections in this introduction are laid out in linear fashion, building upon one another. Sections start with the simplest concepts generally applicable to programming languages, and then move onto more specific information.

### Code

Code is the text which describes a program. All of the instructions, documentation, and information that are used to build a program are considered to be part of the Code.

### Compiler

The compiler is a program which is designed to convert code into machine instructions, which a computer can understand. The compiler is built to read instructions which are written in the forms described by the language standard, and produce instructions to carry out the expected tasks. The compiler may not understand code which does not conform to the language standard, and it is not the purpose of the compiler to guess at the intent of the author or fix errors in the code.

### Source File

A source file is a file which contains some or all of the code for a program. A source file is the conventional means by which the compiler reads code as input. As a means to differentiate UlinC source files from other common file types, and to make identification easier: it is conventional that a UlinC source file be suffixed with the *.ulinc* file extension.

All of the source files and code for a program are collectively known as the **source code** of a program.

### Literals

A literal is a textual representation of an actual value in code. For instance, the literal `5` represents the actual value `5`. Literals are alphanumeric in nature, meaning that they are composed of letters and numbers. Any literals which represent text are expressed as *strings*, using quotation marks:

```
12345 // A numeric literal
"12345" // A string literal
"Hello World!" // A string literal
```

### Symbols

A symbol is a word or group of characters that serves to identify something in a program. Symbols include the names of functions, the names of types, variables, keywords, and literals. Symbols which are the names of types or functions are called *identifiers*. Valid identifiers in UlinC must *only* contain:
- Uppercase and lowercase letters ([A-Z], [a-z])
- Underscores (_)

### Scope

A scope is a section within a program. All locals defined within a section are discarded when the scope exits, unless ownership of the local has been transferred to another scope. Scopes are defined as existing between two curly brackets:

```
{
	// This is a scope
}
```

Scopes can be attached to almost any statement or expression, such as a method signature, a loop statement, or a type definition.

### Variables

Variables (or *locals*) are temporary instances of objects which only exist until the end of the current scope. They include function parameters, as well as locally declared instances.

### Functions

A function is a section of code defined by a method signature, as well as a method body. A method signature contains the return type of the method, as well as the name of the method and the paramether list for the method:

```
int methodName(int x) {
	// method body
}
```

### Objects

UlinC is an Object Oriented programming language. An Object is a container which holds related information and functionality. 

Objects are central to UlinC's goal of being simple and effective.

### White-space

Whitespace (or white-space) in a program is the combination of characters such as spaces, newlines, tabs etc... used to separate symbols from one another. Whitespace also contributes to the readability of source code, and it is conventional that that UlinC code be properly indented and spaced to a reasonable degree. However, all whitespace is treated equally, and is not processed by the compiler.

There are a few exceptions to this, which are covered in [another section].

### Comments

Comments provide the developer with a way to annotate a section of the program, quickly write documentation, or lay out future changes in functionality. Comments are not evaluated by the compiler, and are not included in the compiled program. UlinC provides comment functionality in two forms; single-line and multi-line.

Single-line comments start with two forward slash characters "//", and extend until the next line:

     // This is a single-line comment

Multi-line comments start with a forward slash followed by an asterisk "/\*", and end with an asterisk followed by a forward slash "\*/":

     /* This is a multi-line comment
         Information can be placed on any line between the start and end
     */
Multi-line comments do not necessarily need to be on multiple lines, but that is their intended functionality

### Statements

Statements are the instructions in a program. They are processed by the compiler and converted into machine-readable code, which a computer executes to carry out tasks. Statements begin with any valid combination of symbols, and end with a semi-colon ";".

     print("Hello World!"); // This is a statement

Statements are conventionally written on individual lines, but it is possible (and can be desirable) to write multiple statements on a single line, or to write a single statement on several lines. This is done sometimes to make code more readable.

### Expressions

Expressions are statements which use one or more Operators [TODO].