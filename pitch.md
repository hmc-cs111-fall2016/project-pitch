# LED composing (replace me)

## Describe your project in five words

Easily compose LED color effects

## Audience
_Who are you helping, with your language? What is that person's
experience like now? How would their experience be better if you could help 
them?_

With my language I am trying to help the casual "maker" or LED user more easily
design LED compositions and color effects without having to know a lot of CS
or C coding. Currently, most users of LED strip lights use the default remote 
control that comes with the lights because they don't know how to code anything
better. This remote allows for a classic fade effect or just picking a color 
and leaving it there. To upgrade, someone would have to use a library for
Arduino or Raspberry Pi that is written in C. They would have to know how 
loops and other control flow works and be very comfortable with all the syntax 
of C. For example, to create a function that sends a single color down the LED 
strip, someone would currently have to code:
```
// Cascades a single direction. One time.
void cascade(unsigned long color, byte wait)
{
    for (int i=0; i<LED_COUNT; i++)
    {
      clearLEDs();  // Turn off all LEDs
      leds.setPixelColor(i, color);  // Set just this one
      leds.show();
      delay(wait);
    }
  

}
```
To someone who codes quite often, it is understandable; however, 
to a more casual user, this quickly becomes confusing and is not natural.
If I could help them, their experience would hopefully be better because I
would try and abstract the control flow and C syntax. My current plan would be
to only allow higher order LED control (cascade effect, wave effect etc..)
over single LED control - single LED control invites/requires loops more often-
to make things easier.

## Why a language?
_Why is a **DSL** appropriate for your user(s)? How does it address the need?_

The only way to interact with LEDs presently is through C (well Arduino & C) so 
a language is definitely appropriate. A language also addresses the need by 
allowing someone to easily compose smaller effects into larger compositions
by nature of language design - many languages have the property of creating
larger functions using smaller helper functions to organize code. 
Also, To create whatever design/controls a user likes, I think a language is 
necessary because there are many features to take advantage of that a simple 
user interface could not effectively handle.

## Why you?
_What excites you about this idea? How did you come up with it?_

I really like LED strip lights (I have them in my room and am working on putting
them on my longboard and car) but dont like how the main feature is fading colors and  
going from one color to another. I want to grow this technology to allow 
for more complex light creations. For example, I would love for them to be composed into complex lighting designs similar to music but with lights. I 
came up with this idea at 4 am talking with a friend about how fun LED lights 
are. I had just ordered more and my friend complained about how they were too 
repetitive. I realized maybe that could be fixed and then double realized that 
maybe a DSL is the right idea. 

I also was further excited by LEDs last Friday at MuddHacks where my roomate
and I tried to create an LED display for our suite, which sadly does not work
yet - partially because it is hard to code the LEDs properly.



## Interface (syntax)
_What kinds of things can the user say in your language. How, generally, do they
say it? **Be as specific as possible.** You don't need to design syntax; but you
should be more specific than "The user describes properties of unicorns.", e.g.,
by describing which unicorn properties (horn color, tattoo, etc.) are most 
important to users and what kinds of values those properties might have._ 

For now, and possibly always, I want to focus this language on beginners.
With that in mind, I think the user will only be able to describe a few higher
level LED actions like cascade, wave, fade, flash, and strip color. Various
commands will require different properties but some would be color of the
action (or range of colors for fade etc.), for how long the action should last,
the brightness of the LEDs, and how wide the action should be - a 6 led wide 
cascade or a single led etc.

The value of the properties vary but time will be a length in seconds or 
minutes or both. Color will either be a single RGB/HSV/HSL color or a range of 
them and width will be an integer. 

Additionally, there will be a way connect one composition to another. Similar
to a `Jump` in Assembly, this will be the main way of connecting smaller
compositions together into a more complex one. 

## Operation (semantics)
_What might happen when a program runs? Is there a computational model that
corresponds with your domain? How does a program interact with the
user? What kinds of semantic (i.e., non-syntax) errors might occur, and how 
might they be communicated to the user?_

This seems to be similar to a Data interpretation computational model. 
Theoretically when a program runs the first task will be to build the code for
each block of code. Then it will piece this code together based on what the user
states to be run. This would compile the language into Arduino machine code for
use on an Arduino to control the LEDs. There could definitely be a lot of
Arduino errors like issues connecting to the device, sending incorrect color 
values to the leds, or C errors like SEGFAULT, which would all probably be 
communicated to the user through a console of sorts.



## Expressiveness
_What should be easy to do in this language? What should be possible, but
difficult? What should be impossible or very difficult?_

It should be easy to set up a simple program using one of the "higher LED actions." It should also be easy to set its color, and display time. It should
be possible to chain together these actions into more complex compositions.
Also, it should be possible but difficult to create other "higher LED actions"
out of the lower level actions. For now, it should be impossible or very
difficult to control single LEDs and to use any sort of control flow while
creating the effects. 

## Related work
_Are there any other DSLs in this domain? If not, describe how you know there
aren't and conjecture why not. If so, describe them and provide links. How well 
do they address the need? Are there any particularly admirable qualities of the
language? Are there parts of the language you think could be improved?_

The only information I could find is that to control these lights you must use 
Arduino or Raspberry Pi code to control the wire outputs for the LEDs. I would 
not consider thisa  DSL in my domain but rather a DSL in the domain of all 
electrical engineering projects. I think the reason why there hasnt been a DSL 
is either because those interested in the domain are okay using the regular 
Arduino code or because it is quite a specific domain so it doesnt seem likely 
to have languages created for it. 

Here is a link to the arduino library for addressable LEDs 
https://learn.adafruit.com/adafruit-neopixel-uberguide/arduino-library 
which really shows the complexity of the language. 


## Suitability
_What percentage of your time do you think will be spent directly engaging in
the **language** aspects of this project (e.g., making language design
decisions), as opposed to "systems" aspects of the project (e.g., implementing a
complicated semantics that doesn't require a lot of language design)?_

I think that a lot (most maybe) of this project will be working on the **
language** aspects. Once the back end methods of creating a fade function/color 
change function/etc.. are completed, the rest will be trying to design the 
language in a way that promotes chaining commands and easily integrates aspects 
of looping and time to allow for complex light effects. I have already come up 
with a few options but picking the right one is difficult because there are 
lots of trade-offs to think of. 


## Scope
_How big an idea is this? How ambitious is this project?_

This project could be quite ambitious. There are lots of features that could be 
made for the user and it is easy to get lost in "feature creating land" instead 
of language design land. However, I also think the scope is not too large since 
it focuses on a relatively specific domain. 

## Challenges and opportunities
_Why is this a good project? What are some challenges you expect to face? How
might you overcome them? What are some warning signs that the project has gotten
off track, and how will you get the project back on track if needed?_

This could be a great idea for a project since it is very fun, allows for a lot 
of language design choices, and is mainly designed around allowing the user to 
create complex creations out of simple code. This might not be a good idea 
because it technically requires working with Arduino/Raspberry pi (even though 
this part could realistically be ignored) and because it might be too specific 
of a domain that it really is just useful for me and not a whole lot of others. 

