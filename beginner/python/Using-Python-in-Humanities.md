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

The steps which we will take are:
<li>Devising a clear and answerable question</li>
<li>Gathering a concise dataset</li>
<li>Using Python to navigate the files in our dataset</li>
<li>Writing functions to perform certain analytical tasks on the data</li>
<li>Saving the results of the analysis in a new folder</li>
<li>Interpreting and communicating Python-driven research to others</li>


## The Research Question
Let's construct a hypothetical research situation, where we have a group of texts written by some famous authors. We want to use the Python module 'textblob' to perform some very basic Natural Language Processing tasks on these texts (do not worry; full-level NLP is outisde of the scope of this course!). Let us assume for the moment that we do not know what the module is capable of doing - before continuing further in the lesson, go read the introductory material about the textblob Python module. It is good to solidly establish the habit of reading the documentation from the very start.

Once you have done this, have any natural research questions come to mind? 

[Hidden Answer] Let's say that we have eight passages from famous literary sources, and we want to do some basic text analysis on them to compare styles of authorhship as shown through sentiment analysis (the tone of each text) and the density of noun phrases in each text (how descriptive the texts are).

### Setting Up Files

  Go to the folder where you put your text files for the Milestone Lesson. In that folder, replace any files with eight plain new text files with a couple of paragraphs from some famous works. [or INSERT LINK TO DATASET HERE]. 

The first thing to know is that you should name your file names with the following parameters:
<li>Descriptive names</li>
<li>No spaces: do something like 'no_spaces', or 'nospaces', or 'NoSpaces'</li>
<li>Unique names, so the computer can tell them each apart.</li>

Once you have done this you will have some analysable data with which to work.

### Setting Up Code Workspace
Now open a fresh Jupyter notebook and set up your workspace. Check what your current working directory is, and then build a path to the directory where your files are.

[Hidden Answer]

```python
import os
currentworkingdirectory = os.getcwd()
print('This is the current working directory:', currentworkingdirectory)

targetdirectory = os.path.join(currentworkingdirectory, 'file-looping')
print('This is the target directory:', targetdirectory)
```
This sets the location on your computer where your files are as the location that Python is reading. 

You will now want to have a safe place to save any new files you create during analysis. Try doing that. If you are unsure, search online before peeking at the answer.

[Hidden Answer]
```python
results_dir = os.path.join(currentworkingdirectory, "analysis-results")
os.makedirs(results_dir, exist_ok=True)
print(results_dir)
```
Now you have a working directory populated with your files, and an empty directory ready to receive new files created by the analysis.

Finally, you want to ensure you have the up to date version of textblob. Go ahead and install it inside Jupyter or import it (if it is already installed).

[Hidden Answer]
```python
pip install textblob
from textblob import TextBlob
```
Note that we imported only the class TextBlob from the module. This is optional; you could import the entire module if you wanted. 
! A special note: the sentiment analysis functionality in textblob only works with some additional installations. Here they are below:

```python
!python -m textblob.download_corpora
```

While our texts are in individual files, it can be easier to analyse them if we bring the raw contents into the codespace. Create a new list called 'texts' and tell Python to store the text data in that list.

[Hidden answer]
```python
# Get list of text files (and ignore other file types)
files = [f for f in os.listdir(targetdirectory)
         if f.lower().endswith(".txt") and not f.startswith(".")]

# Read them in
texts = []
for filename in files:
    filepath = os.path.join(targetdirectory, filename)
    with open(filepath, "r", encoding="utf-8") as f:
        content = f.read()
    texts.append((filename, content))

print(f"Loaded {len(texts)} files.")
print(texts)
```
The output should be all of the contents of your text files. Sometimes you may run into problems if your file is not saved in UTF-8. If that happens, re-save the file as UTF-8 and try again. We won’t go into encodings here.

### Performing the Analysis
Now that our texts are in a directory and we have the required modules, we can begin the actual analytical step. It is strongly recommended that you go read a little on sentiment analysis and noun phrase density if you are not already familiar with these concepts. 

Write a function called 'text_analysis' that takes two arguments — the filename and the content. Inside the function, create a TextBlob from the content and return a summary that includes: (a) sentiment polarity, (b) sentiment subjectivity, and (c) the noun phrases TextBlob found. If you are unsure how to do this, look at the documentation before looking up the lesson's answer.

[Hidden Answer]
def text_analysis(filename, content):
    # Create a TextBlob object
    blob = TextBlob(content)
    
    # Extract sentiment
    polarity = blob.sentiment.polarity
    subjectivity = blob.sentiment.subjectivity
    
    # Extract noun phrases
    nouns = blob.noun_phrases
    
    # Return results as a dictionary
    return {
        'filename': filename,
        'polarity': polarity,
        'subjectivity': subjectivity,
        'noun_phrases': nouns
    }

sample_filename, sample_content = texts[0]
result = analyze_text(sample_filename, sample_content)
print(result)
```
You should get a result that looks somewhat like (with the details different depending on text):
"{'filename': 'oldmantext.txt', 'polarity': -0.04283380018674137, 'subjectivity': 0.2992763772175537, 'noun_phrases': WordList(['mixed-up whiskers', '’ t', 'man ’ s', 'body ’ s flesh crawl –', 'clothes –', 't ’', 'floor –', 'old black slouch'])}"

**Ensure you understand the code in the answer before continuing**






