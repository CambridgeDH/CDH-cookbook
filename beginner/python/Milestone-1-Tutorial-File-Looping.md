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
Since we are writing a program from beginning to end, it is important to have a clear picture of each of the program's steps. Developers often write these externally for reference, especially if their programs are complex and involve many s. It is good to get into this habit early in your journey of learning to code.

For each function, we list out the actions that that  will take:

<li>1. Identify and open the folder with our documents</li>
<li>2. Identify the documents inside the folder</li>
<li>3. Open a document</li>
<li>4. Insert a sentence inside the document</li>
<li>5. Save and close the document</li>
<li>6. Repeat steps 2-5 for the next document</li>
<li>7. Terminate when there are no more documents to open and edit</li>

We can break up our actions into specific functions. This will help organise the code. Actions 1-3 will be our first function, 'read_files'. Actions 4-6 will be our second function: 'write_content'.
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

### Identifying and Opening Our Folder
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
Notice the first line here, with the 'with...as' statement. This is a way to create an object, which we call 'currentfiles', that is scanned by os.scandir(). Then we create the first level of the loop with our colon (':') after the end of the first line. This tells Python to open targetdirectory, scan the currentfiles, and then do a specific task. The next level of our loop, 'for file in currentfiles:' tells Python to iterate over every file in our folder, and then the final line tells Python to print the file name for us. Run this code, and if you get a list of the files we named earlier, then the program is working! Note that it will print the filesnames in a random order unless we sort them, which we won't bother with for now.

## Writing the File Modification Loops
Currently, our code can identify the folder that we want and can identify the names of the files within that folder. We now want to write loops that will open and read a file, insert a sentence, save the file and then close the file. These loops will perform this task on all files within the folder.  

### Function 1: Opening and Reading Each File
Our current code is:

```python
with os.scandir(targetdirectory) as currentfiles:
    for file in currentfiles:
        print(file.name)
```
Some operating systems, such as Mac or Linux, often have hidden files as a normal part of the system. When writing code, we often have to exclude these files from being read by our code. There are multiple ways to do this, but since we only have two text (.txt) files in our folder, we can simply tell Python to only deal with files that have names ending in .txt:

```python
with os.scandir(targetdirectory) as currentfiles:
    for file in files:
        if file.name.endswith('.txt'): 
            print(file.name)
```
A handy thing about Python is that this code is pretty self-explanatory. It only prints the names of the files ending with .txt. If you saw other files earlier in this tutorial, (such as DS_Store), they will now be ignored by our program. This is a feature of programming that people often find distracting, but it is necessary for properly working code.
Next, we want to open up each file in the directory, and print its contents (if any). Our files are currently empty, but we can still run the same code as if they had contents:

```python
with os.scandir(targetdirectory) as currentfiles:
    for file in currentfiles:
        if file.name.endswith('.txt'): 
            print(file.name)
            with open(file.path, 'r') as currentfile:
                print(currentfile.read())
```
We have added two new lines to the end of our code. Let's look at them one-by-one:

``` python
with open(file.path, 'r') as currentfile:
```
This line starts another loop within our current loop. Before it, we just looped through each file and printed its name. Now we want to loop through them again and open them. Notice that we have another 'with...as' structure. This is handy because with this structure Python will open and then close the file. 
Inside the parentheses are the specific instructions for the 'open' command. We have file.path, which is the like the 'house number' of each file in the directory. We also have 'r'. This is known as a file mode, and it tells Python to open the file in order to 'read' it only, and not do anything else. Notice that we call the whole thing 'currentfile'. We looped through all files as currentfiles (plural), and now are going to each one as currentfile (singular). This is stylistic. You could use any word for these variables. It's best to use words that make good sense to humans who may read your code later!
Finally, as we are beginning a loop, we end the line with a colon (:).

Next, we have:

```python
print(currentfile.read())
```
This line is indented to tell Python that it is within the loop that is reading each individual file. It prints the content of that file. We spell out 'read' here because it is different from a file mode: it is actually reading the file that is already opening and printing the contents.
If there are no contents, the result will just be the file names printed. If this happens and no error message occurs, then your code is clean and you can move to the next step.

Now, we want to make this block of code its own function. Why? Because it performs a logical, standalone task. It goes into our chosen folder, confirms the files that we want are present, and then loops through every file, reads the content, and then closes the file. 
It is simple to make a function. We simply do this:

```python
def read_files():
    with os.scandir(targetdirectory) as currentfiles:
        for file in currentfiles:
            if file.name.endswith('.txt'): 
                print(file.name)
                with open(file.path, 'r') as currentfile:
                    print(currentfile.read())
read_files()
```
**Notice**: that when we add 'def read_files():, we indented everything after it by one tab. This indentation tells Python that everything after def read_files(): belongs to read_files only. If you do not indent correctly, your code will not work.
Notice our last line, which is just 'read_files()'. This line tells Python to run the function that we just wrote. Your output should be the list of the files within your folder. Since we have not put any content in the files, the last line, 'print(currentfile.read()) will return empty lines between our file names.

### Inserting a Sentence in Each Document
Right now all our code does is open and close each text document within our folder, and read any contents in those documents. We now need to write the function that tells Python to insert a sentence into each document. A built-in Python command, .write, will insert a string of text into an empty text file. This function will look very similar to the one we just wrote, so let's look at it in full:

