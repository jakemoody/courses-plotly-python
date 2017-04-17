---
title       : Starting with some simple Plotly plots
description : This chapter will introduce you to plotly and how you can use Python and plotly together to create stunning data visualizations.
attachments :
  slides_link : https://s3.amazonaws.com/assets.datacamp.com/course/teach/slides_example.pdf

--- type:NormalExercise lang:python xp:100 skills:1 key:880d44e748
## Let's start with a scatter plot

This exercise features an example of Plotly. The first thing we need to do is import the Plotly python library. Here's how it should look:

```
import plotly.plotly as py
import plotly.graph_objs as go
```

Next, we'll use Numpy to create some random data. Then, we'll plot the data as a scatter plot. Since this is the first exercise, we'll do most of the work :) Just import the library and finish the `py.plot` function at the end to create a scatter plot. 



*** =instructions
- Fill in the blanks to import `plotly.plotly` as `py`
- Fill in the blanks to import `plotly.graph_objs` as `go`
- Finish the `py.plot` function by inserting `'basic-scatter'` as the filename. 

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
# Import plotly
import ___ as ___
import ___ as ___

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
py.plot(data, filename=___)

```

*** =solution
```{python}
# Import plotly
import plotly.plotly as py
import plotly.graph_objs as go

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
test_import("plotly.plotly")
test_import("plotly.graph_objs")
test_object("data", do_eval = False)
test_function_v2("plotly.graph_objs.Scatter")
test_function_v2("plotly.plotly.plot")
success_msg("Great work! Plotly plots are interactive, so make sure you play around with the scatter plot you produced! We will load the library for you in the rest of the exercises so you can focus on the code!")
```
--- type:NormalExercise lang:python xp:100 skills:2 key:5e407595b2
## Temperature highs and lows

Alright now it's time to learn by doing! In this exercise you will be challenged to create a Plotly line chart showing average temperature highs and lows in New York throughout 2014. The following data is already available in your environment:

- `month`, contains each month for which there is data
- `high_2014`, contains the average high temperature for each month
- `low_2014`, contains the average low temperature for each month

To begin, we need to first create traces for our data. Traces define and format the data that will ultimately be plotted. The first trace, `trace0`, has been created for you. Let's break it down; To create this trace we used the `go.Scatter()` function which is used to create a trace for a scatter plot. In this function we defined the x-axis as our `month` object, the y-axis as our `high_2014` object, we named the trace 'High 2014', we determined that we wanted the line to be a certain color and width. 

Now it's your turn! Follow the instructions to complete the code and run the exercise to produce the plot!

*** =instructions
- `trace0` has been done for you!
- Create `trace1` using the available information. Using `month` and `low` in the environment, set `x` and `y` appropriately. The name should be `'Low 2014'`, the color of the line should be defined as `'rgb(22, 96, 167)'`, and the width of the line should be `'4'`. 
- Execute the rest of the code. 

*** =hint
- You'll need to use the `low_2014` object to create `trace1` 

*** =pre_exercise_code
```{python}
import plotly.plotly as py
import plotly.graph_objs as go
py.sign_in('datacamp_python', '9IB7oEs6qib6jiwOTwRA')
# Edit the layout
layout = dict(title = 'Average High and Low Temperatures in New York',
              xaxis = dict(title = 'Month'),
              yaxis = dict(title = 'Temperature (degrees F)'))
# Add data
month = ['January', 'February', 'March', 'April', 'May', 'June', 'July',
         'August', 'September', 'October', 'November', 'December']
high_2014 = [28.8, 28.5, 37.0, 56.8, 69.7, 79.7, 78.5, 77.8, 74.1, 62.6, 45.3, 39.9]
low_2014 = [12.7, 14.3, 18.6, 35.5, 49.9, 58.0, 60.0, 58.6, 51.7, 45.2, 32.2, 29.1]
```

*** =sample_code
```{python}
# trace0 is done for you
trace0 = go.Scatter(
    x = month,
    y = high_2014,
    name = 'High 2014',
    line = dict(
        color = ('rgb(205, 12, 24)'),
        width = 4))

