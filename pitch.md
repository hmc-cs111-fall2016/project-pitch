# Succinct Scheduling

## Describe your project in five words
Describe schedules sucinctly and precisely.

## Audience
_Who are you helping, with your language? What is that person's
experience like now? How would their experience be better if you could help 
them?_

This project is designed to serve individuals who need to schedule meetings
among a group of people.  The language would provide a means by which an
individual can specify their preference related to scheduling.  With more than
a handful of reasonably busy individuals it is unlikely that there will be a
meeting time which is the top choice of everyone involved.

Currently the de-facto standards for scheduling are one
of the following two methods:
 * Everyone send out their availability for a small set of times and a leader
picks the times that seem to work best for a plurality.
 * Everyone uses some software, such as a WhenIsGood&#8482; or When2Meet&#8482;
and choses a binary yes/no for each time slot.

Beyond the issue of there not being a single time that works for everyone,
there is also an issue in which individuals will be conservative in listing
times that they could theoretically attend, as Daniel Sonner pointed out,
some people will paint over the times that are *best* for them, but not
*all* the times which could work for them.

Both of these issues (inability to find a time preferred by all individuals
and people being extra conservative with respect to their availability) are
addressed by allowing for greater expressiveness in describing one's schedule.
This is because allowing for a gradation of availability (from totally free, to
somewhat available, to completely busy) might make people less likely to
game the system by saying that they are completely at times that are just
suboptimal for them.  It also means that there is more information which a
clever algorithm could make of when deciding which of two conflicts is worse.

If I was able to help them, users would be able to specify, in a way that feels
natural, their availability and preferences.  Hopefully this can reduce 
the work of an individual (who must compile the results of an email) or the
repetition inherent in painting over the same boxes for pairs of weeks when
using a WhenIsGood&#8482;.


## Why a language?
_Why is a **DSL** appropriate for your user(s)? How does it address the need?_

The essential gap I am trying to bridge is that of language.  I hope to provide
users with a better way of expressing their schedules, to satisfy two specific
goals:
 * Less redundancy: No need to paint the same pattern over multiple weeks.
 * More detailed information: Can specify a range of availability rather than 
 a binary variable for each time slot.

A simple calendar or WhenIsGood does not allow for this level of
expressiveness. An user actually writing text (such as in the email scenario)
does allow for arbitrarily high expressivenes, but would then shift the burden
of interpreting users' availability onto another user (the organizer).  My
language hopes to reach in the middle, allowing greater expressiveness than
other common scheduling tools, without shifting the burden of interpreting
this extra information onto the user.

## Why you?
_What excites you about this idea? How did you come up with it?_

As I mentioned during the previous version of this assignment, I came
up with the idea when I needed to fill out many of these schedules
for all the different organizations whose meetings I attend. 

At least for my schedule, I found that there were many patterns
which would have been easier to describe than painting the same
pattern of boxes over several different days.  There are also some 
relationships that are not just difficult, but actually impossible to 
currently express, such as variability preference of how well a 
certain time fits, or the "I can make any of these hours work, but 
not all of them at the same time." situation.

I am excited about trying to make the language integrate with existing calendar
formats, since this would involve finding a clever abstraction for all the
information which could serve as a medium between the natural / intuitive
language with which users would describe their schedule, and the highly
structured data of an exported Google Calendar or iCal instance.

## Interface (syntax)
_What kinds of things can the user say in your language. How, generally, do they
say it? **Be as specific as possible.** You don't need to design syntax; but you
should be more specific than "The user describes properties of unicorns.", e.g.,
by describing which unicorn properties (horn color, tattoo, etc.) are most 
important to users and what kinds of values those properties might have._ 

The users should write their schedule in a text file or provide an .ical file
(generated from Google calendar or apple calendar, for users who do not want 
 or need the increased expressiveness and concision provided by my DSL, but
 would still like to schedule with others who **do** use the DSL).

Here are some sample descriptions that I am considering:

```
time zone: PST

On Monday, Wednesday, Friday:
  busy 9am - 11am
  busy 12pm - 12:30pm
  busy 3pm - 4pm

On Thursday:
  free one_hour_of(2pm - 5pm)
  busy after(7pm)

On Weekdays:
  free noon-1pm
  free 2pm - 4pm, badness=**
  free 6pm - 7pm, badness=***

```

We can see several things about the syntax.  First: it is almost certainly
destined to be an external DSL, because of its freedom of characters and
complicated parsing (sometimes times have minutes attached, modifiers for 
the time of day, potentially military time, and the use of unary asterisk
counters to represent how undesirable that block would be).

There will also be a file provided by the leader which controls the
portion of the calendar year which the scheduling could potentially occur.

## Operation (semantics)
_What might happen when a program runs? Is there a computational model that
corresponds with your domain? How does a program interact with the
user? What kinds of semantic (i.e., non-syntax) errors might occur, and how 
might they be communicated to the user?_

When a program runs, there are several steps taken. The first step is,
for each input file, the program parses the provided information into the
language's internal representation.

