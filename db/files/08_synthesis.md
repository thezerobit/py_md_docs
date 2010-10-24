Synthesis: Making a simple Python Game
--------------------------------------

We've covered a fair bit of the Python language so far. The best way to
learn a programming language is by using it, so let's put the elements
we've covered together to produce a simple game.

First we need to create a Python file that will eventually be the game.
One way to do this is to open up IDLE (if you have multiple versions of
Python installed, make sure to open IDLE 3, so you are working with
Python 3). In the *File* menu select *New Window*. That should open a
text editor window with *Untitled* as the title. Add this as the first
line of the file, alter the details to taste:

    # my_game.py : a game by Billy Bob

Then you need to save the file. If you select *Save* or *Save As* from
the *File* menu, you should see a *Save As* dialog, asking you where to
save the file and what to call it. You should navigate to a folder that
you might use for projects like this, and set the file name to
*my_game.py* or any name as long as it ends with *.py*. Click *Save*.
Now the title of the editor window should reflect the name you saved it
as.

Add some simple output, letting the user know that there is a game:

    print("Hello, welcome to My Game!")

So now your file should look like this:

    # my_game.py : a game by Billy Bob

    print("Hello, welcome to My Game!")

There doesn't need to be an empty line between the comment at the top
and the *print* line, but I often leave empty lines in my code to make
it easier to read. Most programmers do this. Now, this is a simple
program, although all it does is print out a single line. Run this by
selecting the *Run Module* option from the *Run* menu at the top. At
this point, if you haven't saved your changes, IDLE will ask you if it
is OK to save. Click *OK*. At this point, your program will run in the
first IDLE window with the title *Python Shell*. You may have to switch
to this window. you should see something like this:


    Python 3.1.2 (release31-maint, Sep 17 2010, 20:27:33) 
    [GCC 4.4.5] on linux2
    Type "copyright", "credits" or "license()" for more information.
    ==== No Subprocess ====
    >>> 
    >>> 
    Hello, welcome to My Game!
    >>> 

You can ignore all that stuff at the top of the screen. What's important
is that it printed your message, and then gave you a prompt. When
running Python programs like this one in IDLE, instead of immediately
exiting when completed, you have access to the Python shell in case you
wanted to examine variables or execute more code in the context of the
program you wrote. From now on, I'll refer to this window as the *shell*
and the window where you are editing your program as the *editor*.

So far the program *my_game.py* doesn't really live up to it's hype,
it's not a game yet. Let's fix that. One very simple game is just a
guessing game, one whose odds favor the house. It's a game where you pay
$5 and guess which of three cups the bean is under. If you guess
correctly, you get double the money back (net profit of $5), otherwise
the house keeps your money. Simple, effective way to take money from
unwise gamblers.

Setup Initial Values
--------------------

So, for this game, we'll need to map out some variables to hold
important values. Let's see, we need to keep track of :

  * The player's money.
  * Which cup the bean is under.

Let's add these lines to our game:

    which_cup = 1
    player_money = 20

So, we've put the bean under cup number 1, and the player has 20 bucks.
Let's worry about putting the bean under a different cup each time the
game is played later. Right now, let's just get the game working.  For
the sake of argument, let's say that the three cups will be represented
by the integer values 1, 2, and 3.

User Input
----------

Now we need to ask the user what cup they want to pick. Let's ask them:

    pick = input("Pick a cup (1, 2, or 3): ")

Input from the user always shows up as a string, not an integer, so we
need to convert their input to an integer:

    real_pick = int(pick)

OK, so now that the user has picked, he'll need to pay up:

    player_money = player_money - 5

Let's let the player know we took his money:

    print("Player, you paid $5 and you have $%d left" % player_money)

Now, let's check if they won, and award the money or console the loser.

    if real_pick == which_cup:
        print("You guess the right cup!")
        player_money = player_money + 10
        print("You won $10! You now have $%d" % player_money)
    else:
        print("So sorry, you guessed wrong, you have $%d" % player_money)

Since the program will just exit at this point, let's send the player a
farewell message:

    print("Thanks for playing!")

The program should now look like this:

    # my_game.py : a game by Billy Bob

    print("Hello, welcome to My Game!")

    which_cup = 1
    player_money = 20

    pick = input("Pick a cup (1, 2, 3): ")
    real_pick = int(pick)

    player_money = player_money - 5
    print("Player, you paid $5 and you have $%d left" % player_money)

    if real_pick == which_cup:
        print("You guess the right cup!")
        player_money = player_money + 10
        print("You won $10! You now have $%d" % player_money)
    else:
        print("So sorry, you guessed wrong, you have $%d" % player_money)

    print("Thanks for playing!")

Again, the empty lines are just ones that I put there to group the
related lines of code and make the while thing a bit easier to read.
Yours may now look exactly like mine in this respect. OK, run the
program by selecting *Run Module* from the *Run* menu or just by hitting
*F5*. Now go to the Shell window if it didn't take you there
automatically. You should see this at the bottom:

    >>> 
    Hello, welcome to My Game!
    Pick a cup (1, 2, 3): 

