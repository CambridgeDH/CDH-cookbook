# Critical Python for Data Analysis 
<link rel="stylesheet" href="../../cookbook.css">
<p class="previous-next-lesson"><a href="toc.html">^ Methods Fellows 2025</a></p>

## Contents
- Reading in and Examining Datasets
- Data Transformation and Visualization
- Data Visualization and Mapping
- Categorical and Text Data
- Web Scraping and APIs
- Political Ads and Merging Data
- Social Networks

Welcome to a mini-intro course to using python for data analysis. The
aim of this lesson is to not only equip you with the technical expertise to perform foundational data analysis techniques in Python, but to also challenge you to think critically about the design decisions of *how*
the way you manipulate or analyze your data (including the sourcing and
curation of data) has downstream real-world effects. It is important for data engineers, researchers, and pracitioners analyzing large streams of data to be earnest and intentional about who\'s data matters, and how
their data is represented. Every decision has consequences, as we will
see that the way that we produce and present our data tells a different
narrative based on the analyzer\'s own positionality and the hidden (or
unhidden) biases that may come with it.

The following file has multiple mini-lessons pertaining to learning data analysis with a critical lens. To work through these lessons, please download this file as a Markdown (.md) file, and convert it to a Jupyter or Google Colab Python Notebook (you can simply use a .md to .ipynb converter online, such as the following: <https://www.vertopal.com/en/convert/md-to-ipynb>).


The Python lessons we will go over in this file are the following:

1\) Reading in and examining datasets 2) Performing data transformations 3) Performing visualisations and mapping 4) Working with categorical and text data 5) Web scraping and Application Programming Interfaces (APIs) 6) Merging and Joining Datasets (using datasets of political advertisements, and spotting misinformation within them) 7) Social Networks and Network Analysis

For any questions regarding this notebook and course, please contact
<sf752@cam.ac.uk>. Many thanks and I hope you find this course engaging!

# Reading in and Examining Datasets

## Goals

-   Work with Jupyter/Google Colab notebooks in Python
-   Read data of various types into Python
-   Describe the sources of datasets
-   Perform basic data exploration

This is a Markdown file that can be converted to a Jupyter or Google
Colab notebook (`.ipynb` file). Jupyter notebooks allow you to combine
code, output, and text in one document. You can run code cells by
selecting them and pressing `Shift + Enter`, `Ctrl/Cmd + Enter` on
Google Golab, or clicking the \"Run\" button.

The notebook automatically has access to files and directories (folders)
in the project directory. This makes it much easier to load multiple
data sets.

## 1 Rectangular data {#1-rectangular-data}

The most common type of data we\'ll see is rectangular data, which is
organized into a table of rows and columns. If data come to us in
another form we\'ll often want to make them rectangular.

