Python Lists
------------

In Python, a list is an ordered collection of values. Those values may
be any values that could be stored in a regular variable, like numbers,
strings, boolean values, other lists, etc. Similar structures in other
programming languages are often called arrays, although Python has an
array module which has data structures for the efficient storage of
numerical data.

Lists can be constructed using square brackets:

    >>> my_list = ['a','b','c']
    >>> my_list
    ['a', 'b', 'c']
    >>> type(my_list)
    <class 'list'>

Elements can be accessed using the square bracket syntax, using 0-based
element indexes for either retrieval or assignment.

    >>> my_list[1]
    'b'
    >>> my_list[0] = 'x'
    >>> my_list
    ['x', 'b', 'c']

Lists are mutable, which means they can be modified. They can be
modified other than through assignment in the previous example. You can
add (**append**) values to the end of the list or remove (**pop**)
values from the end of the list.

    >>> my_list
    ['x', 'b', 'c']
    >>> my_list.append('d')
    >>> my_list
    ['x', 'b', 'c', 'd']
    >>> my_list.pop()
    'd'
    >>> my_list
    ['x', 'b', 'c']

The **pop** method also returns the value removed from the list.

    >>> my_list = ['x', 'b', 'c']
    >>> y = my_list.pop()
    >>> y
    'c'
    >>> my_list
    ['x', 'b']

Elements may be inserted into any position using the **insert** method.

    >>> my_list = ['a', 'b', 'c']
    >>> my_list.insert(0, 'x')
    >>> my_list
    ['x', 'a', 'b', 'c']

The *pop* method can also take a positional parameter to remove an
element at a specific location. Notice that *pop* always returns the
value of the element it is removing.

    >>> my_list = ['a', 'b', 'c']
    >>> my_list.pop(1)
    'b'
    >>> my_list
    ['a', 'c']

**Exercise 1:** Write some code that asks a user to enter his or her
name, age and favorite cupcake flavor and constructs a list with those
three values called **userinfo**.

Tuples: Immutable Sequence
--------------------------

There is a data type in Python that is much like a list, but once they
are created, they cannot be changed. The syntax is just a little
different for tuples. They are constructed with parentheses instead of
square brackets.

    >>> my_tuple = ('fun', 'not-fun')
    >>> my_tuple
    ('fun', 'not-fun')
    >>> type(my_tuple)
    <class 'tuple'>
    >>> my_tuple[0]
    'fun'
    >>> my_tuple[1]
    'not-fun'
    >>> my_tuple.append('more-fun?')
    Traceback (most recent call last):
      File "<stdin>", line 1, in <module>
    AttributeError: 'tuple' object has no attribute 'append'

As you can see, you cannot **append** values to a tuple. If you want to
construct a tuple of a single element, it must be followed with a comma.
Otherwise, Python just thinks the parentheses exist to grouping, like
you might do with a mathematical equation.

    >>> (1,) # this is a tuple
    (1,)
    >>> (1) # this is not a tuple, just a single value
    1

Tuples have a number of uses. They are used to return multiple values
from a function. The values can be automatically unpacked in an
assignment.

    >>> def splitter(x):
    ...     return (-x, x)
    ... 
    >>> splitter(1)
    (-1, 1)
    >>> a,b = splitter(1)
    >>> a
    -1
    >>> b
    1

There is such a thing as an empty, or zero-element tuple, though the
reasons for its existence are questionable.

    >>> empty = ()
    >>> empty
    ()
    >>> type(empty)
    <class 'tuple'>
    >>> empty[0]
    Traceback (most recent call last):
      File "<stdin>", line 1, in <module>
    IndexError: tuple index out of range
    >>> len(empty)
    0

You can convert between tuples and lists using the **list** and **tuple**
functions.

    >>> my_list = ['this', 'that', 'the other thing']
    >>> my_list
    ['this', 'that', 'the other thing']
    >>> my_tuple = tuple(my_list)
    >>> my_tuple
    ('this', 'that', 'the other thing')
    >>> list_again = list(my_tuple)
    >>> list_again
    ['this', 'that', 'the other thing']
    >>> list_again == my_list
    True

**Exercise 2:** Do the same thing as exercise 1, but create a tuple
called **userinfotuple** instead of a list.

Dictionaries
------------

