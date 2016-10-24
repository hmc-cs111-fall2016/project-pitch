# Line Animate

## Describe your project in five words
2D line animations using code

## Audience
_Who are you helping, with your language? What is that person's
experience like now? How would their experience be better if you could help 
them?_

This language helps people who want to create 2D line animations in a novel way. 
Digital animation can initially be difficult to learn and often requires knowledge 
of digital illustration platforms as well as some programming skills. Though there 
already exists some good programming languages for animation, such as Processing, 
the domain of these languages is fairly broad and can still be intimidating for those 
who have never programmed before. The limited expressiveness of my language can be 
very appealing to those who don’t want to create digital art, in the form of 2d 
animations, but don’t want to invest too much time. In particular, I think this 
language can be a nice introduction to coding for those who have never programmed 
before because of its simple syntax and limited vocabulary. 

## Why a language?
_Why is a **DSL** appropriate for your user(s)? How does it address the need?_

A DSL is a nice tool for the users because it allows them to create a potentially 
complex and interesting output (2D animations) using a small set of expressions. It 
also allows the user to quickly modify the animations they created by simply modifying 
a line of code. Though animations can be done in a variety of ways, a DSL seems like 
one of the most accessible animation tools, especially since this DSL will be comprised 
of simple words/phrases and numbers. It also deals with a more limited domain of line 
animations using a 2D coordinate system, and it will be interesting to see the creative 
animations that people can make within the constraints of this domain. 

## Why you?
_What excites you about this idea? How did you come up with it?_

