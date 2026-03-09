- A typical variable stores one data item, like the number 59 or the character `'a'`. Instead, sometimes a list of data items should be stored. 
	- Ex: A program recording points scored in each quarter of a basketball game needs a list of 4 numbers
- Requiring a programmer to declare 4 variables is annoying; 200 variables would be ridiculous
- #array is a special variable having one name, but storing a list of data items, with each item being directly accessible
- Some languages use a construct similar to an array called a #vector
- Each item in an array is known as an #element
- normal var is like a truck and a array is like a train
	- truck has one car for carrying "data" but a train has many cars, each of which can carry data
- In an array, each elements location numbers is called the #index, `myArray[2]` has an index 2
- An array's key feature is that the index enables direct access to any element as in `myArray[2]`; different languages may use different syntax, like `myArray(3)` or `myVector.at(3)` 
# Vectors
## Vector declaration and element access
- A programmer commonly needs to maintain a list of items, just as people often maintain lists of items
- #vector is an ordered list of items given of a given data type
- Each item in a vector is called an #element 
- A programmer must include the statement `#include <vector>` at the top of the file to use vectors

#### Construct 5.2.1: Declaring an empty vector.
```
vector<dataType> vectorName;
```

- The statement above declares an empty vector capable of storing an unspecified number of elements
- they type of each vector element is specified within the angle brackets (`<>`)
- #pushBack `push_back()` appends a new element to the end of an existing vector `.at()` accesses a vector element at the index specified within the parentheses
## Vector intialization 
- A vector can be declared with an initial number of elements by specifying the number of elements within parentheses following the vector name
	- Ex: `vector<int> gameScores(4);` declares a vector gameScores with 4 integer elements
- A vector can also be initialized by specifying the initial values in braces {} separated by commas. 
	- Ex: `vector<int> carSales = {5, 7, 11};` creates a vector of three integer elements initialized with values 5, 7, and 11
- Such vector declarations and initialization does not require specifying the vector size, because the vector size is automatically set to the number of elements within the braces
## *Common Error: Forgetting to include &It;vector&gt;*
- A common error is to forget the `#include<vector>` at the top of the file when using vectors
- Trying to then declare a vector variable may yield a strange compiler error:
- The same error message may be seen if the vector library is included but the namespace std is not used
## Using an expression for a vector index
- A powerful aspect of vectors is that the index is an expression
	- Ex: userNums.at(i) uses the value held in the int variable i as the index.
- As such, a vector is useful to easily lookup the Nth item in a list
- A vector's index must be an unsigned integer type
- A vectors The vector index cannot be a floating-point type even if the value is 0.0, 1.0, etc
- The program below allows a user to print the age of the Nth oldest known person to have ever lived
- The program quickly accesses the Nth oldest person's age using `oldestPeople.at(nthPErson -1)` Not that the index is `nthPerson -1` rather than just `nthPerson` because a vector's indices start at 0 so the 1st age is at index 0 the 2nd at index 1, etc.
## Loops and vectors
- A key advantage of vectors becomes evident when used in conjunction with loops
- The program below uses a loop to allow a user to enter 8 integer values, storing those values in a vector, and then printing those 8 values
	- A vector's #size function `size()` returns the number of vector elements 
# Iterating through vectors
## Iterating through vectors using loops
- Iterating through vectors using loops is commonplace and is an important programming skill to master
- vector indices are numbered 0 to N -1 rather than 1 to N
- programmers commonly use this for loop structure
## Determining a quantity about a vector's items
- Iterating through a vector for various purposes is an important programming skill to master
- programs commonly iterate through vectors to determine some quantity about the vector's items
## *Common error: Accessing out of range vector element*
- A common error is to try to access a vector with an index that is out of the vector's index range
	- Ex: Trying to access highScores.at(8) when highScores valid indices are 0-7
	- care should be taken whenever a user enters a number that is then used as a vector index
		- Also when using a loop index as a vector index to ensure the array index is within a vector's valid index range
	- Accessing an index that is out of range
	- It is important when working with negative values to consider that if the values you are working with are negative setting the max to 0 could be bad because you are impacting the possible output of the final result
	- To print a vector in reverse order 
	```
	for (i = vectorName.size() - 1; i >= 0; --i) {
		cout << userVals.at(i) << endl;
	}
	```

# Multiple vectors
- Programmers commonly use multiple same-sized vectors to store related lists
# Vector resize
- Commonly, the size of a list of items is not known during a program's compile time. Thus, a vector's size need not be specified in the vector's declaration. 
- A vectors side can be set or changed while a program executes using #resize `resize(N)`
	- EX: `highScore.resize(10)` resizes the highScores vector to have 10 elements
