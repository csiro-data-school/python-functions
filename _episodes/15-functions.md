---
title: "Creating functions"
teaching: 20
exercises: 20
questions:
- "How do I create my own functions in Python?"
- "How do I use my own functions?"
- "How do I document my functions?"
objectives:
- "Explain the benefits of using functions."
- "Explain and identify the difference between function definition and function call."
- "Write a function that takes a small, fixed number of arguments and produces a single result."
- "Explain the difference between required and optional function arguments."
- "Document your functions with docstrings."
keypoints:
- "Don't repeat yourself. Keep your code DRY by using functions."
- "Break programs down into functions to make them easier to understand."
- "Define a function using `def` with a name, parameters, and a block of code."
- "Defining a function does not run it."
- "Arguments in the function call are matched to the parameters in the function definition."
- "Optional arguments have a default value in the function definition."
- "Functions return results with the `return` statement."
- "Use docstrings to document your functions in a standard way."

---

We've seen how to use and work with Python's built-in functions. How can we 
define extra functions of our own, that do specific tasks?

## Define a function using `def` with a name, parameters, and a block of code

~~~
def print_greeting():
    print('Hello!')
~~~
{: .language-python}

Here, the new function:

- Begins with the keyword `def`, followed by a space
- Next comes the name we give our new function, `print_greeting`
- Parentheses `()` enclose the function's *parameters*. 
- The `def` statement ends with a colon `:`
- The *body* of the function follows, within an indented block of code

> ## Function definition syntax
> Where have we seen the keyword, colon, code block syntax before?
{: .discussion}

> ## Function parameters
> How many parameters does our function have?
{: .discussion}

## Calling functions

* Defining a function does not run it.
* Must call the function to execute the code it contains.
* Calling functions you define is just like calling built-in functions:

~~~
print_greeting()
~~~
{: .language-python}

~~~
Hello!
~~~
{: .output}

* start with the function name
* include arguments within parenthesis
* do not end the function call with a colon! (Why not?)

> ## Hello World
> Modify the function definition example above so that the function call 
> now prints `'Hello world'`
{: .challenge}

## Choosing function names

Functions naming follows the same rules as variable naming. Just like variables,
Python doesn't care what you call your function, as long as it follows the rules. So, this code works:

~~~
def mr_flibble():
    print('Hello!')
    
mr_flibble()
~~~
{: .language-python}
~~~
'Hello'
~~~
{: .output}

However, this wouldn't be a wise choice; it's easier to maintain and understand code if your function name tells you what the function does.

> ## Write a Happy Birthday function
>
> Write a function called `happy_birthday` that prints the message "Happy
> birthday!".
> > ## Solution
> > ~~~
> > def happy_birthday():
> >     print("Happy birthday!")
> > ~~~
> > {: .language-python}
> {: .solution}
{: .challenge}

> ## Call your Happy Birthday function
>
> Call your `happy_birthday` function.
> > ## Solution
> > ~~~
> > happy_birthday()
> > ~~~
> > {: .language-python}
> > ~~~
> > Happy birthday!
> > ~~~
> > {: .output}
> {: .solution}
{: .challenge}

## A Common Error
Functions must be defined before you can call them.
The following code will not work:
~~~
print_farewell()
~~~
{: .language-python}

## Specifying function parameters

Functions are most useful when they can operate on different data. Many of the built-in functions we have seen have *parameters*. It is by providing *arguments* to these *parameters* that we can ask functions to do work on our data.

Let's look again at the help for the built-in function `round`:

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

Here, the parameters of `round` are `number` and `ndigits`. When we call this function:

~~~
round(3.14159265359, 2)
~~~
{: .language-python}
~~~
3.14
~~~
{: .output}

we are providing the arguments `3.14159265359` and `2` to the parameters `number` and `ndigits`, respectively.

We could call round again, changing the arguments:
~~~
round(2.71828, 1)
~~~
{: .language-python}
~~~
2.7
~~~
{: .output}

Here, we are providing different 'data' or 'arguments', to the same parameters `number` and `ndigits`.

We can use parameters to get data into functions we design ourselves as well. Consider our existing 
function definition and call:

~~~
def print_greeting():
    print('Hello!')
    
print_greeting()
~~~
{: .language-python}
~~~
'Hello!'
~~~
{: .challenge}

This is not particularly useful, however, as we can't change what greeting our function prints.
We could, instead, provide a parameter:

~~~
def print_greeting(salutation):
   print(salutation)
~~~
{: .language-python}

