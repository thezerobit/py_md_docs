Every *.py* file is a module
----------------------------

In IDLE, if you create a new file by going to the File menu and select
New Window, writing some python and saving the file with a *.py*
extension, you have created a module. Generally speaking, though, a file
that is meant to run as a stand-alone program or script is not referred
to as a module. A module is generally a Python file that contains some
reusable code. Python comes with a large number of modules. In order to
access the modules, you have to *import* them, which is a way of loading
them into memory for use.

As an example of loading a Python library module, let's look at the math
module. You load a module into your program with the *import* statement.

    >>> import math
    >>> math.pi
    3.141592653589793
    >>> math.sqrt(9)
    3.0

Just using the *import* statement brings in the module as an object with
the name of the module. The attributes of the object are the bits of the
module. As you can see the *math* module contains a variable *pi* which
contains the mathematical constant *pi* or at least a decent
approximation. The attribute *sqrt* is a function that returns the
square root of the value passed in.

Python is built in C and therefore inherits a lot of functionality of
the C programming language. You don't need to know any C to use Python,
but it helps to know that some modules, like the *math* module are based
on the math functions available in the standard C library. It may also
help explain the strange names. If the *math* module 

It's easy enough to create your own Python module. For example, you
could create a file called *thing.py* with the following contents:

    my_age = 99

    def say_my_age():
        print("My age is %s!" % my_age)

Now you can create another *.py* file in the same folder called
*my_program.py* with the following contents:

    import thing

    print(thing.my_age)

    thing.say_my_age

If you run *my_program.py* it will print the following:

    99
    My age is 99!

Basically, when a module is included, it is run and any locally defined
variables or functions become attributes of the module itself. You can
import a module multiple times, but it only gets run once. You can test
this out by adding a *print* statement to the module, so *thing.py*
looks like this:

    print("loading module...")
    my_age = 99

    def say_my_age():
        print("My age is %s!" % my_age)

Now, change *my_program.py* to this:

    import thing

    print(thing.my_age)

    import thing

    thing.say_my_age()

The output will be this:

    loading...
    99
    My age is 99!

It's generally bad form to print anything in a module, since the person
using the module probably just wants access to the variables and
functions defined in the module and doesn't want it printing anything to
the screen while it is loading.

Renaming a module on import
---------------------------

Sometimes you may want to call a module something different than its
given name. Let's say we want to load the *thing* module we just created
but we want it to be called *foo*. That's easy, change *my_program.py*
to look like this:

    import thing as foo

    print(foo.my_age)

    foo.say_my_age()

Nearly the same effect can be had by assigning the module to a different
variable name after import:

    import thing
    foo = thing

    print(foo.my_age)

    foo.say_my_age()

The problem with the last example is that now *thing* and *foo* are
defined in the scope of your program. That may or may not be what you
want.

Importing only part of your module
----------------------------------

If you want to just import part of your module, or you want to import
the whole thing into local scope (as though the module were defined in
your program file itself) you can use the *from foo import bar* syntax.

If we just want to load the *say_my_age* function from the *thing*
module, we could do this:

    from thing import say_my_age

    say_my_age()

Notice how you don't need to get to the pieces of the module through a
module object, they are now directly accessible. We could load the
variable *my_age* as well as the function *say_my_age* like this:

    from thing import my_age, say_my_age

    print(my_age)

    say_my_age()

There is a shortcut to importing all the elements of a module into local
scope which is this:

    from thing import *

    print(my_age)

    say_my_age()







