# Introduction to Python

## Table of Contents

- [Introduction to Python](#introduction-to-python)
  - [Table of Contents](#table-of-contents)
  - [**Python Basics**](#python-basics)
    - [Hello Python!](#hello-python)
    - [Variables and Types](#variables-and-types)
  - [**Python Lists**](#python-lists)
    - [Python Lists](#python-lists-1)
    - [Subsetting Lists](#subsetting-lists)
    - [Manipulating Lists](#manipulating-lists)
  - [**Functions and Packages**](#functions-and-packages)
    - [Functions](#functions)
    - [Methods](#methods)
    - [Packages](#packages)
  - [**Numpy**](#numpy)
    - [Numpy](#numpy-1)
    - [2D Numpy Arrays](#2d-numpy-arrays)
    - [Numpy: Basic Statistics](#numpy-basic-statistics)

## **Python Basics**

### Hello Python!
- Python as a calculator
```python
# Addition, subtraction
print(5 + 5)
print(5 - 5)

# Multiplication, division, modulo, and exponentiation
print(3 * 5)
print(10 / 2)
print(18 % 7)
print(4 ** 2)

# How much is your $100 worth after 7 years?
print (1.1 ** 7 * 100)
```
**[⬆ back to top](#table-of-contents)**

### Variables and Types
- Variable Assignment
```python
# Create a variable savings
savings = 100

# Print out savings
print(savings)
```

- Calculations with variables
```python
# Create a variable savings
savings = 100

# Create a variable growth_multiplier
growth_multiplier = 1.1

# Calculate result
result = savings * growth_multiplier ** 7

# Print out result
print(result)
```

- Other variable types
```python
# Create a variable desc
desc = "compound interest"

# Create a variable profitable
profitable = True
```

- Operations with other types
```python
savings = 100
growth_multiplier = 1.1
desc = "compound interest"

# Assign product of growth_multiplier and savings to year1
year1 = savings * growth_multiplier

# Print the type of year1
print(type(year1))

# Assign sum of desc and desc to doubledesc
doubledesc = desc + desc

# Print out doubledesc
print(doubledesc)
```

- Type conversion
```python
# Definition of savings and result
savings = 100
result = 100 * 1.10 ** 7

# Fix the printout
print("I started with $" + str(savings) + " and now have $" + str(result) + ". Awesome!")

# Definition of pi_string
pi_string = "3.1415926"

# Convert pi_string into float: pi_float
pi_float = float(pi_string)
```

**[⬆ back to top](#table-of-contents)**

## **Python Lists**

### Python Lists
- Create a list
```python
# area variables (in square meters)
hall = 11.25
kit = 18.0
liv = 20.0
bed = 10.75
bath = 9.50

# Create list areas
my_list = [hall, kit, liv, bed, bath]

# Print areas
print(my_list)
```

- Create list with different types
```python
# area variables (in square meters)
hall = 11.25
kit = 18.0
liv = 20.0
bed = 10.75
bath = 9.50

# Adapt list areas
areas = ["hallway", hall, "kitchen", kit, "living room", liv, "bedroom", bed, "bathroom", bath]

# Print areas
print(areas)
```

- List of lists
```python
# area variables (in square meters)
hall = 11.25
kit = 18.0
liv = 20.0
bed = 10.75
bath = 9.50

# house information as list of lists
house = [["hallway", hall],
         ["kitchen", kit],
         ["living room", liv],
         ["bedroom", bed],
         ["bathroom", bath]]

# Print out house
print(house)

# Print out the type of house
print(type(house))
```

**[⬆ back to top](#table-of-contents)**

### Subsetting Lists
- Subset and conquer
```python
# Create the areas list
areas = ["hallway", 11.25, "kitchen", 18.0, "living room", 20.0, "bedroom", 10.75, "bathroom", 9.50]

# Print out second element from areas
print(areas[1])

# Print out last element from areas
print(areas[9])

# Print out the area of the living room
print(areas[5])
```

- Subset and calculate
```python
# Create the areas list
areas = ["hallway", 11.25, "kitchen", 18.0, "living room", 20.0, "bedroom", 10.75, "bathroom", 9.50]

# Sum of kitchen and bedroom area: eat_sleep_area
eat_sleep_area = areas[3] + areas[7]

# Print the variable eat_sleep_area
print(eat_sleep_area)
```

- Slicing and dicing
```python
# Create the areas list
areas = ["hallway", 11.25, "kitchen", 18.0, "living room", 20.0, "bedroom", 10.75, "bathroom", 9.50]

# Use slicing to create downstairs
downstairs = areas[0:6]

# Use slicing to create upstairs
upstairs = areas[6:10]

# Print out downstairs and upstairs

print(downstairs)
# ['hallway', 11.25, 'kitchen', 18.0, 'living room', 20.0]

print(upstairs)
# ['bedroom', 10.75, 'bathroom', 9.5]
```

- Slicing and dicing (2)
```python
# Create the areas list
areas = ["hallway", 11.25, "kitchen", 18.0, "living room", 20.0, "bedroom", 10.75, "bathroom", 9.50]

# Alternative slicing to create downstairs
downstairs = areas[:6]

# Alternative slicing to create upstairs
upstairs = areas[6:]
```

**[⬆ back to top](#table-of-contents)**

### Manipulating Lists
- Replace list elements
```python
# Create the areas list
areas = ["hallway", 11.25, "kitchen", 18.0, "living room", 20.0, "bedroom", 10.75, "bathroom", 9.50]

# Correct the bathroom area
areas[-1] = 10.50

# Change "living room" to "chill zone"
areas[4] = "chill zone"
```
- Delete list elements
```python
areas = ["hallway", 11.25, "kitchen", 18.0,
        "chill zone", 20.0, "bedroom", 10.75,
         "bathroom", 10.50, "poolhouse", 24.5,
         "garage", 15.45]

del(areas[-4:-2])
# ['hallway', 11.25, 'kitchen', 18.0,
#  'chill zone', 20.0, 'bedroom', 10.75,
#  'bathroom', 10.5, 'garage', 15.45]
```

- Extend a list
```python
# Create the areas list and make some changes
areas = ["hallway", 11.25, "kitchen", 18.0, "chill zone", 20.0,
         "bedroom", 10.75, "bathroom", 10.50]

# Add poolhouse data to areas, new list is areas_1
areas_1 = areas + ["poolhouse", 24.5]

# Add garage data to areas_1, new list is areas_2
areas_2 = areas_1 + ["garage", 15.45]
```

- Inner workings of lists
```python
# Create list areas
areas = [11.25, 18.0, 20.0, 10.75, 9.50]

# Create areas_copy
areas_copy = list(areas)

# Change areas_copy
areas_copy[0] = 5.0

# Print areas
print(areas)
```

**[⬆ back to top](#table-of-contents)**

## **Functions and Packages**

### Functions
- Familiar functions
```python
# Create variables var1 and var2
var1 = [1, 2, 3, 4]
var2 = True

# Print out type of var1
print(type(var1))

# Print out length of var1
print(len(var1))

# Convert var2 to an integer: out2
out2 = int(var2)
```

- Multiple arguments
```python
# Create lists first and second
first = [11.25, 18.0, 20.0]
second = [10.75, 9.50]

# Paste together first and second: full
full = first + second
# [11.25, 18.0, 20.0, 10.75, 9.5]

# Sort full in descending order: full_sorted
full_sorted = sorted(full, reverse=True)

# Print out full_sorted
print(full_sorted)
# [20.0, 18.0, 11.25, 10.75, 9.5]
```

**[⬆ back to top](#table-of-contents)**

### Methods
- String Methods
```python
# string to experiment with: place
place = "poolhouse"

# Use upper() on place: place_up
place_up = place.upper()

# Print out place and place_up
print(place)
print(place_up)

# Print out the number of o's in place
print(place.count("o"))
```

- List Methods
```python
# Create list areas
areas = [11.25, 18.0, 20.0, 10.75, 9.50]

# Print out the index of the element 20.0
print(areas.index(20))

# Print out how often 9.50 appears in areas
print(areas.count(9.5))
```

- List Methods (2)
```python
# Create list areas
areas = [11.25, 18.0, 20.0, 10.75, 9.50]

# Use append twice to add poolhouse and garage size
areas.append(24.5)
areas.append(15.45)

# Print out areas
print(areas)
# [11.25, 18.0, 20.0, 10.75, 9.5, 24.5, 15.45]

# Reverse the orders of the elements in areas
areas.reverse()

# Print out areas
print(areas)
```

**[⬆ back to top](#table-of-contents)**

### Packages
- Import package
```python
# Definition of radius
r = 0.43

# Import the math package
import math

# Calculate C
C = 2 * math.pi * r

# Calculate A
A = math.pi * r ** 2

# Build printout
print("Circumference: " + str(C))
print("Area: " + str(A))
```

- Selective import
```python
# Definition of radius
r = 192500

# Import radians function of math package
from math import radians

# Travel distance of Moon over 12 degrees. Store in dist.
dist = r * radians(12)

# Print out dist
print(dist)
```

- Different ways of importing
```python
from scipy.linalg import inv as my_inv
```

**[⬆ back to top](#table-of-contents)**

## **Numpy**

### Numpy
- Your First NumPy Array
```python
# Create list baseball
baseball = [180, 215, 210, 210, 188, 176, 209, 200]

# Import the numpy package as np
import numpy as np

# Create a numpy array from baseball: np_baseball
np_baseball = np.array(baseball)
print(np_baseball)
# [180 215 210 210 188 176 209 200]

# Print out type of np_baseball
print(type(np_baseball))
```

- Baseball players' height
```python
# height is available as a regular list

# Import numpy
import numpy as np

# Create a numpy array from height_in: np_height_in
np_height_in = np.array(height_in)

# Print out np_height_in
print(np_height_in)
# [74 74 72 ... 75 75 73]

# Convert np_height_in to m: np_height_m
np_height_m = np_height_in * 0.0254

# Print np_height_m
print(np_height_m)
# [1.8796 1.8796 1.8288 ... 1.905  1.905  1.8542]
```

- Baseball player's BMI
```python
# height and weight are available as regular lists

# Import numpy
import numpy as np

# Create array from height_in with metric units: np_height_m
np_height_m = np.array(height_in) * 0.0254

# Create array from weight_lb with metric units: np_weight_kg
np_weight_kg = np.array(weight_lb) * 0.453592

# Calculate the BMI: bmi
bmi = np_weight_kg / np_height_m ** 2

# Print out bmi
print(bmi)
```

- Lightweight baseball players
```python
# height and weight are available as a regular lists

# Import numpy
import numpy as np

# Calculate the BMI: bmi
np_height_m = np.array(height_in) * 0.0254
np_weight_kg = np.array(weight_lb) * 0.453592
bmi = np_weight_kg / np_height_m ** 2

# Create the light array
light = bmi < 21

# Print out light
print(light)
# [False False False ... False False False]

# Print out BMIs of all baseball players whose BMI is below 21
print(bmi[light])
# [20.54255679 20.54255679 20.69282047 20.69282047 20.34343189 20.34343189
#  20.69282047 20.15883472 19.4984471  20.69282047 20.9205219 ]
```

- Subsetting NumPy Arrays
```python
# height and weight are available as a regular lists

# Import numpy
import numpy as np

# Store weight and height lists as numpy arrays
np_weight_lb = np.array(weight_lb)
np_height_in = np.array(height_in)

# Print out the weight at index 50
print(np_weight_lb[50])

# Print out sub-array of np_height_in: index 100 up to and including index 110
print(np_height_in[100:111])
```

**[⬆ back to top](#table-of-contents)**

### 2D Numpy Arrays
- Your First 2D NumPy Array
```python
# Create baseball, a list of lists
baseball = [[180, 78.4],
            [215, 102.7],
            [210, 98.5],
            [188, 75.2]]

# Import numpy
import numpy as np

# Create a 2D numpy array from baseball: np_baseball
np_baseball = np.array(baseball)

# Print out the type of np_baseball
print(type(np_baseball))

# Print out the shape of np_baseball
print(np_baseball.shape)
# (4, 2)
```

- Subsetting 2D NumPy Arrays
```python
# baseball is available as a regular list of lists

# Import numpy package
import numpy as np

# Create np_baseball (2 cols)
np_baseball = np.array(baseball)

# Print out the 50th row of np_baseball
print(np_baseball[49])
# [ 70 195]

# Select the entire second column of np_baseball: np_weight_lb
np_weight_lb = np_baseball[:,1]
# [180 215 210 ... 205 190 195]

# Print out height of 124th player
print(baseball[123][0])
```

- 2D Arithmetic
```python
# baseball is available as a regular list of lists
# updated is available as 2D numpy array

# Import numpy package
import numpy as np

# Create np_baseball (3 cols)
np_baseball = np.array(baseball)

# Print out addition of np_baseball and updated
print(np_baseball + updated)
# [[ 75.2303559  168.83775102  23.99      ]
#  [ 75.02614252 231.09732309  35.69      ]
#  [ 73.1544228  215.08167641  31.78      ]
#  ...
#  [ 76.09349925 209.23890778  26.19      ]
#  [ 75.82285669 172.21799965  32.01      ]
#  [ 73.99484223 203.14402711  28.92      ]]

# Create numpy array: conversion
conversion = [0.0254, 0.453592, 1]

# Print out product of np_baseball and conversion
print(np_baseball * conversion)
# [[ 1.8796  81.64656 22.99   ]
#  [ 1.8796  97.52228 34.69   ]
#  [ 1.8288  95.25432 30.78   ]
#  ...
#  [ 1.905   92.98636 25.19   ]
#  [ 1.905   86.18248 31.01   ]
#  [ 1.8542  88.45044 27.92   ]]
```

**[⬆ back to top](#table-of-contents)**

### Numpy: Basic Statistics
- Average versus median
```python
# np_baseball is available

# Import numpy
import numpy as np

# np_baseball
# [[7.400e+04 1.800e+02 2.299e+01]
#  [7.400e+01 2.150e+02 3.469e+01]
#  [7.200e+01 2.100e+02 3.078e+01]
#  ...
#  [7.500e+01 2.050e+02 2.519e+01]
#  [7.500e+01 1.900e+02 3.101e+01]
#  [7.300e+01 1.950e+02 2.792e+01]]

# Create np_height_in from np_baseball
np_height_in = np.array(np_baseball[:,0])
# [7.4e+04 7.4e+01 7.2e+01 ... 7.5e+01 7.5e+01 7.3e+01]

# Print out the mean of np_height_in
print(np.mean(np_height_in))
# 1586.4610837438424

# Print out the median of np_height_in
print(np.median(np_height_in))
# 74.0
```

- Explore the baseball data
```python
# np_baseball is available

# Import numpy
import numpy as np

# Print mean height (first column)
avg = np.mean(np_baseball[:,0])
print("Average: " + str(avg))

# Print median height. Replace 'None'
med = np.median(np_baseball[:,0])
print("Median: " + str(med))

# Print out the standard deviation on height. Replace 'None'
stddev = np.std(np_baseball[:,0])
print("Standard Deviation: " + str(stddev))

# Print out correlation between first and second column. Replace 'None'
corr = np.corrcoef(np_baseball[:,0], np_baseball[:,1])
print("Correlation: " + str(corr))
```

- Blend it all together
```python
# heights and positions are available as lists

# Import numpy
import numpy as np

# Convert positions and heights to numpy arrays: np_positions, np_heights
np_positions = np.array(positions)
np_heights = np.array(heights)

# Heights of the goalkeepers: gk_heights
gk_heights = np_heights[np_positions == 'GK']

# Heights of the other players: other_heights
other_heights = np_heights[np_positions != 'GK']

# Print out the median height of goalkeepers. Replace 'None'
print("Median height of goalkeepers: " + str(np.median(gk_heights)))

# Print out the median height of other players. Replace 'None'
print("Median height of other players: " + str(np.median(other_heights)))
```

**[⬆ back to top](#table-of-contents)**
