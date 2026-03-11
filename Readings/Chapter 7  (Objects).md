# Objects: Introduction
## Grouping things into objects
- Program is made up of items like variables and functions to keep programs understandable
- higher- level groupings of those items are known as objects
- In programming an #object is a grouping of data (variables) and operations that can be performed on that data(functions
## Abstraction / Information hiding
- #abstraction means to have a user interact with an item at a high-level, with lower-level internal details hidden from the user (aka #informationHiding or #encapsulation) 
	- Ex; An oven supports an abstraction of a food compartment and a knob to control heat
	- An oven's user need not interact with the internal parts of an oven
- Objects strongly support abstraction, hiding entire groups of functions and variables, exposing certain functions to a user
- an #abstractDataType (ADT) is a data type whose creation and update are constrained to a specific well-defined operations
- A class can be used to implement an ADT
# Using a class
## Classes intro: Public member functions
- #class construct defines a new type that can group data and functions to form an object
- A class' #publicMemberFunctions indicate all the operations a class user can perform on the object
- The power of classes is that a class user need not know how the class' data and functions are implemented, bud need only understand how each public member function behaves
- A key feature of classes is that a class user need not know how the class is internally implemented
## Using a class
- A programmer can create one or more objects of the same class
- Declaring a variable of a class type creates an #object of that type
	- EX: `Restaurant favLunchPlace;` declares a Restaurant object named favLunchPlace
- The `.` operator known as #memberAccessOperator is used to invoke a function on an object
## string
- String class stores a string's characters in memory along with variables indicating the length and other things, but a string's user need not know such details
- string's user just needs to know what public member functions can be used
# Defining a class
## Private data members
- a class definition has #privateDataMembers
	- variables that member functions can access but class users cannot
- Private members appear after the word `private:` in a class definition
## Defining a class' public member functions
- A programmer defining a class first declares member functions after the `public:` 
- A #functionDeclaration provides the function's name, return type and parameter types, but not the function's statements
- The programmer must also define each member function
- #functionDefinition provides a class name, return type, parameters names and types and the function's statements
- A member function definition has the class name and two colons(::) known as the #scopeResolutionOperator preceding the function's name
- A member function definition can access private data members
## 

Figure 7.3.2: Simple class example: RunnerInfo.
```

#include <iostream>
using namespace std;

class RunnerInfo {
   public:                                
      void SetTime(int timeRunSecs);       // Time run in seconds
      void SetDist(double distRunMiles);   // Distance run in miles
      double GetSpeedMph();                // Speed in miles/hour
   __(A)__
      int timeRun;
      double distRun;
};

void __(B)__::SetTime(int timeRunSecs) {
   timeRun = timeRunSecs;  // timeRun refers to data member
}

void __(C)__SetDist(double distRunMiles) {
   distRun = distRunMiles;
}

double RunnerInfo::GetSpeedMph(){
   return distRun / (timeRun / 3600.0); // miles / (secs / (hrs / 3600 secs))
}

int main() {
   RunnerInfo runner1; // User-created object of class type RunnerInfo
   RunnerInfo runner2; // A second object

   runner1.SetTime(360);
   runner1.SetDist(1.2);

   runner2.SetTime(200);
   runner2.SetDist(0.5);

   cout << "Runner1's speed in MPH: " << runner1.__(D)__ << endl;
   cout << "Runner2's speed in MPH: " << __(E)__ << endl;

   return 0;
}
```
# Inline member functions
## Inline member functions 
- A member function's definition may appear within the class definition, known as an #inlineMemberFunction
- Programmers may use inline short function definitions to yield more compact code, keeping longer function definitions outside the class definition to avoid clutter
- Functions can only have one definition so if something is defined inline it cannot be later defined outside that initial class definition
# Mutators, accessors, and private helpers
- A class' public functions are commonly classified as either mutators or accessors
	- #mutator function may modify a class' data members
	- #accessor accesses data members bud doesn't modify a class' data members
