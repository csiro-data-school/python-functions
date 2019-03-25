---
title: "Additional content"
---

## About Files

- Files store data on disk.
- They can be either text or binary files.
- Text files store text data in standard encodings that can be understood by
  many programs.
    - Often have name extensions that indicate the type of file, such as `.py`
      for Python scripts, `.csv` for comma-separated values data,
      and `.txt` for plain text files.
    - There are different encodings for text data that affect how the text is
      stored. Common encodings are ASCII and UTF-8. We will ignore encodings
      from here on.
- Binary files store binary data. Apart from conventions about the ordering of
  bytes on disk, binary files can have almost any internal structure.
    - There are some well documented binary file standards, such as PDF, and
      NetCDF.
    - However, frequently binary files can only be read by the software that
      created them.
- Python supports working with both binary and text files.
- We only explore working with text files here.

- Files are normally opened in text mode. By appending `"b"` to the mode,
  the file will be opened in binary mode.


## Functions




## Don't Repeat Yourself

One of the core principles of any programming language is, "Don't Repeat
Yourself", often referred to as DRY. If you have an action that should occur
many times, you can define that action once and then call that code whenever you
need to carry out the action.

Functions mean less work for us as programmers, and effective use of functions
results in code that is less error-prone.

When our function works, we don't have to worry about that code anymore. Every
time you repeat code in your program, you introduce an opportunity to make
a mistake. Writing a function means there is one place to fix mistakes, and when
those bugs are fixed, we can be confident that this function will continue to
work correctly.

## Break programs down into functions to make them easier to understand

We can only keep a few items or ideas in working memory at a time. To understand
complicated ideas, we chunk information together and then think about the
higher-level chunks. For example, when thinking about cars we may just think
about engines, wheels, and entertainment systems. Each one is a complicated
system, but we don't need to consider every detail all the time.

Functions serve the same purpose in programs. They chunk some code together so we
can treat it as a single thing elsewhere. For example, I can use a `sort()` function to
order a list of strings without needing to think about the implementation
details of sorting algorithms.

Functions allow us to:

- order our code,
- think about our code at a higher-level,
- make our code more readable,
- make our code reusable,
    - write once, use often
- make our code more reliable,
- make our code easier to update,
    - modifying a function is easier than finding and modifying multiple
      sections of duplicated code
- make our code testable (see the [testing episode]({{ page.root
  }}/13-testing/)),
- define interfaces so others can use our code.

Additionally, functions provide a convenient focal point for documentation.
They are at the right level of detail for documenting your code, and Python has
a number of good tools for generating formatted documentation from functions.

### FIXME: Do I need the next 2 paragraphs?
Conceptually, functions can be treated as a box of code. When using a function
it can be a black box. You need only consider the inputs and outputs: what data
do you supply, and what should you get back. When writing functions they are
a white box: you must pay attention to the internal details as well as the
data flow (inputs and outputs).

Finally, when designing your functions, it can be helpful to only write
functions that do a single task. One function, one job. Complicated functions
that do many things are harder to write, harder to debug, and harder to use.

## Use docstrings to document your functions in a standard way

Python functions can contain a special documentation string, known as the docstring. The docstring can contain information about the purpose and use of your function.

- Docstrings allow us to document our code in a standard way.
- Following the standard makes our code more easily readable to other
  programmers, and also allows software tools to use our documentation
  automatically.
- More technically (see [PEP-257][pep-257]):
    - A docstring is a string literal that occurs as the first statement in
      a module, function, class, or method definition.
    - This string is assigned to the `__doc__` special attribute of the object.
        - This allows it to be used in standard ways, since tools just need to
          look for a value assigned to `__doc__`.
- Docstrings can be either one line, or multiple lines long.

There are a number of docstring conventions. Some of the most useful are:
- Surround docstrings with triple double quotes (`"""`).
- Do not put a blank line before or after the docstring.

### A one-line docstring example
For example (from [PEP-257][pep-257]):
~~~
def kos_root():
    """Return the pathname of the KOS root directory."""
    global _kos_root
    if _kos_root: return _kos_root
    ...
~~~
{: .language-python}
- Triple quotes are used even though the string fits on one line. This makes it
  easy to later expand it.
- The closing quotes are on the same line as the opening quotes. This looks
  better for one-liners.
- There's no blank line either before or after the docstring.
- The docstring is a phrase ending in a period. It prescribes the function or
  method's effect as a command ("Do this", "Return that"), not as a description;
  e.g. don't write "Returns the pathname ...".

### A multi-line docstring example

~~~
def complex(real=0.0, imag=0.0):
    """Form a complex number.

    Keyword arguments:
    real -- the real part (default 0.0)
    imag -- the imaginary part (default 0.0)
    """
    if imag == 0.0 and real == 0.0:
        return complex_zero
    ...
~~~
{: .language-python}
Note the following features:

- A one-line summary at the start,
- Followed by a blank line,
- Further elaboration, in this case a description of the arguments,
- A final carriage return with the final `"""` on their own line.

> ## Add a docstring
> What do you think this function does?
> Add a docstring to it.
> ~~~
> def last_first(first_name, last_name, separator=", "):
>     result = "{0}{1}{2}".format(last_name, separator, first_name)
>     return result
> ~~~
> {: .language-python}
> > ## Solution
> > The function takes a first name and a last name, returning a single string
> > with the last name first, separated from the first name by the separator
> > string.
> > The separator value is optional, with a default value of ", ".
> > ~~~
> > def last_first(first_name, last_name, separator=", "):
> >     """Return a single string in the form "{last_name}{separator}{first_name}".
> >     Arguments:
> >     first_name -- the first name
> >     last_name -- the last name
> >     separator -- the separator used between first and last names (default ", ")
> >     """
> >     result = "{0}{1}{2}".format(last_name, separator, first_name)
> >     return result
> > ~~~
> > {: .language-python}
> {: .solution}
{: .challenge}
