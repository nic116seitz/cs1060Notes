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
## common erorrs
- A common error is to use the opposite loop expression than desired, like using `x == 0` rather than `x != 0`
- One should remember that the expression describes when the loop should iterate not when the loop should terminate
- An #infiniteLoop is a loop that never 