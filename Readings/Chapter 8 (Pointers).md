## Pointers
- A #pointer is a variable that contains a memory address
## Handling different amounts of data
- A program often needs to support data of varying sizes 
- Using a predefined fixed-size array may either waste memory or limit the program's usefulness
## Pointers and dynamically allocated data
- A program can use dynamically allocated array to efficiently handle different amounts of data
- #dynamically allocated array has a size and mem location determined during runtime
- pointer variable is used to store the array's memory location
	- This is due to its dynamic nature as it will change each time the array is dynamically allocated
## Inserting data in arrays/vectors vs linked lists
- Array/Vector stores elements in contiguous memory locations, which enables fast access to any element using the element's index
- inserting an item requires making room by shifting higher-indexed items
- A programmer can use linked list to make inserts faster
- #linkedList consists of items that contain both data and a pointer (link) to the next list item
- Inserting a new item between tow existing items just requires a few operations to update each item's pointer
# Pointers and dynamically allocated arrays
## Pointers and dynamically allocated arrays
- #dynamicallyAllocatedArray size and memory location is determined during runtime
- #new operator can be used to allocate an array
	- allocates memory for the given type and returns a pointer to the allocated memory
	- Ex: `new double[3]` dynamically allocates a double array with three elements
- #pointer can be used to hold the array's memory location
	- pointer is a variable that holds a memory address, rather than holding data
	- it is declared by including `*` before the pointer's name
	- Ex: `double* recordedTimes` declares a double pointer named recordedTimes
- A syntax example below:
```
int numOfsprints;
double* recordedTimes;

cin >> numOfSprints;
recordedTimes = new double[numOfSprints];
```
## Accessing elements in a dynamically allocated array
- elements can be accessed in the same way
- Each element is accessible using `[i]` with the element's index i
- Programs typically uses an integer variable to hold the array size
- Ex: 
```
recordedTimes = new double[numOfSprints];

for (i=0; i < numOfSprints; ++i) {
	cin >> recordedTimes[i];
}
```
- If you exceed the size of an array memory location not allocated to the array gets over written possibly corrupting data in other variables
## Deleting dynamically allocated array
- Dynamically allocated memory must be explicitly deallocated once the program no longer needs the memory
- deallocated memory is then available for allocations to other calls of new
- #delete `delete[]` operator is used to deallocate an array allocated with the new operator
	- Ex `delete[] dynamicallyAllocatedArray;`
- if the array doesn't exist an error occurs
- After delete a program should not attempt to access to access the array pointed to by the pointer variable
- Accessing memory that has been deallocated, such as a deleted dynamically allocated array is a common error and may cause strange program behavior
- Deleting a dynamically allocated array should be done after the last call to the array
- Failing to deallocate memory will cause the program to crash as it excessively pulls memory from the computer
## nullptr
- pointer when declared holds unknown address until initialized
- you may wish to indicate that a pointer points to nothing
	- in this case you may initialize to null
- #nulll means nothing
-  pointer assigned with keyword #nullptr is null
- *check that a pointer is not null before accessing*
#Question : are pointers used to store or point to dynamically allocated arrays

# Changing the size of a dynamically allocated array
## Appending an element to an array
- If you need to change the size of a dynamically allocated array a new array with increased capacity must be allocated
- program must also use a var to hold array's size
- For this the new array should:
	1. Dynamically allocate new array w/ space for additional element
	2. copy existing array's contents to new array
	3. delete existing array
	4. assign array's pointer with new array's address
	5. add new element to last index
	6. Increment var holding array's size
Ex:
```
cin >> nextInput;

newArray = new double[sleepHrsSize + 1];
for (i = 0; i < sleepHrsSize; ++i) {
	newArray[1] = sleepHrs[1];
}

delete[] sleepHrs;

sleepHrs = newArray;

sleepHrs[sleepHrsSize] = nextInput;
++sleepHrsSize;
```

## Appending one array to another array
1. Dynamically allocate new array with space for new elements
2. copy existing array to new array
3. delete existing
4. Assign old array pointer with the new array address
5. append additional elements to new array
6. Update var holding the array's size with the sum of original and num of additional
Ex:
```
newArray = new double[sleepHrsSize + todaysHrsSize];

for (i = 0; i < sleepHrsSize; ++i) {
	newArray[1] = sleepHrs[1];
}
delete[] sleepHrs;

sleepHrs = newArray;

for (i = 0; i < todaysHrsSize; ++i) {
	sleepHrs[sleepHrsSize + i] = todaysHrs[i];
} 

sleepHrsSize += todaysHrsSize;
```

