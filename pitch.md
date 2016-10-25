# Sight Reading for All

## Describe your project in five words
Automatic Sight Reading Material Generation

## Audience
_Who are you helping, with your language? What is that person's
experience like now? How would their experience be better if you could help 
them?_

The target audience is musicians of all levels. Musicians' current experience
with sight reading is usually difficult because it is hard to find the right
level of music to get the most out of a piece of music. I think with this project,
their experience can improve by giving them the ability to find the right kind
of music to sight read.

## Why a language?
_Why is a **DSL** appropriate for your user(s)? How does it address the need?_

A DSL is appropriate because music has many complex forms and elements to learn,
depending on the person's background and interests. There are many genres of music.
In addition, classical music has many elements that cannot be easily found within
an existing piece of music.

Users of this DSL can specify specific elements of music to include in their sight-
reading, without having to randomly guess which pieces of music have the elements
the musicians want to focus on. This is an especially motivating factor because
sight reading is honest to goodness first time interactions with a piece of music,
and one cannot simply just look at music to find what they are looking for. Otherwise,
it isn't sight reading.

I feel the above is important because current musicians only look for the difficulty
of a piece for sight reading. It would be cool for musicians to practice smart when
practicing sight reading.

For reference, here are things off the top of my head that contributes to music's
complexity in a classical and jazz perspective (feel free to skip over; I just
wanted to make a point):

There are many chord progressions. Different kinds of cadences include:

* Authentic (Perfect, Imperfect)
* Plagal (Phrygian, Lydian etc.)
* Half
* Deceptive

There are numerous kinds of chords. The obvious triads are major, minor, diminished,
and augmented. 7th chords include major, minor, dominant, half-diminished, fully-
diminished, and major-minor. Jazz musicians also add alterations, which include
the b9, #9, #11/b5, and #5/b13.

The different kinds of chords also lead to many more chord progressions than the ones
just listed above. Inversions of chords also multiply the number of chords to consider.


There are 12 major scales, one for each key. For each major scale, there are 7
modes:

* Ionian (the major scale itself)
* Dorian
* Phrygian
* Lydian
* Mixolydian
* Aeolian (the natural minor of the major scale)
* Locrian

which gives us 12 * 7 = 84 different kinds of scales. There are also 12 harmonic
and melodic minor scales for each key. In addition, there are artifial scales
(whole tone, whole-half diminished, half-whole diminished), pentatonic scales
(major and minor), and other scales derived from other cultures. Scales can also
be built by specifying a few key base notes and randomly selecting other notes.

Sight reading is also not just about reading notes correctly. It's also about playing
the correct notes correctly. The texture and dynamics are extremely important. There
is also a plethora of Italian, French, German, and other words that describe how
one is supposed to play music as a few symbols does not cut the infinite number of ways
to play music. There are dictionaries of these terms, and most musicians don't most
of these terms off-hand.

Pianists read two lines when sight reading while violinists and others tend to read
one line. So for pianists, how the lines interact with each other is also a factor
when reading music. Many contemporary composers have use polytonality in compositions
(meaning a pianist reads a different key for each line). 

There are also different clefs:

* Treble
* Bass
* Alto
* Tenor

and reading ledger lines far above or below clefs is difficult (as is reading music
with a lot of accidentals such as sharps and flats).

The list goes on...

## Why you?
_What excites you about this idea? How did you come up with it?_

I think this can have a huge impact on how piano teachers teach their students.
One intent of this DSL was for me to create my own sight reading music. However,
I think piano teachers can put this to far greater use. Teachers are trained to
understand the strengths and weaknesses of students. If teachers created music
to train the weaknesses of students without going through the trouble of digging
through piles of music, it would improve the student's learning.

## Interface (syntax)
_What kinds of things can the user say in your language. How, generally, do they
say it? **Be as specific as possible.** You don't need to design syntax; but you
should be more specific than "The user describes properties of unicorns.", e.g.,
by describing which unicorn properties (horn color, tattoo, etc.) are most 
important to users and what kinds of values those properties might have._ 

