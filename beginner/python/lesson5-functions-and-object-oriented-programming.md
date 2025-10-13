# Lesson 5: A Deeper Look at Functions and Introduction to Object Oriented Programming

## Contents


## Overview
In the previous Milestone lesson, you learned how to write a small program in Python to loop through some files and modify them. This program involved writing three different functions, and creating variables that you 'called' within those functions. These are the most basic kinds of functions that one can write in Python, and so now is appropriate to begin looking into the other kinds of functions that are possible in this language. You will also be introduced to the concept of 'Object Oriented Programming' - which is essentially the organisation of much of Python code. Understanding it will enable you to read and use other people's code more effectively and understand common error messages you may receive.

## The Wide World of Function Types
We will begin with function types. Knowing these will help you both to write your own functions and to use the functions others have written.

### User Defined Functions (UDFs)
In the Milestone lesson you learned to write what we call a 'User Defined Function' (UDF). You can remember this by the fact that we have 'def' before the function name. Let's review the 'anatomy' of such a function:

```python
def write_content():
    with os.scandir(targetdirectory) as currentfiles:
        for file in currentfiles: 
            if file.name.endswith('.txt'):
                with open(file.path, 'r+') as currentfile:
                    currentfile.write('We are putting this sentence in our files')
write_content()
```
<li> - 'def' indicates a new function is being defined.</li>
<li> - 'write_content():' is the name of the function. The curved brackets are there to contain 'input parameters' for the function, which are essentially specifications, like the type of food we may want to cook: 'bread' or 'cake'. For this function, we did not need any specific instructions, hence the empty brackets.</li>
<li> - Below the first line, we have an **indented** block of code. The colon on the first line demands indentation, which tells Python that everything under that line is part of that function and nothing else. The indented lines form the 'body' of the function. They are like the cooking instructions for our recipe.</li>
<li> - At the bottom, we have 'write_content()' again. Since we have no input parameters (no special ingredients), we do not include anything in the brackets here. </li>

Let's look at a function that does have input parameters:

``` python
def greet(name, known=False):
  if known:
      print(f'Hello, {name}! We have met before.')
  else:
  print(f'Hello, {name}, I'm Sophie. Nice to meet you!')
greet('Maria', True)
```
Here we define a new function, 'greet'. It has specific input parameters: name (this means when you call the function, you have to give a name), and known=False (this means that if you know the person you are greeting, you need to put 'True' in the brackets when you call the function). 
Try calling the function in a new Jupyter Notebook. Call it with 'greet(name)' and then with 'greet(name, True)'. See what happens? 

Now try removing 'True'. What does the output look like now?

Note the 'f' before the phrase in the print statements. This is called an 'f-string'. It allows us to insert a variable name into our greeting. Try running the function without the 'f'. What happens then?

UDFs are ubiquitous in Python: you will be writing them for the rest of your coding career. But there are other kinds of very useful functions that you should know about.

### Built-In Functions
The version of the Python language that is installed on your computer comes with a variety of 'built-in' functions. They are always available to you for use, regardless of whether you have a specific module installed. Python's documentation has a list of all of them, [here](https://docs.python.org/3/library/functions.html). Have a look at different ones. 

 Built-in functions exist because they are very commonly needed and used in nearly every code situation. For example, we can put them in our UDF above. Let's say we wanted to know how many letters is in someone's name when we greet them, and tell them this fact. Here's how we would add it to our greet() function:

``` python
def greet(name, known=False):
  length = len(name)
  if known:
      print(f'Hello, {name}! Did you know your name has {length} letters?')
  else:
  print(f'Hello, {name}, I'm Sophie. Did you know your name has {length} letters?')
greet('Maria')
```
Here we added in the len() function. Look at the documentation to see how it describes what len() does. It is always good to get in the habit of reading code documentation.

It is important to distinguish 'module functions' from 'built-in' functions. In our looping program, we used code like os.getcwd(). These are functions that exist as part of a module, which is a set of code that someone else built for us to use. Your UDFs can become 'module functions' if you were to build a module and publish it. In that sense, they are 'built-in' to the module, but not to Python itself. If you haven't installed or imported the module, you cannot access them. You can always access built-in functions, however.

