Loops
=====

The **while** Loop
----------------

A **while** block is very similar to an **if** block, with the one
difference is that when the block ends, the flow of execution jumps back
to the beginning, checks the condition again, and executes the block
again. This process continues until the condition becomes false or the
**break** statement is reached. Consider the following code:

    x = 0
    while x < 5:
        print(x)
        x = x + 1
    print("done!")

This little block of code will print out the following:

    0
    1
    2
    3
    4
    done!

It is a simple loop. In each iteration, the value of **x** is printed to
the screen and then incremented. Since the value of x is set to 5
**after** being printed out during the fifth iteration through the loop,
we never get to see the number 5. Notice the output of this code is
slightly different:

    x = 0
    while x < 5:
        x = x + 1
        print(x)
    print("done!")

It looks like this:

    1
    2
    3
    4
    5
    done!

After the value of x is set to 5, the value is printed out. The
condition is not checked until the end of the loop iteration.

Care must be taken to ensure that you do not create an infinite loop. If
you do, usually a running program can be killed by hitting Ctrl-C.

    # This is an infinite loop!
    x = 10
    while x > 5:
        print(x)

In that loop, **x** never changes, so the condition will always be
**True**.  However, it is commonly used idiom to set up a simple loop
with **while True:** and just have the loop exit on **break**:

    x = 0
    while True:
        x = x + 1
        if x > 5:
            break
        print(x)

While loops are useful for loops with an indefinite number of
iterations. For example, if your program needs to have the user enter in
a number of names, you could write something like this:

    names = [] # create an empty list to store names

    while True:
        name = input("Please enter a name, or 'done': ")
        if name == 'done':
            break
        names.append(name)

    print("You have entered %d names." % len(names))
    print(names)

A test run of this program might look something like this:

    Please enter a name, or 'done': Steve
    Please enter a name, or 'done': Frank
    Please enter a name, or 'done': Bob
    Please enter a name, or 'done': done
    You have entered 3 names.
    ['Steve', 'Frank', 'Bob']

**Exercise 1:** Create a program called **guess.py** that picks a number
between 1 and a 100 without telling the user (use **import random** and
**random.randint(1,100)** to generate number). The program should use a
**while** and ask the user to guess the number. If the user guesses the
number correctly, the loop should end and program should congratulate
the user. Otherwise, the program should tell the user if the number is
higher or lower than their guess and continue to loop, allowing the user
to guess until the correct number is found. A test run of the program
should look something like this:

    Guess the number: 35
    Too high!
    Guess the number: 20
    Too high!
    Guess the number: 10
    Too low!
    Guess the number: 15
    Too low!
    Guess the number: 17
    You got it. Goodbye...

The **for** loop
--------------

Python has a very easy syntax for looping through the elements of a
sequence or any object that appears to be a sequence. The most obvious
would be a list.

    some_list = ["this", "that", "other"]

    for word in some_list:
        length = len(word)
        print("The word '%s' has a length of %d." % (word, length))

The line introducing the **for** loop always has this form: **for <var>
in <sequence>:**.  The block executes once for each element in the list
and the variable specified right after the for statement (**word** in
this case) holds a reference to the element for the loop. So the above
code would print out the following:

    The word 'this' has a length of 4.
    The word 'that' has a length of 4.
    The word 'other' has a length of 5.

This also works with tuples and other sequences.

    my_tuple = (1,2,3)

    for num in my_tuple:
        ten_times = num * 10
        print("%d is ten times %d" % (ten_times, num))

    my_string = "Hello"

    for letter in my_string:
        print(letter)

In the case of looping over a string, each character in the string is
considered an element.

**Exercise 2:** Write a program called **names.py** that has the user
enter a list of names.  The program should then use a for loop to
construct another list of capitalized versions of the names entered by
the user and print that. (Elements are added to a list with the
**append** method.  Strings will return a capitalized version of
themselves with the **capitalize** method).

    >>> name = "steve"
    >>> name.capitalize()
    'Steve'
    >>> l = []
    >>> l.append("foo")
    >>> l
    ['foo']

The **range** object
--------------------

For iterating a specific number of times, Python has a handy thing
called a **range**. It's easiest perhaps to see it in action:

    >>> for x in range(5):
    ...     print(x)
    ... 
    0
    1
    2
    3
    4

A **range** object is created by calling the **range** function.

    >>> r = range(5)
    >>> r
    range(0, 5)
    >>> for num in r:
    ...     print(num * 10)
    ... 
    0
    10
    20
    30
    40

A range has a starting value, a step and an end. By default the starting
value is 0 and the step is 1. The range will allow you to iterate from
the beginning to the end, but it exits before you reach the end, so a
**range(5)** iterates from 0 through 4. You can be more specific and
specify the start and the end:

    >>> r2 = range(5,10)
    >>> for x in r2: print(x)
    ... 
    5
    6
    7
    8
    9

You can also specify the step as the third number:

    >>> r3 = range(5,10, 2)
    >>> for x in r3: print(x)
    ...
    5
    7
    9

This allows iterating in reverse:

    >>> r4 = range(10,0,-1)
    >>> for x in r4: print(x)
    ... 
    10
    9
    8
    7
    6
    5
    4
    3
    2
    1

**Exercise 3:** Write a program called **restaurant.py** that asks the
user to enter in exactly 5 restaurant names. The program then selects
one of the entered restaurants at random.

Iterating over dictionaries
---------------------------

Elements in dictionaries (key/value pairs) are not guaranteed to exist
in any particular order within a dictionary. However, it is occasionally
useful to iterate over the elements in a dictionary. Dictionaries
provide two methods, **keys** and **values** which return sequence-like
objects that can be used to loop over the contents of a dictionary.
These objects are merely "views" into either the keys or values of a
given dictionary. Perhaps it is best to see them in action.

    >>> info = {'name' : 'Steve', 'age' : 31, 'hair' : 'brown'}
    >>> info_keys = info.keys()
    >>> info_keys
    dict_keys(['hair', 'age', 'name'])
    >>> for key in info_keys: print(key)
    ... 
    hair
    age
    name
    >>> info['eyes'] = 'brown/green'
    >>> info_keys
    dict_keys(['hair', 'age', 'eyes', 'name'])
    >>> info_values = info.values()
    >>> for val in info_values: print(val)
    ... 
    brown
    31
    brown/green
    Steve

You can use them directly to loop over the contents of a dictionary, but
treating the dictionary itself as the sequence, produces the same
results as looping over the keys.

    >>> for key in info: print(key)
    ... 
    hair
    age
    eyes
    name

Since the **in** membership test operator only checks the keys of a
dictionary, the **values** method can come in handy:

    >>> 'hair' in info
    True
    >>> 'brown' in info
    False
    >>> 'brown' in info.values()
    True

Keeping your dictionaries in order with OrderedDict
---------------------------------------------------

There is a type of dictionary in Python that keeps its key/value pairs
in the same order that you added them. It is called an **OrderedDict**.
In order to use this class, you must import it from the collections
module:

    from collections import OrderedDict

It works much like a normal dictionary, but iterating over the keys or
values always happens in the same order that they were added to the
dictionary initially.

    >>> d = OrderedDict()
    >>> d['name'] = 'Steve'
    >>> d['hair'] = 'brown'
    >>> d['age'] = 31
    >>> for key in d: print(key)
    ... 
    name
    hair
    age
    >>> for val in d.values(): print(val)
    ...
    Steve
    brown
    31

There is a way to create an **OrderedDict** without adding each
key/value pair one at a time by using a **list** of **tuples**.

    >>> info = OrderedDict([('name', 'Steve'), ('hair', 'brown'), ('age', 31)])


