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