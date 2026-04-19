- #algorithm is a sequence of steps for solving a problem
- #recursiveAlgorithm breaks the problem into smaller subproblems and applies the same algorithm to solve the smaller subproblems
- recursive algorithm must describe how to actually do something, known as #baseCase 
# Recursive functions
- Function may call other functions including itself
- If the function calls itself it is a #recursiveFunction 
# Recursive algorithm: Search
## general
#binarySearch 
- begins at midpoint and halves the range after each guess
- The guesses will look as follows:
	1. 50 (middle of 0-100) Lower
	2. 25 (middle of 0-50) Higher
	3. 38 (middle of 26-50) Lower
	4. 32 (middle of 26-38)
- After each guess, the binary search algorithm is applied again, but on a smaller range
## Recursive search function

```
#include <iostream>
using namespace std;

void GuessNumber(int lowVal, int highVal) {
   int midVal;            // Midpoint of low and high value
   char userAnswer;       // User response
   
   midVal = (highVal + lowVal) / 2;
   
   // Prompt user for input
   cout << "Is it " << midVal << "? (l/h/y): ";
   cin >> userAnswer;
   
   if( (userAnswer != 'l') && (userAnswer != 'h') ) { // Base case: found number
      cout << "Thank you!" << endl;                   
   }
   else {                                             // Recursive case: split into lower OR upper half
      if (userAnswer == 'l') {                        // Guess in lower half
         GuessNumber(lowVal, midVal);                 // Recursive call
      }
      else {                                          // Guess in upper half
         GuessNumber(midVal + 1, highVal);            // Recursive call
      }
   }
}

int main() {
   // Print game objective, user input commands
   cout << "Choose a number from 0 to 100." << endl;
   cout << "Answer with:" << endl;
   cout << "   l (your num is lower)" << endl;
   cout << "   h (your num is higher)" << endl;
   cout << "   any other key (guess is right)." << endl;
   
   // Call recursive function to guess number
   GuessNumber(0, 100);
   
   return 0;
}

Choose a number from 0 to 100.
Answer with:
   l (your num is lower)
   h (your num is higher)
   any other key (guess is right).
Is it 50? (l/h/y): l
Is it 25? (l/h/y): h
Is it 38? (l/h/y): l
Is it 32? (l/h/y): y
Thank you!
```
## Recursively searching a sorted list
- Search is commonly performed to a quickly find an item in a sorted list stored in an array or vector
```
#include <iostream>
#include <string>
#include <vector>

using namespace std;

/* Finds index of string in vector of strings, else -1.
   Searches only with index range low to high
   Note: Upper/lower case characters matter
*/

int FindMatch(vector<string> stringsList, string itemMatch, int lowVal, int highVal) {
   int midVal;        // Midpoint of low and high values
   int itemPos;       // Position where item found, -1 if not found
   int rangeSize;     // Remaining range of values to search for match
   
   rangeSize = (highVal - lowVal) + 1;
   midVal = (highVal + lowVal) / 2;
   
   if (itemMatch == stringsList.at(midVal)) {   // Base case 1: item found at midVal position
      itemPos = midVal;
   }
   else if (rangeSize == 1) {                   // Base case 2: match not found
      itemPos = -1;
   }
   else {                                       // Recursive case: search lower or upper half
      if (itemMatch < stringsList.at(midVal)) { // Search lower half, recursive call
         itemPos = FindMatch(stringsList, itemMatch, lowVal, midVal);
      }
      else {                                    // Search upper half, recursive call
         itemPos = FindMatch(stringsList, itemMatch, midVal + 1, highVal);
      }
   }
   
   return itemPos;
}

int main() {
   vector<string> attendeesList(0); // List of attendees
   string attendeeName;             // Name of attendee to match
   int matchPos;                    // Matched position in attendee list
   
   // Omitting part of program that adds attendees
   // Instead, we insert some sample attendees in sorted order
   attendeesList.push_back("Adams, Mary");
   attendeesList.push_back("Carver, Michael");
   attendeesList.push_back("Domer, Hugo");
   attendeesList.push_back("Fredericks, Carlos");
   attendeesList.push_back("Li, Jie");
   
   // Prompt user to enter a name to find
   cout << "Enter person's name: Last, First: ";
   getline(cin, attendeeName); // Use getline to allow space in name
   
   // Call function to match name, output results
   matchPos = FindMatch(attendeesList, attendeeName, 0, attendeesList.size() - 1);
   if (matchPos >= 0) {
      cout << "Found at position " << matchPos << "." << endl;
   }
   else {
      cout << "Not found. " << endl;
   }
   
   return 0;
}
```
# Adding output statements for debugging 
- A big one for this that is used is creating a variable that holds indent amount to represent each level of recursion
	- When another level of recursion is pushed then the indent variable gets incremented with `indentVar + " "` in its recursive call
	- Ex: `RecursiveFunction(lowVar, middleVar, indentVar + " ");`
# Creating a recursive function
#### Write the base case 
- Every recursive function must have a case that returns a value without performing a recursive call
	- That case is called the #baseCase 
	- This can be written first and then tested 
