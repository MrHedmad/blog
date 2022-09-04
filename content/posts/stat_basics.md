+++
title = "Basics of Statistics"
date = "2022-07-27"
description = "A gentle introduction to statistics, that gives you the tools to understand more about it. Also contains some useful reference books to keep in the shelf when you go about running t-tests and the like."
draft = true
toc = true
+++

In this post I am aiming to give the reader some basic statistics concepts that can be useful in everyday lab work. I also aim to clear up some misunderstandings that may come up from time to time when doing statistics work.

As with all of my posts, this is mainly written with regards to biologists, but the concepts are generally applicable, although the examples shown might not.

To write this post, I'm mainly referencing "The Art of Statistics", by David Spiegelhalter (Pelican, 2019, ISBN: 978-0-241-39863-0). I also follow his ingenious ask-a-question pattern for starting chapters.
For more in-depth coverage of statistical modelling, I reference "An Introduction to Statistical Learning", by G. James, D. Witten, T. Hastie and R. Tibshirani (Springer Texts, 2013, ISBN> 978-1-4614-7137-0). I also heavily use online resources for the most common concepts. I'll leave links scattered around when they are relevant.

I make heavy use of footnotes. I'm sorry about that. I use them to give more in-depth explanations that would burden the discussion too much. You can click on them to read them - they feature a handy "go back" arrow so you can get back in the main text quickly.

## Asking questions

Fundamentally, statistics is about answering big questions with little information. A few examples:
- **Determine some measurement**, such as the expression of a protein in a cell type;
- Test if something **has an effect**, for example a drug in a drug trial, or similarly find **differences** between two conditions[^drug_trial];
- **Model** some phenomenon, such as how absorbance is related to concentration;
- **Predict** something, such as tomorrow's stock market.
- Divide a number of things into **clusters**, such as dividing up tumors based on their gene expression signatures.

The question asked is of fundamental importance. From the question, we determine the best course of action to take to answer it. The question has an impact on the collection of the data, on the statistical method used to analyze it, and on the validity of our conclusions. It is therefore vital to ask the correct questions.

### Asking *good* questions

> How tall are people?

Such a question might be posed by some clothing company to tailor better clothes. It seems easy to answer: We could take a measure tape, and start walking around the city, asking people to be measured. Once we gather enough data, say $ 100 $ measurements, we stop and call it a day.

When we think about it, however, the question asked has some fundamental problems. First of all, we have to define what we mean by "tallness". It is probable that we mean the *average* height. But we might also be interested to determine what the most extreme heights are (i.e. the tallest and shortest persons), or the most *common* height. These are just some of the ways we can describe the shape of the **distribution** of our values. Formally:
- The **mean** or average height is $ \mu = \frac{1}{N}\sum{X}$, where $N$ is the number of people and $\sum{X}$ is the sum of all their heights;
- The most frequent height is the **mode** height[^mode_note];
- The **maximum** or **minimum** heights;

To get the *true* average height of all the people that live in Turin, we could *actually* measure every person living in Turin as of today, and then take the average. We would obtain the **population average**, $ \mu $. However, taking a measurement of all $ \approx 860'000$ people[^turin_pop] living in Turin might be hard. It is intuitive (and correct) to think that the average height of a *subset* of our population would estimate well the average height of the overall population.
Formally, we call the subset of the population that we measure to get our data the **sample**. We also say that the **sample average**, $ \bar{\mu} $, is the **best estimator** for the population average $ \mu $. We also refer to all estimations derived from the population as **parameters**, and all estimations derived from samples as **statistics**[^stat_vs_param]. 

