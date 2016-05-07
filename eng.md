<section name="261d" class=" section--body section--middleCenter section-image--
aspectRatioViewport is-imageBackgrounded is-backgrounded is-darkBackgrounded 
section--first is-aboveSectionCaption" score="47.5
"></section><section name="3aa3" class=" section--body" score="41.25">Before we
get into this, allow me to introduce myself — you’re probably going to wonder 
who I think I am before this is over.

I’m **Eric Elliott**, author of **“Programming JavaScript Applications”** **(O
’Reilly
)**, host of the *feature-length documentary film-in-production,* **“
Programming Literacy
”**, and creator of the [**“Learn JavaScript with Eric Elliott”**][1]** **
series of online JavaScript courses.

I have contributed to software experiences for **Adobe Systems, Zumba Fitness,
The Wall Street Journal, ESPN, BBC,**and top recording artists including **
Usher, Frank Ocean, Metallica,** and many more.

I was trapped in the darkness. I was blind — shuffling about, bumping
into things, breaking things, and generally making an unholy mess of everything 
I touched.

In the 90's, I was programming in C++, Delphi, and Java and writing 3D plugins
for the software suite that eventually became Maya (used by lots of major motion
picture studios to make summer blockbuster movies
).

Then it happened: The internet took off. Everybody started building websites,
and after writing and editing a couple online magazines, a friend convinced me 
that the future of the web would be SaaS products (before the term was coined). 
I didn’t know it then, but that subtle course change transformed the way I think
about programming on a fundamental level, because*if you want to make a good
SaaS product, you have to learn JavaScript.*

Once I learned it, I never looked back. Suddenly, everything was easier. The
software I made was more malleable. Code survived longer without being rewritten.
Initially, I thought JavaScript was mostly UI scripting glue, but when I learned
cookies and AJAX blew up, that transformed, too.

I got addicted, and I couldn’t go back. JavaScript offers something other
languages lack:

> Freedom!
JavaScript is one of the most important programming languages of all time, not
simply because of its popularity, but because it popularized two paradigms which
are extremely important for the evolution of programming:

*   **Prototypal Inheritance **(objects without classes, and prototype
    delegation, aka OLOO — Objects Linking to Other Objects), and
   
*   **Functional Programming **(enabled by lambdas with closure)

Collectively, I like to call these paradigms **the two pillars of JavaScript,**
* *and I’m not ashamed to admit that they’ve spoiled me. I don’t want to
program in a language without them.

*JavaScript will be remembered as one of the most influential languages ever
created.* Lots of other languages have already copied one or the other, or both
of the pillars, and the pillars have transformed the way we write applications,
*even in other languages.*

Brendan Eich didn’t invent either of the pillars, but JavaScript exposed the
programming masses to them. Both pillars are equally important, but I’m 
concerned that a large number of JavaScript programmers are completely missing 
one or both innovations, because JavaScript is pretty good at letting you code 
poorly if you don’t bother to learn it properly.

This is actually a feature, because it makes it really easy to pick up
JavaScript and start doing useful things with it, but that phase of your 
development as a JavaScript programmer*should last no more than a year.*

If you haven’t yet, **it’s time to level up.**

If you’re creating constructor functions and inheriting from them, you haven
’t learned JavaScript. It doesn’t matter if you’ve been doing it since 1995. You
’re failing to take advantage of JavaScript’s most powerful capabilities.

***You’re working in the phony version of JavaScript that only exists to
dress the language up like Java.***

You’re coding in this amazing, game-changing, seminal programming language
and*completely missing what makes it so cool and interesting.*

> “Those who are not aware they are walking in darkness will never seek the
> light.” ~ Bruce Lee
>
**Constructors violate the open/closed principle** because they couple all
callers to the details of how your object gets instantiated. Making an HTML5 
game? Want to change from new object instances to use object pools so you can 
recycle objects and
[stop the garbage collector from trashing your frame rate?][2] Too bad. You’
ll either break all the callers, or you’ll end up with a hobbled factory 
function.

