---
title: "Built-in Functions"
teaching: 30
exercises: 30
questions:
- "How can I use built-in functions?"
- "How can I find out what they do?"
objectives:
- "Explain the purpose of functions."
- "Correctly call built-in Python functions."
- "Correctly nest calls to built-in functions."
- "Use help to display documentation for built-in functions."
keypoints:
- "A function may take zero or more arguments."
- "Commonly-used built-in functions include `max`, `min`, and `round`."
- "Functions may only work for certain (combinations of) arguments."
- "Functions may have default values for some arguments."
- "Every function returns something."
- "Use the built-in function `help` to get help for a function."
- "The Jupyter Notebook has two ways to get help."
---

## What is a function?

We've already seen some built in functions:

~~~
greeting = "Welcome back to Python"
print(greeting)
~~~
{: .language-python}

~~~
dna = 'ATCCTGGCTTGTA'
len(dna)
~~~
{: .language-python}

Let's take a closer look:

To call a built-in function, we:

* start with the function's 'name' or *identifier*. In the examples above, this is `print` and `len`
* provide some *arguments* for the function to work on (`greeting` and `dna` respectively in the functions above)
* enclose the argmuments inside rounded brackets `()`

> ## Functions and automation
> Instead of using the built in function, we could instead calculate the length of a string using a `for` loop:
> ~~~
> dna = 'ATCCTGGCTTGTA'
>
> length = 0
> for n in dna:
>     length += 1
> ~~~
> {: language-python}
> 
> However, this approach has some drawbacks:
> * it requires typing three lines of code instead of one
> * every time we want calculate the length of a string, we have to write code to specifically iterate over the string
> * it's more error-prone to write longer, case-specific code
> 
> By using a built in function, we:
> * save ourself some typing
> * let an expert Python developer take responsibility for making sure the code is right
> * do the calculation faster (under the hood, built-in functions are usually written in `C`, a language that is closer to how computers think and runs faster)
> 
> For very very common tasks, there are usually built-in functions available to make our lives easier.
{: .callout}

## Function arguments can be values or defined variables
~~~
len('ATCCTGGCTTGTA')
~~~
{: .language-python}

~~~
len(dna)
~~~
{: .language-python}

## A function may take zero or more arguments.

*   `len` takes exactly one.
*   `print` takes zero or more.
*   `print` with no arguments prints a blank line.

NOTE: You must always use parentheses, even if they're empty, so that Python knows a function is being called.

~~~
print('before')
print()
print('after')
~~~
{: .python}
~~~
before

after
~~~
{: .output}

> ## The functions `int`, `str`, and `float`
> We've also met the built in functions `int`, `str`, and `float`.
> 1. How many arguments do each of these functions take?
> 2. What are the possible `types` of the input arguments?
> 3. How many outputs are there for each function? What are their types?
> {: .challenge}

## Commonly-used built-in functions include `max`, `min`, and `round`.

*   Use `max` to find the largest value of one or more values.
*   Use `min` to find the smallest.
*   Both work on character strings as well as numbers.

~~~
max(1, 2, 3)
~~~
{: .language-python}
~~~
3
~~~
{: .output}

> ## What is the smallest character?
> Have a guess at the output of the following call to `min`:
> ~~~
> min('a', 'A', '0')
> ~~~
> {: .language-python}
> Try out the code. Was your guess correct? What is the output of `max('a', 'A', '0')`?
{: .challenge}

> ## How many arguments?
> 1. In the above examples, how many arguments did `min` and `max` have?
> 2. What is the fewest number of arguments you can supply to `min` or `max`? 
> 3. Is there an upper limit to the number of arguments you can supply?
{: .challenge}

TODO: make into solution
*   `max` and `min` must be given at least one argument.
    *   "Largest of the empty set" is a meaningless question.
    
## Functions may only work for certain (combinations of) arguments.

For example, `max` and `min` must be given things that can be meaningfully compared:

~~~
print(max(1, 'a'))
~~~
{: .python}
~~~
TypeError: unorderable types: str() > int()
~~~
{: .error}

## Functions may have default values for some arguments.

*   `round` will round off a floating-point number.
*   By default, rounds to zero decimal places.

~~~
round(3.14159265359)
~~~
{: .python}
~~~
4
~~~
{: .output}

*   We can specify the number of decimal places we want.

~~~
round(3.14159265359, 1)
~~~
{: .python}
~~~
3.1
~~~
{: .output}

## Reading help
> Every built-in function has online documentation. Read the documentation for `round`:
> ~~~
> help(round)
> ~~~
> {: .language-python}
> ~~~
>
> 1. What is the name of the second, optional argument to `round`?
> 2. What is it's default value?
> 3. Call round again, this time rounding off `pi` to 5 decimal places.
{: .challenge}

> ## The Jupyter Notebook has two other ways to get help.
>
> *   Place the cursor inside the parenthesis of the function,
>    hold down `shift`,
>    and press `tab`.
> *   Or type a function name with a question mark after it.
{: callout}

## Every function returns something.

*   Every function call produces some result. This is called the *return value*.
*   If the function doesn't have a useful result to return,
    it usually returns the special value `None`.

~~~
result = print('example')
print('result of print is', result)
~~~
{: .python}
~~~
example
result of print is None
~~~
{: .output}

## Nesting functions

We can call functions inside other functions. We've already done this, nesting other functions inside the `print` function:

~~~
print("the sequence length is:" len(dna))
print("the nucleotides are: dna)
~~~
{: .challenge}

> ## What Happens When
>
> 1. Explain in simple terms the order of operations in the following program:
>    when does the addition happen, when does the subtraction happen,
>    when is each function called, etc. Write each operation out on a separate line, one by one.
> 2. What is the final value of `radiance`?
>
> ~~~
> radiance = 1.0
> radiance = max(2.1, 2.0 + min(radiance, 1.1 * radiance - 0.5))
> ~~~
> {: .language-python}
{: .challenge}

> ## Spot the Difference
>
> 1. Without running this code, predict what it's output will be:
>
> ~~~
> rich = "gold"
> poor = "tin"
> print(max(rich, poor))
> ~~~
> {: .language-python}
> 
> a) 'gold'
> b) poor
> c) 'tin'
> d) 'poor'
>
> 2. What is the output of `max(len(rich), len(poor))`?
> 3. Does `max(len(rich), poor)` run or produce an error message?
>    If it runs, does its result make any sense?
> {: .language-python}
{: .challenge}

> ## Why Not?
>
> Why don't `max` and `min` return `None` when they are given no arguments?
{: .challenge}
