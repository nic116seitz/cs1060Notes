# Variables and assignments (general)

## Variables and assignments
- #variable is an named item
	- such as x or numPeople
	- this is used to hold a value
- #assignment assigns a variable with a value, such as `x = 5`
	- An assignment's left side must be a variable
	- right side can be an expression
## Assignments with variable on left and right
- Variable can appear on both sides of an assignment 
- increasing a value by one is known as #incrementing
# Variables (int)
## Variable declarations
- #variableDeclaration is a statement that declares a new variable, specifying the variable's name and type
- The compiler allocates  a memory location for the variable 
- #Allocation is the process of determining a suitable memory location to store data like variables
- When assignment happens the processor writes the value into the variable's memory location
- Declaration of a variable is required before assignment so that a variable's memory location is known
- Mem locations are not known to the programmer
#### Compiler optimization
- Modern compilers may ignore unused variables, allocate variables on the stack or use registers for variables

## Assignment statements
- An #assignmentStatment assigns the variable on the left-side of the = with the current value of the right-side expression
- An #expression may be a num like 80, a var name like numApples or a calc like numApples + 1 
- An int like 80 appearing in a expression is known as a #integerLiteral 
- Though not required an int variable is often assigned an initial value when declared 
## Assignment statement with same var on both sides
- Commonly a var appears on both the right and left side of the = operator
- This will reassign the variable with the value after the operation on the right completes
- Ex: 
```
int numItms = 5;

numItems = numItems + 1;
# In this case numItems would be reassigned to 6 by the end
# of the run of the program

```
## Common errors
- Reading a variable that has not yet been assigned a value
	- When this happens the variable's mem location contains some unknown value
	- This is commonly but not always 0
**Compound assignment operators like `+= or -=` work in C++**
# Identifiers
## Rules for identifiers
- Name for a variable or a function is called an #identifier 
- Identifier must be a sequence of letters and digits
- start with a letter or underscore
- Identifiers are #caseSensitve
- #reservedWord is a part of the language like `int` or `short` or `double` aka #keyword
	- Programmers cannot use reserved words as an identifier 
## Style guidelines for identifiers
- Two common conventions for naming variables
	- camelCase: capitalizing every word in a name except the first word
	- Underscore Separated: all words are lowercase but are separated by underscore
- There is no universally better convention it is simply important to stay consistent
## 

Table 2.3.1: C++ reserved words / keywords.

|                                                                                                                                                                                                                                                                                                                                    |                                                                                                                                                                                                                                                            |                                                                                                                                                                                                                                                                                                                                |                                                                                                                                                                                                                                                                         |
| ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| alignas   (since C++11)  <br>alignof   (since C++11)  <br>and  <br>and_eq  <br>asm  <br>auto  <br>bitand  <br>bitor  <br>bool  <br>break  <br>case  <br>catch  <br>char  <br>char16_t   (since C++11)  <br>char32_t   (since C++11)  <br>class  <br>compl  <br>const  <br>constexpr   (since C++11)  <br>const_cast  <br>dcontinue | decltype   (since C++11)  <br>default  <br>delete  <br>do  <br>double  <br>dynamic_cast  <br>else  <br>enum  <br>explicit  <br>export  <br>extern  <br>false  <br>float  <br>for  <br>friend  <br>goto  <br>if  <br>inline  <br>int  <br>long  <br>mutable | namespace  <br>new  <br>noexcept   (since C++11)  <br>not  <br>not_eq  <br>nullptr   (since C++11)  <br>operator  <br>or  <br>or_eq  <br>private  <br>protected  <br>public  <br>register  <br>reinterpret_cast  <br>return  <br>short  <br>signed  <br>sizeof  <br>static  <br>static_assert   (since C++11)  <br>static_cast | struct  <br>switch  <br>template  <br>this  <br>thread_local   (since C++11)  <br>throw  <br>true  <br>try  <br>typedef  <br>typeid  <br>typename  <br>union  <br>unsigned  <br>using  <br>virtual  <br>void  <br>volatile  <br>wchar_t  <br>while  <br>xor  <br>xor_eq |
# Arithmetic expressions (general)
## Basics
- #expression is any individual item or combo of items, like var, literal, operators and parentheses 
	- common place these are used is on the right side of an assignment statement
- #literal specific value in code like 2
- #operator is symbol that performs a built-in calc like +
- common programming operators are shown below


Table 2.4.1: Arithmetic operators.

