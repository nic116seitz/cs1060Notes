# Output and input streams
## The ostream and cout streams
- #ostream short for output stream
	- class that supports output 
	- available via `#include <iostream>` and in namespace `std`
- ostream provides the `<< operator` known as #insertion operator for converting different types of data into a sequence of characters
- #cout is a predefined ostream object (declared as `ostream cout;` in the ostream library) that is pre-associated with a system's standard output, usually a computer screen
## The istream and cin streams
- #istream is short for "input stream"
	- class that supports input 
	- provides `>>` #operator known as the #extractionOperator, to extract data from a data buffer and write the data into different types of variables
	- #cin is a predefined istream pre-associated with a system's standard input, usually a computer keyboard
	- `>>` skips leading whitespace and extracts corresponding possible amount to characters in the target variable's type and stores the result into the variable
# Output formatting
## Floating-point manipulators
- A programmer can adjust the way that a program's output apperas, a task known as output formatting
- #manipulator is a function that overloads the insertion operator `<<` or extraction operator `>>` to adjust the way output appears
- 