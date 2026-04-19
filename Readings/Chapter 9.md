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

## Table 9.2.1: Floating-point manipulators.

| Manipulator                                                                                                                                           | Description                                                                                                                | Example                                                                                                   |
| ----------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------- |
| fixed                                                                                                                                                 | Use fixed-point notation.  <br>From <iostream>                                                                             | // 12.340000<br>cout << fixed << 12.34;                                                                   |
| scientific                                                                                                                                            | Use scientific notation.  <br>From <iostream>                                                                              | // 1.234000e+01<br>cout << scientific << 12.34;                                                           |
| setprecision(p)                                                                                                                                       | If stream has not been manipulated to fixed or scientific:  <br>Sets max number of digits in number                        | // 12.3<br>cout << setprecision(3) << 12.34;<br><br>// 12.34<br>cout << setprecision(5) << 12.34;         |
| If stream has been manipulated to fixed or scientific:  <br>Sets max number of digits in fraction only (after the decimal point).  <br>From <iomanip> | // 12.3<br>cout << fixed << setprecision(1) << 12.34;<br><br>// 1.2e+01<br>cout << scientific << setprecision(1) << 12.34; |                                                                                                           |
| showpoint                                                                                                                                             | Even if fraction is 0, show decimal point and trailing 0s.  <br>Opposite is noshowpoint.  <br>From <iostream>              | // 99<br>cout << setprecision(3) << 99.0;<br><br>// 99.0<br>cout << setprecision(3) << showpoint << 99.0; |

## Table 9.2.2: Text-alignment manipulators.

| Manipulator | Description                                                                                                                                                                                                          | Example                                                                                                   |
| ----------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------- |
| setw(n)     | Sets the number of characters for the next output item only  <br>(does not persist, in contrast to other manipulators).  <br>By default, the item will be right-aligned, and filled with spaces.  <br>From <iomanip> | // "    Amy"<br>// " George"<br>cout << setw(7) << "Amy" << endl;<br>cout << setw(7) << "George" << endl; |
| setfill(c)  | Sets the fill to character c.  <br>From <iomanip>                                                                                                                                                                    | // "****Amy"<br>cout << setfill('*') << setw(7) << "Amy";                                                 |
| left        | Changes to left alignment.  <br>From <iostream>                                                                                                                                                                      | // "Amy    "<br>cout << left << setw(7) << "Amy";                                                         |
| right       | Changes back to right alignment.  <br>From <iostream>                                                                                                                                                                | // "    Amy"<br>cout << right << setw(7) << "Amy";                                                        |
## Buffer manipulators

## Table 9.2.3: Buffer manipulators
| Manipulator | Description                                                                                                                   | Example                                       |
| ----------- | ----------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------- |
| endl        | Inserts a newline character '\n' into the output buffer  <br>and informs the system to flush the buffer.  <br>From <iostream> | // Insert newline and flush <br>cout << endl; |
| flush       | Informs the system to flush the buffer.  <br>From <iostream>                                                                  | // Flush buffer<br>cout << flush;             |
- Flush can be used to immediately show output text to the buffer
# Input string stream
#inputStringStream variable type of #istringstream can be created that reads input from an associated string instead of the keyboard
- syntax for declaration: `istringstream name(inputString);`
## Using getline() w/ string streams
- common use of string streams is to process user input line-by-line
- #getlinela `getline()` reads an input line into a string, and `inSS.str(lineString);` uses the `str()` function to initialize the stream's buffer to string lineString
- Afterwards, the program extracts input from inSS using `>>` The statement `inSS.clear();` is necessary to reset the state of the stream so that subsequent extractions start from the beginning of the input strings
## Reaching the end of a string tream
- A programmer will not always know how much data exist in input string
- Input streams have a Boolean function called #eof `eof()` or #endOfFile that returns true or false depending on whether or not the end of the stream has been reached. 
- An if statement or while loop can check if the end of input string stream has been reached by using the extraction operator
```
while (inSS >> data) {
	...
}
```
- The above example implicitly calls inSS's eof() function, which returns false if more data exists in the string stream to be read and true if the end of string stream has been reached
- When taking input for multiple variables the following syntax can be used to better process and break it up
```
int main() {
string userInput;
istringstream date;
string month;
int day;
int year;

getline(cin, userInput); //Getline to assign the full line to userInput
date.str(userInput); //String function on the istringstream

date >> month >> day >> year; //Breaks up and assigns the various parts of the date with the appropriate variable. 
}
```
# Output string stream
- An #ouputStringStream variable of type #ostringstream can insert characters into a string buffer instead of the screen
- appending:
	- `outputString << appendedThing;`