#### Write the recursive case
- The programmer then adds the recursive case to the function

- *common error is to not cover all possible base cases in a recursive function*
- *Another is to write a recursive function that doesn't always reach a base case. Both errors may lead to infinite recursion, causing the program to fail*
# Recursive math functions
## Fibonacci sequence
- Recursive functions can solve certain math problems, such as computing the Fibonacci sequence
- #FibonacciSequence is 0, 1, 1, 2, 3, 5, 8, 13, 21, 34, etc
- starting with 0, 1, the pattern is to compute the next number by adding the previous two numbers
##### Fibonacci sequence step by step
```
#include <iostream>
using namespace std;

/* Output the Fibonacci sequence step-by-step.
   Fibonacci sequence starts as:
   0 1 1 2 3 5 8 13 21 ... in which the first
   two numbers are 0 and 1 and each additional
   number is the sum of the previous two numbers
*/

void ComputeFibonacci(int fibNum1, int fibNum2, int runCnt) {
   
   cout << fibNum1 << " + " << fibNum2 << " = "
        << fibNum1 + fibNum2 << endl;
   
   if (runCnt <= 1) { // Base case: Ran for user specified
                      // number of steps, do nothing
   }
   else {            // Recursive case: compute next value
      ComputeFibonacci(fibNum2, fibNum1 + fibNum2, runCnt - 1);
   }
}

int main() {
   int runFor;      // User specified number of values computed
   
   // Output program description
   cout << "This program outputs the" << endl
   << "Fibonacci sequence step-by-step," << endl
   << "starting after the first 0 and 1." << endl << endl;
   
   // Prompt user for number of values to compute
   cout << "How many steps would you like? ";
   cin >> runFor;
   
   // Output first two Fibonacci values, call recursive function
   cout << "0" << endl << "1" << endl;
   ComputeFibonacci(0, 1, runFor);
   
   return 0;
}
```
## Greatest common divisor(GCD)
- is the largest number that devices evenly into two numbers
- GCD(12,8) = 4

###### GCD using recursion
```
#include <iostream>
using namespace std;

/* Determine the greatest common divisor
   of two numbers, e.g. GCD(8, 12) = 4
*/
int GCDCalculator(int inNum1, int inNum2) {
   int gcdVal;     // Holds GCD results
   
   if(inNum1 == inNum2) {    // Base case: Numbers are equal
      gcdVal = inNum1;       // Return value
   }
   else {                    // Recursive case: subtract smaller from larger
      if (inNum1 > inNum2) { // Call function with new values
         gcdVal = GCDCalculator(inNum1 - inNum2, inNum2);
      }
      else {
         gcdVal= GCDCalculator(inNum1, inNum2 - inNum1);
      }
   }
   
   return gcdVal;
}

int main() {
   int gcdInput1;     // First input to GCD calc
   int gcdInput2;     // Second input to GCD calc
   int gcdOutput;     // Result of GCD
   
   // Print program function
   cout << "Program outputs the greatest \n"
        << "common divisor of two numbers." << endl;
   
   // Prompt user for input
   cout << "Enter first number: ";
   cin >> gcdInput1;
   
   cout << "Enter second number: ";
   cin >> gcdInput2;
   
   // Check user values are > 1, call recursive GCD function
   if ((gcdInput1 < 1) || (gcdInput2 < 1)) {
      cout << "Note: Neither value can be below 1." << endl;
   }
   else {
      gcdOutput = GCDCalculator(gcdInput1, gcdInput2);
      cout << "Greatest common divisor = " << gcdOutput << endl;
   }
   
   return 0;
}
```

# Recursive exploration of all possibilities
- Good for exploring all possibilities, such as all possible reorderings of a word's letters, all possible subsets of items, all possible paths between cities, etc.
## Word scramble 
```
#include <iostream>
#include <string>
using namespace std;

/* Output every possible permutation of a word.
   Each recursive call moves a letter from
   remainLetters to scramLetters.
*/
void ScrambleLetters(string remainLetters,  // Remaining letters
                     string scramLetters) { // Scrambled letters
   string tmpString; // Temp word permutation
   unsigned int i;   // Loop index
   
   if (remainLetters.size() == 0) { // Base case: All letters used
      cout << scramLetters << endl;
   }
   else {                             // Recursive case: move a letter from
                                      // remaining to scrambled letters
      for (i = 0; i < remainLetters.size(); ++i) {
         // Move letter to scrambled letters
         tmpString = remainLetters.substr(i, 1);
         remainLetters.erase(i, 1);
         scramLetters = scramLetters + tmpString;
         
         ScrambleLetters(remainLetters, scramLetters);
         
         // Put letter back in remaining letters
         remainLetters.insert(i, tmpString);
         scramLetters.erase(scramLetters.size() - 1, 1);
      }
   }
}

int main() {
   string wordScramble; // User defined word to scramble
   
   // Prompt user for input
   cout << "Enter a word to be scrambled: ";
   cin >> wordScramble;
   
   // Call recursive function
   ScrambleLetters(wordScramble, "");
   
   return 0;
}
```
## shopping spree