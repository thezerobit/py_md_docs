Python String Manipulation
--------------------------

Manipulating strings, or text, is central to most programming. Python
provides many tools for dealing with strings of text.

One such tool is the % operator. It works like this:

    >>> name = "World"
    >>> sentence = "Hello, %s!" % name
    >>> print(sentence)
    Hello, World!

It will substitute values into the first string %s for strings and %d
for integers.

    >>> first_name = "Jack"
    >>> last_name = "Johnson"
    >>> print("Greetings, %s %s, how are you?" % (first_name, last_name)
    Greetings, Jack Johnson, how are you?
    >>> x = 100
    >>> print("Mr. %s, would you like $%d?" % (last_name, x))
    Mr. Johnson, would you like $100?

To recap, the **%** operator expects a string on the left and a value or values on
the right.

    "string" % value

or

    "string" % (value1, value2, ...)

**Exercise 1:** Using the **%** operator, create a function called
**greeting2** that has a single parameter called **name** that prints a
greeting like this: 

    Hello, **name**!

Except that the **name** is the one passed in the **name** parameter.

Concatenating Strings
---------------------

You can also just connect strings together with the (+) operator.

    >>> print("Hi, " + "there.")
    Hi, there

You can start with small string and build onto it with (+=).

    >>> title = "Mr. "
    >>> title += "Jack "
    >>> title += "Johnson, "
    >>> title += "Esq."
    >>> print(title)
    Mr. Jack Johnson, Esq.

**Exercise 2:** Create a function just like exercise 1, but that uses
the **+** operator to concatenate strings to produce the same result.

Splitting and Joining Strings
-----------------------------

You can split apart a string into an list of substrings on a particular
letter and join it back together with a different letter.

    >>> sentence = 'the quick brown fox jumped over the lazy dog'
    >>> list_of_words = sentence.split(" ")
    >>> print(list_of_words)
    ['the', 'quick', 'brown', 'fox', 'jumped', 'over', 'the', 'lazy', 'dog']
    >>> new_str = ",".join(list_of_words)
    >>> new_str
    'the,quick,brown,fox,jumped,over,the,lazy,dog'

_Note on arrays:_, the split method on strings creates an object called
a list, which is really a container of many objects: strings in this
case. Lists are discussed in more detail in another section.

Converting between numbers and strings
--------------------------------------

You can convert a number to a string. In this case, it is a **float** or
floating point number since it has a fractional component.

    >>> some_number = 1.999
    >>> some_string = str(some_number)
    >>> some_string
    '1.999'
    >>> type(some_number)
    <class 'float'>
    >>> type(some_string)
    <class 'str'>

You can convert a string back to a number.

    >>> thing = '1.999'
    >>> number = float(thing)
    >>> type(number)
    <class 'float'>
    >>> somestring = '100'
    >>> someint = int(somestring)
    >>> type(someint)
    <class 'int'>

**Exercise 3:** Write a function that takes a single parameter **s**,
converts that to a float and returns that number divided by 10.

Extracting Individual Characters
--------------------------------

One thing to note about strings is that they cannot be changed. Any
operations that look like they are changing strings, are really just
creating brand new strings from the old ones. The technical term for
this is **immutable**, which means unchanging.

You can select certain characters from a string. This is how to extract
the first letter in a string and the third letter:

    >>> title = "captain"
    >>> letter = title[0]
    >>> letter
    'c'
    >>> third_letter = title[2]
    >>> third_letter
    'p'

In the code above, what is returned from using the square brackets is a
string with a single letter in it, a new string that does not change the
original in any way.

**Exercise 4:** Using the square bracket syntax above and string
concatenation, write a function called **shorten** that takes a single
parameter **name**, assuming it is a string, construct a new string
using the first, third and fifth letters in **name** and return that
value. So if you called the function like this: shorten('Frank'), it
would return the string 'Fak' which is the first, third and fifth
letters of 'Frank' concatenated together.

Equality of Strings
-------------------

You can compare strings using the **==** operator.

    >>> "hi" == 'hi'
    True
    >>> 'hi' == 'Hi'
    False

As you can see, the single or double quote marks don't make different
strings. However, capitalization does make a difference.

Getting Input From User
-----------------------

In simple Python program, the easiest way to get input from the user is
with the **input** function. This is how you might get the user to give
you his or her name:

    name = input("please enter your name: ")
    print("Hello, %s!" % name)

When you run this program, it will first show a prompt:

    please enter your name: 

It will wait for the user to type something and hit enter. Whatever it
is that the user enters will then become a string assigned to the
variable **name** and the program execution will continue on..

    please enter your name: Steve
    Hello, Steve!

The **input** function always returns a string value, even if the user
enters numerical digits.

    >>> something = input("How old are you? ")
    How old are you? 99
    >>> something
    '99'
    >>> type(something)
    <class 'str'>

If you want to use the input as a number, it needs to be converted as
shown earlier.

**Exercise 5:** Create a Python file called **yourage.py**. This program
should ask the user to enter their age and enter their name. The program
should calculate how many years until the person is 111 years old and
then print out the following:

    Greeting, <person's name>, you will be 111 years young in <xx> years!

Of course the program should use the name entered by the user and the
number of years calculated until the person is 111.

