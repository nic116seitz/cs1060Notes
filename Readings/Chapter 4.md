# Loops (general)
## Loop basics
- A #loop is a program construct that repeatedly executes the loop's statments (known as the #loopBody)
- While the loop's expression is true; when the expression is false execution proceeds past the loop
- Each time through a loop's statements is called an #iteration
- 
# While loops
## While loop: Basics
- A #whileLoop is a program construct that repeatedly executes a list of sub-statements (known as the #loopBody) while the loop's expression evaluates to true 
- Each execution of the loop body is called an #iteration Once entering the loop body execution continues to the  body's end even if the expression would become false midway through
## Getting input before a loop
- The above examples got user input into a variable only at the end of the loop body
- The examples assigned that variable an initial value that always caused the loop body to execute the first time
- Another common pattern gets that initial value from user input as well, thus getting input in two places: before the loop, and the loop body's end
## Loop expressions
- Various kinds of expressions are found in while loop expressions
- Ex: 
	- sometimes a loop is executed as long as a value is greater than another value or less than another value
	- sometimes a loop is executed as long as a value is not equal to another value
## common errors
- A common error is to use the opposite loop expression than desired, like using `x == 0` rather than `x != 0`
- One should remember that the expression describes when the loop should iterate not when the loop should terminate
- An #infiniteLoop is a loop that never 
## Getting input until a sentinel is seen
- Loops are commonly used to process an input list of values. A #sentinelValue is a special value indicating the end of a list such as a list of positive integers ending with 0, 
# For loops
## Basics
- A loop commonly must iterate a specific number of times such as 10 times
- Though achievable with a while loop. the situation is so common that a special kind of loop exists
- A #forLoop is a loop with three parts at the top loop variable initialization a loop expression and a loop variable update
- A loop describes iterating a specific number of times more naturally than a while loop
```
for (intialExpression; conditionExpression; updateExpression) {
// Loop Body
}
```
- the language supports an #incrementOperator `++i` 
- likewise there is also a #decrementOperator which is `--i`
- There are two increment operators when the plus comes before that is a pre-increment and when the ++ comes after that is a post increment
- `++i` increments before evaluating to a value
- `i++` increments after
- This means if i is 5 `++i` outputs 6 while `i++` outputs 5 (and then becomes 6). 
- When using for loops you can set the first input to determine the amount of times the loop will execute
## Choosing among for and while loops
- Generally a programmer uses a for loop when the number of iterations is known
# More examples
- Analyzing data is a common programming task
- A common data analysis task is to find the maximum value in a list of values
- A loop can achieve that task by updating a max-seen-so-far variable on each iteration 
## Beyond iterating N times
- The three parts of a for loop may be adjusted to do more than just iterate N times. For example, a for loop can output various sequences
## Loop style issues
#### Starting with 0
- Programmers in C, C++, Java and other languages have generally standardized on looping N times by starting with `i = 0` and checking for `i < N`, rather than by using `i = 1` and `i <= N`
- One reason is due to the other constructs (array/vectors), often used with loops, start with 0
- Another is simply that a choice was made
#### The ++ operators
- The `++` operator can appear as `++i` #prefixForm or as `i++` #postfixForm `++i` increments i first and then evaluates the result, while `i++` evaluates the results first and then increments i. The distinction is relevant in a statement like `x = ++I` vs `x = i++` if i is 5 the first yields `x = 6` and the second `x = 5`
- Some consider `++i` safer for beginners in case they type `i = ++i` which typically works as expected (whereas i = i++ does not),
#### In-loop declaration of i
- Variables can be declared throughout code, so many programmers use: `for (int i = 0; i < N; ++i)`. 
## Common errors / good practice
- *a common error is to have a ++i; statement in the loop body, causing the loop variable to be updated twice per iteration* 
# Loops and strings
## Iterating through a string with a for loop
- A programmer commonly iterates through a string, examining each character. The following example counts the number of letters in a string, not counting digits, symbols, etc.
## Iterating until done with a while loop
- A programmer commonly wishes to iterate through a string until something is done.
- A #nestedLoop is a loop that appears in the body of another loop
- The nested loops are commonly referred to as the #innerLoop and #outerLoop
- Nested loops have various uses
	- One it to generate all the combinations of some items
# Break and continue
- a #breakStatement in a loop causes an immediate exit of the loop
- a break statement can sometimes yield a loop that is easier to understand
- A #continueStatement in a loop causes an immediate jump to the loop condition check
- a continue statement can sometimes improve the readability of a loop. 
4.9.1 Though process notes
- first loop: result = 3 | a = 3 
- second loop: result = 8 | a = 4 | b 
# Variable name scope 
## Scope of names
- A declared name is only valid within a region of code known as the name's #scope
- A variable `userNUm` declared in `main()` is only valid within `main()`
- A variable may be declared within other blocks
- A #block is a brace enclosed sequence of statements such as found with an if-else, for loop, or while loop. A variable name'scope extends from the declaration to the closing brace
## For loop index
- Programmers commonly declare a for loop's index variable in the for loop's initialization statement
- That index variable's scope covers the other parts of the for loop up to the for loop's closing brace
- The reason is clear from the for loop's equivalent while loop code shown below, noting the braces around equivalent code

## 

able 4.10.1: Index variable declared in a for loop's initialization statement.

| for loop                                                                        | Equivalent while loop                                                                                           |
| ------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------- |
| for (int i = 0; i < 5; ++i) {<br>   x = x + i;<br>}<br><br>x = x + i;  // ERROR | {<br>   int i = 0;<br>   while (i < 5) {<br>      x = x + i;<br>      ++i;<br>   }<br>}<br>x = x + i;  // ERROR |
## Common error
- *A common error is to declare a variable inside a loop whose value should persist across iterations* 
## Enumerations
- Some variables only need to store a small set of named values
	- Ex: A variable representing a traffic light need only store values named GREEN, YELLOW, or RED. 
- #enumerationType declares a name for a new type and possible values for that type

Construct 4.11.1: Enumeration type.

`enum identifier {enumerator1, enumerator2,  ...};`
- The items within the braces ("enumerators") are integer constants automatically assigned an integer value, with the first item being 0, the second 1, and so on. An enumeration declares a new data type that can be used like the built-in types int, char, etc.
- because different enumerated types might use some of the same names *good practice is to prepend the distinguishing prefix*
- enumerations are used vs strings because enumerations are safer
- If using a string you may not get an error if the string is not within the possible enumerations
- Enumeration also allows for cleaner code as compared to the bool type
- When declaring a second variable you can give it the same enumerations as another by declaring it after the initial variable declared with the enumeration type
- The different enumerators correspond to a number signifying which enumerator is "active"
## 4.12 C++ example: Salary calculations with loops
- A program may exec the same computations repeatedly
