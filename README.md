# PA4-Data-Wrangling-and-Data-Visualization
This repository serves as a submission. This program was made and written in partial fulfillment of the requirements for Advanced Computer Programming and Algorithms (ECE2112).

## Description
This program shows different demonstrations of data wrangling and data visualization, using the Python Data Analysis library (PANDAS) and Matplotlib.

## Instructions
Write a Python script/code in the Jupyter Notebook to do the given problems.

### ECE Board Exam Problem
Using data wrangling and data visualization technique with storytelling, analyze the data and present different (i) data frames; and (ii) visuals using the dataset given.

### Importing PANDAS and Matplotlib
```
import pandas as pd
import matplotlib.pyplot as plt
```
Before writing the code, the Pandas Library and Matplotlib were imported. Pandas grants access to the dataframe object and its associated operations and functions, while Matplotlib grants access to different types of data visualizations.

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

[RefDF]: Results/RefDF.png

### Part 1
Create the following data frames based on the format provided:
* (A) Instru = [“Name”, “GEAS”, “Electronics >70”]; where track is constant as Instrumentation and hometown Luzon
* (B) Mindy = [ “Name”, “Track”, “Electronics”, “Average >=55”]; where hometown is constant as Mindanao and gender Female

**Part 1A**
```
Instru = board.loc[(board['Electronics']>70) # Score for Electronics is more than 70
                    & (board['Track'] == 'Instrumentation') # Constant Instrumentation Track
                    & (board['Hometown'] == 'Luzon') # Constant Luzon Hometown
                    ,['Name','GEAS','Electronics']] # Columns shown
Instru
```
<br>
Inside the variable 'Instru', I took the previously established dataframe, 'board', and used .loc syntax to specify the rows and the columns I want to display. For the rows, as given by the instruction: (1) under 'Electronics', the value must be more than 70, (2) under 'Track', the student must have taken 'Instrumentation' (denoted by '==' in the code), and (3) under 'Hometown', the student must be from 'Luzon' (denoted by '==' in the code). For the columns, given by the instruction, the columns shown are: 'Name', 'GEAS', and 'Electronics.'
<br><br>

**Results**
<br><br>
![alt text][No1A]

[No1A]: Results/No1A.png

**Part 1B**
```
# Add Average Column to Dataframe
board['Average'] = board[['Math','Electronics','GEAS','Communication']].mean(axis=1)
```
<br>
First, I looked for the average of the scores per student. I did this by adding a new column to the 'board' dataframe. The "board['Average']" code adds a new column named 'Average' to the dataframe. Then, I took the specific columns, 'Math', 'Electronics', 'GEAS', and 'Communication' in the dataframe and used .mean() syntax to get the mean. The mean syntax is specified as '(axis=1)' so that it takes the values across the columns (horizontally). 
<br><br>

```
Mindy = board.loc[(board['Average']>=55) # Average is more than or equal to 55
                    & (board['Gender'] == 'Female') # Constant Female Gender
                    & (board['Hometown'] == 'Mindanao') # Constant Mindanao Hometown
                    ,['Name','Track','Electronics','Average']] # Columns shown
Mindy
```
<br>
Next, under the variable 'Mindy', I used the same type of code as the previous part (Part 1A). I used the .loc syntax to specify the rows and the columns I want to display. For the rows, as given by the instruction: (1) under 'Average', the value must be more than  or equal to 55, (2) under 'Gender', the student must identify as 'Female' (denoted by '==' in the code), and (3) under 'Hometown', the student must be from 'Mindanao' (denoted by '==' in the code). For the columns given by the instruction, the columns shown are: 'Name', 'Track', 'Electronics', and 'Average.' 
<br><br>

**Results**
<br><br>
![alt text][No1B]

[No1B]: Results/No1B.png

### Part 2
Create a visualization that shows how the different features contributes to average grade. Does chosen track in college, gender, or hometown contributes to a higher average score?

**Part 2A**
```
gender = board.groupby('Gender', as_index=False)['Average'].mean()

plt.figure(figsize=(5,5))
plt.title("Average Scores by Gender")
plt.xlabel("Gender")
plt.ylabel("Average Scores")
plt.bar(gender['Gender'], gender['Average'])
```
<br>
First, I grouped the data by using the .groupby syntax. This groups the data by the 'Gender' column and gets the average of both Male and Female, using the .mean syntax. The 'as_index' is set to false so that 'Gender' remains a column. The "plt.figure((5,5))" creates a new figure that is 5 by 5 in size (in inches). The "plt.title('Average Scores by Gender')" gives the figure the stated title. I used the .xlabel and the .ylabel syntaxes to name the axes, 'Gender' and 'Average Scores', respectively. Lastly, I used the .bar syntax to generate a bar graph. I specified the 'Gender' from the grouped dataframe, 'gender', as my x-axis, and 'Average' from the same dataframe as my y-axis. 
<br><br>

**Results**
<br><br>
![alt text][No2A]

[No2A]: Results/No2A.png

**Part 2B**
```
track = board.groupby('Track', as_index=False)['Average'].mean()

plt.figure(figsize=(5,5))
plt.title('Average Scores by Track')
plt.xlabel('Track')
plt.ylabel('Average Scores')
plt.bar(track['Track'], track['Average'])
```
<br>
First, I grouped the data by using the .groupby syntax. This groups the data by the 'Track' column and gets the average of Communication, Instrumentation, and Microelectronics, using the .mean syntax. The 'as_index' is set to false so that 'Track' remains a column. The "plt.figure((5,5))" creates a new figure that is 5 by 5 in size (in inches). The "plt.title('Average Scores by Track')" gives the figure the stated title. I used the .xlabel and the .ylabel syntaxes to name the axes, 'Track' and 'Average Scores', respectively. I used the .bar syntax to generate a bar graph. I specified the 'Track' from the grouped dataframe, 'track', as my x-axis, and 'Average' from the same dataframe as my y-axis. 
<br><br>

**Results**
<br><br>
![alt text][No2B]

[No2B]: Results/No2B.png

**Part 2C**
```
hometown = board.groupby('Hometown', as_index=False)['Average'].mean()

plt.figure(figsize=(5,5))
plt.title('Average Scores by Hometown')
plt.xlabel('Hometown')
plt.ylabel('Average Scores')
plt.bar(hometown['Hometown'], hometown['Average'])
```
<br>
First, I grouped the data by using the .groupby syntax. This groups the data by the 'Hometown' column and gets the average of Luzon, Visayas, and Mindanao, using the .mean syntax. The 'as_index' is set to false so that 'Hometown' remains a column. The "plt.figure((5,5))" creates a new figure that is 5 by 5 in size (in inches). The "plt.title('Average Scores by Track')" gives the figure the stated title. I used the .xlabel and the .ylabel syntaxes to name the axes, 'Track' and 'Average Scores', respectively. I used the .bar syntax to generate a bar graph. I specified the 'hometown' from the grouped dataframe, 'hometown', as my x-axis, and 'Average' from the same dataframe as my y-axis. 
<br><br>

**Results**
<br><br>
![alt text][No2C]

[No2C]: Results/No2C.png



## Author
Bernardo, Jaqlyn Trazy B.
* Section: 2ECE-C
* Student No.: 2024198347
