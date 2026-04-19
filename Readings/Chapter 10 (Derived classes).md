- #derivedClass is a class that is derived from another class, called #baseClass or #superclass any class may serve as a base class
- derived class is said to inherit the properties of base class, #inheritance
- #syntax:
	- `class DerivedClass: public BaseClass {...};`
## Inheritance scenarios
- derived class can serve as a base class for another class 
	- Ex:
	- `class Fruititem: public ProduceItem {...}` creates a derived class produce item which was derived from GenericItem
	- `class FrozenFoodItem: public GenericItem {...}`
		- creates a derived class FrozenFoodItem that inherits from GenericItem, just as ProduceItem inherits from GenericItem
# Access by members of a derived class
## Member access
- members of derived class don't have access to the private members of the base class and vice versa
## Protected member access
- public and private are two specifiers 
- third is #protected
	- provides access to derived classes but not to anyone else
## Table 10.2.1: Access specifiers
| Specifier | Description                                             |
| --------- | ------------------------------------------------------- |
| private   | Accessible by self.                                     |
| protected | Accessible by self and derived classes.                 |
| public    | Accessible by self, derived classes, and everyone else. |
**Encapsulation is a goal of OOP. Encapsulation is restricting access to data from outside a class. Protected modifiers loosens encapsulation since data may be directly accessed by the base class and any derived class**
# Overriding member functions
- this is when a derived class defines a member function that has the same name and parameters as the base class's functions
- #override
## Calling a base class function
- Overriding function can call the overridden function by prepending the base class name
- Ex: `Business::GetDescription()`
#### Function calling overridden function of base class
```
class Restaurant : public Business {

   ...

   string GetDescription() const {
      return Business::GetDescription() + "\n  Rating: " + to_string(rating);
   };

   ...
};
```
# Polymorphism and virtual member functions
- #Polymorphism refers to determining which program behavior to execute depending on data types:
	- #Compile-timePolymorphism is where the compiler determines which function to call at compile-time
	- #RuntimePolymorphism is when the compiler is unable to determine which function to call at compile-time, so the determination is made while the program is running
## Virtual functions
- runtime polymorphism only works when an overridden member function in a base class is virtual
- #virtualMember function is a member function that may be overridden in a derived class and is used for runtime polymorphism
- virtual function is declared by prepending the function name with `virtual` 
- #override keyword is an optional keyword used to indicate that a virtual function is overridden in a derived class
	- Syntax: 
	- `Function() const override`
- *Good practice is to use the override keyword when overriding a virtual function ot avoid accidentally misspelling the function name or typing the wrong parameters*
## Pure virtual functrions
- #pureVirtualFunction is a virtual function that provides no definition in the base class and all derived classes must override the function
- syntax for this is `virtual string GetHours() const = 0;` all pureVirtualFunctions must override the base function
- class that has at least one pure virtual function is known as an #abstractBaseClass an abstract base class object cannot be declared
## Abstract classes
- OOP has 3 key features
	- #classes : a class encapsulates data and behavior to create objects
	- #Inheritance: allows one class (subclass) to be based on another class (base class or super)
	- #AbstractClasses: this is a class that guides the design of subclasses but cannot be itself instantiated as an object
# Abstract classes
- #pureVirtualFunction is a virtual function that isn't implemented in the base class
	- All derived classes must override the function
- #AbstractClass is a class that cannot be instantiated as an object but is the superclass for a subclass and specifies how the subclass must be implemented
- #ConcreteClass is a class that is not abstract, and hence an be instantiated

# Is-a versus has-a relationships
- inheritance is commonly confused with the idea of composition
- Composition is the idea that one object may be made up of other objects, such as `MotherInfo` class being made up of objects like `firstName`, `chldrenData`
- UML is used to draw class inheritance relationships 

# UML
## UML class diagrams
- #UnifiedModelingLangauge is a language for software design that uses different types of diagrams to visualize the structure and behavior of programs
- #structuralDiagram visualizes static elements of software, such as the attributes and operations
- #behavioralDiagram visualizes dynamic behavior such as flow of an algo
- #class diagram is a structural diagram that can be used to visually model the classes of a computer program, including member variables and functions
## UML for inheritance
- UML uses an arrow with a solid line and an unfilled arrow to indicated the path of inheritance (arrow points towards the parent class)
- Italics are used to denote abstract classes