| Arithmetic operator | Description                                                                                                |
| ------------------- | ---------------------------------------------------------------------------------------------------------- |
| +                   | The addition operator is +, as in x + y.                                                                   |
| -                   | The subtraction operator is -, as in x - y. Also, the - operator is for negation, as in -x + y, or x + -y. |
| *                   | The multiplication operator is *, as in x * y.                                                             |
| /                   | The division operator is /, as in x / y.                                                                   |
## Evaluations of expressions
- An expression evaluates to a value, which replaces the expression
- #prescedenceRules = pemdas

## 

Table 2.4.2: Precedence rules for arithmetic operators.

| Operator/Convention | Description                                                                                        | Explanation                                                                                                                                                                                    |
| ------------------- | -------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **( )**             | Items within parentheses are evaluated first                                                       | In 2 * (x + 1), the x + 1 is evaluated first, with the result then multiplied by 2.                                                                                                            |
| **unary -**         | - used for negation (unary minus) is next                                                          | In 2 * -x, the -x is computed first, with the result then multiplied by 2.                                                                                                                     |
| *** / %**           | Next to be evaluated are *, /, and %, having equal precedence.                                     | (% is discussed elsewhere)                                                                                                                                                                     |
| **+ -**             | Finally come + and - with equal precedence.                                                        | In y = 3 + 2 * x, the 2 * x is evaluated first, with the result then added to 3, because * has higher precedence than +. Spacing doesn't matter: y = 3+2 * x would still evaluate 2 * x first. |
| **left-to-right**   | If more than one operator of equal precedence could be evaluated, evaluation occurs left to right. | In y = x * 2 / 3, the x * 2 is first evaluated, with the result then divided by 3.                                                                                                             |
## Style: Single space around operators
- *Good practice is to include a single space around operators for readability*
- minus used to represent a negative is known as a #uranaryMinus
## Compound operators
- Special operators are called #compoundOperators
- shorthand for assignment / other operation
- They are:
	- -=
	- \*=
	- \+=
	- /=
	- %=

- #IncrementalDevelopment is the process of writing compiling and testing a small amount of code then writing and compiling a small amount more
# Floating point numbers (double)
## Floating-point (double) variables
- #floatingPointNumber is a real number containing a decimal point that can appear anywhere or **float** in the number
- #double variable stores a floating point number
- #floating-pointLiteral is a number with a fractional part
- *Good practice is to always have a digit before the decimal point, as in 0.5 since .5 may be mistaken for 5*
## Choosing a var type
- Depends on the type of value the var will hold
	- Int generally used for values that are counted
		- Cars
		- Pizzas
		- -Days
	- Floating-point variables are typically used for measurements
		- Temp
		- Meters
## Floating-point division by zero
- Many languages create a divide by zero error when dividing by 0
- C++ creates an infinite number either infinity or -infinity
- This is dependent on operand
- if dividend and divisor in floating-point division are both = 0 the division results in NaN
- #notANumber #NaN indicates unrepresentable or undefined value
## Manipulating floating-point output
The syntax for specify precision for a float is as follows
```
x = 3 # This determines the number of places                       # after the float to use

cout << fixed << setprecision(x) << 3.1244 << endl;
```
- The example above will output 3.124
- #setprecison will round the the number at the end of the specified rounding point
- When dealing with floats everything in
## Scientific notation for floating-point literals
- Good for representing floats much greater or much less than 0
- #scientificNoation is written using an e preceding the power of 10 exponent
- In the case of a negative exponent that shifts the number to the left that amount of places (including the 1s place)
	- Ex:
		- 7.2e-4 = 0.00072
- For large numbers the syntax is to use a float number and then use that as the base to calculate the exponential number needed
	- Ex:
	- 5.4e8 = 540,000,000
# Constant variables
- *Good practice is to minimize the number of literal nums in code*
	- This improves code readability
- An initialized variable whose value cannot change is called a #constantVariable
	- *Good practice is to name constant variables using uppercase letters with words separated by underscores*
- `const` keyword is use to declare the variable as a constant then what type of number it is `float` or `double`
# Using math functions
## Basics
- Standard #mathLibrary has about 20 math operations, known as functions
-  You can include the lib and use those math functions
- #functon is a list of statements that is executed by invoking the function's name
	- This is a #functionCall
- Any function input values or #arguments appear within (), separated by commas if more than one

Table 2.10.1: A few common math functions from the math library.

