# > Prompt

## Describe your project in five words

*Greater Digital Cueing for Theater*

## Audience
_Who are you helping, with your language? What is that person's
experience like now? How would their experience be better if you could help
them?_

For live theater productions, stage managers produce and use a *prompt book*
that includes actor blocking<sup>1</sup>, lighting, sound, and scenic cues<sup>2</sup>.

Wikipedia nicely describes the essence of a prompt book:

> The prompt book, also called transcript, the bible or sometimes simply
> "the book," is the copy of a production script that contains the information
> necessary to create a theatrical production from the ground up. It is a
> compilation of all blocking, business, light, speech and sound cues, lists of
> properties, drawings of the set, contact information for the cast and crew,
> and any other relevant information that might be necessary to help the
> production run smoothly and nicely.

While there are many important components of the prompt book, this project
aims to help stage manager's digitze their cue notes making them searchable,
summarizable, and editable for not only the stage manager, but the rest of the
production team&mdash;including the designers who may alter cues many times
before deciding on a final position for the cue. In the below picture, on
the right side, you can see how these cues are traditionally recorded: in pencil
on paper in the margin of the script:

![Prompt Book Example](/promptBookExample.jpg "Example Prompt Book")

During a production, *each* of the designers will create cue sheets that
look something like:

| Cue # | Page # | Cue Name/Description | Location                 |
|-------|--------|----------------------|--------------------------|
| 0.5   | 0      | House to Half        | after House closes       |
| 0.75  | 0      | Blackout             | 5 second follow          |
| …     | …      | …                    | …                        |
| 247.0 | 86     | Blackout             | Audrey: "…all was well." |      

For a standard production there will likely exist such a cue sheet independently
for scenic transitions, lights, and sound. The stage manager merges all the cues
into the prompt book's script and works with the designers to move their exact
position around as the designers watch the production rehearse.

Not only is this inconvenient, but it can create a disconnect between what the
designer thinks the cue is and what finally ends up in the prompt book; as they
adjust cues, if they are not careful to update their respective cue sheets, the
individual cues may be out of sync.

By creating a digital and semantic way to describe the cues, individual "cue sheets"
could be automatically merged into a digital script and allow for edits to be
propogated to/from the prompt book layout and the individual cue sheets. With
a fully developed system, cues could be edited in realtime by multiple people
and be searchable. There would be no need to flip through the script to see where
that cue at line "…all was well" occurs or what it says. During a rehearsal, if
a designer says take it back to cue 47, the stage manager would instantly be able
to find the page saving time and page flipping. In an ideal world, a nice GUI
would allow the stage manager and production team to easily interact with the
script and generate individualized cue sheets.

## Why a language?
_Why is a **DSL** appropriate for your user(s)? How does it address the need?_

Cue writing is inherently technical and should be written in a procedural way;
the procedural aspect supports my idea that a DSL is appropriate for the task
of cue writing. With a simple, expressive, and concise language, I think many
designers would agree that this could be an appropriate way to author and edit
cues.

Instead of using multiple Excel sheets in varying systematic formats, we can
express the same cues concisely and reliably in a DSL that can allow designers
and stage managers to interact with the cues more efficiently and flexibly.

I will admit, a language that you type out is not the optimal way to compose
the cues; a GUI paired with the DSL, would bring this project to a level who's
convenience and ease of use would make it practical solution for stage managers
and designers.

## Why you?
_What excites you about this idea? How did you come up with it?_

As a stage manager who has worked on several large productions involving hundreds
of cues, I've always dreaded transferring designer cue sheets' cues into the
prompt book. I've also longed for a way to be able to search and jump to cues
without spending time searching through the script.

For the past several shows I've worked on, I've debated making a digital prompt
book, but was dissapointed with the current solutions&mdash;annotating a PDF.
With this frustration, I've debated coming up with my own solution and this
project has presented a good opportunity to explore it further.

## Interface (syntax)
_What kinds of things can the user say in your language. How, generally, do they
say it? **Be as specific as possible.** You don't need to design syntax; but you
should be more specific than "The user describes properties of unicorns.", e.g.,
by describing which unicorn properties (horn color, tattoo, etc.) are most
important to users and what kinds of values those properties might have._

The user should be able to **describe a variety of cue types** (e.g. lighting,
sound, projection, as well as custom cue types) and **specify** with varying degrees
of exactness **where the cue lives** in the script (e.g. top of a page, at a specific
line or word, etc.). The user should also be able to **assign each cue a number
and state**: many times stage managers will right in a *standby* for cue X as well
as a *GO* call for cue X. There should also be the ability to **group cues to go
at once**; for example, if one wanted to cue lights and sound at the same time.
The cue notation should allow for comments/notes; however, it should always be
preferred to express patterns within the languge itself. In other words, since
calling a cue with a visual prompt is a common pattern, it would be best to express
this with a language keyword as opposed to simply leaving this in a comment.

