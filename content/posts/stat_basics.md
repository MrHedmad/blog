+++
title = "Stat Basics"
date = "2022-07-27"
description = "A gentle introduction to statistics, that gives you the tools to understand more about it. Also contains some useful reference books to keep in the shelf when you go about running t-tests and the like."
draft = true
toc = true
+++

In this post I aim to give the reader some basic statistics concepts that can be useful in everyday lab work. I also aim to clear up some misunderstandings that may come up from time to time when doing statistics work.

As with all of my posts, it is written with regards to biologists, but the concepts are applicable to a more general setting, although the examples shown might not.

To write this post, I'm mainly referencing "The Art of Statistics", by David Spiegelhalter (Pelican, 2019, ISBN: 978-0-241-39863-0). I also follow his ingenious ask-a-question pattern for starting chapters.
For more in-depth coverage of statistical modelling, I reference "An Introduction to Statistical Learning", by G. James, D. Witten, T. Hastie and R. Tibshirani (Springer Texts, 2013, ISBN> 978-1-4614-7137-0). I also heavily use online resources for the most common concepts. I'll leave links scattered around when they are relevant.

You will notice a ton of footnotes. I'm sorry about that. I use them to give more in-depth explanations that would burden the discussion too much. You can click on them to read them - they feature a handy "go back" arrow so you can get back in the main text quickly.

## Asking questions

Fundamentally, statistics is about answering big questions with little information. A few examples:
- **Determine some measurement**, such as the expression of a protein in a cell type;
- Test if something **has an effect**, for example a drug in a drug trial, or similarly find **differences** between two conditions[^drug_trial];
- **Model** some phenomenon, such as how absorbance is related to concentration;
- **Predict** something, such as tomorrow's stock market.
- Divide a number of things into **clusters**, such as dividing up tumors based on their gene expression signatures.

The question asked is of **fundamental importance**. From the question, we determine the best course of action to take to answer it. The question has an impact on the collection of the data, on the statistical method used to analyze it, and on the validity of our conclusions. It is therefore vital to ask the correct questions.

### Asking *good* questions

> How tall are people?

Such a question might be posed by some clothing company to tailor better clothes. It seems easy to answer: We could take a measure tape, and start walking around the city, asking people to be measured. Once we gather enough data, say $ 100 $ measurements, we stop and call it a day.

When we think about it, however, the question asked has some fundamental problems. First of all, we have to define what we mean by "tallness". It is probable that we mean the *average* height. But we might also be interested to determine what the most extreme heights are (i.e. the tallest and shortest persons), or the most *common* height. These are just some of the ways we can describe the shape of the **distribution** of our values. Formally:
- The **mean** or average height is $ \mu = \frac{1}{N}\sum{X}$, where $N$ is the number of people and $\sum{X}$ is the sum of all their heights;
- The most frequent height is the **mode** height[^mode_note];
- Sorting the values from smallest to highest, the value in the middle (or the average of the two middle values, in the case of an even number of values) is the **median** value[^median_value].
- The **maximum** or **minimum** heights mark the distribution's **range**;

To get the *true* average height of all the people that live in Turin, we could *actually* measure every person living in Turin as of today, and then take the average. We would obtain the **population average**, $ \mu $. However, taking measurements of all $ \approx 860'000$ people[^turin_pop] living in Turin might be hard. It is intuitive (and correct) to think that the average height of a *subset* of our population could estimate well the average height of the overall population.
Formally, we call the subset of the population that we measure to get our data the **sample**[^sample_vs_sampled_item]. We also say that the **sample average**, $ \bar{\mu} $, is the **best estimator** for the population average $ \mu $. We also refer to all true values of the population as **parameters**, and all estimations derived from samples as **statistics**[^stat_vs_param]. 

