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

{::options parse_block_html="false" /}

{::options parse_block_html="true" /}

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