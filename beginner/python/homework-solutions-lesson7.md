# Homework Solutions Lesson 7: File Handling Essentials
Your tasks in this lesson were to practice using file handling commands and to search for documentation on some file handling modules.

## Task 1
Here is a solution for inserting a line into the middle of a file:

```python
# Step 1: read the file
with open('my_text.txt', 'r') as file:
    lines = file.readlines()

# Step 2: insert a new line (at position 1 after the first line)
lines.insert(1, 'This is the new inserted line.\n')

# Step 3: rewrite the file with the updated content
with open('my_text.txt', 'w') as file:
    file.writelines(lines)

# Step 4: check the new content
with open('my_text.txt', 'r') as file:
    print(file.read())
```
Why is there not a simpler way to do this? Well, there are no gaps in the bytes that comprise each file. Therefore, Python cannot find a location in which to automatically insert content in the middle of a file. What this code does is extract the content, manipulate it in working memory, and then re-insert it into our file.

## Task 2
Here is a solution for copying the content from one file to another while also transforming an aspect of that content:

```python
# Step 1: read source file
with open('source.txt', 'r') as source:
    content = source.read()

# Step 2: transform content (make uppercase)
content_upper = content.upper()

# Step 3: write into target file
with open('target.txt', 'w') as target:
    target.write(content_upper)

# Step 4: confirm
with open('target.txt', 'r') as target:
    print(target.read())
```
The result should be that all the content in the new file is in UPPERCASE. 

## Task 3:
For this task, which is a bit more advanced because it involves reading some slightly more complex documentation, there is a potential solution:

```python
import shutil
# You may need to install shutil

# Copy a file (source → destination)
shutil.copy('source.txt', 'backup_source.txt')
print('File copied successfully.')
# The result should be a duplicate of 'source.txt'

from reportlab.lib.pagesizes import letter
from reportlab.pdfgen import canvas
# Again, you may need to install reportlab first!

# Create a new PDF and write some text
c = canvas.Canvas('example.pdf', pagesize=letter)
c.drawString(100, 750, 'This PDF was created with Python!')
c.save()
print('PDF created successfully.')
# The result should be a PDF with the sentence 'This PDF was created with Python!'
```
If you were able to learn from this homework to better understand file handling, congratulations, you have a major aspect of coding foundation under your belt. These are the kinds of commands which you will use daily in your coding career.



`