```python
def write_content():
    with os.scandir(targetdirectory) as currentfiles:
        for file in currentfiles: 
            if file.name.endswith('.txt'):
                with open(file.path, 'r+') as currentfile:
                    currentfile.write('We are putting this sentence in our files')
write_content()
```
Line 1 of this function defines its name, write_content, and specifies that anything after it which is indented is a part of this function. Next, we have our os.scandir command which is still reading our target directory and the current files in it. On lines 3 and 4 we have our for loop, which tells Python to iterate through every file in our target directory (named 'currentfiles'). If the file is a text (.txt) file, Python is instructed to open it. The next level of the loop, lines 5-6, is a bit different from our previous function. Notice that 'r' now is 'r+'. This indicates Python to open the file in such a way that it can both read **and** modify the file. To write something into our files, we put it in quotes inside the curved brackets after our .write command. **Note that this loop will insert the same phrase into every file in our directory.**
At the end of the function, we 'call' it by 'write_content()'. This tells Python to run the function we just described. 

Run this code and then check the output by opening up one of your files. Is the sentence in it? If not, check that you have the correct level of indentation for every line; this is one of the most common errors in Python.

### Getting a Description of File Contents
We could stop here: we have functioning code that goes into a specific directory, tells us what is in that directory, and then opens up each file and modifies it with a sentence. You can already see the potential uses of code like this. But we can do even more! Let's say we have a lot of files in which we want to insert our sentence. It would be tedious to go in and check each one after, to ensure that our sentence is present. Fortunately, with a final loop, we can instruct Python to print whatever is now in our files.

```Python
def read_files():
    with os.scandir(targetdirectory) as currentfiles:
        for file in currentfiles:
            if file.name.endswith('.txt'):
                with open(file.path, 'r') as currentfile:
                    print(file.name)
                    print(currentfile.read())
read_files()
```
This function is almost the same as our first; the only difference is that at the end, we have added an extra print line. This line employs the .read Python command. Notice that we keep the curved brackets after .read empty; this is because we just want Python to read the entire contents. For example, if we had a long paragraph, we could limit it to the first 10 characters, by putting '10' into those brackets. 

The output for this should be that we should get a list of our two documents' names and after each name, the sentence we put in. Again, check the indentation if this is not working.

## The Entire Picture
Now that we have our three functions, let's look at them all together:

```python
import os
currentworkingdirectory = os.getcwd()
print(currentworkingdirectory)

targetdirectory = os.path.join(currentworkingdirectory, 'file-looping')
print(targetdirectory)

def show_files():
    with os.scandir(targetdirectory) as currentfiles:
        for file in currentfiles:
            if file.name.endswith('.txt'): 
                print(file.name)
show_files()

def write_content():
    with os.scandir(targetdirectory) as currentfiles:
        for file in currentfiles: 
            if file.name.endswith('.txt'):
                with open(file.path, 'r+') as currentfile:
                    currentfile.write('We are putting this sentence in our files')
write_content()

def read_files():
    with os.scandir(targetdirectory) as currentfiles:
        for file in currentfiles:
            if file.name.endswith('.txt'):
                with open(file.path, 'r') as currentfile:
                    print('This is my file:', file.name)
                    print(currentfile.read())
read_files()
```
Pause and read the code for a moment. What do you observe about it? If you run it in full, consider the output. What does it look like? 

If you are observant, you will notice a few things that seem 'odd' about our code. It runs, of course, which is important! But notice:

<li>How repetitive it is. We call os.scandir() multiple times. We specify only .txt files multiple times. The difference between show_files() and read_files() is only one print statement.</li>
<li>The output is correct but a bit difficult to read. The data just appear in order, but it is hard to know what command caused it just by reading.</li>

There are also good things about our code. In particular:
<li>It is 'modular'. That means each function stands on its own. It can run without any of the other functions.</li>
<li>The names of our variables are clear, and flow like natural language</li>
<li>The function names are descriptive, short, and appropriate.</li>

If you are noticing these things, congratulations! You are developing an eye for good code. High-quality Python functions should be as independent as possible. Ideally, each should do a single, specific task, and we want to minimise one function being dependent upon another (though sometimes this is unavoidable). Python code should be easy to read for someone who hasn't written it. This means using descriptive and sensible variable names. 

The issues we see are violations of the 'DRY' principle: 'Don't Repeat Yourself'. Professional developers are very careful to adhere to this principle, and there are other ways to write this program that involve no repetition whatsoever. However, repetition for beginners can actually be useful, because each function is fully standalone with this repetition. You can take it and use it in other programs without changing much. Repeating essential elements helps you learn what good code needs to run. 

Often, programmers will write out a repetitive program like this, and then through a process called **refactoring** will edit their code to be more elegant and streamlined. This is not something you need to worry about unless you wish to become a professional, or unless your code is running very slowly. But it is important to know that refactoring is what we call the code editing process.

There is one thing we can do right now, however, to make the output a little easier to read. In any of the print statements, you can follow this format to clarify what is being printed:

```python
print ('Message to self', printedthing)
```
So, for the very first thing we print, the current working directory, we could write:

```python
print('This is the current working directory:', currentworkingdirectory)
```
Run that line as the third line of this program. You will fine that your note to yourself gets printed, and then the current working directory is printed after it. You can do this for any print statement to make it clearer!

## Conclusion
Congratulations: you have completed your first full Python program! By importing modules and writing a few 'for' loops, you were able to enter directories and modify files without touching them yourself. You also got to see how a programmer thinks about putting together code to achieve a task. It is often by following tutorials like these, which force you to write your own program, that you learn the most about coding. If you want to learn to do even more, you are encouraged to continue to the next lessons of this course. 





