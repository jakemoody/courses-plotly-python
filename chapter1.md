---
title       : Getting started with plotly
description : This chapter will introduce you to plotly and how you can use Python and plotly together to create stunning data visualizations.
attachments :
  slides_link : https://s3.amazonaws.com/assets.datacamp.com/course/teach/slides_example.pdf

--- type:NormalExercise lang:python xp:100 skills:1 key:880d44e748
## Let's start with a scatter plot

This exercise features an example of plotly.

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

# Plot and embed in ipython notebook!
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

# Plot and embed in ipython notebook!
py.plot(data, filename='basic-scatter')

```

*** =sct
```{python}
success_msg("Great work!")
```
--- type:NormalExercise lang:python xp:100 skills:2 key:5e407595b2
## Plotly Line Chart
Create your second cool plot.

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

# Create random data with numpy
import numpy as np

N = 500
random_x = np.linspace(0, 1, N)
random_y = np.random.randn(N)

# Create a trace
trace = go.Scatter(
    x = random_x,
    y = random_y
)

data = [trace]

py.plot(data, filename='basic-line')

```

*** =solution
```{python}
# Create random data with numpy
import numpy as np

N = 500
random_x = np.linspace(0, 1, N)
random_y = np.random.randn(N)

# Create a trace
trace = go.Scatter(
    x = random_x,
    y = random_y
)

data = [trace]

py.plot(data, filename='basic-line')

```

*** =sct
```{python}
success_msg("Great work!")
```
--- type:NormalExercise lang:python xp:100 skills:2 key:8546b612c1
## Try them together

Now we're going to try and scatter plots and line plots together! We've already created some random data for your to play around with:

- `x_axis` will serve as your x-axis for each trace
- `random_y0` will serve as data along the y-axis in `trace0`
- `random_y1` will serve as data along the y-axis in `trace1`
- `random_y2` will serve as data along the y-axis in `trace2`


*** =instructions
- Finish the code to create `trace0` using `random_y0` 
- Finish the code to create `trace1` using `random_y1`
- Finish the code to create `trace2` using `random_y2`
- Combine the data by filling in the blanks!
- Execute the code!
- 
*** =hint
- Take a look at the previous exercises for a refresher on format!

*** =pre_exercise_code
```{python}
import plotly.plotly as py
import plotly.graph_objs as go
py.sign_in('datacamp_python', '9IB7oEs6qib6jiwOTwRA')

import numpy as np

N = 100
x_axis = np.linspace(0, 1, N)
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