Because music is vastly complex, I would like the users to be able to write
specific characteristics they want in their music. Users might want
different lengths of music, and so users might want something like:

`Phrygian scale in measures 9-16`

although this kind of specificity can sometimes be cheating. The above example
seems ok because it doesn't specify the specific notes or textures that are
going to be involved, and if the person writing this program is not going to
be the one sight reading, this kind of specificity is desirable and even needed.

So in general, people specify what properties they want in the music and where
they want it. The where part may or may not be omitted depending on the kind of 
properties they are choosing.

## Operation (semantics)
_What might happen when a program runs? Is there a computational model that
corresponds with your domain? How does a program interact with the
user? What kinds of semantic (i.e., non-syntax) errors might occur, and how 
might they be communicated to the user?_

When a program runs, it reads in the properties and outputs randomly generated
sheet music that adhere to the properties.

I feel that there are a two computational models that could fit to my DSL. The
first is the one that has the language describe the output of the program. The
other is one that is declarative. Although I feel like it would be nice to
have things be more declarative, I would also like the users to have a lot of
control.

Errors would generally occur if the musicians try to mention something not
in the DSL. By that, I mean if they try to describe a property not in the DSL,
the DSL should probably let the user know that it isn't a valid property. I
do think there should be a bit of creativity over the directions that can
be put in the music. One could give a short description of how the piece is
supposed to sound like, and in this case, that short description is arbitrary
and dependent on user input.

## Expressiveness
_What should be easy to do in this language? What should be possible, but
difficult? What should be impossible or very difficult?_

It should be easy to describe what kind of properties (scales, chords, textures,
dynamics, etc) they want in the sheet music generated. It should also be easy
to specify where these things occur if the user requires it. 

## Related work
_Are there any other DSLs in this domain? If not, describe how you know there
aren't and conjecture why not. If so, describe them and provide links. How well 
do they address the need? Are there any particularly admirable qualities of the
language? Are there parts of the language you think could be improved?_

There are several other DSLs in the domain. Milo Han has a small set of links [http://www.randomsheetmusic.com/][Random Sheet Music] Randomly generates music for single clef instruments.

[http://www.link.cs.cmu.edu/melody-generator/][Melisma Stochastic Melody Generator ] Generates midi files based on constraints given by the users.

[https://www.cs.hmc.edu/~keller/jazz/improvisor/][Impro-visor] Generates single line jazz improvisations over lead sheets. It can be used to practice jazz improvisation.

[https://www.sightreadingfactory.com/][Sight Reading Factory] Commerical software that generates surprisingly good sheet music. Users pay to use it.

The algorithms behind generating the music in these places are sophisticated. However, the ability
to describe what a user wants is not in my opinion. A music teacher teaching students of all levels
would need the ability to describe a lot of kinds of things about music in order to give good
sight reading material.

## Suitability
_What percentage of your time do you think will be spent directly engaging in
the **language** aspects of this project (e.g., making language design
decisions), as opposed to "systems" aspects of the project (e.g., implementing a
complicated semantics that doesn't require a lot of language design)?_

I would like to focus more time on language design because I feel that is an important
part of this language. My hope would be something like 60-40 or 70-30 in favor of
language design.

I know that creating the algorithms will take a lot of time. For now, I think I will just
do my best and won't strive to create perfect algorithms.

## Scope
_How big an idea is this? How ambitious is this project?_

I think this is reasonable. It focuses mainly on how musicians of different levels express
the kind of music they want to sight read. This project will probably be a proof-of-concept
because the algorithms are difficult to create well. 

## Challenges and opportunities
_Why is this a good project? What are some challenges you expect to face? How
might you overcome them? What are some warning signs that the project has gotten
off track, and how will you get the project back on track if needed?_

This is an interesting project because I feel like there can be improvements in how musicians
communicate their desires to computers and DSLs. I think with help from the people in the class
and people from the domain, we can create a DSL that allows musicians to express the right kind
of music for sight reading. The biggest warning sign is the case where I spend most of my time
implementing algorithms to generate the random music. This project should be mainly focused
about language design, but of course there will be some time focused on implementing the algorithms
themselves. 