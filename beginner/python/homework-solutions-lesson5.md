# Homework Solutions Lesson 5: A Deeper Look at Functions and Introduction to Object Oriented Programming
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

#Task 3
In the lesson, we used both a lambda function ('format_name = lambda n: n.lower()') and a method ('.lower()') to make text lowercase. This 'redundancy' isn't actually redundancy. It's a core part of the flexibility of the Python language. You can either choose to use a built-in method associated with an object (in this case, an object which we implement under the 'str' Class) or you can write a quick lambda function. The result is the same. To review:

Lambda functions are tools for writing small, one-off functions. They don’t “belong” to any specific object.
Methods are action attributes that are attached to specific objects (like strings). They are usually the most direct way to manipulate an object.

Finally, here is an example of using another lambda method (you could have used any to complete the homework!):

```python
def greet(name):
    repeat_name = lambda n: n * 2
    print(f"Hello, {repeat_name(name)}!")

greet("Maria")
```
Try running this. What does it do? 

