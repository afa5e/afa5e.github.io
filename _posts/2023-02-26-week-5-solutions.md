---
layout: post
title: Week 5 Solutions
categories: 23T1 23T1-Solutions
date:   2023-02-26 11:00:00 +1100
expires: 2023-04-09 23:59:59 +1100
---

* TOC 
{:toc}

## Task 1 - Unique Values
```python
unique_list = list(set(sample1))
print(unique_list)
```

```python
unique = []
for item in sample1:
    if item not in unique:
        unique.append(item)

print(len(unique))
```

## Task 2 - Common values
```python
common = []
for item in sample1:
    if item in sample2:
        common.append(item)

print(common)
```

## Task 3 - Palindromes
```python
is_palindrome = sample2 == sample3[::-1]
print(is_palindrome)
```

## Task 4 - Merge and Sort
```python
sorted = []
for item2, item3 in zip(sample2, sample3):
    if item2 >= item3:
        sorted.append(item3)
        sorted.append(item2)
    else:
        sorted.append(item2)
        sorted.append(item3)

print(sorted)
```

## Task 5 - Smallest
```python
    sample1.sort()
    print(sample1[n])
```

## Task 6 - Most frequent
```python
import collections

most_common = collections.Counter(sample1).most_common(1)[0][0]
print(most_common)
```

## Task 7 - Sum
```python
i = 0
sum = 0

while i <= len(sample1):
    sum += sample1[i]

print(sum)
```

## Task 8 - Product
```python
i = 0
product = 0

while i <= len(sample1):
    product *= sample1[i]

print(product)
```

## Task 9 - Smallest and largest
```python
sample1.sort()
print(sample1[0], sample1[-1])
```

## Task 10 - Array multiply
```python
output = []

while i < len(sample2):
    output.append(sample2[i] * sample1[i])

i = len(sample2)

while i <= len(sample1):
    output.append(sample1[i])

```