## Operation (semantics)
_What might happen when a program runs? Is there a computational model that
corresponds with your domain? How does a program interact with the
user? What kinds of semantic (i.e., non-syntax) errors might occur, and how
might they be communicated to the user?_

This DSL fits under the computational model of a **data interpretation** since the
language simply describes the positions and relationship of cues to one another.
When a program runs, each cue will be grouped with other cues that it should
be called with and produce a master cue sheet as well as several breakdown
versions that divide the cues into individual cue sheets for each department.

As it attempts to group cues together, it may find a user has duplicated cue
numbers or put a *standby* for a cue after a *go* for that cue which would be
incorrect and create an error. The user would realize this through textual messages
specifying the cue number and conflicting situation. In a final version in which
a GUI exists, it would simply highlight the faulty cues.

## Expressiveness
_What should be easy to do in this language? What should be possible, but
difficult? What should be impossible or very difficult?_

It should be easy to describe cues and create custom "departments", but be difficult
enough to define custom departments that people are encouraged to keep it focused.

It should be impossible to describe blocking notes of the actors in this language.
It should be easy to reorder and renumber cues. Perhaps this happens through not
allowing the user to specify numbers, but having them generated at runtime similarly
to how Markdown numbers ordered lists.

## Related work
_Are there any other DSLs in this domain? If not, describe how you know there
aren't and conjecture why not. If so, describe them and provide links. How well
do they address the need? Are there any particularly admirable qualities of the
language? Are there parts of the language you think could be improved?_

[celtx](https://www.celtx.com/features.html) is a tool to create digital video
production scripts that generates various scene breakdowns and statistics from
a script. Since it's aimed at video production it does not include a way to
express cues. For the part of the project where I will need to digitally represent
a script, some ideas can be used from this software.

There are also a few threads floating around the internet ([SMNetwork](http://smnetwork.org/forum/tools-of-the-trade/digital-prompt-books-%28do-you-use-them%29/), [Control Booth](https://www.controlbooth.com/threads/electronic-prompt-book.23827/), and
[an anecdote](https://prezi.com/jquqjnga7lri/creating-a-digital-prompt-book/))
that discuss many people's aprehension and frustrations with current solutions (which
are mostly PDF hacks). Many are afraid to adopt a digiital solution since the
prompt book is so vital and having a computer freeze or malfunction during an
actual show would be extremely troubling.  

For the PDF solutions people have attempted to create, I think it gives an example
of an ultimate goal: create a solution that could produce a PDF of the script with
the appropriate cues giving people the option of printing the script. Alternativly,
an interactive version could be produced for those interested in putting more
faith in technology.

## Suitability
_What percentage of your time do you think will be spent directly engaging in
the **language** aspects of this project (e.g., making language design
decisions), as opposed to "systems" aspects of the project (e.g., implementing a
complicated semantics that doesn't require a lot of language design)?_

For this project, there exists a 50/50 split: designing both the cue langaguage
and a way to encode the script in a form that the cues could be applied to will
take half the time, while actually implementing it will take the other 50. Adding
a GUI version, would shift this to 15/85; however, I don't think at this point
making a GUI would make sense&mdash;unless splitting the project with a partner.

## Scope
_How big an idea is this? How ambitious is this project?_

Creating a text based interface and the supporting language for this project
is a nice balance of goals. In a way, in order to write the DSL for cueing,
I need to make a DSL (or at least an AST) for script to which the cue DSL
implementation could work with. If I aim to make a GUI, I think the projects
scope increases and will push on the amount of time to complete it. The GUI I
imagine would render a digital version of the image of a handwritten prompt
book.

## Challenges and opportunities
_Why is this a good project? What are some challenges you expect to face? How
might you overcome them? What are some warning signs that the project has gotten
off track, and how will you get the project back on track if needed?_

Designing the exact syntax will be tricky. I plan on interviewing some of my
friends and mentors with stage managing experience to get their input. Finding
something that works for many people will prove to be difficult; although each
stage manager has a procedural way of expressing their cues, people use slightly
different syntax. It will be hard to design a DSL that is extensible to allow
but still create a lanaguge that doesn't look like a mix of confusing syntax
from person to person.

If I end up spending too much time on the GUI or cannot express and generate
summaries of cues, then I think the project has "gotten off track". I think
the focus should be on implementing langugae features and less about creating
a pretty GUI. If the langugae is neat and feature-filled, creating an alternative
way to interact with it should be easy.

If this happens, I will devote more time to adding features and commandline
interfaces for the lanaguge. While a CLI isn't ideal for all stage managers,
it will help me produce an MVP that can be later extended into a more user
friendly version.

## Footnotes

<sup>1</sup>*Actor Blocking*: the movement and actions of an actor through
the physical space.

<sup>2</sup>Other types of cues may be included for certain productions.
            e.g. projection cues.
