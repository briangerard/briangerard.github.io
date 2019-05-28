# Sites and Exercises for Scripting Practice

A number of people have asked me for tips on improving their scripting skills in various
languages.  Reading books and tutorials helps, but honestly, there is simply no substitute
for practice.  Writing and running code, and *especially* screwing it up and fixing it,
gets me up to speed in a new language more quickly than any amount of reading alone.

Here are some sites I've found useful, along with Python and Perl [Koans](#footnotes).
Enjoy, and let me know if you have any questions!

## Sites

All of these sites basically have sets of problems that you can solve in various
languages.  They let you edit it online, and then just hit a button and run it through
their tests to see how you did.  So you get instant feedback from the system as you go,
and you know when you've solved the problem.  They each have their own reward systems,
points, badges, ranks, etc.  It can be oddly satisfying to see your score go up as you
complete more challenges.  `:)`


### Exercism

[https://exercism.io/](https://exercism.io/)

One of the first ones I played around on, I like it because other members can review my
code.  They'll point out cases I might have missed, or suggest other approaches to a
problem, or other helpful tips.  It's very handy to get that extra perspective.  It has
definitely made me a better software engineer.  That's not to say that I always take the
suggestions, either.  It's also valuable to gain experience defending the design choices I
made.  There are always tradeoffs to be made, and it helps me clarify my thinking when I
have to articulate which choice I made and why.

You pick which "tracks" (basically, languages) you want to practice, and then tackle
whichever exercises look interesting to you.  Others will be able to see once you've
submitted a completed exercise, and then can give feedback.  They have tracks for Perl5,
Bash, and Python (among many, MANY others).


### Codewars

[https://www.codewars.com/](https://www.codewars.com/)

This is a little more structured than the others, in that they'll suggest new exercises
("katas").  Once you've completed one, there will be suggestions for what to tackle next.
You can jump to other exercises if you want, filter by language or difficulty, etc.
There's also some comment functionality as well, but not quite in the same was as on
Exercism.  Despite the rather shorter blurb here, I do quite like this site.  :)  They
have kata for Python and Shell, but not Perl.


### HackerRank

[https://www.hackerrank.com/](https://www.hackerrank.com/)

This one is actually designed to not just help you improve your coding skills, but also
land a job.  They are specifically geared towards interview preparation and there are a
number of companies that run some of the technical portions of their interviews through
HackerRank.  There are still badges, ranks, points, etc., and you don't have to be
applying for a job in order to use them.  But if you ever apply to a company that uses
their site, you can allow them to see your profile (completed exercises, for instance) as
part of the process, and that can give you an advantage over someone who doesn't use the
site.  It can be a little harder to navigate than the other two, but they also have a lot
of contests going on at any given time, which is another way to get yourself noticed by
potential employers.  They also have Python and Shell, but not Perl.

### Et Cetera...

And finally, to get a little more "meta", here's an article that lists some good
coding practice sites:

[https://medium.com/coderbyte/the-10-best-coding-challenge-websites-for-2018-12b57645b654](https://medium.com/coderbyte/the-10-best-coding-challenge-websites-for-2018-12b57645b654)

FWIW, HackerRank and Codewars are both listed there.  `:)`

## Koans

Lastly, here are the Python and Perl [koans](#footnotes):

* [https://github.com/gregmalcolm/python\_koans](https://github.com/gregmalcolm/python_koans)
* [https://github.com/forcedotcom/PerlKoans](https://github.com/forcedotcom/PerlKoans)

Both of these koans are modeled after what I believe was the original "koans" package,
[Ruby koans](http://rubykoans.com/).  

For each of those you will need to clone their respective git repos and run it from your
shell locally.  If you don't run Linux natively on your own system, I would recommend
pulling down Virtualbox or VMWare Player on your Windoze system and spinning up an Ubuntu
or Fedora instance for these.  Not that you can't use Windows, but if you are going to be
working mostly on the \*nix side anyway, it would be better to learn there.  There are
idiosyncrasies on the M$ side that you probably don't want to have to un-learn when moving
back.

### How to Use the Koans

Essentially, this is test driven development (TDD).  What you are given is a bunch of
tests which are failing.  When you run the tests, they'll fail at the first error they
find.  So you need to edit the appropriate file and fix that issue.  Then run them again,
and they'll fail on the next one.  Fix that.  And so on.

Philosophically, the TDD approach is "red, green, refactor".  What that means is that,
when you are developing something, write the tests first.  When you run your test, before
you've written the code that it's meant to test, clearly, it fails (the test is "red").
Now you need to write the code that will make it succeed (go "green").  Once you have
developed the basic functionality needed, then you go back and refactor - see if there's a
more efficient, clearer, or more robust way to solve the problem.

When you apply that to these koans, it's very similar.  You start with broken code
("red").  You edit the broken file and fix whatever isn't working, so the test passes
("green").  At this point, it's really easy to just move on and do the next one and the
next one, and so on.  To get the most out of them, though, it's best to go **back** into
the file you just fixed and try to understand what's really going on there.  Some problems
are "deeper" than others, of course, but it helps to really try to grok whatever bit of
the language is involved with the particular koan each time.

So that's how you're supposed to think about it, but what are you really supposed to
**do**?

The quick version, taking the [Python](#footnotes) koans as an example, you would cd into either
the 'python2' or 'python3' dir, and then just run 'run.sh'.

The longer version is "RTFM".  `:)`  Each of the koans comes with a README that tells you
how to use them, which is highly recommended reading.


## Footnotes

**1** "Koans" are named for the paradoxical statements Zen Buddhists use for contemplation
and enlightenment, such as "What is the sound of one hand clapping?"

**2** As an aside, if you're going to learn Python, learn Python 3.  It's good to learn
about Python 2, because there's a lot of legacy code out there, but Python 2 is EOL as of 2020.
The Python community is STRONGLY in favor of all new code being in Python 3.

