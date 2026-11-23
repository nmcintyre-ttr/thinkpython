# Preface

Preface

The strange history of this book
In January 1999 I was preparing to teach an introductory programming class in Java. I had
taught it three times and I was getting frustrated. The failure rate in the class was too high
and, even for students who succeeded, the overall level of achievement was too low.
One of the problems I saw was the books. They were too big, with too much unnecessary
detail about Java, and not enough high-level guidance about how to program. And they all
suffered from the trap door effect: they would start out easy, proceed gradually, and then
somewhere around Chapter 5 the bottom would fall out. The students would get too much
new material, too fast, and I would spend the rest of the semester picking up the pieces.
Two weeks before the first day of classes, I decided to write my own book. My goals were:

   • Keep it short. It is better for students to read 10 pages than not read 50 pages.
   • Be careful with vocabulary. I tried to minimize jargon and define each term at first
     use.
   • Build gradually. To avoid trap doors, I took the most difficult topics and split them
     into a series of small steps.
   • Focus on programming, not the programming language. I included the minimum
     useful subset of Java and left out the rest.

I needed a title, so on a whim I chose How to Think Like a Computer Scientist.
My first version was rough, but it worked. Students did the reading, and they understood
enough that I could spend class time on the hard topics, the interesting topics and (most
important) letting the students practice.
I released the book under the GNU Free Documentation License, which allows users to
copy, modify, and distribute the book.
What happened next is the cool part. Jeff Elkner, a high school teacher in Virginia, adopted
my book and translated it into Python. He sent me a copy of his translation, and I had the
unusual experience of learning Python by reading my own book. As Green Tea Press, I
published the first Python version in 2001.
In 2003 I started teaching at Olin College and I got to teach Python for the first time. The
contrast with Java was striking. Students struggled less, learned more, worked on more
interesting projects, and generally had a lot more fun.
vi                                                                                   Preface

Since then I’ve continued to develop the book, correcting errors, improving some of the
examples and adding material, especially exercises.
The result is this book, now with the less grandiose title Think Python. Some of the changes
are:

     • I added a section about debugging at the end of each chapter. These sections present
       general techniques for finding and avoiding bugs, and warnings about Python pit-
       falls.
     • I added more exercises, ranging from short tests of understanding to a few substantial
       projects. Most exercises include a link to my solution.
     • I added a series of case studies—longer examples with exercises, solutions, and dis-
       cussion.
     • I expanded the discussion of program development plans and basic design patterns.
     • I added appendices about debugging and analysis of algorithms.

The second edition of Think Python has these new features:

     • The book and all supporting code have been updated to Python 3.
     • I added a few sections, and more details on the web, to help beginners get started
       running Python in a browser, so you don’t have to deal with installing Python until
       you want to.
     • For Chapter 4.1 I switched from my own turtle graphics package, called Swampy, to a
       more standard Python module, turtle, which is easier to install and more powerful.
     • I added a new chapter called “The Goodies”, which introduces some additional
       Python features that are not strictly necessary, but sometimes handy.

I hope you enjoy working with this book, and that it helps you learn to program and think
like a computer scientist, at least a little bit.
Allen B. Downey

Olin College

Acknowledgments
Many thanks to Jeff Elkner, who translated my Java book into Python, which got this
project started and introduced me to what has turned out to be my favorite language.
Thanks also to Chris Meyers, who contributed several sections to How to Think Like a Com-
puter Scientist.
Thanks to the Free Software Foundation for developing the GNU Free Documentation Li-
cense, which helped make my collaboration with Jeff and Chris possible, and Creative
Commons for the license I am using now.
                                                                                               vii

Thanks to the editors at Lulu who worked on How to Think Like a Computer Scientist.

Thanks to the editors at O’Reilly Media who worked on Think Python.

Thanks to all the students who worked with earlier versions of this book and all the con-
tributors (listed below) who sent in corrections and suggestions.

Contributor List
More than 100 sharp-eyed and thoughtful readers have sent in suggestions and corrections
over the past few years. Their contributions, and enthusiasm for this project, have been a
huge help.

If you have a suggestion or correction, please send email to feedback@thinkpython.com.
If I make a change based on your feedback, I will add you to the contributor list (unless
you ask to be omitted).

