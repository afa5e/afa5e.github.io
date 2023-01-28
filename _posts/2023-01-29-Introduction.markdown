---
layout: post
title:  "Introduction to Python at SRA"
date:   2023-01-28 16:38:41 +1100
categories: 23T1
---
Welcome to the Advanced Coding Class - Python at Sydney Robotics Academy. This 
term we will be covering a range of topics with Python:
  - I/O operations, including from the terminal and filesystem.
  - Different datatypes, such as double, float, integer, char, string, etc.
  - Different methods of storing multiple pieces of data, such as lists.
  - Making our code more readable with functions.
  - Making webpages with HTML, CSS and Javascript.

Firstly, before we can start coding, we need to install some programs. Some of 
these programs will tell our computer how to understand our code, and others 
will help us write our programs.

We will be installing all of these programs from our local website: 
<http://apps.sydneyrobotics.com.au>
1. Python 3.1x - This program will ensure that our computer can understand 
   our code. After the file has been downloaded, open the file and follow 
   the instructions.

2. Visual Studio Code. - This is a simple code editor which has some useful 
   features, including syntax highlighting. This means that our code will 
   change colours depending of what each word does, and if there are any errors.

Once these two programs have been installed, please open VSCode and you will 
see options to change the theme. You can choose any theme you want.

Now, before we write code, we first need to setup our workspace. You will need
a program called a terminal to run our code.

### Windows
In Windows, there are two different terminals, CMD and Powershell. You can also 
install Linux through WSL2 to access a bash/zsh shell. For this lesson, we will 
be using CMD.

To open CMD, you can right click the start button, or use the keybind `WIN-X` 
to open the same menu. Then, select the `command prompt` option.

> If you do not see the `command prompt` option in the list, and instead see
> `powershell`, search for `command prompt` in windows search.
>
> Alternatively, using the run command (`WIN-R`), search for `cmd.exe`.

### Mac OS
In Mac OS, there is only one terminal program, called Terminal. Search for this
program in the apps list and open.

## Using the Terminal

In the terminal, you should see some path to a folder. This is called the prompt
and tells you where you are in the file system. Here in the terminal, you can 
use commands to operate your computer. These commands include:

- `ls` - which lists out all files and folders in the current directory. In 
  windows, this is the `dir` command.
- `mkdir directoryName` - which makes a directory called `directoryName`.
- `cd directoryName` - changes to `directoryName`.
- `cd ..` - moves up one directory.
- `pwd` - shows the full location you are at, windows: `cd`.

Before we create any files, we should first change to our desktop folder and
create a new folder for this term. You folder name must not contain any special 
characters or spaces. If you are continuing from last term, or the holiday you 
can move the folder from that previous class into this new folder under a name 
such as `22T4` or `RoverRun`. 

<details>
    <summary>Hint:</summary>
    <br>
    <ol>
        <li><code>ls</code> or <code>cd</code> to print the contents of the 
        current directory.</li>
        <li>Then, <code>cd</code> into the Desktop folder.</li>
        <li>Now, make a new folder with <code>mkdir</code> with an appropriate 
        name.</li>
        <li>Finally, <code>cd</code> into the newly created folder.</li>
    </ol>
</details>
<br />

Finally, we need to check which command we use to run our python files. To do 
this, try these commands:

- Windows: `py --version`
- Mac OS: `python --version`

If the command returns a version number starting with 2, you will need to use 
these commands:

- Windows: `py -3 --version`
- Mac OS: `python3 --version`

Now, during the term, when you are running your code, you will need to remember 
which command prefix to use.

## Using VSCode

![VSCode](/img/vscode.png)

Now that you have finished setting up VSCode and the terminal, we first need to 
open the folder that we made previously. On the left, open the file/folder menu 
and `select a folder`. Then, you can use the keyboard shortcut `CTRL/CMD-N` to 
create a new file, then we can save the new file with `CTRL/CMD-S`, naming it 
with the `.py` extension. This tells your computer thatthe file is a python 
file, allowing VSCode to apply syntax highlighting.

You can use the keyboard shortcut `CTRL/CMD+~` to open a terminal from within 
VSCode.

## Coding in Python

### Variables
In python, we can store information in objects called variables. In other 
languages you might need to declare the type of data the variable will store, 
in Python you do not need to do this, and can just stane the name of the variable.

```python
# integers
a = 1
b = -10

# floating-point numbers
c = 3.14
d = -0.01

# strings
e = "hello"
f = "123"

# lists
g = [1, 2, 3]
h = [4, 5, 6]
```

### Operators
Now that we can store data, Python allows us to manipulate variables with operators:

#### Arithmetic
```python
# Addition
x + y

# Subtraction
x - y

# Multiplication
x * y

# Division
x / y

# Modulo - remainder after dividing x by y
x % y

#Exponentiation - x to the power of y
x ** y

# Floor division - divide and round down
x // y
```

#### Assignment
We can use these operators to assign values to variables. Not only can we 
directly assign a value, we can also apply an operation to the value at the 
same time.

```python
# Assignment
x = 5

# Increment - same as x = x + 5
x += 5

# Decrement - same as x = x - 5
x -= 5

# Multiply - same as x = x * 5
x *= 5

# Divide - same as x = x / 5
x /= 5

# Modulo - same as x = x % 5
x %= 5

# Floor divide - same as x = x // 5
x //= 5

# Exponentiation - same as x = x ** 5
x **= 5
```

