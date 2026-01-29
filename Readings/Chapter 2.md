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

**Resume Notes at 2.10**