## efficient way to increase array cap
- for efficient solution is to allocated extra cap whenever array is expanded
- Options:
	- A variable to hold the array's cap which is the total number of elements that the array can contain
	- A variable to hold the array's  size
	- an algo to increase the array's capacity commonly by doubling
## Deleting an element from an array
- causes num of existing elements to decrease by one without changing cap
- to maintain continuity all elements after the deleted element are copied to the preceding array index
# Dynamically allocating objects
## Pointer and dynamically allocated objects
- if type is a class, the new operator calls the class' constructor after allocating mem for the object
## Constructor args
- when using pointer to an object, #memberAccessOperator allows access to the object's members with the syntax `a->b`
- Ex: If sleepRecord is a pointer to a Sleep object, then 
  `sleepRecord->Print()` calls the `Print()` member function
- spaces can appear around the `->` operator
## Dereference operator
- #dereferenceOperator `*` is prepended to a pointer variable's name to retrieve the data which the pointer variable points
- The `*` operator and the `.` operator may be combined to access a dynamically allocated object's members a s in `(*a).b` instead of `a->b`
- Ex: `sleepRecord->Print() == (*sleepRecord).Print()`
# Arrays of dynamically allocated objects
- Class methods can be accessed by calling using the array location and then the method being called
	- Ex: `pressureReadings[0].Print();` this calls the print class  method on the first BloodPressure object in pressure readings 
- #delete `delete[]` is used to deallocate an array allocated with the new operator
# Classes with dynamically allocated data
- Three class members are needed to implement an array with extra capacity:
	- Pointer to hold the dynamically allocated array's address
	- A capacity to hold the total number of elements that the array can hold
	- Size to hold the number of elements currently held in the array
##  Reference for generating linked list from loops
```
#include <iostream>
#include <cstdlib>
using namespace std;

class IntNode {
public:
   IntNode(int dataInit = 0, IntNode* nextLoc = nullptr);
   void InsertAfter(IntNode* nodeLoc);
   IntNode* GetNext();
   void PrintNodeData();
private:
   int dataVal;
   IntNode* nextNodePtr;
};

// Constructor
IntNode::IntNode(int dataInit, IntNode* nextLoc) {
   this->dataVal = dataInit;
   this->nextNodePtr = nextLoc;
}

/* Insert node after this node.
 * Before: this -- next
 * After:  this -- node -- next
 */
void IntNode::InsertAfter(IntNode* nodeLoc) {
   IntNode* tmpNext = nullptr;
   
   tmpNext = this->nextNodePtr;    // Remember next
   this->nextNodePtr = nodeLoc;    // this -- node -- ?
   nodeLoc->nextNodePtr = tmpNext; // this -- node -- next
}

// Print dataVal
void IntNode::PrintNodeData() {
   cout << this->dataVal << endl;
}

// Grab location pointed by nextNodePtr
IntNode* IntNode::GetNext() {
   return this->nextNodePtr;
}

int main() {
   IntNode* headObj = nullptr; // Create IntNode pointers
   IntNode* currObj = nullptr;
   IntNode* lastObj = nullptr;
   int i;                // Loop index
   
   headObj = new IntNode(-1);        // Front of nodes list
   lastObj = headObj;
   
   for (i = 0; i < 20; ++i) {        // Append 20 rand nums
      currObj = new IntNode(rand());
      
      lastObj->InsertAfter(currObj); // Append curr
      lastObj = currObj;             // Curr is the new last item
   }
   
   currObj = headObj;                // Print the list
   
   while (currObj != nullptr) {
      currObj->PrintNodeData();
      currObj = currObj->GetNext();
   }
   
   return 0;
}
```

# Memory Regions: Heap/Stack
- #code - region where program instructions are stored
- #StaticMemory - region where global variables as well as static local variables are allocated
	- Static variables are allocated once and stay in the same memory location for the duration of a program's execution
- #TheStack - region where a function's local variables are allocated during a function call
	- function call allocates local variables to the stack 
	- return removes