If you include at least part of the sentence the error appears in, that makes it easy for me to
search. Page and section numbers are fine, too, but not quite as easy to work with. Thanks!

   • Lloyd Hugh Allen sent in a correction to Section 8.4.

   • Yvon Boulianne sent in a correction of a semantic error in Chapter 5.

   • Fred Bremmer submitted a correction in Section 2.1.

   • Jonah Cohen wrote the Perl scripts to convert the LaTeX source for this book into beautiful
     HTML.

   • Michael Conlon sent in a grammar correction in Chapter 2 and an improvement in style in
     Chapter 1, and he initiated discussion on the technical aspects of interpreters.

   • Benoît Girard sent in a correction to a humorous mistake in Section 5.6.

   • Courtney Gleason and Katherine Smith wrote horsebet.py, which was used as a case study
     in an earlier version of the book. Their program can now be found on the website.

   • Lee Harr submitted more corrections than we have room to list here, and indeed he should be
     listed as one of the principal editors of the text.

   • James Kaylin is a student using the text. He has submitted numerous corrections.

   • David Kershaw fixed the broken catTwice function in Section 3.10.

   • Eddie Lam has sent in numerous corrections to Chapters 1, 2, and 3. He also fixed the Makefile
     so that it creates an index the first time it is run and helped us set up a versioning scheme.

   • Man-Yong Lee sent in a correction to the example code in Section 2.4.

   • David Mayo pointed out that the word “unconsciously" in Chapter 1 needed to be changed to
     “subconsciously".

   • Chris McAloon sent in several corrections to Sections 3.9 and 3.10.

   • Matthew J. Moelter has been a long-time contributor who sent in numerous corrections and
     suggestions to the book.
viii                                                                                        Preface

   • Simon Dicon Montford reported a missing function definition and several typos in Chapter 3.
     He also found errors in the increment function in Chapter 13.

   • John Ouzts corrected the definition of “return value" in Chapter 3.

   • Kevin Parks sent in valuable comments and suggestions as to how to improve the distribution
     of the book.

   • David Pool sent in a typo in the glossary of Chapter 1, as well as kind words of encouragement.

   • Michael Schmitt sent in a correction to the chapter on files and exceptions.

   • Robin Shaw pointed out an error in Section 13.1, where the printTime function was used in an
     example without being defined.

   • Paul Sleigh found an error in Chapter 7 and a bug in Jonah Cohen’s Perl script that generates
     HTML from LaTeX.

   • Craig T. Snydal is testing the text in a course at Drew University. He has contributed several
     valuable suggestions and corrections.

   • Ian Thomas and his students are using the text in a programming course. They are the first ones
     to test the chapters in the latter half of the book, and they have made numerous corrections and
     suggestions.

   • Keith Verheyden sent in a correction in Chapter 3.

   • Peter Winstanley let us know about a longstanding error in our Latin in Chapter 3.

   • Chris Wrobel made corrections to the code in the chapter on file I/O and exceptions.

   • Moshe Zadka has made invaluable contributions to this project. In addition to writing the first
     draft of the chapter on Dictionaries, he provided continual guidance in the early stages of the
     book.

   • Christoph Zwerschke sent several corrections and pedagogic suggestions, and explained the
     difference between gleich and selbe.

   • James Mayer sent us a whole slew of spelling and typographical errors, including two in the
     contributor list.

   • Hayden McAfee caught a potentially confusing inconsistency between two examples.

   • Angel Arnal is part of an international team of translators working on the Spanish version of
     the text. He has also found several errors in the English version.

   • Tauhidul Hoque and Lex Berezhny created the illustrations in Chapter 1 and improved many
     of the other illustrations.

   • Dr. Michele Alzetta caught an error in Chapter 8 and sent some interesting pedagogic com-
     ments and suggestions about Fibonacci and Old Maid.

   • Andy Mitchell caught a typo in Chapter 1 and a broken example in Chapter 2.

   • Kalin Harvey suggested a clarification in Chapter 7 and caught some typos.

   • Christopher P. Smith caught several typos and helped us update the book for Python 2.2.

   • David Hutchins caught a typo in the Foreword.

   • Gregor Lingl is teaching Python at a high school in Vienna, Austria. He is working on a Ger-
     man translation of the book, and he caught a couple of bad errors in Chapter 5.
                                                                                                ix

• Julie Peters caught a typo in the Preface.

• Florin Oprina sent in an improvement in makeTime, a correction in printTime, and a nice typo.

• D. J. Webre suggested a clarification in Chapter 3.

• Ken found a fistful of errors in Chapters 8, 9 and 11.

• Ivo Wever caught a typo in Chapter 5 and suggested a clarification in Chapter 3.

• Curtis Yanko suggested a clarification in Chapter 2.