### Anonymous Functions
When writing longer programs, not every action is crucial enough that you need to formally 'define' a function for it. Python has a way of creating a function without giving it a name; we call these 'anonymous' functions. They are also known as 'lambda' functions, derived from a similar concept in lambda calculus. 
These functions are special in that they are **short**, containing only a single action ('expression'), and are meant to accomplish something quickly without the hassle of writing a large block of code. Here is an example of a lambda/anonymous function in our greet code:

```python
def greet(name, known=False):
    format_name = lambda n: n.lower()
  if known:
      print(f'Hello, {format_name(name)}!')
  else:
  print(f'Hello, {format_name(name)}, I'm Sophie')
greet('Maria')
```
Here we have a lambda function that lowers the case of the name. 'lambda' tells Python that this is anonymous. After it, we give the parameter, 'n'. We could call it anything, like 'name'. The colon separates our parameter from the action. Notice that in the {name} statements we call 'format_name' and then in the brackets, put 'name'. Try running this code - what happens?

 To summarise, these three kinds of functions are those which you will most commonly see and use when writing code in Python. It is a good idea to check your modules and check the built-in function list before trying to write code, as the task you might be trying to do may already have functions written for it.

## Introduction to Object-Oriented Programming (OOP)
Now we will turn our focus to the concept of 'Object-Oriented Programming' (abbreviated ubiquitously as 'OOP'). This section is more theoretical than the previous sections of this course, and it may seem disconnected at first from your ultimate goals, but understanding these concepts early on, even in a basic way, will carry you far and give you a stronger foundation upon which to build your skills. 

OOP is essentially the term describing a fundamental operational characteristic of Python. It underlies how code is structured in all of the modules you will encounter, and the terminology around OOP is found in nearly every error message you might get. Knowing a bit about it will help you find what you need in other people's code and will help you understand what Python is trying to tell you when your code does not run. We will discuss the four basics of OOP today: objects, attributes, methods, and classes.

You should first understand that 'Classes' are the 'blueprints' or the 'recipes' that organise Python code into actionable chunks. 

### Objects 
Everything that you deal with in Python is an 'object'. To quote Python's documentation directly, 'objects are Python’s abstraction for data. All data in a Python program is represented by objects or by relations between objects' (link [here](https://docs.python.org/3/reference/datamodel.html) - I suggest you read this page after completing this lesson!). You can ask Python if something is an object, and if so, what kind of object it is:

```python
name = 'Maria'
print(type(name))
```
We get '<class 'str'> back. This output means that 'Maria' is an object belonging to the Class 'str'. This Class organises code around strings, which are literally characters in a row. The variable 'name' that we created contains an 'object' that is in the form of a string, 'M' 'a' 'r' 'i' 'a'. This object we created is the embodiment of the Class 'str' in in our code. We call these embodiments 'instances' of a Class. The Class defines the structure of some data and some actions, and when we use a Class, the result is an object, such as 'name' here.

**For a quick rule of thumb: anything we create in Python is an 'object' or 'instance' implementing a Class.**
Perhaps a metaphor will help. A 'Coffee Mug' Class can be thought of like a blueprint for making a coffee mug. The Class describes all the elements and functions of a coffee mug, such as the handle, the cup, the decoration, etc. Objects are the actual coffee mugs that you produce from the blueprints. Each individual mug in your cupboard is an 'instance' of the blueprint (Class).

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

The elements .year, .month, .day, are 'attributes' of datetime. They hold data pertinent to the object at hand.

### Methods
Objects have data attributes. But code exists to perform tasks, and so objects also have attributes that do things. These are called 'methods'. 
An example of a method that can be performed on a 'str' object is .lower(). This method turns any upper-case letter into a lower-case letter. Let's get this to happen for us:

