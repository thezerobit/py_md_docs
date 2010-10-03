Python Functions
----------------

In the last section we saw the *print* function. You can also define
your own functions as a way to reuse the same piece of code more than
once without having to type it out more than once.

A common use for functions would be to apply a mathematical
transformation to a value. Here is a function to convert degrees from
Fahrenheit to Celcius:

    def to_celcius(degrees_f):
        x = degrees_f - 32
        return x * 5 / 9

If you put this function definition in a *.py* file, then any line after
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
the keyword *def* which tells Python that you are defining a function.
The name *def* is reserved by Python and can't be used as a normal
variable name. The next part is the function name, which in this last
example is *to_celcius*. Functions can be named with the same rules as
variables. After the name of the function is a parenthesized list of
parameters. When a function is called (or "invoked") values can be
passed via the parenthesis. The *to_celcius* function expects a single
parameter which is given the name *degrees_f* within the body of the
function.

The *def* line ends with a colon (:) introducing the beginning of the
function body. The body of the function is the indented portion
following the *def*. Optionally, a function may have a return statement.
When a function is invoked, it may use the *return* keyword to signify
the value of the function call. 

Here is what happens in the previous example:

 * The *to&#95;celcius* function is defined.
 * The function is invoked with the value *32.0*.
 * The flow of control passed into the function where the function local
   variable *degrees&#95;f* contains the value *32.0*.
 * The expression "degrees&#95;f - 32.0" is evaluated and assigned to
   the function local variable *x*.
 * The expression "x * 5 / 9" is evaluated (0.0) and returned from the
   function.
 * The value returned from the function call is assigned to the variable
   *degrees&#95;c*.
 * The print function is called and prints out the number 0.0.

Once a function is defined in a program, it can be called multiple
times. Each time it is called, the parameter variables and variables
declared within the function body are recreated. After the function call
ends by getting to the end of the function body or by hitting a return
statement, those function local variables disappear. So, in the previous
example, the variables *degrees&#95;f* and *x* are only defined within
the scope of the function body, and don't exist outside it.

In other words, if we add *print(x)* to the end of the program it will
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




