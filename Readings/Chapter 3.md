# If-else branches (general)
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