| Function  | Behavior            | Example                         |
| --------- | ------------------- | ------------------------------- |
| sqrt(x)   | Square root of x    | sqrt(9.0) evaluates to 3.0.     |
| pow(x, y) | Power: x^y          | pow(6.0, 2.0) evaluates to 36.0 |
| fabs(x)   | Absolute value of x | fabs(-99.5) evaluates to 99.5   |
Other functions are log (natural log) log2 (log base 2) log10 (log base 10) exp (raising e to a a power) ceil(rounding up) floor (rounding down) various trig functions like sin, cos, tan and more

# Integer division and Modulo
## Division: Integer rounding
- when the operands of the / are ints, the operator performs integer division which doesn't generate any fraction
## Divide by 0
- #divide-by-zeroError occurs at runtime if a divisor is 0
	- this is an example of a #runtimeError 

## Modulo
- This is the remainder of division between two ints
- Both of the numbers in a Modulo must be ints for it to work otherwise it will cause errors

## Type conversions
- #typeConversion is a conversion of one data type to another such as an int or a double
- Automatic conversions are known as #implicitConversion
- in the case of + or \* if one operand is a double then the other is automatically converted to a double
- For assignments the right side type is converted to the left side type
- double to int conversion drops anything past the floating point

## Type casting
- sometimes the type must be explicitly converted
- #typeCast is what does this
- #static_cast operator is the operator that does this in the case of C++

## Common errors
- accidentally perform integer division when floating-point division was intended
- Cast the entire result of int division rather than the operands thus not obtaining the desired floating-point division
# Binary
- Normally a programmer can think in terms of base ten numbers
- However, a compiler must allocate some finite quantity of bits for a variable
- Quantity of bits limits the range of numbers that the var can represent
- Processor stores a number using base 2 #binaryNumber
- #decimalNumber each digit must be 0-9 and each digit's place is weighed by increasing powers of 10
- in #base2 each digit must be 0-1
- Each digit's place is weighed by increasing powers of 2
# Characters
## Basics
- a var of #char type can store a single character like the letter m
- #characterLiteral is surrounded with single quotes
	- Ex:
		- `mychar = 'm'`
## Getting a character from input
- cin can be used to get one character from input
- Character is internally stored as number
- Think ASCII
- Literal numbers are stored in memory as their value as opposed to ASCII
## Escape sequences
- These are non visible characters that have encoding in ASCII

Table 2.14.2: Common escape sequences.

| Escape sequence | Char         |
| --------------- | ------------ |
| \n              | newline      |
| \t              | tab          |
| \\'             | single quote |
| \\"             | double quote |
| \\\             | backslash    |
## Common errors
- Using double quotes instead of single quotes around a single character
	- This causes compiler error
# Strings
## Strings and string literals
- #string is a sequence of characters
- #stringLiteral surrounds a characters sequence with double quotes
## String variables and assignment
- some var should hold a string
- String datatype is not builtin to C++
- Can be used after adding `#include <string>`
- You can also initialize a string variable during declaration
## Getting a string without whitespace from input
- #whitespaceCharacter is a character used to represent horizontal and vertical spaces in text
	- Includes:
		- Space
		- Tab
		- newline char
- In order to remove spaces from a input breakup the input of the user using multiple `cin`
## Getting a string with whitespace from input
- #getline the getline function allows you to get the the entire line of input
# Integer overflow
- Int var cannot store a number larger than the maximum supported by the var's datatype
- *common error is to try to store a value greater than about 2 billion into an int variable
	- This results in overflow
- Declaring a variable of type `long long`
- Most compilers detect when a statement assigns to a var that a literal constant so large as to cause overflow
- The compiler may not report a syntax error but may output a #compilerWarning
	- This is a message that indicates that there may be a potential problem
	- GNU compiler outputs the message:
		- "warning: implicit constant conversion"
		- *Good practice is to not ignore compiler warnings*

# Numeric data types
- int and double are the most common numeric data types
- There are others as well

Table 2.17.1: Integer numeric data types.

| Declaration      | Size (bits) | Number range                                            |
| ---------------- | ----------- | ------------------------------------------------------- |
| char myVar;      | 8           | -128 to 127                                             |
| short myVar;     | 16          | -32,768 to 32,767                                       |
| int myVar;       | 16/32       | (32-bit) -2,147,483,648 to 2,147,483,647                |
| long myVar;      | 32/64       | (32-bit) -2,147,483,648 to 2,147,483,647                |
| long long myVar; | 64          | -9,223,372,036,854,775,808 to 9,223,372,036,854,775,807 |
- int is the most commonly used integer type
- #long_long is used for integers expected to exceed 2 billion
- short is rarely used
	- Mainly used when you want to save memory when storing many smaller numbers

