```python
student name: chongwen sun
student number；106414816
assignment: 530-lab4
```

Question #1 - Python Imports


```python

import random
# Imports the random module


import random as rnd
# Imports the random module and names it rnd


from random import random
# Imports the random() function from the random module


from random import random as rnd
# Imports the random() function from the random module and names it rnd


import numpy.random
# Imports the random submodule of the numpy package


import numpy
# Imports the numpy package


# import X.Y.Z as T
# Imports the Z submodule of the package X.Y and names it as T


from Bio.Blast import NCBIWWW
# Imports the NCBIWWW module from the Bio.Blast package

```

Question #2 - Python Library 


```python
import json
with open("provdata.json", "r") as f:
    data = json.load(f)
items = []
for list_element in data["data"]:
    province_name = None
    population = None

    for key,value in list_element.items():
        if len(key) > 2:
            province_name = key
        else:
            population = float(value)
    items.append((province_name, population))

largest = max(items, key=lambda x: x[1])

print("Province with the largest population: ", largest[0],", Population (millions): ", largest[1])
```

    Province with the largest population:  Ontario , Population (millions):  13.6
    

Question #3 - R Library 


```python
library(jsonlite)

data <- fromJSON("provdata.json", simplifyVector = FALSE)

items <- lapply(data$data, function(obj) {
  province <- names(obj)[nchar(names(obj)) > 2]
  abbrev <- obj[[province]]
  population <- as.numeric(obj[[abbrev]])
  
  data.frame(
    province   = province,
    abbrev     = abbrev,
    population = population,
    stringsAsFactors = FALSE
  )
})

df <- do.call(rbind, items)
idx <- which.max(df$population)
cat("Province with the largest population:", df$province[idx],", Population (millions):", df$population[idx], "\n")
```

    Province with the largest population: Ontario , Population (millions): 13.6 
    

Question #4 - Debugging


# Prints the numbers from 1 to 10
for i in range(1,10)
  print(i)


```python
#correct
for i in range(1,10):
  print(i)
```

    1
    2
    3
    4
    5
    6
    7
    8
    9
    

# Allows user to enter a number until enters STOP. Multiplies number by 2. Handles incorrect user input.
num = int(input("Enter a number:"))
while num != "STOP":  
  print(num*2)  
  num = int(input("Enter a number:"))


```python
while True:
    user_input = input("Enter a number:")
    if user_input == "STOP":
        break
    try:
        num = int(user_input)
        print(num * 2)
    except ValueError:
        print("Invalid input. Please enter a number or STOP.")

```

    Enter a number: 1
    

    2
    

    Enter a number: 2
    

    4
    

    Enter a number: STOP
    

# Prints out items in a list in between 4 and 8 inclusive
data = [6, 5, 3, 4, 7, 1, 8]
for i in range(0,len(data)+1):
  if data[i] >= 4 && data[i] < 8:
    print("Data: ")
  print(data[i])


```python
# Prints out items in a list in between 4 and 8 inclusive
data = [6, 5, 3, 4, 7, 1, 8]
for i in range(0,len(data)):
  if data[i] >= 4 & data[i] < 8:
    print("Data: ")
  print(data[i])

```

    Data: 
    6
    Data: 
    5
    Data: 
    3
    Data: 
    4
    Data: 
    7
    Data: 
    1
    Data: 
    8
    

Question #5 - Getting Help in Python


```python
# Create a Python set with 5 numbers and print it
nums = {1, 2, 3, 4, 5}
print(nums)
# link is https://docs.python.org/3/library/stdtypes.html#set
```

    {1, 2, 3, 4, 5}
    

![My Image](set-screenshot.png)

Question #6 - Getting Help in R


```python
help(data.frame)
```



<table width="100%" summary="page for data.frame {base}"><tr><td>data.frame {base}</td><td style="text-align: right;">R Documentation</td></tr></table>

<h2>Data Frames</h2>

<h3>Description</h3>

