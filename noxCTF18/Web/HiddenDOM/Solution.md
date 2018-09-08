# HiddenDOM?

One of the challenges i participated with was this Web challege called HiddenDOM,
At first glance in the name i knew some "JavaScript HTML DOM Knowledge"[1] was required, hmm let's see.


We're getting here a nicelooking story, and a url :3

let's go inside.







Such a beautiful picure *dazle*

As the usual game, we click on everything,writing jibrish,and trying to see antything we can work with,

oh right.. and opening the source page of course.

Here we go, we have a lead.

In the source code we see this intresting code

 

And by clicking on the Check button. in the url we can see an option for input in GET parameter called target:

Which looks like that: http://chal.noxale.com:5588/index.php?target=
Lets try to do this thingie:

http://chal.noxale.com:5588/index.php?target=http://chal.noxale.com:5588/index.php

Why? because ?target= requesting from us to write a URL.
Why not trying to put the site URL itself?
Hey, Intesting.. look what we got:



In firefox by clicking on the Keyboard on F12, we can work with a tool called a Console,

which can help us to understand client sided javascript which the page holds.

In our first interesting code there are 3 variables which are a bit difficult to understand:

_0x3bc3 , _frss , _xEger

, some things represents Hexdecimal, and some just for the choise of the coder.
by working with the console we can understand abit more about them,
by it translating to us humans the meaning.
