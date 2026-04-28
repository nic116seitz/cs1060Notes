# Required Components
## Person
- Abstract superclass
	- Will have the following properties
		- [ ] Person
			- [ ] First name
			- [ ] Last name
			- [ ] Street name
			- [ ] Method to set first name
			- [ ] Method to set last name
		- [ ] CollegeEmployee
			- [x] Descends from person
			- [x] SSN
			- [x] Annual Salary
			- [x] Department names
			- [x] Methods that override person methods to accept and display CollegeEmployee
				- *This means that the methods in the person class will have to be changed to virtual methods so that they may be overridden*
		- [ ] Faculty
			- [ ] Descends from College Employee
			- [ ] Includes a bool field that will say if they are tenured
		- [ ] Student
			- [x] Descends from person
			- [x] Major
			- [x] field of study
			- [x] GPA
		- [ ] Final Functionality
			- [ ] List all function
				- [ ] Caller Function to call the other print functions for each category level of person
				- [ ] Print function for faculty
				- [ ] Print function for Student
				- [ ] Print Function for non Faculty college employees
			- [ ] Change by name
			- [ ] Change by SSN
	- [ ] Going to different vectors for each of the types

## Todo April 20th 
- [ ] check overrides