<link rel="stylesheet" href="../../cookbook.css">
# Concluding Lesson: First Steps for Coding in Python

<p class="previous-next-lesson"><a href="toc.html">^ Main contents</a></p>
## Contents
- [Overview](#overview)
- [Developing from Here](#developing-from-here)
- [What to Expect](#what-to-expect)

## Overview
This short course has covered the fundamentals of coding in Python. Here is a recap of what we covered. 
Early on we covered important meta-skills around Python programming:

<ul>
<li>What the difference is between coding and programming.</li>
<li>What Python is, how to install and begin using it</li>
<li>Reasons for using code in a Humanities project, what Humanities 'data' is, and how to approach data-driven research in the Humanities</li>
<li>How to search for resources, support, and documentation</li>
</ul>

You have also learned the basics necessary to understand how Python works:

<ul>
<li>Handling data: loading data into the workspace, declaring variables, understanding naming conventions</li>
<li>Navigational basics: commenting, zero-indexing, print statements, various Python operators</li>
<li>Taking actions: How to call a module function to analyse your variables</li>
</ul>

This course then covered the following fundamental programming skills:

<ul>
<li>Data types: what they are and how to declare them</li>
<li>Functions: how they are built and how to declare them</li>
<li>Arguments, parameters, and conditionals</li>
<li>Loops: the for loop, while loop, and nested loops</li>
<li>Different types of functions (built-in, user-defined, with *args and *kwargs)</li>
<li>Basics of Object-Oriented Programming</li>
<li>File management</li>
</ul>

Finally, you have written two small programs:

<ul>
<li>A basic file-looping program to help you practice mastering loops (which are fundamental).</li>
<li>A beginning-to-end data analysis program which saves the results in a separate file on your computer.</li>
</ul>

All of these skills are transferable and extendable beyond the bounds of this lesson. They give you a foundation not just for working in Python, but for considering how code can be used to support various Humanities research and teaching endeavours.

[Back to table of contents](#contents)

## Developing from Here
It is important to state outright what you can accomplish with this foundation, so that you can understand your skills and take informed steps forward. You should now be able to:

<ul>
<li>Research Python software (modules) online to see if it could benefit your research</li>
<li>Find documentation and support to begin using new modules</li>
<li>Navigate your computer's directories without too much struggle</li>
<li>Create, modify, and save basic text files</li>
<li>Read other people's Python code. You will not understand everything, but you now know what Classes, Objects, and Attributes are. That gives you the scaffolding necessary to begin studying more complex programs, use more advanced tutorials, and understand explanations of someone's code.</li>
<li>Write small yet functional Python scripts yourself</li>
<li>Know enough about Python's organisation and the vocabulary we use to discuss Python to begin 'thinking like a programmer' in a general sense.</li>
<li>Troubleshoot simple syntax errors and interpret error messages</li>
</ul>

So what is the next appropriate step? That is dependent upon your goals. If the content in this course make sense to you and you could complete the exercises independently, you are ready for an intermediate level course. If basic file handling is all you want to do, then you will only need to research some extra commands that we did not have the space to cover in this course. If you want to begin rightaway with a field-specific module you have found, you are certainly equipped with the basics.

[Back to table of contents](#contents)

## What to Expect
Let's take each of these paths (intermediate courses, more advanced file handling, and field-specific modules) in turn:

### Intermediate Level Courses
There are many, many Python courses online, of varying costs and utility. The vast majority are geared toward STEM scientists rather than researchers in the Humanities. Since this introductory course was tailored for Humanities researchers, you have had the benefit of becoming acquainted with Python without this STEM overlay. However you may need to work with this STEM overlay in intermediate and advanced courses in order  make full use of the many Python modules that have been developed for Humanities research. One way to make this easier is to approach those classes with a specific goal or project in mind. Having a concrete goal or specified outcome helps you to sift through the course material to find what is useful to you. One of the most difficult parts of learning to code is getting the basics down; gaining further skills is less of a learning curve, and they tend to compound over time.

Another possibility is that you want to do some other more hardcore data analytics/statistics. In that case, you are encouraged to take the Introduction to R course which this Cookbook hosts as well. While there are powerful statistical modules in Python, R is a programming language designed specifically for statistics. Its syntax is streamlined for data analysis, machine learning, and visualisation -- with some modules practically smoother to use than Python. 

### File Handling Commands
We covered some fundamental file handling commands, such as:


<ul>
<li>Navigating directories and finding the current working directory</li>
<li>Opening files</li>
<li>Reading the contents of files</li>
<li>Copying files and appending new information to existing files</li>
<li>Saving files in a specified location</li>
</ul>

The next steps would be to identify the specific file types with which you need to work, and go read up on Python modules that create and save files as those file types. [pypdf](https://pypdf.readthedocs.io/en/stable/) is one such one for PDF files; there are counterparts for spreadsheets, images, etc.

### Field-Specific Modules
If you have a particular module that you want to use, you can now try reading the documentation in more depth. The best place to start is to go to the module's GitHub repository (if one exists, though it's unusual for one not to exist). First, look at the README file. These give essential details about the software and how to use it. You can also search online for the module name and potentially find tutorials and .io websites that give more step-by-step information. If you are needing to use a specific module, a logical step here would be to contact the developer as well - especially in many Digital Humanities spaces, developers are happy to support users in learning how to use their software. Do not be shy to approach them and ask them questions or for directions to find tailored support.

### Getting Stuck and Getting Help
As you progress along your journey of learning to code, it is inevitable that you will get stuck. You will feel like a task is impossible, or a problem is unsolvable. Those who progress utilise a few extremely practical strategies when this happens:

<ul>
<li> Take breaks. Go for walks away from a computer screen, or talk the issue over with a friend in your own words. Often getting stuck staring at a screen with a ton of error messages can be hypnotic, but the moment you walk away or change thinking mediums, your brain switches gears and often the solution becomes clear.</li>
<li>Find a mentor. One of the best ways to develop your coding skills is to force yourself to work on a specific project, and only turn to someone for help when you absolutely cannot proceed. This is the way that many very successful self-taught programmers learned. They worked until they could no longer find a way forward at all, which brought them to the very cusp of their abilities, and then they asked for help from a friendly mentor. This then extended their skillset. Encountering and overcoming the block with the mentor is perhaps the richest learning experience one can have.</li>
<li>Utilise forums. Either your problem will have been posted before, in which case, the answer is there ready for you to find it. Or, you will post a new problem that can help someone else in the future. Either way, everyone wins.</li>
<li>If in doubt, re-read the documentation. Many problems come from skimming or avoiding reading the documentation. </li>
<li>Use AI tools with care. Professional programmers use AI, but for very specific reasons and in boundaried ways. **Continue edits here**
  
  
  Having a language model write code for you before you know how to code yourself is problematic, because in order to use the LLM effectively, you  need to know how to design the program, think through the edge cases, and understand the code that the LLM provides you. If you cannot do these things at a professional level, you will inevitably get code from the LLM that has problems, does not achieve what you ultimately want, or is outdated and less useful to others. At this stage in your learning LLMs are best used to help you understand small details about new code that you encounter. For example, asking an LLM 'explain everything in this line of code' can be a powerful way to extend your knowledge. </li>
<li>Search your error messages on the internet. This is the fastest way to figure out how to debug code. You can also ask ChatGPT what the error means, but often, people have written more in-depth information on forums about specific error messages. </li>
</ul>

Regardless, do not be discouraged when you hit roadblocks. They are inevitable, and part of the coding learning process. Be encouraged that you are not alone; someone else has encountered the same error messages you have, otherwise, the error messages would not exist to begin with!

### The Rest of this Cookbook
This Cookbook is meant to link a wide variety of methods using programming languages such as R and Python. If you want to continue learning coding methods for Humanities research, this Cookbook is constantly growing with new methods that world-class researchers have developed and taught. Working through these lessons will sharpen and extend your newfound skilset.

<p class="credits">Written by Estara Arrant, 2025-04-16<br />Licence: <a href="https://creativecommons.org/licenses/by-sa/4.0/">CC BY-SA 4.0</a></p>

<p class="previous-next-lesson"><a href="lesson8-capstone-using-python-in-humanities.html">&lt; Previous lesson</a></p>
