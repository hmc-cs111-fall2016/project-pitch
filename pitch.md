# Glowsticking Notation

## Describe your project in five words

Creating notation for glowsticking choreography.


## Audience
_Who are you helping, with your language? What is that person's
experience like now? How would their experience be better if you could help 
them?_

Here is a short 
[video](https://www.youtube.com/watch?v=VDdSLuj3CiI#t=15s) of what glowsticking 
looks like. Glowsticking is a type of poi: a performance art often involving 
object manipulation, including glowsticks, fire balls, fire fans, fire batons, 
etc. 

I am helping people who want to describe various glowsticking tricks, which is 
difficult because there are so many factors that make up a trick: speed, the 
string's length, each hand's position and movement, how far the arm extends out, 
and how the torso is turning. 

Creating a DSL would make it easy to describe existing tricks and new tricks 
that can be broken down into simple motions.


## Why a language?
_Why is a **DSL** appropriate for your user(s)? How does it address the need?_

A language can help express my idea because it can combine small motions 
(building blocks) into complex tricks. That way, tricks can be described 
clearly, at least once you understand the language.

I was inspired by juggling notations (see related work). I believe this is a 
language because users can string small building blocks together to create a 
juggling motion. It isn't readily understandable to me, but for those who do 
understand the notation, they can see how juggling tricks are performed. I 
think a similar approach can be applied to glowsticking, though glowstick 
motions are more complicated than ball trajectories.


## Why you?
_What excites you about this idea? How did you come up with it?_

I love glowsticking because it looks super cool, but the only ways to learn 
tricks are through tutorial videos or in-person. There are no 3D simulations 
designed for glowsticking (as far as I know). Also, I personally find it 
hard to teach others because it is difficult to describe ("the glowstick moves 
like this while your hand does this... and your other hand does something 
else... uhh..."). 


## Interface (syntax)
_What kinds of things can the user say in your language. How, generally, do they
say it? **Be as specific as possible.** You don't need to design syntax; but you
should be more specific than "The user describes properties of unicorns.", e.g.,
by describing which unicorn properties (horn color, tattoo, etc.) are most 
important to users and what kinds of values those properties might have._ 

I don't know my exact syntax. But for the sake of simplicity, let us focus on 
"full circle" moves that do not touch the body, shorten string length, or 
involve string manipulation.

There are two main properties that distinguish one move from another:

1. Where the glowsticks are in relation to the body
	a. Plane
		i. Wall - perpendicular to front or back of body
		ii. Wheel - perpendicular to left or right of body
		iii. Floor - perpendicular to the floor
	b. Is the arm rotating (moving in circles), and if so, counterclockwise or clockwise?
	c. Is the glowstick moving counterclockwise or clockwise relative to the hand?
	d. Start and end position of the hand after one full 360° circle.
2. Where the glowsticks are in relation to each other
	a. This can be represented as offset angle phases, as many moves have both glowsticks doing the same motion but starting at different phase positions.

Ideally, with this information, we can build individual tricks based on these 
properties for a "full circle".


## Operation (semantics)
_What might happen when a program runs? Is there a computational model that
corresponds with your domain? How does a program interact with the
user? What kinds of semantic (i.e., non-syntax) errors might occur, and how 
might they be communicated to the user?_

When a program runs, I want to create tricks based on the properties of 
glowsticking motions. Perhaps this can be represented as a time sequence of 360° 
motions with different properties (see syntax). In the far future, the results 
of my DSL can be translated into an API (internal representation) that can be 
used with poi simulators (see related work). 

I think data interpretation is one possible computational model because we want 
to describe our input (as glowsticking tricks). This would be displayed through 
a user interface like a 2D/3D simulator.

Some errors might be the user not providing enough info for a single motion. 
This is a problem because I want the motions to have enough information to be 
unambiguous. In this case, I would have to display error messages that state 
exactly what information is missing.


## Expressiveness
_What should be easy to do in this language? What should be possible, but
difficult? What should be impossible or very difficult?_

It should be easy to describe physical movement of the hands, glowsticks, and 
body/torso. It should also be easy to string these notations together in a 
sequence.

You can attempt to simulate your physics homework, but there are better (more 
general) programs for that.

It should be impossible or very difficult to do my Algs homework, compute 
mathematical expressions, create computer programs (in the traditional sense), 
and make sounds.


## Related work
_Are there any other DSLs in this domain? If not, describe how you know there
aren't and conjecture why not. If so, describe them and provide links. How well 
do they address the need? Are there any particularly admirable qualities of the
language? Are there parts of the language you think could be improved?_

In my 
[free-2.md](https://github.com/tiffanyfong/project-ideas/blob/master/free-2.md), 
I listed two DSLs on juggling and dance notation, which are technically 
different domains from glowsticking. However, they are languages because you can 
compose simple motions to create routines.

I recently found some simulators for poi, which I consider the same domain as 
glowsticking. 

[Flower Simulator](http://www.rationalpeople.us/double.html) is a great tool for 
visualizing a specific move (flower) in 2D.

[VisualSpinner3D](http://www.spinmorepoi.com/theory/) 
looks promising, but it doesn't show on my computer :(. Critique group: does it 
work on your computer?

Both simulators are cool, but they are more on the systems side rather than the 
language side because they aren't very composable. You need to give a name for a 
trick instead of my idea: connecting motions to create a trick. Moreover, the 
tricks available are limited to what has already been premade/hard-coded. But 
they are good at animating individual moves.


## Suitability
_What percentage of your time do you think will be spent directly engaging in
the **language** aspects of this project (e.g., making language design
decisions), as opposed to "systems" aspects of the project (e.g., implementing a
complicated semantics that doesn't require a lot of language design)?_

As long as I focus on the composition of glowsticking moves, I will spend a lot 
of time on language design. My syntax isn't finalized, since there may be better 
ways to describe circular movements. So figuring out the syntax and semantics 
will take up a lot of time.

Ideally, I would try to connect my DSL to the poi simulators, which may involve 
lots of research on the systems. Then again, I'm also creating an internal 
representation for the poi simulators, so that's language design.


## Scope
_How big an idea is this? How ambitious is this project?_

I think describing glowsticking/poi moves is quite ambitious. It's not as simple 
as juggling or dance notation, which have simpler trajectories and lack complex 
object manipulation.

But after finding (open source) poi simulators, my goal is much clearer: using 
my DSL to translate simple motions into glowsticking moves. I think having this 
goal limits my scope in a good way so that I can focus on one simulator system.


## Challenges and opportunities
_Why is this a good project? What are some challenges you expect to face? How
might you overcome them? What are some warning signs that the project has gotten
off track, and how will you get the project back on track if needed?_

This is a good project because I can create a grammar for something that cannot 
be explained well currently. Also, I have access to poi simulators and their 
source code, so I can create internal representations that translate my DSL to 
functional input in the poi simulators.

Some challenges might include deciding which properties of circular motions are 
really important in describing glowsticking moves. In addition, working with the 
simulators might be challenging (I haven't looked at the source code yet).

I'm not sure how this project will go off track because it has a specific goal 
and domain. But I can see myself struggling with details of whatever host 
language I use (especially JavaScript, oh gosh). Actually, I might have trouble 
choosing one host language, so I will need to stick to my decision.
