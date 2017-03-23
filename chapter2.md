---
title       : Getting a bit more fancy
description : More advanced plotting

--- type:NormalExercise lang:python xp:100 skills:2 key:dea4219835
## Boxplots with Plotly

In this exercise you will create a boxplot! Actually, you will create a couple different versions using the same data, `boxplot_data` which is preloaded in the console. We will create four versions of the boxplot: one with all the points, one with only the whiskers, one with suspected outliers, and one with whiskers and outliers. In order to get this variety, you need to change the `boxpoints` argument in the `go.Box()` functions to the right. 

*** =instructions
- Set `boxpoints` equal to `'all'`
- Set `boxpoints` equal to `False`
- Set `boxpoints` equal to `'suspectedoutliers'`
- Set `boxpoints` equal to `'outliers'`
- Combine the trace objects to create the `data` object by filling in the blanks

*** =hint
- Simply fill in the blanks using the instructions! 
*** =pre_exercise_code
```{python}
import plotly.plotly as py
import plotly.graph_objs as go
py.sign_in('datacamp_python', '9IB7oEs6qib6jiwOTwRA')
boxplot_data = [0.75, 5.25, 5.5, 6, 6.2, 6.6, 6.80, 7.0, 7.2, 7.5, 7.5, 7.75, 8.15, 8.15, 8.65, 8.93, 9.2, 9.5, 10, 10.25, 11.5, 12, 16, 20.90, 22.3, 23.25]
```

*** =sample_code
```{python}
# Create traces
trace0 = go.Box(
    y = boxplot_data,
    name = "All Points",
    jitter = 0.3,
    pointpos = -1.8,
    boxpoints = ___,
    marker = dict(
        color = 'rgb(7,40,89)'),
    line = dict(
        color = 'rgb(7,40,89)')
)

trace1 = go.Box(
    y = boxplot_data,
    name = "Only Whiskers",
    boxpoints = ___,
    marker = dict(
        color = 'rgb(9,56,125)'),
    line = dict(
        color = 'rgb(9,56,125)')
)

trace2 = go.Box(
    y = boxplot_data,
    name = "Suspected Outliers",
    boxpoints = ___,
    marker = dict(
        color = 'rgb(8,81,156)',
        outliercolor = 'rgba(219, 64, 82, 0.6)',
        line = dict(
            outliercolor = 'rgba(219, 64, 82, 0.6)',
            outlierwidth = 2)),
    line = dict(
        color = 'rgb(8,81,156)')
)

trace3 = go.Box(
    y = boxplot_data,
    name = "Whiskers and Outliers",
    boxpoints = ___,
    marker = dict(
        color = 'rgb(107,174,214)'),
    line = dict(
        color = 'rgb(107,174,214)')
)

# Combine data
data = [___,___,___,___]

layout = go.Layout(
    title = "Box Plot Styling Outliers"
)

fig = go.Figure(data=data,layout=layout)
py.plot(fig, filename = "Box Plot Styling Outliers")
```

*** =solution
```{python}
# Create traces
trace0 = go.Box(
    y = boxplot_data,
    name = "All Points",
    jitter = 0.3,
    pointpos = -1.8,
    boxpoints = 'all',
    marker = dict(
        color = 'rgb(7,40,89)'),
    line = dict(
        color = 'rgb(7,40,89)')
)

trace1 = go.Box(
    y = boxplot_data,
    name = "Only Whiskers",
    boxpoints = False,
    marker = dict(
        color = 'rgb(9,56,125)'),
    line = dict(
        color = 'rgb(9,56,125)')
)

trace2 = go.Box(
    y = boxplot_data,
    name = "Suspected Outliers",
    boxpoints = 'suspectedoutliers',
    marker = dict(
        color = 'rgb(8,81,156)',
        outliercolor = 'rgba(219, 64, 82, 0.6)',
        line = dict(
            outliercolor = 'rgba(219, 64, 82, 0.6)',
            outlierwidth = 2)),
    line = dict(
        color = 'rgb(8,81,156)')
)

trace3 = go.Box(
    y = boxplot_data,
    name = "Whiskers and Outliers",
    boxpoints = 'outliers',
    marker = dict(
        color = 'rgb(107,174,214)'),
    line = dict(
        color = 'rgb(107,174,214)')
)

# Combine data
data = [trace0,trace1,trace2,trace3]

layout = go.Layout(
    title = "Box Plot Styling Outliers"
)

fig = go.Figure(data=data,layout=layout)
py.plot(fig, filename = "Box Plot Styling Outliers")

```

