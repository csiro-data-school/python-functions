---
title: "Return statements"
teaching: 20
exercises: 20
questions:
- "How can I save the output of functions?"
objectives:
- "Use a `return` statement within the body of a function"
- "Capture a return value in a variable"
- "Understand that all functions return something"
- "Explain the difference between `print` and `return` within a function"
keypoints:
- "Functions return results with the `return` statement."
- "Functions without explicit `return` values return `None`"
- "Within a function, `Print` communicates with humans, `return` communicates with the computer"
---

## Functions output results with the `return` statement

Let's think about some built in functions again:

~~~
print_return = print('Welcome back')
print(print_return)
~~~
{: .language-python}
~~~
None
~~~
{: .output}

~~~
len_return = len('Welcome back')
print(len_return)
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

For example, 

~~~
def average(values):
    return sum(values) / len(values)
~~~
{: .language-python}

~~~
average([2, 10, 4])
average([34.4, 9, 10])
average([-8, 3, 9])
~~~
{: .language-python}
~~~
1.333333333333333
~~~
{: .output}

Why did we only get one output value? Did the function calls work?

Now, try this:
~~~
mean_ints = average([2, 10, 4])
mean_float = average([34.4, 9, 10])
mean_neg = average([-8, 3, 9])
print(mean_ints, mean_float, mean_neg)
~~~
{: .language-python}
~~~
5.333333333333333 17.8 1.333333333333333
~~~
{: .output}

> ## Return versus print (again!)
>
> Note that `return` and `print` are not interchangeable.
> `print` is a Python function that *prints* data to the screen.
> It enables us, *users*, see the data.
> The `return` statement, on the other hand, makes data visible to the program.
{: .callout}

> ## Exercise
> Let's have a look at the following function:
> ~~~
> def add(a, b):
>     print(a + b)
> ~~~
> {: .language-python}
>
> **Question**: What will we see if we execute the following commands?
> ~~~
> A = add(7, 3)
> print(A)
> ~~~
> {: .language-python}
>
> > ## Solution
> > Python will first execute the function `add` with `a = 7` and `b = 3`,
> > and, therefore, print `10`. However, because our function `add` does not have a
> > line that starts with `return` (no `return` "statement"), it will, by default, return
> > nothing which, in Python world, is called `None`. Therefore, `A` will be assigned to `None`
> > and the last line (`print(A)`) will print `None`. As a result, we will see:
> > ~~~
> > 10
> > None
> > ~~~
> > {: .output}
> {: .solution}
{: .challenge}

> ## The Old Switcheroo
>
> Consider this code:
>
> ~~~
> a = 3
> b = 7
>
> def swap(a, b):
>     temp = a
>     a = b
>     b = temp
>
> swap(a, b)
>
> print(a, b)
> ~~~
> {: .language-python}
>
> Which of the following would be printed if you were to run this code?
> Why did you pick this answer?
>
> 1. `7 3`
> 2. `3 7`
> 3. `3 3`
> 4. `7 7`
>
> > ## Solution
> > `3, 7` is correct. Initially `a` has a value of 3 and `b` has a value of 7.
> > When the swap function is called, it creates local variables (also called
> > `a` and `b` in this case) and trades their values. The function does not
> > return any values and does not alter `a` or `b` outside of its local copy.
> > Therefore the original values of `a` and `b` remain unchanged.
> {: .solution}
{: .challenge}

## Functions can have multiple `return` statements

`return` may occur anywhere in the function. However, functions are easier to understand if `return` only occurs:
* at the start to handle special cases
* at the very end, with a final result.

~~~
def average(values):
    if len(values) == 0:
        return None
    return sum(values) / len(values)
~~~
{: .language-python}

> ## Challenge exercise
> Write a function that returns the median value from a list of values. 
> Does your function work if it is supplied an empty list?
> Does your function work if there are multiple data types in your list? Should it?
> What happens if you give your function data that is not a list?
{: .challenge}

---

{% include links.md %}

[pep-257]: https://www.python.org/dev/peps/pep-0257/
