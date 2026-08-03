<link rel="stylesheet" href="../../cookbook.css">
# Homework Solutions Lesson 5: A Deeper Look at Functions and Introduction to Object Oriented Programming
<p class="previous-next-lesson"><a href="toc.html">^ Main contents</a></p>
# Task 1
For this task you should have explored some Classes within the textblob module. As such, there are no 'solutions' for us to cover. But this is an important opportunity to pause and reflect on what you saw. What was confusing? What made sense? If something was confusing, how might you go about finding more information about it?

One of the most important skills anyone writing code can have is to find information. You will never remember all of the code that you have learned, and facts about programming languages can easily slip your mind. Moreover, there is always a new fact or a strange problem that will present itself. If you found aspects of OOP difficult to understand in this first introduction, this is a good opportunity to look for additional resources. Some may confuse you and some may help clarify aspects of the matter. Using ChatGPT can potentially help, but be wary of using it by default to get quick answers. Wrestling with a complex concept like OOP until you understand it without the aid of AI will pay off in the long run. 

# Task 2
A correct way to do this is presented below:

```python
class Greeting:
    def greet(self, name):
        if name in self.names:
            print(f"Hello, {name}!")
        else:
            print(f"{name} is not present.")

# create an object from the class
g = Greeting()

# assign a list of students as the attribute
g.names = ["Maria", "John", "Sophie"]

# enact the method with a name in the list
g.greet("Maria")  

# enact the method with a name not in the list
g.greet("Alex")
```
Remember the following:

<li>You need f-strings to print out variables like {name}</li>
<li>Notice that def greet() gets two parameters, 'self' (connecting it to the object instance) and 'name' (connecting it to the data attribute)</li>
<li>Notice the if statement: 'if name in self.names:'. self.names is an attribute of self, or g. It means that this object has the list of names associated with it. </li>
<li>This task is a bit tricky because I asked you to write an 'if...else' statement. We haven't yet covered those formally. However, you will come across many things in programming that will require you to act before you have formally learned the relevant facts. How did you go about looking for this information? Were you successful? What could you have done differently?</li>

# Task 3
Your task was to incorporate a lambda/anonymous function into the Greeting class to ensure that all the students' names get printed correctly.
Here is a possible solution:

```python
class Greeting:
    def greet(self):
        clean_name = lambda n: n.strip().capitalize()
        print(f"Hello, {clean_name(self.name)}!")

g = Greeting()
g.name = "  maria  "  
g.greet()

```
Try running this. What does it do? 
Notice that this solution uses a lambda/anonymous function (clean_name), and within it, we have string methods, n.strip() and .capitalize()! The takeaway message is that you can use a lambda/anonymous function to support the idiosyncrasies of your situation, and methods are actions predefined by Python that are tied specifically to types of objects (like strings). Methods can be incorporated wherever needed, including inside your own lambda/anonymous functions.

<p class="credits">Written by Estara Arrant, 2025-04-16<br />Licence: <a href="https://creativecommons.org/licenses/by-sa/4.0/">CC BY-SA 4.0</a></p>
