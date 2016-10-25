# Am.Available

## Describe your project in five words

## Audience
_Who are you helping, with your language? What is that person's
experience like now? How would their experience be better if you could help
them?_

My language helps people with scheduling, figuring when they are free, and
suggesting times to schedule events. That person's current experience with
finding free time to schedule things are to look over their calendar,
scrutinizing their free times, aggregating them in a list, and either choosing
a time themselves or sending their availability to a second party. There are
also additional constraints with work hours and different time zones. If the
person makes a mistake and an event is planned for a time for which they are
actuall unavailable, then they have to either go through the entire process
again to reschedule, or if they don't catch it in time, find out they double-
booked themselves when the events are supposed to happen (which is a bad and
embarassing thing).

With my language, users can query their calendar for their own availability,
refined by constraints such as duration of the event they are trying to plan
for, time zones, what hours of the day it can happen, etc. The user will put in
a command, and the program will instantly output a list of times, delimited by
day, that the user is available to plan this event

## Why a language?
_Why is a **DSL** appropriate for your user(s)? How does it address the need?_

In this case, I'm envisioning a command line tool that is interfaced with this
DSL. The DSL is appropriate because, like SQL, it allows the user to input
conditinos for this query. This addresses the need to refine the output as
appropriate to specific conditions.

## Why you?
_What excites you about this idea? How did you come up with it?_

I've needed to give my availability so often in the past couple of months. I
have been scheduling interviews, which is the major reason why I have to give my
availability (often many times because companies schedule 2+ phone interviews
and an onsite). I am also the PM for the Google Clinic, and a lot of PM duties
consist of planning and organization. Having this tool would have been extremely
productive for me! The idea came to me when I had to look up my availability
for the N'th time.


## Interface (syntax)
_What kinds of things can the user say in your language. How, generally, do they
say it? **Be as specific as possible.** You don't need to design syntax; but you
should be more specific than "The user describes properties of unicorns.", e.g.,
by describing which unicorn properties (horn color, tattoo, etc.) are most
important to users and what kinds of values those properties might have._

As hinted at above, users can suggest time zones, constraints on hours (i.e.
9am - 6pm), how long the event will occur for, and how long it takes the user to get
to where they need to be for the event or meeting. The user will also put dates
on and between which they want the event to take place.

For time zones, I would use the time zone's three letter codes, e.g. "PDT". Both
constaints on hours and how long the event will occur for would be in the form
of integers. Constaints will have two numbers, and if only one is given, the
tool would assume the event has to occur on or after that time. The user can
also ignore the starting time constaint by putting an underscore in its place.
The date range that the event should happen is provided in a similar fashion.
The time it takes for the user to get to where they need to be for the event
would also be an integer, but perhaps in the future it can leverage Google Maps
and give an estimate through the user providing a starting location and an
ending location.

## Operation (semantics)
_What might happen when a program runs? Is there a computational model that
corresponds with your domain? How does a program interact with the
user? What kinds of semantic (i.e., non-syntax) errors might occur, and how
might they be communicated to the user?_

When the program runs, the user inputs conditions or constaints and the program
will return the hour/minute times delimited by their respective dates. The
computational model that corresponds with this DSL/tool is "constraint
satisfaction". The program provides output according to the user's input. The
possible semantic errors that I can foresee are constaints that yield no
available times, in which case the program will output a sentence saying so.


## Expressiveness
_What should be easy to do in this language? What should be possible, but
difficult? What should be impossible or very difficult?_

It should be easy to query free times based on the provided constraints
and conditions.


## Related work
_Are there any other DSLs in this domain? If not, describe how you know there
aren't and conjecture why not. If so, describe them and provide links. How well
do they address the need? Are there any particularly admirable qualities of the
language? Are there parts of the language you think could be improved?_

Google Calendar itself provides a "find a time" feature IF you are planning an
event by inviting multiple people. However, I've never used that feature. This
feature is also (as far as I know) not available when the planning is just for
you, or if you need to provide a list of avialable times. There probably isn't
a similar tool like this because the problem seems more or less trivial, and it
is at most seen as a nuisance when needing to plan things.

## Suitability
_What percentage of your time do you think will be spent directly engaging in
the **language** aspects of this project (e.g., making language design
decisions), as opposed to "systems" aspects of the project (e.g., implementing a
complicated semantics that doesn't require a lot of language design)?_

I think it will be split half and half. The language needs to be defined well
enough to be unambiguous and still be an efficient way to do what it is supposed
to do (i.e. query and return free times). Since this tool will most likely be
built on top of the Google Calendar API, it might take some effort to translate
what the API returns into a form that the program can then query.

## Scope
_How big an idea is this? How ambitious is this project?_

Depending on how detailed the constraints can be, this could be a very ambitious
project. For what I've defined above, it seems to have an "average" amount of
ambition and should be very doable.

## Challenges and opportunities
_Why is this a good project? What are some challenges you expect to face? How
might you overcome them? What are some warning signs that the project has gotten
off track, and how will you get the project back on track if needed?_

This is a good project because I will definitely use it! And hopefully others
will as well! Some challenges I expect to face would be the systems design of
how to translate the data produced by the Google Calendar API into a structure
that is convenient to query.

Not super sure on what warning signs could look like as of now, but probably
doing too much to wrestle with the API would probably signal that I am putting
too much emphasis in the wrong places. At that point, it might be worth it to
consider alternatives to using the GCal API (perhaps forgoing relying on an
external system and just query a file format of events that is convenient). At
this moment, there are no plans to make this program a full-blown calendar app,
so too many additional functionalities on that front would probably mean the
emphasis has changed and that I should re-evaluate which features are definitely
needed, which are nice-to-haves, and which are superfluous to the project. Then
I would cut out all the superfluous and hold off on the nice-to-haves until all
the needed features are there, then re-evaluate the project at that time.

