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
- #voidFunctino is a function with the void keyword
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
