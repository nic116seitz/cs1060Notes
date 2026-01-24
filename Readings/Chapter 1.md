# Programming (general)
## Computer program basics
- #program consists of instructions executing one at a time
	- Basic instruction types:
		- #Input: a program gets data from file, keyboard, touchscreen network, etc
		- #Process: program performs computations on data such as adding values
		- #Output: Program puts the data somewhere like file, screen, network, etc
- Data is referred to with #variables
## Computational thinking
- Mathematical thinking became increasingly important throughout the industrial age to enable people to successfully live and work in the information age, many people believe #computationalThinking will become increasingly important for work and everyday life
- #computationalThinking: Creating a sequence of instructions to solve a problem
- #algorithm: A sequence of instructions that solves a problem
# Programming basics
## First program 
- program starts in `main()` executing the statements within main's braces
- Each statement typically appears alone on a line and ends with a semicolon
- int wage statement creates an int var named wage
- the wage = 20 assigns wage with 20
- the cout statement outputs various values
- the return statement ends the program (0 tells the OS the program ended without error)

```
#include <iostream>
using namespace std;

int main() {
	int wage;
	
	wage = 20;
	
	cout << "Salary is ";
	cout << wage * 40 * 52;
	cout << endl;
	
	return 0;
}
```

## Basic input
- Programs get input value
- Then perform processing on input
- and then output values to screen or elsewhere
- cin is short for characters in
## Basic output: Text
- #cout construct supports output
	- it is short for characters out
	- Syntax: `cout << "desired output text";`
		- Text in double quotes is known as a #stringLiteral
- `cout << endl;` starts a newline output called #newline
## Outputting a variable's value
- Outputting a variable's value is achieved via: `cout << x;`
	- *There are no quotes around x*
- If you don't add endl the code will not print to a new line
## Outputting multiple items with one statement
- Single output statements are used for each line o of output by combining outputting of text, var values and a new line. 
- Items are separated by `<<` 
- Combining improves readability because the program's code corresponds more closely to the program's output
# Console input
## Console input with prompts
- A #console is a text-based interface for viewing program output and entering user input
- 1 Common approach for console-based programs is using prompts for each user input
- A #prompt is a message that indicates what the next expected user input is
- Cout is used to generate prompts
- These are then immediately followed by a cin statement
- A program will wait indefinitely while executing a cin statement
- The prompt must be placed before the cin statement 

## Console inputs without prompts
- This is another approach where inputs are entered using tab or spaces to separate them 
- If this approach is taken and there is a mismatch between the number of inputs expected vs the number of inputs entered then the extra inputs will be ignored


# Comments and whitespace
## Comments
- A #comment is a text programmers adds to make code easier for other humans to understand
- #comment is ignored by the compiler
- There are two types of comments:
	- single line which starts with // 
	- multi-line which starts with /* and ends with \*/
	- Multi-line comments are also known as #blockComment 
## Whitepace
- #whitespace refers to blank spaces between items within a statement and blank lines between statements (called newlines)
- A compiler ignores most whitespace
- *Good practice is to deliberately and consistently use whitespace to make a program more readable*
- Conventions around whitespace are defined by a company, team instructor, etc.
- Ex:
	- Use blank lines to separate conceptually distinct statements
	- Indent lines the same amount
	- Align items to reduce visual clutter.
	- Use a single space before and after any operators like =, +, \* or <<
- Spaces are not always ignored by the compiler
- Ex:
		- Print statements where the statement contains a space such as `cout << "Enter input: "`
- Spaces around operators will be ignored

# Errors and warnings
## Syntax errors
- One kind of mistake is #syntaxError
- It is violating a programming language's rules on how symbols can be combined to create a program
- Ex:
	- Forgetting to end a statement with a semicolon
- Compiler generates a message when encountering a syntax error
## Unclear error messages
- Compiler error messages are often unclear or even misleading
- It is a best guess of what went wrong
- Sometimes the error can be on a line before the line that the compiler is throwing the error for
## Fixing the first error
- Some errors create an upsetting long list error messages.
- *Good practice is to focus of fixing just the first error reported by the compiler and then recompiling*
## Logic errors
- Syntax errors are detected by the compiler
- This means syntax error is a type of error called #compile-timeError
- If a program successfully compiles but doesn't work it means it has other types of errors
- #logicError also known as a #bug is an error that that occurs while the program runs
- The term #bug was popularized in 1947 when engineers discovered their program was not working because a moth was stuck in one of the relays
	- The moth was taped into their engineering log book and is still preserved today
- *Good practice especially for new programmers is to compile after writing only a few liens of code, rather than writing tens of lines and then compiling.*
## Compiler warnings
- A compiler will sometimes report a #warning 
- This doesn't stop the compiler from creating an executable but indicates possible logic error
- One example can be in a divide by 0 error 
- The program will compile but will show an error
- *Good practice is to create programs without errors*
# Computers and programs (general)
## Switches
- Switches turn objects on and off 
- it controls whether or not electricity flows through a wire
- In 1900 people created special switches that could be controlled electronically, rather than the person moving the switch up or down
- Engineers realized that they could use electronically controlled switches to perform simple calculations
- Positive voltage = 1
- Negative voltage = 0
- 1s and 0s are known as #bits (binary digits)
## Processors and memory 
- #processors where created to process (execute) a list of desired calculations
- Each calculation called an #instruction
- Instructions were specified by configuring external switches
- Instructions are stored in a memory
- #memory is a circuit that can store 0s and 1s in each of a series of thousands of addressed locations, like a series of addressed mailboxes that each can store an envelope
- Instructions are also stored in memory locations as 0s and 1s
- A computer is basically a processor interacting with a memory