- #TheHeap  - region where "new" operator allocates memory, and where the `delete` operator deallocates memory aka known as #freeStore
# Additional material: Destructors (Simple linked lists)
- #desturctor is a special class member function that is called automatically when a variable of that class type is destroyed
- Within the public class definition the destructor syntax is a function prepended with `~` 
	- Ex:
	- `~LinkedList()`
	- This can be expanded to also create an output or do something else with the value like below
```
class ClassName {
	public:
		IntNode(int value) { //class constructor
			numVal = vlaue;
		}
		~IntNode() { //class destructor
			cout << numVal << endl; //prints the numVal property then deletes
		}		
}
...
```
Example of a ClassList and Class nodes being deleted:
```
#include <iostream> 
using namespace std; 
class IntNode { 
	public: IntNode(int value) {
		numVal = value; 
	} 
	~IntNode() {
		 cout << numVal << endl; 
	} 
	 int numVal;
	 IntNode* next;
}; 
class IntLinkedList {
	 public: IntLinkedList(); 
	 ~IntLinkedList();
	  void Prepend(int);
	  
	  IntNode* head; 
};
IntLinkedList::IntLinkedList() {
	head = nullptr; 
} 
IntLinkedList::~IntLinkedList() {
	while (head) {
		IntNode* next = head->next;
		delete head;
		head = next; 
	}
	cout << "end of list" << endl;
} 
void IntLinkedList::Prepend(int dataValue) {
	IntNode* newNode = new IntNode(dataValue);
	newNode->next = head;
	head = newNode; 
} 
int main() { 
	IntLinkedList* list = new IntLinkedList(); 
	
	list->Prepend(2); 
	list->Prepend(4); 
	list->Prepend(6); 
	list->Prepend(8); 
	
	delete list; 
	
	return 0; 
}
```
# Destructors
- #desturctor is a special class member function that is called automatically when a variable of that class type is destroyed
- think of this as the ability to delete the contents of an array using `delete[]` declared the same way as above followed by the parameter you want to delete
# Memory leaks
- #MemoryLeak occurs when a program that allocates memory loses the ability to access the allocated memory, typically due to a failure to properly destroy/free dynamically allocated memory
- *common error is failing to free allocated memory that is no longer used resulting in a memory leak*

# Copy constructor
```
#include <iostream>
using namespace std;

class MyClass {
public:
   MyClass();
   MyClass(const MyClass& origObject); // Copy constructor
   ~MyClass();
   
   // Set member value dataObject
   void SetDataObject(const int setVal) {
      *dataObject = setVal;
   }
   
   // Return member value dataObject
   int GetDataObject() const {
      return *dataObject;
   }
private:
   int* dataObject;// Data member
};

// Default constructor
MyClass::MyClass() {
   cout << "Constructor called." << endl;
   dataObject = new int; // Allocate mem for data
   *dataObject = 0;
}

// Copy constructor
MyClass::MyClass(const MyClass& origObject) {
   cout << "Copy constructor called." << endl;
   dataObject = new int; // Allocate sub-object
   *dataObject = *(origObject.dataObject);
}

// Destructor
MyClass::~MyClass() {
   cout << "Destructor called." << endl;
   delete dataObject;
}

void SomeFunction(MyClass localObj) {
   // Do something with localObj
}

int main() {
   MyClass tempClassObject; // Create object of type MyClass
   
   // Set and print data member value
   tempClassObject.SetDataObject(9);
   cout << "Before: " << tempClassObject.GetDataObject() << endl;
   
   // Calls SomeFunction(), tempClassObject is passed by value
   SomeFunction(tempClassObject);
   
   // Print data member value
   cout << "After: " << tempClassObject.GetDataObject() << endl;
   
   return 0;
}
```
# Copy assignment operator
## Default assignment operator behavior
- Given two MyClass objects
- Copy would be `classObj2 = classObj1;` to copy classObj1 to classObj2
- not good for use with pointer members as 
 

