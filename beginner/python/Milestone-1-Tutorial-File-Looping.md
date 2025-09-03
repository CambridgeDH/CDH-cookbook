# Milestone 1 Tutorial: A File Looping Program

In the past three lessons you have learned the essential foundations one must know before one can begin coding. However, you have also learned a few fundamental skills which together enable to you write your first Python program. This tutorial will help you put these skills to use by teaching you how to write the correct commands in the proper order for looping through and editing some files.

## The Goal
Before you begin to write any sort of code, it is essential that your aims and objectives are clear to you. By taking a few minutes at the start of any project to clarify exactly what it is that you want to achieve and to gather the tools you need to achieve it, you save yourself potentially hours of stress caused by attempting to write a program without knowing the path forward. It is good practice to always state somewhere what you are doing, how you are doing it, and why.

### What We are Doing
Today we will be writing a program in Python that will go into a file directory, open and read each of the files in that directory, make specific changes to those files, and close them. As this is a repetitive task, we will be writing our code in the form of a 'for loop'.

### How We Will Do This
This is a simple program that uses the Python module os. [Here](https://docs.python.org/3/library/os.html) is a link to the official Python documentation on this module. In this link you will see many headings in bold that look like: os.chdir(), osgetcwd(), etc. These are the specific functions of the module (refer to Lesson 1 for an explanation of the layers of Python code; we used the metaphor of University Libraries) 
