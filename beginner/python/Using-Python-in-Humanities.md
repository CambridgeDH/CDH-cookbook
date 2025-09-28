# Using Python to Support Humanities Research

## Contents

## Overview
Welcome to the final tutorial lesson of this short course. This lesson focuses more on the practicalities of using Python to support and communicate your research, rather than on the act of writing code. In this lesson we will cover some of the fundamental things that should inform your practice as you use code in your research, from data analysis and study design to data visualisation and describing your results to others. 

In the previous lessons you have first learned meta-skills around Python programming:
<li>What the difference is between coding and programming.</li>
<li>What Python is, how to install and begin using it, and how to find resources</li>
<li>Reasons for using code in a Humanities project, what 'data' looks like in the Humanities, and how to approach data-driven research in the Humanities</li>
<li></li>

You have also learned the basics necessary to understand how Python works:
<li>Loading data, declaring variables, naming conventions</li>
<li>Navigational basics: commenting, zero-indexing, print statements, various Python operators</li>
<li>How to call a module function to analyse your variables</li>

This course has covered the following fundamental programming skills:
<li>Data types and how to declare them</li>
<li>Functions: how they are built and how to declare them</li>
<li>Arguments, parameters, conditionals</li>
<li>Loops: the for loop, while loop, nested loops</li>
<li>Different types of functions</li>
<li>Basics of Object-Oriented Programming</li>
<li>File management</li>

This lesson is similar to the earlier Milestone Tutorial Lesson in that we will be walking through an analytical process together. The goal of today's lesson is to explore what it looks like to think through a research question using some texts, apply some code to help answer that question using the skills we have learned, and then assess the results of our analysis. This is meant to help you think through how you might look for digital tools, using Python, that can further your own research project.

## The Research Question
Let's construct a hypothetical research situation, where we have a group of texts written by some famous authors. We want to use the Python module 'textblob' to perform some very basic Natural Language Processing tasks on these texts (do not worry; full-level NLP is outisde of the scope of this course!). Let us assume for the moment that we do not know what the module is capable of doing - before continuing further in the lesson, go read the introductory material about the textblob Python module. It is good to solidly establish the habit of reading the documentation from the very start.

Once you have done this, have any natural research questions come to mind? Often we already know what kinds of questions we want to ask of our data; in an artificial situation like this, it is understandable that questions may not come so easily. Let's say that we have four passages from famous literary sources, and we want to do some basic text analysis on them to compare styles of authorhship.

### Setting Up Files

Take the file structure you created for the Milestone Lesson.  Go to the folder where your text files are. In that folder, create eight plain text files with a couple of paragraphs from some famous works. [or INSERT LINK TO DATASET HERE]. 

The first thing to know is that you should name your file names with the following parameters:
<li>Descriptive names</li>
<li>No spaces: do something like, no_spaces, or nospaces, or NoSpaces</li>
<li>Unique names, so the computer can tell them each apart.</li>

Once you have done this you will have some analysable data with which to work.

### Setting Up Code Workspace
Now open a fresh Jupyter notebook, and reusing the code from the Milestone lesson, set up your workspace:
```python
import os
currentworkingdirectory = os.getcwd()
print('This is the current working directory:', currentworkingdirectory)

targetdirectory = os.path.join(currentworkingdirectory, 'file-looping')
print('This is the target directory:', targetdirectory)
```
This sets the location on your computer where your files are as the location that Python is reading. 

Now you want to make sure you have textblob installed and active:

```python
pip install textblob
from textblob import TextBlob
```