## Figure 8.15.1: Assignment operator performs a deep copy.
```
#include <iostream>
using namespace std;

class MyClass {
public:
   MyClass();
   ~MyClass();
   MyClass& operator=(const MyClass& objToCopy);   
   // Set member value dataObject
   void SetDataObject(const int setVal) {
      *dataObject = setVal;
   }
   
   // Return member value dataObject
   int GetDataObject() const {
      return *dataObject;
   }
private:
   int* dataObject;// Data member
};

// Default constructor
MyClass::MyClass() {
   cout << "Constructor called." << endl;
   dataObject = new int; // Allocate mem for data
   *dataObject = 0;
}

// Destructor
MyClass::~MyClass() {
   cout << "Destructor called." << endl;
   delete dataObject;
}

MyClass& MyClass::operator=(const MyClass& objToCopy) {
   cout << "Assignment op called." << endl;
   
   if (this != &objToCopy) {           // 1. Don't self-assign
      delete dataObject;                  // 2. Delete old dataObject
      dataObject = new int;               // 3. Allocate new dataObject
      *dataObject = *(objToCopy.dataObject); // 4. Copy dataObject
   }
   
   return *this;
}

int main() {
   MyClass classObj1; // Create object of type MyClass
   MyClass classObj2; // Create object of type MyClass
   
   // Set and print object 1 data member value
   classObj1.SetDataObject(9);
   
   // Copy class object using copy assignment operator
   classObj2 = classObj1;
   
   // Set object 1 data member value
   classObj1.SetDataObject(1);
   
   // Print data values for each object
   cout << "classObj1:" << classObj1.GetDataObject() << endl;
   cout << "classObj2:" << classObj2.GetDataObject() << endl;
   
   return 0;
}
```
# Rule of three
#ruleOfThree
- if a programmer explicitly defines any one of three special member functions then the programmer should explicitly define all three
	- Namely destructor copy constructor or copy assignment operator
- these three are also called #theBigThree
- *good practice is to always follow the rule of three and define the big three if any one of these functions is defined *

## Default destructor, copy constructor and copy assignment operator
- IF a programmer doesn't define a special member function then the compiler defines default implementation
	- #defaultDestructor does nothing
	- #defaultCopyConstructor initializes an object's data members with a copy, by value of another object's corresponding members
		- this is called a shallow copy
	- #defaultCopyAssignmentOperator assigns an object's data members with a copy, by value of another object's corresponding members
# Smart pointers
## unique_ptr for single objects
- #smartpointer is a class that wraps around a pointer to an object to simplify the memory management of the object
- to distinguish from pointer the latter is reffered to as raw pointer
- #unique_ptr is a smart pointer that only permits one owner over an object
	- when it goes out of scope the object owned by it is auto deleted
	- to use must include `#include <memory>`
## 

able 8.17.1: Types of smart pointers.

| Type       | Features                                                                                                                                                                                                                                  | When to use                                                                       |
| ---------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------- |
| unique_ptr | A unique_ptr only allows an exclusive ownership of the object. The object's ownership can be transferred to a different unique_ptr, but not shared. When a unique_ptr goes out of scope, the object owned by the unique_ptr is deleted.   | As an efficient replacement of raw pointer                                        |
| shared_ptr | A shared_ptr permits shared ownership of an object. When the last owner of the object goes out of scope, the object is deleted. Internally, a counter, called the reference count, keeps track of the number of owners sharing an object. | When a dynamically allocated object is shared by multiple pointers                |
| weak_ptr   | A weak_ptr allows access to, but not ownership of, an object that is owned by a shared_ptr.                                                                                                                                               | To interact with a dynamically allocated object whose memory is managed elsewhere |
|            |                                                                                                                                                                                                                                           |                                                                                   |
Example of uniue_ptr:
```
class Sleep{
	public:
		Sleep();
		~Sleep();
		void Set(int hoursVal, int minutesVal);
		void Print();
		
		private:
			int hours;
			int minutes;
};
...

void RunSleep(int hoursVal, int minutesVal) {
	unique_ptr<Sleep> sleepRecord(new Sleep());
	
	sleepRecord->Print();
}
```
## 

able 8.17.1: Types of smart pointers.

| Type       | Features                                                                                                                                                                                                                                  | When to use                                                                       |
| ---------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------- |
| unique_ptr | A unique_ptr only allows an exclusive ownership of the object. The object's ownership can be transferred to a different unique_ptr, but not shared. When a unique_ptr goes out of scope, the object owned by the unique_ptr is deleted.   | As an efficient replacement of raw pointer                                        |
| shared_ptr | A shared_ptr permits shared ownership of an object. When the last owner of the object goes out of scope, the object is deleted. Internally, a counter, called the reference count, keeps track of the number of owners sharing an object. | When a dynamically allocated object is shared by multiple pointers                |
| weak_ptr   | A weak_ptr allows access to, but not ownership of, an object that is owned by a shared_ptr.                                                                                                                                               | To interact with a dynamically allocated object whose memory is managed elsewhere |
