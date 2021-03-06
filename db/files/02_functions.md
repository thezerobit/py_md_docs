Python Functions
----------------

In the last section we saw the **print** function. You can use it like
this:

    print("hello")

Which creates the following output on your screen:

    hello

You can also define your own functions as a way to reuse the same piece
of code more than once without having to type it out more than once.

A common use for functions would be to apply a mathematical
transformation to a value. Here is a function to convert degrees from
Fahrenheit to Celcius:

    def to_celcius(degrees_f):
        x = degrees_f - 32
        return x * 5 / 9

If you put a function definition in a **.py** file, then any line after
that you can call the function like any other.

    # temp.py

    def to_celcius(degrees_f):
        x = degrees_f - 32
        return x * 5 / 9

    degrees_c = to_celcius(32.0)
    print(degrees_c)

This program will output the following:

    0.0

There are several parts to the function definition. The first part is
the keyword **def** which tells Python that you are defining a function.
The name **def** is reserved by Python and can't be used as a normal
variable name. The next part is the function name, which in this last
example is **to&#95;celcius**. Functions can be named with the same rules as
variables. After the name of the function is a parenthesized list of
parameters. When a function is called (or "invoked") values can be
passed via the parenthesis. The **to&#95;celcius** function expects a single
parameter which is given the name **degrees&#95;f** within the body of the
function.

The **def** line ends with a colon (:) introducing the beginning of the
function body. The body of the function is the indented portion
following the **def**. Optionally, a function may have a return statement.
When a function is invoked, it may use the **return** keyword to signify
the value of the function call. 

Here is what happens in the previous example:

 * The **to&#95;celcius** function is defined.
 * The function is invoked with the value **32.0**.
 * The flow of control passed into the function where the function local
   variable **degrees&#95;f** contains the value **32.0**.
 * The expression "degrees&#95;f - 32.0" is evaluated and assigned to
   the function local variable **x**.
 * The expression "x * 5 / 9" is evaluated (0.0) and returned from the
   function.
 * The value returned from the function call is assigned to the variable
   **degrees&#95;c**.
 * The print function is called and prints out the number 0.0.

Once a function is defined in a program, it can be called multiple
times. Each time it is called, the parameter variables and variables
declared within the function body are recreated. After the function call
ends by getting to the end of the function body or by hitting a return
statement, those function local variables disappear. So, in the previous
example, the variables **degrees&#95;f** and **x** are only defined within
the scope of the function body, and don't exist outside it.

In other words, if we add **print(x)** to the end of the program it will
cause an error:

    # temp.py

    def to_celcius(degrees_f):
        x = degrees_f - 32
        return x * 5 / 9

    degrees_c = t_celcius(32.0)
    print(degrees_c)
    print(x)

The output will be something like this:

    0.0
    Traceback (most recent call last):
      File "temp.py", line 9, in <module>
        print(x)
    NameError: name 'x' is not defined

**Exercise 1:** Write a function called **my&#95;func** that prints a
greeting using the **print** function.

Single line functions
---------------------

If the body of a function in Python is a single line there is an
alternate possible syntax where the function may be defined on a single
line like this:

    def foo(x): return x + 10

Which is identical to the normal form:

    def foo(x):
        return x + 10

**Exercise 2:** Write a single line function with a single parameter
**x** that returns the value of **x** times 10.

A Note on Keywords
------------------

The keyword **def**, used to define a function, has special meaning and
may not be used as a normal variable name:

    >>> def = 10
      File "<stdin>", line 1
        def = 10
            ^
    SyntaxError: invalid syntax

There are a number of other keywords which similarly are reserved and
may not be used as variable names. You can see a list of these by typing
the following in the Python shell:

    >>> import keyword
    >>> keyword.kwlist
    ['False', 'None', 'True', 'and', 'as', 'assert', 'break', 'class', 'continue', 'def', 
    'del', 'elif', 'else', 'except', 'finally', 'for', 'from', 'global', 'if', 'import', 
    'in', 'is', 'lambda', 'nonlocal', 'not', 'or', 'pass', 'raise', 'return', 'try', 
    'while', 'with', 'yield']

Returning Values
----------------

A Python function will execute from beginning to end when the function
is called but may be cut short with a **return** statement. A **return**
statement signifies the value of the function call itself. Sometimes
functions may be used for their side-effects, such as the built-in
function **print** which outputs text to the screen. Other times,
functions are called for the values they return.

A function call that does not return a particular value with a
**return** statement has the special value **None**.

    def foo(x):
        print("hi, there")

    y = foo(10)
    print(y)

The previous code will have the following output:

    hi, there
    None

When the function calls the **print** function, some text is displayed
on the screen, but since it has not **return** value specified the value
of the function call defaults to **None** which is then assigned to the
variable **y** in the above code.

**Exercise 3:** Write a function called **twentytimes** that returns 20
times the value passed to it. Write a function called **printtwenty**
which prints out 20 times the value passed to it.

Parameters
----------

A function may have zero parameters:

    def no_params():
        print("I am a function with no parameters")

Which can be called like this:

    no_params()

A function may have more than one parameter, in which case the
parameters are separated by commas:

    def mult(x,y,z):
        return x * y * z

A function with multiple parameters is called in the same way, by
separating the parameters with commas:

    mult(10, 20, 30)

The way that the parameters work is that the values passed to the
function in the function call are mapped to the names of the parameters
in the function itself.

So the above call to the **mult** function passes three parameters, the
numbers 10, 20 and 30, which are mapped to the parameters **x**, **y**,
and **z**. More specifically, **x** is 10, **y** is 20, and **z** is 30.

**Exercise 4:** Write a function with no parameters called
**my&#95;name** that returns a string containing your name.

Default Parameters
------------------

A function definition may have parameters with default values, like
this:

    def calc_interest(amount, interest = 0.10):
        return amount * interest

The parameters with the default values must always come after the
parameters without default values. The way it works is that if the
function is called with only 1 parameter, the second parameter has the
default value.

    x = calc_interest(100.0)

    y = calc_interest(200.0, 0.07)

    print(x) # prints 10.0
    print(y) # prints 14.0

In the first call above, only the first parameter **amount** is
specified, so in the function call the **interest** value is the default
(0.10). In the second call to the **calc&#95;interest** function, the
second parameter is given as 0.7, so that is the value of **interest**
for the calculation.

**Exercise 5:** Write a function with two parameters **x** and **y**
where **y** has the default value 20 and the function returns the value
of **x** minus the value of **y**.

A Note on Indentation
---------------------

First of all, Python completely ignores empty lines or lines that have
only have comments (comments start with #). Otherwise, Python starts
with no indentation. Nested blocks of code, such as the body of a
function, are delimited by evenly indenting the lines of code for that
block. Some other programming languages define blocks with curly braces
or keywords, but Python just uses indentation. Indented blocks are
always introduced with a colon at the end of the previous line. All
blocks look like the following:

    something :
        statement_1
        statement_2
        ...
        statement_3

Indentation can be any number of spaces or tabs, but it must be
consistent. Normal Python style sets the indentation to 4 spaces, but
single tabs are popular, as well as 2 or 3 spaces. The following code
will cause an error because it violates indendation rules:

    x = 10
     y = 20 # this line will cause an error

However, remember that empty lines or lines with only a comment are
ignored and are exempt from indentation rules.

    x = 10
     #this comment is ok
    #so is this one

    def my_func(x):
        y = x + 10
      #this comment looks funny, but it's legal
        z = y * 99 # this is still part of the function
          # another strange comment
        print(z) # last line of function

    my_name = "Steve"

