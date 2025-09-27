# Lesson 5: Further Loops and Conditionals
## Contents

## Overview
In previous lessons we covered the basic 'for loop' and used it to build some simple iterative functions and modify some files. However, 'for loops' are just scratching the surface of Python's capabilities. In this lesson we are going to look at two other loop types. We will also introduce the concept of 'conditional statements', which enable your code to respond to different potential situations. Finally, we will take a deeper look at 'arguments', which are the variables you give to functions to help them run. 

## The 'For Loop' Review
Before we get deep into different kinds of loops in Python, let's pause for a moment and review a simple for loop:

```python
patients = ['Alice', 'Ramji', 'Jonathan']

for patient in patients:
    print('Hello', patient)
```
As should be familiar by now, 'patients' is our list of names. The loop identifies this list, and for each element ('patient') in the list, it prints a greeting. Note that we could call this anything, say, 'for unicorn in patients...print ("hello", unicorn)'. The word 'patient' (or unicorn) in this code is a placeholder for the elements in the list.

**The for loop operates by this logic: for each thing in a category, do x** We do not need to tell the loop to stop running; when it has reached the end of the items in the category, it stops. It is the simplest loop in Python.

## The 'While Loop'
The next kind of loop that we encounter in Python is called the 'while' loop. It is slightly more complex than the for loop. It is meant to run the code *while* some condition is true, and to stop running when that condition changes. The basic abstract anatomy of a while loop is:

```python
while condition holds:
    perform task
```
Now obviously we cannot run this code. 'Condition holds' and 'task' have not been defined. However, it is clear how the loop operates. It is important to note that if the condition we state does not have an end point, the loop will run **forever** (or until your computer dies). Let's look at a real 'while loop' in action:

```python
animals = ['jaguar', 'wolf', 'unicorn']
while animals:
    animal = animals.pop(0)
    print('Next animal is:', animal)
```
First, we have a list of animals. The line 'while animals:' looks odd to humans, because it is not a complete statement. We can read this as 'while the list animals has something in it:'. Python operates by the truth value of statements. So, 'While animals = TRUE (the list has something in it), do X.' If 'animals' = FALSE, then nothing is in the list to analyse, and the code would not run.

