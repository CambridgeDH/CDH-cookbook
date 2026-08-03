<link rel="stylesheet" href="../../cookbook.css">
# Lesson 7: File Handling Essentials

<p class="previous-next-lesson"><a href="toc.html">^ Main contents</a></p>

## Contents
- [Overview](#overview)
- [Open and Close](#open-and-close)
- [Reading and Writing](#reading-and-writing)
- [Copying and Reusing Content](#copying-and-reusing-content)
- [Dealing with File Types](#dealing-with-file-types)
- [Renaming Files](#renaming-files)
- [Conclusions](#conclusions)


## Overview
In the first Milestone Lesson you learned, through practicing writing loops, about some fundamentals of file handling: navigating directories, listing files in a directory, and putting in some basic data. However, there are many more aspects to dealing with files in Python, and file handling is a crucial skill. This lesson will briefly cover the main file handling functions that Python provides, and because this task is so essential, these functions are built-in. 

[Back to table of contents](#contents)

## Open and Close
To open files in Python, you can use the following syntax:

```python
desired_file = open('filename.txt', 'file_mode')
print(desired_file)
```
'file_mode' is what we are calling the argument for the file mode that we choose to tell Python when we open a file. There are multiple: 'read', denoted by 'r' (this simply has Python find out what the contents of the file are), 'append', denoted by 'a' (adds new content to the end of a file), 'write', denoted by 'w' (this has Python put something in a file). There is also 'read and write', denoted by 'r+'. We used this one in the Milestone lesson. You can also simply open a file and not include any special argument for the mode, as 'read' is the default.

To close files, we simply run 'desired_file.close()'. 

[Back to table of contents](#contents)

## Reading and Writing
You will already be familiar with this from the Milestone Lesson, but we will repeat it here. To read a file and tell you its contents:

```python
file = open('my.txt')
content = file.read()
print(content)
file.close()
```
However, notice that at the end we have to overtly tell Python to close the file. There is another way to do this which results in Python automatically closing the file after it has read it:

```python
with open('my.txt') as file:
    content = file.read()
    print(content)
```
This statement is known as a 'context manager' in Python. It simply closes the file by itself after the indented block has been run.

To write, we can do this :
```python
with open('my_text.txt', 'w') as file:
    file.write('First line here.')
    file.write('I am tired of writing endless text lines!')
```
Notice again since we are using the context manager 'with...as', the file is closed after the indented lines are run. Notice also how the output has the lines run together? We can avoid this by instructing Python to add in an escape character for a new line, which look like this: ('First line here.\n').

**Important**: Notice that in the above code, we have the 'w' argument for 'write'. Here it is strictly needed because we are writing content into the file we have just created and opened. But if there is something in this file already, 'w' will overwrite those contents! If you want to add content on to the end of preexisting content, use 'a' (append mode). 

[Back to table of contents](#contents)

## Copying and Reusing Content

You can combine the read and write functions to copy content in one file and then re-use it in another:

```python
# Step 1: read the content of the source file. 
with open('source.txt') as source_file:
    content = source_file.read()

# Step 2: write the content into the target file
with open('target.txt', 'w') as target_file:
    target_file.write(content)
```
This code will read the content of one file (when Python 'reads' content, it essentially copies it), and then write it to the next file. If you don't want to replace all the contents of the next file, though, you would need to use the file mode 'a' (append mode). This will place the freshly read content at the end of the content that already exists in the file.

[Back to table of contents](#contents)

## Dealing with File Types
Usually, when opening a file, you can specify the basic file type like .txt, .json, or .csv. You just use that prefix in the open command:

```python
desired_file = open('filename.csv', 'file_mode')
print(desired_file)
```
If you need to save a file as a format that relies on other software (like an Excel spreadsheet; you cannot open an .xlsx file without having Microsoft Excel installed, for example), you will need to download a module specifically for that. A common one for Excel is:

```python
from openpyxl import Workbook

# Create a new workbook and select the active sheet
wb = Workbook()
sheet = wb.active

# Write some data
sheet["A1"] = 'Name'
sheet["B1"] = 'Age'
sheet.append(['Alice', 30])
sheet.append(['Bob', 25])

# Save to file
wb.save('people.xlsx')
```
[Back to table of contents](#contents)

## Renaming Files
Using the 'os' module you can rename your file:

```python
import os
os.rename('old_name.txt', 'new_name.txt')
```

There are other kinds of filetypes and actions are a bit more tricky, and involve more complex Python modules, but if you need them, the solution is to search for them and then read their documentation thoroughly. Common modules for this sort of task are:

<ul>
<li>The os module</li>
<li>The openpyxl module</li>
<li>The shutil module</li>
<li>The reportlab module</li>
</ul>

[Back to table of contents](#contents)

## Conclusions
This brief lesson gives you a basis in the fundamentals of file handling in Python. These functions can be a bit finicky, though, especially as you do not want to accidentally destroy your data, so it's important to practice to get the hang of using them before working with your actual files.

Homework for this lesson:

Task 1: Open a text file and use Python to load all its lines in a list. Then insert a new line somewhere in the middle of that list, and save the updated content back into the file.
Task 2: the content of one file into another, but transform the content while copying (e.g., uppercase, add line numbers, or replace a word). Do not do this manually; have Python do everything for you.
Task 3: (Advanced) Search the internet for the shutil and reportlab module documentation. Use shutil.copy() to duplicate a file. Use reportlab to generate a simple PDF with one line of text.


[Back to table of contents](#contents)

<p class="credits">Written by Estara Arrant, 2025-04-16<br />Licence: <a href="https://creativecommons.org/licenses/by-sa/4.0/">CC BY-SA 4.0</a></p>

<p class="previous-next-lesson"><a href="lesson6-further-loops-and-conditionals.html">&lt; Previous lesson</a> | <a href="lesson8-capstone-using-python-in-humanities.html">Next lesson &gt;</a></p>
