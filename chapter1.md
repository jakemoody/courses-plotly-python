---
title       : Getting started with plot.ly
description : A couple exercises to get started
attachments :
  slides_link : https://s3.amazonaws.com/assets.datacamp.com/course/teach/slides_example.pdf

--- type:NormalExercise lang:python xp:100 skills:1 key:880d44e748
## Plotly example

This exercise features an example of plotly.

Hang on tight - your code may take a moment to run :)

*** =instructions
- Just hit submit answer

*** =hint
- No hints!

*** =pre_exercise_code
```{python}
import plotly.plotly as py
from plotly.graph_objs import Scatter
py.sign_in('datacamp_python', '9IB7oEs6qib6jiwOTwRA')
```

*** =sample_code
```{python}
x = [1, 2, 3]; y = [1, 2, 3];
plot([Scatter(x=x, y=y, mode = 'markers')])
```

*** =solution
```{python}
# no code
```

*** =sct
```{python}
success_msg("Great work!")
```

--- type:NormalExercise lang:python xp:100 skills:2 key:8546b612c1
## Plotly Example No. 2

Create your second cool plot.

Hang on tight - your code may take a moment to run :)


*** =instructions
- Click submit answer
*** =hint

*** =pre_exercise_code
```{python}
import plotly.plotly as py
py.sign_in('datacamp_python', '9IB7oEs6qib6jiwOTwRA')
```

*** =sample_code
```{python}
import plotly.plotly as py
from plotly.graph_objs import *
import pandas as pd

df = pd.read_csv('https://plot.ly/~etpinard/191.csv')

py.plot({
    'data': [
        Scatter(x=df[continent+', x'],
                y=df[continent+', y'],
                text=df[continent+', text'],
                marker=Marker(size=df[continent+', size'], sizemode='area', sizeref=131868,),
                mode='markers',
                name=continent) for continent in ['Africa', 'Americas', 'Asia', 'Europe', 'Oceania']
    ],
    'layout': Layout(xaxis=XAxis(title='Life Expectancy'), yaxis=YAxis(title='GDP per Capita', type='log'))
}, show_link=False)
```

*** =solution
```{python}
import plotly.plotly as py
from plotly.graph_objs import *
import pandas as pd

df = pd.read_csv('https://plot.ly/~etpinard/191.csv')

py.plot({
    'data': [
        Scatter(x=df[continent+', x'],
                y=df[continent+', y'],
                text=df[continent+', text'],
                marker=Marker(size=df[continent+', size'], sizemode='area', sizeref=131868,),
                mode='markers',
                name=continent) for continent in ['Africa', 'Americas', 'Asia', 'Europe', 'Oceania']
    ],
    'layout': Layout(xaxis=XAxis(title='Life Expectancy'), yaxis=YAxis(title='GDP per Capita', type='log'))
}, show_link=False)
```

*** =sct
```{python}
success_msg("Looking good!")
```

--- type:NormalExercise lang:python xp:100 skills:2 key:368be49690
## Plotly Example #3

Make your 3rd Plotly Plot

Hang on tight - your code may take a moment to run :)

*** =instructions
- Click submit answer

*** =hint
- No hints!
*** =pre_exercise_code

```{python}
import plotly.plotly as py
py.sign_in('datacamp_python', '9IB7oEs6qib6jiwOTwRA')
```

*** =sample_code
```{python}
import plotly.plotly as py
from plotly.graph_objs import *
import pandas as pd

df = pd.read_csv('https://raw.githubusercontent.com/plotly/datasets/master/2011_us_ag_exports.csv')

for col in df.columns:
    df[col] = df[col].astype(str)

scl = [[0.0, 'rgb(242,240,247)'],[0.2, 'rgb(218,218,235)'],[0.4, 'rgb(188,189,220)'],\
            [0.6, 'rgb(158,154,200)'],[0.8, 'rgb(117,107,177)'],[1.0, 'rgb(84,39,143)']]

df['text'] = df['state'] + '<br>' +\
    'Beef '+df['beef']+' Dairy '+df['dairy']+'<br>'+\
    'Fruits '+df['total fruits']+' Veggies ' + df['total veggies']+'<br>'+\
    'Wheat '+df['wheat']+' Corn '+df['corn']

data = [ dict(
        type='choropleth',
        colorscale = scl,
        autocolorscale = False,
        locations = df['code'],
        z = df['total exports'].astype(float),
        locationmode = 'USA-states',
        text = df['text'],
        marker = dict(
            line = dict (
                color = 'rgb(255,255,255)',
                width = 2
            ) ),
        colorbar = dict(
            title = "Millions USD")
        ) ]

layout = dict(
        title = '2011 US Agriculture Exports by State<br>(Hover for breakdown)',
        geo = dict(
            scope='usa',
            projection=dict( type='albers usa' ),
            showlakes = True,
            lakecolor = 'rgb(255, 255, 255)'),
             )

fig = dict( data=data, layout=layout )
py.plot( fig, filename='d3-cloropleth-map' )
```

*** =solution
```{python}
import plotly.plotly as py
from plotly.graph_objs import *
import pandas as pd

df = pd.read_csv('https://raw.githubusercontent.com/plotly/datasets/master/2011_us_ag_exports.csv')

for col in df.columns:
    df[col] = df[col].astype(str)

scl = [[0.0, 'rgb(242,240,247)'],[0.2, 'rgb(218,218,235)'],[0.4, 'rgb(188,189,220)'],\
            [0.6, 'rgb(158,154,200)'],[0.8, 'rgb(117,107,177)'],[1.0, 'rgb(84,39,143)']]

df['text'] = df['state'] + '<br>' +\
    'Beef '+df['beef']+' Dairy '+df['dairy']+'<br>'+\
    'Fruits '+df['total fruits']+' Veggies ' + df['total veggies']+'<br>'+\
    'Wheat '+df['wheat']+' Corn '+df['corn']

data = [ dict(
        type='choropleth',
        colorscale = scl,
        autocolorscale = False,
        locations = df['code'],
        z = df['total exports'].astype(float),
        locationmode = 'USA-states',
        text = df['text'],
        marker = dict(
            line = dict (
                color = 'rgb(255,255,255)',
                width = 2
            ) ),
        colorbar = dict(
            title = "Millions USD")
        ) ]

layout = dict(
        title = '2011 US Agriculture Exports by State<br>(Hover for breakdown)',
        geo = dict(
            scope='usa',
            projection=dict( type='albers usa' ),
            showlakes = True,
            lakecolor = 'rgb(255, 255, 255)'),
             )

fig = dict( data=data, layout=layout )
py.plot( fig, filename='d3-cloropleth-map' )
```

*** =sct
```{python}
success_msg("Super!")

```
