# Directory Regex

## Describe your project in five words

Finding files with tree regular-expressions

## Audience
_Who are you helping, with your language? What is that person's
experience like now? How would their experience be better if you could help
them?_

I am helping anyone who wants to use more general regular expressions to find or
perform operations on files.  Currently, there exist tools like `grep` and
`find` that can be paired with regular expression to find files.  In addition,
`find` has an `-exec` option that allows the user to do things like copy or move
files that it matches.  However, these tools have their limitations.  As far as
I know, there is no way to match regular expression involving the tree
structure.  For example you wouldn't be able to find files with the extension
`.cpp` that is a sibling of a file named `foo`.  In addition, you wouldn't be
able to match folders that contain a file `piconot.txt`.  With a regular
expression for matching files, people could locate generic patterns of files
more easily and perform operations on them.

## Why a language?
_Why is a **DSL** appropriate for your user(s)? How does it address the need?_

This project seems similar to Regex, but with more options.  Since Regex is a
DSL, I would imagine that this could also be implemented as one.  It addresses
the need because it hopefully allows users to express more complicated scripts
and commands more succinctly.

## Why you?
_What excites you about this idea? How did you come up with it?_

I like regular expressions, and would like to become more experienced with them.
Also, a two summers ago I spent a long time generating regular expressions for
parsed trees using Stanford's NLP tools called Tregex and Tsurgeon.  These tools
make the process of finding and replacing patterns in trees much more easy,
and I wonder if this idea could extend to the tree of file directory system.
Also, as far as I know, no such tools exist.

## Interface (syntax)
_What kinds of things can the user say in your language. How, generally, do they
say it? **Be as specific as possible.** You don't need to design syntax; but you
should be more specific than "The user describes properties of unicorns.", e.g.,
by describing which unicorn properties (horn color, tattoo, etc.) are most
important to users and what kinds of values those properties might have._

I hope this would be a command-line tool, where the user defines a pattern
similar to the way they would define one with regular expressions.  However,
there would be different connectors describing relationships between
directories.  At the minimum there we would need ways of expressing direct
sibling, child, parent, descendant, and ancestor (optionally with the number of
generations).  Then, for each node, you would use a regular expression to
match the name you wanted.  Additionally, you would be able to capture and name
values, perhaps with parentheses.  If time permits, I would like to add the
ability to perform operations on those matches.

Tregex uses a syntax like `S < (NP $ VP)` to match a clause that is the direct
parent of a noun phrase and a verb phrase.  I would imagine something similar,
which includes capturing variables.  Maybe something like
`project* < ((*)=(filename).cpp $ (filename).hpp )`
would match a folder that starts with "project" that contains a .cpp and .hpp
file of the same name.  In addition, the filename would be returned.

In addition, I would like to add the option to search within a readable file.
This could be indicated with a special sort of parent symbol, maybe `<@`

## Operation (semantics)
_What might happen when a program runs? Is there a computational model that
corresponds with your domain? How does a program interact with the
user? What kinds of semantic (i.e., non-syntax) errors might occur, and how
might they be communicated to the user?_

When a program runs, it should search through your file directory and  at least
return all the matches of the root node and the captured variables.  Ideally, it
would also perform operations that the user specifies on these named variables,
like "copy" or "rename".  Possible errors include ill-formed regular
expressions, which could easily be communicated by an error message.  Also, a
user could mistakenly enter a wrong pattern that would delete several files.
This could be prevented if the program warns the user before moving/deleting
files.

## Expressiveness
_What should be easy to do in this language? What should be possible, but
difficult? What should be impossible or very difficult?_

It should be easy to match files and folders given very complicated structures.
It should also be easy to move these files around easily.  Moreover, it should
be easy to match files and folders by their names and the contents of the files.
It should be possible to do complicated operations apart from finding and
replacing that require shell commands.  It should be impossible to do pretty
much everything else, like writing files, or creating a Turing Machine.

## Related work
_Are there any other DSLs in this domain? If not, describe how you know there
aren't and conjecture why not. If so, describe them and provide links. How well
do they address the need? Are there any particularly admirable qualities of the
language? Are there parts of the language you think could be improved?_

Stanford's Natural Language Processing Team created [Tregex](http://nlp.stanford.edu/software/tregex.shtml) to match patterns
in parsed trees.  This is in a very similar domain, but the use-cases would be
somewhat different.  As far as I know, Tregex only works for trees parsed using
Stanford's natural language parser, and would not help for locating files.
However, I do plan on taking inspiration from their syntax.  At a first glance,
some of the syntax seems pretty hard to understand, for example,

``` @SBAR < /^WH.*-([0-9]+)$/#1%index << (__=empty < (/^-NONE-/ < /^\*T\*-([0-9]+)$/#1%index)) ```

 which apparently will "match only such that the WH-
node under the SBAR is coindexed with the trace node that gets the name empty".
I'm not sure if I could make a syntax could make this more understandable,
since it seems like a somewhat complicated expression.  However, I could make it
more specific to file searching, so, for example, you wouldn't care if something
were the left-sibling or a direct right-sibling.

## Suitability
_What percentage of your time do you think will be spent directly engaging in
the **language** aspects of this project (e.g., making language design
decisions), as opposed to "systems" aspects of the project (e.g., implementing a
complicated semantics that doesn't require a lot of language design)?_

This DSL seems more heavy on the systems side than the language side.  It took
us about a week to implement Regex as an internal, and including the tree
relations would probably be different.  The semantics could become complicated,
especially for tasks like opening files, identifying matches in reasonable
amounts of time, and performing operations with those matches.

## Scope
_How big an idea is this? How ambitious is this project?_

Just for identifying files and folders, I feel like this DSL is within the scope
of this class.  Hopefully, I could add the ability to read files and to perform
operations on the matches, but that might be on the more ambitious side.

## Challenges and opportunities
_Why is this a good project? What are some challenges you expect to face? How
might you overcome them? What are some warning signs that the project has gotten
off track, and how will you get the project back on track if needed?_

I think this is a good project because it fills a need that I found no existing
tools for.  You could argue that it is not a very big need, since you don't
often want to search for files by their surrounding directory structure -- that
is an issue I am still contemplating.  Some challenges I imagine are navigating
through the directories in an efficient way, and implementing the actual
matching algorithm for the trees.  One indication that this project has gone
off-track is if the algorithm is too slow to be feasible, or if the language
becomes so complicated that it is unreadable unless you are very familiar with
it.  Since this language wouldn't be used especially often, I would hope that it
would be relatively easy to learn.  Therefore, if I find that the syntax is too
convoluted, I can hopefully keep the same internal representation but make the
syntax more intuitive.  If I find that the search is too slow, I can perhaps
exclude looking inside of files, or even the "descendant" option.