# Create trace1       



# Make the plot!
data = [trace0, trace1]
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
test_object("trace0",incorrect_msg = "Are you sure you didn't change the trace0 object?",do_eval=False)
test_object("trace1",incorrect_msg = "Did you use low_2014 to create the trace1 object?",do_eval=False)
test_object("data",incorrect_msg = "Are you sure you didn't change the data object?",do_eval=False)
test_object("layout",incorrect_msg = "Are you sure you didn't change the layout object?",do_eval=False)
test_function_v2("plotly.plotly.plot")
test_function_v2("plotly.graph_objs.Scatter")
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
- Finish `trace0` using the objects stated above. 
- Create `trace1`. The `mode` and `name` argument should be 'lines+markers'
- Create `trace2`. The `mode` and `name` argument should be 'markers'
- Combine the traces to create a `data` object. 
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
# Finish trace0
trace0 = go.Scatter(
    x = ___,
    y = ___,
    mode = 'lines',
    name = 'lines'
)

# Create trace1


# Create trace2


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
test_object("trace0",incorrect_msg = "Did you use random_y0 to create the trace0 object?",do_eval=False)
test_object("trace1",incorrect_msg = "Did you use random_y1 to create the trace0 object?",do_eval=False)
test_object("trace2",incorrect_msg = "Did you use random_y2 to create the trace0 object?",do_eval=False)
test_object("data",incorrect_msg = "Double check your data object!",do_eval=False)
test_function_v2("plotly.plotly.plot")
test_function_v2("plotly.graph_objs.Scatter")
success_msg("Looking good!")
```
--- type:NormalExercise lang:python xp:100 skills:2 key:7a036c016a
## Bar charts with Plotly

Let's try one more plot before we finish the chapter! In this exercise you want to compare 2 companies, Company A and Company B. Specifically, you want to compare the headcount by department of each organization. A bar chart is a great way to do this! 

In this exercise, we will create two traces using the `go.Bar()` function. Similar to the `go.Scatter()` function from the previous exercises, we will need to define `x` and `y` in the function. We will also want to define a `name` ('Company A' or 'Company B') for each trace since we are creating a grouped bar chart. The data you need is preloaded in the console. The `departments` will serve as your x-axis. The `headcount_company_a` and `headcount_company_b` objects show the headcount numbers by department for each organization. 


*** =instructions
- Create `trace0` using the objects available in the console and the information provided above
- Create `trace1` using the objects available in the console and the information provided above
- Combine `trace0` and `trace1` to create the `data` object
- Fill in the blanks to create the `fig` object

*** =hint

*** =pre_exercise_code
```{python}
import plotly.plotly as py
import plotly.graph_objs as go
py.sign_in('datacamp_python', '9IB7oEs6qib6jiwOTwRA')

departments = ['Marketing', 'Production', 'Finance', 'R&D', 'HR']
headcount_company_a = [5,14,3,3,2]
headcount_company_b = [2,10,3,8,1]
```

*** =sample_code
```{python}
# Create trace0

# Create trace1

# Fill in the blanks to combine the data and make the plot
data = [___, ___]

# Create the layout
layout = go.Layout(
    barmode='group'
)

fig = go.Figure(data=___, layout=___)
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

# Combine data and plot!
data = [trace0, trace1]
layout = go.Layout(
    barmode='group'
)

fig = go.Figure(data=data, layout=layout)
py.plot(fig, filename='grouped-bar')
```

*** =sct
```{python}
test_object("trace0",incorrect_msg = "Did you change the trace0 object?",do_eval=False)
test_object("trace1",incorrect_msg = "Did you chance the trace1 object?",do_eval=False)
test_object("data",incorrect_msg = "Double check your data object!",do_eval=False)
test_object("fig",incorrect_msg = "Double check your fig object!",do_eval=False)
test_function_v2("plotly.graph_objs.Bar")
test_function_v2("plotly.graph_objs.Figure")
test_function_v2("plotly.graph_objs.Layout")
test_function_v2("plotly.plotly.plot")
success_msg("Nice! Let's try some more plots in the next chapter!")
```
