Truth and Falsehood
-------------------

So far we've seen numerical types (integers and floats) and strings.
There is another important fundamental type in Python which is called
Boolean or bool. It has one of two values, *True* or *False*. These
values represent truth and falsehood. You can use them directly by using
their keywords:

    >>> y = True
    >>> y
    True
    >>> print(y)
    True
    >>> type(y)
    <class 'bool'>

Boolean values respond to logical operators:

    >>> True and False
    False
    >>> True and True
    True
    >>> False and True
    False
    >>> False or True
    True

Boolean Expressions
-------------------

There are a number of expressions, usually comparisons of some type that
result in a Boolean value. Some of these you might remember from math
class.


There are normal comparison operators, *&lt; &gt; &lt;= &gt;=*

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

Conditional Code
----------------

Python has a built in keyword, *if*, that executes a block of code
conditionally:

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

An *if* block can be followed by a mutually exclusive *else* block that
will execute if the condition is false:

    if x > 10:
        print("This may print")
    else:
        print("or this, but never both")

To create multiple mutually exclusive blocks of code, *elif* may be used
with more conditional checks.

    if x > 10:
        print("x is greater than 10")
    elif x > 5:
        print("x is greater than 5, but not greater than 10")
    elif x > 0:
        print("x is greater than 0, but not greater than 5")
    else:
        print("x must be less than or equal to 0")

In an *if* / *elif* / *else* section of code, the conditions are checked
in order and when one is found to be *True* that block executes, and
none of the others. If none of the conditions are true, the *else* blcok
executes, if there is one.