```python
def greet(name):
    print(f'Hello, {name.lower()}!')
greet('John')
```
We passed the parameter 'name' into the function 'greet'. It is an object, which happens in this case to be a string, 'John'. We then 'called' a method on this object, .lower(), which performed the action of lowering the 'J' to 'j'.  It is a bit tricky to distinguish an attribute that is data from one that is a method because we also access methods using this 'dot notation' (with the '.' and then the name of the attribute). Let's distinguish the two:

```python
import math
print(math.pi)
#this is a data attribute. Pi is a specific number!

print(math.sqrt(16))
#this is a method attribute. It takes the square root of 16!
```
So we have seen that objects (which is virtually everything we use in Python) have methods which can be performed with them, and data associated with them. Let's turn back to Classes now to understand them a little bit better.

### Classes
We know that, for example, the module 'math' has .pi associated with it. But this is not automatic: Python as a language needed to be informed of this fact. Otherwise, you could 'call' .pi on a string, like 'name.pi', which would make no sense! As we established above, **Classes** are the recepies that define what specific methods and attributes an object should have. Knowing what classes look like, and what they do, will help you tremendously in reading code and using code that other people have written.

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

<li>1. The class name is Greeting, and like a function, it has the same colon and indentation rules. Class names are always capitalised in code documentation.</li>
<li>2. Under the class name goes the method(s). Note that these look (and operate) much like functions. Ours only has one method, which is to print a greeting. </li>
<li>3.'g = Greeting()'. When you write this, you are telling Python to make an object that follows the instructions of 'Greeting'. We store that object in a variable, which we've termed 'g' here. What we name it does not matter. </li>

Now look again at 'def greet(self):'. The method has this parameter called 'self' specified in the brackets, much like we may specify data for a function. This word 'self' is Python's way of making a connection between the method and the object, which we called 'g'. 'self' ties in the greeting object with the method 'greet'. 

Remember above where we established that objects can have data attributes? 'g.name' creates a data attribute containing the name 'Maria'. Where you see {self.name}, this attaches the data attribute to the object, 'g'. Therefore when we run the last line of code, g.greet(), that specific bit of data, 'Maria', gets automatically attached. 

Remember again that objects can have method attributes. Here our method attribute 'g.greet' attaches the action 'greet' (which prints a phrase) to the object. 

To summarise, we have a Class that's all about printing greetings. From it we created an object, 'g'. When we call 'g' in our code, we use this Class, which contains instructions that 'g' follows. That way, we can store the name Maria as data, an attribute, for 'g'. We can perform the action of printing a phrase as a method attribute for 'g'. 

#### OOP Usefulness
At this stage, simply knowing that 'Classes' exist and a little bit about what they do is sufficient. When you read code documentation on a module and see that it has various Classes, you can then see what different things the module does, and how to make use of them. You can even choose to import only a class from a module, like in the module textblob (which you discovered in earlier lessons):

```python
from textblob import Word
```
This line of code will import the Class 'Word' from the textblob module. Word is a Class that contains many methods around analysing words in texts.

Finally, Python bug reports often deal with the levels of Python structure. A common error, if you call the wrong attribute for an object, is 'this object has no attribute X'. Knowing some of this vocabulary and the way Python is put together will help you interpret such error messages.

## Conclusion
This lesson is probably the most theoretical of this course, and beginners often find these details to be challenging to grasp at first. The best way to acclimate yourself is to read code documentation.

Your homework in this case is to:

1. Search online for the Textblob Python module. You are already familiar with part of it from previous lessons. Read through the quick start guide to refresh your memory. Next, go to [this page](https://textblob.readthedocs.io/en/dev/api_reference.html), which describes the different classes in the textblob module. Read the documentation for the class 'Word'. This will help you get a feel for how Classes appear in documentation in some more accessible language.
2. Take our Class that we made above, and change the .name attribute to a list of students. Instruct the class to only print the greeting if the name specified in your code is present in the list. If the name is not present, instruct the class to print a phrase indicating 'this person is not present'.
3. Notice that we used a lambda function to turn 'Maria' lowercase early in the lesson. Then, we described '.lower' as a method attribute within the Class 'str' (string). Why do you think this redundancy exists in Python structure? Find another lambda function and modify the greeting Maria code with it. 




