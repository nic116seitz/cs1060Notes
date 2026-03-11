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
## Accessing elements in a dynamically allocated array
- elements can be accessed in the same way
- Each element is accessible using `[i]` with the element's index i
- Programs typically uses an integer variable to hold the array size