# Appendices

## Appendix A: Debugging

Appendix A

Debugging

When you are debugging, you should distinguish among different kinds of errors in order
to track them down more quickly:

   • Syntax errors are discovered by the interpreter when it is translating the source code
     into byte code. They indicate that there is something wrong with the structure of the
     program. Example: Omitting the colon at the end of a def statement generates the
     somewhat redundant message SyntaxError: invalid syntax.

   • Runtime errors are produced by the interpreter if something goes wrong while the
     program is running. Most runtime error messages include information about where
     the error occurred and what functions were executing. Example: An infinite recur-
     sion eventually causes the runtime error “maximum recursion depth exceeded”.

   • Semantic errors are problems with a program that runs without producing error mes-
     sages but doesn’t do the right thing. Example: An expression may not be evaluated
     in the order you expect, yielding an incorrect result.

The first step in debugging is to figure out which kind of error you are dealing with. Al-
though the following sections are organized by error type, some techniques are applicable
in more than one situation.

A.1     Syntax errors
Syntax errors are usually easy to fix once you figure out what they are. Unfortunately,
the error messages are often not helpful. The most common messages are SyntaxError:
invalid syntax and SyntaxError: invalid token, neither of which is very informa-
tive.

On the other hand, the message does tell you where in the program the problem occurred.
Actually, it tells you where Python noticed a problem, which is not necessarily where the
error is. Sometimes the error is prior to the location of the error message, often on the
preceding line.
194                                                                Appendix A. Debugging

