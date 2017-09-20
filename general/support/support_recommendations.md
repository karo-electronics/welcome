			Recommendations of the Support-Guys
			===================================
rev. 2016-06-27.01.ow

TOC
---

1) Introduction
2) Where to find stuff?
3) What tools we use and why.
4) Why we are, as we are.


1) Introduction
---------------
This is a memo which contains technical and organizational notes about the
Internet based of Ka-Ro electronics. It's intend follows the IETF's RFC document
series.

This is rather lenghty text comprising of some simple explanations and
guidelines of how customers can more efficiently communicate their problems to
Ka-Ro.

2) What kind of information do we require
-----------------------------------------
Q: I would like to use SPI, yet it doesn't work as thought.
A: This is no statement of any value. This is a statement of the class "printer
   doesn't print" and is no way, shape or form helpful.

We require:
Full and complete bootlogs.
U-Boot commands:
	* `printenv`
	* `fdt print`



2) Where to find stuff?
-----------------------
The Ka-Ro BSP is in no way complex. Data, be it documentation or binary files,
in the BSP it follow a categorizing tree structure, like:

Flashtools		<- All flashing tools
Linux			<- All directly Linux
Linux/target		<- All directly Linux - special: binaries for target
Linux/source		<- All directly Linux - special: sources
Linux/README		<- All directly Linux - special: README!

Yes README files, in contrast to MS-DOS naming convetion, are text files. More
machines worldwide know how to handle that than there are MS-Windows machines.




has a general


3) What tools we use and why.
-----------------------------
We use:

emacs
console
   grep
   find
shell scripts
tcl scripts



4) Why we are, as we are.
-------------------------
Simply put: We reserve us the right to offend.

A good read about that is this:
http://www.wired.com/2013/07/linus-torvalds-right-to-offend/

“Calling things ‘professional’ is… trying to enforce some kind of convention on
others by trying to claim that it’s the only acceptable way,” he wrote, adding:
“I’m sitting in my home office wearing a bathrobe. The same way I’m not going
to start wearing ties, I’m *also* not going to buy into the fake politeness,
the lying, the office politics and backstabbing, the passive aggressiveness,
and the buzzwords. Because THAT is what ‘acting professionally’ results in:
people resort to all kinds of really nasty things because they are forced to
act out their normal urges in unnatural ways.”

In an email interview. Torvalds said that he looked forward to talking about
“workflow” issues like this at the Kernel Summit. He added that, while he
didn’t consider himself to be a particularly emotional person, he gets fiery
about the project that bears his name. “It’s maybe easy to forget for
outsiders. I’ve been doing this for 20+ years, and people don’t think about
*why* I’m still doing it,” he wrote. “I care. Deeply.”

http://www.wired.com/2013/07/sarah_sharp/


In another interview it is said:
Linus says that “if I’m not the way I am, then people will misunderstand me.”

And that is our line of handling:

Be direct
Be unmistakeable
Be clobbering things that lead to bad habits


We are not here to be your friends! We are here to solve your problems. If
that means to be rude, because you are wasting time either 'cause you act like
a newborn while having a title, or exhibit bad habits in your way to communicate
or how to present data [1], don't be confounded by us telling you in not so
uncertain words.


using the proverbial
methods, like those of "rubbing the dog's nose in his own poop".


[1] Why would you put caputred into something like Word and then create a PDF
    instead of giving the orginal captured text file is beyond us.
    Also coloring of text is _not_ universal nor is it bijective, interleaved
    posting style is!

---
## Footnotes & Appendix

---
[Ka-Ro electronics GmbH](http://www.karo-electronics.de)  
Contact support: support@karo-electronics.de
