Hello, Python
-------------

Python is a programming language. That means it is a specific language
for describing computations or algorithms to be executed on a computer.
  Let's take a look at a very simple program, just a single instruction
  to print some text on the screen:

    print("Hello, world!")

To make this a program you would type this into a text editor and save
it as a file with a *.py* extension, like *hello.py*. When you run this
program it has the following output:

    Hello, World

Python, when run from the command line without specifying a file to
execute opens an interactive shell. It also ships with a GUI application
that contains an interactive shell called IDLE. The Python shell allows
you to enter single Python statements that execute right away. Let's
take a look. It looks something like this:

    Python 3.1.2 (release31-maint, Sep 17 2010, 20:27:33) 
    [GCC 4.4.5] on linux2
    Type "help", "copyright", "credits" or "license" for more information.
    >>> print("Hello, World")
    Hello, World
    >>> 

The Python shell gives you a prompt to enter single statements, in the
previous example, I type the simple print command which executed as
soon as I pressed Enter. Python carried out the very simple command, to
print "Hello, World".

*print* is the name of a function defined in the Python programming
environment. It's primary purpose is to output text to the screen, but
it can also output text to a file.

The text *print("Hello, world")* is a statement in the Python
programming language. It contains the name of a function, *print*, and a
string of text, *"Hello, world"* which is passed to the string function.
This is called a *function call* or you could say the print function is
invoked.

