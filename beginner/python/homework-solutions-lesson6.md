# Homework Solutions: Lesson 5: Further Loops and Conditionals

## Task 1:
The code example this task depends on is:

```python
index = 0
while index < len(university_library):
    book = university_library[index]
    if present(book):
        process(book)
        break
    index += 1
else:
    print('No book found.')
```
The elements which were not explained in the lesson are:
<li>'index=0'</li>
<li>'while index < len(university_library)'</li>

The first element a variable used to track our position in the university_library list. It tells Python to start with the 0th element and continue, which is 'index += 1', that appears at  the end of the indented block. This bit of code helps Python keep track of where it is in the list.

The core of the second element is len(university_library). This is the length of the list that 'university library' has. It could be the entire database of books that readers can check out. The loop is stating that while the index is less than the total number of books in the library, then Python should keep checking if each given book is present. Once it reaches the last book, the loop will stop. 

The reason you were encouraged to look these up yourself is because much of your time spent writing code will be searching for answers to such questions. No programmer remembers every fact or bit of syntax. It is the ability to find information that will take you far.

## Task 2:
In this task you were asked to create variables to form the basis of arguments for the function add(). Here is a numerical example (but your code, so long as it ran as you wanted, does not need to involve numbers):

```python
def add(*args):
    return sum(args)

x = 5
y = 10
z = 15

print(add(x, y, z))
```
**! A note of caution**: In this example we used 'x', 'y', 'z' for simplicity's sake. Typically it is a bad idea to use such generic variable names. Ideally you want to write code that someone else could read (or that you could read years later). In your own code be sure to use descriptive variable names. 

## Task 3:
In this task you were asked to come up with a combination of loops and conditionals that produced something meaningful. The possibilities are numerous, but here is an example for reference:

```python
student_assigned_reading = {
    'Alice': ['Macbeth', 'Python Programming', 'Hamlet'],
    'Bob': ['Moby Dick', 'The Odyssey'],
    'Charlie': ['Python Programming', 'Pride and Prejudice', 'Jane Eyre']
}

for student, books in student_assigned_reading.items():  
    print(f'Checking books for {student}:')
    
    index = 0
    while index < len(books):  
        book = books[index]
        
        if book == 'Python Programming':  # conditional
            print(f'  -> {student} has the Python Programming book!')
        else:
            print(f'  -> {student} has {book}.')
        
        index += 1
```

Notice that we use a list of dictionaries (each 'element:element' is one dictionary), we use indexing and a while loop to move through the dictionaries, and we use an if...else formulation to print very specific information from the data.

As you write more code, becoming more familiar with how to move seamlessly between different types of data, different functions, and different syntax structures will become more second-nature. In the meantime, if you were able to complete this homework, you can be confident that you have a foundation in some of the most important elements of Python syntax.

