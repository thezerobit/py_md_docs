Python Types
------------

Just about everything in Python is an object. All objects have a *type*
which is also known as a *class*. The term *class* comes from
classification, a way of organizing similar things. We've already
explored some types in Python. There is the integer or *int* type:

    >>> 1
    1
    >>> type(1)
    <class 'int'>
    >>> x = 1001
    >>> type(x)
    <class 'int'>
    >>> type(x) == int
    True
    >>> y = int()
    >>> y
    0
    >>> type(y)
    <class 'int'>
    >>> int
    <class 'int'>
    >>> type(int)
    <class 'type'>

Integers all belong to the *int* class. As you may have noticed from the
code above, there is an actual object with the name *int* which is a of
class *type*. It is a class object that all integers share. The *type*
function returns the class of an object. When you pass it an integer it
returns the *int* class object. You can invoke the object, like a
function, to create a new integer. If you pass it nothing, it returns
the integer 0. You can pass it an integer and it will return that same
integer. You can also pass it a string and it will try to convert that
into an integer.

    >>> int()
    0
    >>> int(9)
    9
    >>> int("99")
    99

That's pretty handy. You can use this to see if an object is an integer
by comparing the class object returned by the *type* call.

    >>> x = 100
    >>> y = "hello"
    >>> z = "100"
    >>> 
    >>> type(x) == int
    True
    >>> type(y) == int
    False
    >>> type(z) == int
    False

There is another way to check for types, using the *isinstance* function
which takes an object and a type, and returns *True* if the object is of
that type or *False* otherwise.

    >>> x = 100
    >>> y = "100"
    >>> isinstance(x, int)
    True
    >>> isinstance(y, int)
    False

So, objects have a type. Many objects can share the same type. You can
have many integers. The other types we've seen are strings (*str*),
booleans (*bool*), ranges, lists, tuples, and dictionaries (*dict*).

    >>> type([1, 2, 3])
    <class 'list'>
    >>> type((1, 2, 3))
    <class 'tuple'>
    >>> type({ "a" : "b" })
    <class 'dict'>
    >>> type(True)
    <class 'bool'>
    >>> type(range(10))
    <class 'range'>
    >>> type("hi, there")
    <class 'str'>

User Defined Types
------------------

You can define your own classes in Python. This is a very powerful
feature and programs of any significant size generally contain many such
definitions. Instead of enumerating all the benefits of defining your
own classes, let's just look at some examples. 

If we wanted to build a card game, we would need to create a
representation of playing cards. The most obvious way to do this would
be to create a *Card* class to represent cards and then we could create
and manipulate cards with ease. Here's a simple class:

    class Card:
        pass

A class definition is similar to a function definition. The *pass*
keyword in the above example is like an empty place-holder. The body of
the *Card* class is empty, but it can still be used, surprisingly.

    >>> c = Card()
    >>> c
    <__main__.Card object at 0x22dff90>
    >>> type(c) == Card
    True
    >>> isinstance(c, Card)
    True

So, even with an empty class definition, we can still create objects and
use them and differentiate them from other objects. There is, however, a
lot more we can do.

Attributes
----------

All objects in Python have attributes which you can access using the dot
syntax:

    >>> x = "hello"
    >>> x.__class__
    <class 'str'>

Objects of user-defined types can contain arbitrary attributes which are
created through assignment.

    >>> class Something:
    ...     pass
    ... 
    >>> s = Something()
    >>> isinstance(s, Something)
    True
    >>> s.my_attribute
    Traceback (most recent call last):
      File "<stdin>", line 1, in <module>
    AttributeError: 'Something' object has no attribute 'my_attribute'
    >>> s.my_attribute = 10
    >>> s.my_attribute
    10

As you can see, you can't just access an attribute until it has been
created with an assignment statement (that is the one with the single
equal sign). In the above example, I created an empty class called
*Something*, created an instance of that class, and then tried to read
the attribute *my_attribute*. That caused an error, since the object
didn't already have that attribute. Then, I created an attribute called
*my_attribute* on the object using assignment. After that point, it was
available for use.

We need a way to represent playing cards, so let's say that the rank and
suit of the card can be represented with integers. We could say that the
suits are represented by the integers 1 through 4 and the rank by the
integers 1 through 13, 1 being Ace, 11 Jack, 12 Queen, and 13 King. The
number cards are easy to remember, but we'll need some definitions for
the others. 

    CLUBS = 1
    DIAMONDS = 2
    HEARTS = 3
    SPADES = 4

    ACE = 1
    JACK = 11
    QUEEN = 12
    KING = 13

    class Card:
        pass

Upper-case names are usually used in Python to represent constants
(values that will not change). We could use this code and set *suit* and
*rank* attributes on the card objects.

    >>> c = Card()
    >>> c.rank = ACE
    >>> c.suit = CLUBS

Of course, we'll have to be very careful to specify the *rank* and
*suit* every time we create a card, or there could be problems:

    >>> c = Card()
    >>> c.rank = ACE
    >>> c.suit = CLUBS
    >>> 
    >>> d = Card()
    >>> d.rank = ACE
    >>> 
    >>> c.rank == d.rank
    True
    >>> c.suit == d.suit
    Traceback (most recent call last):
      File "<stdin>", line 1, in <module>
    AttributeError: 'Card' object has no attribute 'suit'

We'll see how to make sure that objects of type *Card* have the proper
attributes a little later.

Object Methods
--------------

