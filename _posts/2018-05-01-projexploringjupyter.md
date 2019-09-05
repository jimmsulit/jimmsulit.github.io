---

layout: single
title:  "Mini Project: Exploring Jupyter Notebook"
date:   2018-05-01
comments: true

---


In this guided project, we'll walk through how to work in the Jupyter environment. Jupyter is a widely used data science environment that combines a rich text editor with a console. The Jupyter project was originally called IPython, and focused on supporting just the Python language. Over time, support for other languages like R and Julia were added and the project was renamed to Jupyter.

Jupyter notebook is built around a typical data analysis workflow and it's very different from a standard integrated development environment, such as Pycharm, which focuses more on just working with code. In Jupyter, you work with notebooks, which mix plain text, code, and code outputs in one view. 

## Birth Dates In the United States

The raw data behind the story **Some People Are Too Superstitious To Have a Baby on Friday The 13th**, which you can read [here](https://fivethirtyeight.com/features/some-people-are-too-superstitious-to-have-a-baby-on-friday-the-13th/).

We'll be working with the data set from the Centers for Disease Control and Prevention's National Center for Health Statistics. The data set has the following structure:

Header | Definition
---|---------
`year` | Year
`month` | Month
`date_of_month` | Day number of the month
`day_of_week` | Day of week, where 1 is Monday and 7 is Sunday
`births` | Number of births

We start by reading and opening the csv file. To fully use the capacity of Jupyter notebook, one must know how to properly load the data set. Moreover, running a code that assigns a value to a variable does not display any output. To generate the output that we want, we will use the print() function


```python
f = open("births.csv", 'r')
text = f.read()
print(text)
```

    year,month,date_of_month,day_of_week,births
    1994,1,1,6,8096
    1994,1,2,7,7772
    1994,1,3,1,10142
    1994,1,4,2,11248
    1994,1,5,3,11053
    1994,1,6,4,11406
    1994,1,7,5,11251
    1994,1,8,6,8653
    1994,1,9,7,7910
    1994,1,10,1,10498
    1994,1,11,2,11706
    1994,1,12,3,11567
    1994,1,13,4,11212


It is important to note that for our data to be easier to read, we could split the file's content on the new-line character


```python
lines_list = text.split("\n")
lines_list
```




    ['year,month,date_of_month,day_of_week,births',
     '1994,1,1,6,8096',
     '1994,1,2,7,7772',
     '1994,1,3,1,10142',
     '1994,1,4,2,11248',
     '1994,1,5,3,11053',
     '1994,1,6,4,11406',
     '1994,1,7,5,11251',
     '1994,1,8,6,8653',
     '1994,1,9,7,7910',
     '1994,1,10,1,10498',
     '1994,1,11,2,11706',
     '1994,1,12,3,11567',
     '1994,1,13,4,11212',
     '1994,1,14,5,11570',
     ...]


One of the great features of Jupyter notebook is that you can edit and re-run cells as many times as you want. In real-world data analysis, it's common to try many different techniques on a dataset in order to explore what works. In these cases, being able to edit your code and re-run is critical, because it lets you iteratively analyze your data.

For the next step, we want to know the total number of births for each unique day of the week. We will start by doing the following steps:  
* Create an empty dictionary
* Select all but the header row and assign to a new list object
* Iterate through this new list 
  * Split each line on the comma delimiter
  * Extract the day_of_week value and the births value for each line
  * If the day_of_week value already exists as a key in the dictionary, add the births value to the existing, associated value
  * If the day_of_week value doesn't exist as a key, add it to the dictionary and set the associated value to the births value for that line
* Outside the loop, we display the dictionary to get total number of births


```python
data_no_header = lines_list[1:len(lines_list)]
days_counts = dict()

for line in data_no_header:
    split_line = line.split(",")
    day_of_week = split_line[3]
    num_births = int(split_line[4])

    if day_of_week in days_counts:
        days_counts[day_of_week] = days_counts[day_of_week] + num_births
    else:
        days_counts[day_of_week] = num_births

days_counts
```




    {'1': 5789166,
     '2': 6446196,
     '3': 6322855,
     '4': 6288429,
     '5': 6233657,
     '6': 4562111,
     '7': 4079723}

This is how we get insights from our data, selecting the specific rows and iterating through a list of data to summarize our data set into new actionable insights that could be used as we go further in our data analysis. We will dive more in our data set in the coming projects. 