You can read more about the best estimations of parameters from statistics in [this wikipedia article](https://en.wikipedia.org/wiki/Estimator)[^wikipedia_is_good]. Be careful however that it goes deeper than what we have discussed here.

We can refine our question:

> What is people's average height?

Next, we have to define what "people" are. If by "people" we mean the *whole world*, measuring only people around the city where we live might cause us to have a **non-representative** sample. Imagine we have to determine the average skin tone of all the people in the world. Measuring the skin tone only of people living in Norway (where everyone tends to be light-skinned), or Egypt (where people tend to be dark-skinned), might give us an incorrect representation of the whole world. We would have to travel around the continents, measuring some people from each region, and *then* take the average. 
Formally, our question has to specify the **population of interest**, the group of things that we are interested in.

Our final, good question might be:

> What is the average height of people living in Turin?

### Sampling - best practices

Assume we are lazy, and it's an extremely hot day out due to climate change, so we only measure 10 people from our department (assuming it has air conditioning).
We would then think that $ \bar{\mu} \approx \mu$, but this would not really be the case. As you'd think, with this sample $ \bar{\mu} $ might very well differ from $ \mu $: we could be overestimating or underestimating it.

Intuitively, to get a good estimates from our sample regarding the population (such as $ \mu $ from $ \bar{\mu} $), we need two things:
1. Our sample is sufficiently large;
2. Our sample represents well the whole population;

These two requirements are intimately linked. Take the previous skin tone example: taking one million measurements from the city of Cairo would result in an estimate as bad as taking just 5 measurements, but each from a different continent.

The mathematical best way to address point 2 is to choose from the population **random** items to sample. Assuming we had a list of all the people living in the Turin, our best sampling strategy would be to randomly select $ n $ people to sample. We would then have a **representative sample** of the population of interest.

The first point is harder to address properly. Sometimes, it is easy to choose a large $ n $. In theory, the larger $ n $ is the better. This is intuitive: the more independent people[^not_people] we sample, the better estimate we would make. However, most often having a large $ n $ is not practically possible. We might run into issues such as cost, or the invasiveness of the procedure. It turns out that there *is* a mathematical way to determine the optimal sample size to use. However, it requires to know a few more concepts, so I'll pick it up later. 

There are many sampling strategies and many opinions on what the best sample size is, given some constraints. In theory, random sampling with the mathematical approach of determining $ n $ that we will see later is the best approach. However, in reality we have practical constraints, so adapting our sampling strategy is often required (or even essential). Sampling strategies are a lengthy topic that would not fit here. To read more, consult, for example, [this paper](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC5029234/). A PubMed (or google) search for "sampling strategies" might also be useful.

### Sampling - worst pitfalls

As we said, how we sample the population is vitally important. And when something is vitally important, you know that it is easy to mess up. The most common of such mistakes, and the easiest to miss, is **pseudoreplication**.

Pseudoreplication occurs when we consider as true, independent measurements (i.e. the height measurements of our previous example)[^biological_replicates] measures that instead are not (completely) related to what we actually want to measure, or are not independent from one another.

For instance, we might measure the movement of 100 cells in a migration experiment. However, we monitored 10 different cells from 10 isolated wells. In this case, the 10 cells from the same well are related to one another: they were cultured (and treated) together, and we cannot exclude that they influence each other. So, considering all 100 measurements in our statistical calculation would be an error: not all of the values are independent of one another.
The correct way to handle this is to consider the *wells* as our entity of interest: by averaging the measurements of the 10 cells in each well, and using the resulting 10 values (one per well) in our analysis, we would have truly independent samples[^what_is_unrelated].

The topic of pseudoreplication is so vast that it would not fit here. In recent times, it has been found that most studies in the biologic and medical fields are plagued by pseudoreplicated measures, and thus their conclusions are not robust or have to be rejected outright. Please refer to [this paper](https://journals.plos.org/plosbiology/article?id=10.1371/journal.pbio.2005282) for a solid discussion of the topic.

It is often the case that **the wrong biological entity is sampled** based on our question of interest. Let's say that our question is *"Does lung cancer grow faster that breast cancer?"*. In this case, a researches could take one lung cancer cell line and one breast cell line and record their growth rates. Say that they try to be diligent, and gather 100 independently-run measurements (such as from different wells) for each cell line. However, even with a lot of high-quality data, the experiment **cannot** answer the question of interest. There might be differences between these two cell lines, but this might not be the case for *all* other cell lines, and even less can be said for differences in real cancers[^cell_lines_vs_real]. The researcher sampled the wrong population: their data can only confirm that **those two cell lines** grow at different rates (or don't). The original population of interest is, instead, all the lung and breast cancers, which might be modelled well by using many different cell lines of those two cancer types.


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
[^median_value]: For example, the median of the values [$ 15 $, $ 22 $, $ 39 $, $ 40 $] is $ (22 + 39) / 2 = 30.5$. For reference, the mean is $ 29 $ instead.
[^not_people]: Or mice, or cells, or culture wells, or whatever it is we are interested about.
[^cell_lines_vs_real]: We are running on the assumption that cell lines react and behave like real cancer samples from real patients (i.e. "primary" cell lines). This might not be the case, but much medical research is built on this assumption.
[^biological_replicates]: In the biological setting, these kinds of items are referred to "biological replicates", while repeated measurements of the same 'biological sample' are "technical replicates". Considering technical replicates 
[^sample_vs_sampled_item]: Confusingly, it is often the case tha the word "sample" means both the collection of items measured for a certain study, and the single items themselves (e.g. "My experiment consists in 12 samples"). The more correct term would be 'measurement'. 
[^what_is_unrelated]: The attentive reader might catch that the example I provided is flawed: The cells in the 10 wells are probably derived from the same cell line. They were also probably treated in parallel, and cultured together in the same space. Can we truly say that they are unrelated?
By extension, different people living in the same area (Turin) might influence each other (causing an effect in their height).
It turns out that there is a way to define "independence". See [this wikipedia article](https://en.wikipedia.org/wiki/Independence_(probability_theory)). In layman's terms, if knowing the realization of one of the variables does not affect the probability distribution of another variable (e.g. between the two wells), the variables are said to be independent.
It's harder to determine, however, true independence d
