# Patatap++

## Describe your project in five words


## Audience
_Who are you helping, with your language? What is that person's
experience like now? How would their experience be better if you could help 
them?_

The language is aimed for people interested in creating music and animations in an intuitive, enjoyable way. The goal is to allow users to experience visual music and create melodies in a non-traditional environment - eseentially turning the keyboard into an electronic piano of sorts.  

Right now http://patatap.com/ , which describes itself as a "portable animation and sound kit", does this quite well. There are unique sounds and animations for every letter from A-Z while the spacebar changes the background color. But there are certain things I think could be improved. For one, rather than having the same 26 sounds, it would be cool to be able to swap these out for a different set of sounds. This could allow for many different possibilities like a set where the keys on the left are chords, or a set of drum noises, or a set of hip hop beats and noises. 

The main thing I would want to implement that differentiates it from patatap is the ability to save sequences of sound "layers" and build and add to these layers of sound. Users would be able to save their creations and gradually build up towards a masterpiece. 

## Why a language?
_Why is a **DSL** appropriate for your user(s)? How does it address the need?_

The only way to create visual music is through computers (or physics like in this video: https://www.youtube.com/watch?v=Q3oItpVa9fs) so this domain is already very restricted. A DSL is appropriate because it takes away the programming required to create animations and sounds in a general purpose programming language like JavaScript or a DSL like CSS (whose domain is organization of content on a webpage, not animation). 

## Why you?
_What excites you about this idea? How did you come up with it?_

Music visualization is something I've always been drawn to. When I think of music visualization, the first thing I see is the Windows Media Player animations I saw as a kid. I think it's very exciting to have animations that don't change according to notes in a song, but change directly to notes/sounds through user input. 

I drew inspiration from this website I came across: http://patatap.com/. Ever since I've seen it, I've wanted to build something like it, extending it with my own ideas. 

## Interface (syntax)
_What kinds of things can the user say in your language. How, generally, do they
say it? **Be as specific as possible.** You don't need to design syntax; but you
should be more specific than "The user describes properties of unicorns.", e.g.,
by describing which unicorn properties (horn color, tattoo, etc.) are most 
important to users and what kinds of values those properties might have._ 

In my language, the user should be able to create sounds and animations. Each letter on the keyboard will correspond to a particular sound and animation. Each of the sounds made by a letter should be unique - just like in an instrument. I will have to decide which keys correspond to which notes/sounds and how to organize this mapping and the recording/deletion of layers of sound and animation (syntax). For instance, should the sounds that are higher in pitch be on the QWERTY line and lowers ones be on the ASDF line or to have the sounds I perceive will be most commonly used to be placed on the ASDF line. As the goal is to produce music in a non-traditional way, I want to move away from just musical notes, ideally having different sets of 26 sounds as mentioned previously. 

For each animation, the main elements I need to take into account is the appearance (size, shape, color, patterns, number etc.) of the object to be animated as well as how it enter and exits the screen(fly in, zoom in, fade etc.). The animations ideally should be different enough from each other to feel intriguing and have a small element of randomness (which I really liked in Context-Free)(perhaps the randomness could be set by the user?). There is also the difficult language choice of to what extent I would allow the user to change the appearance of the animated object. If I allow many aspects to be tuned, then users may spend more time on this setup and the creation aspect could feel less spontaneous, taking away from the goal of creating visual music in an intuitive, enjoyable way. There is also the choice of how I want these things to be tuned, whether through keystrokes or some kind of drag-able bar on the screen. 

There are two ways that I envision a user could create animations. The first is that the animation persists between key presses. For instance, if pressing 'a' causes a red triangle to physically loop, pressing 'a' repeatedly makes it loop tighter and tighter. So the triangle is looping even after the note has ended. The second option is that once a letter is pressed, the corresponding animation eventually disappears.

I think a balance between these two approaches, leaning towards the second, is ideal. It's also important to note the difference between an object (physical object, not in the programming sense) and an animation persisting and the consequences of each. Continously occurring animations could get annoying and potentially distract users from the sound aspect. Persisting objects have a similar issue, but are less distracting. I like the idea of some things, such as changing the color of the background, persisting between key presses. But I think that if all objects persisted between key presses, the screen could quickly get littered with many different shapes and objects. Generally, I am opposed to objects and animations persisting after a key press. The main reason for this is the screen clutter that would occur when a user records layers of sound and animations. Inevitably, some of the same keys will be reused between layers (after all, there are only 26). Suppose every layer resuses the same key, then there would be many duplicate objects and animations, all of which persist on the screen. There also seems to be no point to objects and animations persisting between key presses. The layers of sound and animation already provides this persistence: including the persistence of the sound which is infinitely more interesting and adds to the richness of the language much more than just a continous animation. It also seems cleaner for the the page to eventually return to a "blank canvas".

Another aspect to consider is whether one object or animation could also be altered by different keys. Extending the previous example, pressing 'spacebar' after 'a' could change the triangle's color while 'b' could make the triangle bigger and 's' could make it smaller. 
Once again moderation is important as too much overlap between keys could get confusing, but some overlap would definitely be interesting. 


## Operation (semantics)
_What might happen when a program runs? Is there a computational model that
corresponds with your domain? How does a program interact with the
user? What kinds of semantic (i.e., non-syntax) errors might occur, and how 
might they be communicated to the user?_

The computational model that encapsulates this DSL is "Data Interpretation". The program runs in a while loop that continually checks if a key is pressed. When a key is pressed, either the loop will exit or a sound and animation is made and the loop continues. The former case occurs when the user to trying to record/delete layers of sound, before eventually resuming the while loop. A user may press a key that has no behavior defined in the program. This is not really a problem as the program "listens" for certain keys and will simply do nothing when other keys are pressed. 

## Expressiveness
_What should be easy to do in this language? What should be possible, but
difficult? What should be impossible or very difficult?_

It should be very easy to create sequences of sound and animation, whether in real-time or recording "mode". It would be possible but difficult to replicate traditional music as the three rows of a keyboard (only including A-Z) is very different from any instrument. Users used to a piano would have a hard time playing the same songs on a keyboard. 

Altering the same object between layers should generally be impossible as this is both non-intuitive from a user and programmming perspective. Although for objects that persist between layers, I would have to define some rule. For instance, changing the background color between layers should not be allowed. Anything outside of the domain of creating visual music should be impossible.  

## Related work
_Are there any other DSLs in this domain? If not, describe how you know there
aren't and conjecture why not. If so, describe them and provide links. How well 
do they address the need? Are there any particularly admirable qualities of the
language? Are there parts of the language you think could be improved?_

"Right now http://patatap.com/ , which describes itself as a "portable animation and sound kit", does this quite well. There are unique sounds and animations for every letter from A-Z while the spacebar changes the background color. But there are certain things I think could be improved. For one, rather than having the same 26 sounds, it would be cool to be able to swap these out for a different set of sounds. This could allow for many different possibilities like a set where the keys on the left are chords, or a set of drum noises, or a set of hip hop beats and noises. 

The main thing I would want to implement that differentiates it from patatap is the ability to save sequences of sound "layers" and build and add to these layers of sound. Users would be able to save their creations and gradually build up towards a masterpiece." 

- Copied from above

## Suitability
_What percentage of your time do you think will be spent directly engaging in
the **language** aspects of this project (e.g., making language design
decisions), as opposed to "systems" aspects of the project (e.g., implementing a
complicated semantics that doesn't require a lot of language design)?_

I think this project has a 60/40 split: a majority of the time would be spent on implementation (ex: creating unique animations) while the rest would be spent on language aspects like designing the recording part of the project and thinking of unique animations and finding appropriate sounds. 

## Scope
_How big an idea is this? How ambitious is this project?_
I don't think this project is too ambitious. I could have up to 26 animations to design and implement, but the scope is within control - the number of animations and the detail of the animation is up to me. The tricky part is designing the recording aspect and implementing it. 

## Challenges and opportunities
_Why is this a good project? What are some challenges you expect to face? How
might you overcome them? What are some warning signs that the project has gotten
off track, and how will you get the project back on track if needed?_

Besides the recording aspect, the syntax is very straightforward. The challenges would be designing an intuitive way to do the recording part of the project  and thinking of unique animations. There is also the language design choice of how the keys and animations interact (explored in the syntax section, although it relates more to semantics). I think implementing the animations would also be challenging as I am not experienced in this domain, and I may have to learn a JS framework to help with this. 

I think the project has gotten off track if I spend too long on implementing the animations or am not making good progress on the recording aspect. I could shift my priority to the recording aspect and make simpler animations, building on this MVP in the future
