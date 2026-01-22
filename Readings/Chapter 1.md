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