- Data members commonly has two associated functions: a mutator for setting the value and an accessor for getting the value, known as a #setter and #getter function, respectively and typically with names starting with set or get
- Other mutator and accessors may exist that aren't associated with just one data member such as the Print() function
- Accessors are defined as const to make clear that data members won't be changed
- #const after a member function's name and parameters causes a compiler error if the function modifies a data member
- If a const member function calls another member function, that function must also be a const
## Private helper functions
- A programmer creates private functions, known as #privateHelperFunctions to help public functions carry out tasks
- These functions can only called from the class' other functions
# Initialization and constructors
- *Good practice is to intialize all variables when declared*
## Data member initialization (C++11)
- since C++11, a programmer can initialize data members in the class definition. Any variable declared of that class type will initially have those values
## Constructors
- #constructor is called automatically when a variable of that class type is declared, and which can initialize data members
- #defaultConstructor is a constructor callable without arguments
	- This means that it will call an instance of the object with the default private attributes laid out in the object definition
- Constructor has the same name as the class
- Constructor function with no return type (not even a void) is the definition for the class 

Example of a default constructor in the context of a constructor that sets creates restaurant type objects:

```
Restaurant::Restaurant() {  // Default constructor
   name = "NoName";         // Default name: 
                            . NoName indicates name was not set     rating = -1;             
                                 // Default rating:                                               -1 indicates rating                                                was not set
}
```


# Classes and vectors/classes
## A class with a vector: The Reviews class
- A class' private data often involves vectors
-  Programmers commonly use classes within classes
# Separate files for classes
## Two files per class
- Programmers typically put all code for a class into two files separate from other code
	- #ClassName `ClassName.h`: contains class definition, including data members and member function declarations
	- `ClassName.cpp` contains member function definitions
- A file that uses the class, such as a main file or ClassName.cpp, must include ClassName.h
- the `.h` files contents are sufficient to allow compilation as long as the corresponding .cpp files is eventually compiled into the program too
# Choosing classes to create
## Decomposing into classes
- Creating a program may start by a programmer deciding what "things" exist, and what each thing contains and does
- Sketching is a good way to outline the qualities of a class `+` public functionality like get/set name, get/set age 
- For private `-` is used
	- These will be the attributes of the object that the public functions will interact and mutate
## Coding the classes
- A programmer can convert the class sketches into code
- You would first create and test the person class followed by the team class which contains objects from the person class
- Each class gets it's own file for definition
- Each class should be tested after its written
## Included files
- *A common error is to include unnecessary .h files, which misleads the reader*
# Unit testing (classes)
## Testbenches
- A #testbench is a program whose job is to thoroughly test another program (or portion) via a series of input/output checks known as #testCases 
- #unitTesting means to create and run a testbench for a specific item (or **unit**) like a function or a class
## Features of a good testbench
- Automatic checks
	- Values are compared only fails are printed
- Independent test cases
	- Each test cases assigns new values, vs. relying on earlier values
- **100% code coverage** 
	- Every line of code is executed 
	- A good testbench would have more test cases 
- Includes #borderCases or atypical cases such as unusually large, negative or 0 numbers
## Regression testing
- #regressionTesting means to retest an item like a class anytime that item is changed
- If previously passed test cases fail, the item has "regressed"
- A testbench should be maintained along with the item, to always be usable for regression testing
- A testbench may be in a class' file or in a separate file as in `MyClassTest.cpp` for testing the class `MyClass.cpp`
- Testbenches may be complex with thousands of test cases
- Various tools support testing and companies employ *Test Engineers* who only test other programmers items
## Erroneous unit tests
- An erroneous unit test may fail even if the code being tested is correct
- *Common error is for a programmer to assume that a failing unit test means that the code being tested has a bug* 
	- Such an assumption may lead someone to waste time on something that already works
	- **Good practice is to inspect the code of a failing unit test before making changes to the code bing tested**
