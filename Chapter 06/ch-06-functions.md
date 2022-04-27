# Wrting Functions

## Practice exercise 6.1

Write a function for yourself. We want to write a function that adds two numbers.

  1. Create a function that takes two parameters, adds the parameters together, and returns the result.
  2. Set up two different variables with two different values.
  3. Use your function on the two variables, and output the result using ```console.log```.
  4. Create a second call to the function using two more numbers as arguments sent to the function.

## Practice exercise 6.2

We are going to create a program to randomly describe an inputted name.

  1. Create an array of descriptive words.
  2. Create a function which contains a prompt asking the user for a name.
  3. Select a random value from the array using ```Math.random```.
  4. Output into the console the prompt value and the randomly selected array value.
  5. Invoke the function.

# Parameters & Arguments

## Practice exercise 6.3

Create a basic calculator which takes two numbers and one string value indicating an operation. If the operation equals add, the two numbers should be added. If the operation equals subtract, the two numbers should be subtracted from one another. If there is no option specified, the value of the option should be add.

The result of this function needs to be logged. Test your function by invoking it with different operators and no operator specified.

  1. Set up two variables containing number values.
  2. Set up a variable to hold an operator, either ```+``` or ```-```.
  3. Create a function which retrieves the two values and the operator string value within its parameters. 
  4. Use those values with a condition to check if the operator is ```+``` or ```-```, and add or subtract the values accordingly (remember if not presented with a valid operator, the function should default to addition).
  5. Within ```console.log()```, call the function using your variables and output the response to the console.
  6. Update the operator value to be the other operator type—either plus or minus—and call to the function again with the new updated arguments.


# Return Function Values

We are still missing a very important piece to make functions as useful as they are: the ```return``` value. Functions can give back a result when we specify a ```return``` value.

```
function addTwoNumbers(x, y) {
  return x + y;
}
```

```return``` ends the function and sends back whatever value comes after return. If it is an expression, like the one above, it will evaluate the expression to one result and then return it to where it was called (the result variable, in this instance):

```
let result = addTwoNumbers(4, 5);
console.log(result);
```
With these adjustments made, the code snippet logs ```9``` to the terminal.