You can read more about the best estimations of parameters from statistics in [this wikipedia article](https://en.wikipedia.org/wiki/Estimator)[^wikipedia_is_good]. Be careful however that it goes deeper than what we have discussed here.

We can refine our question:

> What is people's average height?

Next, we have to define what "people" are. If by "people" we mean the *whole world*, measuring only people around the city where we live might cause us to have a **non-representative** sample. Imagine we have to determine the average skin tone of all the people in the world. Measuring the skin tone only of people living in Norway (where everyone tends to be light-skinned), or Egypt (where people tend to be dark-skinned), might give us an incorrect representation of the whole world. We would have to travel around the continents, measuring some people from each region, and *then* take the average. 
Formally, our question has to specify the **population of interest**, the group of things that we are interested in.

Our final, good question might be:

> What is the average height of people living in Turin?

### Sampling - best practices

Assume we are lazy, and it's a hot day out due to climate change, so we only measure 10 people from our department (assuming it has air conditioning).
We would then think that $ \bar{\mu} \approx \mu$, but this would not really be the case. As you'd think, in this case $ \bar{\mu} $ might very well differ from $ \mu $, so we could be overestimating or underestimating it.

Intuitively, to get a good estimates from our sample regarding the population (such as $ \mu $ from $ \bar{\mu} $), we need two things:
1. Our sample is sufficiently large;
2. Our sample represents well the whole population;

These two requirements are intimately linked. Take the previous skin tone example: taking one million measurements from the city of London would result in an estimate as bad as taking just 5 measurements, but each from a different continent.

The mathematical best way to address point 2 is to choose from the population **random** items to sample. Assuming we had a list of all the people living in the Turin, our best sampling strategy would be to randomly select $ n $ people to sample. We would then have a representative sample.

The first point is harder to address properly. Sometimes, it is easy to choose a large $ n $. In theory, the larger $ n $ is the better. This is intuitive: the more people we sample, the better estimate we would make. However, most often having a large $ n $ is not practically possible. We might run into issues such as cost, or the invasiveness of the procedure. It turns out that there *is* a mathematical way to determine the optimal sample size to use. However, it requires to know a few more concepts, so I'll pick it up later. 

There are many sampling strategies and many opinions on what the best sample size is, given some constraints. In theory, random sampling with the mathematical approach of determining $ n $ that we will see later is the best approach. However, in reality we have practical constraints, so adapting our sampling strategy is often required (or even essential). Sampling strategies are a lengthy topic that would not fit here. To read more, consult, for example, [this paper](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC5029234/). A pubmed (or google) search for "sampling strategies" might also be useful.

### Sampling - worst pitfalls

As we said, how we sample the population is vitally important. And when something is vitally important, you know that it is easy to mess up. Here, i try to cover the most common mistakes when sampling in the biological context, and how to (try to) avoid them:

**"Convenience" sampling** In this sampling "strategy", the samples are made from the easiest-to-obtain items. For instance, we might measure only people who are near us (like in the previous example where we sampled only people in our air-conditioned department) or are cheapest to find and/or measure (like psychology students for behavioral tests). As we've already said, this is usually a bad idea.



## Approximating answers




## Errors and estimates


## Saying no to hypotheses


## Modelling effects


### To be or not to be parametric, that is the question


## Further reading

[^stat_vs_param]: To be clearer: $ \mu $ is a parameter, while $ \bar{\mu} $ is a statistic.
[^turin_pop]: Source - ISTAT, census of 2020.
[^mode_note]: The average and mode are most often the same, but not always. For example, there are some "bimodal" (two-modes) datasets, where values for a measurement are clustered near two far-away values. In this case, the mode (which will be in one of the two clusters of values) is different from the mean (which is between the two clusters). 
[^wikipedia_is_good]: Coincidentally, wikipedia is really good at dealing with statistics topics. So don't be afraid to consult it for additional information. This is both my and several of my statistics professors' opinion.
[^drug_trial]: In the case of a drug trial, we want to test if there is some difference between two conditions. For example, a group of people with high blood pressure is split in two: half get a treatment that should lower blood pressure, and the other half does not. Then, we would wish to test if the two groups have different blood pressure. In other words, if the drug had an effect on blood pressure. You might be wonder why we need statistics to do this: just measure the blood pressures, and see if the values differ. What statistics can do is tell us whether the differences we see are due to a real effect of the drug, or due to a random fluctuation in blood pressures we would normally expect. This is what we mean when we say that two things are "significantly different".