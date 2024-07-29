+++
title = "Linear Modelling"
date = ""
description = "An introduction to linear modelling, multivariate linear modelling, linear modelling cross-validation and linear model selection."
draft = true
toc = true
+++

## Introduction

In this post I'm going to go over the very basics of linear models, from their applications, to their implementation, to some practical examples.
Reading this short guide should give you enough information to "dip your toes" in the topic of linear modelling and to start building some simple models yourself.

This post is mostly based on the book "Introduction to Statistical learning - Second Edition" (ISBN: 978-1-0716-1417-4) by Gareth James, Daniela Witten, Trevor Hastie and Robert Tibshirani (Springer, 2021).

## What is linear modelling?
With "linear modelling" we refer to a category of statistical models that attempt to find links between a set of **predictors** $P = \\{ p_1, p_2, ..., p_{|P|} \\}$ and a **response** $Y$.

> We refer to the set of predictors with the letter $P$.
> In other words, $|P|$ equals to the number of predictors.
> We refer with $p$ to some *specific* predictor, like $j_2$.

Usually, we have a large number of these predictor-response sets - the **samples**.
For instance, we may measure for $|N|$ people their gross income (our response), and other variables, such as age, gender and tenure (our set of predictors).

Another example often arises in biochemical laboratories: it is known that the concentration of an opaque substance dissolved in water is linearly related to its absorbance (Beer-Lambert's law)[^beer_lambert_law].
Often, we may wish to correlate the absorbance (our predictor) of a sample with the concentration of solute dissolved therein (our response).

We can say that we have a set of $N$ samples:
$$
N = \\{
  \\{ p_{11}, p_{12}, \cdots , p_{1|P|} \\},
  \\{ p_{21}, p_{22}, \cdots, p_{2|P|} \\},
  \cdots,
  \\{ p_{N1}, p_{N2}, \cdots, p_{|N||P|} \\}
\\}
$$

> $N$ is the set of all the predictor sets.
> $|N|$ is the total number of predictor sets, and since we have a set of predictors per response, $|N| = |P|$.
> $n$ is one *specific* predictor set.

[^beer_lambert_law]: The Beer-Lambert law states that light passing in a unit-length optical path through a solution with a single, uniformly-distributed opaque solute will be absorbed following the formula $A = \epsilon c$, where $A$ ($-$) is the absorbance value, $\epsilon$ ($M^{-1} cm^{-1}$) is the molar extinction coefficient for that solute species and $c$ is the species' concentration.
This correlation is clearly linear in $c$.

Since every predictor set $n$ is of the same size (each has $|P|$ predictors), and we have $|N|$ predictors, we have a *matrix* of $|N| x |P|$ dimensions:

$$
  X =
  \begin{bmatrix}
    p_{11} & p_{12} & \dots & p_{1P} \\\
    p_{21} & p_{22} & \dots & p_{2P} \\\
    \vdots & \vdots & \ddots & \vdots \\\
    p_{N1} & p_{N2} & \dots & p_{NP} \\\
  \end{bmatrix}
$$

In this matrix, each row ($n$) is a sample, with all the realizations of the predictor variables $P$.
In linear models, each row is also associated with its response $y_n$.
This is, in essence, a table of values, like one would record during an experiment.

We can see the responses $Y$ as a column vector:

$$
  Y =
    \begin{bmatrix}
    y_1 \\\
    y_2 \\\
    \vdots \\\
    y_|N| \\\
  \end{bmatrix}
$$

When modelling, we wish to find some function $f(n)$ that can **approximate well** the corresponding response $y$.
We have different types of modelling based on the nature that we give to the function $f()$.

Linear models are *linear* since they always model the response as a **linear combination** (read: sum) of the predictors.
This simply means that $f(n)$ is a polynomial sum:

$$
y_n \approx f(n) \approx \beta_0 + \beta_1 \cdot p_{n1} + \beta_2 \cdot p_{n2} + \dots + \beta_{|P|} \cdot p_{n|P|}
$$

Where every $\beta$ coefficient is a real numerical value that binds the predictors $X$ to the responses $Y$.
These $\beta$ values are known as **coefficients** or **parameters**.
These $\beta$ predictors make it so that the sum $\beta_0 + \beta_1 \cdot p_{n1} + \beta_2 \cdot p_{n2} + \dots + \beta_{|P|} \cdot p_{n|P|}$ is *as close as possible* to the true value $y_n$, for every combination of $n$ in $N$ and the respective $y$ in $Y$.

When there is only one predictor ($P = 1$), so that the linear model formula is just $y_n = \beta_0 + \beta_1 x_n$, the model is said to be "simple".
When there is more than one predictor, we refer to the model as "multiple" or "multivariate".

> Take a moment to absorb the above concepts.
> In summary:
> - We want to take a set of numbers, **predictors**, to predict just one other number per set, a **response**.
> - We do this by *summing all numbers in each set*, multiplying them by different **coefficients** $\beta$ that make this sum as close as the response as possible.
> - The set of $\beta$ coefficients is **the same** for every $n$/$y$ pair.

It's useful to imagine a simple linear model as a line through a 2D plane, that approximates well where the data points lie.
We can expand that when we have two predictors $P$, for a total of 3 dimensions (2 predictors + the response variable):
the approximated space is now $3 - 1 = 2$ dimensional: a plane in a 3D space.
This analogy goes on for any number of dimensions: the resulting *hyperplane*[^hyperplanes] is still linear, but spans more and more dimensions.

[^hyperplanes]: With the term "hyperplane" we just mean a plane that spans more than two dimensions.
A hyperplane passing three dimensions is just a regular plane. One that passes through a 2D space is a simple line.

{{< figure
  src="/blog/resources/images/posts/linear_modelling/advertising3D.png"
  style="border-radius: 8px; width: 500px; border:10px solid transparent"
  position="center"
  caption="A 2D linear model, representing a plane, is shown here." captionPosition=left
>}}

### Applications of linear models
Linear models have a variety of applications:

- We may want to know if there is some relationship (or not) between the response and the predictors. For instance, if there is a link with a person's gender and their gross income.
- We may want to **predict** the response based on the predictors. It is often the case that the predictors are easy to measure (e.g. the absorbance of a sample), while the response is hard to measure (e.g. the concentration of the solute).
  The aim of such a model in to predict the (hard-to-measure and unknown) response of a new sample from the (easy-to-measure and known) predictors.
- If we have many predictors, we may want to know which subset of predictors are most closely related to the response. For example, we may gather information on the expression of thousands of genes, and wonder which are related to a certain illness and which are not.

This list is non-exhaustive. Many, many relationships can be modelled well through linear models.

## Estimating the $\beta$ parameters

How do we estimate the $\beta$ parameters?
Notice how *the same $\beta$ parameters are used for all the predictor sets $n$*.
This means that we have to take into consideration all the input sets $n$ to compute the best set of $\beta$ coefficients that we can to have $y_n \approx f(n)$ be true for all possible $n \in N$.

It would be useful to convert the poorly defined relationship $y_n \approx f(n)$ to something more precise.
We can do this by introducing the simbol $e$.
$e$ is some unknown, unquantifiable *error* value, which we define as $e = f(n) - y_n$.
With $e$, we can "correct" our previous definition to be perfectly exact: $y_n  = f(n) + e$.

> Note: $e$ is different for every set $n$, but we don't talk about $e_n$ since we cannot calculate such a value given $n$. If we could, we wouldn't need it, as we could simply assimilate it inside $f(n)$. Therefore, imagine $e$ as a purely "magical" value, for now.

We can leverage $e$ - or better, an estimate of $e$ - to compute our $\beta$ parameters.
Assume a set of $\beta$ parameters, $\beta_i$, with arbitrary values (e.g. all $\beta$ values set to $1$).

:: TODO ::

- ~ Also include how to estimate the quality of the fit, since it relates closely to the error

## The bias-variance trade-off

## Subset selection and shrinkage

## Finding the sweet spot with cross-validation

## The curse of dimensionality

# Applications in R

## Sample data

## A simple multivariate linear model

## Checking the model quality

## Interaction terms

## Cross-validating our model

## Variable selection

## Visualization of linear model data
