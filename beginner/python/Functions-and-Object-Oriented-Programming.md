# Lesson 4: A Deeper Look at Functions and Introduction to Object Oriented Programming

## Contents


## Overview
In the previous Milestone lesson, you learned how to write a small program in Python to loop through some files and make changes to them. This program involved writing three different functions, and creating variables that you 'called' within those functions. These are the most basic kinds of functions that one can write in Python, and so now is appropriate to begin looking into the other kinds of functions that are possible in this language. You will also be introduced to the concept of 'Object Oriented Programming' - which is essentially our 'university library' metaphor that we discussed in the irst lesson, but made concrete through actual code examples, and therefore more practically useful.

## The Wide World of Function Types

### User Defined Functions (UDFs)
In the Milestone lesson you learned to write what we call a 'User Defined Function' (UDF). That's why you put 'def' at the beginning of each function name. Let's review the 'anatomy' of such a function:

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
<li> - Below the first line, we have an *indented* block of code. The colon on the first line demands indentation. The indentation tells Python that everything under that line is part of that function and nothing else. This is the 'body' of the function. It is like the cooking instructions for our recipe.</li>
<li> - At the bottom, we have 'write_content()' again. Since we have no input parameters (no necessary ingredients), we do not include anything in the brackets here. </li>

Let's look at a function that does have input parameters:

``` python
def greet(name, known=False):
  if known:
      print(f'Hello, {name}!')
  else:
  print(f'Hello, {name}, I'm Sophie')
greet('Maria')
```
Here we define a new function, 'greet'. It has specific input parameters: name (this means when you call the function, you have to give a name), and known=False (this means that if you know the person you are greeting, you need to put 'True' in the brackets when you call the function). 
Try calling the function in a new Jupyter Notebook. Call it with 'greet(name)' and then with 'greet(name, True)'. See what happens? 

Note the 'f' before the phrase in the print statements. This is called an 'f-string'. It allows us to insert a variable name into our greeting. Try running the function without the 'f'. What happens then?

UDFs are ubiquitous in Python: you will be writing them for the rest of your coding career. But there are other kinds of functions in Python that you should know about.

### Built-In Functions
The version of the Python language that is installed on your computer comes with a variety of 'built-in' functions. They are always available to you for use, regardless of whether you have a specific module installed. Python's documentation has a list of all of them, [here](https://docs.python.org/3/library/functions.html). Have a look at different ones. 

How might you use a built-in function? The function 'help()' is especially useful. Type it into a cell in your notebook. What happens?
Notice there is a text box inside the output when you run 'help()'. You can type a module name, like 'os', into that box, and get specific help and documentation on the os module. 
You can also use built-in functions inside your UDFs. Let's say we wanted to know how many letters is in someone's name when we greet them, and tell them this fact. Here's how we would add it to our greet() function:

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

It is important to distinguish 'module functions' from 'built-in' functions. In our looping program, we used code like os.getcwd(). These are functions that exist as part of a module, which is a set of code that someone else built for us to use. Your UDFs can become 'module functions' if you were to build a module and publish it. In that sense, they are 'built-in' to the module, but not to Python itself. 

### Anonymous Functions
When writing longer programs, not every action is crucial enough that you need to formally 'define' a function for it. Python has a way of creating a function without giving it a name; we call these 'anonymous' functions. They are also known as 'lambda' functions, derived from a similar concept in lambda calculus. 
These functions are special in that they are *short*, containing only a single action ('expression), and are meant to accomplish something quickly without the hassle of writing a large block of code. Here is an example of a lambda/anonymous function in our greet code:

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

To summarise, we have three (or four, if you are counting module functions) types of functions in Python: User Defined Functions, built-in functions, and one-off lambda functions. 

## Introduction to Object-Oriented Programming (OOP)
At this point it is appropriate to introduce you to the concept of 'Object-Oriented Programming' (abbreviated ubiquitously as 'OOP'). OOP is essentially the term describing an essential operational characteristic of Python. 

### Objects 
In Python we create and manipulate 'objects' at different levels (Module, Class, Function, Variable). Everything that you deal with in Python is an object. What is this 'object'? It is an encoding of data and often, a specific action to take by the computer using that data, stored in the computer's memory. Understanding how Python uses these objects can help you understand and write code more effectively.

In our code above, we tell the computer to print the name 'Maria'. We can check what kind of object Python considers Maria to be:

```python
name = 'Maria'
print(type(name))
```
We get '<class 'str'> back. What do you think that means? It means that 'Maria' is a 'string', literally a few characters in a row. Python considers name to be an variable containing an object that is a string, which is made up of 'M' 'a' 'r' 'i' 'a'. Remember the 'Data types' from the first lesson? These are some of the types that objects can have. 

### Methods
As I mentioned above, often objects have actions associated with them. We call these actions **methods**. These are the things that Python can do with a given object. An example of a method that can be performed on a 'str' object is .lower(). This method turns any upper-case letter into a lower-case letter. Let's get this to happen for us:

```python
def greet(name):
    print(f'Hello, {name.lower()}!')
greet('John')
```
We passed the parameter 'name' into the function 'greet'. It is an object, which happens in this case to be a string, 'John'. We then 'called' a method on this object, .lower(), which performed the action of lowering the 'J' to 'j'. 


### Attributes
Alongside methods, objects also have attributes, which are specific pieces of data that are associated with the object. Do you remember how we said that 'everything that we deal with in Python is an object'? That is literally true, *everything* is an object. So, Python has a module called 'math'. This module itself is an object. You can think that a module called 'math' would have a lot of pieces of specific data associated with it, and that is also correct. In fact, 'math' has a specific piece of data, pi:

```python
import math
print(math.pi)
```

The bit, '.pi' is an **attribute** of the object 'math'. It is tricky, because we also access methods using this 'dot notation'. Let's distinguish it from dot notation denoting a method:

```python
import math
print(math.pi)
#this is an attribute. Pi is a specific number!

print(math.sqrt(16))
#this is an action. It takes the square root of 16!
```
So we have seen that objects (which is virtually everything we use in Python) have methods which can be performed with them, and attributes associated with them. One last thing that is necessary to understand at a basic level about OOP is the concept of a 'class'.

### Classes
We know that, for example, the module 'math' has .pi associated with it. But this is not automatic: Python as a language needed to be informed of this fact. Otherwise, you could call .pi on a string, like 'name.pi', which would make no sense! **Classes** are the recepies that define what specific methods and attributes an object should have. It will be a while before you will be writing classes of your own, but knowing what classes look like, and what they do, will help you tremendously in reading code and using code that other people have written.

```python
class Greeting:
    def greet(self):
        print(f"Hello, {self.name}!")

g = Greeting()
g.name = "Maria"     
print(g.name)        
g.greet()           
```