- `resize()` can be called multiple times. 
- if userScores has size 3 (elements 0, 1,2) `userScores.resize(2);` would delete element 2, leaving elements 0 and 1
- A subsequent access to userScores.at(2) would result in an error
# Vector back() and pop_back()
- The following table summarizes a few common functions for dealing with the back (or last element) of a vector


Table 5.7.1: Functions for back of vector.

|            |                                                                                   |                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| ---------- | --------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| back()     | `int back();`  <br>  <br>Returns vector's last element. Vector is  <br>unchanged. | // playersList initially 55, 99, 44<br>cout << playersList.back(); // Prints 44 <br>// playersList is still 55, 99, 44                                                                                                                                                                                                                                                                                                          |
| pop_back() | `void pop_back();`  <br>  <br>Removes the last element.                           | // playersList is 55, 99, 44 (size 3)<br>playersList.pop_back(); // Removes last element<br>// playersList now 55, 99 (size 2)<br><br>cout << playersList.back(); // Common combination of back() <br>playersList.pop_back();     // followed by pop_back()<br>// Prints 99. playersList becomes just 55<br><br>cout << playersList.pop_back(); // Common error: <br>                                // pop_back() returns void |
# Using a loop to modify, copy or compare vectors
## Modifying vector elements
- A program may need to modify elements while iterating through a vector. 
## Element by element vector copy
- In C++ the `=` operator conveniently performs an element-by-element copy of a vector, called #vectorCopyOperation 
- The operation `vectorB = vectorA` resizes vectorB to vectorA's size, appending or deleting elements as needed. vectorB commonly has a size of 0 before the operation
## Element by element vector comparison
- In C++ the `==` operator conveniently compares vectors element-by-element called a #vectorEqualityOperation, with `vectorA == vectorB` evaluating to true if the vectors are the same size **AND** each element pair is equal
# Swapping two variables (general)
- Sometimes a program must swap values among two variables. #Swapping two variables x and y means to assign y's value to x, and x's value to y. 
- If x is 33 and y is 55 then after swapping x is 55 and y is 33
- A common method for swapping uses a temp variable 
- #temporaryVariable is a variable used briefly to store a value
- to understand the intuition of such a temporary storage, consider a person holding a book in one hand and a phone in the other, wishing to swap the items. The person can temporarily place the phone on a table 
- swaps are actually performed between two list elements
- Reversing a list with n elements can be achieved by swapping element 1 and N, element 2 and N-1, etc (stopping at the middle of the list)
# Debugging
- A common vector mod is to revers a vector's elements. One way to accomplish this goal is to perform a series of swaps
	- Ex: starting with a vector of numbers 10 20 30 40 50 60 70 80 we could first swap the first item with the last item yielding 80 20 30 40 50 60 70 10
# Arrays vs. vectors
- C++ supports two types of ordered lists
	- Arrays: declared as `int myList[10]` accessed as `myList[i]`
	- Vectors: declared `vector<int> myList(10)` accessed as `myList.at(i)`
- Arrays have a simpler syntax than vectors but vectors are safer to use. Thus using vectors rather than arrays is good practice
- Vectors are safer because the access v.at(i) is checked during execution to ensure the index is within the vector's valid range
- An array access involve no check
- *Such checking is important; trying to access an array with an out out-of-range index is a very common error and one of the hardest errors to debug*
- Assigning a out of range index can mysteriously change some other variable's value 
	- Debugging this can suck
- Vectors have more advantages, like resizing during runtime, easy insertion of items at the front or rear, determining vector size, etc. 
- Arrays have minor benefits that don't really outweigh drawbacks 
- arrays have no `.size()` feature
# Two-dimensional arrays
- An array can be declared with two dimensions `int myArray[R][C]` represents a table of int variables with R rows and C columns, so R\*C elements total.
- Conceptually 2D array is a table with rows and columns. 
- Compiler maps 2D array elements to one-dimensional memory, each row following the previous row, known as #row-majorOrder 
- A programmer can initialize a 2D array's elements during declaration using nested braces
- Ex:
```
int arrayName[2][3] = {{12, 30, 44}, {77, 22, 1}};
```
- Arrays of 3 or more dimensions can also be declared, as in `int myArray[2][3][5]`
	- the above example would declare a total of 2 \* 3 \* 5 for a total of 30 elements
	- *Note: the rapid growth in size*
- Be careful to not unnecessarily occupy available memory with a large array
# Char arrays / C strings
- A programmer can use an array to store a sequence of chars, known as a #string 
- Char arrays were the only kinds of strings in C
	- and thus called #Cstrings 
- Because a string can be shorter than the character array, a string in a char array must end with a special character known as a #nullCharacter written as `\0` Given a string literal like `"Star Wars"` the compiler automatically appends a null character
- A char array of size 20 can store strings of length 0 - 19
	- longest string is 19 not 20 because the null character must be stored
- if a char array is initialized when declared then char array's size may be omitted 
	- Ex: `char userName[ ] = "Hellen";` 
	- compiler determines the size from the string literal
