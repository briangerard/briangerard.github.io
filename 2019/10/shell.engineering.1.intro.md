# Shell Script Engineering - Introduction

## What Is This?

A lot of shell scripts I run across (and a few I've written, if I'm being honest) are
written in a fairly ad hoc manner.  They're just slightly better than running a collection
of commands by hand, from a "capital A" Automation perspective.  By that I mean that they
get the job done, but trying to debug, modify, or expand on them is fairly frustrating at
best.  I'm writing this series in the interest of improving the practice of shell
scripting by bringing some disciplines over from the realm of software engineering.

I also want to point out that I do not advocate following everything here all the time.
One of the benefits of scripting in the shell is being able to throw together a quick hack
and knock something out rapidly that would otherwise entail hours of mind numbing
drudgery.  Sometimes, that's really all you need: a one-off script that you're going to
run once and never use again.  For a case like that, trying to make sure you're wrapping
everything in a function, or enforcing a consistent naming convention, or even unit
testing your code is likely overkill and very closely akin to premature optimization (see
"root of all evil").

A quote from Larry Wall about Perl would apply equally well here: "A Perl script is
correct if it's halfway readable and it gets the job done before your boss fires you."
([http://ciscohouston.com/docs/docs/quotes/wall.html](one source), though it's also
paraphrased in the book [https://en.wikipedia.org/wiki/Programming_Perl](Programming
Perl), pp *xx*).  That is to say, I wouldn't advocate polishing your shell script to the
Nth degree if it's just a throwaway.  Just write it, run it, and move on to more
interesting things.

However, if you are writing a script that needs to stick around for a while, whether
that's a cronjob for your company's production servers, an installer that's shipped with a
product, or even your personal shell environment, then the practices I cover in this
series can help you.  Applying a little discipline around the way longer lived scripts are
written can make them more maintainable and understandable, and can also save you a lot of
stress when you inevitably need to modify them in the future.

## Who's It For?

I presume that the reader has *some* exposure to shell scripting, and primarily in
bash/sh.  You don't have to be an expert, and I'll include references to documentation and
whatnot for further reading where appropriate.  I focus on bash and Bourne shell (sh) here
because they are by far the most commonly used shells for scripting.  The Bourne shell (or
equivalent) is more or less ubiquitous throughout the Unix/Linux world, and bash is a
close second.  The Korn shell, though it has some useful features, is much rarer these
days.  And if you're trying to program using the C shell, well, I'm afraid there may be no
help for you anyway.  `;-)`  As for the newer shells (Zsh, Fish, etc.), they're simply not
common enough as yet.  If this series gets popular enough, I may dedicate some space to
them, but that's getting a bit ahead of ourselves at this point.

Enough with the preliminaries already - [shell.engineering.2.vars.and.fns.md](on with the
show!)