Objects can have functions defined in their classes. Usually these
functions are called *methods*, but they look very much like functions.
They look like this:

    class Card:
        def get_suit_name(self):
            if self.suit == CLUBS:
                return "clubs"
            elif self.suit == HEARTS:
                return "hearts"
            elif self.suit == DIAMONDS:
                return "diamonds"
            else:
                return "spades"

The way this works is that you call it on an instance of the *Card*
class and the first parameter, *self*, points to the object itself.
Here's an example:

    >>> c = Card()
    >>> c.rank = 3
    >>> c.suit = HEARTS
    >>> 
    >>> c.get_suit_name()
    'hearts'

When the method *get_suit_name* was called on the object *c*, the
*get_suit_name* function in the *Card* class definition was called. The
parameter *self* in that call was the same object represented by *c*.
Since I had defined the *suit* attribute on that objects as *HEARTS*,
the function returned the string "hearts".

Now, what happens if we haven't defined a *suit* attribute? Trouble.

    >>> d = Card()
    >>> d.get_suit_name()
    Traceback (most recent call last):
      File "<stdin>", line 1, in <module>
      File "blackjack.py", line 13, in get_suit_name
        if self.suit == CLUBS:
    AttributeError: 'Card' object has no attribute 'suit'

It turns out there is a magical method name that always gets called when
an object is instantiated called _ _ init _ _ . (That's with two underscores
on each side.) You can create it like this:

    class Something:
        def __init__(self):
            print("hello")

Now that method will get called each time you create an object of that
type:

    >>> s = Something()
    hello

Like any function, we can add parameters. Let's do that with the Card
class as a way of creating the *rank* and *suit* attributes:

    class Card:
        def __init__(self, suit, rank):
            self.suit = suit
            self.rank = rank
        def get_suit_name(self):
            if self.suit == CLUBS:
                return "clubs"
            elif self.suit == HEARTS:
                return "hearts"
            elif self.suit == DIAMONDS:
                return "diamonds"
            else:
                return "spades"

Building a Deck of Cards
------------------------

If we are creating a card game, it might be handy to create a class to
represent a deck of cards. Here is such a class:

    class Deck:
        def __init__(self):
            self.cards = []
        def add_card(self, card):
            self.cards.append(card)
        def how_many(self):
            return len(self.cards)
        def create_standard(self):
            for suit in range(1,5):
                for rank in range(1,14):
                    self.add_card(Card(suit,rank))

This class has an attribute that is just a list containing *Card*
objects. It has some other helpful methods. One thing we might want to
add to this is a shuffle method that randomizes the order of the cards.
One way to do this would be to create another empty list, and then take
a random card from the main list and move it to the second list. Do this
until the first list is empty and then assign the new list as the
*cards* attribute of the deck, effectively replacing it.

We also should add some methods to the *Card* class to be able to print
out what type of card it is. If we put it all together in one file, it
might look like this:

    import random

    CLUBS = 1
    DIAMONDS = 2
    HEARTS = 3
    SPADES = 4

    ACE = 1
    JACK = 11
    QUEEN = 12
    KING = 13

    class Card:
        def __init__(self, suit, rank):
            self.suit = suit
            self.rank = rank
        def get_suit_name(self):
            if self.suit == CLUBS:
                return "clubs"
            elif self.suit == HEARTS:
                return "hearts"
            elif self.suit == DIAMONDS:
                return "diamonds"
            else:
                return "spades"
        def get_rank_name(self):
            if self.rank == ACE:
                return "ace"
            elif self.rank == JACK:
                return "jack"
            elif self.rank == QUEEN:
                return "queen"
            elif self.rank == KING:
                return "king"
            else:
                return str(self.rank)
        def get_name(self):
            return "%s of %s" % (self.get_rank_name(), self.get_suit_name())

    class Deck:
        def __init__(self):
            self.cards = []
        def add_card(self, card):
            self.cards.append(card)
        def how_many(self):
            return len(self.cards)
        def create_standard(self):
            for suit in range(1,5):
                for rank in range(1,14):
                    self.add_card(Card(suit,rank))
        def shuffle(self):
            new_list = []
            while(len(self.cards) > 0):
                cards_left = len(self.cards)
                card_pick = random.randint(0,cards_left - 1)
                new_list.append(self.cards.pop(card_pick))
            self.cards = new_list

It would be good to try this out. The easiest way to do this is to save
the file in IDLE as something like "cards.py", then select "Run Module"
(hit F5). That brings up the shell where we can play around with these
classes and verify that they do what we expect:

    >>> c = Card(CLUBS, 3)
    >>> c.get_name()
    '3 of clubs'
    >>> d = Deck()
    >>> d.how_many()
    0
    >>> d.create_standard()
    >>> d.how_many()
    52
    >>> d.cards[0].get_name()
    'ace of clubs'
    >>> d.cards[2].get_name()
    '3 of clubs'
    >>> d.cards[12].get_name()
    'king of clubs'
    >>> d.cards[13].get_name()
    'ace of diamonds'
    >>> d.cards[14].get_name()
    '2 of diamonds'
    >>> d.shuffle()
    >>> d.cards[0].get_name()
    '7 of diamonds'
    >>> 
    >>> d.cards[1].get_name()
    'ace of hearts'
    >>> d.cards[2].get_name()
    '5 of diamonds'
    >>> d.cards[3].get_name()
    'jack of clubs'

As you can see, when you create a deck, all the cards are in order.
After calling the *shuffle* method, they are randomized. We are on the
way to building our very own card game.

