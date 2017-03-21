---
title       : Starting with some simple Plotly plots
description : This chapter will introduce you to plotly and how you can use Python and plotly together to create stunning data visualizations.
attachments :
  slides_link : https://s3.amazonaws.com/assets.datacamp.com/course/teach/slides_example.pdf

--- type:NormalExercise lang:python xp:100 skills:1 key:880d44e748
## Let's start with a scatter plot

This exercise features an example of Plotly. We'll start by using Numpy to create some random data. Then, we'll plot the data as a scatter plot. Since this is the first exercise, we'll do most of the work :) Simply execute the code.

Hang on tight - your code may take a moment to run :)

*** =instructions
- Just hit submit answer

*** =hint
- No hints!

*** =pre_exercise_code
```{python}
import plotly.plotly as py
import plotly.graph_objs as go
py.sign_in('datacamp_python', '9IB7oEs6qib6jiwOTwRA')
```

*** =sample_code
```{python}
# Create random data with numpy
import numpy as np

N = 1000
random_x = np.random.randn(N)
random_y = np.random.randn(N)

# Create a trace
trace = go.Scatter(
    x = random_x,
    y = random_y,
    mode = 'markers'
)

data = [trace]

# Plot the data as a scatter plot!
py.plot(data, filename='basic-scatter')

```

*** =solution
```{python}
# Create random data with numpy
import numpy as np

N = 1000
random_x = np.random.randn(N)
random_y = np.random.randn(N)

# Create a trace
trace = go.Scatter(
    x = random_x,
    y = random_y,
    mode = 'markers'
)

data = [trace]

# Plot the data as a scatter plot!
py.plot(data, filename='basic-scatter')

```

*** =sct
```{python}
test_object()
success_msg("Great work!")
```
--- type:NormalExercise lang:python xp:100 skills:2 key:5e407595b2
## Temperature highs and lows

Alright now it's time to learn by doing! In this exerise you will be challenged to create a Plotly line chart showing Avg. Temperature Highs and Lows in New York throughout 2014. The following data is already available in your environment:

- `month`, contains each month
- `high_2014`, contains the average high temperature for each month
- `low_2014`, contains the average low temperature for each month

Follow the instructions to complete the code and run the exercise to produce the plot!

*** =instructions
- `trace0` has been done for you
- Fill in the blanks to complete `trace1`. Use the code used to create `trace0` as a guide. 

*** =hint
- You'll need to input the `low_2014` object in one of the blanks. 

*** =pre_exercise_code
```{python}
import plotly.plotly as py
import plotly.graph_objs as go
py.sign_in('datacamp_python', '9IB7oEs6qib6jiwOTwRA')
# Add data
month = ['January', 'February', 'March', 'April', 'May', 'June', 'July',
         'August', 'September', 'October', 'November', 'December']
high_2014 = [28.8, 28.5, 37.0, 56.8, 69.7, 79.7, 78.5, 77.8, 74.1, 62.6, 45.3, 39.9]
low_2014 = [12.7, 14.3, 18.6, 35.5, 49.9, 58.0, 60.0, 58.6, 51.7, 45.2, 32.2, 29.1]
```

*** =sample_code
```{python}
# Create and style traces

# trace0 is done for you
trace0 = go.Scatter(
    x = month,
    y = high_2014,
    name = 'High 2014',
    line = dict(
        color = ('rgb(205, 12, 24)'),
        width = 4))

# fill in the blanks         
trace1 = go.Scatter(
    x = ___,
    y = ___,
    name = 'Low 2014',
    line = dict(
        color = ('rgb(22, 96, 167)'),
        width = 4,))

data = [trace0, trace1]

# Edit the layout - nothing to do here
layout = dict(title = 'Average High and Low Temperatures in New York',
              xaxis = dict(title = 'Month'),
              yaxis = dict(title = 'Temperature (degrees F)'))

# Make the plot!
fig = dict(data=data, layout=layout)
py.plot(fig, filename='styled-line')
```

*** =solution
```{python}
# Create and style traces
trace0 = go.Scatter(
    x = month,
    y = high_2014,
    name = 'High 2014',
    line = dict(
        color = ('rgb(205, 12, 24)'),
        width = 4))
        
trace1 = go.Scatter(
    x = month,
    y = low_2014,
    name = 'Low 2014',
    line = dict(
        color = ('rgb(22, 96, 167)'),
        width = 4,))

data = [trace0, trace1]

# Edit the layout
layout = dict(title = 'Average High and Low Temperatures in New York',
              xaxis = dict(title = 'Month'),
              yaxis = dict(title = 'Temperature (degrees F)'))

# Make the plot!
fig = dict(data=data, layout=layout)
py.plot(fig, filename='styled-line')

```