**Exercise 1:** Download and install the latest stable release of Python
3.1 [here](http://python.org/download/releases/3.1.3/). Open IDLE, and
enter the following at the "&gt;&gt;&gt;" prompt:

    print("This is only a test", 1 / 2)

Record the output of the command.

String Literals
---------------

In the Python language, you can represent text as a string of letters
delimited with quotation marks, either single quotes or double quotes.

    >>> "Hello, World"
    'Hello, World'
    >>> 'Hello, World'
    'Hello, World'

When you enter an expression, like a string literal, in the Python
shell, it reports back the value of the expression. In a normal Python
program, in order to output the value to the screen, you would need to
use the *print* command. The shell is merely echoing back the value of
the expression for convenience.

There are ways of escaping special characters in the string, using the
backslash (\). For example, a double quoted string may contain a double
quote if escaped and a single quoted string may contain a single quote
if escaped.

    >>> "She said, \"Hello, World.\""
    'She said, "Hello, World."'
    >>> 'It\'s a nice day.'
    "It's a nice day."

You'll notice the shell uses whichever is more convenient, using double
quotes if a string contains only single quotes and vice versa when
displaying the value of the string.

You may see an error if you attempt to enter a string that does not
include matching quote symbols

    >>> "this string is unclosed
    SyntaxError: EOL while scanning string literal
    >>> "double quoted strings may not end with single quote'
    SyntaxError: EOL while scanning string literal
    >>> 'and vice versa"
    SyntaxError: EOL while scanning string literal
    >>> "This is correct"
    'This is correct'
    >>> 'so is this'
    'so is this'

**Exercise 2:** Enter the following text as a double quoted string and
as a single quoted string: *She said, "Python's the best."*
Record the output.

Sequential execution
--------------------

In a simple Python program, the statements execute in order from top to
bottom. Let's create a simple program using a text editor called
*simple.py*:

    # simple.py
    print("Hello, World")
    print("Hi, there!")

The output of running this Python program is:

    Hello, World
    Hi, there

It's a very simple example, but illustrates the point. When the
execution reaches the end of the file, the program exits. There are ways
to control the flow of execution that we'll look at later so your
programs don't just exit right away.

**Exercise 3:** Create a file called *poem.py* that contains several
print statements that print out the lines of a poem in the correct
order.

Numeric literals
----------------

In addition to string literals, Python supports numeric literals. There
are two main types of numeric literals in Python: integers and floating
points. Integers represent regular, integral numbers just like you might
have encountered in a math class.

    100
    >>> -2
    -2
    >>> -999
    -999
    >>> 0
    0

There are also floating point numbers, which are generally used to
represent real numbers or numbers with a fractional component.

    >>> 3.2
    3.2
    >>> -1.9
    -1.9
    >>> 3.14159
    3.14159
    >>> 0.0
    0.0

**Exercise 4:** When you enter numbers into the Python shell, it will
only retain a certain number of digits after the decimal point. Try
entering longer and longer numbers and record how many digits after the
decimal are shown in the number that Python prints out.

Mathematical expressions
------------------------

Python allows you to enter mathematical operators between numbers and
those expressions will be reduced when the program executes according to
the normal rules.

    >>> 5 + -3
    2
    >>> 6 - 9
    -3
    >>> 7 * 8
    56
    >>> 1 / 3
    0.3333333333333333

In Python 3, dividing integers by each other has a floating point result
value. Most operators applied to integers result in an integer value and
the same goes for floating point numbers. If one or more of the
operators is a floating point number or if the operation is division, the
result will be a floating point number.

    >>> 3.0 + 1
    4.0
    >>> 3 + 1
    4
    >>> 3.0 + 1.0
    4.0
    >>> 3 + 1.0
    4.0
    >>> 4 / 2
    2.0

In many programming languages, and even Python (before version 3),
dividing integers resulted in a integer result. You can simulate this
behavior with the special integer division operator (//).

    >>> 4 // 2
    2
    >>> 1 // 2
    0

As you can see, integer division is not generally useful, since any
fractional part of the result is truncated.

**Exercise 5:** Use the Python shell to calculate approximately how much
rent you pay per day in a 30 day month if your rent is $700 a month.
Record what you typed into the Python shell and the output.

Order of Operations
-------------------

You may remember from Algebra class that certain mathematical operations
have precedence over others and should be applied in a certain order.
Python respects these rules. You can also override these rules using
parentheses. You can verify this easily in the shell.

    >>> 1 + 2 * 5
    11
    >>> (1 + 2) * 5
    15

This makes the Python shell a very handy calculator, allowing you to
enter arbitrary mathematical expressions. To raise one number to an
exponential power, use the double-asterisk operator.

    >>> 10 ** 10
    10000000000
    >>> 0.5 ** 10
    0.0009765625
    >>> 10 ** 0.5
    3.1622776601683795
    >>> 100 ** 0.5
    10.0

**Exercise 6:** Use the Python shell to sum the number 5 and 6 and
multiply that value by 7. Record your input to the Python shell and the
output.

Variable Assignment
-------------------

Variables are places to store values, by associating them with a name.
Variables contain letters, numbers and underscores (&#95;), but may not
start with a numerical digit. Here are valid variable names:

    my_var
    x10
    YOU
    _here
    wowza

In order to assign a variable name a value, you use the assignment
operator (=). In an assignment, the right side of the statement is
evaluated first and then assigned to the variable name on the left.

    x = 10 + 20

In this example, first the right hand side (10 + 20) is evaluated and x
is assigned the value 30. We can then do other things with the value
stored in x, using x in place of the value.

    print(x) # prints 30
    y = x * 2 # now y has the value 60

Variables can hold any kind of value and can be changed.

Remember that Python executes commands sequentially from top to bottom.
Here is a short program that calculates interest:

    # interest.py
    interest_rate = 0.05
    starting_amount = 1000.0
    interest_made = starting_amount * interest_rate
    total_amount = starting_amount + interest_made

    print("You made this much interest: $", interest_made)
    print("This is the total amount: $", total_amount)

The first line of the program is a comment, signified by the hash symbol
(#) at the beginning of the line and is ignored. I used to show the name
of the file. The next line assigns the numerical value 0.05 to the
variable *interest_rate*. The line after that assigns the numerical
value 1000.0 to the variable *starting_amount*. The following line first
multiplies the value stored in the *interest_rate* variable with the
value stored in the *starting_amount* variable. The resulting value is
then assigned to a new variable called *interest_made*. After that,
*starting_amount* and *interest_made* are added together and the
resulting value assigned to the variable *total_amount*.

After the calculations, there is a blank line which is ignored by
Python. Empty lines may be used to break up different parts of a
program. In this case, there is a blank line between the lines of code
that calculate the interest and the lines of code which print out the
result.

The two lines that start with "print" just print out some information
for the user. This is what the output of running this program:

    You made this much interest: $ 50.0
    This is the total amount: $ 1050.0

**Exercise 7:** Write a small Python program called *hours.py* that
calculates the number of hours you spend sleeping every week.
