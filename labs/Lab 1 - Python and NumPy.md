---
jupyter:
  jupytext:
    formats: ipynb,md
    text_representation:
      extension: .md
      format_name: markdown
      format_version: '1.1'
      jupytext_version: 1.2.4
  kernelspec:
    display_name: Python 3
    language: python
    name: python3
---

# Name
**Ethan Goldfarb**


**Instructions:** This is an individual assignment, but you may discuss your code with your neighbors.


# Python and NumPy

While other IDEs exist for Python development and for data science related activities, one of the most popular environments is Jupyter Notebooks.

This lab is not intended to teach you everything you will use in this course. Instead, it is designed to give you exposure to some critical components from NumPy that we will rely upon routinely.

## Exercise 0
Please read and reference the following as your progress through this course. 

* [What is the Jupyter Notebook?](https://nbviewer.jupyter.org/github/jupyter/notebook/blob/master/docs/source/examples/Notebook/What%20is%20the%20Jupyter%20Notebook.ipynb#)
* [Notebook Tutorial](https://www.datacamp.com/community/tutorials/tutorial-jupyter-notebook)
* [Notebook Basics](https://nbviewer.jupyter.org/github/jupyter/notebook/blob/master/docs/source/examples/Notebook/Notebook%20Basics.ipynb)

**In the space provided below, what are three things that still remain unclear or need further explanation?**


**YOUR ANSWER HERE**


## Exercises 1-7
For the following exercises please read the Python appendix in the Marsland textbook and answer problems A.1-A.7 in the space provided below.


## Exercise 1

```python
import numpy as np
a = np.ones((6,4)) * 2
# note: there is a fill and fold command
# kwargs: dtype=int, etc.
print(a)
```

## Exercise 2

```python
b = np.ones((6,4)) + np.vstack([(np.eye((4))*2),[0,0,0,0],[0,0,0,0]])
# note: fold diagonal, fill diagonal, also b[range(n),range(n)] = val
#
print(b)
```

## Exercise 3

```python
# No, not standard matrix multiplication.
# One may do pairwise multiplication, but not matrix multiplication. 
# Simply put, the dimensions are not proper for matrix multiplication
```

## Exercise 4

```python
atb = np.dot(a.transpose(),b)
bta = np.dot(a,b.transpose())
print(atb)
print(bta)
# these results are different sizes, as multiplication of a 4 x 6 matrix with a 6 x 4 
#will result in  4 x 4 matrix, and in a 6x6 for 6x4 x 4x6
```

## Exercise 5

```python
def p():
    print("I think it works ", end='lol')
p()
```

## Exercise 6

```python
def p2():
    r = np.reshape(np.random.rand(24), (4,-1))

    print(r)
    print(np.sum(r))
    print(np.sum(r)/24)
    print(np.min(r))
    print(np.max(r))
p2()
```

## Exercise 7

```python
def p3():
    a = np.reshape(np.random.randint(0,3,24), (4,-1))
    print(a)
    count = 0
    for x in range(len(a)):
        for y in range(len(a[0])):
            if a[x][y] == 1:
                count += 1
    print(count)
    print(np.where(a == 1, a, 0))
    print(np.sum(np.where(a == 1, a, 0)))

    #np.info(np.where)
p3()
```

## Exercise 8
Repeat exercise A.1 from Marsland, but create a Pandas DataFrame instead of a NumPy array.

```python
import pandas as pd
pdf = pd.DataFrame(np.ones((6,4)) * 2, index =list("ABCDEF"), columns=list("ABCD"))
print(pdf)
```

## Exercise 9
Repeat exercise A.2 using a DataFrame instead.

```python
pdf2 = pd.DataFrame(np.vstack([np.eye(4),[0,0,0,0],[0,0,0,0]]))
print(pdf2)
# b.iloc[range(n),range(n)] = val
# index location of column
```

## Exercise 10
Repeat exercise A.3 using DataFrames instead.

```python
pdf3 = pd.DataFrame(pdf.values * pdf2.values)
print(pdf3)
#dot product (matrix mult) will not work for aforementioned reasons in E3
```

## Exercise 11
Repeat exercise A.7 using a dataframe.

```python
r = pd.DataFrame(np.random.randint(0,3,(5,5)))
print(r)
print(r.where(r == 1, 0))
print(r.where(r == 1, 0).values.sum())
```

## Exercises 12-14
Now let's look at a real dataset, and talk about ``.loc``. For this exercise, we will use the popular Titanic dataset from Kaggle. Here is some sample code to read it into a dataframe.

```python
titanic_df = pd.read_csv(
    "https://raw.githubusercontent.com/dlsun/data-science-book/master/data/titanic.csv"
)
titanic_df
```

Notice how we have nice headers and mixed datatypes? That is one of the reasons we might use Pandas. Please refresh your memory by looking at the 10 minutes to Pandas again, but then answer the following.


## Exercise 12
How do you select the ``name`` column without using .iloc?

```python
## titanic_df['name']
```

## Exercise 13
After setting the index to ``sex``, how do you select all passengers that are ``female``? And how many female passengers are there?

```python
## loc is value/label based indexing
titanic_df.set_index('sex',inplace=True)
titanic_df.loc['female']
```

## Exercise 14
How do you reset the index?

```python
titanic_df.reset_index(inplace=True)
```

```python

```