• Ben Logan sent in a number of typos and problems with translating the book into HTML.

• Jason Armstrong saw the missing word in Chapter 2.

• Louis Cordier noticed a spot in Chapter 16 where the code didn’t match the text.

• Brian Cain suggested several clarifications in Chapters 2 and 3.

• Rob Black sent in a passel of corrections, including some changes for Python 2.2.

• Jean-Philippe Rey at École Centrale Paris sent a number of patches, including some updates
  for Python 2.2 and other thoughtful improvements.

• Jason Mader at George Washington University made a number of useful suggestions and cor-
  rections.

• Jan Gundtofte-Bruun reminded us that “a error” is an error.

• Abel David and Alexis Dinno reminded us that the plural of “matrix” is “matrices”, not “ma-
  trixes”. This error was in the book for years, but two readers with the same initials reported it
  on the same day. Weird.

• Charles Thayer encouraged us to get rid of the semi-colons we had put at the ends of some
  statements and to clean up our use of “argument” and “parameter”.

• Roger Sperberg pointed out a twisted piece of logic in Chapter 3.

• Sam Bull pointed out a confusing paragraph in Chapter 2.

• Andrew Cheung pointed out two instances of “use before def”.

• C. Corey Capel spotted the missing word in the Third Theorem of Debugging and a typo in
  Chapter 4.

• Alessandra helped clear up some Turtle confusion.

• Wim Champagne found a brain-o in a dictionary example.

• Douglas Wright pointed out a problem with floor division in arc.

• Jared Spindor found some jetsam at the end of a sentence.

• Lin Peiheng sent a number of very helpful suggestions.

• Ray Hagtvedt sent in two errors and a not-quite-error.

• Torsten Hübsch pointed out an inconsistency in Swampy.

• Inga Petuhhov corrected an example in Chapter 14.

• Arne Babenhauserheide sent several helpful corrections.
x                                                                                         Preface

    • Mark E. Casida is is good at spotting repeated words.

    • Scott Tyler filled in a that was missing. And then sent in a heap of corrections.

    • Gordon Shephard sent in several corrections, all in separate emails.

    • Andrew Turner spotted an error in Chapter 8.

    • Adam Hobart fixed a problem with floor division in arc.

    • Daryl Hammond and Sarah Zimmerman pointed out that I served up math.pi too early. And
      Zim spotted a typo.

    • George Sass found a bug in a Debugging section.

    • Brian Bingham suggested Exercise 11.5.

    • Leah Engelbert-Fenton pointed out that I used tuple as a variable name, contrary to my own
      advice. And then found a bunch of typos and a “use before def”.

    • Joe Funke spotted a typo.

    • Chao-chao Chen found an inconsistency in the Fibonacci example.

    • Jeff Paine knows the difference between space and spam.

    • Lubos Pintes sent in a typo.

    • Gregg Lind and Abigail Heithoff suggested Exercise 14.3.

    • Max Hailperin has sent in a number of corrections and suggestions. Max is one of the authors
      of the extraordinary Concrete Abstractions, which you might want to read when you are done
      with this book.

    • Chotipat Pornavalai found an error in an error message.

    • Stanislaw Antol sent a list of very helpful suggestions.

    • Eric Pashman sent a number of corrections for Chapters 4–11.

    • Miguel Azevedo found some typos.

    • Jianhua Liu sent in a long list of corrections.

    • Nick King found a missing word.

    • Martin Zuther sent a long list of suggestions.

    • Adam Zimmerman found an inconsistency in my instance of an “instance” and several other
      errors.

    • Ratnakar Tiwari suggested a footnote explaining degenerate triangles.

    • Anurag Goel suggested another solution for is_abecedarian and sent some additional correc-
      tions. And he knows how to spell Jane Austen.

    • Kelli Kratzer spotted one of the typos.

    • Mark Griffiths pointed out a confusing example in Chapter 3.

    • Roydan Ongie found an error in my Newton’s method.

    • Patryk Wolowiec helped me with a problem in the HTML version.
                                                                                          xi

• Mark Chonofsky told me about a new keyword in Python 3.
• Russell Coleman helped me with my geometry.
• Nam Nguyen found a typo and pointed out that I used the Decorator pattern but didn’t men-
  tion it by name.
• Stéphane Morin sent in several corrections and suggestions.
• Paul Stoop corrected a typo in uses_only.
• Eric Bronner pointed out a confusion in the discussion of the order of operations.
• Alexandros Gezerlis set a new standard for the number and quality of suggestions he submit-
  ted. We are deeply grateful!
