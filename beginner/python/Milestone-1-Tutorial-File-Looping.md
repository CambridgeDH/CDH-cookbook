# Milestone 1 Tutorial: A File Looping Program

In the past three lessons you have learned the essential foundations one must know before one can begin coding. However, you have also learned a few fundamental skills which together enable to you write your first Python program. This tutorial will help you put these skills to use by teaching you how to write the correct commands in the proper order for looping through and editing some files.

## The Goal
Before you begin to write any sort of code, it is essential that your aims and objectives are clear to you. By taking a few minutes at the start of any project to clarify exactly what it is that you want to achieve and to gather the tools you need to achieve it, you save yourself potentially hours of stress caused by attempting to write a program without knowing the path forward. It is good practice to always state somewhere what you are doing, how you are doing it, and why.

### What We are Doing?
Today we will be writing a program in Python that will go into a file directory, open and read each of the files in that directory, make specific changes to those files, and close them. As this is a repetitive task, we will be writing our code in the form of a 'for loop'.

### How We Will Do This?
We will build a simple program that uses the Python module os. [Here](https://docs.python.org/3/library/os.html) is a link to the official Python documentation on this module. In this link you will see many headings in bold that look like: os.chdir(), osgetcwd(), etc. These are the specific functions of the module (refer to Lesson 1 for an explanation of the layers of Python code). This module is known as a 'built-in' module, which means that you do not have to install it separately; it is part of the copy of Python on your computer. The os module instructs Python in navigating your operating system, including your files and directories. 

### Why Are We Doing This?
Navigating through multiple files and performing the same kind of action on each file is one of the most common tasks we do with our computers, and it is easily automated (of course, depending on the kind of task we are doing). It is also straightforward and is an appropriate 'first program' to learn how to write. Writing this program will make you use the concepts and skills taught in the first part of this course. 

## Phase 1: Setting Up the Workspace
The first thing to do is to set up your workspace and your tools. We will operate in Jupyter Notebooks, so open up a fresh one. The os module is the only module needed for the task of navigating directories and opening and closing files, and our program will simply open up files and put some information in them, and then close it. Therefore, we only need the os module. In the first cell, then, import the os module:

```python
import os
```
Hit 'run'. If your cursor moves to the next cell, then the code has run, and the module is imported and active in your workspace. Jupyter Notebooks lives in your home folder, so your script will be there. It's recommended that you save the notebook with a unique name, like 'file-looping-script'. 

Unless you want to do something more complex, that's it, your workspace is set up. It's common practice to begin any program this way, by importing/installing the necessary modules. Essentially, any code you write is made up of other people's programs. We bring these programs in from the start.

## Curating Your Files
Before we can tell Python to go into a directory and loop through files, we have to have the directory and files ready. Choose a straightforward place on your computer, such as your home folder or your desktop, and place in it a folder. In this folder we want to have two empty text (.txt) files. You can call them and this folder whatever you like, but there are a couple of good principles for file naming which will make your life infinitely easier:

<li>1. Use descriptive and unique names</li>
<li>2. Avoid spaces. Use capitalisation or special characters to visually separate out words.</li>

We use descriptive and unique names so that we and the computer always know which files we want to work with. And we avoid spaces in our names because we want Python to be able to identify the files without issues. While an empty space is a Unicode character, it's better to avoid spaces. For this example I've named the folder 'file-looping' and the two empty text files as 'Document1.txt' and 'Document2.txt'. In real life we would want something far more descriptive and specific, but this will do for now.

**At this point we have our module loaded, and we have a directory and files for our program to read.**

## Designing the Program Steps
Since we are writing a program from beginning to end, it is important to have a clear picture of each of the steps we will want the program to take. Developers often write these externally for reference, especially if their programs are complex and involve many functions. Our program will have only one function, but it is still helpful to have a list of the actions our program will take:

<li>1. Identify the folder with our documents</li>
<li>2. Open that folder and identify the documents inside</li>
<li>3. Open a document</li>
<li>4. Perform the task (in our case, we want Python to put a sentence in our document)</li>
<li>5. Save and close the document</li>
<li>6. Open the next document and repeat steps 4 and 5</li>
<li>7. Terminate when there are no more documents to open and edit</li>

The last step is very important: it is possible to write an endless loop in our code that will continue running until the universe ends. We do not want this!
Notice how specific and granular each step is. There is not anything that has been left unsaid in our plan. Why is it so important to be this specific? There is a principle which will carry you far in the world of coding:
**Computers do exactly what you tell them: no more, no less.** 
Therefore, you must tell them exactly what you want them to do. Every step needs to be specified. Computers do not 'read between the lines'. 