# Constructor overloading
## Basics
- This is for providing different initialization values when creating a new object
- class creator can #overload a constructor by defining multiple constructors differing in parameter types
- A constructor declaration can have args
- The constructor with matching parameters will be called
## If any constructor defined, no-arg constructor should also be defined
- If a programmer defines no constructors, the compiler automatically creates a default no-arg constructor
- *Good practice is for the programmer to also explicitly define a no-arg constructor so that that a declaration like*`MyClass x;`*remains supported* 
## Constructors with default parameter values
- constructor's parameters may be a assigned default values
- If those default values allow the constructor to be called w/o args then that constructor can serve as the default constructor
# Constructor initializer lists
- #constructorInitializerList is an alternative approach for initializing data members in a constructor coming after the colon and consisting of comma-separated list of variableName(initValue) items
- The approach is important when a data member is a class type that must be explicitly constructed
- Otherwise that data member is by default constructed
- Using initialization lists avoids the inefficiency of constructing and then modifying an item
# The 'this' implicit parameter
## Implicit parameter
- An object's member function is called using the syntax `object.Function()`
- The object variable before the function name is known as an #implicitParameter of the member function
	- This is because the compiler converts the call syntax `object.Function(...)` into a function call with a pointer to the object implicitly passed as a parameter
	- Ex: `Function(object, ...)`
- Within a member function the implicitly-passed object pointer is accessible via the name #this 
- Syntax for accessing a member `this->member`
- The `->` is the member access operator for a pointer, similar to the `.` for operator for non-pointers
- Using `this->` makes clear that aclass member is being accessed and is essential if a data member and parameter have the same identifier
## Using 'this' in class member functions and constructors
- When an object's member function is called, the object's memory address is passed to the function via the implicit "this" parameter
- An access in SetTime() to `this->hours` first goes to the object's address, then to the hours data member
- If SetTime() instead has the assignment hours = timeHr, the compiler would use `this->hours` for hours because no other variable in SetTime() is named hours
# Operator overloading
## Overview
- C++ allows a programmer to redefine the functionality of built-in operators like `+ , - , and *` to operate on programmer defined objects
	- This is known as #operatorOverloading
- Suppose a class `TimeHrMn` has data members hours and minutes
	- Overloading `+` would allow two `TimeHrMn` objects to be added with the `+` operator
## Overloading TImeHrMn's operator
- To overload +, the programmer creates a member function named operator+ 
- Although `+` requires left and right operands as in `time1 + time 2` the member function only requires the right operand as the parameter, because the left operand is the calling object
	- in other words `time1 + time 2` is equivalent to the function call `time1.operator+(time2)` which is valid syntax but almost never used
## Overloading the `+` operator multiple times
- When an operator like `+` has been overloaded, the compiler determines which `+` operation to invoke based on the operand types
- In 4 + 9, the compiler sees two integer operands and thus applies the built-in `+` operation 
- in `time1 + time2` where time 1 and time2 are `TimeHrMn` objects, the compiler sees two TimeHrMn operands and thus invokes the programmer-defined function
- A programmer can define several functions that overload the same operator, as long as each involves different types so that the compiler can determine which to invoke 

## Figure 7.14.2: Overloading the + operator multiple times.

```
#include <iostream>
using namespace std;

class TimeHrMn {
public:
   TimeHrMn(int timeHours = 0, int timeMinutes = 0);
   void Print() const;
   TimeHrMn operator+(TimeHrMn rhs);   TimeHrMn operator+(int rhsHours);
private:
   int hours;
   int minutes;
};

// Operands: TimeHrMn, TimeHrMn. Call this "A"
TimeHrMn TimeHrMn::operator+(TimeHrMn rhs) {
   TimeHrMn timeTotal;
   
   timeTotal.hours   = hours   + rhs.hours;
   timeTotal.minutes = minutes + rhs.minutes;
   
   return timeTotal;
}

// Operands: TimeHrMn, int. Call this "B"
TimeHrMn TimeHrMn::operator+(int rhsHours) {
   TimeHrMn timeTotal;
   
   timeTotal.hours = hours + rhsHours;
   timeTotal.minutes = minutes; // Stays same
   
   return timeTotal;
}

TimeHrMn::TimeHrMn(int timeHours, int timeMinutes) {
   hours  = timeHours;
   minutes = timeMinutes;
   
   return;
}

void TimeHrMn::Print() const {
   cout << "H:" << hours << ", " << "M:" << minutes << endl;
}

int main() {
   TimeHrMn time1(3, 22);
   TimeHrMn time2(2, 50);
   TimeHrMn sumTime;
   int num;

   num = 91;
   
   sumTime = time1 + time2; // Invokes "A"   sumTime.Print();
   
   sumTime = time1 + 10;    // Invokes "B"   sumTime.Print();
   
   cout << num + 8 << endl; // Invokes built-in add   
   // sumTime = 10 + time1; // ERROR: No (int, TimeHrMn)   
   return 0;
}


```