~~~
print_greeting('Bonjour')
print_greeting('Namaste')
print_greeting('Ciao')
~~~
{: .language-python}
~~~
'Bonjour'
'Namaste'
'Ciao'
~~~
{: .output}

Ta da! Now we can define function that do work on user-supplied data.

* Specify *parameters* when defining a function.
* Use these as *variables* within the function body
* The *arguments* when the function is called are the *values* that get assigned to the 
parameter *variables* inside the function.

Again, the parameter names don't matter, as long as you use the same name within the body of your function. This also works:

~~~
def print_greeting(x):
   print(x)
~~~
{: .language-python}

~~~
print_greeting('Bonjour')
~~~
{: .language-python}
~~~
'Bonjour'
~~~
{: .output}

As usual, however, meaningful parameter names make for better code.

> ## Fill in the blanks
> ~~~
> def print_date(year, month, day):
>     joined = str(____) + '/' + str(____) + '/' + str(____)
>     print(joined)
> 
> ________(1871, 3, 19)
> ~~~
> {: .language-python}
> ~~~
> 1871/3/19
> ~~~
> {: .output}
{: .challenge}

## Arguments in the function call are matched to the parameters in the function definition

We can also explicitly match the arguments to parameters when we call a function, which allows us to
specify them in any order:
~~~
print_date(month=2, day=12, year=1809)
~~~
{: .language-python}
~~~
1809/2/12
~~~
{: .output}

> ## Add a name parameter to your Happy Birthday function
>
> Add a parameter called `name` to your happy birthday function. The function
> should now use the supplied name in the message.
> > ## Solution
> > ~~~
> > def happy_birthday(name):
> >     print("Happy birthday to " + name + "!")
> > ~~~
> > {: .language-python}
> {: .solution}
{: .challenge}

## Optional arguments have a default value in the function definition

* You can add optional arguments to your functions by providing a default value
in the function definition.
* If a value is supplied in the function call, that value will be used.
* If no value is supplied at call time, the default will be used.

~~~
def print_greeting(who=""):
    if who:  # recall that empty strings are treated as False
        print("Hello " + who + "!")
    else:
        print("Hello!")
~~~
{: .language-python}
~~~
print_greeting()
~~~
{: .language-python}
~~~
Hello
~~~
{: .output}
~~~
print_greeting("Brian")
~~~
{: .language-python}
~~~
Hello Brian
~~~
{: .output}

> ## Add a default value to `name`
>
> In your `happy_birthday` function, give the `name` parameter a default value of "you".
> > ## Solution
> > ~~~
> > def happy_birthday(name="you"):
> >     print("Happy birthday to " + name + "!")
> > ~~~
> > {: .language-python}
> {: .solution}
{: .challenge}

> ## Positional and Keyword Arguments
> In the Python world, you will frequently see function arguments described as
> *positional* and *keyword* arguments. Positional arguments are those that are
> matched to parameters by position in the function call, while keyword arguments are matched
> by name. Historically, positional arguments were used for parameters without
> a default value, while keyword arguments were used for parameters with default
> values. However this need not be the case.
{: .callout}

## Functions output results with the `return` statement

Let's think about some built in functions again:

~~~
p_return = print('Welcome back')
print(p_return)
~~~
{: .language-python}
~~~
None
~~~
{: .output}

~~~
l_return = len('Welcome back')
print(l_return)
~~~
{: .language-python}
~~~
12
~~~
{: .output}

So far, the functions we have written are most like the `print` example here; they 
print a value to the screen, however you can't 'save' that value for later by 
assigning it to a variable. If we try, the variable ends up with the value 'None'. 
In contrast, a call to `len` doesn't automatically print anything, however we can 
save it's output to a variable.

You can use a `return` statement to make your function 'give back' some output that can be saved and used downstream.

- Use `return ...` to give a value back to the caller.
- May occur anywhere in the function.
- But functions are easier to understand if `return` occurs:
    - At the start to handle special cases.
    - At the very end, with a final result.
- Every function returns something. If your function does not explicitly
  `return` a value, then `None` is returned automatically.

> ## Averaging numbers
> Write a function that accepts a list of numbers and returns the average.
> If the argument is an empty list, then return `None`. All other error
> conditions can be ignored.
> > ## Solution
> > ~~~
> > def average(values):
> >     if len(values) == 0:
> >         return None
> >     return sum(values) / len(values)
> > ~~~
> > {: .language-python}
> {: .solution}
{: .challenge}



---

{% include links.md %}

[pep-257]: https://www.python.org/dev/peps/pep-0257/
