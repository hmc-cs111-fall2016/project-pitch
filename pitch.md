# Twitch Plays Programming

## Describe your project in five words
Crowdsourcing videogame play via Twitch.

## Audience
_Who are you helping, with your language? What is that person's
experience like now? How would their experience be better if you could help 
them?_

Since Twitch Plays Pokemon began in 2014, there has been lots of interest in
creating similar "crowdplay" games. However, it is an area primarily done by
people willing to overcome the steep curve of learning how to interface with
emulators and Twitch's API. A DSL could help people who would have previously
been excluded from making a "Twitch Plays".

## Why a language?
_Why is a **DSL** appropriate for your user(s)? How does it address the need?_

A DSL is appropriate for multiple reasons. We are focusing on a specific domain,
listening and executing Twitch chat commands. In addition, we are attempting to
make that one domain extremely easy while allowing for everything else to be
hard or impossible. We also want to allow the user to express potentially very
complex compositions of commands, so the richness of a language is a big boost.

## Why you?
_What excites you about this idea? How did you come up with it?_

I was a big fan of the original Twitch Plays Pokemon and I was excited to see
other people continue the tradition, but no one did. I attribute this significantly
to the difficulty in creating such a project.

## Interface (syntax)
_What kinds of things can the user say in your language. How, generally, do they
say it? **Be as specific as possible.** You don't need to design syntax; but you
should be more specific than "The user describes properties of unicorns.", e.g.,
by describing which unicorn properties (horn color, tattoo, etc.) are most 
important to users and what kinds of values those properties might have._

The user would need to specify a couple of things. They would first need to specify
their channel as the program needs to know which chat to scrape. They should also
specify how often the game should execute its commands, e.g. every 10 votes or every
5 seconds. The user might also want to specify how votes are counted, e.g. simple
plurality or drawn from a hat. Finally, the user would need to specify what do when
a command is chosen, e.g. when we choose "!jump", the spacebar should be pressed. I
have ideas for other specifications, but these should be good for a minimum and I
can extend them later.

## Operation (semantics)
_What might happen when a program runs? Is there a computational model that
corresponds with your domain? How does a program interact with the
user? What kinds of semantic (i.e., non-syntax) errors might occur, and how 
might they be communicated to the user?_

I'm still not sure how my program should be evaluated. Right now, I'm leaning
towards a kind of meta programming, where the program is parsed, then used to build
a valid Python program. This way I can rely on Python's interpreter. This language
seems like it will use the "Production Rule" model heavily as it involves a lot of
specifying what a command is and what it should do. I'm sure I'll realize more as
the project goes on, but right now the only semantic error I can foresee is if the
user specified the same command multiple times. This can be reported to the user
on first parse, giving the user the chance to rename the command.

## Expressiveness
_What should be easy to do in this language? What should be possible, but
difficult? What should be impossible or very difficult?_

Specifying what commands can be said in chat to interact with the game and
how those commands should be processed should be very easy. Pretty much
anything else should be hard.

## Related work
_Are there any other DSLs in this domain? If not, describe how you know there
aren't and conjecture why not. If so, describe them and provide links. How well 
do they address the need? Are there any particularly admirable qualities of the
language? Are there parts of the language you think could be improved?_

There are plenty of Twitch bots that allow chat to interact with the stream, 
such as by suggesting what music should be played. A popular one is
[Moobot](http://twitch.moobot.tv/). There is also a lot of work by the
Tool Assisted Speedrun (TAS) community on scripting (
[usually in Lua](http://tasvideos.org/LuaScripting.html)) to interact
with games. However, as far as I know, there hasn't been work to bridge the
two.

## Suitability
_What percentage of your time do you think will be spent directly engaging in
the **language** aspects of this project (e.g., making language design
decisions), as opposed to "systems" aspects of the project (e.g., implementing a
complicated semantics that doesn't require a lot of language design)?_

I think time would be split more towards systems at the beginning, when making an
MVP. But once we progress past single command=single input, I have been extremely
conflicted about how to deal with any kind of global state or conditionals, which
can be very important in some games.

## Scope
_How big an idea is this? How ambitious is this project?_

This is a project that should be relatively easy to get something working, but new
features could be added and the language grow to whatever size I want.

## Challenges and opportunities
_Why is this a good project? What are some challenges you expect to face? How
might you overcome them? What are some warning signs that the project has gotten
off track, and how will you get the project back on track if needed?_

This is a good idea as I am excited about it, there are a couple of interesting
language decisions I would enjoy grappling with, and I think it could be very
beneficial to people who are interested in crowdsourcing a game. If I start spending
too much time looking at the Twitch API and how to interface with an emulator, I would
need to reevaluate progress on the project.
