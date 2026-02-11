"#If-else br nches (general)
## Branch basics (If)
- In a program a #branch is a sequence of statements only executed under a certain condition
## If - else branches
- an #if-else branch has two branches
	- first branch is executed if an expression is true, else the other branch is executed
## If-elseif-else branches
- Commonly a programmer wishes to take one of multiple branches
- An if-else can be extended to an if-elseif-else structure
- Each branch's expression is checked in sequence
- As soon as one branch's expression is found to be true that branch is taken
- if no branch is found to be true the execution will reach the else branch which then executes
- *Note: Else is optional*
# Detecting equal values with branches
## Detecting if two items are equal using an if statement
- A programmer commonly needs to determine if two items are equal
	- an if statement can be used for this
- An #if statement executes a group of statements if an expression is true
	- Braces surround the if branch's statement
	- #Braces `{}` represent a grouping such as a grouping of statements
- #equalityOperator `==` evaluates to true if the left and right sides are equal
- *Good practice is to indent a branch's statements using a consistent number of spaces*
## Equality and inequality operators
- #inequalityOperator `!=` evaluates to true if the left and right side are not equal or different
## If-else statement
- #if-else statement executes one group of statements when a expression is true and another group of statements when the expression is false
## Multi-branch if-else statements
- You may need a program to detect several specific values of a variable
- An if else can be extended to have 3 or more branches
- Each branch's expression is checked in sequence
- As soon as one branch's expression is found to  be true the branch's statements execute
- If no expression is true the else branch executes
## Comparing characters strings and floating point types
- The relational and equality operators work for integer, character and floating point built-in types
- Comparing characters compares their ASCII numerical encoding
- Floats should not be compared using the equality operators due to the imprecise representation of floating point numbers
- The operators can be used for the string type
- If they have the same number of characters and corresponding characters are identical
# Detecting ranges with branches (general)
## Detecting ranges using if-elseif-else
- A common programming task is to detect if a value lies within a certain range and then perform an action depending on where the value lies
- if-elseif-else can detect number ranges with each branch performing a different action for each range
- Each expression only needs to indicate the upper range part
## Using multi-branch if else to detect ranges
- Sequential nature of multi-branch if-else statements is useful to detect ranges of numbers
# Detecting ranges with branches
## Relational operators
- #relationOperator checks how one operand's value relates to another like being greater than
## Detecting ranges with if-else statements
- Programmers use sequential nature of multi-branch if-else arrangement to detect ranges of numbers
# Detecting ranges using logical operators
## Logical and or and not
- A #logicalOperator treats operands as being true or false and evaluates to true or false
	- they include #and, #or, and #not 
	- languages typically use various symbols for those operators

| Logical operator | Description                                                      |
| ---------------- | ---------------------------------------------------------------- |
| a AND b          | Logical AND: true when both of its operands are true.            |
| a OR b           | Logical OR: true when at least one of its two operands are true. |
| NOT a            | Logical NOT: true when its one operand is false, and vice-versa. |
The table below has the symbols use to represent logical operators in C++
## Detecting ranges implicitly vs. explicitly
- Logical operators are used to detect a range by explicitly specifying the high-end and low-end of the range
- If a program should detect increasing ranges without gaps a multi-branch if-else statement can be used without logical oeperators
- the low end of the range is implicitly known upon reaching an expression
- Decreasing range without gaps has implicitly known high-ends
# Detecting ranges with gaps
## Basic ranges with gaps
- Often ranges contain gaps
## Ranges with gaps using logical operators
- Programmers often use logical operators to explicitly detect ranges with an upper and lower bound including rnages with gaps that may have intermediate bounds
# Detecting multiple features with branches
## Multiple distinct if statements
- You can use multiple if statements in sequence to detect multiple features with independent actions
	- They look similar to a multi-branch if-else statement
	- Each if-statement is independent and thus more than one branch can execute
## Nested if-else statements
- A branch's statements can include any valid statements, including another if-else statement
- these are known as #nestedIf-else statements
	- Commonly used to make decisions that are based on multiple features
# Common branching errors
## Common error: Missing branches
- When a branch has a single statement the braces are optional
- *Good practice always uses the braces. Always using braces even when a branch only has one statement prevents the common error of mistakenly thinking a statement is part of a branch*
## Common error: Using the incorrect operators
- Most common error in C and C++ is to use = rather than == in an if-else expression
- `=` is assignment and `==` is equality operator
- If you use `=` mistakenly in a if statement it will reassign the variable it is evaluating to the value that you set in the if statement
# Order of evaluation
## Precedence rules
- The order in which operators are evaluated in an expression are known as #prescedenceRules 

