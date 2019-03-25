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
*   `int`, `str`, and `float` create a new value from an existing one.


## Commonly-used built-in functions include `max`, `min`, and `round`.

*   Use `max` to find the largest value of one or more values.
*   Use `min` to find the smallest.
*   Both work on character strings as well as numbers.
    *   "Larger" and "smaller" use (0-9, A-Z, a-z) to compare letters.

~~~
print(max(1, 2, 3))
print(min('a', 'A', '0'))
~~~
{: .python}
~~~
3
0
~~~
{: .output}

## Functions may only work for certain (combinations of) arguments.

*   `max` and `min` must be given at least one argument.
    *   "Largest of the empty set" is a meaningless question.
*   And they must be given things that can meaningfully be compared.

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
round(3.712)
~~~
{: .python}
~~~
4
~~~
{: .output}

*   We can specify the number of decimal places we want.

~~~
round(3.712, 1)
~~~
{: .python}
~~~
3.7
~~~
{: .output}

## Use the built-in function `help` to get help for a function.

*   Every built-in function has online documentation.

~~~
help(round)
~~~
{: .python}
~~~
Help on built-in function round in module builtins:

round(...)
    round(number[, ndigits]) -> number

    Round a number to a given precision in decimal digits (default 0 digits).
    This returns an int when called with one argument, otherwise the
    same type as the number. ndigits may be negative.
~~~
{: .output}

## The Jupyter Notebook has two ways to get help.

*   Place the cursor inside the parenthesis of the function,
    hold down `shift`,
    and press `tab`.
*   Or type a function name with a question mark after it.

## Every function returns something.

*   Every function call produces some result.
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

> ## What Happens When
>
> 1. Explain in simple terms the order of operations in the following program:
>    when does the addition happen, when does the subtraction happen,
>    when is each function called, etc.
> 2. What is the final value of `radiance`?
>
> ~~~
> radiance = 1.0
> radiance = max(2.1, 2.0 + min(radiance, 1.1 * radiance - 0.5))
> ~~~
> {: .source}
{: .challenge}

> ## Spot the Difference
>
> 1. Predict what each of the `print` statements in the program below will print.
> 2. Does `max(len(rich), poor)` run or produce an error message?
>    If it runs, does its result make any sense?
>
> ~~~
> rich = "gold"
> poor = "tin"
> print(max(rich, poor))
> print(max(len(rich), len(poor)))
> ~~~
> {: .source}
{: .challenge}

> ## Why Not?
>
> Why don't `max` and `min` return `None` when they are given no arguments?
{: .challenge}
