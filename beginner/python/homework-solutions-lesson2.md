<link rel="stylesheet" href="../../cookbook.css">
<p class="previous-next-lesson"><a href="toc.html">^ Main contents</a></p>
# Homework Solutions: Lesson 2: Fundamental Commands and Actions in Python
Here we have given some suggested code and thematic solutions to the relevant homework questions for Lesson 2: Fundamental Commands and Actions in Python.

## Task 1
This task encourages you to get used to reading Python documentation. The textblob package is a popular Natural Language Processing package that has a user-friendly tutorial. It is open-sourced and well supported. Reading documentation about how Python packages and modules work is important, as documentation contains the instructions for how to use other people's code properly.

## Task 2
Examples for various data types

```python
import textblob
import os

# A string
sample_text = '''This is my sample text. Today I walked down to the river and watched the swans and boats go by. As I sat by the river, I saw...'''

print(sample_text)
type(sample_text)

# A list:

garden_trees = ['Olive', 'Oak', 'Apple']
print(garden_trees)
type(garden_trees)

```
## Task 3
If you save a Text file (with the filename ending in .txt) in your home folder (which is the default working directory for Jupyter Notebooks), then you can run the following command

```python

my_text_file = open('filename.txt')
print(my_text_file.read())

# Note that 'my_text_file' is a variable that you create.
# In order to read and print the file, you have to use the variable name, not the file name, in the print command.

```

## Task 4
Say you want your working directory to be your desktop. One way to do this is (it can vary depending on your operating system; this example is cross-platform friendly):

```python
import os

home_dir = os.path.expanduser("~")
# This gives you your home directory

desktop_path = os.path.join(home_dir, "Desktop")
# This creates the path to your desktop

os.chdir(desktop_path)
# This specifies the new home directory as your desktop

print("Current Working Directory:", os.getcwd())
# You can run this command to tell you what your current working directory is now.
```
## Reflection
Hopefully this reflection helped you to see how your data may be viewed differently in a coding context.

## Summary
There you have it: these are the main ways to declare variables, change directories, and open files in Python.

<p class="credits">Written by Estara Arrant, 2025-04-16<br />Licence: <a href="https://creativecommons.org/licenses/by-sa/4.0/">CC BY-SA 4.0</a></p>