*** =sct
```{python}
test_object("trace0",incorrect_msg = "Did you change the trace0 object?",do_eval=False)
test_object("trace1",incorrect_msg = "Did you assign the correct value to the boxpoints argument?",do_eval=False)
test_object("trace2",incorrect_msg = "Did you assign the correct value to the boxpoints argument?",do_eval=False)
test_object("trace3",incorrect_msg = "Did you assign the correct value to the boxpoints argument?",do_eval=False)
test_object("data",incorrect_msg = "Did you assign the correct values to the data object?",do_eval=False)
success_msg("Super! Now you're getting the hang out it!")
```


--- type:NormalExercise lang:python xp:100 skills:2 key:c6553f5c85
## Mapping Mt. Bruno

In this exercise we will visualize elavation data with Plotly! The data for Mt. Bruno is preloaded in the console as `z_data`. 
All you need to do is fill in the blanks and execute the code. 

*** =instructions
- Fill in the blanks to create the `fig` object. 

*** =hint
- Look at the Plotly documentation or check previous exercises if you forget the syntax. 

*** =pre_exercise_code
```{python}
import plotly.plotly as py
import plotly.graph_objs as go
py.sign_in('datacamp_python', '9IB7oEs6qib6jiwOTwRA')
import pandas as pd
# Read data from a csv
z_data = pd.read_csv('https://raw.githubusercontent.com/plotly/datasets/master/api_docs/mt_bruno_elevation.csv')

```

*** =sample_code
```{python}
data = [
    go.Surface(
        z=z_data.as_matrix()
    )
]
layout = go.Layout(
    title='Mt Bruno Elevation',
    autosize=False,
    width=500,
    height=500,
    margin=dict(
        l=65,
        r=50,
        b=65,
        t=90
    )
)
fig = go.Figure(data=___, layout=___)
py.plot(fig, filename='elevations-3d-surface')
```

*** =solution
```{python}
data = [
    go.Surface(
        z=z_data.as_matrix()
    )
]
layout = go.Layout(
    title='Mt Bruno Elevation',
    autosize=False,
    width=500,
    height=500,
    margin=dict(
        l=65,
        r=50,
        b=65,
        t=90
    )
)
fig = go.Figure(data=data, layout=layout)
py.plot(fig, filename='elevations-3d-surface')
```

*** =sct
```{python}
test_object("fig",incorrect_msg = "Did you assign the correct values to the fig object?",do_eval=False)
success_msg("Nice! You just created a 3D plot using Plotly! Let's keeping going with the next exercises!")
```
--- type:NormalExercise lang:python xp:100 skills:2 key:f2824d0db0
## Building a choropleth map with Plotly

Choropleth maps are a create way to visualize data in different regions whether it be countys, states, courntries or more. Plotly adds additional value to this style by allowing you to interactively view data for each region by simply by hovering over the space on the map. 

We've loaded a dataset containing US Agricultural Export data by state. This is available in the console as `df`.

*** =instructions
- In the `dict()` function, fill in the blank with `'choropleth'`
- Fill in the blank in the `py.plot` function with `'d3-choropleth-map'`


*** =hint
- Simply fill in the blanks!
*** =pre_exercise_code

```{python}
import plotly.plotly as py
from plotly.graph_objs import *
py.sign_in('datacamp_python', '9IB7oEs6qib6jiwOTwRA')
import pandas as pd
df = pd.read_csv('https://raw.githubusercontent.com/plotly/datasets/master/2011_us_ag_exports.csv')
```

*** =sample_code
```{python}
for col in df.columns:
    df[col] = df[col].astype(str)

scl = [[0.0, 'rgb(242,240,247)'],[0.2, 'rgb(218,218,235)'],[0.4, 'rgb(188,189,220)'],\
            [0.6, 'rgb(158,154,200)'],[0.8, 'rgb(117,107,177)'],[1.0, 'rgb(84,39,143)']]

df['text'] = df['state'] + '<br>' +\
    'Beef '+df['beef']+' Dairy '+df['dairy']+'<br>'+\
    'Fruits '+df['total fruits']+' Veggies ' + df['total veggies']+'<br>'+\
    'Wheat '+df['wheat']+' Corn '+df['corn']

data = [ dict(
        type=___, # fill in the blank
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

fig = dict( data=data, layout=layout)
py.plot(fig, filename=___ ) # fill in the blank
```

*** =solution
```{python}
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
py.plot( fig, filename='d3-choropleth-map' )
```

