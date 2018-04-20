Recommendations of the Support-Guys
===================================

## TOC

## Introduction
This is a memo, which contains technical and organizational notes about the
Internet based of Ka-Ro electronics. It's structured to follow the spirit/intend
of the [IETF's RFC](rfc-doc) document series.

This is rather lengthy text comprising of some simple explanations and
guidelines of how customers can more efficiently communicate their problems to
Ka-Ro.

Extensions and ideas are welcome. Please use (preferably) the issue tracker or
the support email address, given below.

## Premise
RTFM.

We cannot give you support on basics of GNU/Linux. We assume you are either capable
using a web search engine or to RTFM.

## What kind of information do we require
Premise:

E-Mail subject line should be clear and explanatory and thus should include
the following:

* TX COM
* OS
* Problem in keywords

Example(s):  
From: `TX6Q - Linux - SPI devices not found`  
From: `TX6S - Yocto & Linux 4.4 - Build failed on WLAN`  
From: `TX6DL & QP - Windows EC7 - Monitor flickering`  
From: `TX53 & TX6 - Bootloader/U-Boot - Bricked devices with newest version`  

Do not rehash (reuse) old topics for new problems, even if they stem from the same
line of questioning. One problem solved, new problem arises; i.e. two problems,
two topics.

Do not use HTML mail. The e-mails should be 'Plain-Text' as to keep overhead to a
minimum as well as we see HTML just as what it is, tags and text.

For more about this please read the following references [here](url1), [here](url2)
and [here](url3).


### Dos and Don'ts

* Be concise
* Be pointy
* Be informational
* Attach logs as files
* Give log unique/bijektive filenames


* don't tell stories
  We can't help customers that tell us what they have done, simple as that.
  Customers that tell us their tall tales tend also to make typos in the commands
  instead of just copy paste them.
  Customers that tell us their tall tales tend to have "an error". "An error" that
  has no output, that makes all thing "doesn't work for me". Only appropriate
  answer to that: "It works for us. Try again."

* Provide logs
    - short description of what's:
        - not working
        - what has already been done
        - fdfdf


* don't send URL to download logs from
* don't copy-paste output into the email body and deem it to be a "log"
* don't compress logs

* don't make screenshots from text ouput [1]
*

[1] Text output even when in a VA/VM can be easily captured in it's - so to
speak - "natural from". Either learn to use output redirection or, e.g., of
XTerm's capabilities like "Log to file", which is right there in it's

[VT Options][vt-options]



`Q:` What do we require?  
`A:` Full and complete (boot-)logs. This includes the output from POR
(Power-On-Reset) till, at least, GNU/Linux login prompt and - if applicable
and/or necessary - optionally output from the userspace (everything after the
kernel _is_ userspace), i.e. the procedure in question.

To acquire these users can use the provided

`Q:` *"I would like to use SPI, but it doesn't work as thought."*  
`A:` This is a non-statement. It has no informational value of any kind. It falls
as a statement into the class **"printer doesn't print"** and is in no way,
shape or form helpful. You want us to help you? Be:



should at least provide
the logged output include the following data from the following
points:

- U-Boot
- Linux
- RFS

To do so  of these

U-Boot

## Where to find stuff?
The Ka-Ro BSP is in no way complex. Data, be it documentation or binary files,
in the BSP it follow a categorizing tree structure, like:

    `Flashtools`            <- All flashing tools  
    `Linux`                 <- All directly Linux  
    `Linux/target`          <- All directly Linux - special: binaries for target  
    `Linux/source`          <- All directly Linux - special: sources  
    `Linux/README`          <- All directly Linux - special: README!  

Yes, `README` files, in contrast to MS-DOS naming convention, are text files. More
machines worldwide know how to handle files via magic bytes than there are
MS-Windows machines (using MIME file association).

has a general


## What tools we use and why.
We use:

emacs
console/[CLI](cli)/terminal/XTerm (ugs.)
    grep
    find
    xxdiff
    DDD

shell scripts
tcl scripts

* [`name_ref0`](ref0#da-topic)  <- external file + heading
* [`name_ref0.2`](ref0)         <- external file **ONLY**
* [`name_ref1`][ref1]           <- internal

[Anchor - Headline - of the thing](#footnotes-appendix)

## Why we are, as we are.
Simply put: We reserve us the right to offend.

A good read about that is this:  
http://www.wired.com/2013/07/linus-torvalds-right-to-offend/

***
“Calling things ‘professional’ is... trying to enforce some kind of convention
on others by trying to claim that it’s the only acceptable way,” he wrote,
adding: “I’m sitting in my home office wearing a bathrobe. The same way I’m not
going to start wearing ties, I’m *also* not going to buy into the fake
politeness, the lying, the office politics and backstabbing, the passive
aggressiveness, and the buzzwords. Because THAT is what ‘acting professionally’
results in: people resort to all kinds of really nasty things because they are
forced to act out their normal urges in unnatural ways.”

In an email interview. Torvalds said that he looked forward to talking about
“workflow” issues like this at the Kernel Summit. He added that, while he
didn’t consider himself to be a particularly emotional person, he gets fiery
about the project that bears his name. “It’s maybe easy to forget for
outsiders. I’ve been doing this for 20+ years, and people don’t think about
*why* I’m still doing it,” he wrote. “I care. Deeply.”
***

http://www.wired.com/2013/07/sarah_sharp/

In another interview it is said:

Linus says that “if I’m not the way I am, then people will misunderstand me.”

And that is our line of handling:

* Be direct
* Be unmistakeable
* Be clobbering things that lead to bad habits

OR to put like this:  

We are not here to be your friends! We are here to solve your problems. If that
means to be rude, because you are wasting time either 'cause you act like a
newborn, while having a title, or exhibit bad habits in your way to communicate
or how to present data [1], don't be confounded by us telling you in not so
uncertain words.


using the proverbial
methods, like those of "rubbing the dog's nose in his own poop".


[1] Why would you put captured into something like Word and then create a PDF
    instead of giving the original captured text file is beyond us.
    Also colouring of text is _not_ universal nor is it bijective, interleaved
    posting style is!

---
## Footnotes & Appendix
[rfc-doc]: https://www.ietf.org/rfc.html
[cli](*C*ommand *L*ine *I*nterface)

[ref1]: https://example.com/test
[vt-options]: https://example.com/test

---
[Ka-Ro electronics GmbH](http://www.karo-electronics.de)  
Contact support: support@karo-electronics.de