A Python dictionary is a mapping of unique keys to values. A key in a
dictionary can be any immutable value, like a number, string or even a
tuple. The values that the keys point to can be any Python value.
Dictionaries are surrounded with the curly braces **{}** and have colons
**:** to separate the key and the value, with commas between each pair:

    >>> my_dict = {'a' : 10, 'b' : 10}
    >>> my_dict
    {'a': 10, 'b': 10}
    >>> len(my_dict)
    2

Dictionaries are mutable, which means they can be changed. Elements may
be reference via square brackets, using the key:

    >>> my_dict = {'a' : 10, 'b' : 10}
    >>> my_dict['a']
    10
    >>> my_dict['b']
    10
    >>> my_dict['c'] = 20
    >>> my_dict['c']
    20
    >>> my_dict
    {'a': 10, 'c': 20, 'b': 10}

Dictionaries are unordered, so the order that the keys are added doesn't
necessarily reflect what order they may be reported back. While it is
common to use strings as the keys, it is not a requirement:

    >>> w = { 1 : 'thing', 'this' : 'another thing', (1,2) : 'a tuple!' }
    >>> w
    {'this': 'another thing', 1: 'thing', (1, 2): 'a tuple!'}
    >>> w[(1,2)]
    'a tuple!'

Dictionaries are very similar to data structures found in other
languages. In Ruby or Perl, it is a **hash**. In JavaScript it would be
an **object**. In C++, it might be called a **map**. The name
**dictionary** emphasizes the fact that you can look up values, as you
might in a real dictionary.

    >>> definitions = { 'ray' : 'a drop of golden sun', 'me' : 'a name I call myself' }
    >>> definitions['me']
    'a name I call myself'

**Exercise 3:** Do the same thing as exercise 2, but instead of a list,
create a dictionary called **userinfodict** with these three keys:
'name', 'age', and 'flavor'.  The values associated with those keys are
the values entered by the user.

Commonalities Among Sequences
-----------------------------

In Python, there are a variety of standard ways to interact with
sequences. For example, the **len()** function will return the number of
elements in a sequence (it only returns the number of pairs in a
dictionary). 

    >>> my_string = 'this is a sequence of characters'
    >>> len(my_string)
    32
    >>> my_list = [1, 2, 3, 4]
    >>> len(my_list)
    4
    >>> my_tuple = ('a', 'b', 'c')
    >>> len(my_tuple)
    3
    >>> my_dict = {1 : 'a', 2 : 'b', 3 : 'c'}
    >>> len(my_dict)
    3

You can always access elements of a sequence by passing in an index
using the square brackets. For most sequences, you access the elements
numerically, with 0 representing the first element. For dictionaries,
you must use the key of the key/value pair.

    >>> my_dict = {1 : 'a', 2 : 'b', 3 : 'c'}
    >>> len(my_dict)
    3
    >>> my_string = 'this is a sequence of characters'
    >>> my_string[2]
    'i'
    >>> my_list = ['this', 'is', 'a', 'list']
    >>> my_list[0]
    'this'
    >>> my_list[0][0]
    't'
    >>> my_dict = {'a' : 'one', 'b' : 'two'}
    >>> my_dict['a']
    'one'
    >>> my_dict['b']
    'two'
    >>> my_dict['c']
    Traceback (most recent call last):
      File "<stdin>", line 1, in <module>
    KeyError: 'c'

As you can see, you must be careful to use a valid index to access the
elements of a sequence. For linear sequences (string, list, tuple) you
can always check the length first to make sure that you can access a
certain element.

    >>> my_list = ['this', 'and', 'that']
    >>> if len(my_list) > 2: print(my_list[2])
    ... 
    that
    >>> if len(my_list) > 3: print(my_list[3])
    ... 

For dictionaries, you can check if a key exists in a given dictionary by
using the **in** operator like this:

    >>> my_dict = {'a' : 'one', 'b' : 'two'}
    >>> 'a' in my_dict
    True
    >>> 'b' in my_dict
    True
    >>> 'c' in my_dict
    False
    >>> if 'a' in my_dict: print(my_dict['a'])
    ... 
    one
    >>> if 'c' in my_dict: print(my_dict['c'])
    ... 

**Exercise 4:** Write a function that takes 2 parameters. The first
parameter will be called 'd' and you should expect that to be a
dictionary. The second parameter called 'key' will be a value that may
or may not be a key in the dictionary. The third parameter will be
called 'default'. The purpose of the function is to check if the 'key'
parameter is indeed a key in the dictionary (use **in**). If it is,
return the value stored at that key, otherwise return the value of the
'default' parameter. You most likely need to use **if** / **else**
blocks to write this function.

