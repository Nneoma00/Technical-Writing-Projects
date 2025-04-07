# How to Build a Basic Calculator with Python
This document shows my process for building a basic calculator that enables the user to work with two digits in Python.
## Prerequisites
To follow along, you need to have Python installed on your computer. If you're new to programming or don't code in Python, VS Code might be a better fit as it supports multiple languages. Here's how to use [Python in VS Code](https://code.visualstudio.com/docs/python/python-tutorial).

## Project Details
The calculator project involves implementing a Python program that:
- accepts input from a user
- calculates the input
- outputs the result as a whole number(integer)
- outputs a decimal (float) if division does not result in a whole number

## The Process
### 1. Define a function and initial variable
Most developers can build a basic calculator program without defining functions. However, I prioritized code reusability over simplicity on this project.
I defined a function `bCalc()` and initialized a variable `expression` to the user's input string. Below is an example:

```
def bCalc():
      expression = input("Enter an arithmetic expression: ")
```

### 2. Split the input string and initialize its components.
Assume the user will input a string of 3 characters, including 2 numbers and one operator. We cannot perform arithmetic operations with strings. Therefore, convert the relevant substrings to integers and initialize the operator. In this case, `x` represents the first integer from the string, `y` represents the symbol/operation, while `z` is the second integer in the expression.
See code snippet below:
  ```
    x, operator, z = expression.split()

    x = int(x)
    y = operator
    z = int(z)
```

### 3. Create a list of operators/mathematical symbols
Because this calculator is basic, it will only perform addition, subtraction, multiplication and division operations. The list of operators is assigned to the variable `ops` like so:
```
     ops = ["+", "-", "*", "/"] 
```
     
### 4. Use conditional statements to validate input and output corresponding result
Having split the user's input strings into substrings, the `if-else` statements determine if they've input a valid operator (as declared in the `ops` list). If that condition is met, the rest of the equation executes.
```
    if y in ops and y == "+" :
        result = x + z
        print(result)
```
```
    elif y in ops and y == "-" :
        result = x - z
        print(result)
```
```
    elif y in ops and y == "*" :
        result = x * z
        print(result)
```
**_Example_**
> Enter an arithmetic expression: 1 + 5  
> #Output is 6

If the variable `y` i.e., the user's operator, is represented in the list of valid operators and `y` is +, the calculator adds the integers `x` and `z`. This logic applies to all other operations represented above.

### 5. Customize the division operation to return an `int` if the result is a whole number or a `float` if the result has a remainder
[Dividing integers `(/)` in Python](https://lucydot.github.io/python_novice/03-types-conversion/index.html) automatically results in a float value, unless the developer customizes the code to return an integer. This can be achieved through _floor division_, represented by the double-slash `(//)` operator.

At this point, I introduce 2 new elements: the double slash and the modulo operator `(%)`. In a nested `elif ` statement, I ask the computer to run a floor division, returning a whole number if `x % z == 0` and  output a float (rounded to 2 decimal places) if the division results in a remainder. 
```
    elif y in ops and y == "/":
        if x % z == 0:
            result = x // z
            print(result)
        else:
            result = round(x / z, 2)
            print(result)

```

### 6. Reject any invalid input and call the function at the end
The final else statement sends an error message to the user if their input does not meet any of the preset conditions. 
```
    else:
        print("INVALID INPUT")
bCalc()
```

Indentation is mandatory in Python. Use correct and consistent indentation to ensure your code works [^1].



