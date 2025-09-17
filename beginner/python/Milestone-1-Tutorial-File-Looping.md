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

<li>1. Identify the  with our documents</li>
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
The first thing to do is to determine where to put the files that you want the program to modify. We will be using Jupyter Notebooks to write and run our code, and by default a Jupyter Notebook uses our Home directory as its working directory. It is simplest, then, to put our filesystem in our Home directory. Create an empty folder in your Home directory, and call it 'file-looping'. This will be the folder that our program opens in step 1 above. In this folder put two empty text (.txt) files: these will be the files that our program will open and modify by inserting a sentence. You can call them and this folder whatever you like, but there are a couple of good principles for file naming which will make your life infinitely easier:

<li>1. Use descriptive and unique names</li>
<li>2. Avoid spaces. Use capitalisation or special characters to visually separate out words.</li>


We use descriptive and unique names so that we and the computer always know which files we want to work with. And we avoid spaces in our names because we want Python to be able to identify the files without issues. While an empty space is a Unicode character, it's better to avoid spaces. For this example I've named the two empty text files as 'loop-tutorial-document1.txt' and 'loop-tutorial-documentt2.txt'. Notice that we will also follow these principles when naming the program itself.

### Setting Up the Code Workspace
Open up a fresh Jupyter Notebook (refer to *lesson* for instructions on navigating Jypyter Notebooks). Then, in the first cell, then, import the os module: 

```python
import os
```
Hit 'run'. If your cursor moves to the next cell, then the code has run, and the module is imported and active in your workspace. Jupyter Notebooks lives in your Home directory, so your script will be there. It's recommended that you save the notebook with a unique name and with no spaces, e.g., 'file-looping-script'. It's common practice to begin any program by importing/installing the necessary modules. 
Now that you've opened up a notebook and put in a line of code, save the notebook. I suggest calling it something like 'file-looping-script'. This follows the naming principles we stated earlier.

Now we have:
 - Established our objectives
 - Designed the abstract program
 - Set up our filesystem
 - Set up our code workspace

 Now we can begin writing code!

## Phase 2: Writing the Function
We will now write the code for the function by moving along the steps of our program that we designed. In more complex programs we would not necessarily proceed in the same order as that listed in the program steps, but our program is very simple.

### Identifying Our Folder
Our first aim is to tell our program which folder in our Home directory to open and read. The 'os' module has a function called 'os.getcwd()'. Have a look in the Python documentation for this function. What does it do? 

We can see from the documentation that its function is to 'return a string representing the current working directory'. If we type it under our import command, it should return our Home directory (unless you have set Jupyter Notebooks to have a different default working directory):

```python
import os
os.getcwd()
```

If you remember the concept of variables from previous lessons, you may know that you can save the output of a function like os.getcwd() as a variable. When we do this, we give our code an easy address to our working directory, which we can invoke by just using the variable. Let's do this now:

```python
import os
os.getcwd()
currentworkingdirectory = os.getcwd()
print(currentworkingdirectory)
```
In this code, we assign os.getcwd() the name 'currentworkingdirectory'. When we print it, we should get our Home directory. This links the function of finding the working directory with the name 'currentworkingdirectory'. Now, any time we want the code to find the working directory, we just use this name. 
**Note**: you don't need the second line of your code now. Python knows what os.getcwd() is by default: we included it here as part of the learning process. So, we can safely delete it. Our code now looks like this:

```python
import os
currentworkingdirectory = os.getcwd()
print(currentworkingdirectory)
```
But all this does is select the place in our computer where we already are. We want to somehow tell the computer to move to our folder with our new documents in it. The 'os' module has another function which can help us: os.path.join(). If we look at the documentation, it tells us that this function will 'join one or more path segments intelligently'. Let us join the paths of our Home Directory and our desired folder:

```python
currentworkingdirectory = os.getcwd()
print(currentworkingdirectory)
targetdirectory = os.path.join(currentworkingdirectory, 'file-looping')
print(targetdirectory)
```
You can see from both print statements how the path is preserved. 
**Note:** You may have noticed that there is another function called os.chdir(), which will 'change the current working directory to path.' Why not use this? With os.chdir(), you fully move the entire program into the new directory, and lose the information about where you moved from. os.path.join() preserves the entire path you want to travel (from Home directory to specific folder), and this is easier to follow in more complex programs. Both do what we want, but many programmers prefer os.path.join(). We will stick with this for now!

Now we have a variable called 'targetdirectory' which preserves the path from our Home Directory to our 'file-looping' folder. Let's test things out and see if Python can identify the files within our folder. We use the function os.scandir(), the name of which is pretty self-explanatory: it scans the folder to determine what is in it. This will involve writing our first 'for' loop. After the 'print(targetdirectory)' line, put the following code:

```python
with os.scandir(targetdirectory) as currentfiles:
    for file in currentfiles:
        print(file.name)
```
Notice the first line here, with the 'with...as' statement. This is a way to create an object, which we call 'currentfiles', that is scanned by os.scandir(). Then we create the first level of the loop with our colon (':') after the end of the first line. This tells Python to open targetdirectory, scan the currentfiles, and then do a specific task. The next level of our loop, 'for file in currentfiles:' tells Python to iterate over every file in our folder, and then the final line tells Python to print the file name for us. Run this code, and if you get a list of the files we named earlier, then the program is working!

 





