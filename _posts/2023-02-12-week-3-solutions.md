---
layout: post
title: Week 3 Solutions
categories: 23T1 23T1-Solutions
date:   2023-02-12 11:00:00 +1100
expires: 2023-04-09 23:59:59 +1100
---

* TOC 
{:toc}

## Task 1 - Hello World

```python
print("hello world")
```

## Task 2 - Prefix
This task requires you to try out all three methods of printing out variables: comma separation, `.format()` and fstrings.

```python
text = input("--> ")
print("You typed:", text)
print("You typed: {0}".format(text))
print(f"You typed: {text}")
```

## Task 3 - Unicode
This task needs you to take a user input and convert it to a hex value via an integer. Then you can use the hex value to print out the corresponding character from Unicode.

```python
hex_value = input("Enter a hexadecimal value: ")
unicode_char = chr(int(hex_value, 16))
print("The Unicode character for hexadecimal value " + hex_value + " is " + unicode_char)
```

## Task 4 - Word Count
This task will require the use of the `.split()` function to split a sentence into individual words, then the `len()` function to get the length of the list.

```python
user_input = input("Enter a sentence: ")
word_list = user_input.split()
word_count = len(word_list)
print("The number of words in your sentence is:", word_count)
```

## Task 5 - Anagrams
This task has a few different solutions, the most efficient is to sort both strings into alphabetical order, then compare the strings. If they are equal, then the two words are anagrams. Another method is to iterate through both words and check each letter for matches.

```python
word1 = input("Enter the first word: ")
word2 = input("Enter the second word: ")

if sorted(word1) == sorted(word2):
    print("The words are anagrams.")
else:
    print("The words are not anagrams.")
```

## Task 6 - Fizzbuzz
This task also has many different solutions, and was a common technical interview question in the programming industry. A good video that covers some different methods is this: [https://www.youtube.com/watch?v=QPZ0pIK_wsc](https://www.youtube.com/watch?v=QPZ0pIK_wsc) by Tom Scott.

The solution uses a for loop, but a while loop with an iterator is also valid.

```python
for i in range(1, 101):
    output = ''
    if i % 3 == 0:
        output += 'Fizz'
    if i % 5 == 0:
        output += 'Buzz'
    print(output or i)
```

## Task 7 - Extension Caesar cipher
This task requires the use of for loops and iterating through a list, something that will be covered in a later week. Your code will be iterating though a string, and offsetting the letters by converting it to the ASCII decimal and adding the offset value. The decryption subtracts the offset instead of adding.

```python
message = input('Enter a message: ')
offset = int(input('Enter an offset: '))

encrypted_message = ''
for char in message:
    if char.isalpha():
        shift = ord(char.upper()) + offset
        if shift > ord('Z'):
            shift -= 26
        encrypted_message += chr(shift) if char.islower() else chr(shift).upper()
    else:
        encrypted_message += char

print(f'Encrypted message: {encrypted_message}')

decrypted_message = ''
for char in encrypted_message:
    if char.isalpha():
        shift = ord(char.upper()) - offset
        if shift < ord('A'):
            shift += 26
        decrypted_message += chr(shift) if char.islower() else chr(shift).upper()
    else:
        decrypted_message += char

print(f'Decrypted message: {decrypted_message}')
```

## Task 8 - Extension RPN
This task requires lists to create a stack, a method of storing data in memory. We then can remove the top two values, with `pop()` and apply to operation in RPN order.

```python
expression = input("Enter a reverse Polish notation expression: ")
tokens = expression.split()
stack = []

for i in range(len(tokens)):
    token = tokens[i]
    if token == "+":
        b = int(stack.pop())
        a = int(stack.pop())
        stack.append(a + b)
    elif token == "-":
        b = int(stack.pop())
        a = int(stack.pop())
        stack.append(a - b)
    elif token == "*":
        b = int(stack.pop())
        a = int(stack.pop())
        stack.append(a * b)
    elif token == "/":
        b = int(stack.pop())
        a = int(stack.pop())
        stack.append(int(a / b))
    else:
        stack.append(int(token))

result = stack[0]
print("Result:", result)
```