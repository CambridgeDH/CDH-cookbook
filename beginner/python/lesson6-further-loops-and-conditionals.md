<link rel="stylesheet" href="../../cookbook.css">
# Lesson 6: Further Loops and Conditionals

<p class="previous-next-lesson"><a href="toc.html">^ Main contents</a></p>
## Contents

- [Overview](#overview)
- [The For Loop Review](#the-for-loop--review)
- [The While Loop](#the-while-loop)
- [Nested Loops](#nested-loops)
- [Conditionals](#conditionals)
- [Arguments](#arguments)
- [Conclusion](#conclusion)

## Overview
In previous lessons we covered the basic **for loop** and used it to build some simple iterative functions and modify some files. However, for loops just scratch the surface of Python's capabilities. In this lesson we are going to look at two other loop types. We will also introduce the concept of **conditional statements**, which enable your code to respond to different potential situations. Finally, we will take a deeper look at **arguments**, which are the variables you give to functions to instruct them to run with certain specifications. 

[Back to table of contents](#contents)

## The For Loop Review
Before we get deep into different kinds of loops in Python, let's pause for a moment and review a simple for loop:

```python
patients = ['Alice', 'Ramji', 'Jonathan']

for patient in patients:
    print('Hello', patient)
```
As should be familiar by now, 'patients' is our list of names. The loop identifies this list, and for each element ('patient') in the list, it prints a greeting. Note that we could call this anything, say, 'for unicorn in patients...print ("hello", unicorn)'. The word 'patient' (or unicorn) in this code is a placeholder for the elements in the list. In other words, the template is: 'for each element in the list of elements, print it'. 

**Therefore, the for loop operates by this logic: for each thing in a category, do x** We do not need to tell the loop to stop running; when it has reached the end of the items in the category, it stops. It is the simplest loop in Python.

[Back to table of contents](#contents)

## The While Loop
The next kind of loop that we encounter in Python is called the 'while' loop. It is slightly more complex than the for loop. It is meant to run the code *while* some condition is true, and to stop running when that condition changes. The basic anatomy of a while loop is:

```python
while condition holds:
    perform task
```
Now obviously we cannot run this code. 'Condition holds' and 'task' have not been defined. However this is the essential structure of the while loop. It is important to note that if the condition we state does not have an end point, the loop will run **forever** (or until your computer dies). Let's look at a real 'while loop':

```python
animals = ['jaguar', 'wolf', 'unicorn']
while animals:
    animal = animals.pop(0)
    print('Next animal is:', animal)
```
Let's break this down bit-by-bit:
In the first line we have a list of animals, as denoted by the square brackets. Remember each element in the list must have quote marks and be separated by commas after the quote marks. The line 'while animals:' looks odd to a reader because it is not a complete statement. It translates to: 'while the list called animals has something in it:'...and then the rest of the code will finish that statement.

As an aside, it is important to understand that Python operates by the truth value of statements. So, 'while animals = TRUE (meaning, the list we called 'animals' has something in it), do specified thing.' In the line of code, 'while animals:', the 'true' is implied and the computer runs the program. If the list 'animals' had nothing in it, the computer would interpret the situation as 'while animals = FALSE' and the code would not run. 

The second line has what we call a built-in list method, .pop(). To solidify the habit of reading Python documentation, look at the specs on this built in function [here](https://docs.python.org/3/tutorial/datastructures.html) **before** reading the explanation below.

Essentially, .pop() works with the data structure 'list'. That is why it is specifically called a 'list method'. It removes an item from the list in order to do something with it. Then, our print function tells Python to print the item that was removed from the list. And because this is a loop, it does this again and again until nothing is left in the list. This is like putting your hand in a bag of gifts, and then taking one gift at a time out to show to the recipient. Once the bag is empty, you stop. Once the program removes the last element of the list, the program stops.

<details>
<summary>Now you may wonder why '0' is a parameter in .pop. Take a moment to think about how Python counts things. We discussed this in the first lesson.
</summary>
 We put a 0 in .pop because Python is 0-indexed. It will remove the 0th element in the list each time the loop runs.
</details>

### While Loop Breaks
Consider this scenario: you have a long list of animals, but you only want to list them until you hit a particular animal midway through the list. Fortunately, Python has a method for interrupting a while loop: the loop break. It will cause the loop to terminate at a specified point in the list. Let's see an example:

```python
animals = ['shark', 'panda', 'kingfisher', 'wolf', 'jaguar', 'unicorn', 'eagle']

while animals:
    animal = animals.pop(0)
    print('Next animal is:', animal)
    if animal == 'wolf':   
        break

print('I found all the animals up to and including the wolf')
```
The new line here is 'if animal == 'wolf':'. This line tells Python that if the animal encountered is the string 'wolf', then it should 'break' and stop running the loop. **Notice** the == sign! In Python, since we use '=' to assign variables, we use '==' to say 'equals' instead. So, if 'animal' equals 'wolf', break the loop.

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
The code here is straightforward: the loop is taking the 0th element out of the list. The print statement then prints that element. But when the 0th element is 'wolf', the code is instructed to first take it out like it does for every other element (this is what animals.pop(0) does), and then 'continue' tells it to throw that element away, and then keep running as usual for the rest. Therefore, 'wolf' doesn't get printed, but every other element will be printed.

### While Loop Else
One final element you can add in a while loop is an 'else' clause. Look at the following example:

```python
university_library = ['Book A', 'Book B', 'Book C']

def on_shelf(book):
    return book == 'Book B'
    
def check_out(book):
    print(f"Checking out: {book}")
    
index = 0
while index < len(university_library):
    book = university_library[index]
    if on_shelf(book):
        check_out(book)
        break
    index += 1
else:
    print('Book not found.')
```
Let's decode this bit-by-bit again.
First we have our list, which we named 'university_library', and this list contains three books. The first function, 'on_shelf', checks if a book, as we typed it, is in 'university_library'. The next function, 'check_out', is a print statement that runs if the book is found in 'on_shelf'.

Next we have our 'if' part of the loop. If the book is on the shelf, run the 'check_out' function. Then we break the loop -- we only want to check out one particular book on the shelf, not every book!. The line ' index += 1' tells the computer to search the entire list. 

Then we have the 'else' statement. In our example above, say we want to see if Book A is present and if so, check it out. If it's in our list, the loop terminates and according to the 'check-out' function we wrote, prints: 'Checking out: Book A'.  If our desired book is not located, then the 'else' statement applies, and the output is our sentence, 'Book not found'. 

Things like 'else' and 'break' are very useful for navigating large or multiple datasets and performing analyses on only parts of those datasets. You may also have heard of infinite loops - either the ones that are created by accident when the programmer forgets to put in a terminal point to their loop, or one that is designed to run indefinitely. Beginner programmers do not usually need to write infinite loops on purpose; what is important for you to remember now is that your while loop:

<ul>
<li>Will either end when it runs out of objects, depending on the task</li>
<li>If it needs a condition to run, and that condition never ends, the loop will never end.</li>
</ul>

Here is an example of a loop that is missing a necessary condition:

```python
count = 0
while count < 5:
    print("Count is:", count)
```
The condition upon which the loop operates is: if the count variable is less than 5, print a statement. The problem is that the count variable here is never updated to anything other than 0, which is less than 5. Therefore, if you were to run this code, it would run forever or until you quit your notebook. Try running it and see what happens!

To stop it running forever, we add:

```python
count = 0
while count < 5:
    print("Count is:", count)
    count += 1
```
The last line here increases the count by one each time the loop is run. After 5 times, the loop will terminate.

[Back to table of contents](#contents)

## Nested Loops
The last kind of loop we will cover in this course is the 'nested loop'. These are exactly as the name suggests: loops within loops. They are very handy for multifaceted tasks. Let's look at an example:

```python
plays = ['Macbeth', 'Hamlet', 'Othello', 'King Lear']
authors = ['Shakespeare']

for play in plays:
    for author in authors:
        print(f'This is the play: {play}, and this is its author: {author}')
```
In this loop we have two different variables, 'plays' and 'authors'. We want to join them somehow, and a nested loop structure is ideal for this. The first line, 'for play in plays', tells Python to look at the list of plays and for each element in it, print that element. But we have also added in a layer instructing it to attach each author element printed from that list, to a play in the other list. These two loops work together to print a list of Shakespeare plays and attribute authorship to him. 

You can also have multifaceted data in nested loops:

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
At the start of the code, for the variable 'horses',  we have a list (notice the square brackets: [ ]) of tuples - elements that store multiple bits of information in a single variable inside curved brackets: ('Arabian', 'stable').  In the loop code, "for horse, horse_location in horses:" the program reads through each tuple, which contains two pieces of data: a horse and its location. Note that we don't need to specify 'horse' or 'horse_location' as their own variables; the computer reads the first element in the tuple as a 'horse' and the second element as a 'horse_location'.

**In the inner loop:**
The next piece of relevant data is the 'locations' variable, which is a list [] of dictionaries. Remember that a dictionary in Python is a {key:value pair} enclosed in curly brackets. In this list we have three dictionaries. The inner loop, which is the code "for location in locations:" reads through each dictionary. 

**The If Statement**
This line of code checks if the 'breed' value in the dictionary matches the second element in the tuple. If there is a match, we go to the next code element.

**The Print statement**
This function prints the elements that have been identified and matched above. 

[Back to table of contents](#contents)

## Conditionals
You have probably noticed from the code above that Python uses terminology which is only true under certain circumstances. We discussed this briefly above in the 'while' loop. In fact, there are a number of statements in Python that direct your code to decide on a specific action based on whether a condition is true or false. These are known as **conditionals**. They fall under the category of **control structures**, which are statements that control how a program flows from one command to another. Loops are control structures, and so are conditionals. When we need to write code that does more than just execute commands in order, but to pay attention to specific conditions and act accordingly, we can use conditionals to achieve this.

### The Biggest Conditional: 'If'
You have already seen a lot of 'if' statements in this course. Let's review some of what we know about them:

<ul>
<li>Lines with if statements need to end in a colon.</li>
<li>If statements tell Python to check if something is True. If so, the block of code is run. If not, the code is not run within that indentation segment.</li>
<li>If statements require indentation after them; anything that appears after the statement within that indentatiob block falls within their remit.</li>
<li>If statements can stand alone, or they can be aided by further conditionals (which we are about to learn)</li>
</ul>

### Else and Elif

#### Else
Let's say we have a situation that we want Python to evaluate. However, rather than having the program terminate if situation is false, we want Python instead to do an **alternative** action. We can use this syntax:

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
Here we start with a list of foods, 'refrigerator', and an empty list, 'shopping_list'. We also have a list of 'ingredients'. Our loop is an 'if all' loop, which checks each element in the refrigerator list against each element in the ingredients list. If all = True (everything in 'ingredients' is also in 'refrigerator'), then the code runs a print statement.

If all ≠ true, then Python skips to the else statement. Here we have .extend. This list method takes a list, tuple, or string, and adds elements to it. We extend 'shopping_list' with the 'ingredients' list. 

Now notice our second to last print statement. First we have an f-string, which we have already learned about, to print a specific statement. Next we have {', '.join(shopping_list)}. The brackets are part of the f-string, and inside Python evaluates the expression and inserts the results right in that location.  The .join(shopping_list) then takes each individual element in the shopping_list and makes one long string. We have ', ' to tell Python to separate each item in this string with a comma.

The program essentially checks two different lists, sees if something is on one list but not the other, and then writes the full list. This is the code equivalent of checking your pantry and then writing what's missing for a recipy on your shopping list before you go to the store.

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

[Back to table of contents](#contents)

## Arguments
One last concept we will explore in this lesson is that of 'arguments'. You have already been dealing with arguments since we discussed  the concept of a function. Remember 'parameters' -- these are the placeholder variables listed inside the curved brackets at the start of a function. Arguments are the exact instances of those variables that get acted upon when we call the code. There are different kinds of arguments, and it helps to know them:

### Positional arguments: these need to be passed into the function in a specific order:

```python
names = ['Alice', 'Bob', 'Charlie']
occupations = ['Engineer', 'Doctor', 'Teacher']

def name_occupation(name, occupation):
    print(f'{name} works as a {occupation}.')

for name, occupation in zip(names, occupations):
    name_occupation(name, occupation)

# name_occupation(names[0], occupations[0])

```
In this code we have two lists, 'names' and 'occupations'. The function 'name_occpuation' uses the elements of those lists as positional arguments. First the name, then the occupation is printed. The for loop pairs the lists together element by element specifically, so that you can just run the function once. 

The commented out line of code at the end would be the code you would run to print out Alice's name and occpuation, in that order. 

### Keyword arguments

These are like positional arguments, except that the order does not matter. To see it with the 'names' and 'occupations' list above, we will run the following code:

``` python
name_occupation(occupation='Engineer', name='Alice')
name_occupation(name='Bob', occupation='Doctor')

```
Note that this is not positional because we are overtly specifying, with the = sign, the label to go with 'occupation' and 'name'. We have reversed the order (in the curved brackets, we put occupation first, and name second), but the function still prints what we want.

### Default arguments

Default arguments are instructions written into the function to give a predetermined response if, when calling the function later, you do not specify anything in the curved brackets. In the code below, the default is 'friend':

```python
def greet(name='friend'):
    print('Hello,', name)

greet()        
greet('Jean Luc')
```
We see that in the first calling of the function, 'greet()', the computer outputs 'Hello, friend'. In the second calling, we put in a specific name as an argument, and so the computer ignored the default and used the name instead, 'Hello, Jean Luc'. 

### `*args`

This setting allows a function to accept any number of positional arguments. Python takes these arguments and collects them into a tuple. For an example, run the two functions below just as they are, one at a time in different cells:

```python
# Without *args:
def add(x, y, z):
    return x + y + z
add()
```
```python
# With *args:
def add(*args):
    return sum(args)
add()
```

What can you learn from the error message for the first function? It is expecting exactly 'x, y, z' when you call the function at the end. But since nothing is in the curved brackets, we get an error message.

But the second function expects whatever you throw at it (or don't throw at it). In this case, we gave it nothing, and it returned 0. That's not an error - that's the correct output! 

### *kwargs

This kind of argument collects keyword arguments and stores them in dictionaries:

```python
def print_info(**kwargs):
    print(kwargs)

print_info(name="Alice", age=30, job="Engineer")
```
This is useful because you can type in anything as keywords and have them printed.


[Back to table of contents](#contents)

## Conclusion
In this lesson you have learned more of the variety of Python's syntax, and we covered different ways in which we can get Python to look at our data. It's best to think of these loops and conditionals as tools that you can pick as needed to accomplish a task: if you just want to analyse each element in a dataset only once, you can use a for loop. If you want to skip elements, you can use a break, etc. This is by no means all of the features that Python syntax can offer you, but these are the fundamentals.

Your homework for this lesson involves becoming further acquainted with these tools and becoming more skilled at finding out information about your code:

<ul>
<li>Task 1:</li> The first example in the 'While Loop Else' section is pretty straightforward: it searches an index of books and if it finds a match (we have not written the code to specify the desired match), it processes the book to the reader. But there are some code elements that were not overtly explained in this lesson. Search online and find out exactly what they do. 
<li>Task 2:</li> In the *args type of argument above, we did not pass any argument into 'add()'. It gave 0 because of this. Try now giving this function an exact argument. Create some variables and put them into add() on the last line. 
<li>Task 3:</li> Get creative and come up with a data scenario that would require you to use a combination of at least two types of loops and at least one conditional. See if you can write some code that will successfully run within these parameters.
</ul>

[Back to table of contents](#contents)

<p class="credits">Written by Estara Arrant, 2025-04-16<br />Licence: <a href="https://creativecommons.org/licenses/by-sa/4.0/">CC BY-SA 4.0</a></p>

<p class="previous-next-lesson"><a href="lesson5-functions-and-object-oriented-programming.html">&lt; Previous lesson</a> | <a href="lesson7-file-handling-essentials.html">Next lesson &gt;</a></p>