• Gray Thomas knows his right from his left.
• Giovanni Escobar Sosa sent a long list of corrections and suggestions.
• Daniel Neilson corrected an error about the order of operations.
• Will McGinnis pointed out that polyline was defined differently in two places.
• Frank Hecker pointed out an exercise that was under-specified, and some broken links.
• Animesh B helped me clean up a confusing example.
• Martin Caspersen found two round-off errors.
• Gregor Ulm sent several corrections and suggestions.
• Dimitrios Tsirigkas suggested I clarify an exercise.
• Carlos Tafur sent a page of corrections and suggestions.
• Martin Nordsletten found a bug in an exercise solution.
• Sven Hoexter pointed out that a variable named input shadows a build-in function.
• Stephen Gregory pointed out the problem with cmp in Python 3.
• Ishwar Bhat corrected my statement of Fermat’s last theorem.
• Andrea Zanella translated the book into Italian, and sent a number of corrections along the
  way.
• Many, many thanks to Melissa Lewis and Luciano Ramalho for excellent comments and sug-
  gestions on the second edition.
• Thanks to Harry Percival from PythonAnywhere for his help getting people started running
  Python in a browser.
• Xavier Van Aubel made several useful corrections in the second edition.
• William Murray corrected my definition of floor division.
• Per Starbäck brought me up to date on universal newlines in Python 3.
• Laurent Rosenfeld and Mihaela Rotaru translated this book into French. Along the way, they
  sent many corrections and suggestions.
  In addition, people who spotted typos or made corrections include Czeslaw Czapla, Dale Wil-
  son, Francesco Carlo Cimini, Richard Fursa, Brian McGhie, Lokesh Kumar Makani, Matthew
  Shultz, Viet Le, Victor Simeone, Lars O.D. Christensen, Swarup Sahoo, Alix Etienne, Kuang
  He, Wei Huang, Karen Barber, and Eric Ransom.
xii   Preface
Contents

Preface                                                                                            v

1   The way of the program                                                                         1

    1.1    What is a program? . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .      1

    1.2    Running Python . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .      2

    1.3    The first program . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .     3

    1.4    Arithmetic operators . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .      3

    1.5    Values and types . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .       4

    1.6    Formal and natural languages . . . . . . . . . . . . . . . . . . . . . . . . . .         4

    1.7    Debugging . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .     6

    1.8    Glossary . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .    6

    1.9    Exercises . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .   7

2   Variables, expressions and statements                                                          9

    2.1    Assignment statements . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .        9

    2.2    Variable names . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .       9

    2.3    Expressions and statements . . . . . . . . . . . . . . . . . . . . . . . . . . .        10

    2.4    Script mode . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .     11

    2.5    Order of operations . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .     11

    2.6    String operations . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .     12

    2.7    Comments . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .      12

    2.8    Debugging . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .     13

    2.9    Glossary . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .    14

    2.10   Exercises . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .   14
xiv                                                                                          Contents

3     Functions                                                                                      17

      3.1    Function calls . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .    17

      3.2    Math functions . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .    18

      3.3    Composition . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .     19

      3.4    Adding new functions . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .        19

      3.5    Definitions and uses . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .      20

      3.6    Flow of execution . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .     21

      3.7    Parameters and arguments . . . . . . . . . . . . . . . . . . . . . . . . . . . .        21

      3.8    Variables and parameters are local . . . . . . . . . . . . . . . . . . . . . . .        22

      3.9    Stack diagrams . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .      23

      3.10   Fruitful functions and void functions . . . . . . . . . . . . . . . . . . . . . .       24

      3.11   Why functions? . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .      24

      3.12   Debugging . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .     25

      3.13   Glossary . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .    25

      3.14   Exercises . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .   26

4     Case study: interface design                                                                   29

      4.1    The turtle module . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .     29

      4.2    Simple repetition . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .     30

      4.3    Exercises . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .   31

      4.4    Encapsulation . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .     32

      4.5    Generalization . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .    32

      4.6    Interface design . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .    33

      4.7    Refactoring . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .   34

      4.8    A development plan . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .        35

      4.9    docstring . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .   35

      4.10   Debugging . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .     36

      4.11   Glossary . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .    36

      4.12   Exercises . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .   37
Contents                                                                                           xv

