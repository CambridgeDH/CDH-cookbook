<link rel="stylesheet" href="../../cookbook.css">
# Lesson 5: A Deeper Look at Functions and Introduction to Object Oriented Programming

<p class="previous-next-lesson"><a href="toc.html">^ Main contents</a></p>
## Contents
- [Overview](#overview)
- [The Wide World of Function Types](#the-wide-world-of-function-types)
- [Introduction to Object-Oriented Programming (OOP)](#introduction-to-object-oriented-programming-oop)
- [Conclusion](#conclusion)

## Overview
In the previous Milestone lesson, you learned how to write a small program in Python that loops through some files and modifies them. This program involved writing three different functions, and creating variables that you called within those functions. These are the most basic kinds of functions that one can write in Python, and so now it is appropriate to study more kinds of functions. You will also be introduced to the concept of 'Object Oriented Programming' - which is the structure behind the organisation of Python code. Understanding it will enable you to read and use other people's code more effectively and to understand common error messages you may receive.

[Back to table of contents](#contents)

## The Wide World of Function Types
Understanding what the various function types are will help you both to write your own functions more effectively and to use the functions others have written.

### User Defined Functions (UDFs)
In the Milestone lesson you learned to write what we call a 'User Defined Function' (UDF). You can remember this by the fact that we have 'def' before the function name (short for 'define'). Let's review the 'anatomy' of such a function in the following example:

```python
def write_content():
    with os.scandir(targetdirectory) as currentfiles:
        for file in currentfiles: 
            if file.name.endswith('.txt'):
                with open(file.path, 'r+') as currentfile:
                    currentfile.write('We are putting this sentence in our files')
write_content()
```
1. 'def' indicates a new function is being defined.
2. 'write_content():' is the name of the function. The curved brackets are there to contain 'input parameters' for the function. These input parameters are essentially specifications, for example like the type of food we may want to cook: 'bread' or 'cake'. For the function in the above example we did not need any specific instructions, hence the empty brackets.
3. Below the first line, we have an **indented** block of code. The colon on the first line demands indentation, which tells Python that everything under that line is part of that function and nothing else. The indented lines form the 'body' of the function. They are like the cooking instructions for our recipe.
4. At the bottom, we have 'write_content()' again. Since we have no input parameters (no special ingredients), we do not include anything in the brackets here.


Next let's look at a function that does have input parameters:

``` python
def greet(name, known=False):
  if known:
      print(f'Hello, {name}! We have met before.')
  else:
      print(f'Hello, {name}, I\'m Sophie. Nice to meet you!')
greet('Maria', True)
```
Here we define a new function, 'greet'. It has specific input parameters: name (this means when you call the function, you have to give a name), and known=False (this means that if you know the person you are greeting, you need to put 'True' in the brackets when you call the function). 

Now try calling the function in a new Jupyter Notebook. Call it with 'greet(name)' and then with 'greet(name, True)'. See what happens? 

Now try removing 'True'. What does the output look like now?

Note the 'f' before the phrase in the print statements. This is called an 'f-string'. It allows us to insert a variable name into our greeting. Try running the function without the 'f'. What happens then?

Notice the \ in I'm. This is because we are using single quotes around the entire string. This backslash (\) is an escape character sign and tells the computer to ignore the apostrophe which comes after it. Remove it before running the function and see what happens.

UDFs are ubiquitous in Python: you will be writing them for the rest of your coding career. 

### Built-In Functions
The version of the Python language that is installed on your computer comes with a variety of 'built-in' functions. They are always available to you for use, regardless of whether you have a specific module installed. Python's documentation has a list of all of them, [here](https://docs.python.org/3/library/functions.html). Have a look at different ones. 

 Built-in functions exist because they are very commonly needed and used in nearly every code situation. For example, we can put them in our UDF above. Let's say we wanted to know how many letters is in someone's name when we greet them, and tell them this fact. Here's how we would add it to our greet() function:

``` python
def greet(name, known=False):
  length = len(name)
  if known:
      print(f'Hello, {name}! Did you know your name has {length} letters?')
  else:
      print(f'Hello, {name}, I\'m Sophie. Did you know your name has {length} letters?')
greet('Maria')
```
Here we added in the len() function. Look at the documentation to see how it describes what len() does. It is always good to get in the habit of reading code documentation.

It is important to distinguish 'module functions' from 'built-in' functions. In our looping program, we used code like os.getcwd(). These are functions that exist as part of a module (which, you may remember from Lesson 1, is a set of code that someone else built for us to use). Your UDFs can become 'module functions' if you were to build a module and publish it. In that sense, as the specific user-defined functions that are 'built-in' to the module, they form a unique part of it. If you haven't installed or imported the module, you cannot access them. You can always access built-in functions, however.

A metaphor to help us understand this is the difference between baking bread, and baking a specific kind of bread. To 'cook' in a general sense typically involves preparing ingredients, heating a cooking apparatus, manipulating ingredients while they cook, etc. These kinds of actions are like the built-in functions in Python. When you have Python installed on your machine, you can always access them; it is like having a fully stocked kitchen ready to cook food. But to make flatbread is a more specific task: you would need to heat a specific apparatus depending on the type (a flat oven or stone), and you would need to prepare the flour in a certain way, etc. These are like our more specialised user-defined functions, as they belong to a specific recipe. If you don't know the recipe, you can't use them; similarly if you don't have a module with a specific UDF, you cannot use that UDF.

### Anonymous Functions
When writing longer programs, not every action is crucial enough that you need to formally 'define' a function for it. Python has a way of creating a function without giving it a name; we call these 'anonymous' functions. They are also known as 'lambda' functions, derived from a similar concept in lambda calculus. 
These functions are special in that they are **short**, containing only a single action ('expression'), and are meant to accomplish something quickly without the hassle of writing a large block of code. Here is an example of a lambda/anonymous function in our greet code:

```python
def greet(name, known=False):
    clean = lambda n: n.strip().title()
    if known:
        print(f"Hello, {clean(name)}!")
    else:
        print(f"Hello, {clean(name)}, I'm Sophie.")
greet('  maria')
```
Here we have a lambda function that cleans up a name input to ensure there are no spaces and that the name is capitalised. 'lambda' tells Python that this is anonymous.  After it, we give the parameter, 'n'. We could call it anything, like 'name'. The colon separates our parameter from the action. While we called our anonymous function 'clean', we aren't defining it as a major entity that is stored in Python's memory. It's just an additional sub-instruction inside the function 'greet'. Try running this code - what happens?

It essentially is an action done on the fly to ensure we have the output just as we want it. Instead of writing separately defined (def) functions to strip out whitespace or check if letters are capital or not, we simply threw in an anonymous function quickly. If we are going to exhaust the cooking/baking metaphor, a lambda/anonymous function is like that part of a recipe where it is assumed you will know how to do something, like 'roll the dough extra finely before buttering it'. 

 To summarise, these three kinds of functions are those which you will most commonly see and use when writing code in Python. It is a good idea to check your modules and check the built-in function list before trying to write code, as the task you might be trying to do may already have functions written for it.

[Back to table of contents](#contents)

## Introduction to Object-Oriented Programming (OOP)
Now we will turn our focus to the concept of 'Object-Oriented Programming' (abbreviated ubiquitously as 'OOP'). This section is more theoretical than the previous sections of this course, and it may seem disconnected at first from your ultimate goals, but understanding these concepts early on, even in a basic way, will carry you far and give you a stronger foundation upon which to build your skills. 

OOP is essentially the term describing a fundamental operational characteristic of Python. It underlies how code is structured in all of the modules you will encounter, and the terminology around OOP is found in nearly every error message you might get. Knowing a bit about it will help you find what you need in other people's code and will help you understand what Python is trying to tell you when your code does not run. We will discuss the four basics of OOP today: objects, attributes, methods, and classes.

You should first understand that 'Classes' are the 'blueprints' that organise Python code into actionable chunks, but we will describe them in detail last. 

### Objects 
Everything that you deal with in Python is an 'object'. To quote Python's documentation directly, 'objects are Python’s abstraction for data. All data in a Python program is represented by objects or by relations between objects' (link [here](https://docs.python.org/3/reference/datamodel.html) - I suggest you read this page after completing this lesson!). You can ask Python if something is an object, and if so, what kind of object it is:

```python
name = 'Maria'
print(type(name))
```
We get '<class 'str'> back. This output means that 'Maria' is an object belonging to the Class 'str'. This Class organises code around strings, which are literally characters in a row. The variable 'name' that we created contains an 'object' that is in the form of a string, 'M' 'a' 'r' 'i' 'a'. This object we created is the embodiment of the Class (or blueprint for) 'str' in our code. We call these embodiments 'instances' of a Class. The Class defines the structure of some data and some actions, and when we use a Class, the result is an object, such as 'name' here.

**For a quick rule of thumb: anything we create in Python is an 'object' or 'instance' implementing a Class.**
Perhaps a new metaphor will help. A 'Coffee Mug' Class can be thought of like a blueprint for making a coffee mug. The Class describes all the elements and functions of a coffee mug, such as the handle, the cup, the decoration, the ceramic, etc. Objects are the actual coffee mugs that you produce from the blueprints. Each individual mug in your cupboard is an 'instance' of the blueprint (Class) for making a coffee mug.

### Attributes
Objects do not exist in isolation. They also have attributes: these are specific pieces of data associated with the object. We can think of these as 'characteristics' describing the different elements that make up the object, like data. Take for example, the module 'math'. You may think that a module called 'math' would have a lot of pieces of specific data associated with it, and you would be correct. In fact, 'math' has a specific piece of data, pi:

```python
import math
print(math.pi)
```
The bit, '.pi' is an **attribute** of the object 'math'. 

Let's see another example. The module 'datetime' performs actions around dates and times. 

```python
import datetime

today = datetime.date.today()
print(today.year)
print(today.month)
print(today.day)
```

The elements .year, .month, .day, are 'attributes' of datetime. They hold data pertinent to the object at hand. In keeping with our metaphor, these are like the specific shapes or colours or types of ceramic the Class blueprint has for a specific mug.

### Methods
Objects have data attributes. But code exists to perform tasks, and so objects also have attributes that do things. These are called 'methods'. 
An example of a method that can be performed on a 'str' object is .lower(). This method turns any upper-case letter into a lower-case letter. Let's get this to happen for us:

```python
def greet(name):
    print(f'Hello, {name.lower()}!')
greet('John')
```
We passed the parameter 'name' into the function 'greet'. It is an object, which happens in this case to be a string, 'John'. We then 'called' a method on this object, .lower(), which performed the action of lowering the 'J' to 'j'. Notice that this is slightly different from our anonymous/lambda function above. We inserted a custom instruction into our 'greet' function in order to ensure the greeting came out in a specific way. Here, .lower is a method that is built directly for handling 'str' (string) objects in Python rather than a custom instruction that we came up with for our unique situation. 

It is a bit tricky to distinguish an attribute that is data from one that is a method because we also access methods using this 'dot notation' (with the '.' and then the name of the attribute). Let's distinguish the two:

```python
import datetime
maria_birthday = datetime.date(1990, 1, 1)

print(maria_birthday.year)
print(maria_birthday.strftime("%B"))

```
In the above code, we have done the following:
1. We imported a module called 'datetime'. You are encouraged to go look up what this module does in Python's documentation.
2. We defined a variable (which, if you remember, is also an object), which we called 'maria_birthday'. The info we attached to it was 1990/1/1, but note we separated the elements in the code specifically with commas, as this is standard Python format.
3. Now we have the first print statement. This asks the computer to print a data attribute about maria_birthday, specifically the year. The output is 1990.
4. Now we have the second print statement. It's a bit more complex. The 'strftime' bit is a method attribute (known as 'string format time') which tells Python to format a time string in a certain way. As an input, we have "%B". This is an argument (specific to the strftime method) that we placed within the method that tells Python to spell out the month (you'd have to look this up in the documentation if you wanted to know other arguments for this method).

In other words, a data attribute returns a specific piece of data stored in a variable/object. A method attribute performs an action on a specific piece of data stored in a variable/object.

So we have seen that objects (which is virtually everything we use in Python) have methods which can be performed with them, and data associated with them. Let's turn back to Classes now to understand them a little bit better.

### Classes
As we established above, **Classes** are the blueprints that define what specific methods and attributes an object should have. Knowing what classes look like, and what they do, will help you tremendously in reading code and using code that other people have written.

```python
class Greeting:
    def greet(self):
        print(f'Hello, {self.name}!')

g = Greeting()
g.name = 'Maria'     
print(g.name)        
g.greet()           
```
This looks a bit complicated at the start, so we will deconstruct it bit by bit:

<ol>
<li>The class name is Greeting, and like a function, it has the same colon and indentation rules. Class names are always capitalised in code. For single words like 'Greet', it's just the first letter. If we had two words, like GreetFriend, it would be the first letter of each word with no space. This format is called PascalCase.</li>
<li>Under the class name goes the method(s). Note that these look (and operate) much like functions. Ours only has one method, which is to print a greeting. </li>
<li>'g = Greeting()'. When you write this, you are telling Python to make an object that follows the instructions of 'Greeting'. We store that object in a variable, which we've termed 'g' here. What we name it does not matter. </li>
</ol>

Now look again at 'def greet(self):'. The method has this parameter called 'self' specified in the brackets, much like we may specify data for a function. This word 'self' is Python's way of making a connection between the method and the object, which we called 'g'. 'self' ties in the Greeting object 'g' with the method 'greet'. 

Remember above where we established that objects can have data attributes? 'g.name' creates a data attribute containing the name 'Maria'. Where you see {self.name}, this retrieves the data attribute from the object, 'g' that we set in g.name= 'Maria' and ensures 'Maria' is printed automatically when we run the code. 

Remember again that objects can have method attributes. Here our method attribute 'g.greet()' attaches the action 'greet' (which prints a phrase) to the object. 

To summarise, we have a Class that's all about printing greetings. From it we created an object, 'g'. When we call 'g' in our code, we use this Class, which contains instructions that 'g' follows. That way, we can store the name Maria as data, an attribute, for 'g'. We can perform the action of printing a phrase as a method attribute for 'g'. 

#### OOP Usefulness
At this stage, simply knowing that the OOP organisation exists and a little bit about how it operates is sufficient. When you read code documentation on a module and see that it has various Classes, you can then see what different things the module does, and how to make use of them. You can even choose to import only a class from a module, like in the module textblob (which you discovered in earlier lessons):

```python
from textblob import Word
```
This line of code will import the Class 'Word' from the textblob module. Word is a Class that contains many methods around analysing words in texts.

Finally, Python bug reports often deal with the levels of Python structure. A common error, if you call the wrong attribute for an object, is 'this object has no attribute X'. Knowing some of this vocabulary and the way Python is put together will help you interpret such error messages.

[Back to table of contents](#contents)

## Conclusion
This lesson is probably the most theoretical of this course, and beginners often find these details to be challenging to grasp at first. The best way to acclimate yourself is to read code documentation.

Your homework in this case is to:

1. Search online for the Textblob Python module. You are already familiar with part of it from previous lessons. Read through the quick start guide to refresh your memory. Next, go to [this page](https://textblob.readthedocs.io/en/dev/api_reference.html), which describes the different classes in the textblob module. Read the documentation for the class 'Word'. This will help you get a feel for how Classes appear in documentation in some more accessible language.
2. Take our Class that we made above, and change the .name attribute to a list of students. Instruct the class to only print the greeting if the name specified in your code is present in the list. If the name is not present, instruct the class to print a phrase indicating 'this person is not present'.
3. In the Greeting class example above, the greet() method prints out the name as it was given. Imagine a scenario where you are using this method to print out greetings for your list of students, but the person who made the list did not capitalise all of the names and added odd spaces here and there. Write a simple lambda function that ensures the names get printed correctly.

[Back to table of contents](#contents)

<p class="credits">Written by Estara Arrant, 2025-04-16<br />Licence: <a href="https://creativecommons.org/licenses/by-sa/4.0/">CC BY-SA 4.0</a></p>

<p class="previous-next-lesson"><a href="lesson4-milestone-lesson.html">&lt; Previous lesson</a> | <a href="lesson6-further-loops-and-conditionals.html">Next lesson &gt;</a></p>
