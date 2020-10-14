# Budd
Timothy Budd's APL Compiler

See the book An APL Compiler by Timothy Budd, (C) 1988 Springer Verlag New York Inc.

Like APL\11, this code has been placed here so that it does not get lost forever.

WARNING ----- WARNING ------ WARNING ------
-------------------------------------------

The APL Compiler is experimental software distributed for your
entertainment and amusement.  The following cautions should be noted:

- It is buggy.  I know it.  I try to fix the bugs when I find them and
when I have time, but often neither one nor the other happens.

- There is no support.  I try to answer reasonable questions when I have
time, but as in number 1 I often don't.

Needless to say, the usual qualifications about there being no guarantees
that this software is suitable for anything at all apply.

In addition, the following problems can be noted

- There is almost no documentation.  The references listed at the end of
this note can help some, reading the source code (like reading apl.lex to
see what the input language is like) can help more, but in general the
outlook is bad.  ONE OF THESE DAYS I hope to find time to write some good
documentation, both for the user level and for the internals (there is a
good bit of pretty mathematics hidden in the algorithms contained herein),
but see notes 1 and 2 (above).

RESTRICTIONS
------------

Here are some of the known restrictions
- laminate isn't implemented
- axis don't work with the catenate operator
- over-take doesn't work, in particular the scalar extension to take isn't done correctly.
- Encode only works with a vector on the left (I'm still not sure I understand the semantics in the larger case).
- intra procedure analysis is incomplete, inter procedure analysis is not working at the moment.
- The branch idiom -> (expression)/Label doesn't seem to work.
- You cannot have an assignment statment inside of a branch.

REFERENCES
----------

L. Guibas and D. Wyatt ''Compilation and Delayed Evaluation in APL'', 
Proceedings of the 5th POPL conference
(describes how transposes and rotations can be executed efficiently)

T. Budd, An APL Compiler, University of Arizona Technical Report 81-17
(describes the first version of the compiler, now very outdated).

T. A. Budd, J. M. Treat
Extensions to Grid Selector Composition and Compilation in APL
Information Processing Letters 19 (1984) 117-123.
(describes how the Guibas algorithms are added to the APL compiler)

INSTALLATION INSTRUCTIONS
-------------------------

- if the apl compiler is to be available to all users, copy the file
aplc.h to /usr/include, or wherever include files are read from.
(as distributed, it is assumed that include files will be read from the
users area.  If the file aplc.h is moved to /usr/include, then the printf
in line 44 of dcls.c should be modified to issue an include in the <> form,
instead of the "" form, as per unix conventions).

- type ''make all'' to make all the sources (this will take half an hour
or so).

- There is a hard path contained in the variable P in the shell script
''aplc''.  Modify this to point to the directory containing the binary
files created in step 2.

- Move aplc to the appropriate bin directory.

- There is a test program ulam.apl, try typing ''aplc ulam.apl'', if this
compiles with no problems, type ''a.out'' to execute.

