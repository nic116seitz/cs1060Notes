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