| Operator/Convention | Description                                                              | Explanation                                                                                                                                                                     |
| ------------------- | ------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| ( )                 | Items within parentheses are evaluated first                             | In `(a * (b + c)) - d`, the + is evaluated first, then *, then -.                                                                                                               |
| !                   | ! (logical NOT) is next                                                  | `! x \| y` is evaluated as `(!x) \| y`                                                                                                                                          |
| * / % + -           | Arithmetic operators (using their precedence rules; see earlier section) | `z - 45 * y < 53` evaluates * first, then -, then <.                                                                                                                            |
| <   <=   >   >=     | Relational operators                                                     | `x < 2 \| x >= 10` is evaluated as `(x < 2) \| (x >= 10)` because < and >= have precedence over \|.                                                                             |
| ==   !=             | Equality and inequality operators                                        | `x == 0 && x != 10` is evaluated as `(x == 0) && (x != 10)` because == and != have precedence over &&.  <br>== and != have the same precedence and are evaluated left to right. |
| &&                  | Logical AND                                                              | `x == 5 \| y == 10 && z != 10` is evaluated as `(x == 5) \| ((y == 10) && (z != 10))` because && has precedence over \|.                                                        |
| \|\|                | Logical OR                                                               | \| has the lowest precedence of the listed arithmetic, logical, and relational operators.                                                                                       |
## Common Error: Missing parentheses
- Common error is to write expression that is evaluated in a  different order than expected
- *Good practice is to use parentheses in expressions to make the intended order of evaluation explicit*
## Common Error: Math expression of range
- writing expressions like `(16 < age < 25)` as one might see in mathematics 
- The meaning, however, almost certainly is not what the programmer intended. 
	- Suppose age is presently 28
	- Expression is evaluated left to right so evaluation of `16 < age` yields true
	- Next the expression `true < 25` and in this context `true = 1` so the next statement will be considered true
## Common error: Bitwise rather than logical operators
- Logical AND is && and not just `&` and logical OR is `||` not just `|` .`&` and `|` represent #bitwiseOperators which perform AND or OR on corresponding individual bits of the operands
- Common error is to use a bitwise operator instead of a logical operator 
# Switch statements
## Switch Statements
- A #switch statement can more clearly represent multi-branch behavior involving a variable being compared to constant values
- The program executes the first #case whose constant expression matches the value of the switch expression, executes that case's statements and then jumps to the end
- If no case matches then the #defualtCase statements are executed
- Syntax for switch statement is bellow
```
switch (a) {
	case 0:
		// Print "zero"
		break;
		
	case 1:
		// Print "one"
		break;
	
	case 2:
		// Print "two"
		break;
		
	default:
		// print "unknown"
		break;
	}
```
- Multi branch if statement can also be used, but switch statements make the programmers intent clear to those reading the code
## Switch statement general form
- The switch statement's expression should be an integer or char
- The expression should not be a string or a floating-point type
- Each case must have a constant expression like 2 or 'q'
- A case expression cannot be a variable
- The order of cases doesn't matter assuming break statements exist at the end of each case
- *Good practice is to always have a default case for a switch statement. A programmer may be sure all cases are covered only to be surprised that some case was missing*
## Omitting the break statement
- Omitting the #break statement for a case will cause the statements within the next case to be executed
- such "Falling through" to the next case can be useful when multiple cases such as cases 0,1, and 2 should execute the same statements
# Boolean data type
## Boolean data type
- #Boolean refers to a quantity that only has two possible values, true or false
- A Boolean variable may be set using true or false keywords
## Uses of bool type
- Used to simplify a complex expression
- An expression that combines logical and relational operators can be simplified by assigning bool variables with the result of the of the expression using relational operators
- The if-else expression can then consist of only logical operations using those variables
# String comparisons
## String comparison: Equality
- Two strings are commonly compared for equality
- Equal strings have the same number of chars
- Each corresponding char is identical
## String comparison: Relational
- Strings are sometimes compared relationally (less than, greater than)
- A comparison begins at index 0 and compares each character until the evaluation results in false or the end of the string is reached
- If the length of one string is longer than the next the char numbers are not compared and the longer string is greater than the shorter string
# String access operations
## String character indices
- A string is a sequence of characters in memeory
- Each string character has a position number called an #index starting with 0
- `stringVariableName.at(x)` is slicing in C++ x represents the index being sliced
	- If you index past the length of the string it will return an error
## Changing a character in a string
- A char in a string can be assigned
 ```
 userString = "abcde";
 userString.at(3) = 'x';
 // after the above statements userString will equal "abcxe"
 ```
 - This doesn't work with strings being used where x is in the above example
 
 ## Working with the end of a string
 - Determining the last character in a string is often useful
 - if the string's length is known the last index is length -1
 - `.size()` determines the length of a string
 - push_back() adds a character to the end of a string. Ex: If s1 is "Why", `s1.push_back('?');` changes s1 to "Why?".
- append() adds one string to the end of another. Ex: If s1 is "Hey", `s1.append("!!!");` changes s1 to "Hey!!!".
- The + operator can return a new string with one string appended to another string. Ex: If s1 is "Hey", then `s2 = s1 + "!!!";` assigns s2 with "Hey!!!".
- length() is also interchangeable with size()
- When you append even if only appending you must wrap it in a string `""`
## Common errors
- common error is to access an invalid string index especially exactly one larger than the largest index
- The .at(index) function generates an exception if the index is out of range for the string's size
- #exception is detected runtime error that commonly prints an error message and terminates the program
- C++ also supports C-style access of a string using \[] rather than .at
	- This access does not provide error checking
	- *Good practice is to use .at() rather than brackets due to the error checking in .at()* 
 # Character operations
 - Including the #cctypeLibrary via `#include <cctype>` provides several functions for working with chars 
 - ctype stands for character type
 - The first c in cctype indicates the library is originally from the C language
 ## 

