# To-Do List Organizer

## Describe your project in five words
Chronological to-do lists from categories

## Audience
_Who are you helping, with your language? What is that person's
experience like now? How would their experience be better if you could help 
them?_
The audience would be people who use to-do lists to organize their plans.
Currently, either people organize a to-do list chronologically, or they do it by some bigger, more general
categories. In ordering lists chronologically, it's easy to miss items as you have to think back and forth
between all the categories. When putting to-do lists together by categories, on the other hand, it's hard to
see it as a cohesive to-do list instead of multiple to-do lists that you need to juggle. In other words, it's
easier to write but harder to use.


## Why a language?
_Why is a **DSL** appropriate for your user(s)? How does it address the need?_
It is helpful because the language can allow for a lot of flexibility in what the user wants to be able to
write. Additionally, categorized to-do lists are already like a language. You have a large category with
smaller tasks, each of which has a deadline. Some people create their to-do lists per day while some people 
make them per hour. So, there is a lot of variability in the tasks and timelines, but they all follow a similar
outline of big categories, smaller tasks, and a time scale.


## Why you?
_What excites you about this idea? How did you come up with it?_
I'm very excited about this project because of the usefulness of it. I know a lot of people who struggle with
this same problem and I think that it would be very rewarding to have people use it (after, of course, the
initial prototype struggles). 

Initally, I thought of this idea because of my experiences dealing with multiple people having a bunch of
tasks and having short, stressful periods followed by long, relaxed periods. As I have thought more 
about this idea, though, I don't think this would be my main focus. I think that
multiple people would add too much variability to the language and make it less focused. Right now, I
think the language should focus on one person being more productive with their free time. By being able
to map out when tasks need to be done for one person seems to be effective enough and overall more
helpful because most people make to-do lists only for themselves.


## Interface (syntax)
_What kinds of things can the user say in your language. How, generally, do they
say it? **Be as specific as possible.** You don't need to design syntax; but you
should be more specific than "The user describes properties of unicorns.", e.g.,
by describing which unicorn properties (horn color, tattoo, etc.) are most 
important to users and what kinds of values those properties might have._ 
The user should be able to name categories and give tasks with names and due dates in each of those
categories. The user should also be able to specify a timeline that is consistent with the due
dates of the tasks. For example, if a user says that the task is due Monday night, they should have
a Monday night time slot so that the language can figure out where "Monday night" is in relation
to the rest of the timeline. This way the user can have a to-do list that is the most helpful
to them and allows for customizability.

Additionally this is a rather simple syntax: users will specify categories, tasks (with a time),
and a timeline so the users hopefully do not have to learn much to use this language.


## Operation (semantics)
_What might happen when a program runs? Is there a computational model that
corresponds with your domain? How does a program interact with the
user? What kinds of semantic (i.e., non-syntax) errors might occur, and how 
might they be communicated to the user?_
When a program runs, it should output a list of things to do for each time period given
by the user. The computational model that this fits best is either data visualization
or constraint satisfaction because it shows the to-do lists in a different way and
it must satisfy the constraints of the given to-do lists, such as when things are due.
It should only interact with users through the categorized to-do lists that
the user gave as a program. 


## Expressiveness
_What should be easy to do in this language? What should be possible, but
difficult? What should be impossible or very difficult?_
It should be very easy to write a to-do list for one person in this language. It should
be difficult, but possible, to make related to-do lists for multiple people. These would
probably jsut have to be given as separate to-do lists, where the tasks are already
somewhat split up between the users because, as of the idea right now, returning the
tasks with the tasks spread across multiple to-do lists is not possible right now.
It should be impossible or very difficult to do much more than just to-do lists with
this language.


## Related work
_Are there any other DSLs in this domain? If not, describe how you know there
aren't and conjecture why not. If so, describe them and provide links. How well 
do they address the need? Are there any particularly admirable qualities of the
language? Are there parts of the language you think could be improved?_
I don't think there are any in the specific domain of taking categorical lists and making
them chronological. There are, for instance, Google Tasks, which are along the side of 
Google Calendar. They let people input tasks as they remember them. However, they do not
allow you to make tasks lists by categories. I do like that you can rearrange the task
ordering, so I think could allow the user to write the tasks down by category and then
rearrange them by time. However, this way would be much more difficult than a program
that could do that and optimize it for you.


## Suitability
_What percentage of your time do you think will be spent directly engaging in
the **language** aspects of this project (e.g., making language design
decisions), as opposed to "systems" aspects of the project (e.g., implementing a
complicated semantics that doesn't require a lot of language design)?_
As my idea looks right now, the language itself is rather simple from a systems aspect
because it's just rearranging the given lists, with some small optimizations and
tasks. Because of this, I think most of the project would be refining the language
design aspects of the projects so that it's very usable and intuitive. I think the
main part of this project will be trying to mask that this is programming to the user
and instead make it seem that they are just writing tasks.


## Scope
_How big an idea is this? How ambitious is this project?_
This started out as a very broad idea in scope, but I think that this iteration is
much more refined and focused. Initially, I wanted to have this work for all to-do
lists, regardless of the number of people or how people wanted to write their to-do
lists. I think that the constraints will actually help people because each line of the
program must take one of three forms: a list of times, a category name, or a task with
a time for when it's due. Even if I worked to add more features (depending on how the
first iteration of building this goes), I would still want it to be very simple because
I think that will help users who do not have the background in computer science.


## Challenges and opportunities
_Why is this a good project? What are some challenges you expect to face? How
might you overcome them? What are some warning signs that the project has gotten
off track, and how will you get the project back on track if needed?_
This will be a good projects because it will fit our week-by-week based development.
This is a project that will be very easy to get done in chunks, starting with just
the bare bones of the project and then building up the syntactic sugar that makes it
easy to use and more features depending on the amount of time each part takes. I think
some design issues will come up in trying to figure out if there is a universally simple
way to give to-do lists as programs that everyone, especially non-programmers, will
understand. There will probably also be some coding problems of figuring out how
I want the IR to look (and how many levels of IR I want).  

One way that I will know that this project has gotten out of hand is when the syntax
has gotten out of hand. As I mentioned in the syntax discussion, right now I figure
that the syntax will be rather simple. At first, it may be complicated because the
sugar will not be my main prority. However, after adding sugar it will be a sign
that I have added too many features when the syntax becomes too cluttered and hard to
read. At that point, I will want to figure out what features to remove to make the syntax
clean and easy to read and write.
