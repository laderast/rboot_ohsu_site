# Part 1: Functions and Objects

## Learning Objectives

By the end of this session, you should be able to:

1. **Work** within the RStudio interface to **run** R code in an RMarkdown notebook
2. **Understand** basic R syntax to **use** functions and **assign** values to objects
3. **Create** and **manipulate** vectors and **understand** how R deals with missing data 


## An Intro to R/RStudio

[Tour of R and R Notebooks]

`Help -> Cheetsheets -> RStudio IDE cheat sheet`

### Code Blocks

Now that we have our notebook open, we're ready to start.

First thing of all, is the grey box below.

[Play button]


```r
# basic math
4 + 5 
```

```
## [1] 9
```

Let's learn how to read this code block. Everything that starts with a `#` is called a *comment* and is not code that runs. It is useful for making notes for youself

Below it is the actual code.

Try this one out. It's the same code as above, but with no spaces. Does it still run?


```r
# same code as above, without spaces
4+5
```

```
## [1] 9
```

### Using Functions

R includes functions for other types of math:


```r
# using a function: rounding numbers
round(3.14)
```

```
## [1] 3
```

[function names and arguments, syntax]


```r
# using a function with more arguments
round(3.14, digits = 1)
```

```
## [1] 3.1
```

[getting help]


```r
?round
```

[documentation and arguments]


```r
# can switch order of arguments
round(digits = 1, x = 3.14)
```

```
## [1] 3.1
```

> You may notice that boxes pop up as you type. 
> These represent RStudio's attempts to guess what you're typing and share additional options.

### **Challenge 1:** 

What does the function `hist` do? What are its main arguments? How did you determine this?



### Assigning objects

[objects and variables]


```r
# assigning value to an object
weight_kg <- 55
```

[assignment operator, object naming conventions]

Now that the object has been assigned,
we can reference that object by executing its name:


```r
# recall object
weight_kg
```

```
## [1] 55
```

[using a variable]


```r
# multiple an object (convert kg to lb)
2.2 * weight_kg
```

```
## [1] 121
```

[assigning a new variable]


```r
# assign weight conversion to object
weight_lb <- 2.2 * weight_kg
```

[environment panel]


```r
# reassign new value to an object
weight_kg <- 100
```

[changing variable values]

