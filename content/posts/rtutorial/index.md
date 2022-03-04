+++
title = "Into R, face first"
description = "A short hands-on R tutorial for beginners"
draft = true
toc = true
+++

**NOTE ON GUIDE FORMATTING**
- Comments that exceed 80 characters per line are usually stopped with a `-`
  and then resumed at the next line.

> If you are a complete beginner, I explain some basic concepts in another post,
[Intro to Programming for biologists]( {{< ref "/content/posts/programming_for_biologists/index.md" >}} )

## What is R?
R is a high-level, interpreted programming language, mostly used in statistical
computing and for plotting data. It is the spiritual successor to 
[the S programming language](https://en.wikipedia.org/wiki/S_(programming_language)).
R is part of the [GNU] project, an is thereby free and open-source.

R is powerful when reading and manipulating numerical data, and provides (yet)
unmatched capabilities for modelling and generating graphics for your data,
thanks to the `ggplot2` library.

## Installing R and RStudio

## Using R
### R in the console
On a command prompt, open the R console using the command "R".

The console allows for interactive use of R.
The default console prompt is ">". If a command is detected to be incomplete,
a "+" prompt will appear, until the command is completed.
Esc escapes from the + prompt. 

```r
my.variable <- list(c("I'm some text"), c(1, 2, 3, 4))
my.variable
mean(my.variable[[2]]) -> my.mean ; my.mean # Notice the semicolon
```
Running more than one command per line is allowed, if they are separated 
with a semicolon ";":

```r
print("Hello"); print("World")
```
Spaces are completely ignored by R. Help is available for most functions.
You can get help by using `?` or `??`. `?` looks up help for a specific
function, while `??` searches for the word in all the help pages:
```r
?median
??logarithm
```

### The working directory
The workspace (or working directory, WD) is where R stores the data it creates,
and the default location where it looks for files.
To change the WD use `wd()`

```r
setwd("C:/Users/Myself/RWorkspace")
```

> Note the use of forward slashes instead of backslashes.

To get the current WD use `getwd`:
```r
getwd()
```

R stores information like variables created and command history at the end of
the session in a file called `.RData` and `.RHistory`, saved in the WD. They will
(by default), be loaded back to restore the working environment as it was when
the R session was ended.

> Personally, this is the worst feature of R, as different sessions pollute one
> another. This "feature" can be disabled easily enough by starting R with the
> `--vanilla` flag, or by setting the relevant options in RStudio.

In RStudio, to change the default working directory, go to:
`Tools > Global Options > General` and change the default path.

R is case-sensitive. A and a are different chracters.
```r
a <- c("This is the variable a") ; a
A <- c("This is a new variable A") ; A
```
For all intents and purposes, A and a are two different objects.

## Functions and assignments

A function is a set of directions that R follows to get a result.
A function can be called with the parentheses operator `()`, for instance: 
`FUN_NAME(arg1, arg2, arg3, ...)`. `FUN_NAME` is the name of the function,
while `arg1, ...` are its arguments. A function *RETURNS* its result after it
is run.
```r
rep(x = 1:3, times = 4)
```
In this case, we use the function named rep, which repeats its `x` argument
a `times` times. 

We can omit the name of the arguments if we follow the order of the arguments,
as shown in the function's help page:
```r
?rep() # We see that the default order is rep(x, times)

rep(x = 1:3, times = 3) # These three are the same
rep(1:3, 3)             # 
rep(times = 3, x = 1:3) # We can change the order of the args, if we specify them.
```
Commands can be nested inside each other. R will run them in the correct order
that is, from the inner-most to the outer-most.
```
sum( rep(1:5, 5) ) # This runs rep(), then sum() on whatever rep() returned.
```

We can ***assign*** what a function returns to a variable for storage.
After we assign, calling the variable will be the same of running the function.
The assignment operator is `<-` (or `->`). `=` is the same as `<-`, but `<-` is
preferred.
```r
x <- rep(1:5, 5) # Assignments don't return anything in the console (if working)
sum(x)           # This is the same as sum( rep(1:5, 5) ) from before.

x # Just writing the variable name will print its contents out.
  # Similarly to what `print(x)` would do.
```

## Objects
All variables (called "objects") can be listed with objects() or ls()
```r
objects()
```
Everything in R, even what is printed with `objects()`, is an object.
If an object is not assigned as it is created, it is printed out and then lost.

We can remove assigned objects using `rm()`:
```r
x <- c("Banana", "Papaya", "Guava") 
y <- c(1, 2, 3, 4, 5)

objects()

rm("x") # This will delete (PERMANENTLY) the object x from the environment.

objects()
```
Objects have a set of characteristics:
`mode()` shows us what type of data is inside the object.
This can be `numeric`, `logical`, `character`...
```r
mode(y) # Since y is a set of numbers, this returns "numeric".
```
As we will see later, we can set additional attributes to out objects.
The names() is a type of attribute. We can list user-set attributes with:
```r
attributes(y) # Since we set none, it returns NULL
```
You can get what type of data structure (more or less) an object is:
```r
class(y) # This returns "numeric"
class(data.frame(y)) # This returns "data.frame" as data.frame(y) is a data frame.
```
Functions are objects too! This means that they are assigned to variables an can
be deleted like any other object.