Table 2.17.2: Floating-point numeric data types.

| Declaration | Size    | Supported number range  |
| ----------- | ------- | ----------------------- |
| float x;    | 32 bits | -3.4x1038 to 3.4x1038   |
| double x;   | 64 bits | -1.7x10308 to 1.7x10308 |
- Float data-type is used to save memory similar to how short does the same with ints
- If a variable is assigned with a value larger than its maximum supported value an #overflow occurs
- On some processors (especially low cost used for "embedded" computing like in a care or medical device) floating point calculations run slower than int calculations
- Floating-point types are typically only used when really necessary
# Unsigned
- When you know the outcome of an operation will be positive than you can use the word unsigned


Table 2.18.1: Unsigned integer data types.

| Declaration               | Size    | Supported number range          | Standard-defined minimum size |
| ------------------------- | ------- | ------------------------------- | ----------------------------- |
| unsigned char myVar;      | 8 bits  | 0 to 255                        | 8 bits                        |
| unsigned short myVar;     | 16 bits | 0 to 65,535                     | 16 bits                       |
| unsigned long myVar;      | 32 bits | 0 to 4,294,967,295              | 32 bits                       |
| unsigned long long myVar; | 64 bits | 0 to 18,446,744,073,709,551,615 | 64 bits                       |
| unsigned int myVar;       | 32 bits | 0 to 4,294,967,295              | _16 bits_                     |
- signed numbers use the leftmost bit to store a number's sign
- Signed number have a more complicated representation called two's complement
- The smallest a unsigned short can take is 0
# Random numbers
## Generating a random number
#random
- The `rand()` function in C standard library calls a random int every time the function is called
	- This is done in the rang 0 to RAND_MAX
- Modulo is used to limit the range of random numbers used
- `rand() % 3` can generate the numbers 0 1 2
## Specific ranges
- First you want to determine the number of possible values you want to include in random
- Then you ad x to those numbers to determine your range
	- So if you want to capture 10 - 30 you would do rand `(rand() % 10) + 10`
## Pseudo-random
- ints generated by rand() are pseudo random
	- This is because rand() yields the same sequence of values
- rand uses a built-in integer known as #seed
	- by default the seed is 1
	- Programmer can use a different seed by calling `srand(seedNum)`
- Another way to get a new seed every  time is to call the #time function `time()`
	- This will generate a new seed every time because of the fact that time is changing each time the program is run
- Formula for setting upper and lower bounds to a random number:
	- `(rand() % (upperBound - lowerBound + 1)) + lowerBound`
# Debugging
- #debugging is the process of determining and fixing the cause of a problem in a computer program
- #troubleshooting is a synonym
- A common error is to try to debug without a methodical process
- An example of this process would be as follows:
	 1. Manually set a variable to a value
	 2. Insert print statements to observe variable values
	 3. Comment out unused code
	 4. Visually inspect the code
 - In the process of debugging it is important to add and remove debug statements with care
 # Auto (since C++11)
- The keyword #auto tells the compiler to determine the variable's type using the initial value given
## 

Table 2.21.1: Basic types found by the compiler given the initial value.

| Code                | Variable | Type found   |
| ------------------- | -------- | ------------ |
| `auto v = 2;`       | v        | int          |
| `auto w = 0.5;`     | w        | double       |
| `const auto x = 7;` | x        | const int    |
| `auto y = 'h';`     | y        | char         |
| `auto z = "apple";` | z        | const char * |
- Unless a a string is declared as the  variable it will follow the above shown constant char \*
## Printing the type of an auto variable
- During debugging a programmer may want to see if the compiler has correctly determined an auto variable's type
- #typeid operator reports a variable's type
- typeid's name() returns a string describing the variable's type
- type description is implementation-dependent
- g++ compiler uses "d" for double or "c" for char and "i" for int
- syntax for this is `typeid(x).name()` 
- When entering a string the output of the above will be PKc
	- This stands for:
		- P = pointer
		- K = constant
		- c = character
- when declaring the a type using auto this declaration stays regardless of what that variable's value is reassigned with
	- if auto is assigned with a double initially then even if the variable is reassigned with an int, the int it is reassigned with will be converted to a double
	- The same will happen if the initial statement is a type int then the variable is reassigned to a double
