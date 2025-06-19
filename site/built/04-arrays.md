---
title: "Introduction to Arrays"
teaching: 10
exercises: 2
---


[**Download Chapter PDF (.pdf)**](https://drive.usercontent.google.com/u/1/uc?id=1-VvkJhmjX_LquWR92pioBOhvzTVG6hkc&export=download)

[**Download Chapter notebook (.ipynb)**](https://drive.usercontent.google.com/u/1/uc?id=1s-msBWdPEKJSepD-dYsRDXXsMmpL2X8v&export=download)

[<span style="color: rgb(255, 0, 0);">**Lesson Feedback Survey**</span>](https://docs.google.com/forms/d/e/1FAIpQLSdr0capF7jloJhPH3Pki1B3LZoKOG16poOpuVJ7SL2LkwLHQA/viewform?pli=1)



:::::::::::::::::::::::::::::::::::::: questions

- What are the different types of arrays?
- How is data stored and retrieved from an array?
- What are nested arrays?
- What are tuples?

::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::: objectives
- Understanding the difference between lists and tuples.
- Understanding operations on arrays.
- Storing multidimensional data.
- Understanding the concepts of mutability and immutability.
::::::::::::::::::::::::::::::::::::::::::::::::

<br>
<p align = "center">
<iframe width="560" height="315" src="https://www.youtube.com/embed/RlhGPZv8fZI" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
</p>
<br>
<p align = "center">
<iframe width="560" height="315" src="https://www.youtube.com/embed/KiMQiN4CN8s" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
</p>
<br>
<p align = "center">
<iframe width="560" height="315" src="https://www.youtube.com/embed/id72qTBmCEY" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
</p>
<br>

:::::::::::::::::: prereq
- [Variables and Types](02-input_output.Rmd#varTypes)
- [Logical Operations](02-input_output.Rmd#subsec:logicalOperatons)
- [Conditional Statements](03-conditional_statements.Rmd)


::::::::::::::::::

<p style='text-align: justify;'>
So far, we have been using variables to store individual values. In some circumstances, we may need to access multiple values in order to perform operations. On such occasions, defining a variable for every single value can become very tedious. To address this, we use **arrays**.
</p>

<p style='text-align: justify;'>
Arrays are variables that hold any number of values. Python provides three types of built-in arrays. These are: ```list```, ```tuple```, and ```set```. There are several common features among all arrays in Python; however, each type of array enjoys its own range of unique features that facilitate specific operations.
</p>

:::::::::::::::::::::::::::::::::::: callout
## NumPy 

Additionally, Python has a widely used package called **NumPy**, which provides its own array type known as the **NumPy array**. NumPy arrays are especially useful for mathematical operations, as they support fast, element-wise computations and are optimised for performance. Unlike regular Python arrays, NumPy arrays store data more efficiently and in a fixed type, making them well suited to numerical applications. We will explore their differences from built-in lists later in the Data Handling modules of the L2D course, but they’re worth mentioning now due to their importance in scientific computing.

::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::: callout
## Remember
Each item inside an array may be referred to as an *item* or a *member* of that array.

::::::::::::::::::::::::::::::::::::

## Lists
[**Resource for Lists**](https://docs.python.org/3/tutorial/datastructures.html\#more-on-lists)

<p style='text-align: justify;'>
Lists are the most frequently-used type of arrays in Python. It is therefore important to understand how they work, and how can we use them, and the features they offer, to our advantage.
</p>

<p style='text-align: justify;'>
The easiest way to imagine how a ```list``` works, is to think of it as a table that can have any number of rows. This is akin to a spreadsheet with one column. For instance, suppose we have a table with four rows in a spreadsheet application, as follows:
</p>

![](fig/spreadsheet.png)

The number of rows or **items** in an array determines its *length*. The above table has four rows; therefore it is said to have a *length* of 4.


### **Implementation**

:::::::::::::::::::::::::::::::::::: callout
## Remember
In order to implement a ```list``` in Python, we place values within a pair of square brackets, and separate them from one another using commas, as follows:  `list = [1,2,3]`

::::::::::::::::::::::::::::::::::::


``` python
table = [5, 21, 5, -1]

print(table)
```

``` output
[5, 21, 5, -1]
```



``` python
print(type(table))
```

``` output
<class 'list'>
```

::::::::::::::::::::::::::::::: challenge

## Practice Exercise 1 {#diy:array:list:fibonacci}

Implement a ```list``` array called <span style="color: rgb(32, 121, 77);">fibonacci</span>, whose members represent the first 8 numbers of the [Fibonacci sequence](https://en.wikipedia.org/wiki/Fibonacci_number) as follows:

| FIBONACCI NUMBERS (FIRST 8) |   |   |   |   |   |    |    |
|:---------------------------:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
| 1 | 1 | 2 | 3 | 5 | 8 | 13 | 21 |


::::::::::::::::: solution

## ANSWER


``` python
fibonacci = [1, 1, 2, 3, 5, 8, 13, 21]
```

:::::::::::::::::

:::::::::::::::::::::::::::::::


### **Indexing** {#sec:list:indexing}

In a list, an index is an integer (whole number) that corresponds to a specific item in that array.

<p style='text-align: justify;'>
You can think of an index as a *unique reference* or *key* that corresponds to a specific row in a table. We don't always write the row number when we create a table. However, we always know that the third row of a table refers to us starting from the first row (row \#1), counting three rows down and there we find the third row.
</p>

<p style='text-align: justify;'>
Python, however, uses what we term **zero-based** indexing. We don't count the first row as row \#1; instead, we consider it to be row \#0. As a consequence of starting from \#0, we count rows in our table down to row \#2 instead of \#3 to find the third row. So our table may,essentially, be visualised as follows:
</p>

![](fig/indexing_diagram.png)

::::::::::::::::::::::::::::::::::: callout
## Remember
Python uses **zero-based** indexing system. This means that the first row of an array, regardless of its type, is always referred to with index \#0.

:::::::::::::::::::::::::::::::::::

With that in mind, we can use the index for each item in the list, in order to retrieve it from a ```list```.

Given the following ```list``` of four members stored in a variable called <span style="color: rgb(32, 121, 77);">table</span>:

```
table = [5, 21, 5, -1]
```

we can visualise the referencing protocol in Python as follows:
![](fig/indexing_diagram2.png)
<p style='text-align: justify;'>
As illustrated in this figure; in order to retrieve a member of an array through its index, we write the name of the variable immediately followed by the index value inside a pair of square brackets --- *e.g.* <span style="color: rgb(32, 121, 77);">table[2]</span>. Note, you may have noticed our interchangeable use of the terms ‘list’ and ‘array’. That is because a list, in Python, can be considered as a type of dynamic array (they can increase or decrease in size, as required).
</p>


``` python
print(table[2])
```

``` output
5
```


``` python
print(table[0])
```

``` output
5
```


``` python
item = table[3]

print(item)
```

``` output
-1
```

::::::::::::::::::::::::::::::: challenge

## Practice Exercise 2

Retrieve and display the 5^th^ Fibonacci number from the ```list``` you created in the previous [Practice Exercise 1](#diy:array:list:fibonacci).


::::::::::::::::: solution

## ANSWER


``` python
print(fibonacci[4])
```

``` output
5
```
:::::::::::::::::

:::::::::::::::::::::::::::::::

<p style='text-align: justify;'>
It is sometimes more convenient to index an array, backwards --- that is, to reference the members from the bottom, or end, of the array, first. This is termed **negative indexing**, and is particularly useful when we are dealing with lengthy arrays. The indexing system in Python support both positive and negative indexing systems.
</p>

The table above therefore may also be represented, as follows:

![](fig/indexing_diagram3.png)

:::::::::::::::::::::::::::::::::::: callout
## Remember
Unlike the normal indexing system, which starts from \#0, negative indexes start from \#-1. This serves to definitely highlight which indexing system is being used.

::::::::::::::::::::::::::::::::::::

If the index is a negative number, the indices are counted from the end of the ```list```. We can implement negative indices in the same way as positive indices:


``` python
print(table[-1])
```

``` output
-1
```


``` python
print(table[-2])
```

``` output
5
```


``` python
print(table[-3])
```

``` output
21
```


We know that in <span style="color: rgb(32, 121, 77);">table</span>, index \#-3 refers the same value as index \#1. So let us go ahead and test this:


``` python
equivalence = table[-3] == table[1]

print(equivalence)
```

``` output
True
```


If the index requested is larger than the length of the ```list``` minus one, an ```IndexError``` will be raised:


``` python
print(table[4])
```

``` output
IndexError: list index out of range
```

:::::::::::::::::::::::::::::::::::: callout
## Remember
The values stored in a ```list``` may be referred to as the **members** of that ```list```.

::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::: challenge

## Practice Exercise 3

Retrieve and display the *last* Fibonacci number from the ```list``` you created in [Practice Exercise 1](#diy:array:list:fibonacci).


::::::::::::::::: solution

## ANSWER

``` python
print(fibonacci[-1])
```

``` output
21
```

:::::::::::::::::

:::::::::::::::::::::::::::::::



### **Slicing** {#sec:list:slicing}

It is also possible that you may wish to retrieve more than one consecutive value from a ```list``` at a time. This process is is termed **slicing**, and may be visualised, as follows:

![](fig/slicing_diagram.png)

:::::::::::::::::::::::::::::::::::: callout
## Remember
Python is a **end-inclusive** language. This means that in <span style="color: rgb(32, 121, 77);">table[a:b]</span>, a *slice* includes all the values from, and including index <span style="color: rgb(32, 121, 77);">a</span> right down to, but *excluding*, index <span style="color: rgb(32, 121, 77);">b</span>.

::::::::::::::::::::::::::::::::::::

Given a ```list``` representing the above table:

```
table = [5, 21, 5, -1]
```

we may retrieve a slice of <span style="color: rgb(32, 121, 77);">table</span>, as follows:


``` python
my_slice = table[1:3]

print(my_slice)
```

``` output
[21, 5]
```

```{}
print(table[0:2])
```

If the first index of a slice is \#0, the slice may also be written as:


``` python
print(table[:2])
```

``` output
[5, 21]
```

Negative slicing is also possible:


``` python
# Retrieves every item from the first member down
# to, but excluding the last one:
print(table[:-1])
```

``` output
[5, 21, 5]
```


``` python
print(table[1:-2])
```

``` output
[21]
```

If the second index of a slice represents the last index of a ```list```, it would be written as:

``` python
print(table[2:])
```

``` output
[5, -1]
```


``` python
print(table[-3:])
```

``` output
[21, 5, -1]
```

We may also store indices and slices in variables:


``` python
start, end = 1, 3
new_table = table[start:end]

print(new_table)
```

``` output
[21, 5]
```


The <kbd>slice()</kbd> function may also be used to create a slice variable:

``` python
my_slice = slice(1, 3)

print(table[my_slice])
```

``` output
[21, 5]
```


:::::::::::::::::::::::::::::::::::: callout
## Note
The `slice()` function is mainly used in more advanced cases, such as when you need to define slices dynamically or reuse a slice across multiple operations.

::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::: challenge

## Practice Exercise 4
<p style='text-align: justify;'>
Retrieve and display a slice of Fibonacci numbers from the ```list``` you created in [Practice Exercise 1](#diy:array:list:fibonacci) that includes all the members from the second number onwards --- *i.e*.  the slice must not include the first value in the ```list```.
</p>

::::::::::::::::: solution

## ANSWER


``` python
print(fibonacci[1:])
```

``` output
[1, 2, 3, 5, 8, 13, 21]
```

:::::::::::::::::

:::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::: callout
## Note
<p style='text-align: justify;'>
**Methods** are features of [Object-Oriented Programming (OOP)](https://en.wikipedia.org/wiki/Object-oriented_programming) - a programming paradigm that we do not discuss in the context of this course. You can think of a *method* as a *function* that is associated with a specific *type*. The job of a *method* is to provide a certain functionality unique to the *type* it is associated with. 
</p>

::::::::::::::::::::::::::::::::::::


### **From value to index**

Given a ```list``` called <span style="color: rgb(32, 121, 77);">table</span> as:


``` python
table = [5, 21, 5, -1]
```


We can also determine the index of a specific value. To do so, we use the <kbd>.index()</kbd> *method*. In this case, ```.index()``` is a *method* of type ```list``` that, given a value, finds and produces its index from the ```list```.


``` python
print(table.index(21))
```

``` output
1
```


``` python
last_item = table.index(-1)

print(last_item)
```

``` output
3
```


If a value is repeated more than once in the  ```list```, the index corresponding to the *first* instance of that value is returned:

``` python
print(table.index(5))
```

``` output
0
```

If a value does *not* exist in the ```list```, using <kbd>.index()</kbd> will raise a ```ValueError```:


``` python
print(table.index(9))
```

``` output
ValueError: 9 is not in list
```


::::::::::::::::::::::::::::::: challenge

## Practice Exercise 5

Find and display the index of these values from the ```list``` of Fibonacci numbers that you created in [Practice Exercise 1](#diy:array:list:fibonacci):

* 1
* 5
* 21


::::::::::::::::: solution

## ANSWER


``` python
print(fibonacci.index(1))

print(fibonacci.index(5))

print(fibonacci.index(21))
```

``` output
0
4
7
```

:::::::::::::::::

:::::::::::::::::::::::::::::::

### **Mutability** {#subsubsec:list:mutability}
<p style='text-align: justify;'>
Mutability is a term that we use to refer to a structure’s capability of being change, once it is created. Arrays of type ```list``` are _modifiable_. That is, we can add new values, change the existing ones or remove them from the array, altogether. Variable types that allow their contents to be modified are referred to as *mutable types* in programming.
</p>

#### **Addition of new members**

Given a ```list``` called <span style="color: rgb(32, 121, 77);">table</span>, we can add new values to it using <kbd>.append()</kbd>:

\begin{lstlisting}
	table = [5, 21, 5, -1]
\end{lstlisting}



``` python
table.append(29)

print(table)
```

``` output
[5, 21, 5, -1, 29]
```


``` python
table.append('a text')

print(table)
```

``` output
[5, 21, 5, -1, 29, 'a text']
```

:::::::::::::::::::::::::::::::::::: callout
## Note
Up until the last block of code we have been working with lists of the same data type: namely integers (whole numbers). However, the last code block introduced data of type **string** into the list. The ability to compute and use mixed data types is a feature relatively unique to native Python arrays, and is a feature that is not found in other languages, nor even in NumPy arrays, when these are used in Python.

::::::::::::::::::::::::::::::::::::

<p style='text-align: justify;'>
Sometimes, it may be necessary to insert a value at a specific position or index in a ```list```. To do so, we may use <kbd>.insert()</kbd>, which takes two input arguments; the first representing the index, and the second the value to be inserted:
</p>


``` python
table.insert(3, 56)

print(table)
```

``` output
[5, 21, 5, 56, -1, 29, 'a text']
```

::::::::::::::::::::::::::::::: challenge

## Practice Exercise 6

Given <span style="color: rgb(32, 121, 77);">fibonacci</span> - the ```list``` representing the first 8 numbers in the Fibonacci sequence that you created in [Practice Exercise 1](#diy:array:list:fibonacci):

1. The 10^th^ number in the Fibonacci sequence is 55. Add this value to <span style="color: rgb(32, 121, 77);">fibonacci</span>.

2. Now that you have added 55 to the ```list```, it no longer provides a correct representation of the Fibonacci sequence. Alter <span style="color: rgb(32, 121, 77);">fibonacci</span> and insert the missing number such that the list correctly represents the first 10 numbers in the Fibonacci sequence, as follows:



| FIBONACCI NUMBERS (FIRST 8) |   |   |   |   |   |    |    |   |   |
|:---------------------------:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
| 1 | 1 | 2 | 3 | 5 | 8 | 13 | 21 | 34 | 55 |

::::::::::::::::: solution

## Q1

``` python
fibonacci.append(55)
```

:::::::::::::::::

::::::::::::::::: solution

## Q2

``` python
fibonacci.insert(8, 34)
```

:::::::::::::::::

:::::::::::::::::::::::::::::::

#### **Modification of members**

Given a ```list``` as:


``` python
table = [5, 21, 5, 56, -1, 29, 'a text']
```

we can also modify the exiting value or values inside a ```list```. This process is sometimes referred to as *item assignment*:


``` python
# Changing the value of the 2nd member.

table[1] = 174

print(table)
```

``` output
[5, 174, 5, 56, -1, 29, 'a text']
```


``` python
table[-4] = 19

print(table)
```

``` output
[5, 174, 5, 19, -1, 29, 'a text']
```

<p style='text-align: justify;'>
It is also possible to perform *item assignment* over a *slice* containing any number of values. Note that when modifying a slice, the replacement values must be _the same length_ as the slice we are trying to replace:
</p>


``` python
print('Before:', table)

replacement = [-38, 0]

print('Replacement length:', len(replacement))
print('Slice length:', len(table[2:4]))

# The replacement process:
table[2:4] = replacement

print('After:', table)
```

``` output
Before: [5, 174, 5, 19, -1, 29, 'a text']
Replacement length: 2
Slice length: 2
After: [5, 174, -38, 0, -1, 29, 'a text']
```


``` python
# Using the existing value to determine the new value:
table[2] = table[2] + 50

print(table)
```

``` output
[5, 174, 12, 0, -1, 29, 'a text']
```


::::::::::::::::::::::::::::::: challenge

## Practice Exercise 7

Create a ```list``` containing the first 10 [prime numbers](https://en.wikipedia.org/wiki/Prime_number) as:

```
primes = [2, 3, 5, 11, 7, 13, 17, 19, 23, 29]

```
<p style='text-align: justify;'>
Values 11 and 7, however, have been misplaced in the sequence. Correct the order by replacing the slice of <span style="color: rgb(32, 121, 77);">primes</span> that represents <span style="color: rgb(32, 121, 77);">[11, 7]</span> with <span style="color: rgb(32, 121, 77);">[7, 11]</span>.
</p>

::::::::::::::::: solution

## ANSWER


``` python
primes = [2, 3, 5, 11, 7, 13, 17, 19, 23, 29]

primes[3:5] = [7, 11]
```
:::::::::::::::::

:::::::::::::::::::::::::::::::

#### **Removal of members**
<p style='text-align: justify;'>
When removing a value from a ```list```, we have two options depending on our needs: we either remove the member and retain the value in another variable, or we remove it and dispose of the value, completely.
</p>

<p style='text-align: justify;'>
To remove a value from a ```list``` without retaining it, we use <kbd>.remove()</kbd>. The method takes one input argument, which is the value we would like to remove from our ```list```:
</p>


``` python
table.remove(174)

print(table)
```

``` output
[5, 12, 0, -1, 29, 'a text']
```


Alternatively, we can use <kbd>del</kbd>; a Python syntax that we can use, in this context, to delete a specific member using its index:


``` python
del table[-1]

print(table)
```

``` output
[5, 12, 0, -1, 29]
```
<p style='text-align: justify;'>
As established above, we can also delete a member and retain its value. Of course we can do so by holding the value inside another variable before deleting it.
</p>
<p style='text-align: justify;'>
Whilst this is a valid approach, Python's ```list``` provide us with <kbd>.pop()</kbd> to simplify the process even further. The method takes one input argument for the index of the member to be removed. It removes the member from the ```list``` and returns its value, so that we can retain it in a variable:
</p>


``` python
removed_value = table.pop(2)

print('Removed value:', removed_value)
print(table)
```

``` output
Removed value: 0
[5, 12, -1, 29]
```

::::::::::::::::::::::::::::::: challenge

## Practice Exercise 8

We know that the nucleotides of DNA include Adenine, Cytosine, Thymine and Guanine: <span style="color: rgb(32, 121, 77);">A</span>, <span style="color: rgb(32, 121, 77);">C</span>, <span style="color: rgb(32, 121, 77);">T</span>, and <span style="color: rgb(32, 121, 77);">G</span>.

Given a ```list``` representing a nucleotide sequence:

```
strand = ['A', 'C', 'G', 'G', 'C', 'M', 'T', 'A']
```

1. Find the index of the invalid nucleotide in <span style="color: rgb(32, 121, 77);">strand</span>.

2. Use the index you found to remove the invalid nucleotide from <span style="color: rgb(32, 121, 77);">strand</span> and retain the value in another variable.
Display the result as:

```
Removed from the strand: X
New strand: [X, X, X, ...]
```

3. What do you think happens once we run the following code, and why? What would be the final result displayed on the screen?

```
strand.remove('G')

print(strand)
```

::::::::::::::::: solution

## Q1


``` python
strand = ['A', 'C', 'G', 'G', 'C', 'M', 'T', 'A']

outlier_index = strand.index('M')
```
:::::::::::::::::

::::::::::::::::: solution

## Q2


``` python
outlier_value = strand.pop(outlier_index)

print('Removed from the strand:', outlier_value)
print('New strand:', strand)
```

``` output
Removed from the strand: M
New strand: ['A', 'C', 'G', 'G', 'C', 'T', 'A']
```
:::::::::::::::::

::::::::::::::::: solution

## Q3

One of the two <span style="color: rgb(32, 121, 77);">G</span> nucleotides, the one at index 2 of the original array, is removed. This means that the <kbd>.remove()</kbd> method removes only *first* instance of a member in an array. The output would therefore be:

```
['A', 'C', 'G', 'C', 'M', 'T', 'A']
```
:::::::::::::::::
:::::::::::::::::::::::::::::::

#### **Method--mediated operations**
<p style='text-align: justify;'>
We already know that *methods* are akin to functions that are associated with a specific type. In this subsection, we will be looking at how operations are performed using *methods*. We will not be introducing anything new, but will recapitulate what we already know, but from different perspectives.
</p>

<p style='text-align: justify;'>
So far in this chapter, we have learned how to perform different operations on ```list``` arrays in Python. You may have noticed that some operations return a result that we can store in a variable, while others change the original value.
</p>
With that in mind, we can divide operations performed using *methods* into two general categories:

1. Operations that return a result *without* changing the original array:


``` python
table = [1, 2, 3, 4]

index = table.index(3)

print(index)
print(table)
```

``` output
2
[1, 2, 3, 4]
```


2. Operations that use specific **methods** to *change* the original array, but do *not* necessarily return anything (in-place operations):


``` python
table = [1, 2, 3, 4]

table.append(5)

print(table)
```

``` output
[1, 2, 3, 4, 5]
```


If we attempt to store the output of an operation that does not a return result,  and store this into a variable, the variable will be created, but its value will be set to ```None```, by default:


``` python
result = table.append(6)

print(result)
print(table)
```

``` output
None
[1, 2, 3, 4, 5, 6]
```


It is important to know the difference between these types of operations. So as a rule of thumb, when we use *methods* to perform an operation, we can only change the original value if it is an instance of a *mutable* type. See [Table](02-input_output.Rmd#fig:nativeTypes) in order to find out which of Python’s built-in types are mutable.

The *methods* that are associated with *immutable* objects always return the results and do not provide the ability to alter the original value:

* In-place operation on a *mutable* object of type ```list```:


``` python
table = [5, 6, 7]

table.remove(6)

print(table)
```

``` output
[5, 7]
```


* In-place operation on an *immutable* object of type ```str```:


``` python
string = '567'

string.remove(20)
```

``` output
AttributeError: 'str' object has no attribute 'remove'
```

``` python
print(string)
```

``` output
567
```

* Normal operation on a *mutable* object of type ```list```:


``` python
table = [5, 6, 7]

ind = table.index(6)

print(ind)
```

``` output
1
```

* Normal operation on a *mutable* object of type ```list```:


``` python
string = '567'

ind = string.index('6')

print(ind)
```

``` output
1
```


### **List members**{#listMem}

<p style='text-align: justify;'>
A ```list``` is a collection of members that are independent of each other. This allows for Python to handle mixed data types, as we discussed earlier in the lesson. Each member has its own [type](02-input_output.Rmd#varTypes), and is therefore subject to the properties and limitations of that type:
</p>


``` python
table = [1, 2.1, 'abc']

print(type(table[0]))
print(type(table[1]))
print(type(table[2]))
```

``` output
<class 'int'>
<class 'float'>
<class 'str'>
```
<p style='text-align: justify;'>
For instance, mathematical operations may be considered a feature of all numeric types demonstrated in [Table](02-input_output.Rmd#fig:nativeTypes). However, unless in specific circumstance described in subsection [Non-numeric values](02-input_output.Rmd#subsubsec:mathematicalOperations:nonNumerics), such operations do not apply to instance of type ```str```.
</p>


``` python
table = [1, 2.1, 'abc']

table[0] += 1
table[-1] += 'def'

print(table)
```

``` output
[2, 2.1, 'abcdef']
```
<p style='text-align: justify;'>
A ```list``` in Python plays the role of a container that may incorporate _any number_ of values. Thus far, we have learned how to handle individual members of a ```list```. In this subsection, we will be looking at several techniques that help us address different circumstances where we look at a ```list``` from a 'wholist' perspective; that is, a container whose members are unknown to us.
</p>

#### **Membership test**
[**Membership test operations [advanced]**](https://docs.python.org/3/reference/expressions.html\#membership-test-operations)

We can check to see whether or not a specific value is a member of a ```list``` using the operator syntax <kbd>in</kbd>:


``` python
items = [1, 2.4, 'John', 5, 4]

print(2.4 in items)
```

``` output
True
```


``` python
print(3 in items)
```

``` output
False
```

The results may be stored in a variable:

``` python
has_five = 5 in items

print(has_five)
```

``` output
True
```

Similar to any other [logical expression](02-input_output.Rmd#subsec:logicalOperatons), we can [negate](02-input_output.Rmd#sec:logicalStatements:Negation) membership tests by using the `not` operator:


``` python
expr = 10 not in items

print(expr)
```

``` output
True
```


``` python
expr = 5 not in items

print(expr)
```

``` output
False
```

:::::::::::::::::::::::::::::::::::: callout
## Remember

When testing against ```str values``` --- *i.e.* text; don't forget that in programming, operations involving texts are *always* case-sensitive.


``` python
items = [1, 2.4, 'John', 5, 4]

john_capital = 'John'
john_small = 'john'

print(john_capital in items)
print(john_small in items)
```

``` output
True
False
```
::::::::::::::::::::::::::::::::::::

For *numeric* values, ```int``` and ```float``` may be used interchangeably:


``` python
print(4 in items)
```

``` output
True
```


``` python
print(4.0 in items)
```

``` output
True
```


Similar to other [logical expression](02-input_output.Rmd#subsec:logicalOperatons), membership tests may be incorporated into conditional statements:


``` python
if 'John' in items:
    print('Hello John')
else:
    print('Hello')
```

``` output
Hello John
```

::::::::::::::::::::::::::::::: challenge

## Practice Exercise 9 {#diy:arrays:list:randomPeptides}

Given a ```list``` of randomly generated peptide sequences as:


``` python
peptides = [
  'FAEKE', 'DMSGG', 'CMGFT', 'HVEFW', 'DCYFH', 'RDFDM', 'RTYRA',
  'PVTEQ', 'WITFR', 'SWANQ', 'PFELC', 'KSANR', 'EQKVL', 'SYALD',
  'FPNCF', 'SCDYK', 'MFRST', 'KFMII', 'NFYQC', 'LVKVR', 'PQKTF',
  'LTWFQ', 'EFAYE', 'GPCCQ', 'VFDYF', 'RYSAY', 'CCTCG', 'ECFMY',
  'CPNLY', 'CSMFW', 'NNVSR', 'SLNKF', 'CGRHC', 'LCQCS', 'AVERE',
  'MDKHQ', 'YHKTQ', 'HVRWD', 'YNFQW', 'MGCLY', 'CQCCL', 'ACQCL'
  ]
```
Determine whether or not each of the following sequences exist in <span style="color: rgb(32, 121, 77);">peptides</span>; and if so, what is their corresponding index:


* <span style="color: rgb(32, 121, 77);">IVADH</span>
* <span style="color: rgb(32, 121, 77);">CMGFT</span>
*	<span style="color: rgb(32, 121, 77);">DKAKL</span>
* <span style="color: rgb(32, 121, 77);">THGYP</span>
* <span style="color: rgb(32, 121, 77);">NNVSR</span>


Display the results in the following format:

```
Sequence XXXXX was found at index XX
```
::::::::::::::::: solution

## Q1


``` python
sequence = "IVADH"
if sequence in peptides:
    index = peptides.index(sequence)
    print('Sequence', sequence, 'was found at index',  index)
```
:::::::::::::::::

::::::::::::::::: solution

## Q2


``` python
sequence = "CMGFT"
if sequence in peptides:
    index = peptides.index(sequence)
    print('Sequence', sequence, 'was found at index',  index)
```

``` output
Sequence CMGFT was found at index 2
```
:::::::::::::::::

::::::::::::::::: solution
## Q3


``` python
sequence = "DKAKL"
if sequence in peptides:
    index = peptides.index(sequence)
    print('Sequence', sequence, 'was found at index',  index)
```
:::::::::::::::::

::::::::::::::::: solution
## Q4


``` python
sequence = "THGYP"
if sequence in peptides:
    index = peptides.index(sequence)
    print('Sequence', sequence, 'was found at index',  index)
```
:::::::::::::::::

::::::::::::::::: solution
## Q5


``` python
sequence = "NNVSR"
if sequence in peptides:
    index = peptides.index(sequence)
    print('Sequence', sequence, 'was found at index',  index)
```

``` output
Sequence NNVSR was found at index 30
```
:::::::::::::::::

:::::::::::::::::::::::::::::::

#### **Length**

[**Built-in functions: len**](https://docs.python.org/3.6/library/functions.html\#len)
<p style='text-align: justify;'>
The number of members contained within a ```list``` defines its length. Similar to the length of ```str``` values as discussed in [mathematical operations](02-input_output.Rmd#math_ops) [Practice Exercise 8](02-input_output.Rmd#diy:mathsI) and [Practice Exercise 11](02-input_output.Rmd#diy:mathOpts:Huntington), we use the built-in function <kbd>len()</kbd> also to determine the length of a ```list```:
</p>


``` python
items = [1, 2.4, 'John', 5, 4]

print(len(items))
```

``` output
5
```


``` python
print(len([1, 5, 9]))
```

``` output
3
```
<p style='text-align: justify;'>
The <kbd>len()</kbd> function *always* returns an integer value (```int```) equal to, or greater than, zero. We can store the length in a variable and use it in different [mathematical](02-input_output.Rmd#math_ops) or [logical](02-input_output.Rmd#subsec:logicalOperatons) operations:
</p>


``` python
table = [1, 2, 3, 4]
items_length = len(items)
table_length = len(table)

print(items_length + table_length)
```

``` output
9
```


``` python
print(len(table) > 2)
```

``` output
True
```

We can also use the length of an array in [conditional statements](03-conditional_statements.Rmd):


``` python
students = ['Julia', 'John', 'Jane', 'Jack']
present = ['Julia', 'John', 'Jane', 'Jack', 'Janet']

if len(present) == len(students):
    print('All the students are here.')
else:
    print('One or more students are not here yet.')
```

``` output
One or more students are not here yet.
```

:::::::::::::::::::::::::::::::::::: callout
## Remember
Both <kbd>in</kbd> and <kbd>len()</kbd> may be used in reference to any *type* of array or sequence in Python.

See [Table](02-input_output.Rmd#tb:types:nativeTypes) to find out which of Python's built-in types are regarded as a sequence.

::::::::::::::::::::::::::::::::::::


::::::::::::::::::::::::::::::: challenge

## Practice Exercise 10

Given the ```list``` of random peptides defined in [Practice Exercise 9](#diy:arrays:list:randomPeptides):

1. Define a ```list``` called <span style="color: rgb(32, 121, 77);">overlaps</span>, containing the sequences whose presence in <span style="color: rgb(32, 121, 77);">peptides</span> you previously confirmed in [Practice Exercise 9](#diy:arrays:list:randomPeptides).
2. Determine the length of <span style="color: rgb(32, 121, 77);">peptides</span>.
3. Determine the length of <span style="color: rgb(32, 121, 77);">overlaps</span>.

Display yours results as follows:
```
overlaps = ['XXXXX', 'XXXXX', ...]
Length of peptides: XX
Length of overlaps: XX
```

::::::::::::::::: solution

## Q1

``` python
overlaps = list()

sequence = "IVADH"
if sequence in peptides:
    overlaps.append(sequence)

sequence = "CMGFT"
if sequence in peptides:
    overlaps.append(sequence)

sequence = "DKAKL"
if sequence in peptides:
    overlaps.append(sequence)

sequence = "THGYP"
if sequence in peptides:
    overlaps.append(sequence)

sequence = "NNVSR"
if sequence in peptides:
    overlaps.append(sequence)

print('overlaps:', overlaps)
```

``` output
overlaps: ['CMGFT', 'NNVSR']
```

:::::::::::::::::

::::::::::::::::: solution

## Q2

``` python
print('Length of peptides:', len(peptides))
```

``` output
Length of peptides: 42
```

:::::::::::::::::

::::::::::::::::: solution

## Q3


``` python
print('Length of overlaps:', len(overlaps))
```

``` output
Length of overlaps: 2
```
:::::::::::::::::
:::::::::::::::::::::::::::::::

### **Weak References and Copies**
<p style='text-align: justify;'>
In our discussion on [mutability](#subsubsec:list:mutability), we also explored some of the in-place operations such as <kbd>.remove()</kbd> and <kbd>.append()</kbd>, that we can use to modify an existing ```list```. The use of these operations gives rise the following question: What if we need to perform an in-place operation on a reference variable, but also want to preserve the original array?
</p>

<p style='text-align: justify;'>
In such cases, we create a *copy* of the original array before we call the method and perform the operation. Let's run through this concept.
</p>
Suppose we have:

``` python
table_a = [1, 2, 3, 4]
```
<p style='text-align: justify;'>
A weak reference for <span style="color: rgb(32, 121, 77);">table_a</span>, also referred to as an alias or a symbolic link, may be defined as follows:
</p>

``` python
table_b = table_a

print(table_a, table_b)
```

``` output
[1, 2, 3, 4] [1, 2, 3, 4]
```


Now if we perform an in-place operation on only *one* of the two variables (the original or the alias) as follows:


``` python
table_a.append(5)
```

we will effectively change *both* of them:


``` python
print(table_a, table_b)
```

``` output
[1, 2, 3, 4, 5] [1, 2, 3, 4, 5]
```

<p style='text-align: justify;'>
This is useful if we need to change the name of a variable under certain conditions to make our code more explicit and legible; however, it does *nothing* to preserve an actual copy of the original data.
</p>
To retain a copy of the original array, however, we must perform a *copy* as follows:


``` python
table_c = table_b.copy()

print(table_b, table_c)
```

``` output
[1, 2, 3, 4, 5] [1, 2, 3, 4, 5]
```

where <span style="color: rgb(32, 121, 77);">table_c</span> represents a *copy* of <span style="color: rgb(32, 121, 77);">table_b</span>.

In this instance, performing an in-place operation on one variable would *not* have any impacts on the other:


``` python
table_b.append(6)

print(table_a, table_b, table_c)
```

``` output
[1, 2, 3, 4, 5, 6] [1, 2, 3, 4, 5, 6] [1, 2, 3, 4, 5]
```

<p style='text-align: justify;'>
where both the original array and its weak reference (<span style="color: rgb(32, 121, 77);">table_a</span> and <span style="color: rgb(32, 121, 77);">table_b</span>) changed without influencing the *copy* (<span style="color: rgb(32, 121, 77);">table_c</span>).
</p>

There is also a shorthand for the <kbd>.copy()</kbd> method to create a *copy*. As far as arrays of type ```list``` are concerned, writing:

```
new_table = original_table[:]
```

is exactly the same as writing:

```
new_table = original_table.copy()
```

Here is an example:


``` python
table_a = ['a', 3, 'b']
table_b = table_a
table_c = table_a.copy()
table_d = table_a[:]

table_a[1] = 5

print(table_a, table_b, table_c, table_d)
```

``` output
['a', 5, 'b'] ['a', 5, 'b'] ['a', 3, 'b'] ['a', 3, 'b']
```

<p style='text-align: justify;'>
Whilst both the original array and its weak reference (<span style="color: rgb(32, 121, 77);">table_a</span> and <span style="color: rgb(32, 121, 77);">table_b</span>) changed in this example; the *deep copies* (<span style="color: rgb(32, 121, 77);">table_c</span> and <span style="color: rgb(32, 121, 77);">table_d</span>) have remained unchanged.
</p>

:::::::::::::::::::::::::::::::::::: callout
## Note

The aforementioned versions of copy are called **shallow copies**. A shallow creates a new list, but the items in the new list are still references to the original items. If those items are mutable, such as being a list itself, then changing them in the copy will affect the original. A true deep copy requires use of the `copy.deepcopy()` function from the [copy module](https://docs.python.org/3/library/copy.html).
:::::::::::::::::::::::::::::::::::: 

::::::::::::::::::::::::::::::: challenge

## Practice Exercise 11 {#diy:arrays:list:consensus:one}
<p style='text-align: justify;'>
When defining a consensus sequence, it is common to include annotations to represent ambiguous amino acids. Four such annotations are as follows:
</p>

<p align = "center">
![](fig/residues_annotation.png)
</p>

Given a ```list``` of amino acids as:


``` python
amino_acids = [
    'A', 'R', 'N', 'D', 'C', 'E', 'Q', 'G', 'H', 'I',
    'L', 'K', 'M', 'F', 'P', 'S', 'T', 'W', 'Y', 'V'
  ]
```
<p style='text-align: justify;'>
1. Use <span style="color: rgb(32, 121, 77);">amino_acids</span> to create an independent ```list``` called <span style="color: rgb(32, 121, 77);">amino_acids_annotations</span> that contains all the standard amino acids.
</p>

<p style='text-align: justify;'>
2. Add to <span style="color: rgb(32, 121, 77);">amino_acids_annotations</span> the **1-letter** annotations for the ambiguous amino acids, as outlined in the table.
</p>

<p style='text-align: justify;'>
3. Evaluate the lengths for <span style="color: rgb(32, 121, 77);">amino_acids</span> and <span style="color: rgb(32, 121, 77);">amino_acids_annotations</span> and retain the result in a new ```list``` called <span style="color: rgb(32, 121, 77);">lengths</span>.
</p>

<p style='text-align: justify;'>
4. Using [logical operations](02-input_output.Rmd#subsec:logicalOperatons), test the two values stored in <span style="color: rgb(32, 121, 77);">lengths</span> for equivalence and display the result as a boolean (```True``` or ```False```) output.
</p>

::::::::::::::::: solution

## Q1


``` python
amino_acid_annotations = amino_acids.copy()
```

:::::::::::::::::

::::::::::::::::: solution

## Q2


``` python
amino_acid_annotations.append('X')

amino_acid_annotations.append('B')

amino_acid_annotations.append('Z')

amino_acid_annotations.append('J')
```
:::::::::::::::::

::::::::::::::::: solution

## Q3


``` python
lengths = [len(amino_acids), len(amino_acid_annotations)]

print(lengths)
```

``` output
[20, 24]
```

:::::::::::::::::


::::::::::::::::: solution

## Q4

``` python
equivalence = lengths[0] == lengths[1]

print(equivalence)
```

``` output
False
```


:::::::::::::::::
:::::::::::::::::::::::::::::::

### **Conversion to list** {#arrays:list:conversion}
<p style='text-align: justify;'>
As highlighted earlier in this section, arrays in Python can contain any value - regardless of type. We can exploit this feature to extract some interesting information about the data we store in an array.
</p>

<p style='text-align: justify;'>
To that end, we can [convert](02-input_output.Rmd#sec:conversionType) any sequence to a ```list```. See [Table](02-input_output.Rmd#tb:types:nativeTypes) to find out which of the built-in types in Python are considered to be a sequence.
</p>

Suppose we have the sequence for [Protein Kinase A Gamma (catalytic) subunit for humans](https://www.ncbi.nlm.nih.gov/protein/AAC41690.1?report=fasta) as follows:


``` python
# Multiple lines of text may be split into
# several lines inside parentheses:

human_pka_gamma = (
  'MAAPAAATAMGNAPAKKDTEQEESVNEFLAKARGDFLYRWGNPAQNTASSDQFERLRTLGMGSFGRVMLV'
  'RHQETGGHYAMKILNKQKVVKMKQVEHILNEKRILQAIDFPFLVKLQFSFKDNSYLYLVMEYVPGGEMFS'
  'RLQRVGRFSEPHACFYAAQVVLAVQYLHSLDLIHRDLKPENLLIDQQGYLQVTDFGFAKRVKGRTWTLCG'
  'TPEYLAPEIILSKGYNKAVDWWALGVLIYEMAVGFPPFYADQPIQIYEKIVSGRVRFPSKLSSDLKDLLR'
  'SLLQVDLTKRFGNLRNGVGDIKNHKWFATTSWIAIYEKKVEAPFIPKYTGPGDASNFDDYEEEELRISIN'
  'EKCAKEFSEF'
	)

print(type(human_pka_gamma))
```

``` output
<class 'str'>
```


We can now *convert* our sequence from its original type of ```str``` to ```list``` by using <kbd>list()</kbd> as a *function*. Doing so will automatically decompose the text down into individual characters:


``` python
# The function "list" may be used to convert string
# variables into a list of characters:
pka_list = list(human_pka_gamma)

print(pka_list)
```

``` output
['M', 'A', 'A', 'P', 'A', 'A', 'A', 'T', 'A', 'M', 'G', 'N', 'A', 'P', 'A', 'K', 'K', 'D', 'T', 'E', 'Q', 'E', 'E', 'S', 'V', 'N', 'E', 'F', 'L', 'A', 'K', 'A', 'R', 'G', 'D', 'F', 'L', 'Y', 'R', 'W', 'G', 'N', 'P', 'A', 'Q', 'N', 'T', 'A', 'S', 'S', 'D', 'Q', 'F', 'E', 'R', 'L', 'R', 'T', 'L', 'G', 'M', 'G', 'S', 'F', 'G', 'R', 'V', 'M', 'L', 'V', 'R', 'H', 'Q', 'E', 'T', 'G', 'G', 'H', 'Y', 'A', 'M', 'K', 'I', 'L', 'N', 'K', 'Q', 'K', 'V', 'V', 'K', 'M', 'K', 'Q', 'V', 'E', 'H', 'I', 'L', 'N', 'E', 'K', 'R', 'I', 'L', 'Q', 'A', 'I', 'D', 'F', 'P', 'F', 'L', 'V', 'K', 'L', 'Q', 'F', 'S', 'F', 'K', 'D', 'N', 'S', 'Y', 'L', 'Y', 'L', 'V', 'M', 'E', 'Y', 'V', 'P', 'G', 'G', 'E', 'M', 'F', 'S', 'R', 'L', 'Q', 'R', 'V', 'G', 'R', 'F', 'S', 'E', 'P', 'H', 'A', 'C', 'F', 'Y', 'A', 'A', 'Q', 'V', 'V', 'L', 'A', 'V', 'Q', 'Y', 'L', 'H', 'S', 'L', 'D', 'L', 'I', 'H', 'R', 'D', 'L', 'K', 'P', 'E', 'N', 'L', 'L', 'I', 'D', 'Q', 'Q', 'G', 'Y', 'L', 'Q', 'V', 'T', 'D', 'F', 'G', 'F', 'A', 'K', 'R', 'V', 'K', 'G', 'R', 'T', 'W', 'T', 'L', 'C', 'G', 'T', 'P', 'E', 'Y', 'L', 'A', 'P', 'E', 'I', 'I', 'L', 'S', 'K', 'G', 'Y', 'N', 'K', 'A', 'V', 'D', 'W', 'W', 'A', 'L', 'G', 'V', 'L', 'I', 'Y', 'E', 'M', 'A', 'V', 'G', 'F', 'P', 'P', 'F', 'Y', 'A', 'D', 'Q', 'P', 'I', 'Q', 'I', 'Y', 'E', 'K', 'I', 'V', 'S', 'G', 'R', 'V', 'R', 'F', 'P', 'S', 'K', 'L', 'S', 'S', 'D', 'L', 'K', 'D', 'L', 'L', 'R', 'S', 'L', 'L', 'Q', 'V', 'D', 'L', 'T', 'K', 'R', 'F', 'G', 'N', 'L', 'R', 'N', 'G', 'V', 'G', 'D', 'I', 'K', 'N', 'H', 'K', 'W', 'F', 'A', 'T', 'T', 'S', 'W', 'I', 'A', 'I', 'Y', 'E', 'K', 'K', 'V', 'E', 'A', 'P', 'F', 'I', 'P', 'K', 'Y', 'T', 'G', 'P', 'G', 'D', 'A', 'S', 'N', 'F', 'D', 'D', 'Y', 'E', 'E', 'E', 'E', 'L', 'R', 'I', 'S', 'I', 'N', 'E', 'K', 'C', 'A', 'K', 'E', 'F', 'S', 'E', 'F']
```

::::::::::::::::::::::::::::::: challenge

## Practice Exercise 12

Ask the user to enter a sequence of single-letter amino acids in *lower case*. Convert the sequence to ```list``` and:

1. Count the number of serine and threonine residues and display the result in the following format:

```
Total number of serine residues: XX
Total number of threonine residues: XX
```

2. Check whether or not the sequence contains both serine and threonine residues:

* If it does, display:
```
The sequence contains both serine and threonine residues.
```

* if it does not, display:
```
The sequence does not contain both serine and threonine residues.
```

::::::::::::::::: solution

## Q1
```
sequence_str = input('Please enter a sequence of single-letter amino acids in lower-case: ')

sequence = list(sequence_str)

ser_count = sequence.count('s')
thr_count = sequence.count('t')

print('Total number of serine residues:', ser_count)

print('Total number of threonine residues:', thr_count)
```

:::::::::::::::::

::::::::::::::::: solution

## Q2
```
if ser_count > 0 and thr_count > 0:
    response_state = ''
else:
    response_state = 'not'

print(
    'The sequence does',
    'response_state',
    'contain both serine and threonine residues.'
		)
```
:::::::::::::::::

:::::::::::::::::::::::::::::::


:::::::::::::::::::::::::::::::::::: callout
## Advanced Topic
<p style='text-align: justify;'>
[Generators](https://en.wikipedia.org/wiki/Generator_(computer_programming)) represent a specific [type](02-input_output.Rmd#varTypes) in Python whose results are *not* immediately evaluated. A generator is a specific type of iterable (an object capable of returning elements, one at a time), that can return its items, lazily. This means that it generates values on the fly, and only as and when required in your program. Generators can be particularly useful when working with large datasets, where loading all the data into memory can be computationally expensive. Using generators with such data, can help to process it in more manageable units. 
</p>
<p style='text-align: justify;'>
Generators’ lazy evaluation in [functional programming](https://en.wikipedia.org/wiki/Functional_programming) is often used in the context of a `for-loop`: which we will explore in a later L2D lesson on iterations. We do not further explore generators on this course, but if you are interested to learn more, you can find plenty of information in the [following official documentation](https://docs.python.org/3.6/howto/functional.html\#generators).
</p>

::::::::::::::::::::::::::::::::::::


### **Useful methods** {#subsubsec:list:usefulMethodsForList}

<p style='text-align: justify;'>
In this subsection, we will be reviewing some of the useful and important *methods* that are associated with object of type ```list```. We will make use of snippets of code that exemplify such *methods*, in practice. The  [cheatsheet](#cheatsheat) displayed below shows the *methods* associated with the built-in arrays in Python can be helpful. We will cover the other array types (tuple and set) mentioned, later in this lesson. If you’re curious to learn more, refer to the Python documentation linked [here](https://docs.python.org/3.6/tutorial/datastructures.html#more-on-lists) for more information about each of the individual list methods.
</p>

![Common operations for list, tuple and set arrays in Python.](fig/arrays-cheatsheet.png){#cheatsheat}
<p style='text-align: justify;'>
The *methods* outlined here are not individually described; however, at this point, you should be able to work out what they do by looking at their names and respective examples.
</p>
Count a specific value within a ```list```:


``` python
table_a = [1, 2, 2, 2]
table_b = [15, 16]

print(table_a.count(2))
```

``` output
3
```

Extend a ```list``` by adding two lists to each other, as follows. *(Please note that adding two lists to one another is not considered an in-place operation).*


``` python
table_a = [1, 2, 2, 2]
table_b = [15, 16]

table_c = table_a.copy()  # copy.
table_c.extend(table_b)

print(table_a, table_b, table_c)
```

``` output
[1, 2, 2, 2] [15, 16] [1, 2, 2, 2, 15, 16]
```

`.extend` can also be replicated using the `+` operation:


``` python
table_a = [1, 2, 2, 2]
table_b = [15, 16]

table_c = table_a + table_b

print(table_a, table_b, table_c)
```

``` output
[1, 2, 2, 2] [15, 16] [1, 2, 2, 2, 15, 16]
```


``` python
table_a = [1, 2, 2, 2]
table_b = [15, 16]

table_c = table_a.copy()  # copy.
table_d = table_a + table_b

print(table_c == table_d)
```

``` output
False
```
<p style='text-align: justify;'>
We can also reverse the values in a ```list```. There are two methods for doing so: `.reverse` and `.reversed()`. Note that `.reversed()` is a generator, meaning that the output of the function is not evaluated immediately; and instead, we get a generic output. The first of these two methods is:
</p>

1. Through an in-place operation using <kbd>.reverse()</kbd>

``` python
table = [1, 2, 2, 2, 15, 16]
table.reverse()

print("Reversed:", table)
```

``` output
Reversed: [16, 15, 2, 2, 2, 1]
```



2. And secondly, using <kbd>.reversed()</kbd> - the built-in generator function:

``` python
table = [1, 2, 2, 2, 15, 16]
table_rev = reversed(table)

print("Result:", table_rev)
print("Type:", type(table_rev))
```

``` output
Result: <list_reverseiterator object at 0x116d14d60>
Type: <class 'list_reverseiterator'>
```

We can, however, force the evaluation process by converting the generator results into a ```list```:


``` python
table_rev_evaluated = list(table_rev)

print('Evaluated:', table_rev_evaluated)
```

``` output
Evaluated: [16, 15, 2, 2, 2, 1]
```

Members of a ```list``` may also be sorted in-place, as follows:


``` python
table = [16, 2, 15, 1, 2, 2]
table.sort()

print("Sorted (ascending):", table)
```

``` output
Sorted (ascending): [1, 2, 2, 2, 15, 16]
```

:::::::::::::::::::::::::::::::::::: callout
## Advanced Topic

There is also a further function built into Python: <kbd>sorted()</kbd>. This is also a generator function, offering more advanced features that are beyond the scope of this course. You can find out more about it from the [official Python documentation](https://docs.python.org/3/library/functions.html\#sorted) and [examples](https://docs.python.org/3/howto/sorting.html\#sortinghowto).
::::::::::::::::::::::::::::::::::::

The <kbd>.sort()</kbd> method takes an optional keyword argument entitled *reverse* (default: ```False```). If set to ```True```, the method will perform a descending sort:


``` python
table = [16, 2, 15, 1, 2, 2]
table.sort(reverse=True)

print("Sorted (descending):", table)
```

``` output
Sorted (descending): [16, 15, 2, 2, 2, 1]
```

We can also create an empty ```list```, so that we can add members to it later in our code using <kbd>.append()</kbd>, or <kbd>.extend()</kbd> or other tools:


``` python
table = list() 
# Note: a list can also be instantiated without using the list function. 
# You simply provide a pair of empty square brackets, as below:
# table = []

print(table)
```

``` output
[]
```


``` python
table.append(5)

print(table)
```

``` output
[5]
```


``` python
another_table = ['Jane', 'Janette']
table.extend(another_table)

print(another_table)
```

``` output
['Jane', 'Janette']
```

::::::::::::::::::::::::::::::: challenge

## Practice Exercise 13
<p style='text-align: justify;'>
Create a ```list```, and experiment with each of the methods provided in the above example. Try including members of different *types* in your ```list```, and see how each of these methods behave.
</p>

::::::::::::::::: solution

## ANSWER

This practice exercise was intended to encourage you to experiment with the methods outlined.
:::::::::::::::::

:::::::::::::::::::::::::::::::

### **Nested Arrays** {#arrays:list:nestedArrays}
<p style='text-align: justify;'>
At this point, you should be comfortable with creating, handling and manipulating arrays of type ```list```, in Python. It is important to have a foundational understanding of the principles outlined in this section so far, before starting to learn about *nested arrays*.
</p>

<p style='text-align: justify;'>
We have already established that arrays can contain any value - regardless of type. This means that they can also contain other arrays. An array that includes at least one member that is, itself, an array is referred to as a **nested array**. This can be thought of as a table with more than one column:
</p>

![](fig/nested_arrays.png)

:::::::::::::::::::::::::::::::::::: callout
## Remember
<p style='text-align: justify;'>
Arrays can contain values of any *type*. This rule applies to nested arrays too. We have exclusively included ```int``` numbers in our table in order to simplify the above example.

</p>

::::::::::::::::::::::::::::::::::::

#### **Implementation**
The table can be written in Python as a nested array:


``` python
# The list has 3 members, 2 of which
# are arrays of type list:
table = [[1, 2, 3], [4], [7, 8]]

print(table)
```

``` output
[[1, 2, 3], [4], [7, 8]]
```

#### **Indexing**
The indexing principles for nested arrays are slightly different to those we have familiarised with, up to this point. To retrieve an individual member in a nested ```list```, we always reference the *row index*, followed by the *column index*.

We may visualise the process as follows:

![](fig/nested_arrays2.png)
### Note
In the diagram above, `table[1][0]` assumes that `table[1]` is a list (i.e., a nested array). If table were defined like this:


``` python
table = [[1, 2, 3], 4, [7, 8]]
```

Then `table[1]` would return the number 4, which is an `int` — not a list. Trying to index into an integer like `4[0]` would cause a ```TypeError```, because integers are not subscriptable in Python (i.e., you can’t extract an element from them using square brackets).

In the example we gave, we avoided this, by using `[4]` instead of providing 4 as a singleton, so that `table[1]` returns a list, and `table[1][0]` correctly returns the value 4.

In order to retrieve an entire row, we only need to include the reference for that row. All the values within the row are referenced, implicitly:


``` python
print(table[0])
```

``` output
[1, 2, 3]
```

and to retrieve a specific member, we include the reference for both the row and column:


``` python
print(table[0][1])
```

``` output
2
```

<p style='text-align: justify;'>
We may also extract slices from a nested array. The protocol is identical to normal arrays, described in the previous section of this lesson on [slicing](#sec:list:slicing). In nested arrays, however, we may take slices from the columns as well as the rows:
</p>


``` python
print(table[:2])
```

``` output
[[1, 2, 3], 4]
```


``` python
print(table[0][:2])
```

``` output
[1, 2]
```

Note that only 2 of the 3 members in <span style="color: rgb(32, 121, 77);">table</span> are arrays of type ```list```:


``` python
print(table[0], type(table[0]))
```

``` output
[1, 2, 3] <class 'list'>
```


``` python
print(table[2], type(table[2]))
```

``` output
[7, 8] <class 'list'>
```

However, there is another member that is not an array:



``` python
print(table[1], type(table[1]))
```

``` output
4 <class 'int'>
```

<p style='text-align: justify;'>
In most circumstances, we would want all the members in an array to be *homogeneous* in type --- *i.e.* we want them all to have the same type. In such cases, we can implement the table as:
</p>


``` python
table = [[1, 2, 3], [4], [7, 8]]

print(table[1], type(table[1]))
```

``` output
[4] <class 'list'>
```
<p style='text-align: justify;'>
An array with only one member --- *e.g.* <span style="color: rgb(32, 121, 77);">[4]</span>, is sometimes referred to as a *singleton* array.
</p>

::::::::::::::::::::::::::::::: challenge

## Practice Exercise 14

Given the following Table of pathogens and their corresponding diseases:

![](fig/pathogens.png)
<p style='text-align: justify;'>
1. Substitute <span style="color: rgb(32, 121, 77);">N/A</span> for ```None```, and create an array to represent the table in its presented order. Retain the array in a variable, and display the result.
</p>

<p style='text-align: justify;'>
2. Modify the array you created so that its members are sorted *descendingly*, and display the result.
</p>

::::::::::::::::: solution

## Q1


``` python
disease_pathogen = [
  ["Bacterium", "Negative", "Shigella flexneri" , "Bacillary dysentery"],
  ["Prion", None, "PrP(sc)", "Transmissible spongiform encephalopathies"],
  ["Bacterium", "Negative", "Vibrio cholerae", "Cholera"],
  ["Bacterium", "Negative", "Listeria monocytogenes", "Listeriosis"],
  ["Virus", None, "Hepatitis C", "Hepatitis"],
  ["Bacterium", "Negative", "Helicobacter pylori", "Peptic ulcers"],
  ["Bacterium", "Negative", "Mycobacterium tuberculosis", "Tuberculosis"],
  ["Bacterium", "Negative", "Chlamydia trachomatis", "Chlamydial diseases"],
  ["Virus", None, "Human Immunodeficiency Virus", "Human Immunodeficiency"]
  ]

print(disease_pathogen)
```

``` output
[['Bacterium', 'Negative', 'Shigella flexneri', 'Bacillary dysentery'], ['Prion', None, 'PrP(sc)', 'Transmissible spongiform encephalopathies'], ['Bacterium', 'Negative', 'Vibrio cholerae', 'Cholera'], ['Bacterium', 'Negative', 'Listeria monocytogenes', 'Listeriosis'], ['Virus', None, 'Hepatitis C', 'Hepatitis'], ['Bacterium', 'Negative', 'Helicobacter pylori', 'Peptic ulcers'], ['Bacterium', 'Negative', 'Mycobacterium tuberculosis', 'Tuberculosis'], ['Bacterium', 'Negative', 'Chlamydia trachomatis', 'Chlamydial diseases'], ['Virus', None, 'Human Immunodeficiency Virus', 'Human Immunodeficiency']]
```
:::::::::::::::::

::::::::::::::::: solution

## Q2

``` python
disease_pathogen.sort(reverse=True)

print(disease_pathogen)
```

``` output
[['Virus', None, 'Human Immunodeficiency Virus', 'Human Immunodeficiency'], ['Virus', None, 'Hepatitis C', 'Hepatitis'], ['Prion', None, 'PrP(sc)', 'Transmissible spongiform encephalopathies'], ['Bacterium', 'Negative', 'Vibrio cholerae', 'Cholera'], ['Bacterium', 'Negative', 'Shigella flexneri', 'Bacillary dysentery'], ['Bacterium', 'Negative', 'Mycobacterium tuberculosis', 'Tuberculosis'], ['Bacterium', 'Negative', 'Listeria monocytogenes', 'Listeriosis'], ['Bacterium', 'Negative', 'Helicobacter pylori', 'Peptic ulcers'], ['Bacterium', 'Negative', 'Chlamydia trachomatis', 'Chlamydial diseases']]
```
:::::::::::::::::
:::::::::::::::::::::::::::::::

### **Dimensions** {#arrays:list:dimensions}

A nested array is considered *two-dimensional* or *2D* when:

*	*All* of its members in a nested array are arrays, themselves;


* *All* sub-arrays are of **equal length** --- *i.e.*  all the columns in the table are filled and have the same number of rows; and,


* *All* members of the sub-arrays are *homogeneous* in type --- *i.e.*  they all have the same type (*e.g.* ```int```).


A two dimensional arrays may be visualised as follows:
![](fig/dimensions.png)

:::::::::::::::::::::::::::::::::::: callout
## Advanced Topic
<p style='text-align: justify;'>
Nested arrays may, themselves, be nested. This means that, if needed, we can have 3, 4 or *n* dimensional arrays, too. Analysis and organisation of such arrays is an important part of a field known as [optimisation](https://en.wikipedia.org/wiki/Mathematical_optimization) in computer science and mathematics. Optimisation is the cornerstone of machine learning, and addresses the problem known as [curse of dimensionality](https://en.wikipedia.org/wiki/Curse_of_dimensionality).
</p>

::::::::::::::::::::::::::::::::::::


<p style='text-align: justify;'>
Such arrays are referred to in mathematics as a [matrix](https://en.wikipedia.org/wiki/Matrix_(mathematics)). We can therefore represent a two-dimensional array as a mathematical matrix. To that end, the above array would translate to the annotation displayed in equation below.
</p>

$$table=\begin{bmatrix}
1&2&3\\
4&5&6\\
7&8&9\\
\end{bmatrix}$$


The implementation of these arrays is identical to the implementation of other nested arrays. We can therefore code our table in Python as:


``` python
table = [
  [1, 2, 3],
  [4, 5, 6],
  [7, 8, 9]
  ]

print(table)
```

``` output
[[1, 2, 3], [4, 5, 6], [7, 8, 9]]
```


``` python
print(table[2])
```

``` output
[7, 8, 9]
```


``` python
print(table[1][0])
```

``` output
4
```


``` python
print(table[:2])
```

``` output
[[1, 2, 3], [4, 5, 6]]
```

::::::::::::::::::::::::::::::: challenge

## Practice Exercise 15
<p style='text-align: justify;'>
Computers see images as multidimensional arrays (matrices). In its simplest form, an image is a two-dimensional array containing only two colours.
</p>
Given the following black and white image:

![](fig/image.png)
<p style='text-align: justify;'>
1. Considering that black and white squares represent zeros and ones respectively, create a two-dimensional array to represent the image. Display the results.
</p>

<p style='text-align: justify;'>
2. Create a new array, but this time use ```False``` and ```True``` to represent black and white respectively.
</p>
Display the results.

::::::::::::::::: solution

## Q1

``` python
cross = [
		    [0, 0, 0, 0, 0, 0, 0],
		    [0, 1, 0, 0, 0, 1, 0],
		    [0, 0, 1, 0, 1, 0, 0],
		    [0, 0, 0, 1, 0, 0, 0],
		    [0, 0, 1, 0, 1, 0, 0],
		    [0, 1, 0, 0, 0, 1, 0],
		    [0, 0, 0, 0, 0, 0, 0]
		]

print(cross)
```

``` output
[[0, 0, 0, 0, 0, 0, 0], [0, 1, 0, 0, 0, 1, 0], [0, 0, 1, 0, 1, 0, 0], [0, 0, 0, 1, 0, 0, 0], [0, 0, 1, 0, 1, 0, 0], [0, 1, 0, 0, 0, 1, 0], [0, 0, 0, 0, 0, 0, 0]]
```
:::::::::::::::::

::::::::::::::::: solution

## Q2

``` python
cross_bool = [
  [False, False, False, False, False, False, False],
  [False, True, False, False, False, True, False],
  [False, False, True, False, True, False, False],
  [False, False, False, True, False, False, False],
  [False, False, True, False, True, False, False],
  [False, True, False, False, False, True, False],
  [False, False, False, False, False, False, False]
  ]

print(cross_bool)
```

``` output
[[False, False, False, False, False, False, False], [False, True, False, False, False, True, False], [False, False, True, False, True, False, False], [False, False, False, True, False, False, False], [False, False, True, False, True, False, False], [False, True, False, False, False, True, False], [False, False, False, False, False, False, False]]
```
:::::::::::::::::
:::::::::::::::::::::::::::::::
### **Summary**

At this point, you should be familiar with arrays and how they work, in general. Throughout this section, we extensively covered the Python ```list```,  which is one of the language’s most popular types of *built-in* arrays. We also learned:

* How to \emph{create} a ```list``` from scratch;

* How to *manipulate* a ```list``` using different *methods*;

* How to use *indexing* and *slicing* techniques to our advantage;

* *Mutability* --- a concept we revisit in the forthcoming lessons;

*  *In-place operations*, and the difference between *weak references* and *copies*;

* *Nested* and *multi-dimensional* arrays; and,

* How to *convert* other sequences (*e.g.* ```str```) to ```list```.

## Tuple {#subsec:tuples}

<p style='text-align: justify;'>
Another of Python’s built-in array types is called a ```tuple```. A tuple is an immutable alternative to ```list```. That is, once a tuple has been created, its contents cannot be modified in any way. Tuples are often used in applications where it is imperative that the contents of an array cannot be changed.
</p>
<p style='text-align: justify;'>
For instance, we know that in the [Wnt signaling pathway](http://www.cell.com/cell/fulltext/S0092-8674(12)00586-7), there are two co-receptors. This is final, and would not change at any point in our program.

If you are interested to learn more, please explore the Python documentation on [tuples and sequences](https://docs.python.org/3.6/tutorial/datastructures.html#tuples-and-sequences).

</p>

:::::::::::::::::::::::::::::::::::: callout
## Remember
<p style='text-align: justify;'>
The most common way to implement a ```tuple``` in Python, is to place our comma-separated values inside round parentheses: `x = (1, 2, 3, ...)`. While there is no specific theoretical term for a tuple instantiated with round parentheses, we can refer to this type of tuple as an **explicit tuple**.


You can also instantiate a tuple without parentheses, as well: `x=1, 2, 3`. In this case, Python acknowledges that a tuple is implied, and is therefore assumed. Thus, we often refer to this type of tuple as an **implicit tuple**, and these are created using an operation called *packing*.

</p>

::::::::::::::::::::::::::::::::::::

For the time being, we will be making use of explicit tuples, as they are the clearest and most explicit in annotation, and therefore easiest to program with and recognise. 


``` python
pathway = 'Wnt Signaling'
coreceptors = ('Frizzled', 'LRP')

print(type(coreceptors))
```

``` output
<class 'tuple'>
```


``` python
print(coreceptors)
```

``` output
('Frizzled', 'LRP')
```


``` python
wnt = (pathway, coreceptors)

print(type(wnt))
```

``` output
<class 'tuple'>
```


``` python
print(wnt)
```

``` output
('Wnt Signaling', ('Frizzled', 'LRP'))
```


``` python
print(wnt[0])
```

``` output
Wnt Signaling
```

<p style='text-align: justify;'>
Indexing and slicing principles for a ```tuple``` are identical to those of a ```list```, aforementioned in this lesson’s subsections on [indexing](#sec:list:indexing) and [slicing](#sec:list:slicing).
</p>

### **Conversion to tuple**
Similar to ```list```, we can convert other sequences to ```tuple```:


``` python
numbers_list = [1, 2, 3, 4, 5]

print(type(numbers_list))
```

``` output
<class 'list'>
```


``` python
numbers = tuple(numbers_list)

print(numbers)
```

``` output
(1, 2, 3, 4, 5)
```


``` python
print(type(numbers))
```

``` output
<class 'tuple'>
```


``` python
text = 'This is a string.'

print(type(text))
```

``` output
<class 'str'>
```


``` python
characters = tuple(text)

print(characters)
```

``` output
('T', 'h', 'i', 's', ' ', 'i', 's', ' ', 'a', ' ', 's', 't', 'r', 'i', 'n', 'g', '.')
```


``` python
print(type(characters))
```

``` output
<class 'tuple'>
```


### **Immutability** {#subsec:tuple:immutability}

In contrast with ```list```, however, if we attempt to change the contents of a ```tuple```, a ```TypeError``` is raised:


``` python
coreceptors[1] = 'LRP5/6'
```

``` output
TypeError: 'tuple' object does not support item assignment
```

Even though ```tuple``` is an immutable type, it can contain both mutable and immutable objects:


``` python
# (immutable, immutable, immutable, mutable)
mixed_tuple = (1, 2.5, 'abc', (3, 4), [5, 6])

print(mixed_tuple)
```

``` output
(1, 2.5, 'abc', (3, 4), [5, 6])
```

and mutable objects inside a ```tuple``` may still be changed:

``` python
print(mixed_tuple, type(mixed_tuple))
```

``` output
(1, 2.5, 'abc', (3, 4), [5, 6]) <class 'tuple'>
```



``` python
print(mixed_tuple[4], type(mixed_tuple[4]))
```

``` output
[5, 6] <class 'list'>
```

:::::::::::::::::::::::::::::::::::: callout
## Advanced Topic
<p style='text-align: justify;'>
**Why and how can we change mutable objects inside a tuple, when a ```tuple``` is considered to be an immutable data structure: ** 

Members of a ```tuple``` are not directly stored in memory. An immutable value (*e.g.* an integer: ```int```) has an existing, predefined reference, in memory. When used in a ```tuple```, it is this reference that is *associated* with the ```tuple```, and not the value itself. On the other hand, a mutable object does not have a predefined reference in memory, and is instead created on request somewhere in your computer’s memory (wherever there is enough free space). 

While we can never change or redefine a predefined reference, we can always manipulate something we have defined ourselves. When we make such an alteration, the location of our mutable object in memory may well change, but its reference — which is what is stored in a ```tuple```, remains identical. In Python, it is possible to discover the reference an object is using, with the function ```id()```. Upon experimenting with this function, you will notice that the reference to an immutable object (*e.g.* an ```int``` value) will never change, no matter how many times you define it in a different context or variable. In contrast, the reference number to a mutable object (*e.g.* a ```list```) is changed every time it is defined, even if it contains exactly the same values.
</p>

::::::::::::::::::::::::::::::::::::


``` python
# Lists are mutable, so we can alter their values:
mixed_tuple[4][1] = 15

print(mixed_tuple)
```

``` output
(1, 2.5, 'abc', (3, 4), [5, 15])
```


``` python
mixed_tuple[4].append(25)

print(mixed_tuple)
```

``` output
(1, 2.5, 'abc', (3, 4), [5, 15, 25])
```


``` python
# We cannot remove the list from the tuple,
# but we can empty it by clearing its members:
mixed_tuple[4].clear()

print(mixed_tuple)
```

``` output
(1, 2.5, 'abc', (3, 4), [])
```

Tuples may be empty or have a single value (singleton):


``` python
member_a = tuple()

print(member_a, type(member_a), len(member_a))
```

``` output
() <class 'tuple'> 0
```


``` python
# Empty parentheses also generate an empty tuple.
# Remember: we cannot add values to an empty tuple, later.
member_b = ()

print(member_b, type(member_b), len(member_b))
```

``` output
() <class 'tuple'> 0
```


``` python
# Singleton - Note that it is essential to include
# a comma after the value in a single-member tuple:
member_c = ('John Doe',)

print(member_c, type(member_c), len(member_c))
```

``` output
('John Doe',) <class 'tuple'> 1
```


``` python
# If the comma is not included, a singleton tuple
# is not constructed:
member_d = ('John Doe')

print(member_d, type(member_d), len(member_d))
```

``` output
John Doe <class 'str'> 8
```

### **Packing and unpacking**
As previously discussed, a ```tuple``` may also be constructed without parentheses. This is an implicit operation and is known as *packing*.

:::::::::::::::::::::::::::::::::::: callout
## Remember
Implicit processes must be used sparingly. As always, the more coherent the code, the better it is.

::::::::::::::::::::::::::::::::::::


``` python
numbers = 1, 2, 3, 5, 7, 11

print(numbers, type(numbers), len(numbers))
```

``` output
(1, 2, 3, 5, 7, 11) <class 'tuple'> 6
```


``` python
# Note that for a singleton, we still need to
# include the comma.
member = 'John Doe',

print(member, type(member), len(member))
```

``` output
('John Doe',) <class 'tuple'> 1
```

The reverse of this process is known as unpacking. Unpacking is no longer considered an implicit process because it replaces unnamed values inside an array, with named variables.

:::::::::::::::::::::::::::::::::::: callout
## Note

Unpacking is often employed when you want to store the returned values from a function, when there is more than one. If all returned values are stored in one variable, then they will be stored in a tuple.
::::::::::::::::::::::::::::::::::::


``` python
dimensions = 14, 17, 12

x, y, z = dimensions

print(x)
```

``` output
14
```


``` python
print(x, y)
```

``` output
14 17
```


``` python
member = ('Jane Doe', 28, 'London', 'Student', 'Female')
name, age, city, status, gender = member

print('Name:', name, '- Age:', age)
```

``` output
Name: Jane Doe - Age: 28
```


::::::::::::::::::::::::::::::: challenge

## Practice Exercise 16

Given:

``` python
protein_info = ('GFP', 238)
```

Unpack <span style="color: rgb(32, 121, 77);">protein_info</span> into two distinct variables: <span style="color: rgb(32, 121, 77);">protein_name</span> and <span style="color: rgb(32, 121, 77);">protein_length</span>.



::::::::::::::::: solution

## ANSWER

``` python
protein_name, protein_length = protein_info
```
:::::::::::::::::

:::::::::::::::::::::::::::::::



:::::::::::::::::::::::::::::::::::: callout
## Note
<p style='text-align: justify;'>
There is another type of ```tuple``` in Python referred to as a ```namedtuple```. This allows for the members of a ```tuple``` to be named independently (*e.g.*  ```member.name``` or ```member.age```), and thereby eliminates the need for unpacking. It was originally implemented by [Raymond Hettinger](https://twitter.com/raymondh), one of Python's core developers, for Python 2.4 (in 2004) but was neglected at the time. It has since gained popularity as a very useful tool. ```namedtuple``` is not a built-in tool, so it is not discussed here. However, it is included in the default library and is installed as a part of Python.
If you are feeling ambitious and would like to learn more, please take a look at the [official documentations](https://docs.python.org/3.6/library/collections.html\#collections.namedtuple) and examples. Raymond is also a regular speaker at PyCon (International Python Conferences), recordings of which are available online. He also often uses his Twitter/X account to talk about small, but important features in Python; which could be worth throwing him a follow.
</p>

::::::::::::::::::::::::::::::::::::

### **Summary**
<p style='text-align: justify;'>
In this section of our  Basic Python 2 lesson, we learned about ```tuple``` - another type of built-in array within Python, and one which is *immutable*. This means that once it is created, the array can no longer be altered. We saw that trying to change the value of a ```tuple``` raises a ```TypeError```. We also established that ```list``` and ```tuple``` follow an identical indexing protocol, and that they have two methods in common: <kbd>.index()</kbd> and <kbd>.count()</kbd>. Finally, we talked about *packing* and *unpacking* techniques, and how they improve the quality and legibility of our code.
</p>

<p style='text-align: justify;'>
If you are interested in learning about ```list``` and ```tuple``` in more depth, have a look at the [official documentation of Sequence Types -- list, tuple, range](https://docs.python.org/3/library/stdtypes.html#sequence-types-list-tuple-range).
</p>

## Sets {#subsec:Sets}

Another built-in Python collection type is the set. Unlike lists and tuples, sets are unordered collections of unique elements.

This means:
- Items in a set do not have a defined order or index — you cannot access elements by position.
- A set cannot contain duplicate values — each element must be unique.

Sets are particularly useful for:
- Efficiently checking for membership using the in operator.
- Removing duplicates from other collections.
- Performing mathematical set operations like union, intersection, and difference — often valuable in biological data analysis (e.g., comparing gene lists or identifying shared mutations).

Sets can be created using curly braces {} or the set() constructor.


``` python
unique_samples = {'sample1', 'sample2', 'sample3', 'sample1', 'sampleC'}
print(unique_samples)
```

``` output
{'sampleC', 'sample3', 'sample1', 'sample2'}
```

Let's create a set from a list, as follows:


``` python
samples = [1, 1, '1', 2, 5]
unique_samples = set(samples)
print(unique_samples)
```

``` output
{1, 2, 5, '1'}
```

``` python
print(numbers)
```

``` output
(1, 2, 3, 5, 7, 11)
```

:::::::::::::::::::::::::::::::::::: callout
## Note 

This also illustrates that Python distinguishes between 1 (an integer) and '1' (a string), so both are preserved as unique values.
::::::::::::::::::::::::::::::::::::

### Creating an empty set:

Using {} alone creates an empty dictionary, not a set. Dictionaries are a different type of data structure that we will cover in depth, in a later lesson. To create an empty set, use the set() constructor:


``` python
empty_set = set()
print(empty_set)
```

``` output
set()
```


``` python
empty_dict = {}
print(type(empty_dict))
```

``` output
<class 'dict'>
```

### Mutability:

Sets are mutable, meaning you can add or remove elements after creation:


``` python
gene_set = {'geneA', 'geneB', 'geneC'}
gene_set.add('geneD')
print("After adding geneD:", gene_set)
```

``` output
After adding geneD: {'geneD', 'geneB', 'geneC', 'geneA'}
```

If you attempt to add a duplicate, this will be ignored:


``` python
gene_set.add('geneA')
print("After attempting to add geneA again:", gene_set)
```

``` output
After attempting to add geneA again: {'geneD', 'geneB', 'geneC', 'geneA'}
```


### Indexing and slicing:

Because sets are unordered, they do not support indexing or slicing:


``` python
gene = gene_set[0]
```

``` output
TypeError: 'set' object is not subscriptable
```

### Set operations:

Sets provide fast and expressive ways to compare collections. Below, we use set operations to compare differentially expressed genes from two experiments:


``` python
experiment1_genes = {'TP53', 'MYC', 'BRCA1', 'AKT1', 'KRAS'}
experiment2_genes = {'MYC', 'VEGFA', 'KRAS', 'MAPK1', 'TP53'}
```

Union - all genes from either experiment:

``` python
all_found_genes = experiment1_genes.union(experiment2_genes)
print("All genes found:", all_found_genes)
```

``` output
All genes found: {'TP53', 'KRAS', 'VEGFA', 'MAPK1', 'BRCA1', 'MYC', 'AKT1'}
```

Intersection - genes found in both experiments:

``` python
common_genes = experiment1_genes.intersection(experiment2_genes)
print("Common genes:", common_genes)
```

``` output
Common genes: {'TP53', 'KRAS', 'MYC'}
```

Symmetric difference - genes found in only one of the experiments:

``` python
exclusive_genes = experiment1_genes.symmetric_difference(experiment2_genes)
print("Genes found exclusively in one experiment:", exclusive_genes)
```

``` output
Genes found exclusively in one experiment: {'VEGFA', 'MAPK1', 'BRCA1', 'AKT1'}
```

Difference - genes unique to the first experiment:

``` python
unique_to_exp1 = experiment1_genes.difference(experiment2_genes)
print("Unique to Experiment 1:", unique_to_exp1)
```

``` output
Unique to Experiment 1: {'BRCA1', 'AKT1'}
```

::::::::::::::::::::::::::::::: challenge
## Practise Exercise 17

You have identified a list of potential drug targets from two different experimental screens for a specific disease.

However, there might be some redundancy between the lists, and you want to consolidate them and identify unique targets.

Given the following two lists of gene names (strings):


``` python
screen_A_targets = ['geneX', 'geneY', 'geneZ', 'geneM', 'geneP', 'geneX']
screen_B_targets = ['geneZ', 'geneQ', 'geneR', 'geneM', 'geneS', 'geneT']
```

1. Convert screen_A_targets and screen_B_targets into sets to automatically remove any duplicate gene names within each screen.

2. Find all the unique gene targets identified across both screens (i.e., genes that appear in either screen A or screen B, with no duplicates). Store this result in a variable called all_distinct_targets.

3. Find the gene targets that were identified by both screens (i.e., genes that appear in both screen A and screen B). Store this result in a variable called common_targets.

4. Display the contents of all_distinct_targets and common_targets.

::::::::::::::::: solution

1.
```
screen_A_targets = ['geneX', 'geneY', 'geneZ', 'geneM', 'geneP', 'geneX'] screen_B_targets = ['geneZ', 'geneQ', 'geneR', 'geneM', 'geneS', 'geneT']

set_A = set(screen_A_targets) set_B = set(screen_B_targets)
```

2. 
```
all_distinct_targets = set_A.union(set_B)
```

3.
```
common_targets = set_A.intersection(set_B)
```

4.
```
print(f"All distinct targets: {all_distinct_targets}") print(f"Common targets: {common_targets}")
```

:::::::::::::::::

:::::::::::::::::::::::::::::::
### Summary:

In this section, we’ve introduced the set — an unordered Python collection that stores only unique elements.

Key takeaways:
\- Sets do not preserve order and cannot be indexed or sliced.
\- They automatically remove duplicates from input sequences.
\- Sets are especially useful when the presence or absence of an item matters more than its position.
\- Their support for mathematical operations makes them ideal for comparing datasets — for example, identifying overlapping or exclusive values between gene lists.

:::::::::::::::::::::::::::::::::::: callout
## Interesting Fact
<p style='text-align: justify;'>
Graph theory was initially developed by the renowned Swiss mathematician and logician Leonhard Euler (1707 -- 1783). However graphs, in the sense discussed here, were introduced by the English mathematician James Joseph Sylvester (1814 -- 1897).
</p>

::::::::::::::::::::::::::::::::::::


## Exercises

##
:::::::::::::::::::::::::::::::::::::::: challenge

## End of chapter Exercises

1. We have

```
table = [[1, 2, 3], ['a', 'b'], [1.5, 'b', 4], [2]]
```

What is the length of <span style="color: rgb(32, 121, 77);">table</span> and why?

Store your answer in a variable and display it using <kbd>print()</kbd>.

2. Given the sequence for the Gamma (catalytic) subunit of the Protein Kinase A as:

```
human_pka_gamma = (
  'MAAPAAATAMGNAPAKKDTEQEESVNEFLAKARGDFLYRWGNPAQNTASSDQFERLRTLGMGSFGRVML'
  'VRHQETGGHYAMKILNKQKVVKMKQVEHILNEKRILQAIDFPFLVKLQFSFKDNSYLYLVMEYVPGGEM'
  'FSRLQRVGRFSEPHACFYAAQVVLAVQYLHSLDLIHRDLKPENLLIDQQGYLQVTDFGFAKRVKGRTWT'
  'LCGTPEYLAPEIILSKGYNKAVDWWALGVLIYEMAVGFPPFYADQPIQIYEKIVSGRVRFPSKLSSDLK'
  'DLLRSLLQVDLTKRFGNLRNGVGDIKNHKWFATTSWIAIYEKKVEAPFIPKYTGPGDASNFDDYEEEEL'
  'RISINEKCAKEFSEF'
  )
```

Using the sequence;

* Work out and display the number of Serine (<span style="color: rgb(32, 121, 77);">S</span>) residues.

* Work out and display the number of Threonine (<span style="color: rgb(32, 121, 77);">T</span>) residues.

* Calculate and display the total number of Serine and Threonine residues in the following format:

```
Serine: X
Threonine: X
```

* Create a nested array to represent the following table, and call it \texttt{residues}:

![](fig/nested_index.png)


3. Explain why in the previous question, we used the term *nested* instead of *two-dimensional* in reference to the array? Store your answer in a variable and display it using <kbd>print()</kbd>.

4. [Graph theory](https://en.wikipedia.org/wiki/Graph_theory) is a prime object of discrete mathematics utilised for the non-linear analyses of data. The theory is extensively used in systems biology, and is gaining momentum in bioinformatics too. In essence, a [graph](https://en.wikipedia.org/wiki/Graph_(discrete_mathematics)) is a structure that represents a set of object (nodes) and the connections between them (edges).

The aforementioned connections are described using a special binary (zero and one) matrix known as the [adjacency matrix](https://en.wikipedia.org/wiki/Adjacency_matrix). The elements of this matrix indicate whether or not a pair of nodes in the graph are adjacent to one another.

![](fig/adjacency_matrix.png)
where each row in the matrix represents a node of origin in the graph, and each column a node of destination:

![](fig/adjacency_matrix2.png)
If the graph maintains a connection (edge) between two nodes (*e.g.* between nodes <span style="color: rgb(32, 121, 77);">A</span> and <span style="color: rgb(32, 121, 77);">B</span> in the graph above), the corresponding value between those nodes would be \#1 in the matrix, and if there are no connections, the corresponding value would \#0.

Given the following graph:
![](fig/adjacency_matrix3.png)

Determine the adjacency matrix and implement it as a two-dimensional array in Python. Display the final array.

::::::::::::::::::::: solution

## Solutions will be provided once the submitted assignments are marked and returned.

:::::::::::::::::::::
::::::::::::::::::::::::::::::::::::::::


::::::::::::::::::::::::::::::::::::: keypoints

- ```lists``` and ```tuples``` are 2 types of arrays.
- An index is a unique reference to a specific value and Python uses a zero-based indexing system.
- ```lists``` are mutable because their contents can be modified.
- <kbd>slice()</kbd>, <kbd>.pop()</kbd>, <kbd>.index()</kbd>, <kbd>.remove()</kbd> and <kbd>.insert()</kbd> are some of the key functions used in mutable arrays.
- ```tuples``` are immutable, which means that their contents cannot be modified.

::::::::::::::::::::::::::::::::::::::::::::::::




[r-markdown]: https://rmarkdown.rstudio.com/
