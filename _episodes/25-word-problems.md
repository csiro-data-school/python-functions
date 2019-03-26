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

We now understand the syntax of Python functions and know how to put together very simple functions. However, how do you write a function when it is a bit more complex? How do you:

* know how 'big' to make your function, i.e. how many tasks should it do
* handle all possible inputs
* make sure others (and your future self!) know how to use your function


## Tinker till it works, or ...
Beginner (and often even advanced!) coders often start writing a new function by working out the logic inside
the black box. This path is hard and bug-prone! An alternative approach involves very precisely defining and describing what we want
our function to do first. Once that is crystal clear, working out the nuts and bolts inside the black box is much
easier.
{: .callout}

## The black-box function

A well written function is a bit like a black box:

* you give it some input 
* it does some magic
* it spits out some output. 

Instead of tinkering with the insides first, we can do a really good job of designing what the outside of the box looks like 
first. Only once that is done, do we start work on the 'mechanics' inside the body of the function. 

## Design Recipe

This design recipe can be applied to functions in any language:

> ## DESIGN RECIPE
> 1. **Signature**: this decribes how many inputs and outputs our function has, and their type.
> 2. **Purpose**: a short, succinct description of the task (one line max)
> 3. **Stub**: puts names to the inputs and outputs of the function
> 4. **Examples**: demonstrates how you expect your function to behave in difference scenarios.
>
> We will go through each of these steps in turn below.
{: .callout}

## Design recipe in Python

Say we want to write a function that converts temperature in Fahrenheit to Celsius. Our design recipe looks like this:

~~~
# fahr_to_cel: Float -> Float
def fahr_to_celsius(temp_fahr):
    '''Converts temperature in fahrenheit to temperature in celsius
    >>> fahr_to_celsius(52.0)
    11.1
    >>> fahr_to_celsius(0)
    -17.8
    '''
    
    # magic...
    
    return(temp_cels)
~~~
{: .language-python}

Let's talk through this example step by step.

## Signature
  
The signature formalises the process of describing our function's inputs and outputs. In our example, it is the line:

~~~
# fahr_to_cel: Float -> Float
~~~
{: .language-python}

We start by giving our function a name, `fahr_to_cel`. Next, we describe the number and 'type' of inputs and outputs.
Here, we say `Float -> Float`, meaning we have one input of type `Float`, (before the `->`), and one output of type `Float`
(after the `->`). We start the signature line with a `#`, to turn it into a comment. Python itself doesn't care if this line is there or not, it is just a comment to help us understand the code and get our thoughts in order.

## Purpose

This one sounds deceptively easy: in one sentence (say, 80 characters max), describe what your function does.

> Purpose statement guidelines:
> * Don't repeat info that is in the signature. There is no need for the name of the function, or a description
> of its inputs and outputs.
> * Keep it as generic as possible. If it calculates the area of a rectangle, say it calculates the area of a rectangle. Don't say, it gives the area of a Boorowa field plot. 
> * Try and word it so any colleague in CSIRO would understand it.
> * If you absolutely need more than 80 characters, you probably need to further limit what the 'job' your function does is. You might be better off writing two smaller functions, rather than one larger one.
{: .callout}

In our example above, the purpose statement is:

~~~
Converts temperature in fahrenheit to temperature in celsius
~~~

## Stub

Next comes the stub. The stub 'maps' the inputs and outputs to names, and sets up the 'skeleton' of the function. Here is our stub:

def fahr_to_celsius(temp_fahr):
    
    # magic...
    
    return(temp_cels)
    
Your stub must:

* use the same name as your signature, here `fahr_to_celsius`
* have the same number of inputs and outputs as your signature
* specify valid variable names for the inputs and outputs (`temp_fahr` is the input, `temp_cels` is the output)

## Examples

Examples are the most important part of your function design, and often the most overlooked! If you can master the 
art of writing good examples, then you will be able to write code that works, is easy to read, and is easy to debug.

Our examples are:

~~~
>>> fahr_to_celsius(52.0)
11.1
>>> fahr_to_celsius(0)
-17.8
~~~
{: .language-python}


> ##Example guidelines
> * choose 2 to 4 well-thought out examples
> * try and find 'boundary' conditions. In our example, `0` is a natural boundary for the kind of data we will input.
> * for now, design examples that are **meant** to work, rather designing examples to break your code. 
{: .callout}

> ## Use docstrings to document your functions in a standard way
>
> Python functions can contain a special documentation string, known as the docstring. The docstring can contain information about the purpose and use of your function.
>
> * Docstrings allow us to document our code in a standard way.
> * Following the standard makes our code more easily readable to other
>  programmers, and also allows software tools to use our documentation
>  automatically.
> * More technically (see [PEP-257][pep-257]):
>    * A docstring is a string literal that occurs as the first statement in
>      a module, function, class, or method definition.
>    * This string is assigned to the `__doc__` special attribute of the object.
>        * This allows it to be used in standard ways, since tools just need to
>          look for a value assigned to `__doc__`.
> * Docstrings can be either one line, or multiple lines long.
>
> There are a number of docstring conventions. Some of the most useful are:
> * Surround docstrings with triple double quotes (`"""`).
> * Do not put a blank line before or after the docstring.
>
>
> ### A one-line docstring example
> For example (from [PEP-257][pep-257]):
> ~~~
> def kos_root():
>     """Return the pathname of the KOS root directory."""
>     global _kos_root
>     if _kos_root: return _kos_root
>     ...
> ~~~
> {: .language-python}
> * Triple quotes are used even though the string fits on one line. This makes it
> * easy to later expand it.
> * The closing quotes are on the same line as the opening quotes. This looks
> * better for one-liners.
> * There's no blank line either before or after the docstring.
> * The docstring is a phrase ending in a period. It prescribes the function or
>  method's effect as a command ("Do this", "Return that"), not as a description;
>  e.g. don't write "Returns the pathname ...".
>
> ### A multi-line docstring example
>
> ~~~
> def complex(real=0.0, imag=0.0):
>     """Form a complex number.
>
>     Keyword arguments:
>     real -- the real part (default 0.0)
>     imag -- the imaginary part (default 0.0)
>     """
>     if imag == 0.0 and real == 0.0:
>         return complex_zero
>     ...
> ~~~
> {: .language-python}
> Note the following features:
>
> * A one-line summary at the start,
> * Followed by a blank line,
> * Further elaboration, in this case a description of the arguments,
> * A final carriage return with the final `"""` on their own line.
{: .callout}

> ## fahr_to_celsius
> Write out your own `fahr_to_celsius` function. Now, call your function using your 
> examples that you specified in the docstring. Do your examples exactly match your function output?
> If they don't match, modify your function to match the examples.
{: .challenge}

> ## Change the body, not the examples!
> You've already thought a lot about how you want your function to behave. You've already defined 'correct' behavior.
> If you get an unexpected result, or a result that is not *quite* what you expect, don't cheat and change your examples.
> As we have seen, functions often rely on other functions... if you redefine what you *want* your function to do on the fly, 
> you are likely to break other parts of your code. Instead, keep working on the logic of your function until it exactly 
> matches your examples.
{: .callout}

> ## Fahrenheit to Kelvin
> 1. In order, write out the signature, stub, purpose, and examples for this function using Python notation.
> 2. Now, fill in the body. 
{: .challenge}

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