The second line has what is known as a built-in list method, .pop(). To get you in the habit of reading Python documentation, read up on this built in function [here](https://docs.python.org/3/tutorial/datastructures.html).

Essentially, .pop() works with the data structure 'list'. That is why it is specifically called a 'list method'. It removes an item from the list. Our print function then tells Python to print what was removed from the list. And because this is a loop, it does this again and again until nothing is left in the list. This is like putting your hand in a bag, and then taking one present out at a time to show the recipient. Once the bag is empty, the loop finishes. 
Now you may wonder why '0' is a parameter in .pop. Take a moment to think about how Python counts things. We discussed this in the first lesson.

[hide answer] We put a 0 in .pop because Python is 0-indexed. It will remove the 0th element in the list each time the loop runs.

### While Loop Breaks
Consider this scenario: you have a long list of animals, but you only want to list them until you hit 'wolf'. Fortunately, Python has a method for interrupting a while loop: the loop break. It will cause the loop to terminate at a specified point, and the program to run any code that appears after. Let's see an example:

```python
animals = ['shark', 'panda', 'kingfisher', 'wolf', 'jaguar', 'unicorn', 'eagle']

while animals:
    animal = animals.pop(0)
    print('Next animal is:', animal)
    if animal == 'wolf':   
        break

print('I found all the animals up to and including the wolf')
```
The new line here is 'if animal == 'wolf':'. This line tells Python that if the animal encountered is the string 'wolf', then it should 'break' and stop running the loop. **!Notice** the == sign? Since we use '=' to assign variables, we use '==' to say 'equals' instead. So, if animal equals 'wolf', break the loop.

Notice also that the code keeps running after the loop is broken. It just terminates the loop process and goes to the next line of code, which is our print next print function.

### While Loop Continue
Python also has the capacity to break a loop at a specific location, and then keep going for the rest of the locations This can be very helpful for excluding specific elements from data analysis. In keeping with our trivial example, let's say we really want to leave out 'wolf' from our printing. We use a 'continue' statement:

```python
animals = ['shark', 'panda', 'kingfisher', 'wolf', 'jaguar', 'unicorn', 'eagle']

while animals:
    animal = animals.pop(0)
    if animal == "wolf":
        continue   
    print("Next animal is:", animal)
```
The code here is straightforward: the loop is taking the 0th element out of the list. The print statement then prints that element. But when the 0th element is 'wolf', the code is instructed to take it out (this is animals.pop(0)), and then 'continue' skips the rest of the loop body (the print statement). Therefore, 'wolf' doesn't get printed, and it is removed from the list like every other element that gets processed. The loop then keeps running with the rest of the elements.

### While Loop Else
One last element you can add in a while loop is an 'else' clause. Many people find this concept tricky, because they read 'else' like an 'if' statement.  the loop, but Python does not treat it like this. Look at the following example:

```python
index = 0
while index < len(university_library):
    book = university_library[index]
    if present(book):
        process(book)
        break
    index += 1
else:
    print('No book found.')
```
The 'else' is not an exception to the loop - it only runs if the loop completes. In our example above, if the desired book is found, there is a break in the loop and it terminates. If the desired book is not located, then the 'else' statement applies, and the output is our sentence, 'no book found'. 

Things like 'else' and 'break' are very useful for navigating large or multiple datasets and performing analyses on only parts of those datasets. You may also have heard of infinite loops - either the ones that are created by accident when the programmer forgets to put in a terminal point to their loop, or one that is designed to run indefinitely. Beginning programmers do not usually need to write infinite loops on purpose; what is important for you to remember now is that your while loop:
<li>Will either end when it runs out of objects, depending on the task</li>
<li>If it needs a condition to run, and that condition never ends, the loop will never end.</li>
Here is an example of a loop that is missing a necessary condition:

```python
count = 0
while count < 5:
    print("Count is:", count)
```
The condition upon which the loop operates is that if the count variable is less than 5, print a statement. The problem is, the count variable here is never updated to anything other than 0, which is less than 5. Therefore, if you were to run this code, it would run forever or until you quit your notebook. To fix it, we would add:

```python
count = 0
while count < 5:
    print("Count is:", count)
    count += 1
```
The last line here increases the count by one each time the loop is run. After 5 times, the loop will terminate.


## Nested Loops
The last kind of loop we will cover in this course is the 'nested loop'. These are exactly as the name suggests: loops within loops. They are very handy for multifaceted tasks. Let's look at an example:

```python
plays = ['Macbeth', 'Hamlet', 'Othello', 'King Lear']
authors = ['Shakespeare']

for play in plays:
    for author in authors:
        print(f'This is the play: {play}, and this is its author: {author}')
```
In this loop we have two different variables, 'plays' and 'authors'. We want to join them somehow. A nested loop structure is ideal for this. The first line, 'for play in plays', tells Python to look at the list of plays and for each element in it, print it. But it also adds in a layer, that it much attach the author to each printing of a play. These two loops work together to print a list of Shakespeare plays and attribute authorship to him. 

You can even have multifaceted data for this:

```python
horses = [
    ('Arabian', 'stable'),
    ('Clydesdale', 'pasture'),
    ('Thoroughbred', 'roundpen')
]
locations = [
    {'breed': 'stable', 'size': 'small'},
    {'breed': 'pasture', 'size': 'large'},
    {'breed': 'roundpen', 'size': 'medium'},
]

for horse, horse_location in horses:
    for location in locations:
        if location['breed'] == horse_location:
            print(f"The {horse} is in the {location['size']} {location['breed']}")
```
**In the outer loop:**
Here we have a list of tuples - elements that store multiple bits of information in a single variable: ('Arabian', 'stable'). Notice these are in curved brackets, thus we have a list of them. This loop goes through each horse and its location.

**In the inner loop:**
We have a list [] of dictionaries (remember that a dictionary is a {key:value pair}. {'Breed': 'Stable', 'size': 'small'} is thus a dictionary. The inner loop goes through each dictionary. 

**The If Statement**
This checks if the 'breed' value in the dictionary matches the horse_location from the tuple. If there is a match, we go to the next code element.

**The Print statement**
This function prints the elements that have been identified and matched above. 

## Conditionals
You have probably noticed from the code above that Python uses terminology which only holds true under certain circumstances. In fact, there are a number of statements in Python that direct your code to decide on a specific action based on whether a condition is true or false. These are known as 'conditionals'. They fall under the category of 'control structures', which are statements that control how a program flows from one command to another. Loops are control structures, and so are conditionals. When we need to write code that does more than just execute commands in order, but to pay attention to specific **conditions** and act accordingly, we can use conditionals to achieve this.

### The Biggest Conditional: 'If'
You have already seen a lot of 'if' statements in this course. Let's review some of what we know about them:

<li>Lines with if statements need to end in a colon.</li>
<li>If statements tell Python to check if something is True. If so, the block of code is run. If not, the code is not run **within that indentation segment**.</li>
<li>If statements require indentation after them, so that anything that appears after falls within their remit.</li>
<li>If statements can stand alone, or they can be aided by further conditionals (which we are about to learn)</li>

### Else and Elif

#### Else
Let's say we have a situation which we want Python to evaluate. However, rather than simply not running code if the situation is false, we want Python to do an **alternative** action. We can use this syntax:

```python
if <situation>:
    <do task>
else:
    <do other task>
# The < > are placeholders; not actual code
```
If the situation is true, then the else part of the code is not run, and vice versa. Here is a concrete example:

```python
refrigerator = ['ice cream', 'soda', 'salad']
shopping_list = []

ingredients = ['pizza', 'chilli peppers', 'garlic']

if all(item in refrigerator for item in ingredients):
    print('Yay! We can make dinner!')
else:
    shopping_list.extend(ingredients)

print(f"This is the shopping list: {', '.join(shopping_list)}")

```
Here we start with a list of foods and an empty list, 'shopping_list'. We also have a list of ingredients. Our loop is an 'if all' loop, which checks each element in the refrigerator list with each element in the ingredients list. If all = True (everything in 'ingredients' is also in refrigerator'), then the code runs a print statement.

If all ≠ true, then Python skips to the else statement. Here we have .extend. This list method takes a list, tuple, or string, and adds elements to it. We extend 'shopping_list' with the 'ingredients' list.

Now notice our second to last print statement. First we have an f-string, which we have already learned about. Next we have {', '.join(shopping_list)}. The brackets are part of the f-string, and inside Python evaluates the expression and inserts the results right in that location.  The .join(shopping_list) then takes each individual element in the shopping_list and makes one long string. We have ', ' to tell Python to separate each item in this string with a comma.

You can see the versatility of this tool; it can be used in many similarly creative ways.

#### Elif
Let's now look at elif. We use elif (else...if) when we have more than one alternative. For our shopping list, let's add the contingency that the store is out of one of the ingredients on our new shopping list:

```python
refrigerator = ['ice cream', 'soda', 'salad']
shopping_list = []

ingredients = ['pizza', 'chilli peppers', 'garlic']

store = ['pizza', 'garlic']  # what the store has today

# Build the shopping list (everything we need but don’t already have)
for item in ingredients:
    if item not in refrigerator:
        shopping_list.append(item)

print(f"This is the shopping list: {', '.join(shopping_list)}")

# Now check each shopping list item at the store
for item in shopping_list:
    if item in store:
        print(f'Tick off {item}')
    elif item not in store:
        print(f'We cannot buy {item} today')

```
As you can see, elif is pretty straightforward. You can have as many elif branches as necessary; there is no limit.

## Arguments














Task 1: The first example in the While Loop Else section is pretty straightforward: it searches an index of books and if it finds a match (we have not written the code to specify the desired match), it processes the book to the reader. But there are some new code elements. Search online and find out exactly what they do. 