If you are building the program incrementally, you should have a good idea about where
the error is. It will be in the last line you added.
If you are copying code from a book, start by comparing your code to the book’s code
very carefully. Check every character. At the same time, remember that the book might be
wrong, so if you see something that looks like a syntax error, it might be.
Here are some ways to avoid the most common syntax errors:

  1. Make sure you are not using a Python keyword for a variable name.
  2. Check that you have a colon at the end of the header of every compound statement,
     including for, while, if, and def statements.
  3. Make sure that any strings in the code have matching quotation marks. Make sure
     that all quotation marks are “straight quotes”, not “curly quotes”.
  4. If you have multiline strings with triple quotes (single or double), make sure you
     have terminated the string properly. An unterminated string may cause an invalid
     token error at the end of your program, or it may treat the following part of the
     program as a string until it comes to the next string. In the second case, it might not
     produce an error message at all!
  5. An unclosed opening operator—(, {, or [—makes Python continue with the next line
     as part of the current statement. Generally, an error occurs almost immediately in the
     next line.
  6. Check for the classic = instead of == inside a conditional.
  7. Check the indentation to make sure it lines up the way it is supposed to. Python
     can handle space and tabs, but if you mix them it can cause problems. The best way
     to avoid this problem is to use a text editor that knows about Python and generates
     consistent indentation.
  8. If you have non-ASCII characters in the code (including strings and comments), that
     might cause a problem, although Python 3 usually handles non-ASCII characters. Be
     careful if you paste in text from a web page or other source.

If nothing works, move on to the next section...

A.1.1    I keep making changes and it makes no difference.
If the interpreter says there is an error and you don’t see it, that might be because you and
the interpreter are not looking at the same code. Check your programming environment to
make sure that the program you are editing is the one Python is trying to run.
If you are not sure, try putting an obvious and deliberate syntax error at the beginning of
the program. Now run it again. If the interpreter doesn’t find the new error, you are not
running the new code.
There are a few likely culprits:

   • You edited the file and forgot to save the changes before running it again. Some
     programming environments do this for you, but some don’t.
A.2. Runtime errors                                                                       195

   • You changed the name of the file, but you are still running the old name.
   • Something in your development environment is configured incorrectly.
   • If you are writing a module and using import, make sure you don’t give your module
     the same name as one of the standard Python modules.
   • If you are using import to read a module, remember that you have to restart the
     interpreter or use reload to read a modified file. If you import the module again, it
     doesn’t do anything.
If you get stuck and you can’t figure out what is going on, one approach is to start again
with a new program like “Hello, World!”, and make sure you can get a known program to
run. Then gradually add the pieces of the original program to the new one.

A.2     Runtime errors
Once your program is syntactically correct, Python can read it and at least start running it.
What could possibly go wrong?

A.2.1    My program does absolutely nothing.
This problem is most common when your file consists of functions and classes but does
not actually invoke a function to start execution. This may be intentional if you only plan
to import this module to supply classes and functions.
If it is not intentional, make sure there is a function call in the program, and make sure the
flow of execution reaches it (see “Flow of Execution” below).

A.2.2    My program hangs.
If a program stops and seems to be doing nothing, it is “hanging”. Often that means that it
is caught in an infinite loop or infinite recursion.
   • If there is a particular loop that you suspect is the problem, add a print statement
     immediately before the loop that says “entering the loop” and another immediately
     after that says “exiting the loop”.
      Run the program. If you get the first message and not the second, you’ve got an
      infinite loop. Go to the “Infinite Loop” section below.
   • Most of the time, an infinite recursion will cause the program to run for a while and
     then produce a “RuntimeError: Maximum recursion depth exceeded” error. If that
     happens, go to the “Infinite Recursion” section below.
      If you are not getting this error but you suspect there is a problem with a recursive
      method or function, you can still use the techniques in the “Infinite Recursion” sec-
      tion.
   • If neither of those steps works, start testing other loops and other recursive functions
     and methods.
   • If that doesn’t work, then it is possible that you don’t understand the flow of execu-
     tion in your program. Go to the “Flow of Execution” section below.
196                                                                 Appendix A. Debugging

Infinite Loop

If you think you have an infinite loop and you think you know what loop is causing the
problem, add a print statement at the end of the loop that prints the values of the variables
in the condition and the value of the condition.

For example:
while x > 0 and y < 0 :
    # do something to x
    # do something to y

      print('x: ', x)
      print('y: ', y)
      print("condition: ", (x > 0 and y < 0))
Now when you run the program, you will see three lines of output for each time through
the loop. The last time through the loop, the condition should be False. If the loop keeps
going, you will be able to see the values of x and y, and you might figure out why they are
not being updated correctly.

Infinite Recursion

Most of the time, infinite recursion causes the program to run for a while and then produce
a Maximum recursion depth exceeded error.

If you suspect that a function is causing an infinite recursion, make sure that there is a base
case. There should be some condition that causes the function to return without making a
recursive invocation. If not, you need to rethink the algorithm and identify a base case.

If there is a base case but the program doesn’t seem to be reaching it, add a print state-
ment at the beginning of the function that prints the parameters. Now when you run the
program, you will see a few lines of output every time the function is invoked, and you
will see the parameter values. If the parameters are not moving toward the base case, you
will get some ideas about why not.

Flow of Execution

If you are not sure how the flow of execution is moving through your program, add print
statements to the beginning of each function with a message like “entering function foo”,
where foo is the name of the function.

Now when you run the program, it will print a trace of each function as it is invoked.

A.2.3    When I run the program I get an exception.
If something goes wrong during runtime, Python prints a message that includes the name
of the exception, the line of the program where the problem occurred, and a traceback.

The traceback identifies the function that is currently running, and then the function that
called it, and then the function that called that, and so on. In other words, it traces the
A.2. Runtime errors                                                                         197

sequence of function calls that got you to where you are, including the line number in your
file where each call occurred.

The first step is to examine the place in the program where the error occurred and see if
you can figure out what happened. These are some of the most common runtime errors:

NameError: You are trying to use a variable that doesn’t exist in the current environment.
    Check if the name is spelled right, or at least consistently. And remember that local
    variables are local; you cannot refer to them from outside the function where they are
    defined.

TypeError: There are several possible causes:
        • You are trying to use a value improperly. Example: indexing a string, list, or
          tuple with something other than an integer.
        • There is a mismatch between the items in a format string and the items passed
          for conversion. This can happen if either the number of items does not match or
          an invalid conversion is called for.
        • You are passing the wrong number of arguments to a function. For methods,
          look at the method definition and check that the first parameter is self. Then
          look at the method invocation; make sure you are invoking the method on an
          object with the right type and providing the other arguments correctly.

KeyError: You are trying to access an element of a dictionary using a key that the dictio-
    nary does not contain. If the keys are strings, remember that capitalization matters.

AttributeError: You are trying to access an attribute or method that does not exist. Check
      the spelling! You can use the built-in function vars to list the attributes that do exist.
      If an AttributeError indicates that an object has NoneType, that means that it is None.
      So the problem is not the attribute name, but the object.
      The reason the object is none might be that you forgot to return a value from a func-
      tion; if you get to the end of a function without hitting a return statement, it returns
      None. Another common cause is using the result from a list method, like sort, that
      returns None.

IndexError: The index you are using to access a list, string, or tuple is greater than its
     length minus one. Immediately before the site of the error, add a print statement to
     display the value of the index and the length of the array. Is the array the right size?
     Is the index the right value?

The Python debugger (pdb) is useful for tracking down exceptions because it allows you to
examine the state of the program immediately before the error. You can read about pdb at
https://docs.python.org/3/library/pdb.html.

A.2.4    I added so many print statements I get inundated with output.
One of the problems with using print statements for debugging is that you can end up
buried in output. There are two ways to proceed: simplify the output or simplify the
program.
198                                                              Appendix A. Debugging

To simplify the output, you can remove or comment out print statements that aren’t help-
ing, or combine them, or format the output so it is easier to understand.

To simplify the program, there are several things you can do. First, scale down the problem
the program is working on. For example, if you are searching a list, search a small list. If
the program takes input from the user, give it the simplest input that causes the problem.

Second, clean up the program. Remove dead code and reorganize the program to make
it as easy to read as possible. For example, if you suspect that the problem is in a deeply
nested part of the program, try rewriting that part with simpler structure. If you suspect a
large function, try splitting it into smaller functions and testing them separately.

Often the process of finding the minimal test case leads you to the bug. If you find that
a program works in one situation but not in another, that gives you a clue about what is
going on.

Similarly, rewriting a piece of code can help you find subtle bugs. If you make a change
that you think shouldn’t affect the program, and it does, that can tip you off.

A.3     Semantic errors
In some ways, semantic errors are the hardest to debug, because the interpreter provides
no information about what is wrong. Only you know what the program is supposed to do.

The first step is to make a connection between the program text and the behavior you are
seeing. You need a hypothesis about what the program is actually doing. One of the things
that makes that hard is that computers run so fast.

You will often wish that you could slow the program down to human speed, and with
some debuggers you can. But the time it takes to insert a few well-placed print statements
is often short compared to setting up the debugger, inserting and removing breakpoints,
and “stepping” the program to where the error is occurring.

A.3.1    My program doesn’t work.
You should ask yourself these questions:

   • Is there something the program was supposed to do but which doesn’t seem to be
     happening? Find the section of the code that performs that function and make sure
     it is executing when you think it should.

   • Is something happening that shouldn’t? Find code in your program that performs
     that function and see if it is executing when it shouldn’t.

   • Is a section of code producing an effect that is not what you expected? Make sure that
     you understand the code in question, especially if it involves functions or methods in
     other Python modules. Read the documentation for the functions you call. Try them
     out by writing simple test cases and checking the results.
A.3. Semantic errors                                                                    199

In order to program, you need a mental model of how programs work. If you write a
program that doesn’t do what you expect, often the problem is not in the program; it’s in
your mental model.
The best way to correct your mental model is to break the program into its components
(usually the functions and methods) and test each component independently. Once you
find the discrepancy between your model and reality, you can solve the problem.
Of course, you should be building and testing components as you develop the program.
If you encounter a problem, there should be only a small amount of new code that is not
known to be correct.

A.3.2    I’ve got a big hairy expression and it doesn’t do what I expect.
Writing complex expressions is fine as long as they are readable, but they can be hard to
debug. It is often a good idea to break a complex expression into a series of assignments to
temporary variables.
For example:
self.hands[i].addCard(self.hands[self.findNeighbor(i)].popCard())
This can be rewritten as:
neighbor = self.findNeighbor(i)
pickedCard = self.hands[neighbor].popCard()
self.hands[i].addCard(pickedCard)
The explicit version is easier to read because the variable names provide additional docu-
mentation, and it is easier to debug because you can check the types of the intermediate
variables and display their values.
Another problem that can occur with big expressions is that the order of evaluation may
                                                                            x
not be what you expect. For example, if you are translating the expression 2π into Python,
you might write:
y = x / 2 * math.pi
That is not correct because multiplication and division have the same precedence and are
evaluated from left to right. So this expression computes xπ/2.
A good way to debug expressions is to add parentheses to make the order of evaluation
explicit:
 y = x / (2 * math.pi)
Whenever you are not sure of the order of evaluation, use parentheses. Not only will the
program be correct (in the sense of doing what you intended), it will also be more readable
for other people who haven’t memorized the order of operations.

A.3.3    I’ve got a function that doesn’t return what I expect.
If you have a return statement with a complex expression, you don’t have a chance to
print the result before returning. Again, you can use a temporary variable. For example,
instead of:
return self.hands[i].removeMatches()
200                                                              Appendix A. Debugging

you could write:
count = self.hands[i].removeMatches()
return count
Now you have the opportunity to display the value of count before returning.

A.3.4    I’m really, really stuck and I need help.
First, try getting away from the computer for a few minutes. Computers emit waves that
affect the brain, causing these symptoms:

   • Frustration and rage.
   • Superstitious beliefs (“the computer hates me”) and magical thinking (“the program
     only works when I wear my hat backward”).
   • Random walk programming (the attempt to program by writing every possible pro-
     gram and choosing the one that does the right thing).

If you find yourself suffering from any of these symptoms, get up and go for a walk. When
you are calm, think about the program. What is it doing? What are some possible causes
of that behavior? When was the last time you had a working program, and what did you
do next?
Sometimes it just takes time to find a bug. I often find bugs when I am away from the
computer and let my mind wander. Some of the best places to find bugs are trains, showers,
and in bed, just before you fall asleep.

A.3.5    No, I really need help.
It happens. Even the best programmers occasionally get stuck. Sometimes you work on a
program so long that you can’t see the error. You need a fresh pair of eyes.
Before you bring someone else in, make sure you are prepared. Your program should be as
simple as possible, and you should be working on the smallest input that causes the error.
You should have print statements in the appropriate places (and the output they produce
should be comprehensible). You should understand the problem well enough to describe
it concisely.
When you bring someone in to help, be sure to give them the information they need:

   • If there is an error message, what is it and what part of the program does it indicate?
   • What was the last thing you did before this error occurred? What were the last lines
     of code that you wrote, or what is the new test case that fails?
   • What have you tried so far, and what have you learned?

When you find the bug, take a second to think about what you could have done to find it
faster. Next time you see something similar, you will be able to find the bug more quickly.
Remember, the goal is not just to make the program work. The goal is to learn how to make
the program work.

## Appendix B: Analysis of Algorithms

Appendix B

Analysis of Algorithms

       This appendix is an edited excerpt from Think Complexity, by Allen B. Downey,
       also published by O’Reilly Media (2012). When you are done with this book,
       you might want to move on to that one.

Analysis of algorithms is a branch of computer science that studies the performance of
algorithms, especially their run time and space requirements. See http://en.wikipedia.
org/wiki/Analysis_of_algorithms.

The practical goal of algorithm analysis is to predict the performance of different algo-
rithms in order to guide design decisions.

During the 2008 United States Presidential Campaign, candidate Barack Obama was asked
to perform an impromptu analysis when he visited Google. Chief executive Eric Schmidt
jokingly asked him for “the most efficient way to sort a million 32-bit integers.” Obama
had apparently been tipped off, because he quickly replied, “I think the bubble sort would
be the wrong way to go.” See http://www.youtube.com/watch?v=k4RRi_ntQc8.

This is true: bubble sort is conceptually simple but slow for large datasets. The an-
swer Schmidt was probably looking for is “radix sort” (http://en.wikipedia.org/wiki/
Radix_sort)1 .

The goal of algorithm analysis is to make meaningful comparisons between algorithms,
but there are some problems:

    • The relative performance of the algorithms might depend on characteristics of the
      hardware, so one algorithm might be faster on Machine A, another on Machine B.
      The general solution to this problem is to specify a machine model and analyze the
      number of steps, or operations, an algorithm requires under a given model.

    • Relative performance might depend on the details of the dataset. For example, some
      sorting algorithms run faster if the data are already partially sorted; other algorithms
    1 But if you get a question like this in an interview, I think a better answer is, “The fastest way to sort a million

integers is to use whatever sort function is provided by the language I’m using. Its performance is good enough
for the vast majority of applications, but if it turned out that my application was too slow, I would use a profiler
to see where the time was being spent. If it looked like a faster sort algorithm would have a significant effect on
performance, then I would look around for a good implementation of radix sort.”
202                                                   Appendix B. Analysis of Algorithms

      run slower in this case. A common way to avoid this problem is to analyze the worst
      case scenario. It is sometimes useful to analyze average case performance, but that’s
      usually harder, and it might not be obvious what set of cases to average over.

   • Relative performance also depends on the size of the problem. A sorting algorithm
     that is fast for small lists might be slow for long lists. The usual solution to this
     problem is to express run time (or number of operations) as a function of problem
     size, and group functions into categories depending on how quickly they grow as
     problem size increases.

The good thing about this kind of comparison is that it lends itself to simple classification
of algorithms. For example, if I know that the run time of Algorithm A tends to be pro-
portional to the size of the input, n, and Algorithm B tends to be proportional to n2 , then I
expect A to be faster than B, at least for large values of n.

This kind of analysis comes with some caveats, but we’ll get to that later.

B.1        Order of growth
Suppose you have analyzed two algorithms and expressed their run times in terms of the
size of the input: Algorithm A takes 100n + 1 steps to solve a problem with size n; Algo-
rithm B takes n2 + n + 1 steps.

The following table shows the run time of these algorithms for different problem sizes:

  Input      Run time of   Run time of
    size    Algorithm A    Algorithm B
      10           1 001            111
     100          10 001         10 101
   1 000         100 001      1 001 001
 10 000        1 000 001    100 010 001

At n = 10, Algorithm A looks pretty bad; it takes almost 10 times longer than Algorithm
B. But for n = 100 they are about the same, and for larger values A is much better.

The fundamental reason is that for large values of n, any function that contains an n2 term
will grow faster than a function whose leading term is n. The leading term is the term with
the highest exponent.

For Algorithm A, the leading term has a large coefficient, 100, which is why B does better
than A for small n. But regardless of the coefficients, there will always be some value of n
where an2 > bn, for any values of a and b.

The same argument applies to the non-leading terms. Even if the run time of Algorithm A
were n + 1000000, it would still be better than Algorithm B for sufficiently large n.

In general, we expect an algorithm with a smaller leading term to be a better algorithm for
large problems, but for smaller problems, there may be a crossover point where another
algorithm is better. The location of the crossover point depends on the details of the algo-
rithms, the inputs, and the hardware, so it is usually ignored for purposes of algorithmic
analysis. But that doesn’t mean you can forget about it.
B.1. Order of growth                                                                          203

If two algorithms have the same leading order term, it is hard to say which is better; again,
the answer depends on the details. So for algorithmic analysis, functions with the same
leading term are considered equivalent, even if they have different coefficients.
An order of growth is a set of functions whose growth behavior is considered equivalent.
For example, 2n, 100n and n + 1 belong to the same order of growth, which is written O(n)
in Big-Oh notation and often called linear because every function in the set grows linearly
with n.
All functions with the leading term n2 belong to O(n2 ); they are called quadratic.
The following table shows some of the orders of growth that appear most commonly in
algorithmic analysis, in increasing order of badness.
   Order of                         Name
    growth
       O (1)                   constant
  O(logb n)      logarithmic (for any b)
       O(n)                       linear
 O(n logb n)               linearithmic
      O ( n2 )                quadratic
      O ( n3 )                     cubic
      O(cn )     exponential (for any c)
For the logarithmic terms, the base of the logarithm doesn’t matter; changing bases is the
equivalent of multiplying by a constant, which doesn’t change the order of growth. Sim-
ilarly, all exponential functions belong to the same order of growth regardless of the base
of the exponent. Exponential functions grow very quickly, so exponential algorithms are
only useful for small problems.
Exercise B.1. Read the Wikipedia page on Big-Oh notation at http: // en. wikipedia. org/
wiki/ Big_ O_ notation and answer the following questions:
  1. What is the order of growth of n3 + n2 ? What about 1000000n3 + n2 ? What about n3 +
     1000000n2 ?
  2. What is the order of growth of (n2 + n) · (n + 1)? Before you start multiplying, remember
     that you only need the leading term.
  3. If f is in O( g), for some unspecified function g, what can we say about a f + b, where a and
     b are constants?
  4. If f 1 and f 2 are in O( g), what can we say about f 1 + f 2 ?
  5. If f 1 is in O( g) and f 2 is in O(h), what can we say about f 1 + f 2 ?
  6. If f 1 is in O( g) and f 2 is O(h), what can we say about f 1 · f 2 ?
Programmers who care about performance often find this kind of analysis hard to swal-
low. They have a point: sometimes the coefficients and the non-leading terms make a real
difference. Sometimes the details of the hardware, the programming language, and the
characteristics of the input make a big difference. And for small problems, order of growth
is irrelevant.
But if you keep those caveats in mind, algorithmic analysis is a useful tool. At least for
large problems, the “better” algorithm is usually better, and sometimes it is much better.
The difference between two algorithms with the same order of growth is usually a constant
factor, but the difference between a good algorithm and a bad algorithm is unbounded!
204                                                    Appendix B. Analysis of Algorithms

B.2     Analysis of basic Python operations
In Python, most arithmetic operations are constant time; multiplication usually takes
longer than addition and subtraction, and division takes even longer, but these run times
don’t depend on the magnitude of the operands. Very large integers are an exception; in
that case the run time increases with the number of digits.
Indexing operations—reading or writing elements in a sequence or dictionary—are also
constant time, regardless of the size of the data structure.
A for loop that traverses a sequence or dictionary is usually linear, as long as all of the
operations in the body of the loop are constant time. For example, adding up the elements
of a list is linear:
      total = 0
      for x in t:
          total += x
The built-in function sum is also linear because it does the same thing, but it tends to be
faster because it is a more efficient implementation; in the language of algorithmic analysis,
it has a smaller leading coefficient.
As a rule of thumb, if the body of a loop is in O(n a ) then the whole loop is in O(n a+1 ). The
exception is if you can show that the loop exits after a constant number of iterations. If a
loop runs k times regardless of n, then the loop is in O(n a ), even for large k.
Multiplying by k doesn’t change the order of growth, but neither does dividing. So if the
body of a loop is in O(n a ) and it runs n/k times, the loop is in O(n a+1 ), even for large k.
Most string and tuple operations are linear, except indexing and len, which are constant
time. The built-in functions min and max are linear. The run-time of a slice operation is
proportional to the length of the output, but independent of the size of the input.
String concatenation is linear; the run time depends on the sum of the lengths of the
operands.
All string methods are linear, but if the lengths of the strings are bounded by a constant—
for example, operations on single characters—they are considered constant time. The
string method join is linear; the run time depends on the total length of the strings.
Most list methods are linear, but there are some exceptions:

   • Adding an element to the end of a list is constant time on average; when it runs
     out of room it occasionally gets copied to a bigger location, but the total time for n
     operations is O(n), so the average time for each operation is O(1).
   • Removing an element from the end of a list is constant time.
   • Sorting is O(n log n).

Most dictionary operations and methods are constant time, but there are some exceptions:

   • The run time of update is proportional to the size of the dictionary passed as a pa-
     rameter, not the dictionary being updated.
   • keys, values and items are constant time because they return iterators. But if you
     loop through the iterators, the loop will be linear.
B.3. Analysis of search algorithms                                                           205

The performance of dictionaries is one of the minor miracles of computer science. We will
see how they work in Section B.4.
Exercise B.2. Read the Wikipedia page on sorting algorithms at http: // en. wikipedia. org/
wiki/ Sorting_ algorithm and answer the following questions:

  1. What is a “comparison sort?” What is the best worst-case order of growth for a comparison
     sort? What is the best worst-case order of growth for any sort algorithm?

  2. What is the order of growth of bubble sort, and why does Barack Obama think it is “the wrong
     way to go?”

  3. What is the order of growth of radix sort? What preconditions do we need to use it?

  4. What is a stable sort and why might it matter in practice?

  5. What is the worst sorting algorithm (that has a name)?

  6. What sort algorithm does the C library use? What sort algorithm does Python use? Are these
     algorithms stable? You might have to Google around to find these answers.

  7. Many of the non-comparison sorts are linear, so why does Python use an O(n log n) compar-
     ison sort?

B.3     Analysis of search algorithms
A search is an algorithm that takes a collection and a target item and determines whether
the target is in the collection, often returning the index of the target.

The simplest search algorithm is a “linear search”, which traverses the items of the collec-
tion in order, stopping if it finds the target. In the worst case it has to traverse the entire
collection, so the run time is linear.

The in operator for sequences uses a linear search; so do string methods like find and
count.

If the elements of the sequence are in order, you can use a bisection search, which is
O(log n). Bisection search is similar to the algorithm you might use to look a word up
in a dictionary (a paper dictionary, not the data structure). Instead of starting at the be-
ginning and checking each item in order, you start with the item in the middle and check
whether the word you are looking for comes before or after. If it comes before, then you
search the first half of the sequence. Otherwise you search the second half. Either way, you
cut the number of remaining items in half.

If the sequence has 1,000,000 items, it will take about 20 steps to find the word or conclude
that it’s not there. So that’s about 50,000 times faster than a linear search.

Bisection search can be much faster than linear search, but it requires the sequence to be in
order, which might require extra work.

There is another data structure, called a hashtable that is even faster—it can do a search
in constant time—and it doesn’t require the items to be sorted. Python dictionaries are
implemented using hashtables, which is why most dictionary operations, including the in
operator, are constant time.
206                                                     Appendix B. Analysis of Algorithms

B.4     Hashtables
To explain how hashtables work and why their performance is so good, I start with a simple
implementation of a map and gradually improve it until it’s a hashtable.

I use Python to demonstrate these implementations, but in real life you wouldn’t write
code like this in Python; you would just use a dictionary! So for the rest of this chapter, you
have to imagine that dictionaries don’t exist and you want to implement a data structure
that maps from keys to values. The operations you have to implement are:

add(k, v): Add a new item that maps from key k to value v. With a Python dictionary, d,
     this operation is written d[k] = v.

get(k): Look up and return the value that corresponds to key k. With a Python dictionary,
     d, this operation is written d[k] or d.get(k).

For now, I assume that each key only appears once. The simplest implementation of this
interface uses a list of tuples, where each tuple is a key-value pair.
class LinearMap:

      def __init__(self):
          self.items = []

      def add(self, k, v):
          self.items.append((k, v))

      def get(self, k):
          for key, val in self.items:
              if key == k:
                  return val
          raise KeyError
add appends a key-value tuple to the list of items, which takes constant time.

get uses a for loop to search the list: if it finds the target key it returns the corresponding
value; otherwise it raises a KeyError. So get is linear.

An alternative is to keep the list sorted by key. Then get could use a bisection search, which
is O(log n). But inserting a new item in the middle of a list is linear, so this might not be the
best option. There are other data structures that can implement add and get in log time,
but that’s still not as good as constant time, so let’s move on.

One way to improve LinearMap is to break the list of key-value pairs into smaller lists.
Here’s an implementation called BetterMap, which is a list of 100 LinearMaps. As we’ll
see in a second, the order of growth for get is still linear, but BetterMap is a step on the
path toward hashtables:
class BetterMap:

      def __init__(self, n=100):
          self.maps = []
          for i in range(n):
              self.maps.append(LinearMap())
B.4. Hashtables                                                                          207

    def find_map(self, k):
        index = hash(k) % len(self.maps)
        return self.maps[index]

    def add(self, k, v):
        m = self.find_map(k)
        m.add(k, v)

    def get(self, k):
        m = self.find_map(k)
        return m.get(k)
__init__ makes a list of n LinearMaps.

find_map is used by add and get to figure out which map to put the new item in, or which
map to search.

find_map uses the built-in function hash, which takes almost any Python object and returns
an integer. A limitation of this implementation is that it only works with hashable keys.
Mutable types like lists and dictionaries are unhashable.

Hashable objects that are considered equivalent return the same hash value, but the con-
verse is not necessarily true: two objects with different values can return the same hash
value.

find_map uses the modulus operator to wrap the hash values into the range from 0 to
len(self.maps), so the result is a legal index into the list. Of course, this means that many
different hash values will wrap onto the same index. But if the hash function spreads things
out pretty evenly (which is what hash functions are designed to do), then we expect n/100
items per LinearMap.

Since the run time of LinearMap.get is proportional to the number of items, we expect
BetterMap to be about 100 times faster than LinearMap. The order of growth is still linear,
but the leading coefficient is smaller. That’s nice, but still not as good as a hashtable.

Here (finally) is the crucial idea that makes hashtables fast: if you can keep the maximum
length of the LinearMaps bounded, LinearMap.get is constant time. All you have to do is
keep track of the number of items and when the number of items per LinearMap exceeds
a threshold, resize the hashtable by adding more LinearMaps.

Here is an implementation of a hashtable:
class HashMap:

    def __init__(self):
        self.maps = BetterMap(2)
        self.num = 0

    def get(self, k):
        return self.maps.get(k)

    def add(self, k, v):
        if self.num == len(self.maps.maps):
208                                                     Appendix B. Analysis of Algorithms

               self.resize()

          self.maps.add(k, v)
          self.num += 1

      def resize(self):
          new_maps = BetterMap(self.num * 2)

          for m in self.maps.maps:
              for k, v in m.items:
                  new_maps.add(k, v)

          self.maps = new_maps
__init__ creates a BetterMap and initializes num, which keeps track of the number of items.

get just dispatches to BetterMap. The real work happens in add, which checks the number
of items and the size of the BetterMap: if they are equal, the average number of items per
LinearMap is 1, so it calls resize.

resize makes a new BetterMap, twice as big as the previous one, and then “rehashes” the
items from the old map to the new.

Rehashing is necessary because changing the number of LinearMaps changes the denomi-
nator of the modulus operator in find_map. That means that some objects that used to hash
into the same LinearMap will get split up (which is what we wanted, right?).

Rehashing is linear, so resize is linear, which might seem bad, since I promised that add
would be constant time. But remember that we don’t have to resize every time, so add is
usually constant time and only occasionally linear. The total amount of work to run add n
times is proportional to n, so the average time of each add is constant time!

To see how this works, think about starting with an empty HashTable and adding a se-
quence of items. We start with 2 LinearMaps, so the first 2 adds are fast (no resizing re-
quired). Let’s say that they take one unit of work each. The next add requires a resize, so
we have to rehash the first two items (let’s call that 2 more units of work) and then add the
third item (one more unit). Adding the next item costs 1 unit, so the total so far is 6 units
of work for 4 items.

The next add costs 5 units, but the next three are only one unit each, so the total is 14 units
for the first 8 adds.

The next add costs 9 units, but then we can add 7 more before the next resize, so the total is
30 units for the first 16 adds.

After 32 adds, the total cost is 62 units, and I hope you are starting to see a pattern. After n
adds, where n is a power of two, the total cost is 2n − 2 units, so the average work per add
is a little less than 2 units. When n is a power of two, that’s the best case; for other values of
n the average work is a little higher, but that’s not important. The important thing is that it
is O(1).

Figure B.1 shows how this works graphically. Each block represents a unit of work. The
columns show the total work for each add in order from left to right: the first two adds cost
1 unit each, the third costs 3 units, etc.
B.5. Glossary                                                                          209

                         Figure B.1: The cost of a hashtable add.

The extra work of rehashing appears as a sequence of increasingly tall towers with increas-
ing space between them. Now if you knock over the towers, spreading the cost of resizing
over all adds, you can see graphically that the total cost after n adds is 2n − 2.
An important feature of this algorithm is that when we resize the HashTable it grows
geometrically; that is, we multiply the size by a constant. If you increase the size
arithmetically—adding a fixed number each time—the average time per add is linear.
You can download my implementation of HashMap from https://thinkpython.com/
code/Map.py, but remember that there is no reason to use it; if you want a map, just use a
Python dictionary.

B.5    Glossary
analysis of algorithms: A way to compare algorithms in terms of their run time and/or
     space requirements.
machine model: A simplified representation of a computer used to describe algorithms.
worst case: The input that makes a given algorithm run slowest (or require the most
     space).
leading term: In a polynomial, the term with the highest exponent.
crossover point: The problem size where two algorithms require the same run time or
     space.
order of growth: A set of functions that all grow in a way considered equivalent for pur-
     poses of analysis of algorithms. For example, all functions that grow linearly belong
     to the same order of growth.
Big-Oh notation: Notation for representing an order of growth; for example, O(n) repre-
     sents the set of functions that grow linearly.
linear: An algorithm whose run time is proportional to problem size, at least for large
      problem sizes.
quadratic: An algorithm whose run time is proportional to n2 , where n is a measure of
    problem size.
search: The problem of locating an element of a collection (like a list or dictionary) or
     determining that it is not present.
210                                                Appendix B. Analysis of Algorithms

hashtable: A data structure that represents a collection of key-value pairs and performs
     search in constant time.
Index

abecedarian, 73, 84                         augmented, 93, 100
abs function, 52                            item, 74, 90, 116
absolute path, 139, 145                     tuple, 116, 117, 119, 122
access, 90                             assignment statement, 9
accumulator, 100                       attribute, 153, 169
      histogram, 127                        __dict__, 168
      list, 93                              class, 172, 180
      string, 175                           initializing, 168
      sum, 93                               instance, 148, 153, 172, 180
Ackermann function, 61, 113            AttributeError, 152, 197
add method, 165                        augmented assignment, 93, 100
addition with carrying, 68             Austen, Jane, 127
algorithm, 67, 69, 130, 201            average case, 202
      MD5, 146                         average cost, 208
      square root, 69
aliasing, 95, 96, 100, 149, 151, 170   badness, 203
      copying to avoid, 99             base case, 44, 47
all, 186                               benchmarking, 133, 134
alphabet, 37                           BetterMap, 206
alternative execution, 41              big, hairy expression, 199
ambiguity, 5                           Big-Oh notation, 209
anagram, 101                           big-oh notation, 203
anagram set, 123, 145                  binary search, 101
analysis of algorithms, 201, 209       bingo, 123
analysis of primitives, 204            birthday, 160
and operator, 40                       birthday paradox, 101
any, 185                               bisect module, 101
append method, 92, 97, 101, 174, 175   bisection search, 101, 205
arc function, 31                       bisection, debugging by, 68
Archimedian spiral, 38                 bitwise operator, 3
argument, 17, 19, 21, 22, 26, 97       body, 19, 26, 65
      gather, 118                      bool type, 40
      keyword, 33, 36, 191             boolean expression, 40, 47
      list, 97                         boolean function, 54
      optional, 76, 79, 95, 107, 184   boolean operator, 76
      positional, 164, 169, 190        borrowing, subtraction with, 68, 159
      variable-length tuple, 118       bounded, 207
argument scatter, 118                  bracket
arithmetic operator, 3                      squiggly, 103
assert statement, 159, 160             bracket operator, 71, 90, 116
assignment, 14, 63, 89                 branch, 41, 47
212                                                                               Index

break statement, 66                     compound statement, 41, 47
bubble sort, 201                        concatenation, 12, 14, 22, 73, 74, 95
bug, 6, 7, 13                               list, 91, 97, 101
     worst, 170                         condition, 41, 47, 65, 196
built-in function                       conditional, 194
     any, 185, 186                          chained, 41, 47
bytes object, 141, 145                      nested, 42, 47
                                        conditional execution, 41
calculator, 8, 15                       conditional expression, 183, 191
call graph, 109, 112                    conditional statement, 41, 47, 55, 184
Car Talk, 88, 113, 124                  consistency check, 111, 158
Card class, 172                         constant time, 208
card, playing, 171                      contributors, vii
carrying, addition with, 68, 156, 158   conversion
catch, 145                                  type, 17
chained conditional, 41, 47             copy
character, 71                               deep, 152
checksum, 143, 146                          shallow, 152
child class, 176, 180                       slice, 74, 92
choice function, 126                        to avoid aliasing, 99
circle function, 31                     copy module, 151
circular definition, 55                 copying objects, 151
class, 4, 147, 153                      count method, 79
     Card, 172                          Counter, 187
     child, 176, 180                    counter, 75, 79, 104, 111
     Deck, 174                          counting and looping, 75
     Hand, 176                          Creative Commons, vi
     Kangaroo, 170                      crossover point, 202, 209
     parent, 176                        crosswords, 83
     Point, 148, 165                    cumulative sum, 100
     Rectangle, 149
     Time, 155                          data encapsulation, 179, 181
class attribute, 172, 180               data structure, 122, 123, 132
class definition, 147                   database, 141, 145
class diagram, 177, 181                 database object, 141
class object, 148, 153, 190             datetime module, 160
close method, 138, 141, 143             dbm module, 141
__cmp__ method, 173                     dead code, 52, 60, 198
Collatz conjecture, 65                  debugger (pdb), 197
collections, 187, 188, 190              debugging, 6, 7, 13, 36, 46, 59, 77, 87, 98, 111,
colon, 19, 194                                   122, 133, 144, 152, 159, 168, 178,
comment, 12, 14                                  185, 193
commutativity, 12, 167                      by bisection, 68
compare function, 52                        emotional response, 6, 200
comparing algorithms, 201                   experimental, 25
comparison                                  rubber duck, 134
     string, 77                             superstition, 200
     tuple, 116, 174                    deck, 171
comparison sort, 205                    Deck class, 174
composition, 19, 22, 26, 54, 174        deck, playing cards, 174
Index                                                                                           213

declaration, 110, 112                                      walk, 140
decrement, 64, 69                                          working, 139
deep copy, 152, 153                                   dispatch
deepcopy function, 152                                     type-based, 167
def keyword, 19                                       dispatch, type-based, 166
default value, 129, 134, 165                          divisibility, 39
      avoiding mutable, 170                           division
defaultdict, 188                                           floating-point, 39
definition                                                 floor, 39, 46, 47
      circular, 55                                    divmod, 117, 158
      class, 147                                      docstring, 35, 37, 148
      function, 19                                    dot notation, 18, 26, 76, 148, 162, 172
      recursive, 124                                  Double Day, 160
del operator, 94                                      double letters, 88
deletion, element of list, 94                         Doyle, Arthur Conan, 25
delimiter, 95, 100                                    duplicate, 101, 113, 146, 187
designed development, 160
deterministic, 126, 134                               element, 89, 100
development plan, 36                                  element deletion, 94
      data encapsulation, 179, 181                    elif keyword, 42
      designed, 158                                   Elkner, Jeff, v, vi
      encapsulation and generalization, 35            ellipses, 19
      incremental, 52, 193                            else keyword, 41
      prototype and patch, 156, 158                   email address, 117
      random walk programming, 134, 200               embedded object, 150, 153, 170
      reduction, 85, 87                                     copying, 152
diagram                                               emotional debugging, 6, 200
      call graph, 112                                 empty list, 89
      class, 177, 181                                 empty string, 79, 95
      object, 148, 150, 152, 153, 155, 173            encapsulation, 32, 36, 54, 69, 75, 177
      stack, 23, 97                                   encode, 171, 180
      state, 9, 63, 78, 90, 96, 108, 120, 148, 150,   encrypt, 171
           152, 155, 173                              end of line character, 144
__dict__ attribute, 168                               enumerate function, 119
dict function, 103                                    enumerate object, 119
dictionary, 103, 112, 120, 197                        epsilon, 67
      initialize, 120                                 equality and assignment, 63
      invert, 107                                     equivalence, 96, 152
      lookup, 106                                     equivalent, 100
      looping with, 106                               error
      reverse lookup, 106                                   runtime, 13, 44, 46, 193
      subtraction, 129                                      semantic, 13, 193, 198
      traversal, 120, 168                                   shape, 122
dictionary methods, 204                                     syntax, 13, 193
      dbm module, 141                                 error checking, 58
dictionary subtraction, 186                           error message, 7, 13, 193
diff, 146                                             eval function, 69
Dijkstra, Edsger, 87                                  evaluate, 10
dir function, 197                                     exception, 13, 14, 193, 196
directory, 139, 145                                         AttributeError, 152, 197
214                                                                                   Index

     FileNotFoundError, 140                        for loop, 30, 44, 72, 91, 119, 184
     IndexError, 72, 78, 90, 197                   formal language, 4, 7
     KeyError, 104, 197                            format operator, 138, 145, 197
     LookupError, 107                              format sequence, 138, 145
     NameError, 22, 197                            format string, 138, 145
     OverflowError, 46                             frame, 23, 26, 44, 56, 109
     RuntimeError, 45                              Free Documentation License, GNU, v, vi
     StopIteration, 185                            frequency, 105
     SyntaxError, 19                                    letter, 123
     TypeError, 72, 74, 108, 116, 118, 139, 164,        word, 125, 134
          197                                      fruitful function, 24, 26
     UnboundLocalError, 110                        frustration, 200
     ValueError, 46, 117                           function, 3, 17, 19, 25, 161
exception, catching, 140                                abs, 52
execute, 11, 14                                         ack, 61, 113
exists function, 139                                    arc, 31
experimental debugging, 25, 134                         choice, 126
exponent, 202                                           circle, 31
exponential growth, 203                                 compare, 52
expression, 10, 14                                      deepcopy, 152
     big and hairy, 199                                 dict, 103
     boolean, 40, 47                                    dir, 197
     conditional, 183, 191                              enumerate, 119
     generator, 185, 186, 191                           eval, 69
extend method, 92                                       exists, 139
                                                        factorial, 56, 183
factorial, 183                                          fibonacci, 57, 109
factorial function, 56, 58                              find, 74
factory, 191                                            float, 17
factory function, 188, 189                              fruitful, 24
False special value, 40                                 getattr, 168
Fermat’s Last Theorem, 48                               getcwd, 139
fibonacci function, 57, 109                             hasattr, 153, 168
file, 137                                               input, 45
      permission, 140                                   int, 17
      reading and writing, 137                          isinstance, 58, 153, 166
file object, 83, 87                                     len, 26, 72, 104
filename, 139                                           list, 94
FileNotFoundError, 140                                  log, 18
filter pattern, 93, 100, 184                            math, 18
find function, 74                                       max, 117, 118
flag, 110, 112                                          min, 117, 118
float function, 17                                      open, 83, 84, 137, 140, 141
float type, 4                                           polygon, 31
floating-point, 4, 7, 67, 183                           popen, 142
floating-point division, 39                             programmer defined, 22, 129
floor division, 39, 46, 47                              randint, 101, 126
flow of execution, 21, 26, 58, 59, 65, 178, 196         random, 126
flower, 37                                              reasons for, 24
folder, 139                                             recursive, 43
Index                                                                               215

    reload, 144, 195                     hashable, 108, 112, 120
    repr, 144                            HashMap, 207
    reversed, 121                        hashtable, 112, 206, 210
    shuffle, 175                         header, 19, 25, 194
    sorted, 99, 106, 121                 Hello, World, 3
    sqrt, 18, 53                         hexadecimal, 148
    str, 18                              high-level language, 6
    sum, 118, 185                        histogram, 105
    trigonometric, 18                         random choice, 126, 130
    tuple, 115                                word frequencies, 127
    tuple as return value, 117           Holmes, Sherlock, 25
    type, 153                            homophone, 113
    void, 24                             hypotenuse, 54
    zip, 118
function argument, 21                    identical, 100
function call, 17, 26                    identity, 96, 152
function composition, 54                 if statement, 41
function definition, 19, 20, 25          immutability, 74, 79, 97, 108, 115, 121
function frame, 23, 26, 44, 56, 109      implementation, 105, 112, 132, 169
function object, 27                      import statement, 26, 144
function parameter, 21                   in operator, 205
function syntax, 162                     in operator, 76, 85, 90, 104
function type, 20                        increment, 64, 69, 157, 163
    modifier, 157                        incremental development, 60, 193
    pure, 156                            indentation, 19, 162, 194
functional programming style, 158, 160   index, 71, 78, 79, 90, 103, 197
                                               looping with, 86, 91
gamma function, 58                             negative, 72
gather, 118, 123, 190                          slice, 73, 91
GCD (greatest common divisor), 61              starting at zero, 71, 90
generalization, 32, 36, 85, 159          IndexError, 72, 78, 90, 197
generator expression, 185, 186, 191      indexing, 204
generator object, 185                    infinite loop, 65, 69, 195, 196
geometric resizing, 209                  infinite recursion, 44, 47, 58, 195, 196
get method, 105                          inheritance, 176, 178, 180, 190
getattr function, 168                    init method, 164, 168, 172, 174, 176
getcwd function, 139                     initialization
global statement, 110, 112                     variable, 69
global variable, 110, 112                initialization (before update), 64
     update, 110                         input function, 45
GNU Free Documentation License, v, vi    instance, 148, 153
greatest common divisor (GCD), 61              as argument, 149
grid, 27                                       as return value, 150
guardian pattern, 59, 60, 78             instance attribute, 148, 153, 172, 180
                                         instantiate, 153
Hand class, 176                          instantiation, 148
hanging, 195                             int function, 17
HAS-A relationship, 177, 180             int type, 4
hasattr function, 153, 168               integer, 4, 7
hash function, 108, 112, 207             interactive mode, 11, 14, 24
216                                                                      Index

interface, 33, 36, 169, 179         Liskov substitution principle, 179
interlocking words, 101             list, 89, 94, 100, 121, 184
interpret, 6                              as argument, 97
interpreter, 2                            concatenation, 91, 97, 101
invariant, 159, 160                       copy, 92
invert dictionary, 107                    element, 90
invocation, 76, 79                        empty, 89
is operator, 95, 152                      function, 94
IS-A relationship, 177, 180               index, 90
isinstance function, 58, 153, 166         membership, 90
item, 74, 79, 89, 103                     method, 92
     dictionary, 112                      nested, 89, 91
item assignment, 74, 90, 116              of objects, 174
item update, 91                           of tuples, 119
items method, 120                         operation, 91
iteration, 64, 69                         repetition, 91
iterator, 119–121, 123, 204               slice, 91
                                          traversal, 91
join, 204                           list comprehension, 184, 191
join method, 95, 175                list methods, 204
                                    literalness, 5
Kangaroo class, 170
key, 103, 112                       local variable, 22, 26
key-value pair, 103, 112, 120       log function, 18
keyboard input, 45                  logarithm, 135
KeyError, 104, 197                  logarithmic growth, 203
KeyError, 206                       logical operator, 40
keyword, 10, 14, 194                lookup, 112
     def, 19                        lookup, dictionary, 106
     elif, 42                       LookupError, 107
     else, 41                       loop, 31, 36, 65, 119
keyword argument, 33, 36, 191             condition, 196
Koch curve, 49                            for, 30, 44, 72, 91
                                          infinite, 65, 196
language                                  nested, 174
     formal, 4                            traversal, 72
     natural, 4                           while, 64
     safe, 13                       loop variable, 184
     Turing complete, 55            looping
leading coefficient, 202                  with dictionaries, 106
leading term, 202, 209                    with indices, 86, 91
leap of faith, 57                         with strings, 75
len function, 26, 72, 104           looping and counting, 75
letter frequency, 123               low-level language, 6
letter rotation, 80, 113            ls (Unix command), 142
linear, 209
linear growth, 203                  machine model, 201, 209
linear search, 205                  main, 23, 43, 110, 144
LinearMap, 206                      maintainable, 169
Linux, 25                           map pattern, 93, 100
lipogram, 84                        map to, 171
Index                                                                           217

mapping, 112, 131                   method, list, 92
Markov analysis, 130                Meyers, Chris, vi
mash-up, 132                        min function, 117, 118
math function, 18                   Moby Project, 83
matplotlib, 135                     model, mental, 199
max function, 117, 118              modifier, 157, 160
McCloskey, Robert, 73               module, 18, 26
md5, 143                                bisect, 101
MD5 algorithm, 146                      collections, 187, 188, 190
md5sum, 146                             copy, 151
membership                              datetime, 160
    binary search, 101                  dbm, 141
    bisection search, 101               os, 139
    dictionary, 104                     pickle, 137, 142
    list, 90                            pprint, 112
    set, 113                            profile, 133
memo, 109, 112                          random, 101, 126, 175
mental model, 199                       reload, 144, 195
metaphor, method invocation, 163        shelve, 142
metathesis, 123                         string, 125
method, 36, 75, 161, 169                structshape, 122
    __cmp__, 173                        time, 101
    __str__, 165, 174               module object, 18, 143
    add, 165                        module, writing, 143
    append, 92, 97, 101, 174, 175   modulus operator, 39, 47
    close, 138, 141, 143            Monty Python and the Holy Grail, 156
    count, 79                       MP3, 146
    extend, 92                      mro method, 179
    get, 105                        multiline string, 35, 194
    init, 164, 172, 174, 176        multiplicity (in class diagram), 178, 181
    items, 120                      multiset, 187
    join, 95, 175                   mutability, 74, 90, 92, 96, 111, 115, 121, 151
    mro, 179                        mutable object, as default value, 170
    pop, 94, 175
    radd, 167                       name built-in variable, 144
    read, 143                       namedtuple, 190
    readline, 83, 143               NameError, 22, 197
    remove, 94                      NaN, 183
    replace, 125                    natural language, 4, 7
    setdefault, 113                 negative index, 72
    sort, 92, 99, 176               nested conditional, 42, 47
    split, 95, 117                  nested list, 89, 91, 100
    string, 79                      newline, 45, 175
    strip, 84, 125                  Newton’s method, 66
    translate, 125                  None special value, 24, 26, 52, 92, 94
    update, 120                     NoneType type, 24
    values, 104                     not operator, 40
    void, 92                        number, random, 126
method resolution order, 179
method syntax, 162                  Obama, Barack, 201
218                                                                                     Index

object, 74, 79, 95, 96, 100                    or operator, 40
    bytes, 141, 145                            order of growth, 202, 209
    class, 147, 148, 153, 190                  order of operations, 11, 14, 199
    copying, 151                               os module, 139
    Counter, 187                               other (parameter name), 164
    database, 141                              OverflowError, 46
    defaultdict, 188                           overloading, 169
    embedded, 150, 153, 170                    override, 129, 134, 165, 173, 176, 179
    enumerate, 119
    file, 83, 87                               palindrome, 61, 80, 86, 88
    function, 27                               parameter, 21, 23, 26, 97
    generator, 185                                  gather, 118
    module, 143                                     optional, 129, 165
    mutable, 151                                    other, 164
    namedtuple, 190                                 self, 163
    pipe, 145                                  parent class, 176, 180
    printing, 162                              parentheses
    set, 186                                        argument in, 17
    zip, 123                                        empty, 19, 76
object diagram, 148, 150, 152, 153, 155, 173        parameters in, 21, 22
object-oriented design, 169                         parent class in, 176
object-oriented language, 169                       tuples in, 115
object-oriented programming, 147, 161, 169,    parse, 5, 7
          176                                  pass statement, 41
odometer, 88                                   path, 139, 145
Olin College, v                                     absolute, 139
open function, 83, 84, 137, 140, 141                relative, 139
operand, 14                                    pattern
operator, 7                                         filter, 93, 100, 184
    and, 40                                         guardian, 59, 60, 78
    arithmetic, 3                                   map, 93, 100
    bitwise, 3                                      reduce, 93, 100
    boolean, 76                                     search, 75, 79, 85, 107, 186
    bracket, 71, 90, 116                            swap, 116
    del, 94                                    pdb (Python debugger), 197
    format, 138, 145, 197                      PEMDAS, 11
    in, 76, 85, 90, 104                        permission, file, 140
    is, 95, 152                                persistence, 137, 145
    logical, 40                                pi, 18, 70
    modulus, 39, 47                            pickle module, 137, 142
    not, 40                                    pickling, 142
    or, 40                                     pie, 37
    overloading, 169                           pipe, 142
    relational, 40, 173                        pipe object, 145
    slice, 73, 79, 91, 98, 116                 plain text, 83, 125
    string, 12                                 planned development, 158
    update, 93                                 poetry, 5
operator overloading, 166, 173                 Point class, 148, 165
optional argument, 76, 79, 95, 107, 184        point, mathematical, 147
optional parameter, 129, 165                   poker, 171, 181
Index                                                                          219

polygon function, 31                      random walk programming, 134, 200
polymorphism, 168, 169                    rank, 171
pop method, 94, 175                       read method, 143
popen function, 142                       readline method, 83, 143
portability, 6                            reassignment, 63, 68, 90, 110
positional argument, 164, 169, 190        Rectangle class, 149
postcondition, 36, 59, 179                recursion, 43, 47, 55, 57
pprint module, 112                             base case, 44
precedence, 199                                infinite, 44, 58, 196
precondition, 36, 37, 59, 179             recursive definition, 56, 124
prefix, 131                               red-black tree, 206
pretty print, 112                         reduce pattern, 93, 100
print function, 3                         reducible word, 113, 124
print statement, 3, 7, 165, 197           reduction to a previously solved problem,
problem solving, 1, 6                                85
profile module, 133                       reduction to a previously solved problem,
program, 1, 6                                        87
program testing, 87                       redundancy, 5
programmer-defined function, 22, 129      refactoring, 34–36, 180
programmer-defined type, 147, 153, 155,   reference, 96, 97, 100
          162, 165, 173                        aliasing, 96
Project Gutenberg, 125                    rehashing, 208
prompt, 2, 6, 45                          relational operator, 40, 173
prose, 5                                  relative path, 139, 145
prototype and patch, 156, 158, 160        reload function, 144, 195
pseudorandom, 126, 134                    remove method, 94
pure function, 156, 160                   repetition, 30
Puzzler, 88, 113, 124                          list, 91
Pythagorean theorem, 52                   replace method, 125
Python                                    repr function, 144
     running, 2                           representation, 147, 149, 171
Python 2, 2, 3, 33, 40, 45                return statement, 44, 51, 199
Python in a browser, 2                    return value, 17, 26, 51, 150
PythonAnywhere, 2                              tuple, 117
                                          reverse lookup, 112
quadratic, 209                            reverse lookup, dictionary, 106
quadratic growth, 203                     reverse word pair, 101
quotation mark, 3, 4, 35, 74, 194         reversed function, 121
                                          rotation
radd method, 167                               letters, 113
radian, 18                                rotation, letter, 80
radix sort, 201                           rubber duck debugging, 134
rage, 200                                 running pace, 8, 15, 160
raise statement, 107, 112, 159            running Python, 2
Ramanujan, Srinivasa, 70                  runtime error, 13, 44, 46, 193, 196
randint function, 101, 126                RuntimeError, 45, 58
random function, 126
random module, 101, 126, 175              safe language, 13
random number, 126                        sanity check, 111
random text, 131                          scaffolding, 53, 60, 112
220                                                                             Index

scatter, 118, 123, 191                  squiggly bracket, 103
Schmidt, Eric, 201                      stable sort, 205
Scrabble, 123                           stack diagram, 23, 26, 37, 44, 56, 60, 97
script, 11, 14                          state diagram, 9, 14, 63, 78, 90, 96, 108, 120,
script mode, 11, 14, 24                            148, 150, 152, 155, 173
search, 107, 205, 209                   statement, 10, 14
search pattern, 75, 79, 85, 186              assert, 159, 160
search, binary, 101                          assignment, 9, 63
search, bisection, 101                       break, 66
self (parameter name), 163                   compound, 41
semantic error, 13, 14, 193, 198             conditional, 41, 47, 55, 184
semantics, 14, 162                           for, 30, 72, 91
sequence, 4, 71, 79, 89, 94, 115, 121        global, 110, 112
set, 130, 186                                if, 41
      anagram, 123, 145                      import, 26, 144
set membership, 113                          pass, 41
set subtraction, 186                         print, 3, 7, 165, 197
setdefault, 189                              raise, 107, 112, 159
setdefault method, 113                       return, 44, 51, 199
sexagesimal, 158                             try, 140, 153
shallow copy, 152, 153                       while, 64
shape, 123                              step size, 79
shape error, 122                        StopIteration, 185
shell, 142, 145                         str function, 18
shelve module, 142                      __str__ method, 165, 174
shuffle function, 175                   string, 4, 7, 94, 121
sine function, 18                            accumulator, 175
singleton, 108, 112, 115                     comparison, 77
slice, 79                                    empty, 95
      copy, 74, 92                           immutable, 74
      list, 91                               method, 75
      string, 73                             multiline, 35, 194
      tuple, 116                             operation, 12
      update, 92                             slice, 73
slice operator, 73, 79, 91, 98, 116          triple-quoted, 35
sort method, 92, 99, 176                string concatenation, 204
sorted                                  string method, 79
      function, 99, 106                 string methods, 204
sorted function, 121                    string module, 125
sorting, 204, 205                       string representation, 144, 165
special case, 87, 157                   string type, 4
special value                           strip method, 84, 125
      False, 40                         structshape module, 122
      None, 24, 26, 52, 92, 94          structure, 5
      True, 40                          subject, 163, 169
spiral, 38                              subset, 187
split method, 95, 117                   subtraction
sqrt, 53                                     dictionary, 129
sqrt function, 18                            with borrowing, 68
square root, 66                         subtraction with borrowing, 159
Index                                                                                          221

suffix, 131                                         Turing Thesis, 55
suit, 171                                           Turing, Alan, 55
sum, 185                                            turtle module, 48
sum function, 118                                   turtle typewriter, 37
superstitious debugging, 200                        type, 4, 7
swap pattern, 116                                        bool, 40
syntax, 5, 7, 13, 162, 194                               dict, 103
syntax error, 13, 14, 193                                file, 137
SyntaxError, 19                                          float, 4
                                                         function, 20
temporary variable, 51, 60, 199                          int, 4
test case, minimal, 198                                  list, 89
testing                                                  NoneType, 24
     and absence of bugs, 87                             programmer-defined, 147, 153, 155, 162,
     incremental development, 52                               165, 173
     is hard, 87                                         set, 130
     knowing the answer, 53                              str, 4
     leap of faith, 57                                   tuple, 115
     minimal test case, 198                         type checking, 58
text                                                type conversion, 17
     plain, 83, 125                                 type function, 153
     random, 131                                    type-based dispatch, 166, 167, 169
text file, 145                                      TypeError, 72, 74, 108, 116, 118, 139, 164, 197
Time class, 155                                     typewriter, turtle, 37
time module, 101                                    typographical error, 134
token, 5, 7
traceback, 24, 26, 44, 46, 107, 196                 UnboundLocalError, 110
translate method, 125                               underscore character, 10
traversal, 72, 75, 77, 79, 85, 93, 100, 105, 106,   uniqueness, 101
           119, 127                                 Unix command
     dictionary, 168                                    ls, 142
     list, 91                                       update, 64, 67, 69
traverse                                                database, 141
     dictionary, 120                                    global variable, 110
triangle, 48                                            histogram, 127
trigonometric function, 18                              item, 91
triple-quoted string, 35                                slice, 92
True special value, 40                              update method, 120
try statement, 140, 153                             update operator, 93
tuple, 115, 117, 121, 122                           use before def, 20
     as key in dictionary, 120, 132
     assignment, 116                                value, 4, 7, 95, 96, 112
     comparison, 116, 174                               default, 129
     in brackets, 120                                   tuple, 117
     singleton, 115                                 ValueError, 46, 117
     slice, 116                                     values method, 104
tuple assignment, 117, 119, 122                     variable, 9, 14
tuple function, 115                                     global, 110
tuple methods, 204                                      local, 22
Turing complete language, 55                            temporary, 51, 60, 199
222                                   Index

    updating, 64
variable-length argument tuple, 118
veneer, 175, 180
void function, 24, 26
void method, 92
vorpal, 55

walk, directory, 140
while loop, 64
whitespace, 46, 84, 144, 194
word count, 143
word frequency, 125, 134
word, reducible, 113, 124
working directory, 139
worst bug, 170
worst case, 202, 209

zero, index starting at, 71
zero, index starting at, 90
zip function, 118
     use with dict, 120
zip object, 123
Zipf’s law, 134
