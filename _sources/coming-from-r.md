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

# Coming from R

If you're coming from R, then you're probably already somewhat familiar with integrated developer environments and coding, and most of what you'll want to know about are the differences in tools.

There are, however, some fundamental differences between the two languages. The biggest difference between Python and R is that Python is a general purpose programming language, while R began as a statistical language. But you won't notice that much difference unless you're doing something on a production scale or writing a package. Despite being a general language, Python has really fantastic class support for statistics so you needn't worry about losing any functionality relative to R and, in the special case where you need that one stats package that's only written in R, you can use R directly from Python. A second difference is that Python is more object-oriented while R is more functional. These are two different programming paradigms. Actually, both languages do a bit of both and you're unlikely to notice any difference unless and until you're writing your own packages (and even then quite complicated packages!). Actually, the biggest practical difference I have found is that Python has more of a flavour of the bazaar--lots of people, and you can find everything under the Sun, but it can be a *little bit* chaotic--while R has the feel of a curated garden--there is a chief gardener (RStudio) tending a smaller number of more beautiful things, but the garden is quieter and has boundaries.

Personally, I tend to use Python because I find that its commands are readable and often in clear, plain English, it has a huge ecosystem of packages and users, it scales well to bigger problems, and it is also valuable outside of economics and data science. Sometimes people wonder whether they should learn Python or R. For economics, you really can learn either; they are similar enough to be useful for each other. Python has more generalisability and a significantly larger number of people using it. R has more specificity; it is dominant in some sub-fields. But you can very happily use either to get along in economics. Indeed, almost all of the code examples in this book could also be done in R.

A gotcha to be aware of: R is among the small number of languages where arrays etc. are indexed from 1. Like C++, Python is numbered from zero, with, eg, `a[0]` as the first element.

## Tools similar to those found in an R workflow

In R, the main tools that people use are those provided by RStudio, particularly **dplyr** for data analysis and **ggplot2** for plotting. There are Python equivalents that have very similar syntax to these that you can use to help you to become productive quickly in Python--though these libraries are not so popular in Python. So here are the Python equivalents to the R libraries that you might have seen already:

- **dplyr**: the most similar Python version of this library is [**plydata**](https://plydata.readthedocs.io/en/stable/index.html), while the most popular Python library that performs similar functions is [**pandas**](https://pandas.pydata.org/pandas-docs/stable/index.html). I tend to recommend people learn **pandas** for data analysis in Python because it is comprehensive and ubiquitious. It also has unrivaled documentation.

- **ggplot2**: the most similar Python version of this library is [**plotnine**](https://plotnine.readthedocs.io/en/stable/index.html), while the most popular Python library that performs similar functions is a combination of [**matplolib**](https://matplotlib.org/) and [**seaborn**](https://seaborn.pydata.org/), which builds on **matplotlib**. I think either those two together or **plotnine** are good choices, though **plotnine**'s documentation is not (yet) as good and it's certainly not as widely used. (It's gaining popularity quickly though.)

## R <==> Python

Here are some tables of translations between base R and Python code.

### General

| R      | Python |
| ----------- | ----------- |
| <code> new_function <- function(a, b=5) { <br>return (a+b) <br>} </code>  | <code> def new_function(a, b=5): <br> &nbsp;&nbsp;&nbsp;&nbsp;return a+b </code> |
| <code> for (val in c(1,3,5)){ <br>  print(val) <br> } </code>  | <code> for val in [1,3,5]:<br>&nbsp;&nbsp;&nbsp;&nbsp;print(val)</code>   |
| `a <- c(1,3,5,7)`   | `a = [1,3,5,7]`  |
| `a <- c(3:9)`   | `a = list(range(3,9))` |
| `class(a)`   | `type(a)`    |
| `a <- 5`   | `a = 5` |
| `a^2` | `a**2` |
| `a%%5` | `a%5`|
| `a & b` | `a and b` |
| `a | b` | `a or b` |
| `rev(a)` | `a[::-1]` |
| `a %*% b` | `a @ b` |

### Dataframes

Assuming the use of **pandas** in Python.

| R      | Python |
| ----------- | ----------- |
| `head(df)` | `df.head()` |
| `tail(df)` | `df.tail()` |
| `nrow(df)`   | `df.shape[0]` or `len(df)` |
| `ncol(df)`   | `df.shape[1]` or `len(df.columns)` |
| None  | `df.info()`    |
| `summary(df)`   | `df.describe()` (somewhat similar) |

More here: https://towardsdatascience.com/cheat-sheet-for-python-dataframe-r-dataframe-syntax-conversions-450f656b44ca

### Object types

| R      | Python |
| ----------- | ----------- |
| Single-element vector | Scalar |
| Multi-element vector | List |
| List of multiple types | Tuple |
| Named list | Dict |
| Matrix/Array | numpy ndarray |
| `NULL`, `TRUE`, `FALSE` | `None`, `True`, `False` |