*** =sct
```{python}
success_msg("Great work! Plotly makes it easy to not only visualize the temperate changes over time, but also interactively view the specific measures for each month by hovering over the plot.")
```

--- type:NormalExercise lang:python xp:100 skills:2 key:8546b612c1
## Try them together

Now we're going to try and scatter plots and line plots together! We've already created some random data for your to play around with:

- `random_x` will serve as your x-axis for each trace
- `random_y0` will serve as data along the y-axis in `trace0`
- `random_y1` will serve as data along the y-axis in `trace1`
- `random_y2` will serve as data along the y-axis in `trace2`


*** =instructions
- Finish the code to create `trace0` using `random_y0` 
- Finish the code to create `trace1` using `random_y1`
- Finish the code to create `trace2` using `random_y2`
- Combine the data by filling in the blanks!
- Execute the code!
*** =hint
- Take a look at the previous exercises for a refresher on format!

*** =pre_exercise_code
```{python}
import plotly.plotly as py
import plotly.graph_objs as go
py.sign_in('datacamp_python', '9IB7oEs6qib6jiwOTwRA')

import numpy as np

N = 100
random_x = np.linspace(0, 1, N)
random_y0 = np.random.randn(N)+5
random_y1 = np.random.randn(N)
random_y2 = np.random.randn(N)-5

```

*** =sample_code
```{python}
# Create trace0
trace0 = go.Scatter(
    x = ___,
    y = ___,
    mode = 'lines',
    name = 'lines'
)

# Create trace1
trace1 = go.Scatter(
    x = ___,
    y = ___,
    mode = 'lines+markers',
    name = 'lines+markers'
)

# Create trace2
trace2 = go.Scatter(
    x = ___,
    y = ___,
    mode = 'markers',
    name = 'markers'
)

# Fill in the blanks to combine the data and plot!
data = [___, ___, ___]
py.plot(data, filename='line-mode')

```

*** =solution
```{python}
# Create trace0
trace0 = go.Scatter(
    x = random_x,
    y = random_y0,
    mode = 'lines',
    name = 'lines'
)

# Create trace1
trace1 = go.Scatter(
    x = random_x,
    y = random_y1,
    mode = 'lines+markers',
    name = 'lines+markers'
)

# Create trace2
trace2 = go.Scatter(
    x = random_x,
    y = random_y2,
    mode = 'markers',
    name = 'markers'
)

# Combine the data and plot!
data = [trace0, trace1, trace2]
py.plot(data, filename='line-mode')
```

*** =sct
```{python}
success_msg("Looking good!")
```
--- type:NormalExercise lang:python xp:100 skills:2 key:7a036c016a
## Bar charts with Plotly

Let's try one more plot before we finish the chapter! In this exercise you want to compare 2 companies, Company A and Company B. Specifically, you want to compare the headcount by department of each organization. A bar chart is a great way to do this! The traces are already created for you. Simply fill in the blanks toward the end of the code to combine the data and create the plot.


*** =instructions
- Fill in the blanks to combine the traces into the `data` object
- Fill in the blanks to create the `fig` object

*** =hint

*** =pre_exercise_code
```{python}
import plotly.plotly as py
import plotly.graph_objs as go
py.sign_in('datacamp_python', '9IB7oEs6qib6jiwOTwRA')
```

*** =sample_code
```{python}
# Create trace
trace0 = go.Bar(
    x=['Marketing', 'Production', 'Finance', 'R&D', 'HR'],
    y=[5,14,3,3,2],
    name='Company A'
)
trace1 = go.Bar(
    x=['Marketing', 'Production', 'Finance', 'R&D', 'HR'],
    y=[2,10,3,8,1],
    name='Company B'
)

# Combine data and plot!
data = [trace0, trace1]
layout = go.Layout(
    barmode='group'
)

fig = go.Figure(data=data, layout=layout)
py.plot(fig, filename='grouped-bar')


```

*** =solution
```{python}
# Create trace
trace0 = go.Bar(
    x=['Marketing', 'Production', 'Finance', 'R&D', 'HR'],
    y=[5,14,3,3,2],
    name='Company A'
)
trace1 = go.Bar(
    x=['Marketing', 'Production', 'Finance', 'R&D', 'HR'],
    y=[2,10,3,8,1],
    name='Company B'
)

# Fill in the blanks to combine the data and make the plot
data = [___, ___]
layout = go.Layout(
    barmode='group'
)

fig = go.Figure(data=___, layout=___)
py.plot(fig, filename='grouped-bar')
```

*** =sct
```{python}
success_msg("Nice!")
```
