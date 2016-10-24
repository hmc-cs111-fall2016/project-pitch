# EconGraph

## Describe your project in five words
Creating graphs for economics notes

## Audience
_Who are you helping, with your language? What is that person's
experience like now? How would their experience be better if you could help 
them?_
I am helping students taking economics courses with my DSL. Currently, the 
experience of students in economics classes is less than ideal. Note-taking is
done by hand, with both written words and graphs being taken note of, which is
done simultaneously with listening to lectures. This doesn't sound like a
terrible experience; however, I believe it can be vastly improved.  Much of the
frustration is rooted in the fact that lecture slides often contain major points
or leading questions of a lecture, but don't answer these questions. Rather, the
answers or explanations are given verbally. It goes without saying that 
assessments revolve around the answers to the major questions and therefore the
things _said_ in class. As a result, it's often important to be able to 
transcribe the things Professors say in class for several minutes at a time. 

Transcribing is much easier on a computer.  Typing removes the pain point of 
illegible handwriting when trying to keep up with the Professor's lecture, and
is simply faster.  However, using a computer doesn't allow for easy switching 
between typing and creating graphs. In fact, creating graphs in general is
difficult on a computer.  

Thus, if I could help, I would allow students to type notes to transcribe things
said in class, but also easily create graphs in the same place.  This means that
by typing some commands, we could create any graph that a student would come 
accross in their economics classes.  Of course, some would be easier to create
than others (simple supply-demand graphs, production possibilities curves, etc.),
but ideally all types of economics graphs would be possible to generate. 


## Why a language?
_Why is a **DSL** appropriate for your user(s)? How does it address the need?_
A DSL is appropriate for our users because of several reasons.  Most importantly,
I believe that it's appropriate because note-taking involves language. Thus, if 
we want to improve note-taking, we should do it with some form of language.  We
need to create some way of creating graphs without interfering too much with
the flow of taking notes in a human language, so a language versus an app 
makes a lot of sense in this case.

Furthermore, since we want to improve note taking by moving it from hand-written
to on a computer, it requires some sort of programming language. However, since
the problem we're trying to solve, easily creating graphs in the same place you
take notes, is a very specific domain, we should require as little overhead as
possible for users to learn the language.  Thus, a DSL makes more sense than a 
general programming language for our users.  A DSL also makes more sense than
general graphing libraries that may be available in different languages because
it'll be much more focused on a specific domain and therefore should be very
easy to learn, in addition to being able to be run in a text editor or note
taking app of some sort.

## Why you?
_What excites you about this idea? How did you come up with it?_
I am excited about this idea because I would be able to use it myself. I've had
this issue many times where I find myself lost in class because handwriting is
too slow and requires too much focus while listening to a lecture.

Furthermore, I'm excited because I think this is a project that can be very
easily extensible. While the focus will be on generating economics graphs, I 
can see the language being extended to allow all kinds of graphs to be generated
in place.  It was brought up in a class discussion that a math class could
benefit from something like this, and it would be really cool to add more 
functionality based on the needs of users.

I came up with this when I was in my economics of poverty class this semester.
The Professor's slides really annoy me because they contain major questions,
such as "Did welfare reform really work?", but don't even have a trace of what
the "answer" or ideas related to that question were. Thus, I'd find myself with
notes that are half baked because I've tried to take specific notes and quotes
that the Professor said, but then got left behind and missed things while I was
writing.  I know I never actually have this problem when I type, because I can 
type almost as fast as the professor speaks. Then, I thought about why I was
handwriting at all: the few times that we're asked to take copy down a graph. 
Though these moments in the poverty class are rare, other economics classes have
put is in the habit of handwriting notes. I think that there's a lot lost from
handwriting notes in this context (despite many studies showing handwriting is 
superior for memory retention etc.), so I thought this would be something
solvable by a DSL.


## Interface (syntax)
_What kinds of things can the user say in your language. How, generally, do they
say it? **Be as specific as possible.** You don't need to design syntax; but you
should be more specific than "The user describes properties of unicorns.", e.g.,
by describing which unicorn properties (horn color, tattoo, etc.) are most 
important to users and what kinds of values those properties might have._ 

The user should be able to describe elements of a specific graph that they want.
They will be able to generate very commonly used elements of economics graphs, such
as supply and demand curves, equilibrium point, production possibilities curves,
and so on, with a single function call. Then, they would be able to customize
each of these built-in elements if needed, with things such as slope and
intercepts being passed in as optional parameters. 

In addition, there would be other properties they can generate such as axes
values, titles, axes intersection points, and so on.  I could imagine further, 
more specific customizations being possible to give the DSL an almost secondary
purpose as a graphing language; however, we'd want to focus and make it as easy
as possible for users to create graphs for economics specifically first.


## Operation (semantics)
_What might happen when a program runs? Is there a computational model that
corresponds with your domain? How does a program interact with the
user? What kinds of semantic (i.e., non-syntax) errors might occur, and how 
might they be communicated to the user?_
A program would run when a document is saved. When this happens, we'd expect the 
DSL code to be replaced with an image of the graph that was specified. 

This DSL's computational model is data interpretation, since it reads the data 
the user provides and generates some image based on that.  

The DSL would be run in some notetaking app that is extensible, such as RStudio 
or Jupiter notebook.  I would have to look further into how the program would
communicate with the user, but I imagine there is something equivalent to a 
console in a text editor that would be able to display error messages and other
neccesary information.     

