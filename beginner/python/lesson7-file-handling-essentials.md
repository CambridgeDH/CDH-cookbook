# Lesson 7: File Handling Essentials

## Contents

## Overview
In the first Milestone Lesson you learned through practicing loop writing about a couple of the fundamentals of handling files: navigating directories, listing files in a directory, and putting some basic data into the files. However, there are far more aspects to dealing with files in Python, and this is a crucial skill for any researcher in the Humanities who needs to use Python to analyse their data. This lesson will quickly cover the main file handling functions that Python provides. Because file handling is central to most of what we do as coders, the functions around it are built-in. 

### Open and Close
To open files in Python, you can use the following syntax:

```python
desired_file = open('filename.txt', 'file_mode')
print(desired_file)
```
'file_mode' is what we are calling the argument for the file mode that we choose to tell Python when we open a file. There are multiple: 'read', denoted by 'r' (this simply has Python find out what the contents of the file are), 'append', denoted by 'a' (adds new content to the end of a file), 'write', denoted by 'w' (this has Python put something in a file). There is also 'read and write', denoted by 'r+'. We used this one in the Milestone lesson.

To close files, we simply run 'desired_file.close()'. 

### Reading and Writing
You will already be familiar with this from the Milestone Lesson, but we will repeat it here. To read a file and tell you its contents:

```python
file = open('my.txt', 'r')
content = file.read()
print(content)
file.close()
```
However, notice that at the end we have to overtly tell Python to close the file. There is another way to do this which results in Python automatically closing the file after it has read it:

```python
with open('my.txt', 'r') as file:
    content = file.read()
    print(content)
```
This statement is known as a 'context manager' in Python. It looks a bit like a loop, but it does not iterate through anything. It simply closes the file by itself after the indented block has been run.

To write, we can do this:
```python
with open('my_text.txt', 'w') as file:
    file.write('First line here.')
    file.write('I am tired of writing endless text lines!')
```
Notice again since we are using the context manager 'with...as', the file is closed after the indented lines are run. Notice also how the output has the lines run together? We can avoid this by instructing Python to add in an escape character for a new line, which look like this: ('First line here.\n').
**!Important!**: If there is something in this file already, 'w' will overwrite those contents! If you want to add content on to the end of preexisting content, use 'a' (append mode)! If you use 'a' before the file exists, then it will create the file from scratch.

### Copying and Re-Using Content

You can combine read and write to copy content in one file and re-use it in another:

```python
# Step 1: read the content of the source file
with open('source.txt', 'r') as source_file:
    content = source_file.read()

# Step 2: write the content into the target file
with open('target.txt', 'w') as target_file:
    target_file.write(content)
```
This code will read the content of one file (when Python 'reads' content, it essentially copies it), and then write it to the next file. If you don't want to replace all the contents of the next file, though, you would need to use the file mode 'a' (append mode). 

### Dealing with File Types
Usually, when opening a file, you can specify the basic file type (if it is not dependent on external software), like .txt, .json, or .csv. You just use that prefix in the open command:

```python
desired_file = open('filename.csv', 'file_mode')
print(desired_file)
```
If you need to save a file as a format that relies on other software (like an Excel spreadsheet), you will need to download a module specifically for that. A common one for Excel is:

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

### Renaming Files
Using the 'os' module you can rename your file:

```python
import os
os.rename('old_name.txt', 'new_name.txt')
```

There are other kinds of filetypes and actions are a bit more tricky, and involve more complex Python modules, but if you need them, the solution is to search for them and then read their documentation thoroughly. Common modules for this sort of task are:
<li>The os module</li>
<li>The openpyxl module</li>
<li>The shutil module</li>
<li>The reportlab module</li>

## Conclusions
This brief lesson gives you a basis in the fundamentals of file handling in Python. Such tasks are so common that any coding foundation in Python would be incomplete with out them.

Homework for this lesson:

<li>Task 1:</li> Open a text file and use Python to load all its lines in a list. Then insert a new line somewhere in the middle of that list, and save the updated content back into the file.
<li>Task 2:</li>Copy the content of one file into another, but transform the content while copying (e.g., uppercase, add line numbers, or replace a word). Do not do this manually; have Python do everything for you.
<li>Task 3 (Advanced)</li>: Search the internet for the shutil and reportlab module documentation. Use shutil.copy() to duplicate a file. Use reportlab to generate a simple PDF with one line of text. 



