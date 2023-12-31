# VM Translator

This project consists of three Python files designed to facilitate the
translation of VM code (Virtual Machine code) into ASM code (Hack assembly code).


# File Descriptions

### Main.py:
This script serves as the entry point for the VM Translator.\
It takes a path as an argument and translates all the VM files in that path into corresponding assembly code.\
The translated code is written to an output file with the same name as the input file but with a ".asm" extension.

### Parser.py:
The Parser class in this file is responsible for handling the parsing of a single .vm file.\
It reads VM commands, parses them, and provides convenient access to their components.\
The file also contains detailed information about the VM Language Specification and the types of commands it supports.

### CodeWriter.py
The CodeWriter class in this file translates VM commands into Hack assembly code.\
It includes methods for writing arithmetic, push, pop, label, goto, if-goto, function, call, and return commands.\
Additionally, it contains a method to initialize the VM, write_boot, which sets up the initial state of the Hack machine.


# Usage

To run the program enter:

```sh
python Main.py <input path>
```

Replace <input path> with the path to your VM files directory.

Example:  
Given one vm input file containing the following VM commands:

```sh
push constant 3030
pop pointer 0
```

The program will output the following asm file:

```sh
@256
D=A
@SP
M=D
@$ret.0
D=A
@SP
M=M+1
A=M-1
M=D
@LCL
D=M
@SP
M=M+1
A=M-1
M=D
@ARG
D=M
@SP
M=M+1
A=M-1
M=D
@THIS
D=M
@SP
M=M+1
A=M-1
M=D
@THAT
D=M
@SP
M=M+1
A=M-1
M=D
@SP
D=M
@5
D=D-A
@0
D=D-A
@ARG
M=D
@SP
D=M
@LCL
M=D
@Sys.init
0;JMP
($ret.0)
@3030
D=A
@SP
A=M
M=D
@SP
M=M+1
@SP
AM = M-1
D=M 
@THIS
M=D
```
