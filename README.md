# libcommon

This is a bunch of c source files that provide functionality I use in a lot of my c applications. Much of this code is quite old, but extremely useful.


## Input/output routines.

We have basic input/output routines. I wrote some little variadic functions that are similar to fprintf() in nature but with the added advantage that you can embed ANSI escape codes in your output very easily - something like:

```
   fout(stdout, "Something %`:red`RED%`reset` will %`bright`stand out%`reset`);
```

Where the % is the identifier and the following quoted (backticked) string is an instruction. I'll be uploading a neat little port scanner I wrote in c over the next few days that takes advantage of this and a few other features from this set of libraries.

It basically works like this - the data in the back-ticked string will be either an instruction:

```
   bright
   dim
   underline
   reset
   etc.
```

Or we can embed some : separated colour codes:

```
   %`background:foreground`
```

Both background and foreground properties can be a string or number:

```
   BLACK	0
   RED		1
   GREEN	2
   YELLOW	3
   BLUE		4
   MAGENTA	5
   CYAN		6
   WHITE	7
```

For example:

```
   fout(stdout, "%`white:4`TEXT%`reset`");
```

Would dump blue TEXT on a white background to the console.

Of course, with fout() and relative functions being variadic in nature, we can embed format specifiers within the backticked strings that will expand to a given parameter:

```
   fout(stdout, "Some %`%s:%d`green on red!%`reset", "red", 2);
```

You'll find all of the code in the files:

```
	ansi.h/ansi.c
	fout.h/fout.c
```


## Memory

We also have a library of functions for handling dynamic memory (lists).

There's a lot to cover, here - but the code is fairly self explanitory. There's no linked lists or anything like that - my goal with this module was to provide quick memory allocation and garbage collection. I wanted something as robust and dynamic as arrays in say, php or JavaScript. This neat little library more than fulfils that need. I keep going on about this port scanner! It's on a HD somewhre, it's old but gives a failry decent demo of this library in action...I'll get it uploaded as soon as I find it (or maybe just re-write it, bigger, better - with go-faster stripes!)


## Other...stuff!

We have routines for typical, every day things like handling files, building paths and some routines for parsing and tokenising input data (parse - you could easily build an interpreter with this) as well as routines for handling errors (perr).


## Wrap up

As it's old code that I know like the back of my hand! It's very stable if somewhat archaic in appearance (No comments!) although fairly clean and readable code (as readable as c can be...so pretty!).

Anyway - I might upload some demo programs, including the port scanner, over the next few days. Hopefully someone finds it as useful as I have over the years. Free to do as you like with it - I don't mind, just gimmie a nod and let me know if you do use it, what your experiences were, how it could be improved - or feel free to contribute or criticise!


Michael.