[objects that use other objects don't change]

> You can think of the names of objects like sticky notes.
> You have the option to place the sticky note (name) on any value you choose.
> You can pick up the sticky note and place it on another value,
> but you need to explicitly tell R when you want values assigned to certain objects.


```r
# remove object
remove(weight_lb) 
```

[removing objects]

> You can clear the entire environment using the button at the top of the Environment panel
> with a picture of a broom. 
> This may seem extreme, 
> but don't worry! 
> We can re-create all the work we've already done by executing each line of code again.


### **Challenge 2:** 

What is the value of each item at each step? (Hint, you can see the value of an object by typing in the name of the object, such as with the `mass` line below.)


```r
mass <- 47.5            # 1. mass?
mass
```

```
## [1] 47.5
```

```r
width  <- 122             # 2. width?
mass <- mass * 2.0      # 3. mass?
width  <- width - 20        #4.  width?
mass_index <- mass/width  # 5. mass_index?
```


Make your answers here:

1.
2.
3.
4.
5.


## Vectors

[creating vectors]
[c is for combine]


```r
# assign vector
ages <- c(50, 55, 60, 65) 
# recall vector
ages
```

```
## [1] 50 55 60 65
```

[learning things about vectors]


```r
# how many things are in object?
length(ages)
```

```
## [1] 4
```



```r
# what type of object?
class(ages)
```

```
## [1] "numeric"
```



```r
# performing functions with vectors
mean(ages)
```

```
## [1] 57.5
```

```r
range(ages)
```

```
## [1] 50 65
```

[characters]


```r
# vector of body parts
organs <- c("lung", "prostate", "breast")
```

In this case,
each word is encased in quotation marks,
indicating these are character data,
rather than object names.

### **Challenge 3:** 

Please answer the following questions about `organs`:

1. How many values are in `organs`?
2.  What type of data is `organs`?
3.  get overview of `organs`

Answers here: 

1.
2.
3.

### Data types and Vectors

- **character**: sometimes referred to as string data, tend to be surrounded by quotes
- **numeric**: real or decimal numbers, sometimes referred to as "double"
- integer: a subset of numeric in which numbers are stored as integers
- **logical**: Boolean data (TRUE and FALSE)
- complex: complex numbers with real and imaginary parts (e.g., 1 + 4i)
- raw: bytes of data (machine readable, but not human readable)



### **Challenge 4:** 

R tends to handle interpreting data types in the background of most operations.

The following code is designed to cause some unexpected results in R.

What is unusual about each of the following objects?


```r
num_char <- c(1, 2, 3, "a")
num_logical <- c(1, 2, 3, TRUE)
char_logical <- c("a", "b", "c", TRUE)
tricky <- c(1, 2, 3, "4")
```


### Manipulating vectors


```r
# add a value to end of vector
ages <- c(ages, 90) 
```


```r
# add value at the beginning
ages <- c(30, ages)
```


```r
# extracting second value
organs[2] 
```

```
## [1] "prostate"
```


```r
# excluding second value
organs[-2] 
```

```
## [1] "lung"   "breast"
```


```r
# extracting first and third values
organs[c(1, 3)] 
```

```
## [1] "lung"   "breast"
```




### Missing data


```r
# create a vector with missing data
heights <- c(2, 4, 4, NA, 6)
```

[NA is not a character]


```r
# calculate mean and max on vector with missing data
mean(heights)
```

```
## [1] NA
```

```r
max(heights)
```

```
## [1] NA
```

[ugh. na strikes again!]


```r
# add argument to remove NA
mean(heights, na.rm = TRUE)
```

```
## [1] 4
```

```r
max(heights, na.rm = TRUE)
```

```
## [1] 6
```


```r
# remove incomplete cases
na.omit(heights) 
```

```
## [1] 2 4 4 6
## attr(,"na.action")
## [1] 4
## attr(,"class")
## [1] "omit"
```

### **Challenge:** 

Complete the following tasks after creating this vector (Note: there are multiple solutions):
(solutions [here](solutions/class1_solutions.R))

1. Remove NAs on `more_heights` (assign it to the object `more_heights_complete`)
2. Calculate the `median()` of `more_heights_complete`


```r
# create vector
more_heights <- c(63, 69, 60, 65, NA, 68, 61, 70, 61, 59, 64, 69, 63, 63, NA, 72, 65, 64, 70, 63, 65)
# remove NAs

# calculate the median
```

## Wrapping up

[R/Rstudio]
[objects]
[data types]




## Assignment 


1.  Object manipulation

Create an object called `agge` that contains your age in years. Then
reassign the object to a new object called `age` (e.g., correct the typo). Then remove the previous object from your environment and then calculate your age in days


```r
#create agge object

#reassign agge value to age

#remove agge object

#Use math to calculate your age in days
```


2.  Vector manipulation (character data):

Create a object called `buildings` representing a vector that contains four names of buildings on OHSU's campus, including the building where you work (here's a reference: https://www.ohsu.edu/visit/maps). 

Add `Portland, Oregon` to the beginning of the vector, and `Phys Plant` to the end of the vector

subset the vector to show only the building in which you work.


```r
#create buildings object
buildings <- c()

#Add "Portland, Oregon" to the beginning of buildings

#Add "Phys Plant" to the end of buildings

#subset buildings to show only your building
buildings[]
```

```
## NULL
```


3. Vector manipulation (numerical data):

The following vector represents the number of vacation days possessed by various employees.

How many employees are represented in the vector?

How many vacation days total?


```r
vacation_days <- c(5, 7, 20, 1, 0, 0, 12, 4, 2, 2, 2, 4, 5, 6, 7, 10, 4)

#how many employees are represented in the vector?

#how many vacation days total?
```


## Submitting your homework

Submit your `part1-FIRSTNAME-LASTNAME.nb.html` file in Sakai. To download it, click on the `More` gear icon, and click **Export** to download it to your computer.