5   Conditionals and recursion                                                                     39

    5.1    Floor division and modulus . . . . . . . . . . . . . . . . . . . . . . . . . . .        39

    5.2    Boolean expressions . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .     40

    5.3    Logical operators . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .     40

    5.4    Conditional execution . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .       41

    5.5    Alternative execution . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .     41

    5.6    Chained conditionals . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .      41

    5.7    Nested conditionals . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .     42

    5.8    Recursion . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .   43

    5.9    Stack diagrams for recursive functions . . . . . . . . . . . . . . . . . . . . .        44

    5.10   Infinite recursion . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .    44

    5.11   Keyboard input . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .      45

    5.12   Debugging . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .     46

    5.13   Glossary . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .    47

    5.14   Exercises . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .   47

6   Fruitful functions                                                                             51

    6.1    Return values . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .     51

    6.2    Incremental development . . . . . . . . . . . . . . . . . . . . . . . . . . . .         52

    6.3    Composition . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .     54

    6.4    Boolean functions . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .     54

    6.5    More recursion . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .    55

    6.6    Leap of faith . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .   57

    6.7    One more example . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .        57

    6.8    Checking types . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .      58

    6.9    Debugging . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .     59

    6.10   Glossary . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .    60

    6.11   Exercises . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .   60
xvi                                                                                           Contents

7     Iteration                                                                                       63
      7.1    Reassignment . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .       63
      7.2    Updating variables . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .       64
      7.3    The while statement . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .        64
      7.4    break . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .    66
      7.5    Square roots . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .     66
      7.6    Algorithms . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .     67
      7.7    Debugging . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .      68
      7.8    Glossary . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .     68
      7.9    Exercises . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .    69

8     Strings                                                                                         71
      8.1    A string is a sequence . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .     71
      8.2    len . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .    72
      8.3    Traversal with a for loop . . . . . . . . . . . . . . . . . . . . . . . . . . . . .      72
      8.4    String slices . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .    73
      8.5    Strings are immutable . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .        74
      8.6    Searching . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .    74
      8.7    Looping and counting . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .         75
      8.8    String methods . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .       75
      8.9    The in operator . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .      76
      8.10   String comparison . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .      77
      8.11   Debugging . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .      77
      8.12   Glossary . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .     79
      8.13   Exercises . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .    79

9     Case study: word play                                                                           83
      9.1    Reading word lists . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .       83
      9.2    Exercises . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .    84
      9.3    Search . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .   85
      9.4    Looping with indices . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .       86
      9.5    Debugging . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .      87
      9.6    Glossary . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .     87
      9.7    Exercises . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .    88
Contents                                                                                             xvii

10 Lists                                                                                              89

   10.1    A list is a sequence . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .       89

   10.2    Lists are mutable . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .        90

   10.3    Traversing a list . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .      91

   10.4    List operations . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .      91

   10.5    List slices . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .    91

   10.6    List methods . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .       92

   10.7    Map, filter and reduce . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .         93

   10.8    Deleting elements . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .        94

   10.9    Lists and strings . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .      94

   10.10 Objects and values . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .           95

   10.11 Aliasing . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .       96

   10.12 List arguments . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .         97

   10.13 Debugging . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .          98

   10.14 Glossary . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .        100

   10.15 Exercises . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .       100

11 Dictionaries                                                                                      103

   11.1    A dictionary is a mapping . . . . . . . . . . . . . . . . . . . . . . . . . . . .         103

   11.2    Dictionary as a collection of counters . . . . . . . . . . . . . . . . . . . . . . 104

   11.3    Looping and dictionaries . . . . . . . . . . . . . . . . . . . . . . . . . . . . .        106

   11.4    Reverse lookup . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .        106

   11.5    Dictionaries and lists . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .      107

   11.6    Memos . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .       109

   11.7    Global variables . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .      110

   11.8    Debugging . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .       111

   11.9    Glossary . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .      112

   11.10 Exercises . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .       113
xviii                                                                                      Contents

12 Tuples                                                                                          115

   12.1    Tuples are immutable . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .      115

   12.2    Tuple assignment . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .      116

   12.3    Tuples as return values . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .     117

   12.4    Variable-length argument tuples . . . . . . . . . . . . . . . . . . . . . . . .         118

   12.5    Lists and tuples . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .    118

   12.6    Dictionaries and tuples . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .     120

   12.7    Sequences of sequences . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .      121

   12.8    Debugging . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .     122

   12.9    Glossary . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .    122

   12.10 Exercises . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .     123

