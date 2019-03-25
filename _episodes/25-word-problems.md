---
title: "Word problems"
teaching: 30
exercises: 30
questions:
- "How do I get from a description of a problem, to a code solution?"
objectives:
- "Extract coding task from word problem"
- "Identify input and output data"
- "Describe a coding task's main function"
- "Formulate useful examples of the task"
keypoints:
- "Functions operate on input data, producing output data"
- "Identifying and describing the data task is the biggest challenge in writing functions"
- "A systematic design recipe will help you write elegant functions from the get-go!"
---

## The black-box function

Functions are at the heart of programing; they are the machines that do work. 
Once we've written a function, it's a bit like a black box:

* you give it some input 
* it does some magic
* it spits out some output. 

~~~
first_name = 'Kerensa'
len(first_name)
~~~
{: .language-python}

~~~
7
~~~
{: .output}

Here, we've called the fuction `len()`, with the input data `first_name`, and received some 
output data `7`. We don't see the internal workings or calculations of the function, len() 
is essentially a black box that does some processing.

## Tinker till it works, or ...
Beginner (and often even advanced!) coders often start writing a new function by working out the logic inside
the black box. This path is hard and bug-prone! An alternative approach involves very precisely defining and describing what we want
our function to do first. Once that is crystal clear, working out the nuts and bolts inside the black box is much
easier.
{: .callout}

## Words to functions

Often, the hardest part of writing your own functions, is working out *what* you actually want your function to *do*. 
You're given a description of a task someone wants completed, and you need to turn this into language that the 
computer understands. Let's try some word problems. A colleague sends you an email asking:

"The field data is back from the trial, but unfortunately I'm having a lot of trouble loading it into the software because 
the assistant recorded the dates using the month's name, and the software demands dates formatted like 2018-03-02, 
2018-06-04, etc. Do you think you could write me a quick script to help me out?" 

Start by identifying the data in the description (it can help to use a highlighter to start with!). Here, the output data is a string, formatted as: `yyyy-mm-dd`. As 
input data, we have the names of months, also a string. Presumably, based on the output, we are given year and day as well.

> ## Data discussion
> Is this data description complete?
> Are we given enough information to write the program?
{: .discussion} 

After you've worked out the data, work out what the actual task you are being asked to do is. Here, you might say 
"Reformat dates containing month names to ODBC canonical date format e.g. yyyy-mm-dd."


> ## Antibiotics
> 
> Identify the input data, output data, and task in this word problem:
>
> Antibiotics are sometimes tested by placing antibiotic-impregnated paper disks onto bacteria-covered agar in a petri dish.
> Bacterial death spreads out from the antibiotic creating a perfect circular bacteria-free zone. You've recorded the 
> diameter of several hundreds of test plates, with three replicates per plate. You want to find 
> the average area of the bacterial zones for your resistance calculations.
{: .challenge}

> ## DNA
>
> Identify the input data, output data, and task in this word problem: 
>
> The component acids that form DNA are often represented as 'A', 'T', 'G', and 'C', e.g. 'AATCGCGTTA'. The amount 
> of 'G' and 'C' in 
> a DNA sequence tends to be organism specific. You've received some sequence data from a service provider,
> and as a simple test of contamination you want to check its GC ratio.
{: .challenge}

> ## Design Recipe
> As you can see from the exercises above, there are often ambiguities involved in interpreting a problem. 
> Choices need to be made, often regarding:
> * the kind of input data your function will accept, and output data it will generate
> * the function's purpose; will it do everything in the description, or a smaller implied task?
>
> There is often not a 'right' or 'wrong' answer to these questions. However, you need answers in order to 
> define whether your function is working correctly, and in fact to know what you want to code in the first 
> place.
> This is where a 'Design Recipe' can help, by forcing you to answer these questions before you write code.
{: .callout}

{% include links.md %}
