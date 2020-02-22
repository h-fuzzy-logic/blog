---
layout: post
title: Being Pythonic - List Comprehensions to Create Lists
summary: Using list comprehensions can increase performance and readability   
categories: [Python, Being Pythonic, List Comprehension]
mainimageurl: "/img/python-large.png"
mainimagealt: "Python logo"
mainimageattribution: "Image from Python Software Foundation"
---

<h1 class="h4">Background</h1>
Python lists are used to group other values such as integers and strings.  Often new lists need to be created from operations performed on existing lists.  List comprehensions in Python improve performance and readability over other approaches such as loops and maps.  The syntax for a list comprehension consists of three parts surrounded by brackets:
1. Desired output as an expression 
2. For clause
3. Zero or more if clauses

<h1 class="h4">Code Samples</h1>
The first several samples show different ways to create a list of booleans indicating if the numbers from 0 to 9 are even.  A simple function named ```is_even``` is defined first to show how operations can be performed when creating lists.  The last sample shows using a list comprehension with an if clause to get only the even numbers.  

```Python
 
def is_even(num):
    return num % 2 == 0 

# making the new list with a for loop
isEvenFromLoop = []
for x in range(10):
    isEvenFromLoop.append(is_even(x))
print (isEvenFromLoop)

Output: 
[True, False, True, False, True, False, True, False, True, False]


# making the new list with a map
isEvenFromMap = list(map(lambda  x: is_even(x), range(10)))
print (isEvenFromMap)

Output: 
[True, False, True, False, True, False, True, False, True, False]


# making the new list with a list comprehension 
isEvenFromListComprehension = [is_even(x) for x in range(10)]
print (isEvenFromListComprehension)

Output: 
[True, False, True, False, True, False, True, False, True, False]


# list comprehension with an if clause 
evensOnly = [x for x in range(10) if is_even(x)]
print (evensOnly)

Output: 
[0, 2, 4, 6, 8]
```

So the next time you need to create a new list, consider using a list comprehension if your first approach is wordy or slow.    




