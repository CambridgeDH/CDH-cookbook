<link rel="stylesheet" href="../../cookbook.css">
<p class="previous-next-lesson"><a href="toc.html">^ Main contents</a></p>
# Homework Solutions: Lesson 1: Introduction to the Python Language
Here we have given some suggested code and thematic solutions to the relevant homework questions for Lesson 1: Introduction to the Python Language.

## Task 1
This task involved doing a search online for some relevant Digital Humanities Python packages. You could have used any search engine, or an AI tool, to help you find some potential packages. If you are struggling, a particular site that describes a lot of methods for Digital Humanities is [Programming Historian](https://programminghistorian.org/en/). However, the best way to become acquainted with packages you may need is to get involved in real projects and start trying to produce code. The needs of that project will force you to go looking for code that might exist which accomplishes specific goals related to your project. 

## Task 2
In this task you were asked to open your Notebook software (see the Prerequisites page for a course on coding Notebook software such as Jupyter Notebooks or Google Colab). Let's say you found a package called 'reallycoolpackage'. In a cell, you would type the following, and then hit enter or 'run':

```python
%pip install reallycoolpackage
```
In order to use this package, however, we also have to load it:

```python
import reallycoolpackage
```
Let's say you went one step further and found a module within reallycoolpackage, called 'coolmodule', which someone wrote as open source software and put it online, perhaps on the [Python Package Index](https://pypi.org/). Here's how you should have imported it:

```python
from reallycoolpackage import coolmodule
# Note that you can rename the module as something easier to type:
from reallycoolpackage import coolmodule as cm
```
However if you you found a built-in Python module using the [Python Module Index](https://docs.python.org/3/py-modindex.html), you can simply import it without installing. These built-in modules were already included when you first installed Python on your computer:

```python
import calendar
```
Note that with all of these statements, as long as you do not get an error message, you can know that the cell has run properly. 

## Task 3
This task asked you to look at some of the modules in the Python Module Index. This exercise would have helped you to see how the code in the modules is structured, and to get a feel for how code is formally described. If terms are very unfamiliar, you can search them online. Additionally, if you are struggling with a built-in Python module, you can run the following command:

```python
import module
help(module)
# Replace 'module' with the name of the module that you need to import and get help with.
```

## Task 4
The purpose of this task is to get you to explore what exists online about code that may do things of interest to you. Remember that **it is not cheating to search the internet for information when you are coding or learning to code!**

## Summary
And, that's it!  This lesson should have you comfortably installing and importing packages and modules. Once you can do this easily, you are ready to start learning how to write more substantial commands.


<p class="credits">Written by Estara Arrant, 2025-04-16<br />Licence: <a href="https://creativecommons.org/licenses/by-sa/4.0/">CC BY-SA 4.0</a></p>