If you see an error, you may have entered something incorrectly, so
you'll need to go back and take a closer look at your program. Usually
errors have a line number involved, that should help you find what line
your error is one. Remember, Python is very sensitive to indentation, so
if there are extra spaces at the beginning of a line that shouldn't be
indented, that could cause an error.

Assuming that you did see the above lines, enter the number *1* and hit
enter:

    Hello, welcome to My Game!
    Pick a cup (1, 2, 3): 1
    Player, you paid $5 and you have $15 left
    You guess the right cup!
    You won $10! You now have $25
    Thanks for playing!
    >>> 

So far, so good, but you *knew* the bean was under cup number 1, so
that's not really fair. Let's test the losing case, too. Run the game
again (*Run Module* or *F5* in the editor window). This time, guess
number 2:

    Hello, welcome to My Game!
    Pick a cup (1, 2, 3): 2
    Player, you paid $5 and you have $15 left
    So sorry, you guessed wrong, you have $15
    Thanks for playing!
    >>> 

OK, it looks good. Let's make it better though. Let's identify some
issues:

  * Anyone who plays the game more than a couple times will soon
    discover that the bean is always under the first cup.
  * You can only play the game once, so you start over with $20 each
    time you play. It would be nice to rack up a larger sum or run out
    of money.
  * We aren't checking the user input which might not be a valid guess
    or even a number at all which might cause the program to crash on
    the line *real_pick = int(pick)*.

Using a Standard Module
-----------------------