# Overloading comparison operators
## Overloading the equality `==` operator
- This is for comparing objects of a programmer-defined class for equality
- To overload `==` the programmer creates a function named `operator==` that returns bool and takes two const reference args of the class type for the left-hand-side and right-hand-side operands
	- Ex: to overload the `==` operator for a Review class, the programmer defines a function `bool operator== (const Review& lhs, const Review& lhs)`
- The programmer must also determine when two objects are considered equal
	- In the review class two Review objects are equal if the objects have the same rating and comment
- The equality operator can be overloaded for operands of different types.
## Overloading the < operator
- A programmer can also overload relational operators like the less than operator `<` 
- The operator should return true if the object on the left side of the `<` is less than the object on the right side of the operator 
## Overloading all equality and relational operators
- A common approach is to first overload the `==` and `<` oeprators and then overload other comparison operators using `==` and `<`
	- Overloading `!=` using `==`:
		- `bool operator!=(const Reviews lhs, const Review& rhs) { return !(lhs = rhs); }`
	- Overloading `>`, `<=` and `>=` using `<`:
		- ```
		  `bool operator>(const Review& lhs, const Review& rhs) { return rhs < lhs; } 
		  bool operator<=(const Review& lhs, const Review& rhs) { return !(lhs > rhs); } 
		  bool operator>=(const Review& lhs, const Review& rhs) { return !(lhs < rhs); }`
		  ```
## Sorting a vector
- The #sort `sort()` function defined in C++ Standard Template Library's (STL) algorithms library can sort vectors containing objects of programmer-defined classes
- To use `sort()` a programmer must:
	- Add `#include <algorithm>` to enable the use of sort()
	- Overload the `<` operator for the programmer-defined class
	- call the `sort()` function as `sort(myVecotor.begin(), myVector.end())`
	Batman = 7
	Up = 2
	It = 13
	Frozen = 11
# Vector ADT
- #standardTemplateLibrary defines classes for common Abstract Data Types (ADTs). A #vector is an ADT of an ordered, indexable list of items. The vector ADT is implemented as a class (actually a class template that supports different types such as `vector<int>` or `vector<string>`)
- For commonly-used vector member functions below, assume a vector is declared as 
- `vector<T> vectorName();`
- where T represents the vector's element type, such as:
- `vector<int> teamNums(5);`
## 

Table 7.16.1: Vector ADT functions.

Notes: size_type is an unsigned integer type. T represents the vector's element type.