Table 3.15.1: Character functions return values.

|            |                                     |                                                                          |     |            |                   |                                                                                           |
| ---------- | ----------------------------------- | ------------------------------------------------------------------------ | --- | ---------- | ----------------- | ----------------------------------------------------------------------------------------- |
| isalpha(c) | true if alphabetic:  <br>a-z or A-Z | isalpha('x') // true<br>isalpha('6') // false<br>isalpha('!') // false   |     | toupper(c) | Uppercase version | letter = toupper('a')  // A<br>letter = toupper('A')  // A<br>letter = toupper('3')  // 3 |
| isdigit(c) | true if digit: 0-9.                 | isdigit('x') // false<br>isdigit('6') // true                            |     | tolower(c) | Lowercase version | letter = tolower('A')  // a<br>letter = tolower('a')  // a<br>letter = tolower('3')  // 3 |
| isspace(c) | true if whitespace.                 | isspace(' ')  // true<br>isspace('\n') // true<br>isspace('x')  // false |     |            |                   |                                                                                           |
- Spaces count as alphas for the sake of checking `isalpha`

# Finding, inserting, and replacing text in a string
## Finding text in a string
- often there is a need to find and work with text inside another string
- #find `find()` function is used to find a string or char inside a string
- if the string is not found then the output will be `string::npos` 
## Finding text starting from the middle of a string
- Sometimes there is a need to find text starting from a specific location inside a string instead of from the beginning of a string
- `find(textToFind, startIndex)` returns the index of the first occurrence of textToFind starting at the index startIndex instead of index 0
- The find function will find return the relative position to the start index specified
## Getting a substring
- #substring is a contiguous part of a string
- `substr(startIndex, numCharacters)` function is used to get a substring of a string
- When used without the length parameter it returns the substring from startIndex to the end of the string
## Inserting and replacing text in a string
- #insert `insert()` inserts text into a string `.insert(startIndex, newText)` this inserts text before the character at startIndex
- #replace `replace(startIndex, numCharacters, newText)` replaces the substring starting at the index with a numCharacters spec
- The num of characters refers to the number of characters being replaced not the length of the text replacing the original
- *Be aware of spacing when using the insert function*
# Conditional expressions
- This is a way to write if statements that changes the syntax to provide shorthand for longer conditionals
```
// Long Form //
if (condition) {
	myVar = expr1;
}
else {
	myVar = expr2;
}

// Short Form //
myVar = (condition) ? expr1 : expr2;

```
- #conditionalExpression has the form `condtion ? exprWhenTrue: exprWhenFalse`
- All three operands are expressions 
- If the condition evaluates to true then `exprWhenTrue` is evaluated
- If the condition is false then the `exprWhenFalse` is evaluated
- A conditional expression has three operands and thus `?` and `:` are sometimes referred to as a #ternaryOperator
- *Good practice is to restrict usage of conditional expression to an assignment statement*
# Floating-point comparison
- Floating-point numbers should not be compared using ==
- Some floating point numbers cannot be exactly represented in the limited memory of 64 bits
- Floating point numbers should be compared for "close enough rather than exact equality"
- for this fabs is used
- the difference indicating threshold that floating-point numbers are equal is often called the #epsilon 
- This value depends on the program's expected values
- In simple terms when comparing two floats you find the difference and then try test to see if the resulting number is less then 0.0001
- Syntax:
	- `fabs(double1 - double2) < 0.0001`
- This is how you get close enough to check for equality among doubles or floats
# Short circuit evaluation
- logical operator evaluates operands from left to right
- #ShortCircuitEvaluation skips evaluating later operands if the result of the logical operator can already be determined
- logical AND operator short circuits to false if the first operand evaluates to false and skips evaluating the second operand
- logical OR operator short circuits to true if the first operand is true and skips evaluating the second operand

| Operator                  | Example                                                                                                                 | Short circuit evaluation                                                                                             |
| ------------------------- | ----------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------- |
| `operand1 && operand2`    | **`true`** `&& operand2`                                                                                                | If the first operand evaluates to true, operand2 is evaluated.                                                       |
| **`false`** `&& operand2` | If the first operand evaluates to false, the result of the AND operation is always false, so operand2 is not evaluated. |                                                                                                                      |
| `operand1 \| operand2`    | **`true`** `\| operand2`                                                                                                | If the first operand evaluates to true, the result of the OR operation is always true, so operand2 is not evaluated. |
| **`false`** `\| operand2` | If the first operand evaluates to false, operand2 is evaluated.                                                         |                                                                                                                      |
**This table is broken try to fix when possible see 3.19.1
