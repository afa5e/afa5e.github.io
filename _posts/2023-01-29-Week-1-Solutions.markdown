---
layout: post
title:  "Week 1 Solutions"
date:   2023-01-29 9:30:42 +1100
categories: 23T1 23T1-Solutions
---

* TOC 
{:toc}

## Task 1 - Hello World

```python
print("Hello, World!")
```

## Task 2 - Sum of two numbers

You were asked to create a program that asks the user for two numbers, then add 
them together. The minimum needed to finish this task is:

{::options parse_block_html="true" /}

<details><summary markdown="span">Solution:</summary>
<hr style="height:10px; visibility:hidden;" />

```python
first = input()
second = input()

print(int(first) + int(second))
```

</details>
<hr style="height:10px; visibility:hidden;" />
{::options parse_block_html="false" /}

But, we can improve out code by changing a few lines, namely adding a prompt to 
inform the user of what is asked of them, and converting to float to preserve 
decimals.

{::options parse_block_html="true" /}
<details><summary markdown="span">Better:</summary>
<hr style="height:10px; visibility:hidden;" />

```python
print("First number: ", end = "")
first = input()

print("Second number: ", end = "")
second = input()

print(float(first) + float(second))
```

</details>
<br/>
{::options parse_block_html="false" /}

## Task 3 - Simple Calculator

This task introduces the use of control flow within your code, allowing you 
to selectively run some lines based on the user input. If the user selects 
add, we need to add the two inputs, same for subtract, multiply and divide. 
To do this, we could use an if-elif-else statement, but new to python 3.10 
is the match-case system, allowing us to compare the value of a single variable 
against multiple options. This allows the code to be more readable and self 
explanatory.

{::options parse_block_html="true" /}
<details><summary markdown="span">Ok:</summary>
<hr style="height:10px; visibility:hidden;" />

```python
print("First number: ", end = "")
first = float(input())

print("Operation: ", end = "")
op = input()

print("Second number: ", end = "")
second = float(input())

if op == "add":
    answer = first + second
elif op == "subtract":
    answer = first - second
elif op == "multiply":
    answer = first * second
elif op == "divide":
    answer = first / second
else:
    print("Invalid input")
    exit()

print(answer)
```

</details>
<br/>

<details><summary markdown="span">Better:</summary>
<hr style="height:10px; visibility:hidden;" />

```python
print("First number: ", end = "")
answer = float(input())

print("Operation: ", end = "")
op = input()

print("Second number: ", end = "")

match op:
    case "add":
        answer += float(input())
    case "subtract":
        answer -= float(input())
    case "multiply":
        answer *= float(input())
    case "divide":
        answer /= float(input())
    case _:
        print("Invalid input")
        exit()

print(answer)
```

</details>
<br/>
{::options parse_block_html="false" /}

## Task 4 - Factorial
This task introduces loops within our code to minimise us manually copying 
lines of code. Here, we are using a while loop to repeatedly multiply by a 
number to form the factorial.


{::options parse_block_html="true" /}
<details><summary markdown="span">Solution:</summary>
<hr style="height:10px; visibility:hidden;" />

```python
print("Number: ", end = "")
number = int(input())
factorial = 1

while number != 0:
    factorial *= number
    number -= 1

print(factorial)
```

</details>
<br/>
{::options parse_block_html="false" /}

## Task 5 - Largest number
As we have not covered using lists yet, we cannot sort a list of numbers to 
find the highest. Instead as the user inputs the numbers, your code will check 
if the latest input is greater than the current highest number.

{::options parse_block_html="true" /}
<details><summary markdown="span">Hint:</summary>
<hr style="height:10px; visibility:hidden;" />

You can ask the user for an input and with a while loop repeat your code that 
compares the input until it is blank.

```python
number = float(input())

while number:
    # check for the largest number

print(largest)
```

</details>
<br>

<details><summary markdown="span">Solution:</summary>
<hr style="height:10px; visibility:hidden;" />

We can store the current highest number in a variable (set to zero at the start), 
then if the latest input is greater, use update the variable to this new value.

```python
number = input()
biggest = 0

while number:
    if float(number) > biggest:
        biggest = float(number)

    number = input()

print(biggest)
```

</details>
<br/>
{::options parse_block_html="false" /}

## Task 6 - Second largest

