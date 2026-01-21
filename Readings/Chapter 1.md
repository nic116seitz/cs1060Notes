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