13 Case study: data structure selection                                                            125

   13.1    Word frequency analysis . . . . . . . . . . . . . . . . . . . . . . . . . . . . .       125

   13.2    Random numbers . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .        126

   13.3    Word histogram . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .      127

   13.4    Most common words . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .         128

   13.5    Optional parameters . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .       129

   13.6    Dictionary subtraction . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .      129

   13.7    Random words . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .        130

   13.8    Markov analysis . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .     130

   13.9    Data structures . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .   132

   13.10 Debugging . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .       133

   13.11 Glossary . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .      134

   13.12 Exercises . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .     134

14 Files                                                                                           137

   14.1    Persistence . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .   137

   14.2    Reading and writing . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .       137

   14.3    Format operator . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .     138

   14.4    Filenames and paths . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .       139

   14.5    Catching exceptions . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .     140
Contents                                                                                            xix

   14.6    Databases . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .    141

   14.7    Pickling . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .   142

   14.8    Pipes . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .    142

   14.9    Writing modules . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .      143

   14.10 Debugging . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .        144

   14.11 Glossary . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .       145

   14.12 Exercises . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .      145

15 Classes and objects                                                                              147

   15.1    Programmer-defined types . . . . . . . . . . . . . . . . . . . . . . . . . . . .         147

   15.2    Attributes . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .     148

   15.3    Rectangles . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .     149

   15.4    Instances as return values . . . . . . . . . . . . . . . . . . . . . . . . . . . .       150

   15.5    Objects are mutable . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .      151

   15.6    Copying . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .      151

   15.7    Debugging . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .      152

   15.8    Glossary . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .     153

   15.9    Exercises . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .    154

16 Classes and functions                                                                            155

   16.1    Time . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .   155

   16.2    Pure functions . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .     156

   16.3    Modifiers . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .    157

   16.4    Prototyping versus planning . . . . . . . . . . . . . . . . . . . . . . . . . . .        158

   16.5    Debugging . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .      159

   16.6    Glossary . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .     160

   16.7    Exercises . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .    160

17 Classes and methods                                                                              161

   17.1    Object-oriented features . . . . . . . . . . . . . . . . . . . . . . . . . . . . .       161

   17.2    Printing objects . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .     162

   17.3    Another example . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .        163
xx                                                                                           Contents

     17.4   A more complicated example . . . . . . . . . . . . . . . . . . . . . . . . . .           164

     17.5   The init method . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .      164

     17.6   The __str__ method . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 165

     17.7   Operator overloading . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .       165

     17.8   Type-based dispatch . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .        166

     17.9   Polymorphism . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .       167

     17.10 Debugging . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .       168

     17.11 Interface and implementation . . . . . . . . . . . . . . . . . . . . . . . . . .          169

     17.12 Glossary . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .      169

     17.13 Exercises . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .     170

18 Inheritance                                                                                       171

     18.1   Card objects . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .     171

     18.2   Class attributes . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .     172

     18.3   Comparing cards . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .        173

     18.4   Decks . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .    174

     18.5   Printing the deck . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .      174

     18.6   Add, remove, shuffle and sort . . . . . . . . . . . . . . . . . . . . . . . . . .        175

     18.7   Inheritance . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .    176

     18.8   Class diagrams . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .       177

     18.9   Debugging . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .      178

     18.10 Data encapsulation . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .        179

     18.11 Glossary . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .      180

     18.12 Exercises . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .     181

19 The Goodies                                                                                       183

     19.1   Conditional expressions . . . . . . . . . . . . . . . . . . . . . . . . . . . . .        183

     19.2   List comprehensions . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .        184

     19.3   Generator expressions . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .        185

     19.4   any and all . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 185

     19.5   Sets . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .   186

     19.6   Counters . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .     187
Contents                                                                                           xxi

  19.7     defaultdict . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .   188

  19.8     Named tuples . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .      189

  19.9     Gathering keyword args . . . . . . . . . . . . . . . . . . . . . . . . . . . . .        190

  19.10 Glossary . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .       191

  19.11 Exercises . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .      192

A Debugging                                                                                        193

  A.1      Syntax errors . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .   193

  A.2      Runtime errors . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .    195

  A.3      Semantic errors . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .     198

B Analysis of Algorithms                                                                           201

  B.1      Order of growth . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .     202

  B.2      Analysis of basic Python operations . . . . . . . . . . . . . . . . . . . . . . 204

  B.3      Analysis of search algorithms . . . . . . . . . . . . . . . . . . . . . . . . . .       205

  B.4      Hashtables . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .    206

  B.5      Glossary . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .    209
xxii   Contents
