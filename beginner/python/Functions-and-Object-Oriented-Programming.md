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
greet(Maria)
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
greet(Maria)
```
Here we added in the len() function. Look at the documentation to see how it describes what len() does. It is always good to get in the habit of reading code documentation.