Let's tackle the fact that the bean is always under cup 1. We really
need to pick a random value for the cup, either 1, 2, or 3. Fortunately,
there is a standard module in Python that generates random numbers for
us. It's called *random* of all things. The documentation for the module
is found here: [http://docs.python.org/py3k/library/random.html](http://docs.python.org/py3k/library/random.html)

We need to import the module to use it, so lets add a new line of code
near the top of the program, just after the first comment:

    import random

The way to get a random number is to make a call to the *randint*
function of the *random* module. That function takes two parameters,
which define the lower and upper bound for the random number to return.
So, we need a number from 1 to 3. The line which initializes the
*which_cup* variable to 1, should be changed to the following:

    which_cup = random.randint(1,3)

Just in case you had a hard time with those edits, here is the complete
program again, with the changes made:

    # my_game.py : a game by Billy Bob
    import random

    print("Hello, welcome to My Game!")

    which_cup = random.randint(1,3)
    player_money = 20

    pick = input("Pick a cup (1, 2, 3): ")
    real_pick = int(pick)

    player_money = player_money - 5
    print("Player, you paid $5 and you have $%d left" % player_money)

    if real_pick == which_cup:
        print("You guess the right cup!")
        player_money = player_money + 10
        print("You won $10! You now have $%d" % player_money)
    else:
        print("So sorry, you guessed wrong, you have $%d" % player_money)

    print("Thanks for playing!")

You should really test this out, play the game a few times, you'll
notice that sometimes you win guessing 2 or 3 and you may lose guessing
So, we've fixed the predictability of the first version of *my_game.py*.

Put it in a loop
----------------

To address the fact that the game only lets you play it once, let's put
it in a loop. This is much easier than it sounds. First we need to
identify which parts of the game should only be executed once, and which
parts need to be in the loop. The lines we should only run once, are the
*import* statement at the top, and the line that initializes the
player's money. Since we will want to generate a new value for
*which_cup*, that should be in the loop. Let's reorganize our code a bit
to separate the part that should be in a loop from the rest.

Before we make an actual loop, let's move the initialization of the
*player_money* variable up to the top and mark the loop with some
comments. This will not change the way the program runs, yet:

    # my_game.py : a game by Billy Bob
    import random

    print("Hello, welcome to My Game!")

    player_money = 20

    # loop starts here
    which_cup = random.randint(1,3)

    pick = input("Pick a cup (1, 2, 3): ")
    real_pick = int(pick)

    player_money = player_money - 5
    print("Player, you paid $5 and you have $%d left" % player_money)

    if real_pick == which_cup:
        print("You guess the right cup!")
        player_money = player_money + 10
        print("You won $10! You now have $%d" % player_money)
    else:
        print("So sorry, you guessed wrong, you have $%d" % player_money)
    # loop ends here

    print("Thanks for playing!")

OK, so let's make that an actual loop, by creating a simple *while True*
loop:

    # my_game.py : a game by Billy Bob
    import random

    print("Hello, welcome to My Game!")

    player_money = 20

    while True:
        which_cup = random.randint(1,3)

        pick = input("Pick a cup (1, 2, 3): ")
        real_pick = int(pick)

        player_money = player_money - 5
        print("Player, you paid $5 and you have $%d left" % player_money)

        if real_pick == which_cup:
            print("You guess the right cup!")
            player_money = player_money + 10
            print("You won $10! You now have $%d" % player_money)
        else:
            print("So sorry, you guessed wrong, you have $%d" % player_money)

    print("Thanks for playing!")

Now to get this right, you'll need to be meticulous about how you indent
the loop portion. The easiest way to do this with the IDLE editor is to
highlight the lines you want to indent and hit the TAB key on the
keyboard. That indents each line exactly 4 spaces.

The line that prints "Thanks for playing!" is not indented, which
signifies that it is not part of the body of the *while* loop. That
means, when the loop exits (which currently it can't do) it will print
that message once and then the program will exit.

Before we run this program, there are a few problems. One problem is
that the loop will never end, and the user will be forced to play this
game over and over. That's not a good situation. Let's give them an
option to quit.

We could change the input line to this:

    pick = input("Pick a cup (1, 2, 3) or q to quit: ")

And then add these lines after it:

    if pick == "q":
        break

The *break* statement will break the program out of the *while* loop. So
the user can now quit by entering "q".

Here is the complete program after these last edits:

    # my_game.py : a game by Billy Bob
    import random

    print("Hello, welcome to My Game!")

    player_money = 20

    while True:
        which_cup = random.randint(1,3)

        pick = input("Pick a cup (1, 2, 3) or q to quit: ")
        if pick == "q":
            break
        real_pick = int(pick)

        player_money = player_money - 5
        print("Player, you paid $5 and you have $%d left" % player_money)

        if real_pick == which_cup:
            print("You guess the right cup!")
            player_money = player_money + 10
            print("You won $10! You now have $%d" % player_money)
        else:
            print("So sorry, you guessed wrong, you have $%d" % player_money)

    print("Thanks for playing!")

Now, let's play a bit:

    Hello, welcome to My Game!
    Pick a cup (1, 2, 3) or q to quit: 1
    Player, you paid $5 and you have $15 left
    So sorry, you guessed wrong, you have $15
    Pick a cup (1, 2, 3) or q to quit: 2
    Player, you paid $5 and you have $10 left
    So sorry, you guessed wrong, you have $10
    Pick a cup (1, 2, 3) or q to quit: 1
    Player, you paid $5 and you have $5 left
    So sorry, you guessed wrong, you have $5
    Pick a cup (1, 2, 3) or q to quit: 3
    Player, you paid $5 and you have $0 left
    So sorry, you guessed wrong, you have $0
    Pick a cup (1, 2, 3) or q to quit: 1
    Player, you paid $5 and you have $-5 left
    You guess the right cup!
    You won $10! You now have $5
    Pick a cup (1, 2, 3) or q to quit: q
    Thanks for playing!
    >>> 

So, there's a complete game, sort of. We haven't dealt with the
situation where the user gives bad input, but I'll leave that as an
exercise for the reader.

On Errors and Debugging
-----------------------

It is quite easy to make an error while entering this code. Usually, if
there is an error, Python will dump an error message with line numbers.
Always check the line number first. In the IDLE editor, you can press
*Alt-G* to go to a particular line number. 99% of the time, the error
will be on the line number specified in the error message. If the error
isn't obvious (mis-named variable, wrong indentation, missing operator,
etc) then you may need to read the error message itself and try to
puzzle out what went wrong. It can be frustrating, but it is an
important skill in programming.

Another way of figuring out what is going wrong is by adding *print*
statements. You can print out the value of any variable at any time in
the program by adding a print statement. If you are uncertain about the
behavior of the *random* module, you can add a line after the one that
sets the *which_cup* variable:

    print("The randomly selected cup is %d" % which_cup)

Now, you'll want to make sure the indentation of that lines matches the
one before it. This way you can see that the program is working
correctly:

    Hello, welcome to My Game!
    The randomly selected cup is 1
    Pick a cup (1, 2, 3) or q to quit: 1
    Player, you paid $5 and you have $15 left
    You guess the right cup!
    You won $10! You now have $25
    The randomly selected cup is 3
    Pick a cup (1, 2, 3) or q to quit: 3
    Player, you paid $5 and you have $20 left
    You guess the right cup!
    You won $10! You now have $30
    The randomly selected cup is 1
    Pick a cup (1, 2, 3) or q to quit: 2
    Player, you paid $5 and you have $25 left
    So sorry, you guessed wrong, you have $25
    The randomly selected cup is 2
    Pick a cup (1, 2, 3) or q to quit: 3
    Player, you paid $5 and you have $20 left
    So sorry, you guessed wrong, you have $20
    The randomly selected cup is 3
    Pick a cup (1, 2, 3) or q to quit: q
    Thanks for playing!
    >>> 

You obviously don't want to leave this line in the program, but for
testing purposes, you can see that the program is working correctly.

This technique is called *print debugging* or *printf debugging* since
the print statement in the C programming language was called *printf*.

