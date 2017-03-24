---
title       : Getting a bit more fancy
description : More advanced plotting

--- type:NormalExercise lang:python xp:100 skills:2 key:dea4219835
## Boxplots with Plotly

In this exercise you will create a boxplot! Actually, you will create a couple different versions using the same data, `boxplot_data` which is preloaded in the console. We will create three versions of the boxplot: one with all the points, one with only the whiskers, and one with whiskers and outliers. For the exercise, we will create traces using `go.Box()`. We already created `trace0` which is available in the console. Take a look at the structure and then follow the instructions to create `trace1` and `trace2`.


*** =instructions
- Create `trace1` where: 
    -  `y = boxplot_data`
    - `name = "Only Whiskers"`
    - `boxpoints = False`
    - `marker = dict(color = 'rgb(9,56,125)')`
    - `line = dict(color = 'rgb(9,56,125)')`
- Create `trace2` where: 
    - `y = boxplot_data`
    - `name = "Whiskers and Outliers"`
    - `boxpoints = "outliers"`
    - `marker = dict(color = 'rgb(107,174,214)')`
    - `line = dict(color = 'rgb(107,174,214)')`
- Combine the trace objects to create the `data` object by filling in the blanks
- Complete the `go.Figure()` function to create the `fig` object

*** =hint
- Look at the `trace0` in the IPython Shell to view it's structure.
*** =pre_exercise_code
```{python}
import plotly.plotly as py
import plotly.graph_objs as go
py.sign_in('datacamp_python', '9IB7oEs6qib6jiwOTwRA')
boxplot_data = [0.75, 5.25, 5.5, 6, 6.2, 6.6, 6.80, 7.0, 7.2, 7.5, 7.5, 7.75, 8.15, 8.15, 8.65, 8.93, 9.2, 9.5, 10, 10.25, 11.5, 12, 16, 20.90, 22.3, 23.25]

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

```

*** =sample_code
```{python}
# Create traces


# Combine trace0, trace1, trace2
data = [___,___,___]

# Create the layout
layout = go.Layout(
    title = "Box Plot Styling Outliers"
)

# Plot the figure
fig = go.Figure(data=___,layout=___)
py.plot(fig, filename = "Box Plot Styling Outliers")
```

*** =solution
```{python}
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
    name = "Whiskers and Outliers",
    boxpoints = 'outliers',
    marker = dict(
        color = 'rgb(107,174,214)'),
    line = dict(
        color = 'rgb(107,174,214)')
)

# Combine data
data = [trace0,trace1,trace2]

# Create the layout
layout = go.Layout(
    title = "Box Plot Styling Outliers"
)

# Plot the figure
fig = go.Figure(data=data,layout=layout)
py.plot(fig, filename = "Box Plot Styling Outliers")

```

*** =sct
```{python}
test_object("trace1",incorrect_msg = "Did you assign the correct value to the boxpoints argument?",do_eval=False)
test_object("trace2",incorrect_msg = "Did you assign the correct value to the boxpoints argument?",do_eval=False)
test_object("data",incorrect_msg = "Did you assign the correct values to the data object?",do_eval=False)
success_msg("Super! Now you're getting the hang out it!")
```


--- type:NormalExercise lang:python xp:100 skills:2 key:c6553f5c85
## Mapping Mt. Bruno

Next, we're going to show you how you can even visualize surface data with Plotly! The data for Mt. Bruno is preloaded in the console as `z_data`. 
In this exercise you will use the `go.Surface()` to create a trace like the previous. This time, you only need to set one argument, `z`. The `layout` object has already been created and is available in the console for you.

*** =instructions
- Create an object `data` where the `z` arugument is equal to `z_data` as a matrix (don't forget the bracket notation!)

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
```

*** =sample_code
```{python}
# Create the data object

# Fill in the blanks and plot the figure
fig = go.Figure(data=___, layout=___)
py.plot(fig, filename='elevations-3d-surface')
```

*** =solution
```{python}
# Create the 
data = [
    go.Surface(
        z=z_data.as_matrix()
    )
]

# Fill in the blanks and plot the figure
fig = go.Figure(data=data, layout=layout)
py.plot(fig, filename='elevations-3d-surface')
```

*** =sct
```{python}
test_object("data",incorrect_msg = "Did you remember to add the bracket notation around your `go.Surface()` function? ",do_eval=False)
test_object("fig",incorrect_msg = "Did you assign the correct values to the fig object?",do_eval=False)
success_msg("Nice! You just created a 3D plot using Plotly! Let's keeping going with the next exercises!")
```
--- type:NormalExercise lang:python xp:100 skills:2 key:f2824d0db0
## Building a choropleth map with Plotly

Choropleth maps are a create way to visualize data in different regions whether it be countys, states, courntries or more. Plotly adds additional value to this style by allowing you to interactively view data for each region by simply by hovering over the space on the map. 

We've loaded a dataset containing US Agricultural Export data by state. This is available in the console as `df`. We also created the `layout` object to help get you started. You need to format the data for the Choropleth map and execute the code!

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
for col in df.columns:
    df[col] = df[col].astype(str)

scl = [[0.0, 'rgb(242,240,247)'],[0.2, 'rgb(218,218,235)'],[0.4, 'rgb(188,189,220)'],\
            [0.6, 'rgb(158,154,200)'],[0.8, 'rgb(117,107,177)'],[1.0, 'rgb(84,39,143)']]

df['text'] = df['state'] + '<br>' +\
    'Beef '+df['beef']+' Dairy '+df['dairy']+'<br>'+\
    'Fruits '+df['total fruits']+' Veggies ' + df['total veggies']+'<br>'+\
    'Wheat '+df['wheat']+' Corn '+df['corn']
layout = dict(
        title = '2011 US Agriculture Exports by State<br>(Hover for breakdown)',
        geo = dict(
            scope='usa',
            projection=dict( type='albers usa' ),
            showlakes = True,
            lakecolor = 'rgb(255, 255, 255)'),
             )
```

*** =sample_code
```{python}
# Create the data object
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

# Fill in the blank and plot the figure!
fig = dict( data=data, layout=layout)
py.plot(fig, filename=___ ) 
```

*** =solution
```{python}
# Create the data object
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

# Plot the figure!
fig = dict( data=data, layout=layout )
py.plot( fig, filename='d3-choropleth-map')
```

*** =sct
```{python}
test_object("data",incorrect_msg = "Did you enter `type='choropleth'`?'",do_eval=False)
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
