# Python Data Science Toolbox (Part 1)

## Table of Contents

- [Python Data Science Toolbox (Part 1)](#python-data-science-toolbox-part-1)
  - [Table of Contents](#table-of-contents)
  - [**Writing your own functions**](#writing-your-own-functions)
    - [User-defined functions](#user-defined-functions)
    - [Multiple parameters and return values](#multiple-parameters-and-return-values)
    - [Bringing it all together](#bringing-it-all-together)
  - [**Default arguments, variable-length arguments and scope**](#default-arguments-variable-length-arguments-and-scope)
    - [Scope and user-defined functions](#scope-and-user-defined-functions)
    - [Nested functions](#nested-functions)
    - [Default and flexible arguments](#default-and-flexible-arguments)
    - [Bringing it all together](#bringing-it-all-together-1)
  - [**Lambda functions and error-handling**](#lambda-functions-and-error-handling)
    - [Lambda functions](#lambda-functions)
    - [Introduction to error handling](#introduction-to-error-handling)
    - [Bringing it all together](#bringing-it-all-together-2)

## **Writing your own functions**

### User-defined functions
- Write a simple function
```python
# Define the function shout
def shout():
    """Print a string with three exclamation marks"""
    # Concatenate the strings
    shout_word = 'congratulations' + '!' * 3
    
    # Print shout_word
    print(shout_word)

# Call shout
shout()
```

- Single-parameter functions
```python
# Define shout with the parameter, word
def shout(word):
    """Print a string with three exclamation marks"""
    # Concatenate the strings: shout_word
    shout_word = word + '!!!'

    # Print shout_word
    print(shout_word)

# Call shout with the string 'congratulations'
shout('congratulations')
```

- Functions that return single values
```python
# Define shout with the parameter, word
def shout(word):
    """Return a string with three exclamation marks"""
    # Concatenate the strings: shout_word
    shout_word = word + '!!!' 

    # Replace print with return
    return shout_word

# Pass 'congratulations' to shout: yell
yell = shout('congratulations')

# Print yell
print(yell)
```

**[⬆ back to top](#table-of-contents)**

### Multiple parameters and return values
- Functions with multiple parameters
```python
# Define shout with parameters word1 and word2
def shout(word1, word2):
    """Concatenate strings with three exclamation marks"""
    # Concatenate word1 with '!!!': shout1
    shout1 = word1 + '!!!'
    
    # Concatenate word2 with '!!!': shout2
    shout2 = word2 + '!!!'
    
    # Concatenate shout1 with shout2: new_shout
    new_shout = shout1 + shout2

    # Return new_shout
    return new_shout

# Pass 'congratulations' and 'you' to shout(): yell
yell = shout('congratulations', 'you')

# Print yell
print(yell)
```

- A brief introduction to tuples
```python
# Unpack nums into num1, num2, and num3
num1, num2, num3 = nums

# Construct even_nums
even_nums = (2, num2, num3)
```

- Functions that return multiple values
```python
# Define shout_all with parameters word1 and word2
def shout_all(word1, word2):
    
    # Concatenate word1 with '!!!': shout1
    shout1 = word1 + '!!!'
    
    # Concatenate word2 with '!!!': shout2
    shout2 = word2 + '!!!'
    
    # Construct a tuple with shout1 and shout2: shout_words
    shout_words = (shout1, shout2)

    # Return shout_words
    return shout_words

# Pass 'congratulations' and 'you' to shout_all(): yell1, yell2
yell1, yell2 = shout_all('congratulations', 'you')

# Print yell1 and yell2
print(yell1)
print(yell2)
```

**[⬆ back to top](#table-of-contents)**

### Bringing it all together
- Bringing it all together (1)
```python
# Import pandas
import pandas as pd

# Import Twitter data as DataFrame: df
df = pd.read_csv('tweets.csv')

# Initialize an empty dictionary: langs_count
langs_count = {}

# Extract column from DataFrame: col
col = df['lang']
# 0      en
# 1      en
# 2      et
# 3      en
#      ... 
# 19     en
# 20    und
# 21     en
#      ... 
# 28     en
# 29    und
#      ... 
# 99     en
# Name: lang, Length: 100, dtype: object

# Iterate over lang column in DataFrame
for entry in col:

    # If the language is in langs_count, add 1 
    if entry in langs_count:
        langs_count[entry] += 1
    # Else add the language to langs_count, set the value to 1
    else:
        langs_count[entry] = 1

# Print the populated dictionary
print(langs_count)
# {'en': 97, 'et': 1, 'und': 2}
```

- Bringing it all together (2)
```python
# Define count_entries()
def count_entries(df, col_name):
    """Return a dictionary with counts of 
    occurrences as value for each key."""

    # Initialize an empty dictionary: langs_count
    langs_count = {}
    
    # Extract column from DataFrame: col
    col = df[col_name]
    
    # Iterate over lang column in DataFrame
    for entry in col:

        # If the language is in langs_count, add 1
        if entry in langs_count.keys():
            langs_count[entry] += 1
        # Else add the language to langs_count, set the value to 1
        else:
            langs_count[entry] = 1

    # Return the langs_count dictionary
    return langs_count

# Call count_entries(): result
result = count_entries(tweets_df,'lang')

# Print the result
print(result)
```

**[⬆ back to top](#table-of-contents)**

## **Default arguments, variable-length arguments and scope**

### Scope and user-defined functions
- The keyword global
```python
# Create a string: team
team = "teen titans"

# Define change_team()
def change_team():
    """Change the value of the global variable team."""

    # Use team in global scope
    global team

    # Change the value of team in global: team
    team = "justice league"

# Print team
print(team)
# teen titans

# Call change_team()
change_team()

# Print team
print(team)
# justice league
```

**[⬆ back to top](#table-of-contents)**

### Nested functions
- Nested Functions I
```python
# Define three_shouts
def three_shouts(word1, word2, word3):
    """Returns a tuple of strings
    concatenated with '!!!'."""

    # Define inner
    def inner(word):
        """Returns a string concatenated with '!!!'."""
        return word + '!!!'

    # Return a tuple of strings
    return (inner(word1), inner(word2), inner(word3))

# Call three_shouts() and print
print(three_shouts('a', 'b', 'c'))
# ('a!!!', 'b!!!', 'c!!!')
```

- Nested Functions II
```python
# Define echo
def echo(n):
    """Return the inner_echo function."""

    # Define inner_echo
    def inner_echo(word1):
        """Concatenate n copies of word1."""
        echo_word = word1 * n
        return echo_word

    # Return inner_echo
    return inner_echo

# Call echo: twice
twice = echo(2)

# Call echo: thrice
thrice = echo(3)

# Call twice() and thrice() then print
print(twice('hello'), thrice('hello'))
# hellohello hellohellohello
```

- The keyword nonlocal and nested functions
```python
# Define echo_shout()
def echo_shout(word):
    """Change the value of a nonlocal variable"""
    
    # Concatenate word with itself: echo_word
    echo_word = word + word
    
    # Print echo_word
    print(echo_word)
    
    # Define inner function shout()
    def shout():
        """Alter a variable in the enclosing scope"""    
        # Use echo_word in nonlocal scope
        nonlocal echo_word
        
        # Change echo_word to echo_word concatenated with '!!!'
        echo_word = echo_word + '!!!'
    
    # Call function shout()
    shout()
    
    # Print echo_word
    print(echo_word)

# Call function echo_shout() with argument 'hello'
echo_shout('hello')
# hellohello
# hellohello!!!
```

**[⬆ back to top](#table-of-contents)**

### Default and flexible arguments
- Functions with one default argument
```python
# Define shout_echo
def shout_echo(word1, echo = 1):
    """Concatenate echo copies of word1 and three
     exclamation marks at the end of the string."""

    # Concatenate echo copies of word1 using *: echo_word
    echo_word = word1 * echo

    # Concatenate '!!!' to echo_word: shout_word
    shout_word = echo_word + '!!!'

    # Return shout_word
    return shout_word

# Call shout_echo() with "Hey": no_echo
no_echo = shout_echo('Hey')

# Call shout_echo() with "Hey" and echo=5: with_echo
with_echo = shout_echo('Hey', 5)

# Print no_echo and with_echo
print(no_echo)
# Hey!!!

print(with_echo)
# HeyHeyHeyHeyHey!!!
```

- Functions with multiple default arguments
```python
# Define shout_echo
def shout_echo(word1, echo = 1, intense = False):
    """Concatenate echo copies of word1 and three
    exclamation marks at the end of the string."""

    # Concatenate echo copies of word1 using *: echo_word
    echo_word = word1 * echo

    # Make echo_word uppercase if intense is True
    if intense is True:
        # Make uppercase and concatenate '!!!': echo_word_new
        echo_word_new = echo_word.upper() + '!!!'
    else:
        # Concatenate '!!!' to echo_word: echo_word_new
        echo_word_new = echo_word + '!!!'

    # Return echo_word_new
    return echo_word_new

# Call shout_echo() with "Hey", echo=5 and intense=True: with_big_echo
with_big_echo = shout_echo('Hey', 5, True)

# Call shout_echo() with "Hey" and intense=True: big_no_echo
big_no_echo = shout_echo('Hey', intense=True)

# Print values
print(with_big_echo)
# HEYHEYHEYHEYHEY!!!

print(big_no_echo)
# HEY!!!
```

- Functions with variable-length arguments (*args)
```python
# Define gibberish
def gibberish(*args):
    """Concatenate strings in *args together."""

    # Initialize an empty string: hodgepodge
    hodgepodge = ''

    # Concatenate the strings in args
    for word in args:
        hodgepodge += word

    # Return hodgepodge
    return hodgepodge

# Call gibberish() with one string: one_word
one_word = gibberish('luke')

# Call gibberish() with five strings: many_words
# args <class 'tuple'>
# ('luke', 'leia', 'han', 'obi', 'darth')
many_words = gibberish("luke", "leia", "han", "obi", "darth")

# Print one_word and many_words
print(one_word)
# luke

print(many_words)
# lukeleiahanobidarth
```

- Functions with variable-length keyword arguments (**kwargs)
```python
# Define report_status
def report_status(**kwargs):
    """Print out the status of a movie character."""

    print("\nBEGIN: REPORT\n")

    # Iterate over the key-value pairs of kwargs
    for keys, values in kwargs.items():
        # Print out the keys and values, separated by a colon ':'
        print(keys + ": " + values)

    print("\nEND REPORT")

# First call to report_status()
# kwargs <class 'dict'>
# {'name': 'luke', 'affiliation': 'jedi', 'status': 'missing'}
report_status(name="luke", affiliation="jedi", status="missing")
# name: luke
# affiliation: jedi
# status: missing

# Second call to report_status()
report_status(name="anakin", affiliation="sith lord", status="deceased")
# name: anakin
# affiliation: sith lord
# status: deceased
```

**[⬆ back to top](#table-of-contents)**

### Bringing it all together
- Bringing it all together (1)
```python
# Define count_entries()
def count_entries(df, col_name):
    """Return a dictionary with counts of
    occurrences as value for each key."""

    # Initialize an empty dictionary: cols_count
    cols_count = {}

    # Extract column from DataFrame: col
    col = df[col_name]
    
    # Iterate over the column in DataFrame
    for entry in col:

        # If entry is in cols_count, add 1
        if entry in cols_count.keys():
            cols_count[entry] += 1

        # Else add the entry to cols_count, set the value to 1
        else:
            cols_count[entry] = 1

    # Return the cols_count dictionary
    return cols_count

# Call count_entries(): result1
result1 = count_entries(tweets_df, 'lang')

# Call count_entries(): result2
result2 = count_entries(tweets_df, 'source')

# Print result1 and result2
print(result1)
print(result2)
```
- Bringing it all together (2)
```python
# Define count_entries()
def count_entries(df, *args):
    """Return a dictionary with counts of
    occurrences as value for each key."""
    
    #Initialize an empty dictionary: cols_count
    cols_count = {}
    
    # Iterate over column names in args
    for col_name in args:
    
        # Extract column from DataFrame: col
        col = df[col_name]
    
        # Iterate over the column in DataFrame
        for entry in col:
    
            # If entry is in cols_count, add 1
            if entry in cols_count.keys():
                cols_count[entry] += 1
    
            # Else add the entry to cols_count, set the value to 1
            else:
                cols_count[entry] = 1

    # Return the cols_count dictionary
    return cols_count

# Call count_entries(): result1
result1 = count_entries(tweets_df, 'lang')

# Call count_entries(): result2
result2 = count_entries(tweets_df, 'lang', 'source')

# Print result1 and result2
print(result1)
print(result2)
```

**[⬆ back to top](#table-of-contents)**

## **Lambda functions and error-handling**

### Lambda functions
- Writing a lambda function you already know
```python
# Define echo_word as a lambda function: echo_word
echo_word = (lambda word, echo: word * echo)

# Call echo_word: result
result = echo_word('hey', 5)

# Print result
print(result)
```

- Map() and lambda functions
```python
# Create a list of strings: spells
spells = ["protego", "accio", "expecto patronum", "legilimens"]

# Use map() to apply a lambda function over spells: shout_spells
shout_spells = map(lambda item: item + '!!!', spells)
# shout_spells <class 'map'>
# ['protego!!!', 'accio!!!', 'expecto patronum!!!', 'legilimens!!!']

# Convert shout_spells to a list: shout_spells_list
shout_spells_list = list(shout_spells)
# shout_spells_list <class 'list'>

# Print the result
print(shout_spells_list)
# ['protego!!!', 'accio!!!', 'expecto patronum!!!', 'legilimens!!!']
```

- Filter() and lambda functions
```python
# Create a list of strings: fellowship
fellowship = ['frodo', 'samwise', 'merry', 'pippin', 'aragorn', 'boromir', 'legolas', 'gimli', 'gandalf']

# Use filter() to apply a lambda function over fellowship: result
result = filter(lambda item: len(item) > 6, fellowship)

# Convert result to a list: result_list
result_list = list(result)

# Print result_list
print(result_list)
# ['samwise', 'aragorn', 'boromir', 'legolas', 'gandalf']
```

- Reduce() and lambda functions
```python
# Import reduce from functools
from functools import reduce

# Create a list of strings: stark
stark = ['robb', 'sansa', 'arya', 'brandon', 'rickon']

# Use reduce() to apply a lambda function over stark: result
result = reduce(lambda item1, item2: item1 + item2 , stark)

# Print the result
print(result)
# robbsansaaryabrandonrickon
```

**[⬆ back to top](#table-of-contents)**

### Introduction to error handling
- Error handling with try-except
```python
# Define shout_echo
def shout_echo(word1, echo=1):
    """Concatenate echo copies of word1 and three
    exclamation marks at the end of the string."""

    # Initialize empty strings: echo_word, shout_words
    echo_word = ''
    shout_words = ''

    # Add exception handling with try-except
    try:
        # Concatenate echo copies of word1 using *: echo_word
        echo_word =word1 * echo

        # Concatenate '!!!' to echo_word: shout_words
        shout_words = echo_word + '!!!'
    except:
        # Print error message
        print("word1 must be a string and echo must be an integer.")

    # Return shout_words
    return shout_words

# Call shout_echo
shout_echo("particle", echo="accelerator")
# word1 must be a string and echo must be an integer.
```

- Error handling by raising an error
```python
# Define shout_echo
def shout_echo(word1, echo=1):
    """Concatenate echo copies of word1 and three
    exclamation marks at the end of the string."""

    # Raise an error with raise
    if echo < 0:
        raise ValueError('echo must be greater than or equal to 0')

    # Concatenate echo copies of word1 using *: echo_word
    echo_word = word1 * echo

    # Concatenate '!!!' to echo_word: shout_word
    shout_word = echo_word + '!!!'

    # Return shout_word
    return shout_word

# Call shout_echo
shout_echo("particle", echo = -1)
# Traceback (most recent call last):
#   File "<stdin>", line 20, in <module>
#     shout_echo("particle", echo=-1)
#   File "<stdin>", line 8, in shout_echo
#     raise ValueError('echo must be greater than or equal to 0')
# ValueError: echo must be greater than or equal to 0
```

**[⬆ back to top](#table-of-contents)**

### Bringing it all together
- Bringing it all together (1)
```python
# Select retweets from the Twitter DataFrame: result
# tweets_df['text'] <class 'pandas.core.series.Series'>
result = filter(lambda x: x[0:2] == 'RT', tweets_df['text'])

# Create list from filter object result: res_list
res_list = list(result)

# Print all retweets in res_list
for tweet in res_list:
    print(tweet)
```

- Bringing it all together (2)
```python
# Define count_entries()
def count_entries(df, col_name='lang'):
    """Return a dictionary with counts of
    occurrences as value for each key."""

    # Initialize an empty dictionary: cols_count
    cols_count = {}

    # Add try block
    try:
        # Extract column from DataFrame: col
        col = df[col_name]
        
        # Iterate over the column in dataframe
        for entry in col:
    
            # If entry is in cols_count, add 1
            if entry in cols_count.keys():
                cols_count[entry] += 1
            # Else add the entry to cols_count, set the value to 1
            else:
                cols_count[entry] = 1
    
        # Return the cols_count dictionary
        return cols_count

    # Add except block
    except:
        print('The DataFrame does not have a ' + col_name + ' column.')

# Call count_entries(): result1
result1 = count_entries(tweets_df, 'lang1')
# The DataFrame does not have a lang1 column.

# Print result1
print(result1)
# None
```

- Bringing it all together (3)
```python
# Define count_entries()
def count_entries(df, col_name='lang'):
    """Return a dictionary with counts of
    occurrences as value for each key."""
    
    # Raise a ValueError if col_name is NOT in DataFrame
    if col_name not in df.columns:
        raise ValueError('The DataFrame does not have a ' + col_name + ' column.')

    # Initialize an empty dictionary: cols_count
    cols_count = {}
    
    # Extract column from DataFrame: col
    col = df[col_name]
    
    # Iterate over the column in DataFrame
    for entry in col:

        # If entry is in cols_count, add 1
        if entry in cols_count.keys():
            cols_count[entry] += 1
            # Else add the entry to cols_count, set the value to 1
        else:
            cols_count[entry] = 1
        
        # Return the cols_count dictionary
    return cols_count

# Call count_entries(): result1
result1 = count_entries(tweets_df, 'lang1')
# Traceback (most recent call last):
#   File "<stdin>", line 30, in <module>
#     result1 = count_entries(tweets_df, 'lang1')
#   File "<stdin>", line 8, in count_entries
#     raise ValueError('The DataFrame does not have a ' + col_name + ' column.')
# ValueError: The DataFrame does not have a lang1 colum

# Print result1
print(result1)
```

**[⬆ back to top](#table-of-contents)**
