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
- 