# Style guidelines
- #styleGuidelines 
## 

Table 2.22.1: Sample style guide.

|                                                                                                                                                                                                                                                                                 |                                                                                                                           |                                                                                                                            |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------- |
| Sample guidelines used in this material                                                                                                                                                                                                                                         | Yes                                                                                                                       | No (for our sample style)                                                                                                  |
| Whitespace                                                                                                                                                                                                                                                                      |                                                                                                                           |                                                                                                                            |
| Each statement usually appears on its own line.                                                                                                                                                                                                                                 | x = 25;<br>y = x + 1;                                                                                                     | x = 25;   y = x + 1;     // No<br>if (x == 5) { y = 14; }  // No                                                           |
| A blank line can separate conceptually distinct groups of statements, but related statements usually have no blank lines between them.                                                                                                                                          | x = 25; <br>y = x + 1;                                                                                                    | x = 25; <br>           // No<br>y = x + 1;                                                                                 |
| Most items are separated by one space (and not less or more). No space precedes an ending semicolon.                                                                                                                                                                            | C = 25;<br>F = ((9 * C) / 5) + 32;<br>F = F / 2;                                                                          | C=25;               // No<br>F = ((9*C)/5) + 32; // No<br>F = F / 2 ;         // No                                        |
| Sub-statements are indented 3 spaces from parent statement. Tabs are not used as tabs may behave inconsistently if code is copied to different editors.  <br>(Auto-tabbing may need to be disabled in some source code editors).                                                | if (a < b) {<br>   x = 25;<br>   y = x + 1;<br>}                                                                          | if (a < b) {<br>        x = 25;    // No<br>        y = x + 1; // No<br>}<br>if (a < b) {<br> x = 25;           // No<br>} |
| Braces                                                                                                                                                                                                                                                                          |                                                                                                                           |                                                                                                                            |
| For branches, loops, functions, or classes, opening brace appears at end of the item's line. Closing brace appears under item's start.                                                                                                                                          | if (a < b) {<br>   // Called K&R style<br>}<br>while (x < y) {<br>   // K&R style<br>}                                    | if (a < b) <br>{<br>   // Also popular, but we use K&R <br>}                                                               |
| For if-else, the else appears on its own line                                                                                                                                                                                                                                   | if (a < b) {<br>   ...<br>}<br>else { <br>   // Called Stroustrup style  <br>   // (modified K&R)<br>}                    | if (a < b) {<br>   ...<br>} else {<br>   // Original K&R style<br>}                                                        |
| Braces always used even if only one sub-statement                                                                                                                                                                                                                               | if (a < b) {<br>   x = 25;<br>}                                                                                           | if (a < b)  <br>   x = 25;  // No, can lead to error later                                                                 |
| Naming                                                                                                                                                                                                                                                                          |                                                                                                                           |                                                                                                                            |
| Variable/parameter names are camelCase, starting with lowercase                                                                                                                                                                                                                 | int numItems;                                                                                                             | int NumItems;   // No<br>int num_items;  // Common, but we don't use                                                       |
| Variable/parameter names are descriptive, use at least two words (if possible, to reduce conflicts), and avoid abbreviations unless widely-known like "num". Single-letter variables are rare; exceptions for loop indices (i, j), or math items like point coordinates (x, y). | int numBoxes; <br>char userKey;                                                                                           | int boxes;   // No<br>int b;       // No<br>char k;      // No<br>char usrKey; // No                                       |
| Constants use upper case and underscores (and at least two words)                                                                                                                                                                                                               | const int MAXIMUM_WEIGHT = 300;                                                                                           | const int MAXIMUMWEIGHT = 300; // No<br>const int maximumWeight = 300; // No<br>const int MAXIMUM = 300;       // No       |
| Variables usually declared early (not within code), and initialized where appropriate and practical.                                                                                                                                                                            | int i; <br>char userKey = '-';                                                                                            | int i;        <br>char userKey; <br><br>userKey = 'c';<br>int j;        // No                                              |
| Function names are CamelCase with uppercase first.                                                                                                                                                                                                                              | PrintHello()                                                                                                              | printHello()   // No<br>print_hello()  // No                                                                               |
| Miscellaneous                                                                                                                                                                                                                                                                   |                                                                                                                           |                                                                                                                            |
| Lines of code are typically less than 100 characters wide.                                                                                                                                                                                                                      | Code is more easily readable when lines are kept short. One long line can usually be broken up into several smaller ones. |                                                                                                                            |
