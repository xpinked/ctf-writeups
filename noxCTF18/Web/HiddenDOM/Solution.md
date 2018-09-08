# HiddenDOM?

One of the challenges i participated with was this Web challege called HiddenDOM,
At first glance in the name i knew some "JavaScript HTML DOM Knowledge"[1] was required, hmm let's see.
[![N|Solid](https://raw.githubusercontent.com/xpinked/ctf-writeups/master/noxCTF18/Web/HiddenDOM/Screenshots/Screenshot_1.png)]

We're getting here a nicelooking story, and a url :3

let's go inside.

[![N|Solid](https://raw.githubusercontent.com/xpinked/ctf-writeups/master/noxCTF18/Web/HiddenDOM/Screenshots/Screenshot_2.png)]

Such a beautiful picure *dazle*

As the usual game, we click on everything,writing jibrish,and trying to see antything we can work with,

oh right.. and opening the source page of course.

Here we go! We have our first lead!

In the source code we see this intresting code
[![N|Solid](https://raw.githubusercontent.com/xpinked/ctf-writeups/master/noxCTF18/Web/HiddenDOM/Screenshots/Screenshot_3.png)]
 
We can see there is an option to write a URL and clicking Check,
By doing soo, We're discovering a GET option in the url
Which looks like that: http://chal.noxale.com:5588/index.php?target=
Lets try to do this thingie:
http://chal.noxale.com:5588/index.php?target=http://chal.noxale.com:5588/index.php

Why? because itd requesting from us to write a URL there.
Why not trying to put the site URL itself?
Hey, Intesting.. look what we got:

[![N|Solid](https://raw.githubusercontent.com/xpinked/ctf-writeups/master/noxCTF18/Web/HiddenDOM/Screenshots/Screenshot_5.png)]

Looks like it Printed in this textarea a part from the html code?
intersting.. maybe we can later use this intersing mechanism.

Lets look around in the interesting looking Javascript we saw in the Source code,

In our first interesting code there are 3 variables which are a bit difficult to understand:

_0x3bc3 , _frss , _xEger

We can see that _0x3bc3 is a list?
and the other variables are using some items from that list.
Some things represents Hexdecimal, and some just for the choise of the coder.

In firefox by clicking on the Keyboard on F12, we can work with a tool called a Console,

which can help us to understand client sided javascript which the page holds.

by working with the console we can understand abit more about them,
by it translating to us humans the meaning.

lets call that variable _0x3bc3 and see what it holds:

[![N|Solid](https://raw.githubusercontent.com/xpinked/ctf-writeups/master/noxCTF18/Web/HiddenDOM/Screenshots/Screenshot_6.png)]

Alright... some human laguage!

lets try to translate the Javascript Code, in our beloved Notepadd++ by putting each name in its called place:
[![N|Solid](https://raw.githubusercontent.com/xpinked/ctf-writeups/master/noxCTF18/Web/HiddenDOM/Screenshots/Screenshot_7.png)]

Alright! We have a DOM!
looking at it we can see there is a input which this script creates,
lets call the most called variable there,
_xEger in our Console, lets see what it dose:
[![N|Solid](https://raw.githubusercontent.com/xpinked/ctf-writeups/master/noxCTF18/Web/HiddenDOM/Screenshots/Screenshot_8.png)]

Intersting indeed, as we saw in our "Translated Code" it actually dose creates a new input which called "expression".
Maybe it works like our previous discovery, "target", maybe its a GET parameter as well?
And also by looking closely we can see that its default input is this string:
" /<[^<>]{1,}hidden[^<>]{1,}>/ "
I donno it looks like some sort of regex?
lets try to add this new discovery to our URL, with a bit of a twist,
instead of its default, lets write that: /<[^<>]{1,}id[^<>]{1,}>/
and lets see what we got.
We try this URL: http://chal.noxale.com:5588/index.php?expression=/<[^<>]{1,}id[^<>]{1,}>/&target=http://chal.noxale.com:5588

[![N|Solid](https://raw.githubusercontent.com/xpinked/ctf-writeups/master/noxCTF18/Web/HiddenDOM/Screenshots/Screenshot_9.png)]

OMG! It Actually changed somthing!
We got a new line, in our previous try we didnt have that line:
 ""\<form action="index.php" id="main_form" style="position:sticky;"\> ""
