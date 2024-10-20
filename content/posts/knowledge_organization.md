+++
title = "Knowledge Organization"
date = "2024-10-20"
description = "A collection of methods, strategies and tools on the collection, organization and utilization of personal knowledge."
draft = true
toc = true
+++

This post aims to be a collection of all of my notes, thoughts and experiences regarding the need of organizing knowledge for personal use.
The strategies of organizing knowledge are known under many terms, such as [personal knowledge management](https://en.wikipedia.org/wiki/Personal_knowledge_management), [personal information management](https://en.wikipedia.org/wiki/Personal_information_management), or more generally [information management](https://en.wikipedia.org/wiki/Information_management).

I find all the wikipedia material above very confusing, so I'll invent my own definition for this phenomenon, one I'll use throughout this post.

> "Knowledge Management" is any strategy that an individual might use to deal with the complexity of information in their daily lives.

I hope this term is general enough to fit all the concepts I'll touch in this piece.

## Ok, but what's "Knowledge"?

I'm glad you asked. Defining what "knowledge" or "information" is is quite hard, and philosophers have chipped away at the problem since philosophers existed.
Intuitively, knowledge encompasses basically anything: from shopping lists to bibliographic indexes, from a binder with all important receipts to a large wikipedia-style knowledgebase of all the processes in a company.

I don't want to give a universal definition for what knowledge is, but for the scope of this post, we can say that Knowledge (or interchangeably "information") is basically any concept that can be conceived, as long as it is cohesive and meaningful.

This definition should be sufficiently broad to cover more or less anything that you can think of, from simple assertions like "My name is Luca" to more complicated ideas, like this blog post.

Dealing with information is a key aspect of any system that be considered to be alive.
Without information we would not be alive - constantly dealing with information, big or small, is a fundamental aspect of any living system.
Bacteria, for example, sense the chemical composition of the medium in which they live and make choices, e.g., on where to swim towards[^chemotaxis].
Animals make decisions based on their surrouding environments.

Arguably, humans have based their evolutionary success on the keen management, processing and usage of information.
Our big brains make us adept at processing information, so much so that many authors say that "we are *bombarded* with information".
I think *bombarded* is a misnomer; we are "bombarded" with information in the same way that [a young Clark Kent is bombarded by their superpowers](https://www.youtube.com/watch?v=VcdFURryKjA), but in stark contrast to Superman, we are dealing with this information from the moment we are born.

## The flesh is weak
The brain is not able to conserve every bit of information that we come across, and for good reason: the majority of information that we process daily is useless (the fact that the train was five minutes late, that the color of the blouse of the person sitting next to me was blue, etc...), and so our brains silently delete it either immediately or soon after.

While this is a desirable trait, we want to retain some information.
Biologically, we are hard wired to keenly recall information regarding bad things that have occoured to us[^negbias], to avoid them next time.
We also recall that doing something has resulted in good things, like receiving food (something something [Pavlov](https://en.wikipedia.org/wiki/Classical_conditioning)).
However, when humans have started to do *knowledge work*[^kwork], we quickly realized that the fleshy brain is excellent at processing information but very bad at collecting and storing it.
For this reason, we delegate those tasks that our brains are bad at doing (collecting, recalling, arranging) to phisical objects (i.e. written words on a notepad).
This process is called [*externalization*](https://en.wikipedia.org/wiki/External_memory_(psychology)).

We externalize both our memory (taking notes when attending a lecture or a meeting) and when processing large volumes of data (doing a calculation on paper, or brainstorming on post-it notes).
Whenever we are dealing with a ton of information, as is routine when doing knowledge work, we have the need to externalize some of that work.

## Managing Knowledge

Here we can talk about what "management" of knowledge is.
Knowledge management strategies are simply those strategies that we enact when we externalize information processing.

As you'd expect, there are many areas where externalization is useful or even essential when doing knowledge work:
- Collecting information (externalizing memory);
- Finding relevant information (externalizing recalling);
- Structuring information and relating it with itself (externalizing thinking);
- Presenting information in a structured way to convey it to others (externalizing talking, or writing).

In this post I hope to cover the many strategies peoples have used over the years when dealing with each of these areas.

> One of the ways we externalise, if not the only one, is through writing. This is fairly obvious, but I wanted to highlight it here.
> Writing is "thinking with your hand", as many authors have said.

At their core, all of these systems deal with *items*.
An item can be any piece of information: a TO-DO task, a short assertion, notes regarding a lecture, with in theory no limit to complexity or lenght.
As these knowledge items grow larger and larger, they tend to become unwieldy to access.
Imagine a single note containing a whole book chapter.
The time it would take to retrieve a specific information from the large amount of knowledge inside a book chapter is very large: you need to read the whole chapter again.

This is why many methods call for *atomic* items.
The word "atomic" is a bit of a misnomer, as the items need not be physically short, but semantically short.
An atomic item is one that contains a single, cohesive, useful piece of information.
Here is where the "personal" in "personal knowledge system" comes in: the definition of "single, cohesive, useful item" is deeply personal.
It might be the case that a single assertion is useful for you ("My name is Luca"), and that could be an item. Other times, more structured discussions of materials, collating together a variety of topics are "single, cohesive and useful" for you, and they would make up an "atomic" note.
For the "unwieldiness" of large items, people generally tend to write shorter atomic items, but the short lenght is a byproduct of the "single, cohesive, useful" ideas, not the other way around[^explain].

We can also distinguish two main classes of personal knowledge methods:
- A *system* is a method that tries to deal with all types of information in all four externalization areas.
- A *method* is often much more specific, dealing with just one or two types of information. A system might be composed of many different methods.

A single strategy might fall somewhere in between a system and a method due to inherent flexibility of the medium by which they are implemented[^medium].

Since we are dealing with organizing *items*, some large categories of methods can be drawn:
- **Knowledge Network**: A system or method that collects items and attempts to link them together. This is done both to categorize information for better retrieval, and in the hopes that the structure of the network might allow additional insight to emerge[^networkinsight].
- **Task-based**: A system or method that primarely deals with TODO tasks, organizing, structuring and presenting them in a more actionable[^actionable] way.

## The big dump
Here's a list of all the main personal knowledge management systems or methods that I could find:

| Strategy           | Sys / Met | Type            | Support | Focus           | C/F/S/P |
|--------------------|-----------|-----------------|---------|-----------------|---------|
| Bullet Journal     | S         | Task-Based      | A (D)   | Tasks, Ideas    | CF--    |
| Commonplace Books  | S         | Collection      | A (D)   | Concepts, Ideas | CFS-    |
| Second Brain       | S         | Collection      | D       | Agnostic        | CF-P    |
| Zettelkasten       | S         | Knowledge Graph | D (A)   | Concepts, Ideas | CFSP    |
| PARA Method        | M         | Filing Method   | N/A     | Agnostic        | -FS-    |
| Link Your Thinking | S         | Knowledge Graph | D       | Agnostic        | CFSP    |
| Get Things Done    | M         | Task-Based      | A (A)   |                 | CFS-    |
| Digital Garden     | S         | Knowledge Graph | D       |                 | C-SP    |
| Kanban             | S         | Task-Based      | D (A)   | Tasks           | CF--    |
| Action Method      | S         | Task-Based      | A (D)   | Agnostic        | CFS-    |
| Personal Wiki      | S         | Knowledge Graph | D       | Concepts, Ideas | CFS-    |
| Eisenhower Matrix  | M         | Task Based      | A       | Tasks           | --S-    |

Other systems or ideas in the knowledge management space that did not fit well in the above table are:
- The Cornwell Notetaking system;
- The Memex method;



[^chemotaxis]: This is called "[chemotaxis](https://en.wikipedia.org/wiki/Chemotaxis)".
[^negbias]: This is called "[Negativity Bias](https://en.wikipedia.org/wiki/Negativity_bias)". It's what positive affirmations try to combat.
[^kwork]: With "knowledge work" I mean any kind of activity that exclusively or primarely deals with the processing of information, rather than a physical action executed in the world. For instance, the act of planning how to build a house is knowledge work. The act of physically building the house, while indubitably involving knoweldge, is "manual" or "skilled" work.
[^explain]: With this I mean that while a long note might be "single, cohesive and useful", shorter notes tend to fit much more commonly in this framework. For this reason, "atomic" was chosen as an adjective.
[^medium]: For example, many systems involve using a notebook. The flexibility of working on paper lets the implementation of the system to be tweaked to the user's content, potentially extending a method into a system, or combining external methods in a single system.
[^networkinsight]: I have yet to put my finger on what this "additional insight" looks like in a practical sense. In the netowrk-like systems that I have tried, the only examples is finding surprising neighboring items when adding or reviewing items.
[^actionable]: Something "actionable" is something that can be acted upon. For instance, knowing that in two months time a task will be due is not actionable today (but it will be in two months). An "actionable system" is a system that (automatically) tries to present items that are immediately actionable to the user, while not showing those that are not.
