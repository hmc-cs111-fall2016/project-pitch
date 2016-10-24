# CSound++

## Describe your project in five words

Digital instrument creation for musicians.

## Audience
_Who are you helping, with your language? What is that person's
experience like now? How would their experience be better if you could help 
them?_

The language targets musicians interested in digital music synthesis. The
prototypical user is one familiar with the basics of computer music, but does
not necessarily possess a strong technical background. The user understands
computers insofar as they are used to make music, but prefers to think in terms
of musical concepts rather than technical ones.

There are currently two tools that can be used to make digital music. The first
is a DSL called [CSound](http://www.csounds.com/). CSound allows users to
combine oscillators -- primitive signal generation components -- and effects
like filters to literally build from scratch their own digital instruments.
This gives the user a lot of power and freedom to create many different kinds
of instruments, but the oscillator- level of abstraction requires thinking more
technically and less conceptually than many musicians are used to. For this
reason, and because of CSound's intimidating opcode-based syntax, the language
is not very popular outside of academia.

On the other end of the abstraction spectrum are Digital Audio Workstations
(DAWs). Popular DAWs like [Pro Tools](http://www.avid.com/pro-tools/) and [FL
Studio](http://www.image-line.com/flstudio/) usually have built-in digital
"instruments" which user's can program by writing a MIDI score. These are
usually prefabricated instruments that can only be customized by changing
certain parameters. They lack the fluency to combine and compose instruments
which is offered by a language like CSound. As a result, it is possible to get
a range of sounds out of each instrument, but it is hard or impossible to
create completely new instruments.

I believe there is a solution which offers the best of both words. A language
with the flexibility of CSound that operates at a level closer to the musician-
oriented DAWs than to the techie-oriented CSound would provide a solution for
musicians looking for more flexibility than offered by a DAW, but who are put
off by the technicalities of CSound.

## Why a language?
_Why is a **DSL** appropriate for your user(s)? How does it address the need?_

The domain is easily broken down into primitive components which can be
composed in a flexible way. There are two basic types that a user will want to
deal with: sources, which produce a signal, and effects, which take a signal as
input and produce a modified signal. It is easy to see how many effects can be
chained together to create a new kind of effect. Also, a source can be attached
to an effects chain to create a new kind of source.

With this basic design, we have vocabulary (sources and effects) and fluency
(chains of components). The advantage of approaching the problem this way is
that it mimics the way music producers are used to thinking: just about every
DAW provides a method for creating effects chains and using them to modify the
recordings that make up the song.

## Why you?
_What excites you about this idea? How did you come up with it?_

I have been interested in making music of all kinds for years. I took Music 88
(Computer Music) last year, and while I enjoyed learning CSound and using it to
make music, I also felt frustrated that it is so difficult to use.

I was discussing potential project ideas with Daniel Zhang when the
conversation turned to Melodica, and we both felt that it would be fun to make
a music language like that. It seemed natural to me that there should be a
language targeted at serious musicians which, provided the user is
knowledgeable in the domain, is as easy to use as Melodica, but which provides
more power and flexibility than a DAW. In short, I want to fill in the gap in
this spectrum:

```
Simple ----------------> Powerful
Melodica -> DAWs -> ??? -> CSound
                     ^
                  CSound++
```

## Interface (syntax)
_What kinds of things can the user say in your language. How, generally, do they
say it? **Be as specific as possible.** You don't need to design syntax; but you
should be more specific than "The user describes properties of unicorns.", e.g.,
by describing which unicorn properties (horn color, tattoo, etc.) are most 
important to users and what kinds of values those properties might have._ 

The user creates instruments by combining components. There are three types of
components, distinguished by their inputs and outputs.

A _source_ is a component which produces a signal. (A signal is like a
potential sound. At runtime, it can be synthesized into a sound via the
computer's DAC, or perhaps it can be written to a file.) A source has no input
(though it may have _parameters_, see below) and a single output. There will be
several types of primitive sources, distinguished by the characteristics of the
signals they produce. Examples include frequency modulation synthesizers and
physical modeling synthesizers.

An _effect_ is a component which modifies a signal. Its input is a signal, and
its output is a new, transformed signal. Examples of primitive effects may
include equalization, compression, and distortion.

Effects can be combined into chains by connecting the output of one effect to
the input of the next effect. It is easy to see that a chain of effects is
itself an effect, since it has one input, which is passed through all the
effects in series, until we reach the final output. Also note that if we
connect the output of a source to the input of an effect, we get a source.

This describes the basic way in which the user can create new components by
chaining together existing components. But what if the user wants to modify a
signal by sending it through two effects chains in parallel, and then combining
the results? This leads to the third kind of component:

A _multiplexer_ is a component which takes two or more inputs and produces a
single output. They are distinguished by the method used to combine the inputs
into a single signal. For example, you could have a multiplexer whose output is
the sum of its inputs, or one whose output is a weighted average of its inputs.

The last feature I propose for the language is designed to aid in code reuse.
Components can have parameters which modify the behavior of the component.
These are not inputs; the feature behaves more like C++ templates in that each
instantiation of a component with different parameters is conceptually a
different component, which just happens to use the same code. For example, an
instrument (which is really just a source) may have parameters to determine the
pitch and amplitude of the signal it produces.

## Operation (semantics)
_What might happen when a program runs? Is there a computational model that
corresponds with your domain? How does a program interact with the
user? What kinds of semantic (i.e., non-syntax) errors might occur, and how 
might they be communicated to the user?_

The computational model is "production rules". A program written in CSound++
takes as input a MIDI score. This can be a prewritten MIDI file, are a live
stream of MIDI events from a MIDI controller such as a keyboard. The events
are then parsed into lists of parameters, including information such as pitch
and velocity (which generally corresponds to loudness). These parameters are
then used to instantiate a CSound++ instrument, which produces an audio signal,
the output of the program.

This method of instantiating the instruments with parameters obtained from the
MIDI score may mean that all instruments accept several implicit parameters,
corresponding to the information contained in a MIDI note-on event.

## Expressiveness
_What should be easy to do in this language? What should be possible, but
difficult? What should be impossible or very difficult?_

It should be easy to create instruments that are based on commonly-used patterns like frequency modulation or physical modeling. It should be harder, but possible, to create completely different kinds of instruments. This may mean exposing CSound-like primitives, but encouraging users to use the higher level constructs where possible.

It should be difficult or almost impossible to produce a complete song with
this language. The language is not a DAW; that is, it is not meant to be used
for recording, mixing or mastering. More likely, the user would need to combine
instruments written in this language with a fully-feature DAW to produce a
complete song.

## Related work
_Are there any other DSLs in this domain? If not, describe how you know there
aren't and conjecture why not. If so, describe them and provide links. How well 
do they address the need? Are there any particularly admirable qualities of the
language? Are there parts of the language you think could be improved?_

CSound and any DAW would fall into this domain. See above for a description of
these tools, their advantages, and their problems.

## Suitability
_What percentage of your time do you think will be spent directly engaging in
the **language** aspects of this project (e.g., making language design
decisions), as opposed to "systems" aspects of the project (e.g., implementing a
complicated semantics that doesn't require a lot of language design)?_

I plan on leveraging CSound to implement the semantics of my language. CSound
comes with tools for generating audio from instruments, and for interfacing
with MIDI data. This means that the only semantics I would have to implement
would be the translation from CSound++ to CSound, which should be quite
feasible. This will leave lots of time for language decisions.

## Scope
_How big an idea is this? How ambitious is this project?_

I think this project is distinctly doable, given that most of the technical work could leverage existing solutions as described above. In fact, I believe it would be possible (though probably not recommended) to implement a prototype of this language using the CSound preprocessor.

## Challenges and opportunities
_Why is this a good project? What are some challenges you expect to face? How
might you overcome them? What are some warning signs that the project has gotten
off track, and how will you get the project back on track if needed?_

This project should emphasize the extensibility of the language, as advocated
for by Steele, since it focuses on a small set of primitives which can be
combined to create new primitive-like objects. This focus on composition and
extensibility should make for a good case study in language design.

I expect to meet a significant challenge in deciding what features to add. I
have a tendency to get excited and run from one feature to the next without
really finishing any of them, especially in a project like this where the
domain interests me -- I can already think of way more features I would like to
implement than I will probably have time for. Overcoming this challenge will
require foresight, planning, and an honest evaluation of which features are
necessary for a minimum viable project.

One way the project could get offtrack is feature creep. I should notice this
early, as it will mean deviating from the plan I have laid out ahead of time. I
could also get offtrack if the implementation of the semantics starts taking up
more time than planned for. If this starts to happen, I will need to reevaluate
whether the feature that is difficult to implement is really necessary, and I
may need to come up with alternatives that would be easier to build.
