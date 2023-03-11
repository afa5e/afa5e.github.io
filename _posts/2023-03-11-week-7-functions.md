---
layout: post
title: Week 6 - Loops
date: 2023-03-11 23:59 +1100
categories: 23T1
expires: 2023-09-09 23:59:59 +1100
---

* TOC
{:toc}

## Functions

In Python, a function is a block of reusable code that performs a specific task. Functions are used to avoid repeating code, simplify complex code, and modularize programs. This means that anytime we want to reuse code in our program, we can define a function and call it anytime we want.

### Syntax:
```python
def functionName(parameter1, parameter2):
    # function implementation

    return value
```

We use the `def` keyword to tell python that we want to make a function, then followed by the name of the function. Then in brackets, we can list out the variable names for any parameters that we need. Finally, we end the line with a colon, and indent the entire contents of the function.

Inside the function we can add any code we need, but variables outside the function, or outside the scope, are not accessible from the inside. Similarly, any variable that we make or change inside the function will not be reflected outside. To pass information in or out of functions we need to use parameters and `return`s.


### Parameters
After the function name we can specify the variables that we need to pass into the function. These variables are called parameters and must be used when calling the function. We can have any number of parameters. But, if we do not know if a parameter is needed or not, we can use the optional parameter flag `*`. This will require the extra parameters to be wrapped in a tuple.

```python
def myFunction(letter1, letter2, *letter3):
    output = letter1 + letter2 + letter3

    return output

print(myFunction('a', 'b'))
```

### Import statements
Sometimes we need to use functions that other people have written. Instead of copying the code, we can import functions with the `import moduleName` line at the very beginning of the file. If you tried the extension tasks from last week, you may have imported  the `random` module. 

### Return statement
As variables inside the scope/function are not reflected outside, we need to pass information back out. To do this, we use the `return` keyword, followed by the variable or value that we are returning.

```python
def functionName():
    return 0
```

## Testing
Python `unittest` is a built-in unit testing framework in Python. It is used to test individual units or components of a software system. Unit testing is a method of software testing where individual units of code are tested in isolation to ensure that each unit is working as expected.

The `unittest` framework provides a set of tools for constructing and running tests, organizing test code into test cases and test suites, and reporting test results. It is also designed to support test automation, where tests can be run automatically as part of a continuous integration (CI) or continuous delivery (CD) pipeline.

### Importing
`Unittest` is a built in module in python, but is not automatically added to every python file. To import `unittest` we use: `import unittest` on line 1 of our file.

### Classes
The `unittest` module requires us to create classes to test individual function. A class is an object that has functions assigned to it. We will not be focusing on what a class is and how to use is in OOP design.

### Usage

After defining our function, we need to add the following test framework to the file.

```python
class className(unittest.testCase):
    def testName(self):
        self.assertEqual(functionName(param1, param2), output)
        self.assertEqual(functionName(param1, param2), output)
        self.assertEqual(functionName(param1, param2), output)
        self.assertEqual(functionName(param1, param2), output)

    def testName(self):
        self.assertEqual(functionName(param1, param2), output)
        self.assertEqual(functionName(param1, param2), output)
        self.assertEqual(functionName(param1, param2), output)
        self.assertEqual(functionName(param1, param2), output)

    def testName(self):
        self.assertEqual(functionName(param1, param2), output)
        self.assertEqual(functionName(param1, param2), output)
        self.assertEqual(functionName(param1, param2), output)
        self.assertEqual(functionName(param1, param2), output)

if __name__ == '__main__':
    unittest.main()
```

Example testing:

```python
import unittest

def addNum(a, b):
    return a + b

class testAddNum(unittest.TestCase):
    def testingPositive(self):
        self.assertEqual(addNum(0, 0), 0)
        self.assertEqual(addNum(1, 0), 1)
        self.assertEqual(addNum(0, 1), 1)
        self.assertEqual(addNum(1, 1), 2)
        
    def testingNegative(self):
        self.assertEqual(addNum(-1, -1), -2)
        self.assertEqual(addNum(-2, 0), -2)
        self.assertEqual(addNum(0, -10), -10)
        self.assertEqual(addNum(-10, -10), -20)

if __name__ == '__main__':
    unittest.main()
```

## Tasks:
For this week, not only will you need to implement the functions, but also write tests for them.
1. Implement a function that returns the difference between two integers.
2. Implement a function that returns the reverse of a string.
3. Implement the factorial math function.
4. Implement a function that generates the nth fibonacci number.
5. Implement a sorting algorithm.
6. Using the optional parameter flag, create a function that multiplies all the parameters together.
