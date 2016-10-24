# Typesetting Tableau Trees

## Describe your project in five words

## Audience
_Who are you helping, with your language? What is that person's
experience like now? How would their experience be better if you could help 
them?_

My language is for people who want to draw tableau trees, more specifically for students in CS 81.
CS 81 requires trees that are rendered digitally and the recommended method for drawing the trees is to use Google Sheets.
So students have to create text-boxes and arrows and drag them around to draw tree, which is quite cumbersome.
A common alternative is to use LaTeX to typeset a tree.
However, not everyone knows how to use LaTeX because the syntax is a bit challenging (and requires a lot of boilerplate). 
Even if someone uses LaTeX for their other classes, they may not be familiar with the LaTeX packages for typesetting trees.

## Why a language?
_Why is a **DSL** appropriate for your user(s)? How does it address the need?_

Logicians already use a DSL, LaTeX, for this purpose.
A language has a steeper learning curve compared to using Google Sheets, but once someone has learned a language, it should be much easier to use the language than drawing a diagram.
It seems like another DSL, with a simpler interface compared to LaTeX can improve a user's experience.

## Why you?
_What excites you about this idea? How did you come up with it?_

I'm taking CS 81 and I really dislike drawing trees on Google Sheets.
I use LaTeX for my other classes, so my initial thought was to use it for CS 81 as well.
I tried using several LaTeX packages to draw tableaux trees but my experience has been frustrating thus far.
I TeX-ed tableau trees for one of my assignments but it required a lot of trial and error as well as reading a _lot_ of samples of various tree structures. 
I would be really happy if there was an easier way for me to draw trees for my homework.

## Interface (syntax)
_What kinds of things can the user say in your language. How, generally, do they
say it? **Be as specific as possible.** You don't need to design syntax; but you
should be more specific than "The user describes properties of unicorns.", e.g.,
by describing which unicorn properties (horn color, tattoo, etc.) are most 
important to users and what kinds of values those properties might have._ 

Like LaTeX the programmer would write text to a file. 
The programmer types out what would be on each line of the tableau tree,
using special characters for logic symbols.
The programmer should also have a way to draw a check mark at the end of each line of the tree.
Tableau trees are binary trees so the programmer can also specify if the tree branches off.

One possible syntax is
```
(A \or B) \and C \check
C
A \or B
  A
    branch1
    branch2
  B
```
to draw

![tree](/images/tree.png)

which is similar to how qtree, a LaTeX package for trees, structures code but this doesn't require entering math mode using \$.
Anthony mentioned in his critique that the backslash may not be necessary in this language.
This would restrict programmers from having variable names like 'or' and 'and', but then again those would be bad variable names in a logic proof.

## Operation (semantics)
_What might happen when a program runs? Is there a computational model that
corresponds with your domain? How does a program interact with the
user? What kinds of semantic (i.e., non-syntax) errors might occur, and how 
might they be communicated to the user?_

The file is read an compiled.
A program would render a tree based on the text file and output an image file.
This fits the data-entry model.
Drawing a tree is a sub-problem of drawing a graph, which was the given example for the data-entry model.

Syntax errors, such as branching in 3 directions, should be reported after compilation, before the tree is drawn.
This could be reported by writing to an error stream or file.

Semantic errors would result in a malformed tree.
I'm not sure how this would be reported to the user other than by having an image file of a weird tree.

## Expressiveness
_What should be easy to do in this language? What should be possible, but
difficult? What should be impossible or very difficult?_

It should be easy to draw any binary tree with logic symbols.

It should be possible, but maybe not necessarily easy, to draw trees with text that contains symbols other than logic symbols.
Maybe Unicode symbols.
It should be possible to use different kinds of logic symbols.
For example, not can be represented with ¬ or !, the user should be able to choose which set of symbols they want to use.

It should be impossible to draw trees that are not binary.
It should also be impossible to draw a graph with a cycle.

## Related work
_Are there any other DSLs in this domain? If not, describe how you know there
aren't and conjecture why not. If so, describe them and provide links. How well 
do they address the need? Are there any particularly admirable qualities of the
language? Are there parts of the language you think could be improved?_

There are LaTeX packages that logicians use for drawing trees.
[Here](http://www.logicmatters.net/latex-for-logicians/trees/) are some examples.
However, installing LaTeX is not very easy as the common TeX distributions are quite large.
LaTeX also has a steep learning curve, which may not be worth it for someone who only needs to draw logic trees.

[prooftrees](http://ctan.org/pkg/prooftrees) seems to be the most comprehensive package for drawing trees.
There is a lot of customization available, as seen on page 5 of their documentation. 
It lets programmers pick their set of logic symbols, and preferred format, and even allows color coding. 
It also lets the programmer thoroughly annotate their trees.
The drawback to this is that it is more customization than the typical CS 81 student needs.
This clutters up the syntax for someone who is unfamiliar with it.

[Qtree](http://www.ling.upenn.edu/advice/latex/qtree/) is what I have been using for my CS 81 homework.
However, as mentioned before, this is designed for linguists.
Qtree's documentation states that
> The front end of _qtree_ reads a tree description written in the familiar (to linguists) bracket notation. 
However, I found this bracket notation confusing.
Furthermore, this package requires a lot of work-around to get it to draw tableau trees.
[Here](https://github.com/cpence/latex-tableaux) is a page that explains how to wrangle qtree to make it work for tableau trees.
Tree packages generally expect each node to be a single line, which is not the case for tableau trees.
It would also be much nicer if users don't have to exit and enter math mode in order to typeset the tree.

## Suitability
_What percentage of your time do you think will be spent directly engaging in
the **language** aspects of this project (e.g., making language design
decisions), as opposed to "systems" aspects of the project (e.g., implementing a
complicated semantics that doesn't require a lot of language design)?_

If I decide to leverage an existing tree typesetting tool, I estimate that 70% of my time would be spent engaging in the language aspect.
I would need to learn how to interact with the tool, but once I figure that out I can focus on designing the interface to the tool.

If I decide to write the program myself, as I thought I would in the project-ideas assignment, I would need to spend much more time on semantics.

Initially, I thought that the ideal syntax was very obvious and straightforward.
But from Anthony's critiques, I think there are still more design decisions to consider.
Such as designating a character to invoke logic symbols.

Graphviz is an example for an alternative syntax for drawing graphs, and thus trees.
So there may be a better syntax for trees that I have not considered.

## Scope
_How big an idea is this? How ambitious is this project?_

The project has a very specific purpose, for a very specific user base.
So I think the project is has a narrow enough scope.
I don't think it's very ambitious.

## Challenges and opportunities
_Why is this a good project? What are some challenges you expect to face? How
might you overcome them? What are some warning signs that the project has gotten
off track, and how will you get the project back on track if needed?_

This is a good project because I have my own motivation for completing it.
The project probably won't be completed in time for me to use it in class, but I think having to use the tools I currently have in class will keep me motivated.

I expect some challenge in interfacing with a tree typesetting package, as I'm already having some trouble with them right now.
Using a package as a host language is probably more challenging than using it to draw a specific tree.
I hope to avoid this as much as possible by researching a lot of tools before settling on a host language.
I should avoid splitting my time between two (or more) host languages, which would be a sign that the project may have gotten off track.
I would get back on track by choosing one host language and sticking with it as much as possible.
