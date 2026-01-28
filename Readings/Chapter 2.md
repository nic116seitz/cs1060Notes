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

|                                                                                                                                                                                                                                                                                                                                   |                                                                                                                                                                                                                                                            |                                                                                                                                                                                                                                                                                                                                |                                                                                                                                                                                                                                                                         |
| --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| alignas   (since C++11)  <br>alignof   (since C++11)  <br>and  <br>and_eq  <br>asm  <br>auto  <br>bitand  <br>bitor  <br>bool  <br>break  <br>case  <br>catch  <br>char  <br>char16_t   (since C++11)  <br>char32_t   (since C++11)  <br>class  <br>compl  <br>const  <br>constexpr   (since C++11)  <br>const_cast  <br>continue | decltype   (since C++11)  <br>default  <br>delete  <br>do  <br>double  <br>dynamic_cast  <br>else  <br>enum  <br>explicit  <br>export  <br>extern  <br>false  <br>float  <br>for  <br>friend  <br>goto  <br>if  <br>inline  <br>int  <br>long  <br>mutable | namespace  <br>new  <br>noexcept   (since C++11)  <br>not  <br>not_eq  <br>nullptr   (since C++11)  <br>operator  <br>or  <br>or_eq  <br>private  <br>protected  <br>public  <br>register  <br>reinterpret_cast  <br>return  <br>short  <br>signed  <br>sizeof  <br>static  <br>static_assert   (since C++11)  <br>static_cast | struct  <br>switch  <br>template  <br>this  <br>thread_local   (since C++11)  <br>throw  <br>true  <br>try  <br>typedef  <br>typeid  <br>typename  <br>union  <br>unsigned  <br>using  <br>virtual  <br>void  <br>volatile  <br>wchar_t  <br>while  <br>xor  <br>xor_eq |