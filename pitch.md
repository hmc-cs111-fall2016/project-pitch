# Generate Coloring Pages 

## Describe your project in five words
Simple generation of coloring pages.

## Audience
_Who are you helping, with your language? What is that person's
experience like now? How would their experience be better if you could help 
them?_

People who want to color usually buy coloring books, and it's very hard for 
them to find coloring pages of the specific images that they like.
This DSL will allow the users to create coloring pages with any pictures
they already own, that they like. 


## Why a language?
_Why is a **DSL** appropriate for your user(s)? How does it address the need?_

Its domain is very specific in a way that it manipulates images to create coloring pages. Recently there has been an increase in the number of adults who do coloring in their leisure time and they sometimes find themselves having to buy a whole coloring book, even if they are not found of every single page in it, because it contains a few pages they really like. So this DSL would allow the user to create a coloring page with a picture they like, without having to purchase it. 

## Why you?
_What excites you about this idea? How did you come up with it?_

I've recently got into coloring and I've found it very frustrating looking for coloring books, because a lot of them have a few pages that I like but not enough for me to buy the entire book. Also, when I came across great photos or pictures, I wished that I had them in coloring pages version.

## Interface (syntax)
_What kinds of things can the user say in your language. How, generally, do they
say it? **Be as specific as possible.** You don't need to design syntax; but you
should be more specific than "The user describes properties of unicorns.", e.g.,
by describing which unicorn properties (horn color, tattoo, etc.) are most 
important to users and what kinds of values those properties might have._ 

There's going to be a method that takes in a filename of an image as a string,
"generate (String filename)", for example. The image that the user wishes to 
convert into a coloring page has to be in the same directory as the code that 
has this method.
There may be a few different versions of this "generate" method that generates
coloring pages with a different modifications. 
I imagine that the syntax is not going to be that complicated because the main
purpose of this DSL is to convert an image to a coloring page. 


## Operation (semantics)
_What might happen when a program runs? Is there a computational model that
corresponds with your domain? How does a program interact with the
user? What kinds of semantic (i.e., non-syntax) errors might occur, and how 
might they be communicated to the user?_

I imagine the program can be run on the terminal. At first, the user will be 
able to import a picture they already own. This is the part where they can call
the "generate" method, passing on the filename of the image as a parameter. 
The user might find it inconvenient that they can't see the final product of 
their coloring page on the terminal since this program is not interactive that way.


## Expressiveness
_What should be easy to do in this language? What should be possible, but
difficult? What should be impossible or very difficult?_

It should be easy for the user to generate coloring pages with pictures they 
already own. They willalso be able to specify their own arbitrary settings such as removing all colorsfrom the original pictures except purple. However, it would be impossible or very difficult for the user to take a peak on the final product before the program ends. In other words, they wouldn't be able to interact with the final 
product in real-time.


## Related work
_Are there any other DSLs in this domain? If not, describe how you know there
aren't and conjecture why not. If so, describe them and provide links. How well 
do they address the need? Are there any particularly admirable qualities of the
language? Are there parts of the language you think could be improved?_

I had no idea this existed before I just did some research, there's a website 
that allows users to convert photos into coloring pages, 
https://www.reallycolor.com/. I want my DSL to essentially do the same thing, 
but also provide users with different settings such as removing all colorings 
except a certain color.
Also, I find it very inconvenient that this website doesn't offer the service 
for free.

## Suitability
_What percentage of your time do you think will be spent directly engaging in
the **language** aspects of this project (e.g., making language design
decisions), as opposed to "systems" aspects of the project (e.g., implementing a
complicated semantics that doesn't require a lot of language design)?_

Developing language aspects of the project would be time-consuming since 
manipulating colors and other things of photos can be hard. But I don't imagine 
this project needing to integrate with any APIs. And the system part would be 
less time-consuming, since most of it would be converting the picture into a 
sketched veresion of it, possibly in a pdf.

## Scope
_How big an idea is this? How ambitious is this project?_

I think this project is ambitious for me in a way that it's going to require a 
lot of image manipulation, which I've always found hard.


## Challenges and opportunities
_Why is this a good project? What are some challenges you expect to face? How
might you overcome them? What are some warning signs that the project has gotten
off track, and how will you get the project back on track if needed?_

This project is suitable as a DSL class project, since it has a very narrow and 
specific domain. However, the scope of the project might be a barrier because it
 will be very time-consuming and require me to do a lot of self-learning 
 beforehand about image manipulation.
