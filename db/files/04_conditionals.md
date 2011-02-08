Truth and Falsehood
-------------------

So far we've seen numerical types (integers and floats) and strings.
There is another important fundamental type in Python which is called
Boolean or bool. It has one of two values, **True** or **False**. These
values represent truth and falsehood. You can use them directly by using
their keywords literal represenations **True** and **False**
(capitalization is important):

    >>> y = True
    >>> y
    True
    >>> print(y)
    True
    >>> type(y)
    <class 'bool'>
    >>> type(False)
    <class 'bool'>

Boolean values respond to logical operators **and** and **or**:

    >>> True and False
    False
    >>> True and True
    True
    >>> False and True
    False
    >>> False or True
    True
    >>> False or False
    False

Boolean Expressions
-------------------

There are a number of expressions, usually comparisons of some type that
result in a Boolean value. Some of these you might remember from math
class.


There are normal comparison operators, "less than" : **&lt;**, "greater
than" : **&gt;**, "less than or equal to" :  **&lt;=**, "greater than or
equal to" : **&gt;=**, and "equal to" : **==**.

    >>> 10 > 20
    False
    >>> 20 > 10
    True
    >>> 1.2 < 3.4
    True
    >>> 3.0 < 3.0
    False
    >>> 3.0 <= 3.0
    True
    >>> 2.0 == 2.5
    False
    >>> (2 + 2) == 4
    True
    >>> (2 + 2) == 5
    False

**Exercise 1:** Write a function called **candrink** that takes as a
single parameter an age and returns **True** if the age is greater than
or equal to 21, **False** otherwise.

Conditional Code
----------------

The real power of boolean values is in the ability to run different code
based on the value of boolean expressions. Python has a built in
keyword, **if**, that executes a block of code conditionally:

    if True:
        print("let's do this")

    if False:
        print("this will never happen")

The blocks of code are delimited with indentation, just like functions.

    x = 10
    if x < 20:
        print("x is less than 20")
        x = x * 3

    if x >= 20:
        print("now x is greater than or equal to 20")

An **if** block can be followed by a mutually exclusive **else** block that
will execute if the condition is false:

    if x > 10:
        print("This may print")
    else:
        print("or this, but never both")

**Exercise 2:** Write a function called **enterbar** that takes a single
parameter called 'age'. If the age is less than 21 print a message: 
"Come back in X years!" where X is the number of years until the person
trying to enter the bar is 21. Otherwise, the function should print the
message, "Drink responsibly".

Many Paths to Choose From
-------------------------

To create multiple mutually exclusive blocks of code, **elif** may be used
with more conditional checks.

    if x > 10:
        print("x is greater than 10")
    elif x > 5:
        print("x is greater than 5, but not greater than 10")
    elif x > 0:
        print("x is greater than 0, but not greater than 5")
    else:
        print("x must be less than or equal to 0")

In an **if** / **elif** / **else** section of code, the conditions are checked
in order and when one is found to be **True** that block executes, and
none of the others. If none of the conditions are true, the **else**
block executes, if there is one.


**Exercise 3:** Write a program in a file called **decisions.py**. In
the program ask the user to input his or her age. Also, ask the user whether
or not he or she is driving ('y' or 'n'). If the user is under 21, print
a message requesting that the person leave, if the person is 21 or over
and is not driving, offer a drink, and if the person is over 21 and
driving, offer a complimentary non-alcoholic beverage.

