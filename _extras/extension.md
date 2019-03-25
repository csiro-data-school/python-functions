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