If you return an arbitrary object from a constructor function, it will break
your prototype links, and the*\`this\`* keyword will no longer be bound to the
new object instance in the constructor. It’s also less flexible than a real 
factory function because you can’t use*\`this\`* at all in the factory; it just
gets thrown away.

Constructors that aren’t running in strict mode can be downright dangerous,
too. If a caller forgets*\`new\`* and you’re not using *strict mode* or *ES6
classes* *[sigh]*, anything you assign to *\`this\`* will pollute the global
namespace. That’s ugly.

Prior to strict mode, this language glitch caused hard-to-find bugs at two
different startups I worked for, during critical growth periods when we didn’t 
have a lot of extra time to chase down hard-to-find bugs.

In JavaScript, **factory functions** are simply constructor functions ***minus*
** the ***\`new\` *requirement,** **global pollution danger** and **awkward
limitations** (including that annoying initial capitalized letter convention
).

**JavaScript doesn’t need constructor functions** because *any function can
return a new object.*With dynamic object extension, object literals and `*
Object.create
()`, *we have everything we need — with none of the mess. And *\`this\`*
behaves just like it does in any other function. Hurray!

> “Quite frequently I am not so miserable as it would be wise to be.” ~ T.H
> . White
>
Everyone has heard the boiling frog analogy: If you put a frog in boiling water
, it will jump out. If you put the frog in cool water and gradually increase the
heat, the frog will boil to death because it doesn’t sense the danger. In this 
story, we are the frogs.

If *constructor* behavior is the *frying pan*, ***classical inheritance*** isn
’t*the fire;* ***it’s the fire from Dante’s seventh circle of hell.***

> “The problem with object-oriented languages is they’ve got all this
> implicit environment that they carry around with them. You wanted a banana but 
> what you got was a gorilla holding the banana and the entire jungle.” ~ Joe 
> Armstrong
>
Classical Inheritance generally lets you inherit only from a single ancestor,
forcing you into awkward taxonomies. I say awkward because without fail,*every
OO design taxonomy I have ever seen in a large application was eventually wrong.
*

Say you start with two classes: *Tool* and *Weapon*. You’ve already screwed
up
 — *You can’t make the game “Clue.”*

*The coupling between a child class and its parent is the tightest form of
coupling in OO design.*That’s the opposite of reusable, modular code.

Making *small changes *to a class creates *rippling side-effects *that break
things that should be completely unrelated.

The obvious solution to taxonomy troubles is to go back in time, build up new
classes with subtle differences by changing up what inherits from what — but it’
s too tightly coupled to properly extract and refactor. You end up duplicating 
code instead of reusing it. You violate the**DRY** principle (Don’t Repeat
Yourself
).

As a consequence, you keep growing your subtly different jungle of classes, and
as you add inheritance levels, your classes get more and more arthritic and 
brittle. When you find a bug, you don’t fix it in one place.*You fix it
everywhere.*

> “Oops. Missed one.” — Every Classical OO programmer, ever.
This is known as **the duplication by necessity problem **in OO design circles
.

[**ES6 classes don’t fix any of these problems.**][3]** **ES6 makes them worse
, because these***bad ideas ****will be officially blessed by the spec, *and
written about in a thousand books and blog posts.

**The *\`class\` *keyword will probably be the most harmful feature in
JavaScript.**I have enormous respect for the brilliant and hard-working people
who have been involved in the standardization effort, but even brilliant people 
occasionally do the wrong thing. Try adding .1 + .2 in your browser console, for
instance. I still think Brendan Eich has contributed greatly to the web, to 
programming languages, and to computer science in general.

P.S. Don’t use *\`super\` *unless you enjoy stepping through the debugger into
multiple layers of inheritance abstraction.

These problems have a multiplying effect as your application grows, and
eventually, the only solution is to rewrite the application from scratch or 
scrap it entirely — sometimes the business just needs to cut its losses.

I have seen this process play out ***again****, and ****again****, ****job****
after****job****, ****project**** after ****project****.* *Will we ever learn
?*

At one company I worked for, *it caused a software release date to slip by an
entire year for a rewrite.* I believe in **updates, not rewrites.** At another
company I consulted for,*it almost caused the entire company to crash and burn
.*

> **These problems are not just a matter of taste or style. This choice can
> make or break your product.
>**
Large companies can usually chug along like nothing is wrong, but startups can
’t afford to spin their wheels on problems like these while they’re struggling 
to find their product/market fit on a limited runway.

***I’ve never seen any of the problems above in a modern code base that
avoids classical inheritance altogether.***

> “Perfection is reached not when there is nothing more to add, but when
> there is nothing more to subtract.” ~ Antoine de Saint-Exupéry
>
A while back, I was working on a library to demonstrate how to use prototypal
inheritance for my book,[“Programming JavaScript Applications”][4] (O’Reilly
), when I settled on an interesting idea: a factory function that helps you 
produce factory functions that you can inherit from and compose together. I 
called the composable factories “stamps,” and the library, “Stampit.” The 
library is very small and simple. I gave a talk about Stampit at the O’Reilly 
Fluent Conference in 2013 (included here at the end of the article), and wrote a
blog post about stamps (see below
).

There is a small, but steadily growing community of developers whose coding
styles have been transformed by stamps. Stampit is in production use in multiple
apps with millions of monthly active users.<figure name="d01f" id="d01f" class
="graf--figure graf--layoutInsetLeft graf-after--p" score="-12.5
">

![][5]</figure>

> “I have been using Stampit a lot and really enjoy the power afforded by the
> simplicity in the separation of concerns between the types of prototypes as well
> as composable nature of stamps. Classical deep inheritance trees always bothered
> me, especially in the context of web development where business needs are often 
> a moving target. The above mentioned talk and Stampit have inspired different 
> thinking and allow me to do things that feel like interfaces without the 
> overhead, or inherit private data with privileged methods from multiple sources.
> My prototypal inheritance is now strong, my objects have become shapeless, 
> formless, like water. Keep up the great work, class sugar has nothing on this.
> ” ~ Justin Schroeder, Senior Developer, Wrecking Ball Media Group
>
Stampit isn’t the only alternative, of course. Douglas Crockford doesn’t use **
*\`this\`* at all, instead opting for an entirely functional approach to code
reuse.

All his objects are just stateless bags of functions, or data-only objects like
associative arrays with no methods. This works well unless you’re creating a 
hundreds of thousands of objects and you need your app to perform smoothly at or
near realtime (think game engines, realtime signal processors, etc…). In those 
situations, delegating calls to methods can save you from a lot of manual memory
management.

Other good alternatives include making better use of JavaScript modules as an
alternative to inheritance (I recommend npm and ES6 modules with Browserify or 
WebPack), or simply cloning objects by copying properties from a source object 
to a new object (e.g.*\`Object.assign()\`*, *\`$.extend()\`, \`_.extend()\`,*
etc
…).

The copy mechanism is another form of prototypal inheritance. Sources of clone
properties are a specific kind of prototype called**exemplar prototypes, **and
cloning an exemplar prototype is known as**concatenative inheritance.**

Even if you follow Douglas Crockford’s advice and stop using *\`this\`, *you
can still do things the prototypal way. Concatenative inheritance is possible 
because of a feature in JavaScript known as**dynamic object extension: **the
ability to add to an object after it has been instantiated.

**You never need classes in JavaScript,** and I have never seen a situation
where class is a better approach than the alternatives. If you can think of any,
leave a comment, but I’ve been making that challenge for years now, and*nobody
has come up with a good use-case* — just flimsy arguments about micro-
optimizations or style preferences.

When I tell people that constructors and classical inheritance are bad, they
get defensive.*I’m not attacking you. I’m trying to help you.*

People get attached to their programming style as if their coding style is how
they express themselves.*Nonsense.*

> What you make with your code is how you express yourself.
How it’s implemented doesn’t matter **at all** *unless it’s implemented
poorly.*

> The only thing that matters in software development is that your users love
> the software.
>
I can warn you that there’s a cliff ahead, but some people don’t believe
there is danger until they experience it first hand. Don’t make that mistake;*
the cost can be enormous.* **This is your chance** to learn from the mistakes
that countless others have made*again* and *again* over the span of *decades.*
Entire books have been written about these problems.

The seminal [“Design Patterns” book by the Gang of Four][6] is built around two
foundational principles:

*“Program to an interface, not an implementation,”* and *“favor object
composition over class inheritance.
”*

Because child classes code to the implementation of the parent class, the
second principle follows from the first, but it’s useful to spell it out.

> The seminal work on classical OO design is anti-class inheritance.
It contains a whole section of object creational patterns that exist solely to
work around the limitations of constructors and class inheritance.

Google *“new considered harmful,” “inheritance considered harmful,”* and *“
super is a code smell.
”* You’ll dig up dozens of articles from blog posts and respected
publications like Dr. Dobb’s Journal dating back to before JavaScript was 
invented, all saying much the same thing:*\`new\`*, brittle classical
inheritance taxonomies, and parent-child coupling (e.g.*\`super\`*) are recipes
for disaster.

*Even James Gosling, the creator of Java, admits that Java didn’t get objects
right.*

Want to stick with JavaScript references? [Douglas Crockford][7] got *Object.
create
()* added to the language so he wouldn’t have to use *\`new\`*.

Kyle Simpson (author, [“You Don’t Know JS”][8]) wrote a fascinating three part
blog series on the topic called[“JS Objects: Inherited a Mess.”][9]

Kyle argues that prototypal inheritance is anti-class, that’s simpler and
better than class. He even coined the term**OLOO** (Objects Linked to Other
Objects) to clarify the distinction between prototype delegation and class 
inheritance.

> “Simplicity is about subtracting the obvious and adding the meaningful
> .” ~ John Maeda
>
*   **Gets simpler** (Easier to read and to write. No more wrong design
    taxonomies.
    )
*   **Gets more flexible** (Switch from new instances to recycling object pools
    or proxies? No problem.
    )
*   **Gets more powerful & expressive** (Inherit from multiple ancestors?
    Inherit private state? No problem.
    )

> “If a feature is sometimes dangerous, and there is a better option, then
> always use the better option.” ~ Douglas Crockford
>
I’m not trying to take a useful tool away from you. I’m warning you that *what
you think is a tool is actually a foot-gun.* In the case of constructors and
classes, there are*several better options.*

Another common argument that programmers use is that it should be up to them
how they express themselves, as if code style rises to the level of art or 
fashion. This argument is a purely emotional and irrational:

*Your code isn’t the product of your self expression any more than a painter
’s paintbrush is the product of their self expression.****Code is the tool. The
program is the product.***

Yes, *some code is art in and of itself,* but if it doesn’t stand alone
published on paper,***your code doesn’t fall into that category.**** *Otherwise
, as far as your users are concerned,*the code is a black box, and what they
enjoy is the program.*

Good programming style requires that when you’re presented with a choice that
’s elegant, simple, and flexible, or another choice that’s complex, awkward, and
restricting, you choose the former. I know it’s popular to be open minded about 
language features, but*there is a right way and a wrong way.*

**Choose the right way.**

*~ Eric Elliott*

P.S. Don’t miss 
[The Two Pillars of JavaScript Part 2: Functional Programming (How to Stop Micromanaging Everything)][10]

 [1]: http://ericelliottjs.com/
 [2]: https://www.youtube.com/watch?v=RWmzxyMf2cE
 [3]: https://medium.com/p/how-to-fix-the-es6-class-keyword-2d42bb3f4caf

 [4]: http://www.amazon.com/gp/product/1491950293?ie=UTF8&camp=213733&creative=393185&creativeASIN=1491950293&linkCode=shr&tag=eejs-20&linkId=ZURITP6JDCUKP6QF
 [5]: img/1*6432XLMVYjpOCisNaKEBgw.jpeg

 [6]: http://www.amazon.com/gp/product/0201633612?ie=UTF8&camp=213733&creative=393185&creativeASIN=0201633612&linkCode=shr&tag=eejs-20&linkId=5S2XB3C32NLP7IVQ
 [7]: https://www.youtube.com/watch?v=bo36MrBfTk4

 [8]: http://www.amazon.com/s/?_encoding=UTF8&camp=213733&creative=393193&linkCode=shr&tag=eejs-20&linkId=YSQEZLRZIRKYVBNS&rl=search-alias%3Daps&field-keywords=you%20don%27t%20know%20js&sprefix=you+don%27t+know+js%2Caps
 [9]: http://davidwalsh.name/javascript-objects
 [10]: http://bit.ly/jspillars2