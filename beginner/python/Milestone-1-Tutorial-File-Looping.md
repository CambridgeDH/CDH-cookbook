# Milestone 1 Tutorial: A File Looping Program

In the past three lessons you have learned the necessary essentials to begin coding. These essentials provide you with a few fundamental skills that enable to you to write your first Python program. This tutorial is designed to have you put those skills to use by showing how to write the correct commands, in the proper order, for looping through and editing files.

## Phase 1: Objectives, Program Design, and Workspace Setup
Before you begin to write any sort of code, it is essential that you set clear objectives. Pausing and stating what exactly you want to achieve, and gathering the tools needed to achieve it, will potentially save you hours of time. It is never wise to start writing a computer program without your goals understood and the tools readily available. This involves recording somewhere the following three things: what you are doing, how you are doing it, and your reasons for doing it.

#### What We are Doing?
Today we will be writing a program in Python that will go into a file directory, open and read each of the files in that directory, put a sentence into those files, and save and close them. 

#### How We Will Do This?
As this is a repetitive task, we will be writing our code in the form of a 'for loop'. We do this by building a simple program that uses the Python module 'os'.The os module instructs Python in navigating your operating system, including your files and directories. This module is known as a 'built-in' module, which means that it is part of the copy of Python on your computer.  [Here](https://docs.python.org/3/library/os.html) is a link to the official Python documentation on this module. In this link you will see many headings in bold that look like os.chdir(), osgetcwd(), etc. These are the specific functions of the module (refer to Lesson 1 for an explanation of the layers of Python code). 

#### Why Are We Doing This?
Navigating through multiple files and performing the same kind of action on each file is one of the most common tasks we do with our computers, and it is easily automated. Because it is straightforward, it is a good 'first program' to learn how to write, and it will make you use the concepts and skills taught in the first part of this course. You will be able to use the components of this program to write future programs for navigating and modifying your files.

### Designing the Program Steps
Since we are writing a program from beginning to end, it is important to have a clear picture of each of the program's steps. Developers often write these externally for reference, especially if their programs are complex and involve many functions. It is good to get into this habit early in your journey of learning to code.

For each function, we list out the actions that that function will take. Then, we put the functions together. Our program is simple, though, so we only have one function to design:

<li>1. Identify the folder with our documents</li>
<li>2. Open that folder and identify the documents inside</li>
<li>3. Open a document</li>
<li>4. Insert a sentence inside the document</li>
<li>5. Save and close the document</li>
<li>6. Repeat steps 2-5 for the next document</li>
<li>7. Terminate when there are no more documents to open and edit</li>

Notice how each step is specific and granular. There is nothing left unsaid in our plan. Why is it so important to be this specific? It is because of an essential principle about computers:
**Computers do exactly what you tell them: no more, no less.** 
Computers do not 'read between the lines'. The faster you embrace the concept of designing specific and granular programs, the faster you will progress because you will not try to write programs that imply invisible steps that the computer cannot follow.
Now that we have established our objectives and thought through the steps of our program, we need to set up our filesystem.

### Curating Your Files
The first thing to do is to determine where to put the files that you want the program to modify. We will be using Jupyter Notebook to write and run our code, and by default Jupyter Notebook uses our Home folder as its working directory. It is simplest, then, to put our filesystem in our Home folder. Create an empty folder in your Home folder, and call it 'file-looping'. This will be the folder that our program opens in step 1 above. In this folder put two empty text (.txt) files: these will be the files that our program will open and modify by inserting a sentence. You can call them and this folder whatever you like, but there are a couple of good principles for file naming which will make your life infinitely easier:

<li>1. Use descriptive and unique names</li>
<li>2. Avoid spaces. Use capitalisation or special characters to visually separate out words.</li>


We use descriptive and unique names so that we and the computer always know which files we want to work with. And we avoid spaces in our names because we want Python to be able to identify the files without issues. While an empty space is a Unicode character, it's better to avoid spaces. For this example I've named the two empty text files as 'loop-tutorial-document1.txt' and 'loop-tutorial-documentt2.txt'. Notice that we will also follow these principles when naming the program itself.

### Setting Up the Code Workspace
Open up a fresh Jupyter Notebook (refer to *lesson* for instructions on navigating Jypyter Notebooks). Then, in the first cell, then, import the os module: 

```python
import os
```
Hit 'run'. If your cursor moves to the next cell, then the code has run, and the module is imported and active in your workspace. Jupyter Notebooks lives in your home folder, so your script will be there. It's recommended that you save the notebook with a unique name and with no spaces, e.g., 'file-looping-script'. 
It's common practice to begin any program by importing/installing the necessary modules. 

Now we have:
 - Established our objectives
 - Designed the abstract program
 - Set up our filesystem
 - Set up our code workspace

 Now we can begin writing code!

 




 