![image](https://user-images.githubusercontent.com/47826697/165562060-38499436-eef7-4958-9969-d615e33bd498.png)


What do you think this code returns?

```
let resultsArr = [];
for(let i = 0; i < 10; i ++){
  let result = addTwoNumbers(i, 2*i);
  resultsArr.push(result);
}
console.log(resultsArr);
```

<details>
<summary>Click to see soluton!</summary>

It logs an array of all the results to the screen. The function is being called in a loop. The first iteration, ```i```, equals ```0```. Therefore, the result is ```0```. The last iteration, ```i```, equals ```9```, and therefore the last value of the array equals ```27```. Here are the results:

 ```
[
   0,  3,  6,  9, 12,
  15, 18, 21, 24, 27
]
  ```
</details>

## Practice exercise 6.4

Modify the calculator that you made in Practice exercise 6.2 to return added values instead of printing them. Then, call the function 10 or more times in a loop, and store the results in an array. Once the loop finishes, output the final array into the console.

  1. Set up an empty array to store the values that will be calculated within the loop.
  2. Create a loop that runs 10 times, incrementing by 1 each time, creating two values each iteration. 
  3. For the first value, multiply the value of the loop count by 5. 
  4. For the second value, multiply the value of the loop counter by itself.
  5. Create a function that returns the value of the two parameters passed into the function when it is called. 
  6. Add the values together, returning the result.
  7. Within the loop, call the calculation function, passing in the two values as arguments into the function and storing the returned result in a response variable.
  8. Still within the loop, push the result values into the array as it iterates through the loop.
  9. After the loop is complete, output the value of the array into the console.

You should see the values ```[0, 6, 14, 24, 36, 50, 66, 84, 104, 126]``` for the array in the console.


# Recursive functions

In some cases, you want to call the same function from inside the function. It can be a beautiful solution to rather complex problems. There are some things to keep in mind though. What do you think this will do?

```
function getRecursive(nr) {
  console.log(nr);
  getRecursive(--nr);
}
getRecursive(3);
```

<details>
<summary>Click to see solution!</summary>

  It prints 3 and then counts down and never stops. Why is it not stopping? Well, we are not saying when it should stop. 
</details>


Look at our improved version:

```
function getRecursive(nr) {
  console.log(nr);
  if (nr > 0) {
    getRecursive(--nr);
  }
}
getRecursive(3);
```
This function is going to call itself until the value of the parameter is no longer bigger than ```0```. And then it stops.

What happens when we call a function recursively is it goes one function deeper every time. The first function call is done last. For this function it goes like this:

```
getRecursive(3)
getRecursive(2)
getRecursive(1)
getRecursive(0)
done with getRecursive(0) execution
done with getRecursive(1) execution
done with getRecursive(2) execution
done with getRecursive(3) execution
```

The next recursive function will demonstrate that:

```
function logRecursive(nr) {
  console.log("Started function:", nr);
  if (nr > 0) {
    logRecursive(nr - 1);
  } else {
      console.log("done with recursion");
  }
  console.log("Ended function:", nr);
}
logRecursive(3);
```

It will output:

```
Started function: 3
Started function: 2
Started function: 1
Started function: 0
done with recursion
Ended function: 0
Ended function: 1
Ended function: 2
Ended function: 3
```

## Practice exercise 6.6

A common problem we can solve with **recursion*** is calculating the factorial.

Quick mathematics refresher about factorials:

  - The factorial of a number is the product of all positive integers bigger than 0, up to the number itself. So for example, the factorial of seven is 7 * 6 * 5 * 4 * 3 * 2 * 1. You can write this as 7!.

How are recursive functions going to help us calculate the factorial? 
  - We are going to call the function with a lower number until we reach 0. In this exercise, we will use recursion to calculate the factorial result of a numeric value set as the argument of a function.

  1. Create a function that contains a condition within it checking if the argument value is ```0```.
  2. If the parameter is equal to ```0```, it should return the value of ```1```. 
  3. Otherwise, it should return the value of the argument multiplied by the value returned from the function itself, subtracting one from the value of the argument that is provided. This will result in running the block of code until the value reaches ```0```.
  4. Invoke the function, providing an argument of whatever number you want to find the factorial of. The code should run whatever number is passed initially into the function, decreasing all the way to ```0``` and outputting the results of the calculation to the console. 
  5. It could also contain a ```console.log()``` call to print the current value of the argument in the function as it gets invoked.
  6. Change and update the number to see how it affects the results.

# Nested functions

Just as with loops, ```if``` statements, and actually all other building blocks, we can have functions inside functions. This phenomenon is called **nested functions***:

```
function doOuterFunctionStuff(nr) {
  console.log("Outer function");
  doInnerFunctionStuff(nr);
  function doInnerFunctionStuff(x) {
    console.log(x + 7);
    console.log("I can access outer variables:", nr);
  }
}
doOuterFunctionStuff(2);
```
This will output:

```
Outer function
9
I can access outer variables: 2
```
As you can see, the outer function is calling its nested function. This nested function has access to the variables of the parent. 

## Practice exercise 6.7

Create a countdown loop starting at a dynamic value of ```10```.

  1. Set the start variable at a value of 10, which will be used as the starting value for the loop.
  2. Create a function that takes one argument, which is the countdown value.
  3. Within the function, output the current value of the countdown into the console.
  4. Add a condition to check if the value is less than 1; if it is, then return the function.
  5. Add a condition to check if the value of the countdown is not less than 1, then continue to loop by calling the function within itself.
  6. Make sure you add a decrement operator on the countdown so the preceding condition eventually will be true to end the loop. Every time it loops, the value will decrease until it reaches ```0```.
  7. Update and create a second countdown using a condition ```if``` the value is greater than ```0```. If it is, decrease the value of the countdown by ```1```.
  8. Use ```return``` to return the function, which then invokes it again and again until the condition is no longer true.
  9. Make sure, when you send the new countdown value as an argument into the function, that there is a way out of the loop by using the ```return``` keyword and a condition to continue the loop if met.

# Anonymous functions

So far, we have been naming our functions. We can also create functions without names if we store them inside variables. We call these functions **anonymous**. Here is a non-anonymous function:

```
function doingStuffAnonymously() {
  console.log("Not so secret though.");
}
```
Here is how to turn the previous function into an anonymous function:

```
function () {
  console.log("Not so secret though.");
};
```
As you can see, our function has no name. It is anonymous. So you may wonder how you can invoke this function. Well actually, you can't like this!

  - We will have to store it in a variable to call the anonymous function; we can store it like this:

```
let functionVariable = function () {
  console.log("Not so secret though.");
};
```
An anonymous function can be called using the variable name, like this:

```
functionVariable();
```
It will simply output 
```
 Not so secret though..
```

## Practice exercise 6.8

  1. Set a variable name and assign a function to it. 
  2. Create a function expression with one parameter that outputs a provided argument to the console.
  3. Pass an argument into the function.
  4. Create the same function as a normal function declaration.