|             |                                                                                                                                                                                                         |                                                                                                                                                                  |
| ----------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| at()        | `at(size_type n)`  <br>  <br>Accesses element n.                                                                                                                                                        | teamNums.at(3) = 99;    // Assigns 99 to element 3 <br>x = teamNums.at(3);     // Assigns element 3's value 99 to x                                              |
| size()      | `size_type size() const;`  <br>  <br>Returns vector's size.                                                                                                                                             | if (teamNums.size() > 0) {  // Size is 5 so condition is true<br>   ...<br>}                                                                                     |
| empty()     | `bool empty() const;`  <br>  <br>Returns true if size is 0.                                                                                                                                             | if (teamNums.empty()) {  // Size is 5 so condition is false<br>   ...<br>}                                                                                       |
| clear()     | Removes all elements. Vector size becomes 0.                                                                                                                                                            | teamNums.clear();         // Vector now has no elements<br>cout << teamNums.size();  // Prints 0<br>teamNums.at(3) = 88;      // Error; element 3 does not exist |
| push_back() | `void push_back(const T& x);`  <br>  <br>Copies x to new element at vector's end, increasing size by 1. Parameter is pass by reference to avoid making local copy, but const to make clear not changed. | // Assume vector is empty<br>teamNums.push_back(77);  // Vector is: 77 <br>teamNums.push_back(88);  // Vector is: 77, 88<br>cout << teamNums.size(); // Prints 2 |
| erase()     | `iterator erase (iteratorPosition);`  <br>  <br>Removes element from position. Elements from higher positions are shifted back to fill gap. Vector size decrements.                                     | // Assume vector is 77, 33, 88<br>teamNums.erase(teamNums.begin() + 1); // Now 77, 88<br>// (Strange position indication explained below)                        |
| insert()    | `iterator insert(iteratorPosition, const T& x);`  <br>  <br>Copies x to element at position. Items at that position and higher are shifted over to make room. Vector size increments.                   | // Assume vector is 77, 88<br>teamNums.insert(teamNums.begin() + 1, 33); // Now 77, 33, 88                                                                       |
- push_back() appends an item to the vector's end, automatically resizing the vector
- One can deduce that the vector class has a private data member that stores the current size In fact, the vector class has several private data members
	- However, to use a vector, a programmer only need to know the public abstraction of the vector ADT
## vector's insert() and erase() member functions
- The `insert()` function takes a position arg indicating where the new element should be inserted
	- However, position is not just a number like 1 but is rather `myVector.begin() + 1` 
	- erase function works similarly
- `erase()` can be used to extend the player jersey numbers program with a player delete option
## Inserting elements in sorted order
- common use of `insert()` is to insert a new item in sorted order
# Namespaces
## Defining a namespace
- #nameConflict occurs when two or more items like variables, classes or functions have the same name
	- Ex: One programmer creates a Seat class for auditoriums, and a second programmer creates a Seat class for airplanes
	- Third programmer creating a reservation system for airlines and concert tickets wants to use both Seat classes but a error occurs for name conflict
- #namespace defines a region (or scope) used to prevent name conflicts
- Above, the auditorium seat class code can be put in an `auditorium` namespace, and airplane seat class code in an `airplane`name space #scopeResolutionOperator `::` allows specifying in which namespace to find a name, as in: `auditorium::Seat concertSeat;` and `airplane::Seat flightSeat;`
## std namespace
- All items in the C++ standard library are part of the #std namespace (short for standard)
- To use classes like string or predefined objects like cout, a programmer can use one of two approaches:
	1. #scopeResolutionOperator `::` can be used to specify std namespace before C++ std library items
		 Ex: `std::cout << "Hello";` or `std::string userName;`
	 2. #nameSpaceDirective can add the statement using `namespace std;` to direct compiler to check the std namespace for any names later in the file that aren't otherwise declared
		 Ex: For `string userName;` the compiler will check namespace std for string
 - *Most guidelines discourage `using namespace`*


  # Static data members and functions
  ## Static data members
  - Keyword static indicates a variable is allocated in memory only once during a program's execution
  - static vars are allocated once and reside in static memory for entire program
	  - retains value throughout the program
  - #staticDataMember in a class is a data member of the class instead of data member of each class object
  - Thus, static data members are independent of any class object and can be accessed without creating a class object 
  - static data member is declared inside inside the class definition but must also be defined outside the class declaration within a class function
  - a static data member can be accessed just by var name
  - A public static data member can be accessed outside the class using the scope resolution operator
  ## Static member functions
  - #staticMemberFunction
  - is a class function that is independent of class objects
  - Static members functions are typically used to access and mutate private static data members from outside the class 
  - Since static methods are independent of class objects the this parameters is not passed to a member function so 