- An array of chars ending with a null character in known as a #null-terminatedString 
- Outputs automatically handle null-terminated strings
- you cannot assign the string as in `movieTitle = "Indiana Jones";`
- *Common error is to loop the string's array size rather than stopping at null char*
- *Another error is for the program user to enter a string larger than the array*
- Not including a nullchar will also cause problems
# C-String library functions
- C++ provides functions for working with C strings, presented in #cstring library
- To use those functions the programmer starts with: `#include <cstring>`
## 

Table 5.14.1: Some C string modification functions.

Given:  

char orgName[100] = "United Nations"; 
char userText[20] = "UNICEF"; 
char targetText[10];

|           |                                                                                                                                                                                                                                                                                                                                                                                            |                                                                                                                                                                                                                                             |
| --------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| strcpy()  | `strcpy(destStr, sourceStr)`  <br>  <br>Copies sourceStr (up to and including the null character) to destStr. destStr must have enough space for sourceStr, including the null character.                                                                                                                                                                                                  | strcpy(targetText, userText);<br>   // Copies "UNICEF" + null char to targetText <br>strcpy(targetText, orgName);<br>   // Error: "United Nations" has > 10 chars<br>targetText = orgName;<br>   // Error: Strings can't be copied this way |
| strncpy() | `strncpy(destStr, sourceStr, numChars)`  <br>  <br>Copies up to numChars characters from sourceStr. destStr must have enough space for the copied characters, including the null character. If sourceStr has less than numChars characters, strncpy will fill the remaining space with the null character.                                                                                 | strncpy(orgName, userText, 6);<br>   // orgName is "UNICEF Nations"                                                                                                                                                                         |
| strcat()  | `strcat(destStr, sourceStr)`  <br>  <br>Copies sourceStr to _end_ of destStr (starting at destStr's null character) and then appends a null character. destStr must have enough space for the addition of sourceStr plus the null character.                                                                                                                                               | strcat(orgName, userText);<br>   // orgName is "United NationsUNICEF"                                                                                                                                                                       |
| strncat() | `strncat(destStr, sourceStr, numChars)`  <br>  <br>Copies up to numChars characters from sourceStr to _end_ of destStr (starting at destStr's null character) and then appends a null character. destStr must have enough space for the addition of sourceStr plus the null character. Copying of sourceStr characters continues until either the end of sourceStr or numChars is reached. | strcpy(targetText, "abc");<br>   // targetText is "abc"<br>strncat(targetText, "123456789", 3);<br>   // targetText is "abc123"                                                                                                             |
- For `strcpy()` a *common error is to copy the source string that is too large, causing an out-of-range access in the destination string*
-  another is to call strcpy with the source string first rather than the destination string, which copies in the wrong direction
- string assignment  does not copy the string and should not be used unless during initialization
## 

Table 5.14.2: Some C string information functions.

Given:  

char orgName[100] = "United Nations"; 
char userText[20] = "UNICEF"; 
char targetText[10];

|          |                                                                                                                                                                                                                   |                                                                                                                                                                                                                                                                        |
| -------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| strchr() | `strchr(sourceStr, searchChar)`  <br>  <br>Returns NULL if searchChar does not exist in sourceStr. (Else, returns address of first occurrence, discussed elsewhere).  <br>NULL is defined in the cstring library. | if (strchr(orgName, 'U') != NULL) { // 'U' exists in orgName?<br>   ...  // 'U' exists in "United Nations", branch taken<br>}  <br>if (strchr(orgName, 'u') != NULL) { // 'u' exists in orgName?<br>   ...  // 'u' doesn't exist (case matters), branch not taken<br>} |
| strlen() | `size_t strlen(sourceStr)`  <br>  <br>Returns number of characters in sourceStr up to, but not including, first null character. size_t is integer type.                                                           | x = strlen(orgName);    // Assigns 14 to x <br>x = strlen(userText);   // Assigns 6 to x<br>x = strlen(targetText); // Error: targetText may lack null char                                                                                                            |
| strcmp() | `int strcmp(str1, str2)`  <br>  <br>Returns 0 if str1 and str2 are equal, non-zero if they differ.                                                                                                                | if (strcmp(orgName, "United Nations") == 0) {<br>   ... // Equal, branch taken<br>}<br>if (strcmp(orgName, userText) != 0) {<br>   ... // Not equal, branch taken<br>}                                                                                                 |
- `strcmp()` is usually used to compare for inequality returning 0 if the string are the same length and have identical characters.
- *Common error is to use == when comparing C strings* 
- *Another is to forget the compare results of strcmp with 0*  you can use if 
- `if (strcmp(str1, str2) == 0) {...}`
# Char library functions cctype 
## 

Table 5.15.1: Functions that check whether a character is of a given category.

The examples below assume the following string declaration.  

char myString[30] = "Hey9! Go";

|                                                                                                                                         |                                                                                                                                                                                                                                                                                                                            |
| --------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| isalpha(c) -- Returns true if c is alphabetic: a-z or A-Z.                                                                              | isalpha('A');            // Returns true<br>isalpha(myString[0]);    // Returns true because 'H' is alphabetic<br>isalpha(myString[3]);    // Returns false because '9' is not alphabetic                                                                                                                                  |
| isdigit(c) -- Returns true if c is a numeric digit: 0-9.                                                                                | isdigit(myString[3]);    // Returns true because '9' is numeric<br>isdigit(myString[4]);    // Returns false because ! is not numeric                                                                                                                                                                                      |
| isalnum(c) -- Returns true if c is alphabetic or a numeric digit. Thus, returns true if either isalpha or isdigit would return true.    | isalnum('A');            // Returns true<br>isalnum(myString[3]);    // Returns true because '9' is numeric                                                                                                                                                                                                                |
| isspace(c) -- Returns true if character c is a whitespace.                                                                              | isspace(myString[5]);    // Returns true because that character is a space ' '.<br>isspace(myString[0]);    // Returns false because 'H' is not whitespace.                                                                                                                                                                |
| islower(c) -- Returns true if character c is a lowercase letter a-z.                                                                    | islower(myString[0]);    // Returns false because 'H' is not lowercase. <br>islower(myString[1]);    // Returns true because 'e' is lowercase.<br>islower(myString[3]);    // Returns false because '9' is not a lowercase letter.                                                                                         |
| isupper(c) -- Returns true if character c is an uppercase letter A-Z.                                                                   | isupper(myString[0]);    // Returns true because 'H' is uppercase. <br>isupper(myString[1]);    // Returns false because 'e' is not uppercase.<br>isupper(myString[3]);    // Returns false because '9' is not an uppercase letter.                                                                                        |
| isblank(c) -- Returns true if character c is a blank character. Blank characters include spaces and tabs.                               | isblank(myString[5]);    // Returns true because that character is a space ' '. <br>isblank(myString[0]);    // Returns false because 'H' is not blank.                                                                                                                                                                    |
| isxdigit(c) -- Returns true if c is a hexadecimal digit: 0-9, a-f, A-F.                                                                 | isxdigit(myString[3]);  // Returns true because '9' is a hexadecimal digit.<br>isxdigit(myString[1]);  // Returns true because 'e' is a hexadecimal digit.<br>isxdigit(myString[6]);  // Returns false because 'G' is not a hexadecimal digit.                                                                             |
| ispunct(c) -- Returns true if c is a punctuation character. Punctuation characters include: !"#$%&'()*+,-./:;<=>?@[\]^_`{\|}~           | ispunct(myString[4]);  // Returns true because '!' is a punctuation character. <br>ispunct(myString[6]); // Returns false because 'G' is not a punctuation character.                                                                                                                                                      |
| isprint(c) -- Returns true if c is a printable character. Printable characters include alphanumeric, punctuation, and space characters. | isprint(myString[0]);    // Returns true because 'H' is a alphabetic. <br>isprint(myString[4]);    // Returns true because '!' is punctuation.<br>isprint(myString[5]);    // Returns true because that character is a space ' '.<br>isprint('\0');           // Returns false because the null character is not printable |
| iscntrl(c) -- Returns true if c is a control character. Control characters are all characters that are not printable.                   | iscntrl(myString[0]);    // Returns false because 'H' is a not a control character <br>iscntrl(myString[5]);    // Returns false because space is a not a control character<br>iscntrl('\0');           // Returns true because the null character is a control character                                                  |
## 

Table 5.15.2: Functions that convert a character to upper or lower case.

The examples below assume the following string declaration.  

char myString[30] = "Hey9! Go";

|                                                                                                                                                                    |                                                                                                                                                                                                                                                                    |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| toupper(c) -- If c is a lowercase alphabetic character (a-z), returns the uppercase version (A-Z). If c is not a lowercase alphabetic character, just returns c.   | letter = toupper(myString[0]);  // Returns 'H' (no change) <br>letter = toupper(myString[1]);  // Returns 'E' ('e' converted to 'E') <br>letter = toupper(myString[3]);  // Returns '9' (no change) <br>letter = toupper(myString[5]);  // Returns ' ' (no change) |
| tolower(c) -- If c is an uppercase alphabetic character (A-Z), returns the lowercase version (a-z). If c is not an uppercase alphabetic character, just returns c. | letter = tolower(myString[0]);  // Returns 'h' ('H' converted to 'h')<br>letter = tolower(myString[1]);  // Returns 'e' (no change)<br>letter = tolower(myString[3]);  // Returns '9' (no change) <br>letter = tolower(myString[5]);  // Returns ' ' (no change)   |


