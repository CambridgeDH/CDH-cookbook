<link rel="stylesheet" href="../../cookbook.css">
# Lesson 8: Capstone: Using Python in Humanities Research 

<p class="previous-next-lesson"><a href="toc.html">^ Main contents</a></p>
## Contents

- [The Research Question](#the-research-question)
- [Conclusions](#conclusions)

## Overview
Welcome to the capstone tutorial lesson of this short course. Here we will focus specifically on a beginning-to-end workflow for using Python to conduct a small sample research project and produce a visualisation of the results. This lesson is similar to the earlier Milestone Tutorial Lesson in that we will be walking through an analytical process together. Our goal is to explore thinking through a research question about some texts, use our newfound skill sto write some code to help answer that question, and then assess the results and make them visible to others. This limited exercise is an example of a code-driven Humanities research project in miniature form. 

These are the steps to take:

<ul>
<li>Devise a clear and answerable question</li>
<li>Gather a concise dataset</li>
<li>Use Python to navigate the files in our dataset</li>
<li>Write functions to perform certain analytical tasks on the data</li>
<li>Save the results of the analysis in a new folder</li>
</ul>

[Back to table of contents](#contents)

## The Research Question
Let's construct a hypothetical research situation: we have a group of texts written by some famous authors, and we want to use the Python module 'textblob' to perform some very basic Natural Language Processing tasks on these texts. Let us assume for the moment that we do not know what the module is capable of doing - before continuing further in the lesson, go read the introductory material about it.

<details>
<summary>Once you have done this, have any natural research questions come to mind? Click on the arrow here to compare the questions you thought of to the ones we will pursue today. How do they differ? Note how specific the objective is, and note how we pinpointed the exact method to use.</summary>

Let's say that we have eight passages from famous literary sources. An objective could be to compare styles of authorship, perhaps based on how their tone changes. For this we can choose the NLP method of sentiment analysis. Another objective could be to determine how descriptive the texts are. An NLP task for this is to measure the proportion of the texts that contain noun phrases (known as 'density').
</details>

## Setting Up Files

  Go to the folder where you put your text files for the Milestone Lesson. In that folder, replace any files with a few (best to have at least 4) plain new text files with a couple of paragraphs from some famous works. [Project Gutenberg](https://www.gutenberg.org/) is a great place to find classic works that you can download and save as plain .txt files. Remember that you should name your file names with the following parameters:

<ul>
<li>Descriptive names</li>
<li>No spaces: do something like 'no_spaces', or 'nospaces', no-spaces, or 'NoSpaces'</li>
<li>Unique names, so the computer can tell them each apart.</li>
</ul>

Once you have done this you will have some analysable data with which to work.

## Setting Up Code Workspace
Now open a fresh Jupyter or Google Colab notebook and set up your workspace. Check what your current working directory is, and then build a path to the directory where your files are. Do this yourself first and then expand the arrows below to see if you got the code correct.

<details>
<summary>Expand to check your answer (This code sets the folder where your files are as the location that Python is reading) </summary>
<pre>
<code>
import os
currentworkingdirectory = os.getcwd()
print('This is the current working directory:', currentworkingdirectory)

targetdirectory = os.path.join(currentworkingdirectory, 'file-looping')
print('This is the target directory:', targetdirectory)
</code>
</pre>
</details>



You will now want to have a safe place to save any new files you create during analysis. Try doing that before peeking at the answer, and if you are unsure, search online to see if you can make headway yourself.

<details>
<summary>Expand to check your answer (this creates a working directory populated with your files, and an empty directory ready to receive new files created during the analysis</summary>
<pre>
<code>
results_dir = os.path.join(currentworkingdirectory, "analysis_results_textblob")
os.makedirs(results_dir, exist_ok=True)
print(results_dir)
</code>
</pre>
</details>



Finally, you want to ensure you have the up to date version of textblob. Go ahead and install it inside Jupyter or import it (if it is already installed).

<details>
<summary>Expand to check your answer (these are the basic install and import commands) </summary>
<pre>
<code>
pip install textblob
from textblob import TextBlob
</code>
</pre>
</details>

Note that in the answer above, we imported only the class TextBlob from the module. This is optional; you could import the entire module if you wanted. 

**A special note**: the sentiment analysis functionality in textblob only works with some additional installations. Here they are below:

```python
!python -m textblob.download_corpora
```

While our texts are in individual files, it can be easier to analyse them if we bring the raw contents into the codespace. Create a new list called 'texts' and tell Python to store the text data in that list.


<details>
<summary>Expand to check your answer</summary>
<pre>
<code>
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
</code>
</pre>
</details>

The output should be all of the contents of your text files. Sometimes you may run into problems if your file is not saved in UTF-8. If that happens, re-save the file as UTF-8 and try again. We won’t go into encodings here.

## Performing the Analysis
Now that our texts are in a directory and we have the required modules, we can begin the actual analytical step. It is strongly recommended that you go read a little on sentiment analysis and noun phrase density if you are not already familiar with these concepts. 

Write a function called 'text_analysis' that takes two arguments — the filename and the content. Inside the function, create a TextBlob from the content and return a summary that includes: (a) sentiment polarity, (b) sentiment subjectivity, and (c) the noun phrases TextBlob found. If you are unsure how to do this, look at the documentation before looking up the lesson's answer.


<details>
<summary>Expand to check your answer</summary>
<pre>
<code>
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
</code>
</pre>
</details>

You should get a result that looks somewhat like (with the details different depending on text):
```python
"{'filename': 'oldmantext.txt', 'polarity': -0.04283380018674137, 'subjectivity': 0.2992763772175537, 'noun_phrases': WordList(['mixed-up whiskers', '’ t', 'man ’ s', 'body ’ s flesh crawl –', 'clothes –', 't ’', 'floor –', 'old black slouch'])}"
```
**Ensure you understand the code in the answer before continuing!**

Now that you have code that will assess one of your texts, write a loop that will assess them all in this way. As an aside, a major programming trick is to get something working for a small thing, and then expand. Take things one small bite at a time!
For each file, call your text_analysis function, and print out the filename with its sentiment polarity and subjectivity. This will give you a quick overview of all the texts.

<details>
<summary>Expand to check your answer</summary>
<pre>
<code>
for filename, content in texts:
    result = text_analysis(filename, content)
    print(f"File: {result['filename']}")
    print(f"  Polarity: {result['polarity']}")
    print(f"  Subjectivity: {result['subjectivity']}")
    print()
</code>
</pre>
</details>

The result should be a list of filenames with their polarity and subjectivity as decimals under them.

TextBlob also gives us noun phrases. Instead of printing them all, let’s count how many noun phrases appear in each text. Add this count to your printed output.


<details>
<summary>Expand to check your answer</summary>
<pre>
<code>
for filename, content in texts:
    result = text_analysis(filename, content)
    noun_count = len(result["noun_phrases"])
    
    print(f"File: {result['filename']}")
    print(f"  Polarity: {result['polarity']}")
    print(f"  Subjectivity: {result['subjectivity']}")
    print(f"  Number of noun phrases: {noun_count}")
    print()
</code>
</pre>
</details>

Now you should see the number of noun phrases in each text.

Finally, you might like to plot some of this data on a chart. We have not gotten into the depths of Python visualisation, but here is a simple code snippet which will help you plot the polarity of each text:

```python
import matplotlib.pyplot as plt

# Collect filenames and polarity scores
filenames = []
polarities = []

for filename, content in texts:
    result = text_analysis(filename, content)
    filenames.append(result["filename"])
    polarities.append(result["polarity"])

# Simplest bar chart
plt.bar(filenames, polarities)

# Tilt the x-axis labels so they’re easier to read
plt.xticks(rotation=45)

plt.show()

```
Here are some pointers to understand that code:
1. The import statement is written to shorten the name for typing convenience. The module is now called 'plt'. 
2. The second block of code creates a place to store the filenames and polarity scores separately.
3. The third code block goes through each text, runs the analysis function, and builds two lists: one of filenames, one of polarity scores. Those two lists are then used for plotting in the  bar chart command: .bar() is a function in the nicknamed 'plt' module. We give it the filenames and the polarities so that it can plot them as a bar chart. 
4. Finally, because we need to be able to see the labels, 'plt' has a function called xticks() which has a parameter, 'rotation'. We rotate the labels 45 degrees. 
5. plt.show is the command in 'plt' to show the plot we just constructed.

## Saving Our Analysis
Now let’s save all the results into a file, and also save the plot as an image. Both will go into the analysis_results_textblob folder we created earlier. Take a look at this code. Try to understand it naturally before reading the explanation afterward.

```python
# 1. Collect results
results = []
filenames = []
polarities = []

for filename, content in texts:
    result = text_analysis(filename, content)
    noun_count = len(result["noun_phrases"])
    results.append(f"{result['filename']}: Polarity={result['polarity']}, "
                   f"Subjectivity={result['subjectivity']}, "
                   f"Noun Phrases={noun_count}")

    filenames.append(result["filename"])
    polarities.append(result["polarity"])

# 2. Save results to a text file
results_path = os.path.join(results_dir, "analysis_summary.txt")
with open(results_path, "w", encoding="utf-8") as f:
    for line in results:
        f.write(line + "\n")
print(f"Results saved to: {results_path}")

plt.bar(filenames, polarities)
plt.xticks(rotation=45)
plt.ylabel("Polarity")
plt.title("Sentiment Polarity of Texts")

plot_path = os.path.join(results_dir, "sentiment_plot.png")
plt.tight_layout()
plt.savefig(plot_path)
plt.close()

print(f"Plot saved to: {plot_path}")
```

Here is the explanation of that code:
1. The first three lines create containers for the results and the filenames.
2. The first loop saves those things in these containers.
3. The second loop uses those containers to save the results in a new text file, and save it in the directory you created above for the results.
4. The final few blocks of code create the plot and give it its various elements. It then saves it in the directory for the results.

[Back to table of contents](#contents)

## Conclusions
Congratulations! Within a few lines of code you have taken some texts and have automated an analysis of their natural language features. This is a miniature example of what a code-driven research workflow can look like.

Some crucial things to remember:

<ul>
<li>Have a concrete question that is answerable using code. Vague questions are unlikely to help get you satisfactory results</li>
<li>Take the time to prepare your datasets and design your approach to the problem. A big coding project is made much easier with some clarity on the direction you are headed!</li>
<li>Keep your old code and documentation. Chances are, you can re-use a lot of what you write.</li>
<li>Comment your code to remind future you what your code does.</li>
<li>Read the formal documentation! Search the internet when you have questions! It is not cheating to look for assistance.</li>
</ul>

## Homework
This was an intensive lesson where you were encouraged to write a lot of your own code before looking at the answers. However, to get the most out of this lesson, it is worth now pondering your own research challenges and situations. What kinds of data do you have? What things would you like to know about it, or accomplish with it? What steps would you need to take to get your data ready for digital analysis of any kind? If you are looking for a particular method, can you search online to find some Python modules which perform this method? 

By asking these questions with a greater awareness of what it takes to write code and run it on real data, you will be enabling yourself to do more with these powerful tools. 

<p class="credits">Written by Estara Arrant, 2025-04-16<br />Licence: <a href="https://creativecommons.org/licenses/by-sa/4.0/">CC BY-SA 4.0</a></p>

<p class="previous-next-lesson"><a href="lesson7-file-handling-essentials.html">&lt; Previous lesson</a> | <a href="lesson9-concluding-lesson.html">Next lesson &gt;</a></p>