Possible errors include calling functions that don't exist.  For example,
we may not support the Engel curve for whatever reason, and if a student called
EngelCurve(), it would be an error. This would be communicated through the
console. 

Semantic errors are more difficult to think of. I would imagine semantic errors
could include sepcifying a slope that does not match what the user intended, or
calling the wrong type of curve.  These would be communicated by the image
generated, as it wouldn't match what the user intended.

## Expressiveness
_What should be easy to do in this language? What should be possible, but
difficult? What should be impossible or very difficult?_
It should be very easy to generate common economic graphs. Generating a standard
supply-demand graph, production possibilities curve, cobb-douglas graph, should 
be possible to do in under 5 lines of code.  It should be possible, but difficult
to create graphs that are not common economics graphs. By manipulating slope,
intercepts, creating appropriate axes and titles, we could probably create some
graphs for other purposes, thought it'd take considerably more effort to do.  It
should be impossible to do algorithms homework, build websites, and do most other
things done in general purpose programming languages with this DSL.

## Related work
_Are there any other DSLs in this domain? If not, describe how you know there
aren't and conjecture why not. If so, describe them and provide links. How well 
do they address the need? Are there any particularly admirable qualities of the
language? Are there parts of the language you think could be improved?_

There are no other DSLs in this domain that I could find. I was able to find
some apps that addressed the need for a simple graph maker, such as 
[Economics Graph Maker](https://www.economicsgraphmaker.com/) and [GraphTool](http://harmon.uconn.edu/GraphTool/). I looked into widgets and extensions for note
taking apps, specifically Jupyter notebook and Microsoft OneNote, and wasn't able
to find any DSL.  These seem like the likely places that I'd find a DSL that
integrates with note-taking, so I am quite sure there aren't any out there.
I don't think there's been one created because extensible note-taking apps seem
to be relatively new.  Furthermore, this is such a specific domain, and I think
most people are focused on creating extensions that can appeal to a wide variety
of people.  I also think creating apps to solve problems is more common than
creating a language, which is why we can find apps but not a DSL to solve this
problem. 

## Suitability
_What percentage of your time do you think will be spent directly engaging in
the **language** aspects of this project (e.g., making language design
decisions), as opposed to "systems" aspects of the project (e.g., implementing a
complicated semantics that doesn't require a lot of language design)?_

This is a difficult one to gauge.  Because we're trying to make it as easy as 
possible for a user to build economics graphs, much of the essential functionality
could be solved through individual function calls like`SupplyCurve()`.  However, 
deciding on how to best design customization and transformations on graphs could
prove a significant challenge.  Balancing ease and speed with users' freedom to
express the graphs they want could require a considerable  amount of attention 
and time.

In terms of systems aspects of the project, the DSL needs to run in some 
note-taking application.  Thus, my concern with systems programming lies in 
whether these applications' APIs will provide the functionality that I need and
are easy to work with. If I can find a notebook app that is extensible and 
provides enough access to functionality such that building in a DSL is trivial,
I will have very litle time spent on systems aspects of the project.  However,
I am not sure whether that will be the case, so it really depends on the apps
that I find.        

## Scope
_How big an idea is this? How ambitious is this project?_
I think this is a pretty "big" idea.  I think that if I am successfully able to
implement this DSL, it really can provide an alternative way to take notes on
the computer for more quantitative subjects.  While laptops and students taking
notes with laptops are ubiquitous in schools, I don't think we can say that 
society has found an effective way to improve the classroom experience in lecture
based classes through computers other than greater access to powerpoint slides.
I think the student experience could be greatly improved by this DSL. 

If I am able to navigate the environment that the DSL will run in, I don't think
it is overly ambitious to complete this project.  If working with the notebook
API to parse code and create visualizations is straightforward, I don't see a
reason why I couldn't complete this project.  That being said, requiring an
outside application and therefore outside API as a major part of my project puts
me out of control for a big chunk of my project. I won't really know how that 
process will be, so finding an application that allows me to focus on language
design rather than "systems" programming will be crucial and determine how
ambitious this project really is. 

## Challenges and opportunities
_Why is this a good project? What are some challenges you expect to face? How
might you overcome them? What are some warning signs that the project has gotten
off track, and how will you get the project back on track if needed?_

This is a good project because it solves a real problem, and one that should be
solved by a language rather than an app.  Hopefully if this project is 
successful, it can provide an example of a clear use case where a DSL is superior 
to an app.  

A major challenge I expect to face is finding the best note-taking app to have
my DSL run in.  Given that I need an outside app to make my DSL work, I expect
that I'll run into some obstacles in implementing my DSL in the context of
another app that I don't get to control.  I have already started my research
on this challenge, and starting early in figuring this out is the best plan of
action to overcome this. 

Another challenge will be figuring out how best to design the language.  I have
a strong bias towards a syntax I'd came up with in the `project-ideas` assignment,
which would not provide a lot of opportunity for design aspects of the project.
To solve this, I just need to put a lot more thought and do more surveying to see
what actually is the preferred design among potential users rather than just 
jumping to my own conclusions. 

I think if I am spending too much time wrestling with the API of the 
external note-taking application, I would be off-track.  This would make it more
of a systems project than a design project, so I would have to reconsider my 
idea, or think of an alternative environment to implement it for. 