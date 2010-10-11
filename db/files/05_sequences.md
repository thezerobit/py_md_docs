Python Lists
------------

In Python, a list is an ordered collection of values. Those values may
be any values that could be stored in a regular variable, like numbers,
strings, boolean values, other lists, etc. Similar structures in other
programming languages are often called arrays, although Python has an
array module which has data structures for the efficient storage of
numerical data.

Lists can be constructed using square brackets:

    >>> my_list = ["a","b","c"]
    >>> my_list
    ['a', 'b', 'c']
    >>> type(my_list)
    <class 'list'>

Elements can be accessed using the square bracket syntax, using 0-based
element indexes for either retrieval or assignment.

    >>> my_list[1]
    'b'
    >>> my_list[0] = "x"
    >>> my_list
    ['x', 'b', 'c']

Lists are mutable, which means they can be modified. They can be
modified other than through assignment in the previous example. You can
add (append) values to the end of the list or remove (pop) values from
the end of the list.

    >>> my_list
    ['x', 'b', 'c']
    >>> my_list.append("d")
    >>> my_list
    ['x', 'b', 'c', 'd']
    >>> my_list.pop()
    'd'
    >>> my_list
    ['x', 'b', 'c']

Elements may be inserted into any position using the insert method.

    >>> my_list.insert(0, "a")
    >>> my_list
    ['a', 'x', 'b', 'c']

The *pop* method can also take a positional parameter to remove an
element at a specific location. Notice that *pop* always returns the
value of the element it is removing.

    >>> my_list.pop(1)
    'x'
    >>> my_list
    ['a', 'b', 'c']

Tuples: Immutable Sequence
--------------------------

There is a data type in Python that is much like a list, but once they
are created, they cannot be changed. The syntax is just a little
different for tuples. They are constructed with parentheses instead of
square brackets.

    >>> my_tuple = ("fun", "not-fun")
    >>> my_tuple
    ('fun', 'not-fun')
    >>> type(my_tuple)
    <class 'tuple'>
    >>> my_tuple[0]
    'fun'
    >>> my_tuple[1]
    'not-fun'
    >>> my_tuple.append("more-fun?")
    Traceback (most recent call last):
      File "<stdin>", line 1, in <module>
    AttributeError: 'tuple' object has no attribute 'append'

As you can see, you cannot *append* values to a tuple. If you want to
construct a tuple of a single element, it must be followed with a comma.
Otherwise, Python just thinks the parentheses exist to grouping, like
you might do with a mathematical equation.

    >>> ("1",)
    ('1',)
    >>> ("1")
    '1'

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

You can convert between tuples and lists using the *list* and *tuple*
commands:

    >>> my_list = ["this", "that", "the other thing"]
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

Dictionaries
------------

A Python dictionary is a mapping of unique keys to values. A key in a
dictionary can be any immutable value, like a number, string or even a
tuple. The values that the keys point to can be any Python value.
Dictionaries are constructed with the curly braces *{}* with colons *:*
to separate the key and the value, with commas between each pair:

    >>> my_dict = {"a" : 10, "b" : 10}
    >>> my_dict
    {'a': 10, 'b': 10}
    >>> len(my_dict)
    2

Dictionaries are mutable, which means they can be changed. Elements may
be reference via square brackets, using the key:

    >>> my_dict["a"]
    10
    >>> my_dict["b"]
    10
    >>> my_dict["c"] = 20
    >>> my_dict["c"]
    20
    >>> my_dict
    {'a': 10, 'c': 20, 'b': 10}

Dictionaries are unordered, so the order that the keys are added doesn't
necessarily reflect what order they may be reported back. While it is
common to use strings as the keys, it is not a requirement:

    >>> w = { 1 : "thing", "this" : "another thing", (1,2) : "a tuple!" }
    >>> w
    {'this': 'another thing', 1: 'thing', (1, 2): 'a tuple!'}
    >>> w[(1,2)]
    'a tuple!'

Dictionaries are very similar to data structures found in other
languages. In Ruby or Perl, it is a *hash*. In JavaScript it would be an
*object*. In C++, it might be a *map*. The name *dictionary* emphasizes
the fact that you can look up values, as you might in a real dictionary.

    >>> definitions = { "ray" : "a drop of golden sun", "me" : "a name I call myself" }
    >>> definitions["me"]
    'a name I call myself'
