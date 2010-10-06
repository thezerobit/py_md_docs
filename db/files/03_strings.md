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

You can split apart a string into an array of parts on a particular
letter and join it back together with a different letter.

    >>> st = 'the quick brown fox jumped over the lazy dog'
    >>> arr = st.split(" ")
    >>> print(arr)
    ['the', 'quick', 'brown', 'fox', 'jumped', 'over', 'the', 'lazy', 'dog']
    >>> new_str = ",".join(arr)
    >>> new_str
    'the,quick,brown,fox,jumped,over,the,lazy,dog'

You can convert a number to a string.

    >>> some_number = 1.999
    >>> some_string = str(some_number)
    >>> some_string
    '1.999'
    >>> type(some_number)
    <class 'float'>
    >>> type(some_string)
    <class 'str'>

You can convert a string to a number

    >>> thing = '1.999'
    >>> number = float(thing)
    >>> type(number)
    <class 'float'>

You can select certain characters from a string.

    >>> title = "captain"
    >>> letter = title[0]
    >>> letter
    'c'

You can compare strings.

    >>> "hi" == 'hi'
    True
    >>> 'hi' == 'Hi'
    False

As you can see, the single or double quote marks don't make different
strings. However, capitalization does make a difference.

Getting Input From User
-----------------------

In simple Python program, the easiest way to get input from the user is
with the *input* function. This is how you might get the user to give
you his or her name:

    name = input("please enter your name: ")
    print("Hello, %s!" % name)

When you run this program, it will first show a prompt:

    please enter your name: 

It will wait for the user to type something and hit enter. Whatever it
is that the user enters will then become a string assigned to the
variable *name* and the program execution will continue on..

    please enter your name: Steve
    Hello, Steve!


