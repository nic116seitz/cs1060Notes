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