- copying to variable:
	- `myVar = outputString.str()`
# File input
- To take file as input you must have `#include <fstream>` in your includes
- next in variable declaration you must have `ifstream fileStream`
- `fileStream.open("filename.ext")` function has a string parameter str that specifies the name of the file to open
	- `.ext` will be the extension of the file being accessed
- for this process an if statement creating an error is useful to indicate the error which would look something like:
```
if (!fileStream.is_open()) {
	cout << "Could not open file filename.ext" << endl;
	return 1; // 1 indicates error
}
```
- from there you can assign parts of the file to variables
	- `fileStream >> var1`
- when done using the stream close it using the close method
	- `fileStream.close();`
- filename param can be C++ string or null-terminated Cstring
- program can also use a user-entered string as the filename, such as using `cin >> filename;`
- to check for errors in reading a file you can use the #failFunction `fail()`
```
while (!inFS.fail()) {
      cout << "num: " << fileNum << endl;
      inFS >> fileNum;
   }
```
## Input stream errors
- #streamError occurs when insertion of extraction fails
- causes stream to enter error state
	- This causes bugs in further stream extraction


## Table 9.5.1: Stream error state flags and functions to check error state.

| Flag    | Meaning                                                                                                                             | Function                                                                                                       |
| ------- | ----------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------- |
| goodbit | Indicates no error flags are set and the stream is good.                                                                            | good() returns true if no stream errors have occurred.                                                         |
| eofbit  | Indicates if end-of-file reached on extraction.                                                                                     | eof() returns value of eofbit, if end-of-file reached on extraction.                                           |
| failbit | Indicates a logical error for the previous extraction or insertion operation.                                                       | fail() returns true if either failbit or badbit is set, indicating an error for the previous stream operation. |
| badbit  | Indicates an error occurred while reading or writing the stream, and the stream is bad. Further operations on the stream will fail. | bad() returns true if badbit is set, indicating the stream is bad.                                             |
# File output
- #ofstream is a class that supports writing to a file
1. declare var of `ofstream`
2. file is opened using `open()` function
3. `is_open()` called to check open state
4. data is written using `<<`
5. after desired data is written `close()`
## 

Table 9.7.1: Basic steps for opening and writing a file.

| Action                                        | Sample code                                                                                            |
| --------------------------------------------- | ------------------------------------------------------------------------------------------------------ |
| Open the file helloWorld.txt for writing      | `<br>ofstream outFS;<br>outFS.open("helloWorld.txt");<br>`<br>                                         |
| Check to see if the file opened successfully  | ```<br>if (!outFS.is_open()) {<br>// Do not proceed to code that writes to the file<br>}<br>```<br>``` |
| Write the string "Hello World!" to the file   | `outFS << "Hello World!" << endl;`                                                                     |
| Close the file after writing all desired data | outFS.close();                                                                                         |
# Overloading stream operators
## Overloading the `<<` operator
- << is known as the #insertionOperator
- A C++ class can overload this by creating a member function called `operator<<`
## Overloading the `>>` operator
- can be overloaded similarly to insertion operator 
## Extending cin and cout
- by default a programmer-defined C++ class does not work with cin and cout