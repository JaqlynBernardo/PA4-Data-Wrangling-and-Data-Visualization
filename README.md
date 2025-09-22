# PA4-Data-Wrangling-and-Data-Visualization
This repository serves as a submission. This program was made and written in partial fulfillment of the requirements for Advanced Computer Programming and Algorithms (ECE2112).

## Description
This program shows different demonstrations of data wrangling and data visualization, using the Python Data Analysis library (PANDAS) and Matplotlib.

## Instructions
Write a Python script/code in the Jupyter Notebook to do the given problems.

### Importing PANDAS Library
```
import pandas as pd

```
Before writing the code, the Pandas Library and Matplotlib were imported. Pandas grants access to the dataframe object and its associated operations and functions, while Matplotlib grants access to types of data visualizations.

### Reference Dataframe
ECE Board Exam 2 dataset
```
board = pd.read_excel('board2.xlsx')
board
```
<br>
First, the variable 'board' was declared. Inside the variable is the pd.read_excel calling the file 'board2.xlsx'. Then the board dataframe was called to be printed.
<br><br>

**Results**
<br><br>
![alt text][RefDF]

[RefDF]:

### ECE Board Exam Problem
Using data wrangling and data visualization technique with storytelling, analyze the data and present different (i) data frames; and (ii) visuals using the dataset given.

**Part 1A**
```
Instru = board.loc[(board['Electronics']>70) # Score for Electronics is more than 70
                    & (board['Track'] == 'Instrumentation') # Constant Instrumentation Track
                    & (board['Hometown'] == 'Luzon') # Constant Luzon Hometown
                    ,['Name','GEAS','Electronics']] # Columns shown
Instru
```
<br>

<br><br>

**Results**
<br><br>
![alt text][No1A]

[No1A]: 

**Part 1B**
```
# Add Average Column to Dataframe
board['Average'] = board[['Math','Electronics','GEAS','Communication']].mean(axis=1)
```
<br>

<br><br>

```
Mindy = board.loc[(board['Average']>=55) # Average is more thanor equal to 55
                    & (board['Gender'] == 'Female') # Constant Female Gender
                    & (board['Hometown'] == 'Mindanao') # Constant Mindanao Hometown
                    ,['Name','Track','Electronics','Average']] # Columns shown
Mindy
```
<br>

<br><br>

**Results**
<br><br>
![alt text][No1B]

[No1B]: 

**Part 2A**
```
plt.figure(figsize=(5,5))
plt.title("Average Scores by Gender")
plt.xlabel("Gender")
plt.ylabel("Average Scores")
plt.bar(board['Gender'], board['Average'])
```
<br>

<br><br>

**Results**
<br><br>
![alt text][No2A]

[No2A]: 

**Part 2A**
```
plt.figure(figsize=(5,5))
plt.title("Average Scores by Track")
plt.xlabel("Track")
plt.ylabel("Average Scores")
plt.bar(board['Track'], board['Average'])
```
<br>

<br><br>

**Results**
<br><br>
![alt text][No2B]

[No2B]: 

**Part 2C**
```
plt.figure(figsize=(5,5))
plt.title("Average Scores by Hometown")
plt.xlabel("Hometown")
plt.ylabel("Average Scores")
plt.bar(board['Hometown'], board['Average'])
```
<br>

<br><br>

**Results**
<br><br>
![alt text][No2C]

[No2C]: 



## Author
Bernardo, Jaqlyn Trazy B.
* Section: 2ECE-C
* Student No.: 2024198347
