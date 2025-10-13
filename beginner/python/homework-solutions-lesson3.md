<link rel="stylesheet" href="../../cookbook.css">

# Homework Solutions: Lesson 3: The Mechanics of the Python Language
Here you will find sample solutions for each of the three difficulty levels of the homework for Lesson 3: The Mechanics of the Python Language.

## Easy Level
This task asks you to create a list of up to ten elements and then write a loop that prints them with a meaningful phrase.

```python
students = ["Sarah", "John", "Lina", "Rebecca", "Muhammad", "Jenna"]

for name in students:
    print("Welcome to the class", name)
```

## Medium Level
This task asks you to put two arguments into a printing function, for example, like so:

```python
def favorite_food(name, food):
    print(name, "loves", food)

favorite_food("Sarah", "pizza")
favorite_food("John", "sushi")
favorite_food("Lina", "pasta")
```

## Hard Level
Finally, this task asks you to exercise your searching skills to find some code that can identify the second item in a list. Here's the simplest way to do it:

```python
# Create a list
fruits = ["apple", "banana", "cherry", "kiwi", "elderberry"]

# Get the second item (remember Python starts counting from 0!)
print(fruits[1])
```
The explanation is that 'fruits[1]' is the input which we give the print statement. This tells Python to find the 'fruits'list, and then find the second item in that list. 

## Summary
These three examples are potential solutions to the homework prompts for lesson 3. There are potentially other ways to write code that will work for these, so be sure that if you found a different way, that you look at each component of the code you found to understand exactly what it does. 

<p class="credits">Written by Estara Arrant, 2025-04-16<br />Licence: <a href="https://creativecommons.org/licenses/by-sa/4.0/">CC BY-SA 4.0</a></p>
