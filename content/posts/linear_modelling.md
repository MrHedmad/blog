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
With "linear modelling" we refer to a category of statistical models that attempt to find links between a set of *predictors* $J = j_1, j_2, ..., j_p$ and a *response* $Y$. Note that we index the set of predictors with the letter $p$. In other words $p$ equals to the number of predictors.

Usually, we have a large number of these predictor-response sets - the *samples*: for instance, we may measure for $n$ people their gross income (our response), and other variables, such as age, gender and tenure (our set of *predictors*).

Another, simpler example often arises in biochemical laboratories: it is known that the concentration of an opaque substance dissolved in water is linearly related to its absorbance (Beer-Lambert's law)[^beer_lambert_law].
Often, we may wish to correlate the absorbance (our predictor) of a sample with the concentration of solute dissolved therein (our response).

[^beer_lambert_law]: The Beer-Lambert law states that light passing in a unit-length optical path through a solution with a single, uniformly-distributed opaque solute will be absorbed following the formula $A = \epsilon c$, where $A$ ($-$) is the absorbance value, $\epsilon$ ($M^{-1} cm^{-1}$) is the molar extinction coefficient for that solute species and $c$ is the species' concentration.
This correlation is clearly linear in $c$.

We can say that we have a set of $X$ samples: $X = x_1, x_2, ..., x_n$. Since we have each predictor measured in each sample, we have a *matrix* of $n x p$ dimensions:

$$
X = 
\begin{pmatrix}
x_{11} & x_{12} & \dots & x_{1p} \\\
x_{11} & x_{12} & \dots & x_{1p}\\\
\vdots & \vdots & \ddots & \vdots\\\
x_{n1} & x_{n2} & \dots & x_{np}\\\
\end{pmatrix}
$$

In this matrix, each row is a sample, with all the realizations of the predictor variables $J$.
In linear models, each row is also associated with its response $y_n$.
Imagine it being a spreadsheet, where you stored your experiment's data.

Linear models are *linear* since they always model the response as a **linear combination** of the predictors:

$$
y = f(x) = \beta_0 + \beta_1 x_1 + \beta_2 x_2 + \dots + \beta_p x_p
$$

Where every $\beta$ coefficient is a real numerical value that binds the predictors $X$ to the responses $Y$. These values are known as **coefficients** or **parameters**.

When there is only one predictor, so that the linear model formula is just $y = \beta_0 + \beta_1 x$, the model is said to be "simple".
When there is more than one predictor, we refer to the model as "multiple" or "multivariate".

It's valuable to imagine a simple linear model as a simple line through a 2D plane, that approximates well where the data points lie.
We can expand that when we have two predictors, for a total of 3 dimensions (2 predictors + the response variable):
the approximated space is now $3 - 1 = 2$ D, a plane in a 3D space.
This analogy goes on for any number of dimensions: the resulting *hyperplane*[^hyperplanes] is still linear, but spans more and more dimensions.

[^hyperplanes]: With the term "hyperplane" we just mean a plane that spans more than two dimensions.
A hyperplane passing three dimensions is just a regular plane. One that passes through a 2D space is a simple line.

{{< figure src="/blog/resources/images/posts/linear_modelling/advertising3D.png" style="border-radius: 8px; width: 300px; border:10px solid transparent; float:center" caption="A 2D linear model, representing a plane, is shown here. It models data regarding sales and bananas and lorem ipsum dolor sit amet" captionPosition=left >}}

### Applications of linear models
Linear models have a variety of applications:

- We may want to know if there is some relationship (or not) between the response and the predictors. For instance, if there is a link with a person's gender and their gross income.
- We may want to **predict** the response based on the predictors. It is often the case that the predictors are easy to measure (e.g. the absorbance of a sample), while the response is hard to measure (e.g. the concentration of the solute).
  The aim of such a model in to predict the (hard-to-measure and unknown) response of a new sample from the (easy-to-measure and known) predictors.
- If we have many predictors, we may want to know which subset of predictors are most closely related to the response. For example, we may gather information on the expression of thousands of genes, and wonder which are related to a certain illness and which are not.

This list is non-exhaustive. Many, many relationships can be modelled well through linear models. 



## Estimating the $\beta$ parameters

How do we estimate the 

## Expanding to non-linear relationships

## Measuring the quality of the fit

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
