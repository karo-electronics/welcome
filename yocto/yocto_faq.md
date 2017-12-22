Proudly stolen from:
https://stackoverflow.com/questions/13489332/tracking-variable-assignments-in-bitbake


Tracking variable assignments in bitbake

Ask Question
up vote
9
down vote
favorite
4
I'm using bitbake / openembedded, but my recipe fails because some path-variable ends up being not set correctly I think. Specifically i'm adding files to SRC_URI, but the error indicates the attempt to copy the file is done using the wrong path. Therefore

1) How can I verify the "current" path-variable used when using file:// protocol

2) Given that I somehow confirm which variable is used to search for files, can I track assignments to said variable in my dependency-graph? I mean, bitbake must encounter appends/prepends to the variable in some order in some set of recipe-files, which i would like to inspect in order to find my error

Bonus question: I'm thinking that my current "debug-method" for detecting errors in my recipes is too primitive (e.g. adding -D -D -D to the command-line and subsequently wade through the piles of output to look for hints). How do "professionals" debug their bitbake recipes?

Update: I've found a much better way of debugging my recipes:

It turns out, that after the "fetch" task of a given recipe has successfully completed, the working folder for the recipe is created. Inside this folder is a "temp" sub-folder containing the code executed (e.g run.do_fetch.######) and the results (e.g. log._do_fetch.######) for each task in the recipe.

Inspecting the "run..###" file will tell you the exact value of any variable, and the exact commands/Python-functions executed for the task. The output of a given "run" is stored in the "log..###" file with same id/number as the "run" file. Somehow this very basic information did not register while I read the manual, but now I always look in the "temp" folder when a recipe fails.

openembedded bitbake
shareimprove this question
edited Jan 30 '14 at 14:45
asked Nov 21 '12 at 8:41

S.C. Madsen
3,22341944

Re: "exact value ofany variable": I see only environment variables in these run. files. Not any BitBake variables. I see CFLAGS and RANLIB and things like that; I don't see WORKDIR, or S, or FILESEXTRAPATHS or whatever. – Kaz Apr 5 at 18:14
add a comment
3 Answers
active oldest votes
up vote
14
down vote
accepted
I presume you've discovered bitbake -e, right? That dumps the environment specific to a single bitbake "target" (ie. a recipe.) I believe FILESPATH is the key variable that bitbake uses to find files specified in a file:// SRC_URI component. Using bitbake -e (recipe) | grep ^FILESPATH= will display that very large path variable!

I don't know of a way to track assignments to that variable, but there are several ways to modify it. (Actually I recall a bitbake patch which would annotate the output of bitbake -e with what file modified which variable but can't recall the details. Ask on the oe list.) In any case, if you remove the '=' sign from the grep above you can see the other ways FILESPATH can be modified. I think this is covered in the various docs, as well.

Finally, you may have better luck asking on the openembedded mailing list, rather than here on stackoverflow.

Bitbake -e and the log files (found in ${WORKDIR}/temp) are your best debug tools. (Also check out ack-grep. Better than grep for some bitbake-related use cases.) Where is WORKDIR you ask?

bitbake -e (recipe) | grep ^WORKDIR=

Once you get familiar with WORKDIR, you'll see the pattern and won't have to find it that way.

Happy baking! ;)

shareimprove this answer
answered Nov 21 '12 at 23:22

challinan
1,424810

Yes, I'm using -e to view the results. But the results between two of my recipes differ, and I cannot see why in the dumped environment. – S.C. Madsen Nov 22 '12 at 14:17

I somehow missed, that you mentioned the "WORKDIR/temp" folder in your answer. Discovering the "temp" folder has been a real eye-opener for me, and has greatly improved my success-rate with bitbake. Thanks! – S.C. Madsen Jan 30 '14 at 14:48
add a comment
up vote
1
down vote
Turns out, that there is a patch for doing this in later versions of BitBake, its just not supported in the one I'm currently using :-(

shareimprove this answer
answered Dec 19 '12 at 13:15

S.C. Madsen
3,22341944

Hi, S.C., Can you be specific which patch and how you use it? I'm looking for the same solution. – minghua Oct 28 '13 at 21:37
1	 	
@minghua I'm sorry but I've forgotten where I found the patch. Found via Google searching for clues to debugging bitbake. – S.C. Madsen Nov 5 '13 at 17:06
add a comment
up vote
0
down vote
I would suggest using Toaster, in interactive mode. In the configuration page, you can track variable assignment history.

The mockup is here: https://www.yoctoproject.org/toaster/build-configuration.html

To use it, run "source toaster start" after "source oe-init-build-env" and in the web interface you will find data logged from your builds.

Hope this helps, Alex

shareimprove this answer