First we will need to download the data that we will be using for this
lesson. You can download the folder called `lesson_1_data` from here:
<https://drive.google.com/drive/folders/1zRIhA9QN5G6dZPjqk_Q7Ccy-HQQSHMua?usp=sharing>.
In the same directory as this notebook file, place this folder called
`lesson_1_data`. If you are using Google Colab, you can simply upload
the contents of the folder to your Google Colab session (a guide on how
to do so can be found here:
<https://colab.research.google.com/notebooks/io.ipynb#scrollTo=eikfzi8ZT_rW>),
Inside, there\'s a comma-separated values (CSV) file called
`seattle_airbnb.csv`. This contains data about 100 Airbnb listings from
Seattle.

These data come from Inside Airbnb, <http://insideairbnb.com/>. Go to
the website and have a look at the About, Behind, and Get the Data
pages. *Use what you read to answer the questions below. Just type your
answers below the questions.*

**Question 1.1: Who created these data sets?**

*\[Your answer here\]*

**Question 1.2: Why did they do it?**

*\[Your answer here\]*

**Question 1.3: Where were the data sourced from?**

*\[Your answer here\]*

## 2: Setup {#2-setup}

Python doesn\'t come with everything we need loaded by default. Before
we do anything else, we need to import *libraries* (also called packages
or modules). Libraries contain specialized functions and data that we
can use to do useful things. The main library we\'ll use is called
**pandas**, which is the standard library for data manipulation,
exploration, and analysis in Python.

You can read more about pandas here: <https://pandas.pydata.org/>

If a library hasn\'t been installed in your Python environment, you\'ll
need to install it. For instance, you\'d type `pip install pandas` in a
terminal or command prompt. In Jupyter and Google Colab notebooks, you
can also use `!pip install pandas`. You only need to do this once for
each Python installation, but in order to use a library, you have to
import it in each notebook or script.

Code cells let us incorporate code into notebooks like this one.
They\'re very useful for creating interactive documents and for testing
out new code. The output from a code cell shows up right below it. You
can run a code cell by selecting it and pressing `Shift + Enter`,
`Ctrl/Cmd + Enter` on Google Golab, or clicking the \"Run\" button.

**Question 2.1: Run this cell to import pandas and numpy (a numerical
computing library):**

``` python
import pandas as pd
import numpy as np

print("Libraries loaded successfully!")
```

## 3: Importing data {#3-importing-data}

To use data inside Python, we first have to import, or *read*, that data
into our environment and save it to a variable.

``` python
airbnb_data = pd.read_csv("lesson_1_data/seattle_airbnb.csv")
```

When we do this, we assign the values of the data to a variable,
`airbnb_data`, using the equals sign (`=`). The object we create is
called a DataFrame (in pandas).

**Question 3.1: What is the role of each component in the above line of
code?**

-   `airbnb_data`: the variable name we used for the DataFrame
-   `=`: *\[Your answer here\]*
-   `pd.read_csv()`: *\[Your answer here\]*
-   `"lesson_1_data/seattle_airbnb.csv"`: *\[Your answer here\]*

## 4: Looking at the data {#4-looking-at-the-data}

You can display the DataFrame by typing the name of the variable. In
Jupyter notebooks, if a variable is the last line in a cell, it will
automatically be displayed.

**Question 4.1: Run the cell below to display the DataFrame:**

``` python
airbnb_data
```

The `.head()` method shows you the first five rows of a DataFrame by
default.

**Question 4.3: Use the head method in the code cell below to show the
first rows of airbnb_data:**

``` python
# Your code here
```

**Question 4.4: `.head()` shows the first 5 rows by default. Change the
following code to show the first 10 rows:**

``` python
airbnb_data.head(5)
```
What if you want to look at the *last* several rows of a DataFrame
instead of the first several rows?

You can access help documentation for any function or method by typing
`?` before it or using the `help()` function.

**Question 4.5: Based on what you know, show the last 5 rows of
airbnb_data (hint: use `.tail()` instead of `.head()`)**

``` python
# Your code here
```

You can extract a single column in several ways. The most common are:

-   Using bracket notation: `dataframe['column_name']`
-   Using dot notation: `dataframe.column_name` (only works if column
    name has no spaces)

**Question 4.6: Use bracket notation to display the \'price\' column:**

``` python
# Your code here
```

**Question 4.7: Get basic information about the DataFrame using
`.info()` and `.describe()` methods:**

``` python
airbnb_data.info()
```

``` python
airbnb_data.describe()
```

## 5: Hierarchical data {#5-hierarchical-data}

Data isn\'t always a single, flat table. Sometimes it\'s nested or
hierarchical.

`colors.json` is a file in JSON format. This is a common format for web
data. Python has a built-in `json` library for reading JSON files.

**Question 5.1: Run the code below to import the json library and read
the file \"lesson_1\_data/colors.json\":**

``` python
import json

with open("lesson_1_data/colors.json", "r") as file:
    json_data = json.load(file)

print("JSON data loaded successfully!")
```

When you load JSON data, it becomes a Python dictionary (a data structure with keys and values):

``` python
print(type(json_data))
print(json_data)

You can use bracket notation `[]` to extract pieces of this data. For
example, to get the 5th color (index 4, since Python uses 0-based
indexing):

``` python
json_data['colors'][4]
```

**Question 5.2: Display the information for the color red (hint: you\'ll
need to try different indices):**

``` python
# Your code here
```

## 6: Saving your work {#6-saving-your-work}

Jupyter notebooks automatically save periodically, but you should also
manually save using `Ctrl+S` (or `Cmd+S` on Mac) or by clicking the save icon.

**Question 6.1: Save your notebook now.**

You can also export your notebook in different formats (HTML, PDF, etc.) using the File menu → Download as. 

You should save your work somewhere you can easily access it again, such as your cloud storage or local drive.

## Challenge: Excel worksheets

In the data folder, there is an Excel spreadsheet, `airbnb.xlsx`. It
contains data for three cities (Seattle, Boston, Chicago) in separate
sheets.

**Challenge:** Use pandas to read in all of this data. Read each sheet
separately, then combine them into one DataFrame.

Hints:

-   Look up `pd.read_excel()` documentation
-   Use the `sheet_name` parameter to specify which sheet to read
-   Use `pd.concat()` to combine multiple DataFrames

``` python
# Your code here
# You may need to install openpyxl: `pip install openpyxl`
```

## Just for fun: Image data

Images are data too, and Python can import and manipulate them as well.
If you have extra time, check out the PIL/Pillow library:

<https://pillow.readthedocs.io/en/stable/>

``` python
# Uncomment to install and use:
# !pip install Pillow
# from PIL import Image
# import matplotlib.pyplot as plt

# cat = Image.open("lesson_1_data/Black_white_cat_on_fence.jpg")
# plt.imshow(cat)
# plt.axis('off')
# plt.show()

# # Flip the image
# cat_flipped = cat.transpose(Image.FLIP_TOP_BOTTOM)
# plt.imshow(cat_flipped)
# plt.axis('off')
# plt.show()
```

## Hints

**3.1**

-   `=` is the assignment operator - it assigns the value on the right
    to the variable on the left
-   `pd.read_csv()` is a pandas function that reads CSV files and
    returns a DataFrame
-   `"lesson_1_data/seattle_airbnb.csv"` is the file path (location) of
    the data file

**4.3** You\'ll need to write: `airbnb_data.head()`

**4.4** You\'ll need to change the value from 5 to 10:
`airbnb_data.head(10)`

**4.5** Use `.tail(5)` instead of `.head(5)`

**4.6** Use: `airbnb_data['price']`

**5.2** `json_data['colors'][4]` gave us the info for \'yellow\', so try
changing the 4 to other numbers to find \'red\'. Remember Python uses
0-based indexing (starts counting at 0).

# Data Transformation and Visualization

------------------------------------------------------------------------

## Goals {#goals}

-   Begin exploring a data set on our own
-   Master method chaining in pandas
-   Learn basic data manipulation operations
-   Produce basic visualizations

## 0: Check-in {#0-check-in}

We\'ll continue working with the Inside Airbnb data. This time, we\'ll
use the full data set of listings for Seattle but this time we\'ll focus
on performing data transformations.

**Question 0.1: Use the code block below to write the following code**

First, import the `pandas` library (using the alias `pd`).

Once you\'ve imported pandas, the `pd.read_csv()` function will read
data into Python.

Download the `lesson_2_3_data/` from the same Google Drive link as in
lesson 1:
<https://drive.google.com/drive/u/2/folders/1zRIhA9QN5G6dZPjqk_Q7Ccy-HQQSHMua>.
Read the `listings.csv` file from the `lesson_2_3_data/` folder into
Python (either by uploading the foler and its contents to Google Colab,
or putting it in the same directory as this notebook within Jupyter
Notebook) and assign it to the variable name `airbnb_data` using the `=`
operator.

``` python
# Your code here
```

## 1: Exploring the Data {#1-exploring-the-data}

This DataFrame has more variables (= columns) and observations (= rows)
than last lab\'s data set. You can get an overview of the different
columns using the `.info()` method:

``` python
airbnb_data.info()  # display basic information about the data
```

Sometimes we\'ll just want to get the names of the columns. We can use
the `.columns` attribute to do that.

**Question 1.1: Display the column names of airbnb_data**

``` python
# Your code here
```

**Question 1.2: Interpret the output from `.info()`: what kind of
information does it give you?**

*\[Your answer here\]*

## 2: Data Transformation {#2-data-transformation}

### Method Chaining

In Python pandas, we use **method chaining** to perform multiple
operations in sequence. This is similar to the pipe (`%>%`) in R. Method
chaining takes the output from one method and immediately applies
another method to it. If you were making a whole bunch of peanut butter
and pickle sandwiches, you could do it this way:

``` python
slices = Cut(bread)
smeared = Smear(slices, condiment='peanut_butter')
pickled = Apply(smeared, what='pickles', method='carefully')
sandwich = Close(pickled)
```

That\'s annoying because we\'re really doing all of those things to the
same object. I don\'t really think of my partially made sandwich as
\'smeared\' or \'pickled\'. Instead, I do all of those steps together,
and keep working on the same object as I apply each transformation.
That\'s what method chaining does for us in pandas:

``` python
sandwich = (bread
    .Cut()
    .Smear(condiment='peanut_butter')
    .Apply(what='pickles', method='carefully')
    .Close()
)
```

Notice how each method is called on the result of the previous method.
In Python, we often use parentheses to wrap multi-line method chains for
better readability.

Unfortunately, we don\'t have the technology yet to make real sandwiches
this way. Instead, we\'ll be doing the same thing to data.

Let\'s practice method chaining!

For example, to look at the first 6 unique values of the `neighbourhood`
column:

``` python
# Instead of nested functions:
# list(airbnb_data['neighbourhood'].unique())[:6]

# We can write:
airbnb_data['neighbourhood'].unique()[:6]  # show the top six unique neighborhoods
```

**Question 2.1: Use method chaining to show the first 20 listing names**

Hint: Use `.head(20)` on the \'name\' column

``` python
# Your code here
```

## 3: Data Manipulation Operations {#3-data-manipulation-operations}

Now that we understand method chaining, we can start putting together
different operations to perform multi-step analysis. In pandas, we have
several key operations for data manipulation. Remember that our course
material offers a starting point! Coding is about facing new problems,
making mistakes, using internet resources like Stack Overflow, and
solving those problems (but your classmates and I are also here to
help).

### Filtering Rows

We can filter data to a subset by **row** using several methods:

-   Boolean indexing: `df[df['column'] == value]`
-   The `.query()` method: `df.query('column == value')`

You can filter by values in one or more columns, using comparison
operators like these:

-   `==`: equal to
-   `!=`: not equal to
-   `>`, `<`, `>=`, `<=`
-   `.isin()`: check if value is in a list

This will give us the observations in the \"Central Area\" neighbourhood
group:

``` python
# Method 1: Boolean indexing
airbnb_data[airbnb_data['neighbourhood_group'] == "Central Area"]
```

``` python
# Method 2: Using .query() - often cleaner for complex filters
airbnb_data.query('neighbourhood_group == "Central Area"')
```

These show the listings in the Central Area.

What about multiple criteria? For instance, if we only want to see
listings in the Central Area with at least 10 reviews:

``` python
# `&` means "and", `|` means "or" (when using boolean indexing, use parentheses!)
airbnb_data[
    (airbnb_data['neighbourhood_group'] == "Central Area") &
    (airbnb_data['number_of_reviews'] >= 10)
]
```

``` python
# Or using .query() - no parentheses needed around each condition
airbnb_data.query('neighbourhood_group == "Central Area" and number_of_reviews >= 10')
```

**Question 3.1: How many listings?**

How many listings are there in the UDistrict? Write code to filter the
data set only to listings in the \"University District\"
`neighbourhood_group`.

Hint: Use `.shape[0]` or `len()` to count the number of rows.

``` python
# Your code here
```

**Bonus: How many units are there in \'Other neighborhoods\' that have a
price less than \$70 a night?**

``` python
# Your code here
```

### Selecting Columns

We can select particular **columns** by name using bracket notation:

``` python
# Select specific columns
airbnb_data[['id', 'name', 'neighbourhood_group', 'neighbourhood',
             'price', 'number_of_reviews']].head(100)
```

This is how we generated the data for Lab 1.

You can use `.drop()` to remove particular columns:

``` python
airbnb_data.drop(columns=['latitude', 'longitude'])
```

**Question 3.2: Select to show only the prices**

``` python
# Your code here
```

**Question 3.3: Use filtering and column selection to display the prices
and names of the listings with more than 10 reviews**

``` python
# Your code here
```

### Sorting Data

The `.sort_values()` method reorders a DataFrame by one or more columns,
in ascending or descending order.

Let\'s order the data by price, cheapest first:

``` python
(airbnb_data
 [['id', 'name', 'host_name', 'neighbourhood', 'price', 'number_of_reviews']]  # select columns
 .query('price > 0')  # exclude prices of $0 or less
 .sort_values('price')  # sort by ascending price
)
```

Most expensive first:

``` python
(airbnb_data
 [['id', 'name', 'host_name', 'neighbourhood', 'price', 'number_of_reviews']]  # select columns
 .query('price > 0')  # exclude prices of $0 or less
 .sort_values('price', ascending=False)  # sort by descending price
)
```

**Question 3.4: Which listings have the most reviews?**

Show the listings in the UDistrict that have the most reviews:

``` python
# Your code here
```

## 4: Data Visualization {#4-data-visualization}

Now that we can adjust what data we\'re looking at with some operations,
we can start making visualizations. Not only do these look cool, but
they\'re a great way to get a sense for big patterns in your data.

We\'ll start by plotting a single variable, using bar charts and
histograms.

For visualization in Python, we\'ll use:

-   **matplotlib**: The fundamental plotting library
-   **seaborn**: A higher-level library built on matplotlib with better
    defaults

Let\'s import them:

``` python
import matplotlib.pyplot as plt
import seaborn as sns

# Set a nice default style
sns.set_style("whitegrid")
%matplotlib inline
```

### Histograms

What\'s the distribution of reviews that an Airbnb gets? We can see this
using a histogram. Histograms are for *continuous* or numeric values.

``` python
plt.figure(figsize=(10, 6))
plt.hist(airbnb_data['number_of_reviews'], bins=30, edgecolor='black')
plt.xlabel('Number of Reviews')
plt.ylabel('Frequency')
plt.title('Distribution of Reviews')
plt.show()
```

Or using seaborn for a cleaner look:

``` python
plt.figure(figsize=(10, 6))
sns.histplot(data=airbnb_data, x='number_of_reviews', bins=30)
plt.title('Distribution of Reviews')
plt.show()
```

**Question 4.1: Make a histogram of prices. When you do this, you\'ll
see that it\'s hard to make sense of, because a few prices are really
large.**

To get a better look at the distribution of prices, filter out large
values before plotting (e.g. `price <= 500`).

``` python
# Your code here
```

### Bar Charts

We can see that there are three types of rooms:

``` python
airbnb_data['room_type'].unique()
```

Let\'s plot how many listings there are from each neighborhood group
using a bar chart. Bar charts are for *categorical* values.

``` python
plt.figure(figsize=(12, 6))
airbnb_data['neighbourhood_group'].value_counts().plot(kind='bar')
plt.xlabel('Neighbourhood Group')
plt.ylabel('Count')
plt.title('Airbnb Listings in Seattle by Neighborhood Group')
plt.xticks(rotation=45, ha='right')
plt.tight_layout()
plt.show()
```

Or using seaborn:

``` python
plt.figure(figsize=(12, 6))
sns.countplot(data=airbnb_data, x='neighbourhood_group')
plt.xlabel('Neighbourhood Group')
plt.ylabel('Count')
plt.title('Airbnb Listings in Seattle by Neighborhood Group')
plt.xticks(rotation=45, ha='right')
plt.tight_layout()
plt.show()
```

**Question 4.2: Make a bar chart showing the number of listings for each
room type**

``` python
# Your code here
# Consider adjusting the rotation angle as necessary
```

**Question 4.3: Would we want to use a bar chart or a histogram to
visualize the number of reviews?**

*\[Your answer here\]*

**Question 4.4: Make the appropriate visualization**

``` python
# Your code here
```

## Just for fun: Seaborn Styles

Seaborn has a variety of built-in styles you can use to make your plots
look different. Here are some examples:

``` python
# Try different styles:
# 'darkgrid', 'whitegrid', 'dark', 'white', 'ticks'

sns.set_style("white")
plt.figure(figsize=(10, 6))
sns.histplot(data=airbnb_data, x='number_of_reviews', bins=30)
plt.title('Distribution of Reviews')
plt.xlabel('Number of Reviews')
plt.show()

# You can also try different color palettes:
# sns.set_palette("husl")
# sns.set_palette("Set2")
# sns.set_palette("viridis")
```

## Hints {#hints}

**0.1** Your code should look like:

``` python
import pandas as pd
airbnb_data = pd.read_csv('lesson_2_3_data/listings.csv')
```

**1.1** Use `airbnb_data.columns` to see column names

**1.2** Consider the example output from `.info()`:

-   What does it tell you about column names?
-   What does it tell you about data types?
-   What does it tell you about missing values?

**2.1** You can write: `airbnb_data['name'].head(20)`

**3.3** First filter to listings with more than 10 reviews, then select
the name and price columns:

``` python
airbnb_data[airbnb_data['number_of_reviews'] > 10][['name', 'price']]
```

**3.4** Try to filter for University District, then sort by
`number_of_reviews` in descending order:

``` python
.query('neighbourhood_group == "University District"')
.sort_values('number_of_reviews', ascending=False)
```

**4.1** Filter the data first:

``` python
price_filtered = airbnb_data[airbnb_data['price'] <= 500]
plt.figure(figsize=(10, 6))
sns.histplot(data=price_filtered, x='price', bins=30)
plt.title('Distribution of Prices (≤ $500)')
plt.show()
```

**4.2** Copy the code from the neighborhood group bar chart and change
\'neighbourhood_group\' to \'room_type\'.

# Data Visualization and Mapping

------------------------------------------------------------------------

## Goals {#goals}

-   Add color to our visualizations
-   Add facets to our visualizations
-   Make visualizations using maps
-   Control color output using palettes

## 0: Lab Check-in {#0-lab-check-in}

For the first half of this lab, we\'ll use the `gapminder` data set.
This example is adapted from Kieran Healy\'s book, *Data Visualization:
A Practical Introduction*, chapters 3 and 4: <http://socviz.co/>

For the second half, we\'ll use the Seattle Airbnb listings from Inside
Airbnb.

**Question 0.1: Run the cell below to import the necessary packages**

``` python
# Uncomment if you need to install packages:
# !pip install gapminder folium

import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
from gapminder import gapminder

# Set style
sns.set_style("whitegrid")
%matplotlib inline

print("Packages loaded successfully!")
```

## 1: Visualizations with Covariation {#1-visualizations-with-covariation}

Bar charts and histograms are great at showing variation along one
variable. However, we\'re often interested in the relationship between
two or more variables. That is, a bar chart or histogram shows the
*variation* of a single variable. The visualizations we\'ll learn in
this module show the *covariation* between variables.

Before we start, let\'s take a look at the gapminder data.

**Question 1.1: Use `.info()` to examine the gapminder data**

``` python
# Your code here
```

**Question 1.2: What\'s one variable that is continuous? What\'s one
that\'s categorical?**

*\[Your answer here\]*

Read about the origins of the gapminder data set by looking at the
source: <https://www.gapminder.org/data/>

### Scatterplots

Scatterplots are a good way to visualize the relationship between two
variables, and to look for outliers.

``` python
# Set the default style to minimal (clean look)
sns.set_style("whitegrid")

# Create a scatterplot and save it to a variable
fig, ax = plt.subplots(figsize=(10, 6))
ax.scatter(gapminder['gdpPercap'], gapminder['lifeExp'], alpha=0.5)
ax.set_xlabel('GDP per Capita')
ax.set_ylabel('Life Expectancy')
ax.set_title('Life Expectancy vs GDP per Capita')
plt.show()

# We saved the figure to 'fig' and axes to 'ax' so we can reference them later
```

**Question 1.3: Make a scatterplot comparing the population and the life
expectancy**

``` python
# Your code here
```

### Scales

To better see our data, we can transform the x-axis into a log scale.

``` python
# Create the same plot but with log scale on x-axis
fig, ax = plt.subplots(figsize=(10, 6))
ax.scatter(gapminder['gdpPercap'], gapminder['lifeExp'], alpha=0.5)
ax.set_xscale('log')  # Set x-axis to log scale
ax.set_xlabel('GDP per Capita (log scale)')
ax.set_ylabel('Life Expectancy')
ax.set_title('Life Expectancy vs GDP per Capita (Log Scale)')
plt.show()
```

**Question 1.4: Add a log scale to your population vs life expectancy
plot**

``` python
# Your code here
```

**Question 1.5: What do you think accounts for the distinctive shape of
your scatterplot?**

*\[Your answer here\]*

### Colors

In addition to the x and y axes, another aesthetic available to use is
`color`. This means we can look at how up to three variables change
together!

For example, we can color data points by continent, a categorical
variable:

``` python
# Using seaborn makes coloring by groups easy
plt.figure(figsize=(10, 6))
sns.scatterplot(data=gapminder, x='gdpPercap', y='lifeExp',
                hue='continent', alpha=0.6)
plt.xscale('log')
plt.xlabel('GDP per Capita (log scale)')
plt.ylabel('Life Expectancy')
plt.title('Life Expectancy vs GDP per Capita by Continent')
plt.show()
```

If you map a continuous/numeric variable onto color, the plotting
library will pick a gradient scale:

``` python
# Color by a continuous variable (log of population)
plt.figure(figsize=(10, 6))
scatter = plt.scatter(gapminder['gdpPercap'], gapminder['lifeExp'],
                     c=np.log10(gapminder['pop']), cmap='viridis', alpha=0.6)
plt.xscale('log')
plt.xlabel('GDP per Capita (log scale)')
plt.ylabel('Life Expectancy')
plt.title('Life Expectancy vs GDP per Capita (colored by log population)')
plt.colorbar(scatter, label='Log10(Population)')
plt.show()
```

**Question 1.6: Remake your population vs life expectancy plot by
choosing a continuous variable to add colors**

``` python
# Your code here
```

**Question 1.7: Remake your plot by choosing a categorical variable to
add colors that explain the interesting shapes**

``` python
# Your code here
# Hint: Use seaborn's scatterplot with the hue parameter
```

### Facets

Let\'s take a different way of breaking down these data by continent.
This time, we\'ll *facet* the data into \"small multiple\" plots.

In Python, we use `FacetGrid` from seaborn to create faceted plots.

``` python
# Create faceted plot using seaborn
g = sns.FacetGrid(gapminder, col='continent', col_wrap=3, height=4)
g.map(plt.scatter, 'gdpPercap', 'lifeExp', alpha=0.5)
g.set(xscale='log')
g.set_axis_labels('GDP per Capita (log scale)', 'Life Expectancy')
g.fig.suptitle('Life Expectancy vs GDP per Capita by Continent', y=1.02)
plt.show()
```

**Question 1.8: Add continent facets to your population vs life
expectancy plot**

``` python
# Your code here
```

## 2: Creating New Columns {#2-creating-new-columns}

Creating new columns is one of the most important operations in data
analysis. It allows you to add variables to your dataset by transforming
or combining existing variables.

What if we wanted to look at *total* GDP, not just per capita GDP? To do
this, we\'d have to create a new column. Total GDP is GDP per capita
times population.

``` python
# Filter to year 2007 and create new column
gap_2007 = gapminder[gapminder['year'] == 2007].copy()
gap_2007['gdp'] = gap_2007['gdpPercap'] * gap_2007['pop']

# Create plot
plt.figure(figsize=(12, 6))
sns.scatterplot(data=gap_2007, x='pop', y='gdp', hue='continent', s=100, alpha=0.7)
plt.xlabel('Population')
plt.ylabel('Total GDP')
plt.title('Total GDP vs Population (2007)')
plt.show()
```

## 3: Exercise - Life Expectancy Over Time {#3-exercise---life-expectancy-over-time}

Instead of looking at the relationship between life expectancy and GDP,
now we\'ll look at changes in life expectancy over time. You can use the
code cells below for all the questions.

### 3.1: Line plot of life expectancy by year {#31-line-plot-of-life-expectancy-by-year}

**Create a plot where `x = year` and `y = lifeExp`.** This time, use
line plots (`plt.plot()`) instead of scatter plots. Initially, it won\'t
look quite right.

``` python
# Your code here
# Hint: plt.plot(gapminder['year'], gapminder['lifeExp'])
```

### 3.2: Grouping by country {#32-grouping-by-country}

**You need to tell the plot to draw separate lines for each country.**
To do this, you\'ll need to plot each country separately using a loop or
use seaborn\'s lineplot. Does it look more reasonable now?

``` python
# Your code here
# Method 1: Loop through each country
# plt.figure(figsize=(12, 6))
# for country in gapminder['country'].unique():
#     data = gapminder[gapminder['country'] == country]
#     plt.plot(data['year'], data['lifeExp'], alpha=0.3, linewidth=0.5)

# Method 2: Use seaborn (easier!)
# plt.figure(figsize=(12, 6))
# sns.lineplot(data=gapminder, x='year', y='lifeExp', units='country',
#              estimator=None, alpha=0.3, linewidth=0.5)
```

### 3.3: Facet by continent and interpret {#33-facet-by-continent-and-interpret}

**Finally, facet by continent.** Does life expectancy seem to have
increased over time everywhere? Do you see any dips or decreases?

``` python
# Your code here
# Hint: Create a FacetGrid and use map to plot lines for each country
```

*\[Your interpretation here\]*

## 4: Maps {#4-maps}

You can create interactive maps in Python using latitude and longitude
data. We\'ll use a package called `folium`
(<https://python-visualization.github.io/folium/>), which creates
Leaflet.js maps (the same library used in R\'s leaflet package).

The Inside Airbnb data has latitudes and longitudes for each listing, so
we\'ll use that.

**Question 4.1: Run the cell below to import folium and read the
listings data**

``` python
# Uncomment if you need to install folium
# !pip install folium

import folium

# Read the data
airbnb_data = pd.read_csv('lesson_2_3_data/listings.csv')
print(f"Loaded {len(airbnb_data)} listings")
airbnb_data.head()
```

### Points and Popups

`folium` uses method chaining (similar to pandas) to add layers to maps.

``` python
# Create a map centered on Seattle
# Folium automatically uses the latitude and longitude data to find the right map
seattle_map = folium.Map(
    location=[airbnb_data['latitude'].mean(), airbnb_data['longitude'].mean()],
    zoom_start=12
)

# Add circles for each listing (first 100 to keep it manageable)
# By adding the popup argument, we can click on a circle to show the name
for idx, row in airbnb_data.head(100).iterrows():
    folium.CircleMarker(
        location=[row['latitude'], row['longitude']],
        radius=5,
        popup=row['name'],
        color='blue',
        fill=True,
        fillColor='blue'
    ).add_to(seattle_map)

seattle_map
```

**Question 4.2: Make a folium map that only includes listings with a
price over \$200 and shows the price when the circle is clicked**

``` python
# Your code here
```

### Colors and Legends: Qualitative/Categorical

Colors require a bit more setup than with other plotting libraries. You
need to create a color mapping, and then use that mapping for your
markers and the legend.

``` python
# We're going to start by making a smaller DataFrame to use for our visualization
# Assign the small dataframe the name 'example_data'
example_data = airbnb_data[airbnb_data['neighbourhood'] == 'University District'].copy()

# Create color mapping for room types
# This is similar to colorFactor in R leaflet
room_colors = {
    'Entire home/apt': 'red',
    'Private room': 'blue',
    'Shared room': 'green'
}

# Create map
udistrict_map = folium.Map(
    location=[example_data['latitude'].mean(), example_data['longitude'].mean()],
    zoom_start=14
)

# Add circles which we can click to see the names
# Color the circles with our palette
for idx, row in example_data.iterrows():
    folium.CircleMarker(
        location=[row['latitude'], row['longitude']],
        radius=6,
        popup=row['name'],
        color=room_colors.get(row['room_type'], 'gray'),
        fill=True,
        fillColor=room_colors.get(row['room_type'], 'gray'),
        fillOpacity=0.7
    ).add_to(udistrict_map)

# Add a legend so we know what's what
legend_html = '''
<div style="position: fixed;
            bottom: 50px; right: 50px; width: 150px; height: 90px;
            background-color: white; border:2px solid grey; z-index:9999;
            font-size:14px; padding: 10px">
<p><strong>Room Type</strong></p>
<p><span style="color:red">●</span> Entire home/apt</p>
<p><span style="color:blue">●</span> Private room</p>
<p><span style="color:green">●</span> Shared room</p>
</div>
'''
udistrict_map.get_root().html.add_child(folium.Element(legend_html))

udistrict_map
```

**Question 4.3: Use the same code from above, but map a neighborhood of
your choice**

Hint: You can check unique neighborhoods with
`airbnb_data['neighbourhood'].unique()`

``` python
# Your code here
```

### Colors and Legends: Numeric/Continuous

You should use different color palettes for categorical vs numeric data.
You\'ve got a couple options for plotting numeric data:

-   **Linear mapping**: maps numbers directly onto a color gradient
-   **Binning by value**: each color spans the same numeric range
-   **Binning by quantile**: each color has the same number of data
    points

We\'ll demonstrate linear mapping first.

``` python
import matplotlib.cm as cm
import matplotlib.colors as mcolors

# Filter to University District
example_data = airbnb_data[airbnb_data['neighbourhood'] == 'University District'].copy()

# Create a colormap (similar to colorNumeric in R)
# This uses a red-purple gradient
min_price = example_data['price'].min()
max_price = example_data['price'].max()
norm = mcolors.Normalize(vmin=min_price, vmax=max_price)
cmap = cm.get_cmap('RdPu')

# Create map
price_map = folium.Map(
    location=[example_data['latitude'].mean(), example_data['longitude'].mean()],
    zoom_start=14
)

# Add markers
for idx, row in example_data.iterrows():
    color = mcolors.to_hex(cmap(norm(row['price'])))
    folium.CircleMarker(
        location=[row['latitude'], row['longitude']],
        radius=6,
        popup=row['name'],
        color=color,
        fill=True,
        fillColor=color,
        fillOpacity=0.7
    ).add_to(price_map)

# Note: For a more sophisticated legend, you would need to create custom HTML
# or use folium's colormap feature

price_map
```

**Question 4.4: Use similar code from above, but create a color scheme
based on quantiles instead**

Hint: Use `pd.qcut()` to bin the prices by quantiles (similar to
colorQuantile in R), then assign colors to each bin.

``` python
# Your code here
# Start by creating quantile bins:
# example_data['price_quantile'] = pd.qcut(example_data['price'], q=5, labels=['Q1', 'Q2', 'Q3', 'Q4', 'Q5'])
```

**Question 4.5: Compare the two maps of prices in the UDistrict. Which
mapping of prices to colors---linear mapping by value or binning by
quantile---do you think is more useful here, and why? There isn\'t a
right answer.**

*\[Your answer here\]*

## 5: Exercise - Mapping Airbnb in Seattle {#5-exercise---mapping-airbnb-in-seattle}

### 5.1: Choose a variable {#51-choose-a-variable}

**Think about what variable you\'d like to display in your map.**

*\[Write your variable name here\]*

### 5.2: Plot the distribution {#52-plot-the-distribution}

**Create a bar plot or histogram as appropriate to look at the
distribution of your variable**

``` python
# Your code here
```

### 5.3: Are there values that seem like outliers? {#53-are-there-values-that-seem-like-outliers}

Outliers are data points that seem very different from the rest of the
data. For instance, if one listing costs 10x the average price, then a
color palette using linear mapping will show that listing as one color
and all the rest of the listings as another. In other words, outliers
can make it hard to see important differences (they can cause other
problems for analysis too). That might be a good reason to exclude those
listings from our map. On the other hand, removing outliers might remove
important data: don\'t we want the people looking at our visualization
to know that there was a very expensive listing? Using a quantile
palette is a way to include outliers but still show variation.

A couple reasons to think about data in this way:

-   It\'s part of understanding **patterns and distributions** in your
    data
-   It helps you think about **data quality and potential flaws** in
    your data
-   It makes you articulate your **choices and goals** when you present
    your data

### 5.4: Including outliers {#54-including-outliers}

**If there are outliers, do you think you should include them in your
graph? Justify your answer.**

*\[Your answer here\]*

All of the subsequent code can be written in the code cell below.

### 5.5: Create a DataFrame {#55-create-a-dataframe}

**Create a new DataFrame for the rest of the exercise, filtering as
necessary**

### 5.6: Create a color palette {#56-create-a-color-palette}

**Use that DataFrame to create a color palette for your variable**

### 5.7: Create a folium map {#57-create-a-folium-map}

**Create a folium map using your new data set**

``` python
# Your code here for 5.5, 5.6, and 5.7
```

## Hints {#hints}

**1.2** Continuous variables are numeric columns (like `lifeExp`, `pop`,
`gdpPercap`). Categorical variables are text/factor columns (like
`country`, `continent`).

**1.3** Use `plt.scatter()` or `sns.scatterplot()` with `x='pop'` and
`y='lifeExp'`

**1.4** Add `plt.xscale('log')` or `ax.set_xscale('log')` after creating
your scatter plot

**3.2** To plot lines for each country:

``` python
plt.figure(figsize=(12, 6))
for country in gapminder['country'].unique():
    data = gapminder[gapminder['country'] == country]
    plt.plot(data['year'], data['lifeExp'], alpha=0.3, linewidth=0.5)
plt.xlabel('Year')
plt.ylabel('Life Expectancy')
plt.show()
```

**3.3** Use `FacetGrid`:

``` python
g = sns.FacetGrid(gapminder, col='continent', col_wrap=3, height=4)
# Then map the plotting function to each facet
```

**4.1** Remember that you can use
`airbnb_data['neighbourhood'].unique()` to list all of the unique values
of the neighbourhood column

**4.2** Filter the data first:

``` python
expensive = airbnb_data[airbnb_data['price'] > 200]
# Then use popup=f"${row['price']}"
```

**4.4** Create quantile bins:

``` python
example_data['price_bin'] = pd.qcut(example_data['price'], q=5, labels=['Very Low', 'Low', 'Medium', 'High', 'Very High'])
# Then create a color dictionary mapping each label to a color
```

# Categorical and Text Data

------------------------------------------------------------------------

## Goals {#goals}

-   Understand different data types in Python
-   Move between categorical and other types of data
-   Locate keywords in texts
-   Use regular expressions to manipulate text data

## 1: Data in Python {#1-data-in-python}

We\'ve already done a lot with data in Python. But it\'s time to pause
briefly to talk about the different kinds of data Python can hold and
the different formats Python can hold the data in.

### Data Types

There are several main kinds of data we deal with in Python. We call
them *types* of data:

-   **Numeric**: `int` (integer) like 1000, or `float` (decimal) like
    2.3 or 4.4e23
-   **String**: `"super cool"`, `"airbnb is totally hard to deal with"`,
    `"1,000,000"`, or `"free cheese in the break room"`
-   **Boolean**: `True` or `False` (note the capitalization!)

**Question 1.1: Assign the following three variables values of each
type**

``` python
# a =
# b =
# c =
```

We can check the type of a variable by using the function `type()`.

``` python
print(type(1000))
print(type("super cool"))
print(type(True))
```

**Question 1.2: Check the types of \'a\', \'b\', and \'c\' from 1.1
using `type()`**

``` python
# Your code here
```

### Data Structures

So far in this course, we\'ve mostly worked with DataFrames. But Python
has many ways to organize data. We\'ll talk about the main data
structures.

**1. Scalar: single values**

Assign a single value to make a scalar:

``` python
my_scalar = 45
print(my_scalar)
```

**2. List: one-dimensional data structure, *multiple data types
allowed***

Use square brackets `[]` or `list()` to make a list:

``` python
my_list = [45, 32, 31, 10000]
print(my_list)
print(f"Length: {len(my_list)}")
```

**Question 1.3: Check the length of my_list and my_scalar using `len()`.
What happens when you try to get the length of a scalar?**

``` python
# Your code here
```

Unlike some other structures, Python lists can hold different types of
data:

``` python
my_mixed_list = [45, 4.5, "450", True]
print(my_mixed_list)
print("Types:", [type(x) for x in my_mixed_list])
```

**3. NumPy Array: multi-dimensional data structure, only one type of
data allowed**

NumPy arrays are similar to R vectors and matrices - they require all
elements to be the same type:

``` python
import numpy as np

# 1D array (like an R vector)
my_array = np.array([45, 32, 31, 10000])
print("1D array:", my_array)
print("Type:", my_array.dtype)

# 2D array (like an R matrix)
my_matrix = np.array([[1, 2, 3, 4],
                      [5, 6, 7, 8],
                      [9, 10, 11, 12],
                      [13, 14, 15, 16],
                      [17, 18, 19, 20]])
print("\n2D array (5x4 matrix):")
print(my_matrix)
print("Shape:", my_matrix.shape)
```

**Question 1.4: What data type is stored in my_matrix? What happens if
you try to create an array with mixed types?**

``` python
# Your code here
# Try: np.array([45, 4.5, "450"])
```

### Accessing Data in Structures

For lists and arrays, accessing data is done with square brackets `[]`.
**Important**: Python uses 0-based indexing (counting starts at 0)!

``` python
# Grab the third item (index 2) in my_mixed_list
print("Third item:", my_mixed_list[2])

# Grab the item in the third row (index 2) and second column (index 1) of my_matrix
print("Matrix[2, 1]:", my_matrix[2, 1])

# Grab the whole second column of my_matrix (all rows, column 1)
print("Second column:", my_matrix[:, 1])
```

**4. Dictionary: key-value pairs, *multiple data types allowed***

Dictionaries are similar to named lists in R. They store key-value
pairs:

``` python
my_dict = {
    'name': 'Alice',
    'age': 25,
    'height': 5.6,
    'likes_python': True
}

print(my_dict)
print("\nAccess by key:", my_dict['name'])
```

**Question 1.5: Make a dictionary in Python of your favorite things.**

``` python
# Your code here
```

**5. DataFrame: two-dimensional data structure, only one type of data
per column**

This is the data structure we use most often for data analysis in
Python. DataFrames are like spreadsheets - each column is a single type,
but different columns can have different types. That\'s great because we
usually want to work with data where each observation (row) has
variables of different types.

When we use `pd.read_csv()` to read a file, pandas automatically makes a
DataFrame for us. But we can also make a new DataFrame from lists or
dictionaries. Imagine if I had some data on trees:

``` python
import pandas as pd

tree_id = [1, 2, 3, 4]  # set tree ids from 1-4
tree_heights = [19, 20, 35, 5]  # real measured tree heights with a measuring tape
tree_ages = [40, 35, 60, 4]  # I asked each tree
tree_names = ["oak", "poplar", "willow", "beech"]  # two of these trees really like Pokemon

tree_data = pd.DataFrame({
    'tree_id': tree_id,
    'tree_heights': tree_heights,
    'tree_ages': tree_ages,
    'tree_names': tree_names
})

tree_data
```

Then we can use all the DataFrame operations we\'ve learned.

**Question 1.6: Create a new column that shows the average number of
feet each tree has grown per year**

``` python
# Your code here
# Hint: tree_data['growth_per_year'] = ...
```

## 2: Categorical Data {#2-categorical-data}

Let\'s think about the kinds of variables we encounter during analysis.
Continuous variables can be represented with numeric types.

But what about categorical variables? We might represent them with
strings, but strings are open-ended and potentially messy.

To better represent categorical data, pandas has a special data type
called **categorical**. Categorical data gives us more tools
specifically for working with categories, which are especially handy for
visualizations and analysis.

This module is inspired by R for Data Science Chapter 15 and adapted for
Python.

### Example: Gapminder

We\'ll use the `gapminder` data set again to illustrate working with
categorical data.

**Question 2.1: Load the necessary packages and examine the gapminder
data. Which variables should be categorical?**

``` python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
from gapminder import gapminder

# Look at data types
gapminder.info()
gapminder.head()
```

The values that a categorical variable can take on are called
**categories** or **levels**.

**Question 2.2: Convert \'continent\' to categorical and look at its
categories. How many categories does it have? What order are they in?**

``` python
# Convert to categorical
gapminder['continent'] = gapminder['continent'].astype('category')

# Your code here to examine the categories
# Hint: gapminder['continent'].cat.categories
```

### Ordering Categories by Frequency

The gapminder data includes countries with complete data from 1952 to
2007. How many countries is that per continent? We\'ll start with a
simple bar chart, and then improve it step by step.

``` python
# Filter to one year and create bar chart
gap_2007 = gapminder[gapminder['year'] == 2007]

plt.figure(figsize=(10, 6))
gap_2007['continent'].value_counts().plot(kind='bar')
plt.xlabel('Continent')
plt.ylabel('Count')
plt.title('Countries per Continent')
plt.show()
```

First, let\'s order the bars by frequency (count):

``` python
# Reorder by frequency
gap_2007_ordered = gap_2007.copy()
continent_order = gap_2007_ordered['continent'].value_counts().index
gap_2007_ordered['continent'] = pd.Categorical(gap_2007_ordered['continent'],
                                               categories=continent_order,
                                               ordered=True)

plt.figure(figsize=(10, 6))
gap_2007_ordered['continent'].value_counts().plot(kind='bar')
plt.xlabel('Continent')
plt.ylabel('Count')
plt.title('Countries per Continent (ordered by frequency)')
plt.show()
```

Next, let\'s put the bars in ascending order (reverse):

``` python
# Reverse the order
continent_order_rev = continent_order[::-1]  # Reverse the list
gap_2007_ordered['continent'] = pd.Categorical(gap_2007_ordered['continent'],
                                               categories=continent_order_rev,
                                               ordered=True)

plt.figure(figsize=(10, 6))
gap_2007_ordered['continent'].value_counts().sort_index().plot(kind='bar')
plt.xlabel('Continent')
plt.ylabel('Count')
plt.title('Countries per Continent (ascending order)')
plt.show()
```

Finally, let\'s flip the axes for better readability:

``` python
plt.figure(figsize=(10, 6))
gap_2007_ordered['continent'].value_counts().sort_index().plot(kind='barh')
plt.xlabel('Number of Countries')
plt.ylabel('Continent')
plt.title('How many countries per continent?\nCountries with complete data, Gapminder')
plt.tight_layout()
plt.show()
```

Compare this to the bar chart we started with---it should be easier now
to see the point of the plot and to compare across continents.

### Ordering Categories by Another Variable

Instead of frequencies, you can reorder categories by values of some
other numeric variable.

**Question 2.3: Create a new DataFrame by filtering the gapminder data
down to countries in Asia in 2007.**

``` python
# gapminder_asia_2007 =
```

**Question 2.4: Choose one of the continuous variables. Make a dot plot
of this variable by country.**

You\'ll want country names on the y-axis for legibility.

``` python
# Your code here
```

**Question 2.5: Reorder countries by that same continuous variable, and
remake your plot.**

Be sure to give your plot an appropriate title.

``` python
# Hint: Sort the dataframe first, then create an ordered categorical
# gapminder_asia_2007_sorted = gapminder_asia_2007.sort_values('variable_name')
```

### Converting to Categorical

If you want to use categorical tools on data stored as strings, you\'ll
need to convert that variable to categorical first using
`.astype('category')`.

**Question 2.6: Convert the tree_names variable to categorical in the
tree_data from above.**

``` python
# Your code here
```

**Question 2.7: Plot one of the continuous variables against tree_names,
reordering appropriately.**

``` python
# Your code here
```

### Going Further with Categorical Data

Pandas includes many other tools for working with categorical data. For
example, you can:

-   Rename categories: `.cat.rename_categories()`
-   Combine categories: `.cat.set_categories()`
-   Reorder categories: `.cat.reorder_categories()`

Check out the pandas documentation for more:
<https://pandas.pydata.org/docs/user_guide/categorical.html>

## 3: Text Data (Strings) {#3-text-data-strings}

String data is more than just categories---it can contain rich, messy,
unstructured data that we might use to produce categories or quantities.

Python has powerful built-in string methods, and we can also use regular
expressions (regex) for more complex pattern matching. Let\'s start with
a list of fruit names as example data.

**Question 3.1: Run the cell below to create a list of fruit names**

``` python
fruit = [
    'apple', 'apricot', 'avocado', 'banana', 'bell pepper', 'bilberry',
    'blackberry', 'blackcurrant', 'blueberry', 'boysenberry', 'cherry',
    'chili pepper', 'clementine', 'cloudberry', 'coconut', 'cranberry',
    'cucumber', 'currant', 'damson', 'date', 'dragonfruit', 'durian',
    'eggplant', 'elderberry', 'feijoa', 'fig', 'goji berry', 'gooseberry',
    'grape', 'grapefruit', 'guava', 'honeydew', 'huckleberry', 'jackfruit',
    'jambul', 'jujube', 'kiwi fruit', 'kumquat', 'lemon', 'lime', 'loquat',
    'lychee', 'mandarine', 'mango', 'mulberry', 'nectarine', 'nut', 'olive',
    'orange', 'pamelo', 'papaya', 'passionfruit', 'peach', 'pear',
    'persimmon', 'physalis', 'pineapple', 'plum', 'pomegranate', 'pomelo',
    'purple mangosteen', 'quince', 'raisin', 'rambutan', 'raspberry',
    'redcurrant', 'rock melon', 'salal berry', 'satsuma', 'star fruit',
    'strawberry', 'tamarillo', 'tangerine', 'tomato', 'ugli fruit',
    'watermelon'
]

print(f"We have {len(fruit)} fruits")
print("First 10:", fruit[:10])
```

### Combining Strings

We can join strings together using the `+` operator or the `.join()`
method:

``` python
# Using + operator
print("pine" + "apple")

# Adding multiple strings
print("pine" + "apple" + "s")

# With spaces
print("crab" + " " + "apple")

# Using join for multiple items
words = ["pine", "apple"]
print("".join(words))  # No separator
print(" ".join(words))  # With space separator
```

**Question 3.2: Combine all of the fruit in the `fruit` list into a
single string, delineated by commas.**

``` python
# Your code here
# Hint: Use ", ".join()
```

### Pattern Matching in Strings

The basic idea is that we take a **string** (or list of strings) and
apply some sort of **pattern** to it. We can:

-   Filter items that match the pattern
-   Get True/False for every item
-   Extract the pattern itself from every item

This is handy for filtering data or creating new variables from messy
text.

Let\'s begin by looking at fruits starting with the letter \"a\":

``` python
# Filter fruits starting with 'a'
a_fruits = [f for f in fruit if f.startswith('a')]
print("Fruits starting with 'a':", a_fruits)
```

We can also check each item and get True/False:

``` python
# Check which fruits start with 'a'
starts_with_a = [f.startswith('a') for f in fruit]
print("First 10 results:", starts_with_a[:10])
```

If we have a DataFrame of fruit, we can use this with filtering:

``` python
fruit_data = pd.DataFrame({'fruit': fruit})
fruit_data[fruit_data['fruit'].str.startswith('a')]
```

**Question 3.3: Find all the fruit names that end with \"a\". Do this
with both the `fruit` list and `fruit_data` DataFrame.**

``` python
# Your code here
# Hint: Use .endswith() for lists, .str.endswith() for DataFrames
```

### Regular Expressions

For more complex patterns, we use **regular expressions** (regex).
Let\'s extract particular patterns using the `re` module:

``` python
import re

# Extract patterns: 'fruit', 'berry', or 'melon'
pattern = r'fruit|berry|melon'

# Extract for each fruit name
extracted = [re.search(pattern, f).group() if re.search(pattern, f) else None
             for f in fruit]

# Show some examples
for i in range(10):
    print(f"{fruit[i]:20s} -> {extracted[i]}")
```

**Question 3.4: Make a bar chart using these extracted elements. You can
add any other elements that you\'re interested in to the pattern.**

``` python
# Your code here
# Hint: Create a DataFrame with the extracted patterns, then use value_counts()
```

## Exercises

Python has many string methods built in. These exercises are meant to
familiarize you with a few of them.

**Question 3.5: Substrings. Extract the first letter of each fruit. Make
a bar chart of initial letter frequencies.**

Hint: Use string slicing with `[0]`

``` python
# Your code here
```

**Question 3.6: Splitting strings. Try out `.split()` on the
`best_coast` data below. Can you turn city and state into separate
columns of a DataFrame?**

``` python
best_coast = ["Seattle, WA", "Portland, OR", "San Francisco, CA", "Vancouver, BC"]

# Your code here
# Hint: Use .split(", ") to split on comma+space
```

### Going Further with Text Data

If you want to get fancy with extracting bits of strings, you\'ll need
to learn more about **regex** (regular expressions). Regex is a powerful
way of representing complex patterns.

Useful resources:

-   Python regex documentation:
    <https://docs.python.org/3/library/re.html>
-   Interactive regex tester: <https://regex101.com/>
-   Python string methods:
    <https://docs.python.org/3/library/stdtypes.html#string-methods>

For more advanced text analysis (word counts, sentiment analysis, etc.),
check out:

-   **NLTK** (Natural Language Toolkit): <https://www.nltk.org/>
-   **spaCy**: <https://spacy.io/>
-   **TextBlob**: <https://textblob.readthedocs.io/>

## Hints {#hints}

**1.3** Scalars don\'t have a length - they\'re single values. You\'ll
get an error if you try `len()` on a number.

**1.6**
`tree_data['growth_per_year'] = tree_data['tree_heights'] / tree_data['tree_ages']`

**2.4** For a dot plot:

``` python
plt.figure(figsize=(10, 8))
plt.scatter(gapminder_asia_2007['variable'], gapminder_asia_2007['country'])
plt.xlabel('Variable Name')
plt.ylabel('Country')
plt.show()
```

**2.5** To reorder:

``` python
asia_sorted = gapminder_asia_2007.sort_values('variable_name')
asia_sorted['country'] = pd.Categorical(asia_sorted['country'],
                                        categories=asia_sorted['country'].unique(),
                                        ordered=True)
```

**3.2** `", ".join(fruit)`

**3.4**

``` python
fruit_data['type'] = [re.search(pattern, f).group() if re.search(pattern, f) else 'other'
                      for f in fruit]
fruit_data['type'].value_counts().plot(kind='bar')
```

**3.6** One way to do it:

``` python
cities = [x.split(", ")[0] for x in best_coast]
states = [x.split(", ")[1] for x in best_coast]
coast_df = pd.DataFrame({'city': cities, 'state': states})
```

# Collecting Data Using the Internet

The architecture of the Internet shapes the ways we can collect data
from it. We\'ll introduce you to two ways of getting data from the
Internet:

1.  **Web scraping**
2.  **Application Programming Interfaces (APIs)**

Web scraping is made possible by the front-end structure of a web
page---the HTML and CSS that make up most of what you see on the
Internet.

Web APIs are structured ways of making web requests. This is how
websites communicate with databases and with each other; most data is
transmitted over the Internet in this way.

## Setup {#setup}

To collect Internet data, we\'ll use several Python packages:

-   **requests**: For making HTTP requests (like R\'s `httr`)
-   **BeautifulSoup**: For parsing HTML and web scraping (like R\'s
    `rvest`)
-   **pandas**: For working with data

You may need to install these packages first.

``` python
# Uncomment to install packages if needed:
# !pip install requests beautifulsoup4 lxml pandas

import requests
from bs4 import BeautifulSoup
import pandas as pd
import json
import matplotlib.pyplot as plt
import seaborn as sns

# Set style
sns.set_style("whitegrid")
%matplotlib inline

print("Packages loaded successfully!")
```

    Requirement already satisfied: requests in /usr/local/lib/python3.12/dist-packages (2.32.4)
    Requirement already satisfied: beautifulsoup4 in /usr/local/lib/python3.12/dist-packages (4.13.5)
    Requirement already satisfied: lxml in /usr/local/lib/python3.12/dist-packages (6.0.2)
    Requirement already satisfied: pandas in /usr/local/lib/python3.12/dist-packages (2.2.2)
    Requirement already satisfied: charset_normalizer<4,>=2 in /usr/local/lib/python3.12/dist-packages (from requests) (3.4.4)
    Requirement already satisfied: idna<4,>=2.5 in /usr/local/lib/python3.12/dist-packages (from requests) (3.11)
    Requirement already satisfied: urllib3<3,>=1.21.1 in /usr/local/lib/python3.12/dist-packages (from requests) (2.5.0)
    Requirement already satisfied: certifi>=2017.4.17 in /usr/local/lib/python3.12/dist-packages (from requests) (2026.1.4)
    Requirement already satisfied: soupsieve>1.2 in /usr/local/lib/python3.12/dist-packages (from beautifulsoup4) (2.8.3)
    Requirement already satisfied: typing-extensions>=4.0.0 in /usr/local/lib/python3.12/dist-packages (from beautifulsoup4) (4.15.0)
    Requirement already satisfied: numpy>=1.26.0 in /usr/local/lib/python3.12/dist-packages (from pandas) (2.0.2)
    Requirement already satisfied: python-dateutil>=2.8.2 in /usr/local/lib/python3.12/dist-packages (from pandas) (2.9.0.post0)
    Requirement already satisfied: pytz>=2020.1 in /usr/local/lib/python3.12/dist-packages (from pandas) (2025.2)
    Requirement already satisfied: tzdata>=2022.7 in /usr/local/lib/python3.12/dist-packages (from pandas) (2025.3)
    Requirement already satisfied: six>=1.5 in /usr/local/lib/python3.12/dist-packages (from python-dateutil>=2.8.2->pandas) (1.17.0)
    Packages loaded successfully!

## Web Scraping

This example is inspired by tutorials on web scraping, adapted for
Python.

We\'ll extract a table from this Wikipedia page:
<https://en.wikipedia.org/wiki/World_Health_Organization_ranking_of_health_systems_in_2000>

First, have a look at the page in a web browser. Then right-click and
hit \"Inspect\" (or \"Inspect Element\") to look at the underlying HTML.

Then, read the page into Python using `requests.get()` and parse it with
BeautifulSoup.

``` python
# Get the webpage
url = "https://en.wikipedia.org/wiki/World_Health_Organization_ranking_of_health_systems_in_2000"
headers = {
    'User-Agent': 'Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/91.0.4472.124 Safari/537.36'
}
response = requests.get(url, headers=headers)

# Parse the HTML
soup = BeautifulSoup(response.content, 'html.parser')

print(f"Status code: {response.status_code}")
# Check if soup.title is not None before accessing .string
if soup.title:
    print(f"Page title: {soup.title.string}")
else:
    print("Page title could not be found.")
```

    Status code: 200
    Page title: World Health Organization ranking of health systems in 2000 - Wikipedia

There are multiple ways to identify and select HTML elements:

-   **CSS selectors**: Using `.select()` or `.select_one()`
-   **Tag names**: Using `.find()` or `.find_all()`
-   **Attributes**: Using parameters like `class_`, `id`, etc.

Let\'s find the table on this page:

``` python
# Method 1: Find by CSS selector (inspect the page to get this)
# table = soup.select_one('#mw-content-text > div > table')

# Method 2: Find the first table with class 'wikitable'
table = soup.find('table', class_='wikitable')

print("Found table:", table is not None)
```

    Found table: True

Now let\'s parse this table into a pandas DataFrame. Pandas has a
built-in function `read_html()` that can extract tables from HTML:

``` python
import io

# Method 1: Use pandas read_html (easiest!)
# Pass the HTML content we already fetched with the User-Agent header
health_rankings = pd.read_html(io.StringIO(response.text))[0]  # Get the first table

print(f"Shape: {health_rankings.shape}")
health_rankings.head(10)
```

    Shape: (191, 7)

    /tmp/ipython-input-1119983338.py:3: FutureWarning: Passing literal html to 'read_html' is deprecated and will be removed in a future version. To read from a literal string, wrap it in a 'StringIO' object.
      health_rankings = pd.read_html(response.text)[0]  # Get the first table

``` json
{"summary":"{\n  \"name\": \"health_rankings\",\n  \"rows\": 191,\n  \"fields\": [\n    {\n      \"column\": \"Country\",\n      \"properties\": {\n        \"dtype\": \"string\",\n        \"num_unique_values\": 191,\n        \"samples\": [\n          \"Singapore\",\n          \"Iceland\",\n          \"South Korea[4]\"\n        ],\n        \"semantic_type\": \"\",\n        \"description\": \"\"\n      }\n    },\n    {\n      \"column\": \"Attainment of goals / Health / Level (DALE)\",\n      \"properties\": {\n        \"dtype\": \"number\",\n        \"std\": 55,\n        \"min\": 1,\n        \"max\": 191,\n        \"num_unique_values\": 188,\n        \"samples\": [\n          116,\n          8,\n          157\n        ],\n        \"semantic_type\": \"\",\n        \"description\": \"\"\n      }\n    },\n    {\n      \"column\": \"Attainment of goals / Health / Distribution\",\n      \"properties\": {\n        \"dtype\": \"number\",\n        \"std\": 55,\n        \"min\": 0,\n        \"max\": 191,\n        \"num_unique_values\": 188,\n        \"samples\": [\n          104,\n          10,\n          158\n        ],\n        \"semantic_type\": \"\",\n        \"description\": \"\"\n      }\n    },\n    {\n      \"column\": \"Attainment of goals / Health / Overall goal attainment\",\n      \"properties\": {\n        \"dtype\": \"number\",\n        \"std\": 55,\n        \"min\": 1,\n        \"max\": 191,\n        \"num_unique_values\": 190,\n        \"samples\": [\n          120,\n          15,\n          91\n        ],\n        \"semantic_type\": \"\",\n        \"description\": \"\"\n      }\n    },\n    {\n      \"column\": \"Health expenditure per capita in international dollars\",\n      \"properties\": {\n        \"dtype\": \"number\",\n        \"std\": 55,\n        \"min\": 1,\n        \"max\": 191,\n        \"num_unique_values\": 189,\n        \"samples\": [\n          147,\n          2,\n          171\n        ],\n        \"semantic_type\": \"\",\n        \"description\": \"\"\n      }\n    },\n    {\n      \"column\": \"Performance / On level of health\",\n      \"properties\": {\n        \"dtype\": \"number\",\n        \"std\": 55,\n        \"min\": 1,\n        \"max\": 191,\n        \"num_unique_values\": 191,\n        \"samples\": [\n          14,\n          27,\n          107\n        ],\n        \"semantic_type\": \"\",\n        \"description\": \"\"\n      }\n    },\n    {\n      \"column\": \"Performance / Overall health system performance\",\n      \"properties\": {\n        \"dtype\": \"number\",\n        \"std\": 55,\n        \"min\": 1,\n        \"max\": 191,\n        \"num_unique_values\": 190,\n        \"samples\": [\n          136,\n          37,\n          101\n        ],\n        \"semantic_type\": \"\",\n        \"description\": \"\"\n      }\n    }\n  ]\n}","type":"dataframe","variable_name":"health_rankings"}
```

### Alternative: Manual table parsing

Sometimes you need to parse a table manually if it has complex structure
or if `read_html()` doesn\'t work well:

``` python
# Find all rows in the table
rows = table.find_all('tr')

# Extract headers
headers = [th.text.strip() for th in rows[0].find_all('th')]
print("Headers:", headers)

# Extract data rows
data = []
for row in rows[1:]:  # Skip header row
    cols = row.find_all('td')
    if cols:  # Only if row has data
        data.append([col.text.strip() for col in cols])

# Create DataFrame
health_rankings_manual = pd.DataFrame(data, columns=headers)
print(f"\nShape: {health_rankings_manual.shape}")
health_rankings_manual.head()
```

    Headers: ['Country', 'Attainment of goals / Health / Level (DALE)', 'Attainment of goals / Health / Distribution', 'Attainment of goals / Health / Overall goal attainment', 'Health expenditure per capita in international dollars', 'Performance / On level of health', 'Performance / Overall health system performance']

    Shape: (191, 7)

``` json
{"summary":"{\n  \"name\": \"health_rankings_manual\",\n  \"rows\": 191,\n  \"fields\": [\n    {\n      \"column\": \"Country\",\n      \"properties\": {\n        \"dtype\": \"string\",\n        \"num_unique_values\": 191,\n        \"samples\": [\n          \"Singapore\",\n          \"Iceland\",\n          \"South Korea[4]\"\n        ],\n        \"semantic_type\": \"\",\n        \"description\": \"\"\n      }\n    },\n    {\n      \"column\": \"Attainment of goals / Health / Level (DALE)\",\n      \"properties\": {\n        \"dtype\": \"string\",\n        \"num_unique_values\": 188,\n        \"samples\": [\n          \"116\",\n          \"8\",\n          \"157\"\n        ],\n        \"semantic_type\": \"\",\n        \"description\": \"\"\n      }\n    },\n    {\n      \"column\": \"Attainment of goals / Health / Distribution\",\n      \"properties\": {\n        \"dtype\": \"string\",\n        \"num_unique_values\": 188,\n        \"samples\": [\n          \"104\",\n          \"10\",\n          \"158\"\n        ],\n        \"semantic_type\": \"\",\n        \"description\": \"\"\n      }\n    },\n    {\n      \"column\": \"Attainment of goals / Health / Overall goal attainment\",\n      \"properties\": {\n        \"dtype\": \"string\",\n        \"num_unique_values\": 190,\n        \"samples\": [\n          \"120\",\n          \"15\",\n          \"91\"\n        ],\n        \"semantic_type\": \"\",\n        \"description\": \"\"\n      }\n    },\n    {\n      \"column\": \"Health expenditure per capita in international dollars\",\n      \"properties\": {\n        \"dtype\": \"string\",\n        \"num_unique_values\": 189,\n        \"samples\": [\n          \"147\",\n          \"2\",\n          \"171\"\n        ],\n        \"semantic_type\": \"\",\n        \"description\": \"\"\n      }\n    },\n    {\n      \"column\": \"Performance / On level of health\",\n      \"properties\": {\n        \"dtype\": \"string\",\n        \"num_unique_values\": 191,\n        \"samples\": [\n          \"14\",\n          \"27\",\n          \"107\"\n        ],\n        \"semantic_type\": \"\",\n        \"description\": \"\"\n      }\n    },\n    {\n      \"column\": \"Performance / Overall health system performance\",\n      \"properties\": {\n        \"dtype\": \"string\",\n        \"num_unique_values\": 190,\n        \"samples\": [\n          \"136\",\n          \"37\",\n          \"101\"\n        ],\n        \"semantic_type\": \"\",\n        \"description\": \"\"\n      }\n    }\n  ]\n}","type":"dataframe","variable_name":"health_rankings_manual"}
```

### Exercise: Try out web scraping

Now try this out on a new web page.

Read in this Wikipedia page listing US cities by population:
<https://en.wikipedia.org/wiki/List_of_United_States_cities_by_population>

Extract the first table (the full list of cities) from it and parse it
into a DataFrame. Look at the DataFrame, and pay attention to the data
types. Do you see anything you\'d need to process further before making
any plots of this data? (You don\'t actually have to process or plot the
data.)

You can extract a table from a different web page instead, if you wish.

``` python
# Write your code here
```

## APIs and Web Requests

### HTTP Verbs and Status Codes

HTTP is a protocol which underlies the web. You make a **request** to a
particular URL and get a **response** back.

The methods for making requests are called verbs: GET, POST, PUT,
DELETE\...

Common status codes:

-   **200**: OK (success)
-   **404**: Not Found
-   **500**: Server Error

A basic example:

``` python
# Make a GET request
r = requests.get("https://http.cat/200")

print(f"Status code: {r.status_code}")
print(f"Headers: {dict(r.headers)}")
print(f"Content type: {r.headers['Content-Type']}")
```

    Status code: 200
    Headers: {'Date': 'Sun, 08 Feb 2026 21:56:35 GMT', 'Content-Type': 'image/jpeg', 'Content-Length': '31128', 'Connection': 'keep-alive', 'Server': 'cloudflare', 'last-modified': 'Sun, 01 Feb 2026 21:34:48 GMT', 'etag': '"697fc6f8-7998"', 'expires': 'Thu, 31 Dec 2037 23:55:55 GMT', 'Cache-Control': 'max-age=315360000', 'Accept-Ranges': 'bytes', 'Age': '85643', 'cf-cache-status': 'HIT', 'Nel': '{"report_to":"cf-nel","success_fraction":0.0,"max_age":604800}', 'Report-To': '{"group":"cf-nel","max_age":604800,"endpoints":[{"url":"https://a.nel.cloudflare.com/report/v4?s=fhX7Lt%2FohE7GrenMW%2FOSr1mrmkyjOOb0tE0AIlX6HrMVsnntr5anHGw5leoOsWBE5hn%2BQ4FHzw7sUUGU3YolDvLUz8h0LLxR"}]}', 'CF-RAY': '9cae60b7ea499b6b-SEA', 'alt-svc': 'h3=":443"; ma=86400'}
    Content type: image/jpeg

This particular URL returns an image. Let\'s save it:

``` python
# Save the image
with open('200.jpg', 'wb') as f:
    f.write(r.content)

print("Image saved as 200.jpg")
print(f"File size: {len(r.content)} bytes")
```

    Image saved as 200.jpg
    File size: 31128 bytes

### Paths and Query Parameters

The World Bank has a database of information about different countries:
<https://datahelpdesk.worldbank.org/knowledgebase/topics/125589>

To get data from the World Bank API, we need to build a URL. In addition
to the base website name, this can have two trailing components:

-   A **path**, separated with slashes (like `/path/to/resource`)
-   A **query**, separated with `?` and `&` (like
    `?key1=value1&key2=value2`)

In Python\'s `requests` library, we can use the `params` parameter to
add query parameters:

``` python
# The base URL
wb_url = "http://api.worldbank.org/v2/country/us"

# Query parameters as a dictionary
wb_params = {
    'format': 'json'
}

# Make the request
r2 = requests.get(wb_url, params=wb_params)

print(f"Status code: {r2.status_code}")
print(f"Final URL: {r2.url}")
```

    Status code: 200
    Final URL: https://api.worldbank.org/v2/country/us?format=json

Let\'s look at the JSON response in a pretty format:

``` python
# Parse JSON and pretty print
data = r2.json()
print(json.dumps(data, indent=2))
```

    [
      {
        "page": 1,
        "pages": 1,
        "per_page": "50",
        "total": 1
      },
      [
        {
          "id": "USA",
          "iso2Code": "US",
          "name": "United States",
          "region": {
            "id": "NAC",
            "iso2code": "XU",
            "value": "North America"
          },
          "adminregion": {
            "id": "",
            "iso2code": "",
            "value": ""
          },
          "incomeLevel": {
            "id": "HIC",
            "iso2code": "XD",
            "value": "High income"
          },
          "lendingType": {
            "id": "LNX",
            "iso2code": "XX",
            "value": "Not classified"
          },
          "capitalCity": "Washington D.C.",
          "longitude": "-77.032",
          "latitude": "38.8895"
        }
      ]
    ]

### Exercise: Population of a Country

The World Bank has data on country populations over time. To access
this, we need a different path.

The path should be: `country/us/indicator/SP.POP.TOTL`

**Write a new request to get this data:**

``` python
# Write your code here
# new_url = "http://api.worldbank.org/v2/country/us/indicator/SP.POP.TOTL"
# params = {'format': 'json', 'per_page': 100}
# r3 = requests.get(new_url, params=params)
```

Now extract the data into a DataFrame:

``` python
# Uncomment and complete this code:
# data = r3.json()
# df = pd.DataFrame(data[1])  # The second element contains the actual data
# df.head()
```

**Once you\'ve extracted the DataFrame, make a line plot of population
growth over time:**

``` python
# Write your code here
# Hint: You may need to convert 'date' to numeric and 'value' to numeric
# df['date'] = pd.to_numeric(df['date'])
# df['value'] = pd.to_numeric(df['value'])
# df = df.sort_values('date')
# plt.figure(figsize=(12, 6))
# plt.plot(df['date'], df['value'])
# plt.xlabel('Year')
# plt.ylabel('Population')
# plt.title('US Population Over Time')
# plt.show()
```

## Challenge: Authentication

Many APIs require some form of **authentication** to access. The
simplest form of authentication is through an API key, which you send as
a query parameter or header along with your request.

### Example: Using an API key

Here\'s a general pattern for using API keys:

``` python
# Method 1: As a query parameter
params = {
    'api_key': 'YOUR_API_KEY_HERE',
    'other_param': 'value'
}
response = requests.get(url, params=params)

# Method 2: As a header
headers = {
    'Authorization': 'Bearer YOUR_API_KEY_HERE'
}
response = requests.get(url, headers=headers)
```

### API Options to Try

Choose one of these APIs to practice with:

**1. OpenWeatherMap API** (Free tier available):

-   Sign up: <https://openweathermap.org/api>
-   Get current weather for a city

**2. NASA APIs** (No auth required for some endpoints):

-   Explore: <https://api.nasa.gov/>
-   Try the APOD (Astronomy Picture of the Day) API

**3. The Movie Database (TMDb)** (Free API key):

-   Sign up: <https://www.themoviedb.org/settings/api>
-   Search for movies and get details

**Note**: Be careful with APIs that require credit cards. Always read
the terms of service and pricing information.

``` python
# Write your API code here
# Example with a hypothetical API:
# api_key = "YOUR_API_KEY"
# url = "https://api.example.com/data"
# params = {'api_key': api_key, 'query': 'something'}
# response = requests.get(url, params=params)
# data = response.json()
```

## More APIs

Most major websites have some sort of public API now. In some cases,
there are Python packages designed to make working with those APIs
easier. In each case, you\'ll have to read the documentation to figure
out how to use the API. That documentation is usually written for
application developers, *not* for researchers or data scientists.

### Social Media APIs

**Twitter (X)**: <https://developer.twitter.com/en/docs>

-   Python library: `tweepy`
-   Note: API access policies have changed significantly

**Reddit**: <https://www.reddit.com/dev/api/>

-   Python library: `praw` (Python Reddit API Wrapper)
-   More accessible than some other social media APIs

**Mastodon**: <https://docs.joinmastodon.org/api/>

-   Python library: `Mastodon.py`
-   Open-source alternative to Twitter

### News and Content APIs

**The New York Times**: <https://developer.nytimes.com/>

-   Free API key for personal use
-   Article search, book reviews, movie reviews, etc.

**The Guardian**: <https://open-platform.theguardian.com/>

-   Free API access
-   Article search and content API

### Other Useful APIs

**GitHub**: <https://docs.github.com/en/rest>

-   Python library: `PyGithub`
-   Repository data, user data, etc.

**Spotify**: <https://developer.spotify.com/documentation/web-api/>

-   Python library: `spotipy`
-   Music data, playlists, audio features

**Yelp**: <https://www.yelp.com/developers/documentation/v3>

-   Business and review data
-   Free API key with rate limits

### Important Notes

-   **Rate limits**: Most APIs limit how many requests you can make per
    hour/day
-   **Terms of service**: Always read and follow the API\'s terms of
    service
-   **Authentication**: Many APIs require OAuth or API keys
-   **Changes**: API endpoints and requirements can change, so tutorials
    may become outdated
-   **Ethics**: Just because you *can* scrape or access data doesn\'t
    mean you *should*. Consider privacy, consent, and the impact of your
    data collection.

## Best Practices for Web Scraping and APIs

### Web Scraping Ethics

1.  **Check robots.txt**: Look at `website.com/robots.txt` to see
    what\'s allowed
2.  **Respect rate limits**: Don\'t overwhelm servers with too many
    requests
3.  **Use appropriate delays**: Add `time.sleep()` between requests
4.  **Check terms of service**: Some sites prohibit scraping
5.  **Identify yourself**: Use a custom User-Agent string

### Example: Adding delays and custom headers

``` python
import time

# Custom headers to identify yourself
headers = {
    'User-Agent': 'Educational Research Bot (your.email@example.com)'
}

# Example: Making polite requests with delays
urls = [
    'https://example.com/page1',
    'https://example.com/page2',
]

# for url in urls:
#     response = requests.get(url, headers=headers)
#     # Process the response
#     time.sleep(1)  # Wait 1 second between requests

print("Always be respectful when scraping!")
```

    Always be respectful when scraping!

## Additional Resources

### Web Scraping {#web-scraping}

-   **Beautiful Soup Documentation**:
    <https://www.crummy.com/software/BeautifulSoup/bs4/doc/>
-   **Requests Documentation**: <https://requests.readthedocs.io/>
-   **Scrapy** (for larger projects): <https://scrapy.org/>
-   **Selenium** (for JavaScript-heavy sites):
    <https://selenium-python.readthedocs.io/>

### APIs

-   **Public APIs List**: <https://github.com/public-apis/public-apis>
-   **REST API Tutorial**: <https://restfulapi.net/>
-   **JSON Documentation**: <https://www.json.org/>

### Legal and Ethical Considerations

-   Always check a website\'s `robots.txt` file
-   Review terms of service before scraping
-   Consider reaching out to website owners for permission
-   Be mindful of copyright and data privacy laws
-   Think about the ethical implications of your data collection

# Political Ads & Merging Data {#political-ads--merging-data}

------------------------------------------------------------------------

## Goals {#goals}

-   To familiarize you with audits of political advertising online
-   To teach you how to combine and join data sets

## Background on Facebook Ads

There are two different databases of advertisements with political
content on Facebook.

**First**, from ProPublica:
<http://projects.propublica.org/facebook-ads/>

**Second**, from Facebook (now Meta):
<https://www.facebook.com/ads/library/>

ProPublica offers its data for download in a CSV; Facebook does not
always make this easy. However, researchers from NYU have scraped data
from the Facebook database, and they have publicized it for researchers.
You can read about their research in the New York Times here, in an
article that provides context for the creation of the database:
<https://www.nytimes.com/2018/07/17/technology/political-ads-facebook-trump.html>

### Questions: Data Provenance

Spend a few minutes on each database webpage. Search for and look at
different ads, then answer these questions:

-   Why do you think there are two databases of political ads on
    Facebook?
-   What\'s different about how these databases were created and how ads
    were added to them?
-   What kinds of things can you search for? Which, in your opinion, is
    easier to use? Which is more transparent?

*\[Write your answers here\]*

## Setup and Data

We will use data from the **Online Political Ads Transparency Project**,
by Laura Edelson, Shikhar Sakhuja, and Damon McCoy from NYU. Their
project homepage is here: <https://online-pol-ads.github.io/>

All of the CSV files we\'ll use are stored on this page:
<https://github.com/online-pol-ads/FBPoliticalAds/tree/master/RawContentFiles>

You can download the CSV files using their URLs, or download the entire
repository and put the data in a data subfolder of your lab project.

``` python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns

# Set style
sns.set_style("whitegrid")
%matplotlib inline

print("Packages loaded successfully!")
```

    Packages loaded successfully!

``` python
# Option 1: Load from GitHub (uncomment to use)
base_dir = "https://raw.githubusercontent.com/online-pol-ads/FBPoliticalAds/master/RawContentFiles"

# Option 2: Load from local data folder
# base_dir = "data"

# Load ads data from multiple files
ads = pd.read_csv(f"{base_dir}/ads.csv")
ads2 = pd.read_csv(f"{base_dir}/ads2.csv", names=ads.columns, header=0)
ads3 = pd.read_csv(f"{base_dir}/ads3.csv", names=ads.columns, header=0)

# Load ad sponsors
ad_sponsors = pd.read_csv(f"{base_dir}/ad_sponsors.csv")

# Load snapshots
snapshots = pd.read_csv(f"{base_dir}/snapshots.csv")

print("Data loaded successfully!")
print(f"ads shape: {ads.shape}")
print(f"ads2 shape: {ads2.shape}")
print(f"ads3 shape: {ads3.shape}")
```

    Data loaded successfully!
    ads shape: (149999, 11)
    ads2 shape: (149999, 11)
    ads3 shape: (148016, 11)

## Combining More of the Same Data: `pd.concat()` {#combining-more-of-the-same-data-pdconcat}

We\'ll start by looking at the ads data.

If different DataFrames are just more observations of the same data, you
can stack them on top of each other using `pd.concat()`. The DataFrames
need to have the same columns!

This is equivalent to R\'s `bind_rows()`.

``` python
# Concatenate (stack) the three DataFrames
ads_all = pd.concat([ads, ads2, ads3], ignore_index=True)

print(f"Combined shape: {ads_all.shape}")
```

    Combined shape: (448014, 11)

Let\'s see how well it worked, and look at the data with some helper
functions. Notice anything unusual about the number of unique IDs?

``` python
# Look at the data structure
print("\nDataFrame info:")
ads_all.info()

print(f"\nDimensions: {ads_all.shape}")
print(f"Number of rows: {len(ads_all)}")
print(f"Number of unique nyu_ids: {ads_all['nyu_id'].nunique()}")

# Display first few rows
ads_all.head()
```


    DataFrame info:
    <class 'pandas.core.frame.DataFrame'>
    RangeIndex: 448014 entries, 0 to 448013
    Data columns (total 11 columns):
     #   Column         Non-Null Count   Dtype  
    ---  ------         --------------   -----  
     0   archive_id     448014 non-null  int64  
     1   id             448014 non-null  int64  
     2   page_id        448014 non-null  int64  
     3   start_date     0 non-null       float64
     4   end_date       0 non-null       float64
     5   text           443634 non-null  object 
     6   image_url      318730 non-null  object 
     7   video_url      113221 non-null  object 
     8   ad_sponsor_id  448014 non-null  int64  
     9   nyu_id         448014 non-null  int64  
     10  has_cards      448014 non-null  object 
    dtypes: float64(2), int64(5), object(4)
    memory usage: 37.6+ MB

    Dimensions: (448014, 11)
    Number of rows: 448014
    Number of unique nyu_ids: 448014

``` json
{"type":"dataframe","variable_name":"ads_all"}
```

Notice that the number of unique IDs is less than the total number of
rows. This means there are duplicate entries!

## Merge Two Different Data Sets: `pd.merge()` {#merge-two-different-data-sets-pdmerge}

Now we\'ll introduce multiple tables with different units of
observation. This is called **relational data**. You *join* these
different tables of data using **keys**.

These are tricky concepts to understand. I recommend looking through the
diagrams here to get a better handle on different kinds of joins:

<https://pandas.pydata.org/docs/user_guide/merging.html>

or the R4DS chapter:
<https://r4ds.had.co.nz/relational-data.html#understanding-joins>

In the political ads data, each ad has a sponsor:

``` python
# Look at the ad_sponsors data
ad_sponsors.head()
```

``` json
{"summary":"{\n  \"name\": \"ad_sponsors\",\n  \"rows\": 13349,\n  \"fields\": [\n    {\n      \"column\": \"nyu_id\",\n      \"properties\": {\n        \"dtype\": \"number\",\n        \"std\": 3853,\n        \"min\": 1,\n        \"max\": 13349,\n        \"num_unique_values\": 13349,\n        \"samples\": [\n          5726,\n          7589,\n          5961\n        ],\n        \"semantic_type\": \"\",\n        \"description\": \"\"\n      }\n    },\n    {\n      \"column\": \"name\",\n      \"properties\": {\n        \"dtype\": \"string\",\n        \"num_unique_values\": 13348,\n        \"samples\": [\n          \"Committee to Elect Judy McCullough for Senate\",\n          \"Katie Reiter for State Representative, 30510 Red Maple Lane, Sfld., MI 48076\",\n          \"WomenStrong International\"\n        ],\n        \"semantic_type\": \"\",\n        \"description\": \"\"\n      }\n    }\n  ]\n}","type":"dataframe","variable_name":"ad_sponsors"}
```

In the `ads` data, these are represented by the ID only. If we join the
data, then we can match particular ads to their sponsors\' names.

First, let\'s rename the columns of `ad_sponsors` to make them clearer:

``` python
# Rename columns
ad_sponsors.columns = ['ad_sponsor_id', 'ad_sponsor_name']

ad_sponsors.head()
```

``` json
{"summary":"{\n  \"name\": \"ad_sponsors\",\n  \"rows\": 13349,\n  \"fields\": [\n    {\n      \"column\": \"ad_sponsor_id\",\n      \"properties\": {\n        \"dtype\": \"number\",\n        \"std\": 3853,\n        \"min\": 1,\n        \"max\": 13349,\n        \"num_unique_values\": 13349,\n        \"samples\": [\n          5726,\n          7589,\n          5961\n        ],\n        \"semantic_type\": \"\",\n        \"description\": \"\"\n      }\n    },\n    {\n      \"column\": \"ad_sponsor_name\",\n      \"properties\": {\n        \"dtype\": \"string\",\n        \"num_unique_values\": 13348,\n        \"samples\": [\n          \"Committee to Elect Judy McCullough for Senate\",\n          \"Katie Reiter for State Representative, 30510 Red Maple Lane, Sfld., MI 48076\",\n          \"WomenStrong International\"\n        ],\n        \"semantic_type\": \"\",\n        \"description\": \"\"\n      }\n    }\n  ]\n}","type":"dataframe","variable_name":"ad_sponsors"}
```

We want to keep all the rows of `ads_all`, so we use a **left** join.

In pandas:

-   `how='left'` is equivalent to R\'s `left_join()`
-   `how='right'` is equivalent to R\'s `right_join()`
-   `how='inner'` is equivalent to R\'s `inner_join()`
-   `how='outer'` is equivalent to R\'s `full_join()`

``` python
# Left join: keep all rows from ads_all
ads_with_sponsors = ads_all.merge(ad_sponsors,
                                  left_on='ad_sponsor_id',
                                  right_on='ad_sponsor_id',
                                  how='left')

print(f"Shape after join: {ads_with_sponsors.shape}")
ads_with_sponsors.head()
```

    Shape after join: (448014, 12)

``` json
{"type":"dataframe","variable_name":"ads_with_sponsors"}
```

Now we can ask, which sponsors have the most different ads?

``` python
# Count ads by sponsor and show top 10
(ads_with_sponsors['ad_sponsor_name']
 .value_counts()
 .head(10)
)
```

```{=html}
<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>count</th>
    </tr>
    <tr>
      <th>ad_sponsor_name</th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>the Trump Make America Great Again Committee</th>
      <td>16706</td>
    </tr>
    <tr>
      <th>Massoumi Web Holdings LLC</th>
      <td>15478</td>
    </tr>
    <tr>
      <th>California Counties Solar Program</th>
      <td>14262</td>
    </tr>
    <tr>
      <th>Donald J. Trump for President, Inc.</th>
      <td>10083</td>
    </tr>
    <tr>
      <th>TZ Insurance Solutions</th>
      <td>7481</td>
    </tr>
    <tr>
      <th>Nevada Counties Solar Program</th>
      <td>6286</td>
    </tr>
    <tr>
      <th>The Hill</th>
      <td>4346</td>
    </tr>
    <tr>
      <th>LifeZette Inc.</th>
      <td>4240</td>
    </tr>
    <tr>
      <th>Priorities USA Action and SMP. Not authorized by any candidate or candidate's committee.</th>
      <td>4049</td>
    </tr>
    <tr>
      <th>Planned Parenthood Federation of America</th>
      <td>3988</td>
    </tr>
  </tbody>
</table>
</div><br><label><b>dtype:</b> int64</label>
```

Alternative approach using groupby:

``` python
# Using groupby and count
(ads_with_sponsors
 .groupby('ad_sponsor_name')
 .size()
 .reset_index(name='n')
 .dropna()
 .sort_values('n', ascending=False)
 .head(10)
)
```

``` json
{"summary":"{\n  \"name\": \")\",\n  \"rows\": 10,\n  \"fields\": [\n    {\n      \"column\": \"ad_sponsor_name\",\n      \"properties\": {\n        \"dtype\": \"string\",\n        \"num_unique_values\": 10,\n        \"samples\": [\n          \"Priorities USA Action and SMP. Not authorized by any candidate or candidate's committee.\",\n          \"Massoumi Web Holdings LLC\",\n          \"Nevada Counties Solar Program\"\n        ],\n        \"semantic_type\": \"\",\n        \"description\": \"\"\n      }\n    },\n    {\n      \"column\": \"n\",\n      \"properties\": {\n        \"dtype\": \"number\",\n        \"std\": 5086,\n        \"min\": 3988,\n        \"max\": 16706,\n        \"num_unique_values\": 10,\n        \"samples\": [\n          4049,\n          15478,\n          6286\n        ],\n        \"semantic_type\": \"\",\n        \"description\": \"\"\n      }\n    }\n  ]\n}","type":"dataframe"}
```

## Snapshots and Impressions

Next, we\'ll combine our ad and sponsor information with `snapshots`
data on the price and number of impressions for each ad.

``` python
# Remove columns that are redundant
# Note: 'nyu_id' means something different in each data set!
ads_with_sponsors = ads_with_sponsors.drop(columns=['id', 'start_date', 'end_date', 'nyu_id'])

# Join snapshots with ads
# Rather than renaming columns, use left_on and right_on parameters
# to specify which columns to use as keys
snapshots_with_ads = snapshots.merge(ads_with_sponsors,
                                     left_on='ad_archive_id',
                                     right_on='archive_id',
                                     how='left')

print(f"Shape after join: {snapshots_with_ads.shape}")
snapshots_with_ads.head()
```

    Shape after join: (1000000, 17)

``` json
{"type":"dataframe","variable_name":"snapshots_with_ads"}
```

`.groupby()` and `.agg()` will let us sum up ads by sponsor:

``` python
# Group by sponsor and sum impressions and spending
sponsor_impressions = (snapshots_with_ads
                      .groupby('ad_sponsor_name')
                      .agg({
                          'min_impressions': 'sum',
                          'min_spend': 'sum'
                      })
                      .reset_index()
                      .dropna()
                      )

print(f"Number of sponsors: {len(sponsor_impressions)}")
sponsor_impressions.head(10)
```

    Number of sponsors: 11754

``` json
{"summary":"{\n  \"name\": \"sponsor_impressions\",\n  \"rows\": 11754,\n  \"fields\": [\n    {\n      \"column\": \"ad_sponsor_name\",\n      \"properties\": {\n        \"dtype\": \"string\",\n        \"num_unique_values\": 11754,\n        \"samples\": [\n          \"Jessica Stalder\",\n          \"the Collum for Idaho Campaign, Donna Pence Treasurer\",\n          \"Mark Brunton\"\n        ],\n        \"semantic_type\": \"\",\n        \"description\": \"\"\n      }\n    },\n    {\n      \"column\": \"min_impressions\",\n      \"properties\": {\n        \"dtype\": \"number\",\n        \"std\": 3375277,\n        \"min\": 0,\n        \"max\": 135655000,\n        \"num_unique_values\": 1493,\n        \"samples\": [\n          1379000,\n          2140000,\n          1494000\n        ],\n        \"semantic_type\": \"\",\n        \"description\": \"\"\n      }\n    },\n    {\n      \"column\": \"min_spend\",\n      \"properties\": {\n        \"dtype\": \"number\",\n        \"std\": 32185,\n        \"min\": 0,\n        \"max\": 1005400,\n        \"num_unique_values\": 593,\n        \"samples\": [\n          132700,\n          5900,\n          140300\n        ],\n        \"semantic_type\": \"\",\n        \"description\": \"\"\n      }\n    }\n  ]\n}","type":"dataframe","variable_name":"sponsor_impressions"}
```

Now let\'s visualize the relationship between spending and impressions:

``` python
# Scatterplot of spending vs impressions
plt.figure(figsize=(10, 6))
plt.scatter(sponsor_impressions['min_spend'],
           sponsor_impressions['min_impressions'],
           alpha=0.5)
plt.xlabel('Minimum Spend ($)')
plt.ylabel('Minimum Impressions')
plt.title('Relationship between Ad Spending and Impressions')
plt.tight_layout()
plt.show()

print("More money, more eyeballs.")
```

![](vertopal_9714c20675c04eeca65082f99a71713a/88c01762cce8b429729ba77bc6c54046c461da4e.png)

    More money, more eyeballs.

### Questions: Most Impressions

Write code to show the **top 25** sponsors by number of impressions,
using `.sort_values()` and `.head()`.

``` python
# Write your code here
# Hint: sponsor_impressions.sort_values('min_impressions', ascending=False).head(25)
```

**Discussion question**: Do some of these sponsors seem to be the same
or a closely related political entity? Which ones?

*\[Write your answer here\]*

## Challenge: Join More Data

`demo_group.csv` and `snapshot_demo.csv` contain information on
impressions broken down by demographic groups. See if you can join these
to the snapshot information from above to break down sponsors by
impressions.

**Important**: Be careful about what order you join data in. You may
want to use `how='right'` as well as `how='left'`.

R4DS has a drawing of the different tables in the `nycflights13` data
showing how they relate
(<https://r4ds.had.co.nz/relational-data.html#nycflights13-relational>);
consider sketching out something similar for the political ads data as
you work with more tables.

**Research questions**:

-   What do the impressions for the Planned Parenthood Federation of
    America look like for different demographic groups?
-   Which groups does the NRA target?
-   Are they different?

``` python
# Load the demographic data
# demo_group = pd.read_csv(f"{base_dir}/demo_group.csv")
# snapshot_demo = pd.read_csv(f"{base_dir}/snapshot_demo.csv")

# Write your code here to join and analyze the data
```

## Summary: Join Operations in Pandas

Here\'s a quick reference for joining data in pandas:

### Basic Syntax

``` python
# Join two DataFrames
result = df1.merge(df2,
                   left_on='key_column_in_df1',
                   right_on='key_column_in_df2',
                   how='left')  # or 'right', 'inner', 'outer'
```

### Types of Joins

  pandas          R (dplyr)        Description
  --------------- ---------------- ------------------------------------
  `how='left'`    `left_join()`    Keep all rows from left DataFrame
  `how='right'`   `right_join()`   Keep all rows from right DataFrame
  `how='inner'`   `inner_join()`   Keep only matching rows
  `how='outer'`   `full_join()`    Keep all rows from both

### Combining DataFrames (Stacking)

  ---------------------------------------------------------------------------------------
  pandas                            R (dplyr)                Description
  --------------------------------- ------------------------ ----------------------------
  `pd.concat([df1, df2])`           `bind_rows()`            Stack DataFrames vertically

  `pd.concat([df1, df2], axis=1)`   `bind_cols()`            Combine DataFrames
                                                             horizontally
  ---------------------------------------------------------------------------------------

### When to Use Each Join

-   **Left join**: When you want to keep all records from your main
    dataset and add information from another dataset
-   **Right join**: Less common, but useful when the right DataFrame is
    your primary dataset
-   **Inner join**: When you only want records that appear in both
    datasets
-   **Outer join**: When you want to keep all records from both
    datasets, even if they don\'t match

## Additional Resources {#additional-resources}

### Pandas Documentation

-   **Merging and Joining**:
    <https://pandas.pydata.org/docs/user_guide/merging.html>
-   **GroupBy Operations**:
    <https://pandas.pydata.org/docs/user_guide/groupby.html>

### Understanding Relational Data

-   **R for Data Science** (concepts apply to pandas too):
    <https://r4ds.had.co.nz/relational-data.html>
-   **Visual Join Diagrams**:
    <https://www.datasciencemadesimple.com/join-in-pandas-python-pandas-join-merge-and-concatenate/>

### Political Ads Research

-   **NYU Online Political Ads Project**:
    <https://online-pol-ads.github.io/>
-   **Facebook Ad Library**: <https://www.facebook.com/ads/library/>
-   **ProPublica Political Ads**:
    <http://projects.propublica.org/facebook-ads/>

### Critical Thinking About Data

As you work with this political advertising data, consider:

1.  **Data Quality**: What might be missing from these datasets? What
    can\'t we see?
2.  **Power Dynamics**: Who controls access to this data? Why does it
    matter that researchers had to scrape this information?
3.  **Social Impact**: How does political advertising on social media
    affect democracy and public discourse?
4.  **Methodology**: What are the limitations of studying ads through
    databases like these? What questions can and can\'t we answer?
5.  **Ethics**: What are the ethical considerations in collecting,
    analyzing, and publicizing this data?

# Social Networks

------------------------------------------------------------------------

These exercises are based on a workshop written and taught by Alex
Hanna, Pablo Barberá, and Dan Cervone:
<https://github.com/pablobarbera/data-science-workshop/tree/master/sna>

Adapted for Python using NetworkX.

## 0: Setup {#0-setup}

We\'ll use the **NetworkX** package to manipulate and visualize
networks. NetworkX is the standard network analysis library in Python.

You can read more about NetworkX here: <https://networkx.org/>

You\'ll need to install and load these packages:

``` python
# Uncomment to install packages if needed:
# !pip install networkx matplotlib pandas seaborn

import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
import networkx as nx
from networkx.algorithms import community

# Set style
sns.set_style("white")
%matplotlib inline

print("Packages loaded successfully!")
print(f"NetworkX version: {nx.__version__}")
```

    Requirement already satisfied: networkx in /usr/local/lib/python3.12/dist-packages (3.6.1)
    Requirement already satisfied: matplotlib in /usr/local/lib/python3.12/dist-packages (3.10.0)
    Requirement already satisfied: pandas in /usr/local/lib/python3.12/dist-packages (2.2.2)
    Requirement already satisfied: seaborn in /usr/local/lib/python3.12/dist-packages (0.13.2)
    Requirement already satisfied: contourpy>=1.0.1 in /usr/local/lib/python3.12/dist-packages (from matplotlib) (1.3.3)
    Requirement already satisfied: cycler>=0.10 in /usr/local/lib/python3.12/dist-packages (from matplotlib) (0.12.1)
    Requirement already satisfied: fonttools>=4.22.0 in /usr/local/lib/python3.12/dist-packages (from matplotlib) (4.61.1)
    Requirement already satisfied: kiwisolver>=1.3.1 in /usr/local/lib/python3.12/dist-packages (from matplotlib) (1.4.9)
    Requirement already satisfied: numpy>=1.23 in /usr/local/lib/python3.12/dist-packages (from matplotlib) (2.0.2)
    Requirement already satisfied: packaging>=20.0 in /usr/local/lib/python3.12/dist-packages (from matplotlib) (26.0)
    Requirement already satisfied: pillow>=8 in /usr/local/lib/python3.12/dist-packages (from matplotlib) (11.3.0)
    Requirement already satisfied: pyparsing>=2.3.1 in /usr/local/lib/python3.12/dist-packages (from matplotlib) (3.3.2)
    Requirement already satisfied: python-dateutil>=2.7 in /usr/local/lib/python3.12/dist-packages (from matplotlib) (2.9.0.post0)
    Requirement already satisfied: pytz>=2020.1 in /usr/local/lib/python3.12/dist-packages (from pandas) (2025.2)
    Requirement already satisfied: tzdata>=2022.7 in /usr/local/lib/python3.12/dist-packages (from pandas) (2025.3)
    Requirement already satisfied: six>=1.5 in /usr/local/lib/python3.12/dist-packages (from python-dateutil>=2.7->matplotlib) (1.17.0)
    Packages loaded successfully!
    NetworkX version: 3.6.1

``` python
from google.colab import drive
drive.mount('/content/drive')
```

    Mounted at /content/drive

## 1: Star Wars {#1-star-wars}

Our first example is a small network of character interactions in Star
Wars: Episode IV, described further here:
<https://cdn.rawgit.com/pablobarbera/data-science-workshop/master/sna/01_networks_intro.html>

### Look at the data: nodes and edges

First, read in the data. The data for this lesson is called
`lesson_7_data` and can be downloaded from the same Google Drive link
that contains the data from previous lessons, found here:
<https://drive.google.com/drive/u/2/folders/1zRIhA9QN5G6dZPjqk_Q7Ccy-HQQSHMua>.
There are **two** data sets: one of nodes, and one of edges.

``` python
# Read the data
nodes_sw = pd.read_csv("lesson_7_data/star-wars-network-nodes.csv")
edges_sw = pd.read_csv("lesson_7_data/star-wars-network-edges.csv")

print("Nodes data:")
print(nodes_sw.head())
print(f"\nNumber of nodes: {len(nodes_sw)}")

print("\nEdges data:")
print(edges_sw.head())
print(f"\nNumber of edges: {len(edges_sw)}")
```

    Nodes data:
              name  id
    0        R2-D2   0
    1    CHEWBACCA   1
    2        C-3PO   2
    3         LUKE   3
    4  DARTH VADER   4

    Number of nodes: 22

    Edges data:
        source target  weight
    0    C-3PO  R2-D2      17
    1     LUKE  R2-D2      13
    2  OBI-WAN  R2-D2       6
    3     LEIA  R2-D2       5
    4      HAN  R2-D2       5

    Number of edges: 60

**Look at both data sets and answer these questions:**

**1.1: How many characters are there? Which data set lists the
characters?**

*\[Your answer here\]*

**1.2: How many connections between the characters? Which data set lists
the connections?**

*\[Your answer here\]*

**1.3: Based on that, in your own words, what do you think a *node* is?
What\'s an *edge*?**

*\[Your answer here\]*

### Make a graph

When we combine the nodes and edges, we get a network object called a
**graph**.

In NetworkX, we can create graphs in several ways:

-   `nx.Graph()` for undirected graphs
-   `nx.DiGraph()` for directed graphs
-   `nx.from_pandas_edgelist()` to create from a DataFrame

``` python
# Create an undirected graph from the edge list
g_sw = nx.from_pandas_edgelist(edges_sw,
                               source='source',
                               target='target',
                               edge_attr='weight',
                               create_using=nx.Graph())

# Add node attributes from the nodes DataFrame
node_attrs = nodes_sw.set_index('name').to_dict('index')
nx.set_node_attributes(g_sw, node_attrs)

# Display graph info
print(f"Number of nodes: {g_sw.number_of_nodes()}")
print(f"Number of edges: {g_sw.number_of_edges()}")
print(f"\nNodes: {list(g_sw.nodes())[:5]}...")
print(f"\nEdges (first 5): {list(g_sw.edges())[:5]}")
```

    Number of nodes: 21
    Number of edges: 60

    Nodes: ['C-3PO', 'R2-D2', 'LUKE', 'OBI-WAN', 'LEIA']...

    Edges (first 5): [('C-3PO', 'R2-D2'), ('C-3PO', 'CHEWBACCA'), ('C-3PO', 'BERU'), ('C-3PO', 'LUKE'), ('C-3PO', 'OWEN')]

**1.4: This is an *undirected* graph. Why?**

*\[Your answer here - Hint: Think about whether the relationship between
characters is one-way or two-way\]*

### Plotting a graph

To make sense of network data, it\'s good to visualize it. NetworkX
provides several layout algorithms and drawing functions.

What\'s important:

-   **Layouts**: Where should the different nodes go? NetworkX has
    several layout algorithms:

    -   `spring_layout` (force-directed, like \"nicely\" or \"fr\" in R)
    -   `kamada_kawai_layout` (another force-directed algorithm)
    -   `circular_layout`, `random_layout`, etc.

-   Because layouts are often random, it\'s a good idea to set a
    **seed** so you get the same layout each time.

-   You draw nodes and edges separately with `nx.draw_networkx_nodes()`
    and `nx.draw_networkx_edges()`

``` python
# Set random seed for reproducibility
np.random.seed(123)

# Create layout
pos = nx.spring_layout(g_sw, seed=123)

# Create figure
plt.figure(figsize=(12, 8))

# Draw edges
nx.draw_networkx_edges(g_sw, pos, alpha=0.5, edge_color='gray')

# Draw nodes
nx.draw_networkx_nodes(g_sw, pos, node_size=600,
                      node_color='steelblue', alpha=0.5)

# Remove axes
plt.axis('off')
plt.tight_layout()
plt.show()
```

![](vertopal_9714c20675c04eeca65082f99a71713a/555a88114b75f8dd35cb3de03cd4072090e63df5.png)

Let\'s add labels to show the character names:

``` python
# Set random seed for reproducibility
np.random.seed(123)

# Create layout
pos = nx.spring_layout(g_sw, seed=123)

# Create figure
plt.figure(figsize=(12, 8))

# Draw edges
nx.draw_networkx_edges(g_sw, pos, alpha=0.5, edge_color='gray')

# Draw nodes
nx.draw_networkx_nodes(g_sw, pos, node_size=600,
                      node_color='steelblue', alpha=0.5)

# Draw labels
nx.draw_networkx_labels(g_sw, pos, font_size=10)

# Remove axes
plt.axis('off')
plt.title('Star Wars Character Network', fontsize=16)
plt.tight_layout()
plt.show()
```

![](vertopal_9714c20675c04eeca65082f99a71713a/d78baa67484323613e4e6a1abd938a5e9e5658a1.png)

### Measuring communities

Finally, it\'s possible to algorithmically group nodes into
**communities** in a variety of ways. NetworkX has several community
detection algorithms.

We\'ll use the **Louvain method**, which is similar to the infomap
algorithm used in R:

``` python
# Detect communities using the Louvain method
communities = community.louvain_communities(g_sw, seed=123)

# Create a dictionary mapping nodes to community IDs
community_map = {}
for i, comm in enumerate(communities):
    for node in comm:
        community_map[node] = i

print(f"Number of communities detected: {len(communities)}")
for i, comm in enumerate(communities):
    print(f"Community {i}: {comm}")
```

    Number of communities detected: 4
    Community 0: {'R2-D2', 'OWEN', 'C-3PO', 'BERU'}
    Community 1: {'OBI-WAN', 'GREEDO', 'LUKE', 'HAN', 'JABBA', 'CHEWBACCA', 'LEIA'}
    Community 2: {'TARKIN', 'MOTTI', 'DARTH VADER'}
    Community 3: {'RED LEADER', 'BIGGS', 'GOLD LEADER', 'RED TEN', 'CAMIE', 'WEDGE', 'DODONNA'}

``` python
# Set random seed for reproducibility
np.random.seed(123)

# Create layout
pos = nx.spring_layout(g_sw, seed=123)

# Get node colors based on community
node_colors = [community_map[node] for node in g_sw.nodes()]

# Create figure
plt.figure(figsize=(12, 8))

# Draw edges
nx.draw_networkx_edges(g_sw, pos, alpha=0.5, edge_color='gray')

# Draw nodes colored by community
nx.draw_networkx_nodes(g_sw, pos, node_size=600,
                      node_color=node_colors,
                      cmap=plt.cm.Set3, alpha=0.7)

# Draw labels
nx.draw_networkx_labels(g_sw, pos, font_size=10)

# Remove axes
plt.axis('off')
plt.title('Star Wars Character Network - Communities', fontsize=16)
plt.tight_layout()
plt.show()
```

![](vertopal_9714c20675c04eeca65082f99a71713a/4fd1b1764c46b0e81686d686497f40aa2cad68a0.png)

**1.5: Interpret this plot. If you\'ve seen Star Wars, what are the two
main groups here? (If you haven\'t, ask a friend.)**

*\[Your answer here\]*

## 2: US Congress Members on Twitter {#2-us-congress-members-on-twitter}

Our second network is US Congress members on Twitter, from 2016:
<https://cdn.rawgit.com/pablobarbera/data-science-workshop/master/sna/03_challenge_1_solutions.html>

``` python
# Read the data
nodes = pd.read_csv("lesson_7_data/congress-twitter-network-nodes.csv", dtype={'id_str': str})
edges = pd.read_csv("lesson_7_data/congress-twitter-network-edges.csv", dtype=str)

print("Nodes shape:", nodes.shape)
print("\nFirst few nodes:")
print(nodes.head())

print("\nEdges shape:", edges.shape)
print("\nFirst few edges:")
print(edges.head())
```

    Nodes shape: (517, 8)

    First few nodes:
          id_str          twitter    bioid                name gender chamber  \
    0   20209807    AnderCrenshaw  C001045      Ander Crenshaw      M     rep   
    1  234797704  AustinScottGA08  S001189        Austin Scott      M     rep   
    2   82453460  BennieGThompson  T000193  Bennie G. Thompson      M     rep   
    3  516880804  BettyMcCollum04  M001143      Betty McCollum      F     rep   
    4   74508260     BillPascrell  P000096   Bill Pascrell Jr.      M     rep   

            party  followers_count  
    0  Republican             9107  
    1  Republican             8316  
    2    Democrat             5002  
    3    Democrat             7211  
    4    Democrat             5362  

    Edges shape: (61766, 2)

    First few edges:
         source    target
    0  20209807  17976923
    1  20209807  25086658
    2  20209807  22509548
    3  20209807  19739126
    4  20209807   5558312

``` python
# Create a directed graph
g = nx.from_pandas_edgelist(edges,
                            source='source',
                            target='target',
                            create_using=nx.DiGraph())

# Add node attributes
node_attrs = nodes.set_index('id_str').to_dict('index')
nx.set_node_attributes(g, node_attrs)

print(f"Number of nodes: {g.number_of_nodes()}")
print(f"Number of edges: {g.number_of_edges()}")
```

    Number of nodes: 514
    Number of edges: 61766

**2.1: How many representatives and how many senators are in the data?**

``` python
# Count by chamber
print(nodes['chamber'].value_counts())
```

    chamber
    rep    424
    sen     93
    Name: count, dtype: int64

**2.2: This is a *directed* graph. Why?**

*\[Your answer here - Hint: Think about Twitter following relationships.
If A follows B, does B necessarily follow A?\]*

### Senators by party affiliation

Let\'s plot just the senators:

``` python
# Filter to senators only
senator_ids = nodes[nodes['chamber'] == 'sen']['id_str'].tolist()
g_sen = g.subgraph(senator_ids).copy()

print(f"Number of senators: {g_sen.number_of_nodes()}")
print(f"Number of edges: {g_sen.number_of_edges()}")
```

    Number of senators: 92
    Number of edges: 4049

``` python
# Set random seed
np.random.seed(123)

# Create layout
pos = nx.spring_layout(g_sen, seed=123, k=0.5)

# Get party colors
party_colors = {'R': 'red', 'D': 'blue', 'I': 'green'}
node_colors = [party_colors.get(g_sen.nodes[node].get('party', 'gray'), 'gray')
              for node in g_sen.nodes()]

# Create figure
plt.figure(figsize=(14, 10))

# Draw edges (very transparent because there are many)
nx.draw_networkx_edges(g_sen, pos, alpha=0.1, edge_color='gray',
                      width=0.1, arrows=False)

# Draw nodes
nx.draw_networkx_nodes(g_sen, pos, node_size=50,
                      node_color=node_colors, alpha=0.5)

# Remove axes
plt.axis('off')
plt.title('US Senate Twitter Network (2016)', fontsize=16)

# Add legend
from matplotlib.patches import Patch
legend_elements = [Patch(facecolor='red', alpha=0.5, label='Republican'),
                  Patch(facecolor='blue', alpha=0.5, label='Democrat'),
                  Patch(facecolor='green', alpha=0.5, label='Independent')]
plt.legend(handles=legend_elements, loc='upper right')

plt.tight_layout()
plt.show()
```

![](vertopal_9714c20675c04eeca65082f99a71713a/e9579e9bd8549cf41f68cf0074ddc726b4b86c76.png)

### Labeling senators

Let\'s clean up the graph a bit. We\'ll remove isolated nodes (senators
not connected to anyone) and label senators from Washington state.

``` python
# Remove isolated nodes
isolated_nodes = list(nx.isolates(g_sen))
g_sen_connected = g_sen.copy()
g_sen_connected.remove_nodes_from(isolated_nodes)

print(f"Removed {len(isolated_nodes)} isolated nodes")
print(f"Remaining nodes: {g_sen_connected.number_of_nodes()}")
```

    Removed 0 isolated nodes
    Remaining nodes: 92

``` python
# Set random seed
np.random.seed(123)

# Create layout
pos = nx.spring_layout(g_sen_connected, seed=123, k=0.5)

# Get party colors
node_colors = [party_colors.get(g_sen_connected.nodes[node].get('party', 'gray'), 'gray')
              for node in g_sen_connected.nodes()]

# Create figure
plt.figure(figsize=(14, 10))

# Draw edges
nx.draw_networkx_edges(g_sen_connected, pos, alpha=0.1, edge_color='gray',
                      width=0.1, arrows=False)

# Draw nodes
nx.draw_networkx_nodes(g_sen_connected, pos, node_size=100,
                      node_color=node_colors, alpha=0.4)

# Label Washington senators
wa_senators = ['Patty Murray', 'Maria Cantwell']
wa_labels = {node: g_sen_connected.nodes[node].get('name', '')
            for node in g_sen_connected.nodes()
            if g_sen_connected.nodes[node].get('name', '') in wa_senators}
nx.draw_networkx_labels(g_sen_connected, pos, wa_labels, font_size=12)

# Remove axes
plt.axis('off')
plt.title('US Senate Twitter Network - Washington Senators Labeled', fontsize=16)

# Add legend
plt.legend(handles=legend_elements, loc='upper right')

plt.tight_layout()
plt.show()
```

![](vertopal_9714c20675c04eeca65082f99a71713a/eed4a0148c1f8c659d71be076664eab3c69fe8a4.png)

**2.3: Do you see evidence of polarization, i.e. of homophily by
political party?**

*\[Your answer here\]*

If we convert the graph to an undirected graph, we can use a community
detection algorithm on it:

``` python
# Convert to undirected
g_sen_undirected = g_sen_connected.to_undirected()

# Detect communities
communities_sen = community.louvain_communities(g_sen_undirected, seed=123)

# Create community map
community_map_sen = {}
for i, comm in enumerate(communities_sen):
    for node in comm:
        community_map_sen[node] = i

print(f"Number of communities detected: {len(communities_sen)}")
for i, comm in enumerate(communities_sen):
    print(f"Community {i}: {len(comm)} members")
```

    Number of communities detected: 2
    Community 0: 46 members
    Community 1: 46 members

``` python
# Set random seed
np.random.seed(123)

# Create layout
pos = nx.spring_layout(g_sen_undirected, seed=123, k=0.5)

# Get community colors
node_colors = [community_map_sen[node] for node in g_sen_undirected.nodes()]

# Create figure
plt.figure(figsize=(14, 10))

# Draw edges
nx.draw_networkx_edges(g_sen_undirected, pos, alpha=0.1, edge_color='gray', width=0.1)

# Draw nodes
nx.draw_networkx_nodes(g_sen_undirected, pos, node_size=50,
                      node_color=node_colors, cmap=plt.cm.Set3, alpha=0.4)

# Remove axes
plt.axis('off')
plt.title('US Senate Twitter Network - Community Detection', fontsize=16)
plt.tight_layout()
plt.show()
```

![](vertopal_9714c20675c04eeca65082f99a71713a/5291d081f653b65c5ac7d4d72414dea17585f8fe.png)

### Questions: House of Representatives

Do you see evidence of polarization in the House of Representatives too?
Make a plot of representatives only.

**Important**: Don\'t plot the edges this time! If you do, your plot
will be very slow. With many nodes, just showing the node positions is
enough.

Also experiment with layouts other than `spring_layout`. Try
`kamada_kawai_layout` (similar to \"kk\" in R).

``` python
# Set random seed
np.random.seed(123)

# Write your code here
# Hint: Filter to chamber == 'rep', create subgraph, remove isolated nodes
# Use nx.draw_networkx_nodes() without drawing edges
```

### Questions: Number of Followers

You can vary node size according to the number of followers. Do this for
the Senate graph.

Then, add labels to your plot for the top 5 senators by number of
followers.

**Hint**: Use the `node_size` parameter with a list of sizes based on
follower counts.

``` python
# Set random seed
np.random.seed(123)

# Write your code here
# Hint:
# 1. Get followers_count for each node
# 2. Scale the values for node_size (e.g., divide by 1000)
# 3. Find top 5 by followers and create labels dict
# 4. Use nx.draw_networkx_labels() with that dict
```

## Challenge: Network Measures

There are a variety of mathematical measures for characterizing
properties of networks.

**Assortativity** measures the amount of homophily in a graph - the
tendency of nodes to connect with similar nodes.

Calculate the assortativity by party for the House, the Senate, and
Congress as a whole.

In NetworkX, use `nx.attribute_assortativity_coefficient()`.

``` python
# Write your code here
# Hint:
# senate_assortativity = nx.attribute_assortativity_coefficient(g_sen_undirected, 'party')
# Values closer to 1 indicate high homophily, closer to -1 indicate heterophily
```

## Summary: Network Analysis in Python

Here\'s a quick reference for network analysis operations:

### Creating Graphs

  ----------------------------------------------------------------------------
  R (igraph/tidygraph)         Python (NetworkX)             Description
  ---------------------------- ----------------------------- -----------------
  `graph_from_data_frame()`    `nx.from_pandas_edgelist()`   Create graph from
                                                             DataFrame

  `as_tbl_graph()`             No equivalent (NetworkX       
                               graphs are already easy to    
                               work with)                    

  `directed = FALSE`           `create_using=nx.Graph()`     Undirected graph

  `directed = TRUE`            `create_using=nx.DiGraph()`   Directed graph
  ----------------------------------------------------------------------------

### Graph Operations

  --------------------------------------------------------------------------------------------------------------
  R                               Python                                  Description
  ------------------------------- --------------------------------------- --------------------------------------
  `filter(chamber == "sen")`      `g.subgraph(node_list)`                 Filter to subset

  `filter(!node_is_isolated())`   `g.remove_nodes_from(nx.isolates(g))`   Remove isolated nodes

  `to_undirected()`               `g.to_undirected()`                     Convert to undirected

  `mutate(community = ...)`       Create dict and add with                Add node attributes
                                  `nx.set_node_attributes()`              
  --------------------------------------------------------------------------------------------------------------

### Layouts

  R (ggraph)            Python (NetworkX)            Description
  --------------------- ---------------------------- -----------------------
  `layout = "nicely"`   `nx.spring_layout()`         Force-directed layout
  `layout = "fr"`       `nx.spring_layout()`         Fruchterman-Reingold
  `layout = "kk"`       `nx.kamada_kawai_layout()`   Kamada-Kawai
  `layout = "circle"`   `nx.circular_layout()`       Circular layout

### Community Detection

  ----------------------------------------------------------------------------------------------
  R                   Python                              Description
  ------------------- ----------------------------------- --------------------------------------
  `group_infomap()`   `community.louvain_communities()`   Community detection

  `group_louvain()`   `community.louvain_communities()`   Louvain method
  ----------------------------------------------------------------------------------------------

### Plotting

  R (ggraph)                Python (NetworkX)             Description
  ------------------------- ----------------------------- -------------
  `geom_edge_link()`        `nx.draw_networkx_edges()`    Draw edges
  `geom_node_point()`       `nx.draw_networkx_nodes()`    Draw nodes
  `geom_node_text()`        `nx.draw_networkx_labels()`   Draw labels
  `aes(color = party)`      `node_color` parameter        Color nodes
  `aes(size = followers)`   `node_size` parameter         Size nodes

### Network Measures

  -------------------------------------------------------------------------------------------------------------
  R                         Python                                       Description
  ------------------------- -------------------------------------------- --------------------------------------
  `graph_assortativity()`   `nx.attribute_assortativity_coefficient()`   Measure homophily

  `degree()`                `g.degree()`                                 Node degree

  `betweenness()`           `nx.betweenness_centrality()`                Betweenness centrality

  `closeness()`             `nx.closeness_centrality()`                  Closeness centrality
  -------------------------------------------------------------------------------------------------------------

## Additional Resources {#additional-resources}

### NetworkX Documentation

-   **NetworkX Tutorial**:
    <https://networkx.org/documentation/stable/tutorial.html>
-   **Algorithms Reference**:
    <https://networkx.org/documentation/stable/reference/algorithms/index.html>
-   **Drawing**:
    <https://networkx.org/documentation/stable/reference/drawing.html>

### Alternative Python Libraries

-   **graph-tool**: <https://graph-tool.skewed.de/> (faster for large
    networks)
-   **igraph for Python**: <https://igraph.org/python/> (Python
    interface to igraph)
-   **Plotly**: <https://plotly.com/python/network-graphs/> (interactive
    network visualizations)

### Network Science Resources

-   **Network Science by Barabási**: <http://networksciencebook.com/>
-   **Social Network Analysis Workshop**:
    <https://github.com/pablobarbera/data-science-workshop/tree/master/sna>

### Critical Thinking About Networks

As you work with network data, consider:

1.  **What do edges represent?** Following on Twitter is different from
    friendship, which is different from collaboration.
2.  **What\'s missing?** Not everyone is on Twitter. What biases might
    this introduce?
3.  **Causality**: Does network structure cause behavior, or does
    behavior create network structure?
4.  **Power and influence**: How do network positions relate to power?
    Who is central? Who is peripheral?
5.  **Temporal dynamics**: Networks change over time. How might this
    network look different today?
6.  **Ethics**: What are the implications of analyzing people\'s social
    connections?

<p class="credits">Written by Sonia Fereidooni, <sf752@cam.ac.uk>, 2026-07-22<br />Licence: <a href="https://creativecommons.org/licenses/by-sa/4.0/">CC BY-SA 4.0</a></p>

<p class="previous-next-lesson"><a href="">Methods Fellows 2025 lessons</a></p>
