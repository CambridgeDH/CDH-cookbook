<link rel="stylesheet" href="../../cookbook.css">
# Concluding Lesson: First Steps for Coding in Python

<p class="previous-next-lesson"><a href="toc.html">^ Main contents</a></p>
## Contents
- [Overview](#overview)
- [Developing from Here](#developing-from-here)
- [What to Expect](#what-to-expect)
- [Getting Stuck and Getting Help](#getting-stuck-and-getting-help)
- [The Rest of this Cookbook](#the-rest-of-this-cookbook)

## Overview
This short course has covered the fundamentals of coding in Python. Here is a recap of what we covered. 
First you learned some important meta-skills and concepts around Python programming:

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
<li>Different types of functions (built-in, user-defined)</li>
<li>Basics of Object-Oriented Programming</li>
<li>File management</li>
</ul>

Finally, you have written two small programs as part of the coursework:

<ul>
<li>A basic file-looping program to help you practice mastering loops (which are fundamental).</li>
<li>A beginning-to-end data analysis program which saves the results in a separate file on your computer.</li>
</ul>

All of these skills are transferable and extendable beyond this course. They give you a foundation both for future work in Python, and using code to support various Humanities research and teaching endeavours.

[Back to table of contents](#contents)

## Developing from Here
Let's take a quick look at what you can now accomplish with this foundation; this will help you understand your abilities and plan your next steps. 
After this course you should now be able to:

<ul>
<li>Effectively research Python software (modules) online to identify what is useful for your work </li>
<li>Find documentation and support to begin working with new modules</li>
<li>Use Python to efficiently navigate your computer's directories </li>
<li>Automatically create, modify, and save basic text files using Python</li>
<li>Read other people's Python code. You will not understand everything, but you now know what Classes, Objects, and Attributes are. That gives you the scaffolding necessary to begin studying more complex programs, use more advanced tutorials, and understand explanations of someone's code.</li>
<li>Write small yet functional Python scripts yourself</li>
<li>Know enough about Python's organisation and the vocabulary we use to discuss Python to begin 'thinking like a programmer' in a general sense.</li>
<li>Troubleshoot simple syntax errors and interpret error messages (or find resources to help you interpret them)</li>
</ul>

The next step for you depends on your goals. If the content in this course make sense to you and you could complete the exercises independently, you are ready for an intermediate level course. If basic file handling is all you want to do, then you will only need to research some extra commands that we did not have the space to cover in this course. If you want to begin directly working with a field-specific module you have found, you are certainly equipped with the basics, but will need to find further resources as you progress. 

Ultimately it is important to remember that getting the basics down is one of the steepest learning curves when becoming a coder/programmer. Typically, after overcoming this first hurdle, people find they gain momentum in acquiring new skills, and their abilities compound over time.

[Back to table of contents](#contents)

## What to Expect
Let's look at each of these paths (intermediate courses, more advanced file handling, and field-specific modules) in turn to see what you might encounter:

### Intermediate Level Courses
There are many, many Python courses online, of varying costs and utility. The vast majority are geared toward STEM scientists rather than researchers in the Humanities. Since this introductory course was tailored for Humanities researchers, you have had the benefit of becoming acquainted with Python without this STEM overlay. However you may need to work with this STEM overlay in intermediate and advanced courses in order  make full use of various modules. It is much easier and more effective to approach those classes with a specific goal or project in mind, because it will give you the structure needed to  sift through the course material for what is useful and what is not. 

Another possibility is that you want to do some other more hardcore data analytics/statistics. In that case, you are encouraged to take the Introduction to R course which this Cookbook hosts as well. While there are powerful statistical modules in Python, R is a programming language designed specifically for statistics. Its syntax is streamlined for data analysis, machine learning, and visualisation and some find that if those are their main tasks, it is a more effective language.

### File Handling Commands
In Lesson 7 we covered some fundamental file handling commands, such as:


<ul>
<li>Navigating directories and finding the current working directory</li>
<li>Opening files</li>
<li>Reading the contents of files</li>
<li>Copying files and appending new information to existing files</li>
<li>Saving files in a specified location</li>
</ul>

The next steps would be to identify the specific file types with which you need to work, and go read up on Python modules that create and save files as those file types. For example, if you need to work with PDF files, then [pypdf](https://pypdf.readthedocs.io/en/stable/) is a good module to research and use. There are many counterparts for other file types like spreadsheets, images, etc.

### Field-Specific Modules
If you have a particular module that you want to use, you can now try reading the documentation in more depth. The best place to start is to go to the module's GitHub repository (if one exists, though it's unusual for one not to exist). First, look at the README file. These give essential details about the software and how to use it. You can also search online for the module name and potentially find tutorials  that give more step-by-step information. If you are needing to use a specific module, a logical step here would be to contact the developer as well - especially in many Digital Humanities spaces, developers are happy to support users in learning how to use their software. People who build open-source software are delighted that others want to use it, so do not be shy to approach them for support!

[Back to table of contents](#contents)

## Getting Stuck and Getting Help
As you progress along the journey of learning to code, you will get stuck. You will feel like a task is impossible, or a problem is unsolvable. This is normal (all of us have been there!) and not a sign that you are bad at coding; rather it's a signal that you are building your abilities. Many who have struggled on this journey have developed practical strategies to help them through it:

<ul>
<li> Take breaks. Go for walks away from a computer screen, or talk the issue over with a friend or mentor in your own words. Getting stuck staring at a screen with a ton of error messages can be hypnotic, and many find it difficult to step away. Resist the urge to dig your heels in; the moment you walk away or change thinking mediums, your brain switches gears and often the solution (or a new thing to try) comes into view.</li>
<li>Find a mentor. One of the best ways to develop your coding skills is to force yourself to work on a specific project, and only turn to someone for help when you absolutely cannot proceed. This is the way that many successful self-taught programmers learned. They worked until they could no longer find a way forward at all, which brought them to the very cusp of their abilities, and then they asked for help from a friendly mentor. This then extended their skillset. Encountering a challenge, pushing it to the edge, and then overcoming it with a mentor is one of the richest learning experiences!</li>
<li>Utilise forums. Either your problem will have been posted before, in which case, the answer is there ready for you to find it. Or, you will post a new problem that can help someone else in the future. Either way, everyone wins.</li>
<li>If in doubt, re-read the documentation. Many problems come from skimming or avoiding reading the documentation. Yes, it is boring. Yes, you will want to do anything else. But it can save you headaches! </li>
</ul>

### A Note on AI
In the first lesson of this course we covered the use of AI and commercial LLMs in learning to code. Now that you have some foundational knowledge, what should your relationship to these tools be? Going forward, the principles we discussed in Lesson 1 are generally the same. However, it is strongly recommended that as you grow your skills, if you do use AI, you operate on the principle of using AI/LLMs as tools that support your efforts rather than replacing them. Centre yourself at the core of your coding or programming project, rather than allowing an LLM to do the creative or analytical work for you. Of course, you always should consider the option of not using these tools; while their use has become nearly ubiquitous in many software areas, and while they are certainly valuable resources, they are not strictly necessary for one to write good code that works well for their project.


[Back to table of contents](#contents)

## The Rest of this Cookbook
This Cookbook is meant to link a wide variety of methods using programming languages such as R and Python. If you want to continue learning coding methods for Humanities research, this Cookbook is constantly growing with new methods that world-class researchers in the Humanities, Computer Science, and Data Science have developed and taught. Working through these lessons will sharpen and extend your newfound skilset.

[Back to table of contents](#contents)

<p class="credits">Written by Estara Arrant, 2025-04-16<br />Licence: <a href="https://creativecommons.org/licenses/by-sa/4.0/">CC BY-SA 4.0</a></p>

<p class="previous-next-lesson"><a href="lesson8-capstone-using-python-in-humanities.html">&lt; Previous lesson</a></p>