*** =sct
```{python}
test_object("data",incorrect_msg = "Did you enter `type='choropleth'`?'",do_eval=False)
test_object("layout",incorrect_msg = "Did you change the layout object?",do_eval=False)
test_object("fig",incorrect_msg = "Did you change the fig object?",do_eval=False)
success_msg("Awesome! Choropleth maps with Plotly can be an extremely helpful way to present your data. Let's check out the final exercise.")
```


--- type:NormalExercise lang:python xp:100 skills:2 key:e5eb0920aa
## 2014 US City Populations

In this final exercise, we will build an interactive bubble map with Plotly showing 2014 US City Populations. The data is available in the console as `df`. 

*** =instructions
- Fill in the blank in the `dict` function with `'scattergeo'`
- Fill in the blank in the `py.plot` function with `'d3-bubble-map-populations'`

*** =hint
- Simply fill in the blanks!

*** =pre_exercise_code
```{python}
import plotly.plotly as py
import pandas as pd
py.sign_in('datacamp_python', '9IB7oEs6qib6jiwOTwRA')
df = pd.read_csv('https://raw.githubusercontent.com/plotly/datasets/master/2014_us_cities.csv')
```

*** =sample_code
```{python}
df.head()

df['text'] = df['name'] + '<br>Population ' + (df['pop']/1e6).astype(str)+' million'
limits = [(0,2),(3,10),(11,20),(21,50),(50,3000)]
colors = ["rgb(0,116,217)","rgb(255,65,54)","rgb(133,20,75)","rgb(255,133,27)","lightgrey"]
cities = []
scale = 5000

for i in range(len(limits)):
    lim = limits[i]
    df_sub = df[lim[0]:lim[1]]
    city = dict(
        type = ___, # fill in the blank
        locationmode = 'USA-states',
        lon = df_sub['lon'],
        lat = df_sub['lat'],
        text = df_sub['text'],
        marker = dict(
            size = df_sub['pop']/scale,
            color = colors[i],
            line = dict(width=0.5, color='rgb(40,40,40)'),
            sizemode = 'area'
        ),
        name = '{0} - {1}'.format(lim[0],lim[1]) )
    cities.append(city)

layout = dict(
        title = '2014 US city populations<br>(Click legend to toggle traces)',
        showlegend = True,
        geo = dict(
            scope='usa',
            projection=dict( type='albers usa' ),
            showland = True,
            landcolor = 'rgb(217, 217, 217)',
            subunitwidth=1,
            countrywidth=1,
            subunitcolor="rgb(255, 255, 255)",
            countrycolor="rgb(255, 255, 255)"
        ),
    )

fig = dict( data=cities, layout=layout )
py.plot( fig, validate=False, filename=___ ) # fill in the blank
```

*** =solution
```{python}
df.head()

df['text'] = df['name'] + '<br>Population ' + (df['pop']/1e6).astype(str)+' million'
limits = [(0,2),(3,10),(11,20),(21,50),(50,3000)]
colors = ["rgb(0,116,217)","rgb(255,65,54)","rgb(133,20,75)","rgb(255,133,27)","lightgrey"]
cities = []
scale = 5000

for i in range(len(limits)):
    lim = limits[i]
    df_sub = df[lim[0]:lim[1]]
    city = dict(
        type = 'scattergeo',
        locationmode = 'USA-states',
        lon = df_sub['lon'],
        lat = df_sub['lat'],
        text = df_sub['text'],
        marker = dict(
            size = df_sub['pop']/scale,
            color = colors[i],
            line = dict(width=0.5, color='rgb(40,40,40)'),
            sizemode = 'area'
        ),
        name = '{0} - {1}'.format(lim[0],lim[1]) )
    cities.append(city)

layout = dict(
        title = '2014 US city populations<br>(Click legend to toggle traces)',
        showlegend = True,
        geo = dict(
            scope='usa',
            projection=dict( type='albers usa' ),
            showland = True,
            landcolor = 'rgb(217, 217, 217)',
            subunitwidth=1,
            countrywidth=1,
            subunitcolor="rgb(255, 255, 255)",
            countrycolor="rgb(255, 255, 255)"
        ),
    )

fig = dict( data=cities, layout=layout )
py.plot( fig, validate=False, filename='d3-bubble-map-populations' )
```

*** =sct
```{python}
test_object("cities",incorrect_msg = "Did you enter `type='choropleth'`?'",do_eval=False)
test_object("layout",incorrect_msg = "Did you change the `layout` object?'",do_eval=False)
success_msg("Congrats! You just completed the last exercises of our Plotly tutorial. We hope we inspired you to consider Plotly for your next visualization task! You can read their documentation in more depth at https://plot.ly/python")
```
