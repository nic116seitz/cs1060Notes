## Unhandled exceptions
- #exception is an unexpected incident that stops normal program execution
## Catching exceptions
- try catch blocks
	- #tryBlock surrounds normal code, which is exited immediately if a statement within the try block throws an exception
	- #catchBlock catches an exception thrown in a preceding try block
	- If the thrown exception's type matches the catch block's parameter type, the code within the catch block executes. A catch block is called an #exceptionHandler
## Handling exceptions
- A program may be able to resolve some exceptions
- The previous example only printed an error message and an invalid shipping cost instead the program can handle the exception and get user input again until a valid input is provided 
## Common exception types

| Type              | Cause of exception                                                                                                                                    |
| ----------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------- |
| runtime_error     | Errors that occur and are detected at runtime. runtime_error is a base class for other exceptions.                                                    |
| system_error      | Errors originating from the underlying operating system or other low-level system components. system_error's typically have an associated error code. |
| invalid_argument  | Errors due to invalid user inputs or invalid inputs to program components (e.g., function arguments).                                                 |
| out_of_range      | Errors due to accessing elements outside of a supported range (e.g., vector indices).                                                                 |
| ios_base::failure | Errors due to failures in reading or writing input/output streams.                                                                                    |
# Throwing exceptions
## Using throw statements
- #throw statement can throw an exception, like runtime_error, which causes execution to jump immediately to the end of a try block
- `isnan()` can be used to check if something is not a number
	- This is an example of something that can be combined with the throw to impact the outcome of a try-catch
- `.what()` method is used to output what exception caused the catch to trigger
- The errors can be customized above by defining the error type and then using parentheses combined with strings to define what the output statement will be
- Ex: `throw runtime_error("User defined error message");`
## Use exceptions to separate error checking from normal code
- this is to detect errors and throw exceptions to keep error-checking code separate from normal code, reducing redundant error checks
- Ex:
This code below computes the density of an object by taking the ratio of mass and volume inputs. If either input is negative, the program throws an exception to handle the error
```
#include <iostream>
#include <cmath>
using namespace std;

int main() {
   double massVal = 0;   // Object mass (kg)
   double volumeVal = 0; // Object volume (m^3)
   double densityCalc;   // Resulting density
   
   try {
      cin >> massVal;

      // Error checking, greater than zero mass
      if (massVal <= 0.0) {
         throw runtime_error("Invalid mass");
      }

      cin >> volumeVal;

      // Error checking, greater than zero volume
      if (volumeVal <= 0.0) {
         throw runtime_error("Invalid volume");
      }

      densityCalc = massVal / volumeVal;

      cout << "Density: " << densityCalc;
   }
   catch (runtime_error& excpt) {
      // Prints the error message passed by the throw statement
      cout << excpt.what() << endl;
   }
   
   return 0;
}
```
## Multiple exception handlers
- code within a try block may throw different types of exceptions
## Handling exceptions thrown by other functions
- A function can throw an exception when called by another function
- The calling function can handle exceptions thrown by the called function
# Exceptions with files
## Handling exceptions from opening invalid files
- A program may try to open a file that doesn't exist
## Closing files
- *Good practice is to close all files to allow the OS to cleanup any resources used while reading from or writing to a file*
Below is an example of a program that considers this closing the file before exiting

```
#include <iostream>
#include <fstream>
#include <ios>
#include <string>
#include <iomanip>
using namespace std;

int main() {
   string inputFileName;
   ifstream inputFile;
   int totalReviews;
   int reviewCount = 0;
   double inputReview;
   double sumReviews = 0.0;
   double avgReview;

   cin >> inputFileName;
   inputFile.exceptions(ifstream::failbit); 

   try {
      inputFile.open(inputFileName);
      
      inputFile >> totalReviews;
      for (int i = 0; i < totalReviews; ++i) {
         inputFile >> inputReview;
         sumReviews += inputReview;
         reviewCount++;
      }
      avgReview = sumReviews / reviewCount;
      cout << fixed << setprecision(1);
      cout << "Average of reviews: " << avgReview << endl; 
   }
   catch (ios_base::failure& excpt) {
      cout << "Error reading file input: " << excpt.what() << endl;
   }
 
   // Closes the opened file.
   if (inputFile.is_open()) {
      inputFile.close();
   }

   return 0;
}
```
## Handling exceptions when writing to files
- `outputFile.exceptions(ofstream::failbit);` can be used as a way to throw errors when a file fails to write in a program
## Writing  to files after handling exceptions
- A programmer can use a catch block to do additional processing, even if an exception is thrown in the try statement
	- Ex: if an exception is thrown after a program has opened and partially read a file, code within the catch block can preserve calculations the program has made up to when the exception was thrown

Below is an example that will be helpful for reference when using file streams

```
#include <iostream>
#include <fstream>
#include <ios>
#include <string>
#include <iomanip>
using namespace std;

int main() {
   string inputFileName;
   string outputFilename;
   ifstream inputFile;
   ofstream outputFile;
   int totalReviews;
   int reviewCount = 0;
   double inputReview;
   double sumReviews = 0.0;

   cin >> inputFileName;
   cin >> outputFilename;
   inputFile.exceptions(ifstream::failbit); 
   outputFile.exceptions(ofstream::failbit);
   
   try {
      inputFile.open(inputFileName);
      outputFile.open(outputFilename, ios::app);
      
      inputFile >> totalReviews;
      for (int i = 0; i < totalReviews; ++i) {
         inputFile >> inputReview;
         sumReviews += inputReview;
         reviewCount++;
      }
      outputFile << fixed << setprecision(1);
      outputFile << (sumReviews / reviewCount) << endl;
   }
   catch (ios_base::failure& excpt) {
      if (inputFile.fail()) {
         cout << "Error reading input file: " << excpt.what() << endl;
         if (outputFile.is_open()) {
            if (outputFile.good()) {
               try {
                  cout << "Writing average review for available data." << endl;
                  outputFile << fixed << setprecision(1);
                  outputFile << (sumReviews / reviewCount) << endl;
               }
               catch (ios_base::failure& excpt) {
                  cout << "Error accessing output file: " << excpt.what() << endl;
               }
            }
         }
      }
      else if (outputFile.fail()) {
         cout << "Error accessing output file: " << excpt.what() << endl;
      }
   }

   if (inputFile.is_open()) {
      inputFile.close();
   }
   if (outputFile.is_open()) {
      outputFile.close();
   }

   return 0;
}
```
# User-defined exceptions
## The exceptions class
- catch block that catches the `exception` type can catch exceptions of any type
- A program that uses the `exception` in a catch block may not be able to differentiate between what exception types are caught
- **This could be good for initial exception mapping**
