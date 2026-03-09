# User-defined function basics
## Functions(general)
- used to reduce redundancy
- #function : grouping of predefined statements for repeatedly used operations
- functions prevent main from being long and confusing
## Basics of function
- #function is named list of statements
- #functionDefinition consist of new functions name and a block of statmenets
- #function call is invocation of function name causing functions statements to execute
- #block is a list of statement surrounded by braces
## Returning a value from a function
- function may return one value using a #returnStatement
- void return type means the function returns no value
## Parameters
- #parameter is a function input specified in function definition
- #argument is a value provided to a function's parameter during a function call
- syntax for defining function and args is `type functionName(type arg1, type arg2){...};`
- syntax for passing arg is similar to other langs `FunctionName(arg);`
- cannot use expressions as args ie `var + 3` cannot be a arg
# Print functions
## Printing from a function
- #void keyword indicates a function that doesn't return a value
- #voidFunction is a function with the void keyword
- used to reduce outputs in main()
- basically this is used to eliminate the return statement
## Calling a print function multiple times
- Good for concise code and reusability of print functions
# Reasons for defining functions
## Improving readability
- Decomposing a program into functions can greatly aid program readability
## Modular and incremental program development
- #modularDevelopment is the process of dividing a program into separate modules that can be developed and tested separately and then integrated into a single program
  #incrmentalDevelopment is a process in which a programmer writes, compiles and tests a small amount of code then repeats
- #functionStub is a function definition whose statements have not yet been written
	- A function stub is a complete function definition but lacks the statements to implement the desired computation
	- Program can be compiled and executed and a user can enter numbers but then the FIXME message will be printed
	- Can later complete function
## Avoid writing redundant code
- Each function should have easily-recognizable behavior
- `main()` should be easily understandable via the sequence of function calls
- functions shouldn't have more than 30 lines of code
# Writing mathematical functions
## Mathematical functions
- functions are defined to compute mathematical calculations involving several numerical parameters and returning numerical result
## Calling functions in expressions
- void return type cannot be used within an expression instead being used
## Modular functions for mathematical expressions
- modularity allows more complex functions to incorporate simpler functions
# Functions with branches
- may include branches and other statements
# Unit testing (functions
- *Good practice is to test small parts of the program individually, before testing the entire program, which can more readily support and fixing bugs*
- #unitTesting is the process of individually testing small parts of a program
- unit test in conducted by creating a #testBench
	- This is a separate program that checks whether the function returns correct output
	- Each unique set of values is known as #testVector 
- `assert()` enables compact readable test harnesses, and also eases the task of examining the program's output for correctness
- A program without detected errors would simply output `"Testing started"` followed by `"Testing completed"`
- A programmer should choose test vectors that thoroughly exercise a function
- Ideally the programmer would choose test vectors that thoroughly exercise a function
- Good test vectors also include #borderCases that represent fringe scenarios
# How functions work
- Each function call creates a new set of local variables, forming part of what is known as a #stackFrame
- return causes those local variables to be discarded

# Pass by reference
- a functions return construct can only return one value
- normal parameters are #passByValue
	- meaning the argument's value is copied into a local variable for the parameter
- #pass-by-reference doesn't create a local copy of the argument, but rather the parameter refers directly to the argument variable's memory locaiton
- Appending & to a parameter's data type makes the parameter pass-by-reference type
- Pass by reference parameters should be used sparingly
- For the case of two return values, commonly a programmer should instead create two functions
## Reference variables
- A #reference is a variable type that refers to another variable
- Programer must initialize each reference with an existing variable, which can be done by initializing the reference variable when the reference is declared
# Using pass by reference to modify string/vector parameters
- Functions commonly modify a string or vector
- Sometimes a programmer defines a vector or string as pass by reference even though the function doesn't modify the parameter to prevent the performance and memory overhead of copying the arg that mould otherwise occur
- #const can be prepended to a function's vector or string parameter to prevent the function from modifying the parameter
- In the cases of small vectors it is better to make a copy than to use passing by reference
- When you don't want modifications to the vector, you would make the vector a const
# Functions with C string parameters
- Functions commonly modify Cstrings. Te following function modifies a string by replacing spaces with hyphens
- The parameter definition `[]` to indicate an array pattern 
	- Ex: `void Funciton(char charArray[]) {...}`
- A  programmer can explicitly define an array parameter as a pointer using `char* charArray` instead of `char chararray[]` 
- C strings are automatically passed using a pointer
# Scope of variable/function definitions
- The name of a defined variable or function item is only visible to part of a program, known as the item's #scope 
- variables declared in a function has a scope limited to inside that function
- Because a compiler scans a program line-by-line form top to bottom the scope starts after the declaration
# Default parameter values
- Sometimes a function's last parameter (or last few should be optional)
- A function can have a #defaultParameterValue for the last parameter meaning a call can optionally omit a corresponding arg
- This is determined by assigning it in the function definition
# Function name overloading
- sometimes there are two functions with the same name but differing in the number or types of parameters, known as #functionNameOverloading
- The compiler determines which function to call based on arg types
- More than two sam-named functions is allowed as long as each has a distinct param types 
- You cannot use different return types across both functions
# Parameter error checking
##  Verifying parameter values
- Function expects param values to be within some range
- *Good practice is to check that a param's value is within an expected range*
- If not in range the function might take one or more of various actions like outputting an error message, assigning a valid value, returning a value indicating failure, exiting the program, etc.
# Preprocessor and include
- #preprocessor is a tool that scans the file from top to bottom looking for any lines that begin with \#, known as a #hashSymbol
- Each such line is not a program statement but directs the preprocessor to modify the file in some way before compilation continues, each such line being known as a #preprocessorDirective 
- *Good practice is to use a .h suffix for any file that will be included in another file h is short for header, to indicate that the file is intended to be included at the top  (or header) of other files*
- the characters surrounding the filename determine where the preprocessor looks for the file
	- `#include "myfile.h"` a file name in quotes means that the preprocessor will look for the file in the same folder/directory as the including file
	- `#include <stdfile>` a filename in angle brackets causes the preprocessor to look in the system's standard library folder/directory
- The big take away is that quotes are for files and angle brackets are for system standard library folder/directory
# Separate files
- One benefit of separating files out is preventing a main file from becoming too large to manage
- Another benefit is that the separated part could be useful in other programs
- #headerFileGuards are preprocessor directives which cause the compiler to only include the contents of the header file once
- `#define FILENAME_H` defines the symbol `FILENAME_H` to the preprocessor
- The `#ifndef FILENAME_H` and `#endif` form a pair that instructs the preprocessor to process the code between the pair only if `FILENAME_H` is not defined ("idndef") is short for if not defined
- *Good practice is to guard every header file*
```
#ifndef FILENAME_H
#define FILENAM_H

// Header file contents

#endif
```



## 

Figure 6.18.2: Compiling multiple files together.

|                                                                                                                                                                                                                  |                                               |
| ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------- |
| Without `#include "threeintsfcts.h"` in main.cpp                                                                                                                                                                 | With `#include "threeintsfcts.h"` in main.cpp |
| > g++ -Wall main.cpp threeintsfcts.cpp<br>main.cpp: In function  int main():<br>main.cpp:8: error: ThreeIntsSum was not declared in this scope<br>main.cpp:9: error: ThreeIntsAvg was not declared in this scope | > g++ -Wall main.cpp threeintsfcts.cpp<br>>   |
- Header files should contain function declarations for functions defined in another file
- Guarding a header file prevents multiple inclusion of that file by the preprocessor