<p>The function <code>data.frame()</code> creates data frames, tightly coupled
collections of variables which share many of the properties of
matrices and of lists, used as the fundamental data structure by most
of <span style="font-family: Courier New, Courier; color: #666666;"><b>R</b></span>'s modeling software.
</p>


<h3>Usage</h3>

<pre>
data.frame(..., row.names = NULL, check.rows = FALSE,
           check.names = TRUE, fix.empty.names = TRUE,
           stringsAsFactors = default.stringsAsFactors())

default.stringsAsFactors()
</pre>


<h3>Arguments</h3>

<table summary="R argblock">
<tr valign="top"><td><code>...</code></td>
<td>
<p>these arguments are of either the form <code>value</code> or
<code>tag = value</code>.  Component names are created based on the tag (if
present) or the deparsed argument itself.</p>
</td></tr>
<tr valign="top"><td><code>row.names</code></td>
<td>
<p><code>NULL</code> or a single integer or character string
specifying a column to be used as row names, or a character or
integer vector giving the row names for the data frame.</p>
</td></tr>
<tr valign="top"><td><code>check.rows</code></td>
<td>
<p>if <code>TRUE</code> then the rows are checked for
consistency of length and names.</p>
</td></tr>
<tr valign="top"><td><code>check.names</code></td>
<td>
<p>logical.  If <code>TRUE</code> then the names of the
variables in the data frame are checked to ensure that they are
syntactically valid variable names and are not duplicated.
If necessary they are adjusted (by <code>make.names</code>)
so that they are.</p>
</td></tr>
<tr valign="top"><td><code>fix.empty.names</code></td>
<td>
<p>logical indicating if arguments which are
&ldquo;unnamed&rdquo; (in the sense of not being formally called as
<code>someName = arg</code>) get an automatically constructed name or
rather name <code>""</code>.  Needs to be set to <code>FALSE</code> even when
<code>check.names</code> is false if <code>""</code> names should be kept.</p>
</td></tr>
<tr valign="top"><td><code>stringsAsFactors</code></td>
<td>
<p>logical: should character vectors be converted
to factors?  The &lsquo;factory-fresh&rsquo; default is <code>TRUE</code>, but
this can be changed by setting <code>options(stringsAsFactors
      = FALSE)</code>.</p>
</td></tr>
</table>


<h3>Details</h3>

<p>A data frame is a list of variables of the same number of rows with
unique row names, given class <code>"data.frame"</code>.  If no variables
are included, the row names determine the number of rows.
</p>
<p>The column names should be non-empty, and attempts to use empty names
will have unsupported results.  Duplicate column names are allowed,
but you need to use <code>check.names = FALSE</code> for <code>data.frame</code>
to generate such a data frame.  However, not all operations on data
frames will preserve duplicated column names: for example matrix-like
subsetting will force column names in the result to be unique.
</p>
<p><code>data.frame</code> converts each of its arguments to a data frame by
calling <code>as.data.frame(optional = TRUE)</code>.  As that is a
generic function, methods can be written to change the behaviour of
arguments according to their classes: <span style="font-family: Courier New, Courier; color: #666666;"><b>R</b></span> comes with many such methods.
Character variables passed to <code>data.frame</code> are converted to
factor columns unless protected by <code>I</code> or argument
<code>stringsAsFactors</code> is false.  If a list or data
frame or matrix is passed to <code>data.frame</code> it is as if each
component or column had been passed as a separate argument (except for
matrices protected by <code>I</code>).
</p>
<p>Objects passed to <code>data.frame</code> should have the same number of
rows, but atomic vectors (see <code>is.vector</code>), factors and
character vectors protected by <code>I</code> will be recycled a
whole number of times if necessary (including as elements of list
arguments).
</p>
<p>If row names are not supplied in the call to <code>data.frame</code>, the
row names are taken from the first component that has suitable names,
for example a named vector or a matrix with rownames or a data frame.
(If that component is subsequently recycled, the names are discarded
with a warning.)  If <code>row.names</code> was supplied as <code>NULL</code> or no
suitable component was found the row names are the integer sequence
starting at one (and such row names are considered to be
&lsquo;automatic&rsquo;, and not preserved by <code>as.matrix</code>).
</p>
<p>If row names are supplied of length one and the data frame has a
single row, the <code>row.names</code> is taken to specify the row names and
not a column (by name or number).
</p>
<p>Names are removed from vector inputs not protected by <code>I</code>.
</p>
<p><code>default.stringsAsFactors</code> is a utility that takes
<code>getOption("stringsAsFactors")</code> and ensures the result is
<code>TRUE</code> or <code>FALSE</code> (or throws an error if the value is not
<code>NULL</code>).
</p>


