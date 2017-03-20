---
title       : Getting started with plotly
description : This chapter will introduce you to plotly and how you can use Python and plotly together to create stunning data visualizations.
attachments :
  slides_link : https://s3.amazonaws.com/assets.datacamp.com/course/teach/slides_example.pdf

--- type:NormalExercise lang:python xp:100 skills:1 key:880d44e748
## Let's start with a scatter plot

This exercise features an example of plotly. We'll start by using Numpy to create some random data. Then, we'll plot the data as a scatter plot. Since this is the first exercise, we'll do most of the work :) Simply execute the code.

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
success_msg("Great work! Plotly plots are interactive, so make sure you play around with the scatter plot you produced!")
```

--- type:NormalExercise lang:python xp:100 skills:2 key:5e407595b2
## Plotly Line Chart
L

Hang on tight - your code may take a moment to run :)

*** =instructions
- Just submit the code

*** =hint

*** =pre_exercise_code
```{python}
import plotly.plotly as py
import plotly.graph_objs as go
py.sign_in('datacamp_python', '9IB7oEs6qib6jiwOTwRA')
```

*** =sample_code
```{python}
# Add data
month = ['January', 'February', 'March', 'April', 'May', 'June', 'July',
         'August', 'September', 'October', 'November', 'December']
high_2014 = [28.8, 28.5, 37.0, 56.8, 69.7, 79.7, 78.5, 77.8, 74.1, 62.6, 45.3, 39.9]
low_2014 = [12.7, 14.3, 18.6, 35.5, 49.9, 58.0, 60.0, 58.6, 51.7, 45.2, 32.2, 29.1]

# Create and style traces
trace0 = go.Scatter(
    x = month,
    y = high_2014,
    name = 'High 2014',
    line = dict(
        color = ('rgb(205, 12, 24)'),
        width = 4)
)
trace1 = go.Scatter(
    x = month,
    y = low_2014,
    name = 'Low 2014',
    line = dict(
        color = ('rgb(22, 96, 167)'),
        width = 4,)

data = [trace0, trace1]

# Edit the layout
layout = dict(title = 'Average High and Low Temperatures in New York',
              xaxis = dict(title = 'Month'),
              yaxis = dict(title = 'Temperature (degrees F)'),
              )

# Make the plot!
fig = dict(data=data, layout=layout)
py.plot(fig, filename='styled-line')
```

*** =solution
```{python}
# Add data
month = ['January', 'February', 'March', 'April', 'May', 'June', 'July',
         'August', 'September', 'October', 'November', 'December']
high_2014 = [28.8, 28.5, 37.0, 56.8, 69.7, 79.7, 78.5, 77.8, 74.1, 62.6, 45.3, 39.9]
low_2014 = [12.7, 14.3, 18.6, 35.5, 49.9, 58.0, 60.0, 58.6, 51.7, 45.2, 32.2, 29.1]

# Create and style traces
trace0 = go.Scatter(
    x = month,
    y = high_2014,
    name = 'High 2014',
    line = dict(
        color = ('rgb(205, 12, 24)'),
        width = 4)
)
trace1 = go.Scatter(
    x = month,
    y = low_2014,
    name = 'Low 2014',
    line = dict(
        color = ('rgb(22, 96, 167)'),
        width = 4,)

data = [trace0, trace1]

# Edit the layout
layout = dict(title = 'Average High and Low Temperatures in New York',
              xaxis = dict(title = 'Month'),
              yaxis = dict(title = 'Temperature (degrees F)'),
              )

# Make the plot!
fig = dict(data=data, layout=layout)
py.plot(fig, filename='styled-line')

```

*** =sct
```{python}
success_msg("Great work!")
```
--- type:NormalExercise lang:python xp:100 skills:2 key:8546b612c1
## Try them together

Create the third plot

Hang on tight - your code may take a moment to run :)


*** =instructions
- Click submit answer
*** =hint

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

N = 100
random_x = np.linspace(0, 1, N)
random_y0 = np.random.randn(N)+5
random_y1 = np.random.randn(N)
random_y2 = np.random.randn(N)-5

# Create traces
trace0 = go.Scatter(
    x = random_x,
    y = random_y0,
    mode = 'lines',
    name = 'lines'
)
trace1 = go.Scatter(
    x = random_x,
    y = random_y1,
    mode = 'lines+markers',
    name = 'lines+markers'
)
trace2 = go.Scatter(
    x = random_x,
    y = random_y2,
    mode = 'markers',
    name = 'markers'
)
data = [trace0, trace1, trace2]

py.iplot(data, filename='line-mode')
```

*** =solution
```{python}
# Create random data with numpy
import numpy as np

N = 100
random_x = np.linspace(0, 1, N)
random_y0 = np.random.randn(N)+5
random_y1 = np.random.randn(N)
random_y2 = np.random.randn(N)-5

# Create traces
trace0 = go.Scatter(
    x = random_x,
    y = random_y0,
    mode = 'lines',
    name = 'lines'
)
trace1 = go.Scatter(
    x = random_x,
    y = random_y1,
    mode = 'lines+markers',
    name = 'lines+markers'
)
trace2 = go.Scatter(
    x = random_x,
    y = random_y2,
    mode = 'markers',
    name = 'markers'
)
data = [trace0, trace1, trace2]

py.plot(data, filename='line-mode')

```

*** =sct
```{python}
success_msg("Looking good!")
```