This task is very similar to the previous task, but instead of the highest 
number, we want to store the second highest. To this, we can modify the code 
from task 5 and also store the second highest number. When the user submits a 
number that is higher than the current stored number, set the second highest 
to the highest and update the highest to the new number.

{::options parse_block_html="true" /}
<details><summary markdown="span">Solution:</summary>
<hr style="height:10px; visibility:hidden;" />

```python
number = input()
biggest = 0
secondBiggest = 0

while number:
    if float(number) > biggest:
        secondBiggest = biggest
        biggest = float(number)

    number = input()

print(secondBiggest)
```

</details>
<br/>
{::options parse_block_html="false" /}

## Task 7 - Is prime

This task combines loops, if-else conditionals and the modulo operation. We can 
check if a number is coprime with all integers from 2 to itself. To check for 
this, we will use the modulo operator to check if the remainder is zero or not.

{::options parse_block_html="true" /}
<details><summary markdown="span">Solution:</summary>
<hr style="height:10px; visibility:hidden;" />

```python
prime = int(input())
count = 2

while count != prime:
    if prime % (count) == 0:
        print("no")
        exit()
    else:
        count += 1

print("yes")
```

</details>
<br/>
{::options parse_block_html="false" /}

## Task 8 - Next prime

We have code from task 8 which can check if a number is prime or not, if we take 
the user input and check increasing numbers from it, we can return the next prime.

{::options parse_block_html="true" /}
<details><summary markdown="span">Solution:</summary>
<hr style="height:10px; visibility:hidden;" />

```python
prime = int(input()) + 1
isPrime = False

while not isPrime:
    count = 2
    isPrime = True

    while count != prime:
        if prime % (count) == 0:
            isPrime = False
            break
        else:
            count += 1
    
    if isPrime == False:
        prime += 1

print(prime)
```

</details>
<br/>
{::options parse_block_html="false" /}

## Task 9 - Digital sum

Here, we can use loops to iterate through a string. If we keep the user input 
as a string and select each character, either with string slicing and an iterator 
or a for loop, we can add each digit to a sum.

{::options parse_block_html="true" /}
<details><summary markdown="span">Solution using string slicing:</summary>
<hr style="height:10px; visibility:hidden;" />

```python
number = input()
total = 0
i = 0

while i != len(number):
    total += int(number[i])
    i += 1

print(total)
```

</details>
<br/>

<details><summary markdown="span">Solution with for loops:</summary>
<hr style="height:10px; visibility:hidden;" />

```python
number = input()
total = 0

for char in number:
    total += int(char)

print(total)
```

</details>
<br/>
{::options parse_block_html="false" /}

## Task 10 - Palindrome Checker

In this task, we can use string slicing to reverse a string. Recalling from 
week 1, the first index specifies the starting position and the second index 
the ending position. If we add a third number, also separated by a colon, we 
can choose which direction to slice against.

{::options parse_block_html="true" /}
<details><summary markdown="span">Solution:</summary>
<hr style="height:10px; visibility:hidden;" />

```python
number = input()

reverse = number[::-1]

if number == reverse:
    print("Yes")
else:
    print("No")
```

</details>
<br/>
{::options parse_block_html="false" /}

## Task 11 - Binary Ones

Here, we can break the task into two sections: convert a number to base 2 
and count the occurances of a character.

To convert to base 2, we need to subtract decreasing powers of 2 from the 
original. We first can find the highest power of two that is smaller than the 
number. To do this, we need to take the log base 2 of the decimal number. We 
will first need to import the math module into out program with `import math` 
at the beginning of our code. Then, we can use `math.log(decimal, 2)` function 
to get the exponent of 2. We can then round this down by abusing the `int()` 
function to remove the decimal section.

Then, we can repeatedly try to subtract the powers of two from the decimal until 
we run out of numbers. If this is applied correctly, you should not have a 
remainder after this.

Instead of counting the number of 1s inthe binary number, we can increment a 
counter when we are calculating the binary number.

{::options parse_block_html="true" /}
<details><summary markdown="span">Solution:</summary>
<hr style="height:10px; visibility:hidden;" />

```python
import math

decimal = int(input())
exponent = int(math.log(decimal, 2))
count = 0

while exponent >= 0:
    if (decimal - (2 ** exponent)) >= 0:
        decimal -= (2 ** exponent)
        count += 1

    exponent -= 1

print(count)
```

</details>
<br/>
{::options parse_block_html="false" /}