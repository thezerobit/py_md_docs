The *while* Loop
----------------

A *while* block is very similar to an *if* block, with the one
difference is that when the block ends, the flow of execution jumps back
to the beginning, checks the condition again, and executes the block
again. This process continues until the condition becomes false or the
*break* statement is reached. Consider the following code:

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

It is a simple loop, in each iteration, the value of *x* is printed to
the screen and then incremented. Since the value of x is set to 5
*after* being printed out, we never get to see the number 5. Notice the
output of this code is slightly different:

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

In that loop, *x* never changes, so the condition will always be *True*.
However, it is commonly used idiom to set up a simple loop with *while
True:* and just have the loop exit on *break*:

    x = 0
    while True:
        x = x + 1
        if x > 5:
            break
        print(x)


The *for* loop
--------------

Python has a very easy syntax for looping through the elements of a
sequence or any object that appears to be a sequence. The most obvious
would be a list.

    some_list = ["this", "that", "other"]

    for word in some_list:
        length = len(word)
        print("The word '%s' has a length of %d." % (word, length))

The block executes once for each element in the list and the variable
specified right after the for statement (*word* in this case) holds a
reference to the element for the loop. So the above code would print out
the following:

    The word 'this' has a length of 4.
    The word 'that' has a length of 4.
    The word 'other' has a length of 5.

This also works with tuples

    my_tuple = (1,2,3)

    for num in my_tuple:
        ten_times = num * 10
        print("%d is ten times %d" % (ten_times, num))