## Instructions

Table 1.6.1: Sample processor instructions.
X, Y, Z and num are each an int

|                     |                                                                                       |
| ------------------- | ------------------------------------------------------------------------------------- |
| **Add X, \#num, Y** | Adds data in memory location _X_ to the number _num_, storing result in location _Y_. |
| **Sub X, \#num, Y** | Subtracts _num_ from data in location _X_, storing result in location _Y_.            |
| **Mul X, \#num, Y** | Multiplies data in location _X_ by _num_, storing result in location _Y_.             |
| **Div X, \#num, Y** | Divides data in location _X_ by _num_, storing result in location _Y_.                |
| **Jmp Z**           | Tells the processor that the next instruction to execute is in memory location _Z_.   |
- The programmer-created seq of instructions is called a #program, #application or #app
## Writing computer programs
- instructions are represented with 0s and 1s 
- This is known as #machineInstructions
- A sequence of machine instructions together form an #executableProgram
- Because binary is hard to understand programmers created programs called #assemblers to automatically translate human readable instructions 
- This is known as #assembly language instructions
- in the 1960s and 70s programmers created #high-levelLanguages to support programming formulas or algorithms
- To support these high-level languages programmers created #compilers
- #compilers are programs that automatically translate high-level language programs into executable programs

# IDE
## Intro to IDEs
- #IDE stands for integrated development environment
- Is software that integrate a text editor and a compiler with additional tools
## Common features
- Syntax highlighting
- Automatic delimiter completion
	- This is the function that adds matching closing bracket
- Automatic indentation
- Shortcuts
- File manager
## Console and cli in an IDE
- Ide typically includes a console for user input and program output
- #console or #terminal is a text-based interface that allows a user to run programs, enter input and view program output
- A console's #command-lineInterface (CLI) is an interface that allows a user to enter the commands to run programs and work with files
	- You can run program with command line args
# Computer tour
- Computer originally referred to a person that performed computations by hand
- 40s and 50s this changed to large machiens
- 70s/80s the term expanded to refer to home/office computers 
	- These were known as PCs (personal computer)
## Components of a computer
- Input/output devices
	- screen
	- keyboard
	- mice
	- touchscreens
	- microphones
	- speakers
	- printers
	- USB interfaces
	- I/O devices are commonly called peripherals
- Storage
	- SSD uses flash memory to store files and other data, such as program files, song/movie files or office documents.
		- SSDs are non-volatile meaning that they maintain their contents even when turned off
- Memory:
	- #RAM (random-access-memory) temporarily holds data read from storage and is designed such that any address can be accessed faster than an SSD and disk
	- random-access comes from the ability to access any memory location quickly and in arbitrary order without having to spin a disk to get to the right position
	- Ram is more expensive per bit due to RAM's speed
	- Ram loses its contents when powered off
- Processor
	- #processor runs the comps programs, reading and executing instructions from memory, performing operations and reading/writing data to and from mem
	- When powered on the processor starts executing the program whose first instructions is at mem location 0
		- This program is generally BIOS (basic input output system)
			- This sets up basic peripherals
	- After starting BIOS the processor starts OS
	- #operatingSystem allows a user to run other programs and interfaces with many other peripherals
	- Processors are also called CPUs (central-processing-unit)
	- Because speed is important a processor may contain a small amount of RAM on its own chip this is called #cache 
- Clock
	- A processor's instruction execute at a rate governed by the processor's #clock 
	- This ticks at a specific speed such as 1GHz (1 billion ticks per second)
- Computers typically run multiple programs simultaneously such as a web browser, an office app, etc.
- After computers invented and occupied rooms engineers created smaller switches called #transistors these were later integrated onto a single chip called #integratedCircut
- Engineers continued to make transistors smaller leading to #MoorsLaw The doubling of IC capacity roughly every 18 months, which continued for several decades
- 1971 Intel produced the first single-IC processor named the 4004 
# Language history
- 1978 Brian Kernighan and Dennis Ritchie at ATT Bell Labs published a book describing a new high-level language with the simple name C being named after another language called B
- C was dominant during the 80s & 90s
- 1985 Bjarne Stroustrup published a book describing C-based lang called C++
	- Added constructs to support the style of programming known as OOP
	- ++ comes from the operator in c that increases number
	- C/++ are both popular first langs for programming comps, 
		- They are used for a variety of desktop and embedded sys
# Problem solving
## Programming langs vs problem solving
- creating a program involves more than just knowing a programming lang
- Programming is largely about #problemSolving

## Precision, logic, and computational thinking
- Many people find that programming encourages precise logical thought that can lead to better writing and speaking
- Though process need to build correct precise and logical programs is sometimes called #computationaThinking
# Why whitespace and precision matter
## Whitespace and precise formatting
- #whitespace is blank or newline
- students output must match exactly (including whitespace)