#### Comparison
We can compare a variable or value against another.

```python
# Equal
x == y

# Not equal
x != y

# Greater than
x > y

# Less than
x < y

# Greater than or equal to
x >= y

# Less than or equal to
x <= y
```

#### Logical
Logical operators allow us to combine multiple boolean statements.

```python
x == 1 and y >= 2

x == 1 or y >= 2

x == 1 not y >= 2
```

### Control Flow
Instead of running every line of code in our file, we can use control statements 
to choose which lines to run, and repeat if necessary. All of these require you 
to indent the code within the control statement. This is unlike most other 
languages which uses curly braces to demark them.

```python
# If condition is true, then run 
if condition:
    runThis()
    andThis()

# If-elif-else
if condition1:
    runThis()
    andThis()
elif condition2:
    runThis()
    andThis()
else:
    runThis()
    andThis()

# Match allows us to check the value of a single variable against multiple 
# options
match command:
    case "Hello, World!":
        print("Hello to you too!")
    case "Goodbye, World!":
        print("See you later")
    case other:
        print("No match found")

# Looping while a condition is True
while condition:
    repeatThis()
```

### Commands
In Python, there are many built in commands, such as `print()` which prints 
everything in the parentheses to the terminal.
```python
# Printing to the terminal. The print() function can take zero, one or two 
# arguments.
# No arguments prints an empty line
print()

# One argument prints the value of the variable or the string in the quotes.
print(variable)
print("Hello")

# A second argument allows you to set the terminating characters, by default
# a newline is added after every print, but with end = "" you can set it to 
# any character(s) you want.
print("hello", end = "")

```

Python can request input from the terminal in your program via the `input()`
command. You will need to assign a variable to the `input()` function to store 
the input from the user. The input will always be stored as a string.
```python
variable = input()
```

Python can convert between strings and integers/decimals with the `str()`, 
`int()` and `float()` functions.
```python
# Converts the user input to an integer
variable = int(input())

# Generally, we need to check if the input is valid, but here we can safely 
# assume the strigns are safe to convert. The int() function will crop 
# decimals off the number, to avoid this use the float() function.
variable = float(input())

# We can convert back to a string with the str() function.
str(1)
```

We can also split a string between characters to form a list with 
`string.split(separator, maxsplit)` where the separator is what separates 
each item in the list. This separator will be removed by this operation.
Maxsplit will set how many split operations to apply, i.e. you will have
`maxsplit + 1` items in the output given enough separators in the input.

```python
# ['hello', 'my name is Peter', 'I am 26 years old']
txt = "hello, my name is Peter, I am 26 years old"

x = txt.split(", ")

# ['apple', 'banana#cherry#orange']
txt = "apple#banana#cherry#orange"

x = txt.split("#", 1)
```

Python can also measure how long a string is with the `len()` function.
```python
# 4
len("abcd")
```

### String slicing
In Python, we can treat a string as a list of characters, allowing us to 
choose any subset of the characters with string slicing.

Using square brackets after a variable containing a string, we can use 
list indicies to choos the start and end of a substring.

We can also specify a single number to choose a single character.

```python
x = "helloworld"

# "hello"
x[0:5]
x[:5]

# "world"
x[5:]

# "low"
x[3:6]

# "h"
x[0]
```
### Running our code
To run our code in the terminal, we first need to check that we are in the folder 
that contains our python file. To do this, `ls` (`dir` if windows) to check the 
contents of the current folder. If you do not see your python file, `cd` into the 
correct folder. Then, run the Python file with the `py` or `python` command 
followed by the name of the file.

Example: `py helloworld.py`

## Tasks
This week's tasks are for you to get used to writing code in python and using 
tools such as VSCode and the terminal. The tasks start simple and gradually 
get more difficult. You do not need to finish all of the tasks, but they will 
be available for you to access at home if you like.

1. Write a program that prints "Hello, World!" to the console.
2. Write a program that takes two numbers as input from the user and prints 
   the sum of the numbers to the console.
3. Create a python program that can act as a simple calculator 
   (add, subtract, multiply and divide).
4. Write a program that calculates the factorial of a number entered by the user.
5. Write a program that takes a list of numbers as input and finds the largest 
   number in the list and print it out.
6. Write a program that takes a list of integers as input and returns the 
   second largest number in the list.
7. Ask the user for a number and check if it is prime or not.
8. Write a program that takes a number as input and returns the next prime 
   number greater than the given number.
9.  Write a program that takes a number as input and returns the sum of the 
    digits of that number.
10. Write a program that takes a number as input and returns True if the 
    number is a palindrome (i.e. it reads the same forwards and backwards), 
    False otherwise.
11. Write a program that takes a number as input and returns the number of 1s 
    in its binary representation.
12. Write a program that takes a number as input and returns True if the number 
    is a perfect square, False otherwise.
13. Write a program that takes a number as input and returns the next palindrome 
    number greater than the given number.
14. Write a program that takes a number as input and returns the number of ways 
    to represent it as a sum of positive integers.
15. Create a program that takes a string as input and returns the length of the 
    longest valid parenthesis substring.
