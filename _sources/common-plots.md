---
jupytext:
  cell_metadata_filter: -all
  formats: md:myst
  text_representation:
    extension: .md
    format_name: myst
    format_version: '0.8'
    jupytext_version: 1.5.0
kernelspec:
  display_name: 'Python 3.8.6 64-bit (''codeforecon'': conda)'
  language: python
  name: codeforecon
---

# Common plots

## Introduction

In this chapter, we'll look at some of the most common plots that you might want to make--and how to create them using the most popular libraries. If you need an introduction to these libraries, see the previous chapter.

Throughout, we'll assume that the data are in a tidy format (one row per observation, one variable per column). First, though, let's import the libraries we'll need.

```{code-cell} ipython3
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
from plotnine import *
import altair as alt
from vega_datasets import data
```

```{code-cell} ipython3
:tags: ["remove-cell"]

# Set seed for reproducibility
np.random.seed(10)
# Set max rows displayed for readability
pd.set_option('display.max_rows', 6)
```

## Scatter plot

In this example, we see a simple scatter plot with categories using the cars data:

```{code-cell} ipython3
cars = data.cars()
cars.head()
```

```{code-cell} ipython3
:tags: ["remove-cell"]
from myst_nb import glue

# Matplotlib
colormap = plt.cm.Set1
colorst = [colormap(i) for i in
           np.linspace(0, 0.9, len(cars['Origin'].unique()))]
fig, ax = plt.subplots()
for i, origin in enumerate(cars['Origin'].unique()):
    cars_sub = cars[cars['Origin'] == origin]
    ax.scatter(cars_sub['Horsepower'],
               cars_sub['Miles_per_Gallon'],
               color=colorst[i],
               label=origin,
               alpha=0.6,
               edgecolor='k')
ax.set_ylabel('Miles per Gallon')
ax.set_xlabel('Horsepower')
ax.legend()
plt.show()

glue("m_scatter", fig, display=False)
```


````{panels}
```{code-cell} ipython3
colormap = plt.cm.Set1
colorst = [colormap(i) for i in
           np.linspace(0, 0.9, len(cars['Origin'].unique()))]
fig, ax = plt.subplots()
for i, origin in enumerate(cars['Origin'].unique()):
    cars_sub = cars[cars['Origin'] == origin]
    ax.scatter(cars_sub['Horsepower'],
               cars_sub['Miles_per_Gallon'],
               color=colorst[i],
               label=origin,
               alpha=0.6,
               edgecolor='k')
ax.set_ylabel('Miles per Gallon')
ax.set_xlabel('Horsepower')
ax.legend()
plt.show()
```
---
```{glue:} m_scatter
```
````

````{panel} Matplotlib
```{code-cell} ipython3
# Matplotlib
colormap = plt.cm.Set1
colorst = [colormap(i) for i in
           np.linspace(0, 0.9, len(cars['Origin'].unique()))]
fig, ax = plt.subplots()
for i, origin in enumerate(cars['Origin'].unique()):
    cars_sub = cars[cars['Origin'] == origin]
    ax.scatter(cars_sub['Horsepower'],
               cars_sub['Miles_per_Gallon'],
               color=colorst[i],
               label=origin,
               alpha=0.6,
               edgecolor='k')
ax.set_ylabel('Miles per Gallon')
ax.set_xlabel('Horsepower')
ax.legend()
plt.show()
```
````

bah bad

`````{tabbed} Matplotlib

````{panels}

```{code-block} python
colormap = plt.cm.Set1
colorst = [colormap(i) for i in
           np.linspace(0, 0.9, len(cars['Origin'].unique()))]
fig, ax = plt.subplots()
for i, origin in enumerate(cars['Origin'].unique()):
    cars_sub = cars[cars['Origin'] == origin]
    ax.scatter(cars_sub['Horsepower'],
               cars_sub['Miles_per_Gallon'],
               color=colorst[i],
               label=origin,
               alpha=0.6,
               edgecolor='k')
ax.set_ylabel('Miles per Gallon')
ax.set_xlabel('Horsepower')
ax.legend()
plt.show()
```
---
```{glue:} m_scatter
```

````

`````

````{tabbed} seaborn

```{code-block} python
df.mean()
```
some text
````

````{tabbed} plotnine

```{panels}

Content of the left panel.
---
right panel

```

````