<h3>Value</h3>

<p>A data frame, a matrix-like structure whose columns may be of
differing types (numeric, logical, factor and character and so on).
</p>
<p>How the names of the data frame are created is complex, and the rest
of this paragraph is only the basic story.  If the arguments are all
named and simple objects (not lists, matrices of data frames) then the
argument names give the column names.  For an unnamed simple argument,
a deparsed version of the argument is used as the name (with an
enclosing <code>I(...)</code> removed).  For a named matrix/list/data frame
argument with more than one named column, the names of the columns are
the name of the argument followed by a dot and the column name inside
the argument: if the argument is unnamed, the argument's column names
are used.  For a named or unnamed matrix/list/data frame argument that
contains a single column, the column name in the result is the column
name in the argument.  Finally, the names are adjusted to be unique
and syntactically valid unless <code>check.names = FALSE</code>.
</p>


<h3>Note</h3>

<p>In versions of <span style="font-family: Courier New, Courier; color: #666666;"><b>R</b></span> prior to 2.4.0 <code>row.names</code> had to be
character: to ensure compatibility with such versions of <span style="font-family: Courier New, Courier; color: #666666;"><b>R</b></span>, supply
a character vector as the <code>row.names</code> argument.
</p>


<h3>References</h3>

<p>Chambers, J. M. (1992)
<em>Data for models.</em>
Chapter 3 of <em>Statistical Models in S</em>
eds J. M. Chambers and T. J. Hastie, Wadsworth &amp; Brooks/Cole.
</p>


<h3>See Also</h3>

<p><code>I</code>,
<code>plot.data.frame</code>,
<code>print.data.frame</code>,
<code>row.names</code>, <code>names</code> (for the column names),
<code>[.data.frame</code> for subsetting methods 
and <code>I(matrix(..))</code> examples;
<code>Math.data.frame</code> etc, about
<em>Group</em> methods for <code>data.frame</code>s;
<code>read.table</code>,
<code>make.names</code>.
</p>


<h3>Examples</h3>

<pre>
L3 &lt;- LETTERS[1:3]
fac &lt;- sample(L3, 10, replace = TRUE)
(d &lt;- data.frame(x = 1, y = 1:10, fac = fac))
## The "same" with automatic column names:
data.frame(1, 1:10, sample(L3, 10, replace = TRUE))

is.data.frame(d)

## do not convert to factor, using I() :
(dd &lt;- cbind(d, char = I(letters[1:10])))
rbind(class = sapply(dd, class), mode = sapply(dd, mode))

stopifnot(1:10 == row.names(d))  # {coercion}

(d0  &lt;- d[, FALSE])   # data frame with 0 columns and 10 rows
(d.0 &lt;- d[FALSE, ])   # &lt;0 rows&gt; data frame  (3 named cols)
(d00 &lt;- d0[FALSE, ])  # data frame with 0 columns and 0 rows
</pre>

<hr /><div style="text-align: center;">[Package <em>base</em> version 3.6.1 ]</div>



```python
screenshot
```

![My Image](data-frame-help.png)

Question #7 - Help Online

![My Image](stack-overflow-question.png)

![My Image](stack-overflow-answer.png)


```python

```
