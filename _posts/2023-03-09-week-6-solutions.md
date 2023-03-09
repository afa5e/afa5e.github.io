---
layout: post
title: Week 6 Solutions
categories: 23T1 23T1-Solutions
date:   2023-03-05 11:00:00 +1100
expires: 2023-04-09 23:59:59 +1100
---

* TOC 
{:toc}

## For loops
### Task 1 - 1 to 20
We will be using the `range()` function in the for loop to iterate through the numbers.

```python
for i in range(0, 21):
    print(i)
```

### Task 2 - Even numbers
We could use an `if` statement inside our for loop from [task 1](#task-1---1-to-20), or use the step parameter in `range()` to count up in twos.
```python
for i in range(0, 21):
    if i % 2 == 0:
        print(i)
```

```python
for i in range(0, 21, 2):
    print(i)
```

### Task 3 - Sum
We can create a variable to store our cumulative sum and use a for loop.
```python
sum = 0
for i in range(0, 101):
    sum += i

print(sum)
```

### Task 4 - Reverse a string.
We will use the `range()` function to iterate from the length of the string down to 0 by setting the step parameter to -1 and the start to the length of the string.
```python
string = "hello world"
reversed = ""

for i in range(len(string) -1, -1, -1):
    reversed += string[i]

print(reversed)
```

### Task 5 - Pascal's triangle
For this extension task, we will not be using $$N \choose R$$ to generate each row, instead we will use memoization to store each row in a 2D array and add each pair together to make the next row. Then, we will use the `join()` function to format the triangle correctly.

```python
num_rows = 20
triangle = [[1]]
for i in range(1, num_rows):
    row = [1]
    for j in range(1, i):
        row.append(triangle[i-1][j-1] + triangle[i-1][j])
    row.append(1)
    triangle.append(row)

for row in triangle:
    print(" ".join(str(num) for num in row).center(120))
```

## While loops
### Task 1 - Random number quiz
```python
import random

# Generate a random number between 1 and 100
random_number = random.randint(1, 100)

# Start a loop to keep prompting the user for guesses until they guess the correct number
while True:
    # Ask the user to enter a guess
    user_guess = int(input("Guess the number between 1 and 100: "))

    # Check if the user's guess is correct
    if user_guess == random_number:
        print("Congratulations! You guessed the correct number.")
        break  # Exit the loop since the user has guessed correctly

    # Check if the user's guess is too high
    elif user_guess > random_number:
        print("Too high. Guess again.")

    # If the user's guess is neither correct nor too high, it must be too low
    else:
        print("Too low. Guess again.")
```

### Task 2 - Average
```python
# Initialize a sum variable and a count variable
total = 0
count = 0

# Start a loop to prompt the user for numbers
while True:
    # Ask the user to enter a number
    number = int(input("Enter a number (enter a negative number to stop): "))

    # Check if the number is negative
    if number < 0:
        break  # Exit the loop since the user has entered a negative number

    # If the number is not negative, add it to the sum and increment the count
    total += number
    count += 1

# Calculate the average, but only if the user entered at least one non-negative number
if count > 0:
    average = total / count
    print("The average of the numbers you entered is:", average)
else:
    print("You did not enter any non-negative numbers.")
```