I’m excited about this idea because I’ve always wanted to learn how to create animations 
but am hesitant because of how difficult and time-consuming it might be. For the first 
round of project brainstorming, I had a very vague idea of wanting to create DSL for 
animations. When I found out about languages like Processing I thought it might be too 
broad of a domain that already has good DSL’s in place. However, after talking to Prof. 
Ben (and also working on the Piconot assignment), I came up with an idea for creating 
animations with a continuous line. For example, this [video](https://vimeo.com/28416351) is what I sort of envisioned 
as an output for this DSL. However, I’m thinking that this 
DSL will be limited to only straight lines.

## Interface (syntax)
_What kinds of things can the user say in your language. How, generally, do they
say it? **Be as specific as possible.** You don't need to design syntax; but you
should be more specific than "The user describes properties of unicorns.", e.g.,
by describing which unicorn properties (horn color, tattoo, etc.) are most 
important to users and what kinds of values those properties might have._ 

The user will be able to define different rules that specify the coordinate where a 
line starts, the direction it travels towards, and the distance it travels. Optional 
things that the user can define is the speed of the line, the weight of the line, the
color of the line, and whether or not the line will disappear as it travels (otherwise 
default values will be set). Here is an example of the code I am envisioning:

```// Creates two small spirals at the same time
Start (50, 50) 
Right: 10
Down: 10
Left: 15
Up: 15
Right: 20
Down: 20
Left: 25
Up: 25

Start (100, 50)
Right: 10
Down: 10
Left: 15
Up: 15
Right: 20
Down: 20
Left: 25
Up: 25
```

But I also want the user to be able to store and reuse a set of rules, so the code could be rewritten as follows:

```// Creates two small spirals
Rule spiralRule = 
{
	Right: 10
	Down: 10
	Left: 15
	Up: 15
	Right: 20
	Down: 20
	Left: 25
	Up: 25
}

Start (50, 50)
Do spiralRule
	
Start (100, 50)
Do spiralRule
```

Finally, here is an example of the same code with the including values of speed, weight, color, and disappearance.

```// Creates one fleeting red spiral and one blue spiral
Rule spiralRule = 
{
	Right: 10
	Down: 10
	Left: 15
	Up: 15
	Right: 20
	Down: 20
	Left: 25
	Up: 25
}

Speed(20)
Weight(50)
Color(red)
Disappearance(true)

Start (50, 50)
Do spiralRule

Speed(20)
Weight(50)
Color(blue)
	
Start (100, 50)
Do spiralRule
```

## Operation (semantics)
_What might happen when a program runs? Is there a computational model that
corresponds with your domain? How does a program interact with the
user? What kinds of semantic (i.e., non-syntax) errors might occur, and how 
might they be communicated to the user?_

This domain corresponds with a data interpretation model, since the user is basically 
defining a set of rules results in the corresponding 2D line animation. More specifically, 
it can also be seen as state interpretation because the user is defining the state of a 
line or multiple lines and where they should travel next. When the program runs, the rules 
will be read in line by line and the appropriate line/rectangle objects will be created. 
A standalone GUI application will pop up that shows the 2D animation produced by their 
rules. As the user is writing their code, they can intermittently run the program to have 
a sense of what their rules are producing. 

One semantic error that could occur is the line being out of boundary. In this case, the 
user should be notified with an error message that says, “Out of boundary!”. Additionally, 
the user may define the line with a speed that is too fast or weight that is to large, in 
which case they should be notified with a message like, “Invalid speed: must be between 1 and 
100”. The user may also forget to defining a starting coordinate and be notified with “Please 
define starting coordinate!”.

## Expressiveness
_What should be easy to do in this language? What should be possible, but
difficult? What should be impossible or very difficult?_

It should be easy to create 2D line animations in this language! Specifically, it should
be fairly easy to create multiples of a specific animation, and it should be easy to create 
animations that have a degree of symmetry. However, since the lines are limited to straight 
lines, it could be difficult to create more organic forms or 3D-appearing forms It could also 
be difficult to create a lot of text using the lines (although if the user defined a rule for 
each letter, it could be a reasonable task). Finally, it should be impossible to create animations
using something other than lines! 

## Related work
_Are there any other DSLs in this domain? If not, describe how you know there
aren't and conjecture why not. If so, describe them and provide links. How well 
do they address the need? Are there any particularly admirable qualities of the
language? Are there parts of the language you think could be improved?_

As I mentioned in my last project write-up, [Processing](https://processing.org/) is a DSL that is similar to the type 
of language I want to create. It is a language for "learning how to code within the context of 
the visual arts", and it allows the user to create still digital art as well as animated digital 
art. There are many libraries that extend the language, showing its extensibility and success as 
a readable and writable language. I actually think this DSL addresses the desire to create art and 
animation very effectively, and I wish I had known more about this before! I suppose a drawback of 
the language is that it has such a wide range of features that it might require some investment of 
time to become proficient with the language, and it is not necessarily the most intuitive for those 
who have never programmed before.

The [CSS3 Animations](http://www.w3schools.com/css/css3_animations.asp) library “allows animations of most HTML elements.” It is less expressive than Processing in the sense that it can only be used to create really basic animations or animate existing elements. I think a drawback of this is that it also requires knowledge of HTML and may be intimidating for people without programming experience. However, the syntax is pretty readable and I could see how I can use elements of it in my own DSL.

Finally, there is a feature in Powerpoint that allows for [line animations](https://www.screenr.com/6Rg), and if we’re playing 
the “Is this a DSL?” game, I definitely think this would count as a DSL. Animations in powerpoint 
are really simple to use, and they allow people without programming knowledge to add animations in
their presentations. This is an example of a 2D line animation that was created in Powerpoint!

## Suitability
_What percentage of your time do you think will be spent directly engaging in
the **language** aspects of this project (e.g., making language design
decisions), as opposed to "systems" aspects of the project (e.g., implementing a
complicated semantics that doesn't require a lot of language design)?_

I’d say 70% of the time will be spent on engaging in the language aspects. A lot of decisions 
will need to be made on how much to limit the expressiveness of the language, because there are 
an endless number of features that could be made available to the user. I think the challenge will
be sticking to an even more specific domain within 2D line animations, so that the language will be 
super easy and enjoyable to use. The other 30% of the time will be spent on the “systems” aspect, and 
it will mostly be figuring out how to get the code translated to the GUI window where the animations 
will be displayed. I will need to figure out the limitations of the window size and how many animations
can simultaneously be executed.

## Scope
_How big an idea is this? How ambitious is this project?_

I plan to begin with implementing the only the bare bones features, which is allowing the user to define 
a rule that specifies the coordinate where a line starts, the direction it travels towards, and the distance
it travels. I envision this DSL being implemented as an external DSL in Scala, although I’d like to look more
into other possible host languages. I’d say that these features wouldn’t take too long to design and implement. 
However, I think the project will be ambitious in figuring out how to allow the user to organize the code and 
deciding which additional features will be allowed. Because I have very little experience in the domain of 
animations, I think it will also be a big task for me to become more familiar with languages and applications 
in the domain, which may help inform my own language design. Overall, I’d say it’s a big project yet feasible
to carry out throughout the rest of the semester.

## Challenges and opportunities
_Why is this a good project? What are some challenges you expect to face? How
might you overcome them? What are some warning signs that the project has gotten
off track, and how will you get the project back on track if needed?_

I think this is a good project because I have narrowed down the domain significantly from my original idea. 
I think it will be a challenge to stick to this more limited domain because there are many other cool animation
features that could be implemented, but may or may not contribute to the user’s experience of using this language.
Designing how the code can be organized is also a challenge that I foresee. I am not sure how much freedom I 
should give the user to organize their code, but I also don’t want to limit the organization too much, though this
would make for easier parsing. In addition, I’m thinking about implementing this language using Scala, but I am
definitely not confident in my Scala knowledge at this point. 

I’m hoping to address as many design challenges at the very beginning, so that I have a really clear idea of how 
to move forward with the implementation. I think I often get sidetracked by wanting to create the finished product 
as quickly as possible, and I neglect good design and coding practices along the way. So before I even begin coding, 
I want to have a very solid design for the language written out. I also hope review Scala basics and also learn some 
more features before beginning implementation, so I won’t get stuck as often during the implementation process. I 
might know that the project has gotten off track if I am focusing too much on figuring out Scala or getting stuck 
on semantic details, and if this happens, I may need to reevaluate the the size of the domain and limit it more if necessary.