The next step in the run of the program is to combine the internal
representation data generated for each individual into a version of the
internal representation which contains, for each possible time in the range
of possible schedules.

Finally, the program would use this internal representation to attempt to
find a solution to the scheduling problem and output this data to the
user (perhaps with an explanation of why it was selected and some of the
second choices -- providing these extra bits of information isn't essential,
these are more of stretch goals).

One of the semantic troubles which could occur would be if a user put in
rules which are inconsistent.  One simple example of this might not be
an error at all. For example, if someone says they are available on Weekdays
from 1pm to 6pm and then they say that they are busy from 4 to 5 on Tuesdays,
we don't assume they are inconsistent, we rather assume that both statements
are valid except for the block during which they are in conflict, for which
we consider the more specific case.

This is similar to how browsers will interpret CSS, some conflicts are allowed
and the more specific directive is followed. I would anticipate trying to
follow this behavior (though probably logging these incidents to the user could
ensure they were intended).

There is also the opportunity for conflicts with the same specificity, in which
the best choice seems to be simply returning an error and reporting it to the
user.

There is also the semantic issue which could result if the combination of schedules
finds no valid schedule. I'm not sure I would classify this as an error exactly,
but certainly an unfortunate outcome which the code should be prepared to handle.

## Expressiveness
_What should be easy to do in this language? What should be possible, but
difficult? What should be impossible or very difficult?_

I haven't made any changes to expressiveness since the last time I
considered this idea.

It should be easy to describe when are the great, good, bad, and terrible
times to meet (likely default values of great and terrible respectively).
It should also be possible to express more complicated dependencies,
such as a preference for a meeting time that coincides or avoids another
group member, or a freedom in a 3 hour block where only 1 block can be
scheduled at a time.

It should be very difficult to do perform functions unrelated to scheduling,
such as arithmetic, nested control flow, or see implementation details.

I don't think there should be anything in between (of medium difficulty).


## Related work
_Are there any other DSLs in this domain? If not, describe how you know there
aren't and conjecture why not. If so, describe them and provide links. How well 
do they address the need? Are there any particularly admirable qualities of the
language? Are there parts of the language you think could be improved?_

As I mentioned there are definitely already DSLs in this domain:
 * [WhenIsGood](http://whenisgood.net/)
 * [When2Meet](http://www.when2meet.com)

These are indeed DSLs because they are computerized schedulers
with a specific syntax (painting over certain blocks), and associated
semantics (painted blocks are free blocks).

These DSLs are quite minimalistic (i.e. when they run, they only support the
intersection operation for the sets of times from each individual -- as far
as I can tell).  I am also looking at some of the features provided for
[Premium Users](http://whenisgood.net/PremiumInfo).

My solution to the scheduling problem might be a bit more
ambitious in the functionality it hopes to provide.  This does allow for more
expressiveness, which is nice, but expressiveness is a double edged sword,
I will need to take care during design to avoid feature creep and extra complexity
for users.  Perhaps I will find that the existing websites' simplicity is
more desirable than the benefits of the expressiveness I aim to provide (but
I hope not!).

I think that they address the need pretty well at the present, but I think that
my DSL could cut down on repetition and allow users to better express themselves.

## Suitability
_What percentage of your time do you think will be spent directly engaging in
the **language** aspects of this project (e.g., making language design
decisions), as opposed to "systems" aspects of the project (e.g., implementing a
complicated semantics that doesn't require a lot of language design)?_

The main reason I finally settled on this project was that I felt it had the best
balance of **language** design to systems programming of any of my potential
choices.  As I mentioned in the previous assignment, the underlying internal
representation could be represented with just a [protocol
buffer](https://en.wikipedia.org/wiki/Protocol_Buffers) for each individual.

Armed with the parsing tools from the Picobot lab, the work of writing a 
parser to take the syntax of my language to the internal representation should 
be overshadowed by the work of designing the best interface/fluency of the
language for the user's sake.

Based on Daniel Sonner's helpful advice, I have decided not to focus on the
algorithms to find an optimal schedule given a set of constraints, which could
potentially be *very* interesting, so that I can focus the lion's share of
my time on designing an intuitive syntax and then implementing it.

## Scope
_How big an idea is this? How ambitious is this project?_

I think that this is a good, ambitious project.  It has enough extensions and
places to cut back such that I will be able to make a very **very** minimal
prototype upon which I can iterate, gradually adding more of the
desired characteristics.

This will ensure that it isn't to big to get off the ground, but that there
are enough extensions to the project to keep me busy.

## Challenges and opportunities
_Why is this a good project? What are some challenges you expect to face? How
might you overcome them? What are some warning signs that the project has gotten
off track, and how will you get the project back on track if needed?_

I think it is a good idea, since it has a use case that individuals do encounter
somewhat regularly so this DSL might just be able to fit into that niche.

My worries that the idea was more of an "app" than a "language" have been
assuaged by me realization that I will be focusing primarily on the design of
the syntax of the language and ensuring its fluency for the user.
