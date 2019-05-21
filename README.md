# +/∞

plus over infinity, a crash course in k

**[genesis](#genesis)**

* k → [ø](#ø) | [who](#who) | [why](#why) | [wha](#wha) | [how](#how)

**[exodus](#exodus)**

* [get](#get) | [run](#run)
* style → [cmt](#style-annot) | [sep](#style-sep) | [tab](#style-ident) | [ids](#style-name) | [time](#style-space) | [bad](#style-bad)
* parlance → [xyz](#parl-xyz) | [rank](#parl-rank)

**[numbers](#numbers)**

* vector math → [v≠a](#vectors-vs-atoms) | [v+v](#v-plus-v) | [v+a](#v-plus-a) | [v x](#v-indexing)  | [shp](#v-shp)
* [type system](#two-types-of-types) → [\`i\`f](#typ-num) | [\`c\`n](#typ-char) | [\`d\`t](#typ-time) | [\`1\`2](#typ-lambda) | [mix](#typ-mix) | [cst](#typ-cast)
* order of eval → [rtl](#right-to-left-and-back-again) | [(1)2](#rtl-precedence)
* verb+adverb → [nsl](#no-stinking-loops)

**[proverbs](#proverbs)**

* reading code → [how](#how-to-solve-it)

---------------------

## genesis

### ø

Computer languages have been around, but in the beginning was the wørd. We will 
be writing code in a language called k, but it helps to talk about it first.

**k is different**. At first, you will be questioning its design, and it will 
respond by questioning things that you consider common sense, but soon it will 
become a constructive conversation, and here is how. The first thing newcomers 
frown upon is why the assignment operator is `:` instead of `=`. But before you 
close the tab, try a simple thought experiment. Consider the following code:

```java
x = x + 1
```

Most programmers will agree that this expression makes perfect sense, but if 
you show it to a math guy, be ready to hear "no, it isn't". And once you see 
what makes him think that way, you will also see why we assign values with `:` 
in k. The above expression looks nonsensical to a k programmer for the same 
reason it is to a math guy, and k will most always evaluate it to false. It is 
possible to produce a k expression where `x=x+1` evaluates to true, and once 
you can, please submit a pull request and say "hello".

k has a different perspective on some other things as well, but it is not 
necessarily wrong. It can just as well be right, but in a different way, and 
this short introduction invites you to look at those things that other way. And
we hope they might also feel obvious and natural to you, like `x≠x+1` just did.

---------------------

This crash course is not looking to make you an expert k programmer, because 
that takes a lot of time and effort. It aims to give enough confidence and 
motivation for you to continue on your own. We value your time, so we promise 
it will be fast and violent.

* The text cuts a lot of corners on general programming and CS at some expense 
  of readability.
* The course is driven entirely by densely annotated code, comments contain 
  essential material.
* New syntax is often introduced inline, some assumed self-explanatory, some 
  relies on your intuition.
* The narrative is linear, each chapter builds on all previous.
* Skipping exercises will halt your progress.

This might feel a bit intense, but we hope the course is still lightweight enough
to be completed in one session.

This document is **not a k reference**. The majority of subjects are covered at
depth sufficient to give a general overview and encourage further research but 
by no means exhaustive.

### who

The man behind k is a computer scientist by the name Arthur Whitney. He is the 
principal designer of the language, and he is an iconic figure in a community 
of some of the most sophisticated programmers and scientists employed by some 
of the most influential institutions on the planet. Since early 90s, he delivers
ever more powerful revisions of a concept he has been refining throughout his 
career, a system to build very efficient software that transforms large amounts 
of data into large amounts of money.

That is, k enjoys much success in the world of finance, where this kind of 
problems existed long before the term **big data** was coined. Many people 
embraced the k way and made successful careers by building solutions using k, 
and they appreciate their tool as much as they appreciate the man behind it, 
and we believe they have their reasons.

### why

There is a good chance that you have heard or read about k language. A lot of 
people know the story. What is much less likely is that you have ever met a 
professional k programmer. This happens not just because k programmers are 
rare — there are separate reasons for that, mostly because k is never fishing 
for cheap publicity. This is how we all heard about a language called k, but 
what we hear more often is how much it sucks to be a Java programmer.

Jokes aside, implementations of similar systems in languages like C++ or Java 
usually involve thousands of lines of code written by large teams, built on top 
of complex library stacks and even more complex infrastructure. Such projects
are expensive and inflexible, often go out of budget and miss deadlines.

In comparison, k solutions are typically a few factors of magnitude less code,
implemented by small and agile teams, rarely require external dependencies, and 
ship on time. 

At first it could be hard to understand how this can even be true, but compare 
the effort of keeping 100 lines of code in sync with rapidly changing 
requirements and free of bugs, compared to 10,000 lines of code that do the 
same thing. Against all intuition, it is not 100 times easier, but 10,000 times
easier, and that is the effect of cyclomatic complexity.

### wha

k is an expressive, simple and powerful computer language.

The power stems from the fact that k is designed as a *tool of thought*. The 
vocabulary, syntax and the choice of abstractions offered by the language drive 
you to think about problems in a focused and clear way that quickly takes you 
to efficient and elegant solutions. And the reason why thinking in terms of k 
is so effective is nothing supernatural: brevity is a soul of wit.

k programs are concise, the syntax of the language is terse, and there is no 
boilerplate code to write. In k, most of the time is spent on thinking about 
the problem rather than writing and refactoring code or browsing source.

### how

k interpreter is incredibly compact and efficient runtime environment. The 
entire system is:

* a single binary executable
* without any external dependencies
* that fits in the cache of your CPU

And that gives a selection of fundamental algorithms, data structures, 
techniques and primitives that withstood the test of decades of production use 
in some of the world's most demanding data processing environments, where 
inefficiency directly translates into loss of revenue. The inner components 
of the system are polished to fit together and complement each other to deliver 
top performance. It is also not uncommon for k newcomers to experience shock 
when they first see how much can be done with a few precise keystrokes, and
how fast.

All of k programming takes place in **REPL**, an idea that is actually much 
older than many seem to think. It has been around for at least half a century, 
and is known as *dialogue approach*, a live conversation between a human and 
machine as a flow of questions and answers. And in k, this conversation is much 
more fluent than in any other modern REPL-driven system you may be familiar 
with, because the questions are short and the answers are fast. This is the 
essence of the way of k, an experience that all k programmers consider 
immensely satisfying. This is why people who write software in k love 
their jobs.

## exodus

Since the only known way to learn how to program is to write programs, you will
need a live k environment. Fortunately, as all things k, it takes very little 
effort.

### get

We will use a trial version of k, which comes with a reasonable limit of 1 
gigabyte of workspace per k process. This limit is for your own protection, so 
that you don’t accidentally convert too much data into too much money too early, 
because, as any k programmer will tell you, with great power comes great 
responsibility.

The k interpreter is currently available for `Linux` and `macOS` on `x86_64` 
architecture.

Without further ado, go to https://anaconda.org and follow the instructions. 
Anaconda shell integration option is recommended. Once you install Anaconda, 
install the package called `shakti`, which is nothing else but `k` in disguise:

```sh
conda install -c shaktidb shakti
```

As all things k, the development of k language itself is happening at 
terrifying pace. New builds are published up to several times a week, so 
make sure you always use the latest version:

```sh
alias kup="conda update -c shaktidb shakti"
kup
```

### run

Assuming conda's `bin` is in your PATH, Start your very first k session like so:

```sh
$ k
2019-04-21 15:38:18 40core 512gb avx2 © shakti m2.0 prod
 █
```

There isn't much to write home about, so lets take a look at the startup 
banner. It packs a lot of useful information:


| it says             | it means                      |
| :-------------------|:------------------------------|
| 2019-04-21 15:38:18 | timestamp of your k build     |
| 40core              | cpu cores you can use in k    |
| 512gb               | max workspace, expect 1gb     |
| avx2                | the best your cpu can do      |
| shakti              | the company behind k          |
| m                   | `m` for macos, `l` for linux  |
| 2.0                 | because it is better than 1.0 |
| prod                | your build is `test` for now  |

If it ever comes to that, always include your banner in your bug reports.

At any time during k session, you can:

`\h` view k reference card

`\l` view k change log

`\\` quit k session

However, at this point we highly recommend to avoid issuing any of the above 
commands, especially the latter.

---------------------

**Practice:**

* Make sure you have `rlwrap` utility installed, and put an alias 
  `alias k="rlwrap k"` into your rc file. This makes your minimalistic k 
  development environment a lot more pleasant to use.

* Type in your first k expressions, and enjoy your first answers:

```q
 2+2            /simplest face of k is a calculator
4

 x:42           /: is assign so x is now the answer
 x=x+1          /= is equal, and of course it isn't
0

 +/∞            /we knew you would want to try that
∞               /and guess what, it happens to be ∞
```

---------------------

Unfortunately, we are not equipped to discuss much of that yet, but the lesson 
wasn't fruitless, and `+/∞` actually makes a lot of sense, the meaning is very 
simple and only few pages away.

### remarks on style

As any other language, k expects a programmer to observe and follow certain 
conventions on coding style and terminology in order to understand the 
code written by the others and let their own code be understood. While some 
rules of the house of k are universal, some are not.

-------------------

<a name="style-annot"></a>
**Annotations** in your k code is the best way not to end up coding Java for 
food, unless you are Arthur Whitney. We dare to assume you are not, so comments
start with `/`. When used inline, prepend at least one space. Here 
is an annotated declaration of two variables:

```q
/annotations are your friends
x:42

y:42 /now, always and forever
```

<a name="style-sep"></a>
-------------------

**Separator** character in k is `;` and it is used for one thing and one thing 
only, to separate **k expressions**. As you can see above, k doesn't require 
you to terminate the line explicitly with `;` because **`\n` is also an 
expression separator**. Separator is used the same way and means the same thing
everywhere in any context (except comments), e.g. to separate expressions 
inside a function body, vector declaration, function arguments, etc. Later we 
will see that separator is also a part of certain language constructs, but it 
has the same meaning there as well. But by far the most frequent implicit use 
of a separator you will encounter in the wild is to separate expressions 
within one line:

```q
x:1; y:2; z:3       /one line, three expressions
z:1;y:2;x:3         /denser version of the above
```

<a name="style-ident"></a>
-------------------

**Indentation** in k is a tricky subject. Basically, what you generally want
is **no indentation**. This means if your k expression is getting so large that 
you are tempted to split it into separate lines, you likely need to refactor
or return to the blackboard. Sometimes, however, indentation is fine and even 
necessary, and it is always *one space*. Not two, not four, one. Tabs will be 
frowned upon because they take a lot of **space**, see below.

<a name="style-name"></a>
-------------------

**Identifiers** in k follow an unusual convention. Capitals are used by k 
programmers very sparingly, which applies both to code and comments. Identifiers
in `camelCase` can sometimes be tolerated, while `c_style` identifiers are not 
permitted at all since `_` is an operator. Identifiers of functions and 
variables are very often boiled down to an absolute minimum, names 1-3 
characters long are commonplace, which does not impact readability given that 
their definitions are annotated. Short identifiers might sound like a bad idea
to Java programmers who are used to see identifiers longer than 100 bytes, 
but unlike Java, k source requires very little or no scrolling. When the 
entire program fits in your visual buffer, "cryptic" identifiers are no longer 
a problem because their annotated declarations are always right in front of you:

```q
kei:42         /kenneth eugene iverson
```

<a name="style-space"></a>
-------------------

**Space** is a major point of contention in software development. There are 
several approaches to k code organization, and our take on the subject is a 
subjective opinion, which is up for you to consider:

* Screen space is about three keystrokes: **`\n`**, **`\t`** and 0x20, less 
  surprisingly. If we define two extremes as "tall, lean, sparse and readable" 
  and "robust, wide, dense and cryptic", then C and Java are good examples of 
  `tlsr`, and k is all the way down `rwdc` road.

* The right balance between two extremes is `asap`, or "adequately spaced and 
  annotated program". While k syntax encourages you to produce very dense code,
  think of others and don't sacrifice too much readability. Waste of space is a
  waste of time, but so is unreadable code. Comments are part of the code and 
  also take space, so boil them down to some reasonable size.

* With k, it is possible to minimize code scrolling or even avoid it completely.
  When the entire program or component fits in your view, you lose no time on 
  navigating and switching contexts. For example, every code block in this 
  document fits on a laptop screen and remains readable on mobiles.

* Syntax highlighting is essential and bad highlighting is worse than none, so 
  choose carefully from k syntax definitions available for your editor. The best
  is often the one you wrote yourself, and k syntax is extremely regular and 
  simple.

* Medium is the message, so refer to k code in this document. Please send pull 
  requests to help us improve, and if you like the style, it is yours to have. 

<a name="style-bad"></a>
-------------------

**Code bloat** is bad form. Avoid writing extra code as much as you can — there
is too much of it written already. Look to remove any inessential code, yours or
not. But if you have to write more, make sure it is useful, secure, compact, 
maintainable and scalable.

### remarks on parlance

The most important terminology in k revolves around functions. Functions in k 
are first-class citizens. k has lambdas, eval, apply, recursion, and then some.
It takes a leap of faith to believe it, but k is probably more lispy than 
certain Lisps, only you don't need to get past any parens. However, since 
there are no linked lists under the hood, k is not lisp, because it was 
designed to be fast.

<a name="parl-xyz"></a>
-------------------

**Implicit arguments** is an uncommon feature, most languages require you to 
explicitly declare function arguments. Of course you can also do that in k
if you want to, but if you don't, a function can have up to three implicit 
arguments called `x`, `y` and `z`, which basically means you declare them by 
simply referencing them in the function body. It is an extremely convinient 
feature, not nearly as scary as it sounds:

```q
 f:{x+y+z}    /f[] takes three arguments
 f[1;2;3]     /and here is how to call f
6
  
 f:{x*x}      /f[] has only one argument
 f 2          /and you can omit brackets
 
 e:{[a;b;c]   /not so implicit, but why?
  a+b+c}

 e[1;2;3]     /f with 9 extra keystrokes
6
```

Note that when calling a function with three arguments `f[1;2;3]` we had to use
square brackets and use an expression separator, because each argument passed 
to a function is an expression in its own right. However, second function only 
takes one argument, and we were allowed to omit brackets, although we could 
also say `f[2]`.

This illustrates the core principle of k syntax — almost everything that you 
intuitively feel you should be able to omit, can and should be omitted. Top 
candidates for omission are square `[]` and round brackets `()`. The lesser 
you type, the better your code will get.

Syntax for explicit argument declaration `{[a;b]}` is just a side remark, it 
will not be used in this text again.

<a name="parl-rank"></a>
-------------------

**Rank** is another way of saying *valence*, a fancy word that describes a 
simple idea that is extremely important to be understood well. Rank of an 
operator or a function is basically the count of arguments they take. Two 
functions shown above have ranks of 3 and 1, respectively. 

Two specific ranks are so important that they have their own names. 
A function or an operator that takes...

* one argument is **monadic**
* two arguments is **dyadic**

A function in k can of rank 1 to 9. That is:

* it is not really possible to define a function with no arguments. Rank zero,
  or **niladic** functions do not exist in k.
* a function cannot take more than nine explicit arguments, and some say this 
  is an overly generous limit.

As you will see, the vast majority of native operators in `k` have exactly two 
completely different meanings based on the context where they are used, which 
is in turn defined by the number of arguments offered to the operator. To 
overlook this fact is a grave mistake, so you better get a very strong grip on 
the idea that some things in life are **monadic**, while others are **dyadic**.

For example, when you used your first ever k operator in the expression `2+2`, 
you have used the `+` operator in a dyadic context since it received *two* 
operands to work on, left and right. We will introduce monadic `+` operator 
later.

-------------------

**Recap:**

So far you know how to:

* add two integers
* assign values to variables
* declare and call basic functions
* be friends with `x`, `y` and `z`
* tell monadic and dyadic apart
* annotate your code

This is a good start, but tells you absolutely nothing about what k really is,
and from here things will start to get real.

## numbers

### vectors vs atoms

The word `atom` is a synonym for `scalar value`, or simply `scalar`. Every 
language has them, and in k they are as useful as elsewhere. But k belongs to a
family of *vector languages*, which means its fundamental type is an ordered 
set of atoms or other ordered sets. In k parlance, terms "array", "list"
and "vector" are often used interchageably and refer to the same thing, but we
will stick with `vector` to avoid confusing you, because vectors are much more 
general than classic *arrays* and have nothing to do with *linked lists*. 

```q
 a:42             /a scalar variable, an atom with a name
 
 x:(0,1,2,3,4)    /one way of declaring an integer vector
 y:0 1 2 3 4      /same effect using more informal syntax

 x
0 1 2 3 4

 y
0 1 2 3 4
```

k is strictly "pass by value", there are no references or pointers:

```q
 x:0 1 2 3 4     /everything is passed by value
 y:x             /so this will make a copy of x
 y               /y is a clone, not a reference
0 1 2 3 4     

 y:x:0 1 2 3 4   /same effect in one expression
```

<a name="v-plus-v"></a>
The most enlightening fact about vectors is that most operations you expect 
to work for atoms work equally well for vectors, too:

```q
x:y:0 1 2 3 4    /x and y are twin copies

 x+y             /pairwise sum of vectors
0 2 4 6 8 

x*y              /product is pairwise too
0 2 4 9 16

 x%y             /division is %, get used 
ø 1 1 1 1

 0%0             /ø is nan, void and null
ø

 x=y             /compare x to y pairwise
1 1 1 1 1        /1 is truthy, 0 is false
```


<a name="v-plus-a"></a>
Mixing atomic and vector operands makes total sense and is very useful:

```q
 x:0 1 2 3 4

 x+1             /increment all elements
1 2 3 4 5 

 x=1             /compare each of x to 1
0 1 0 0 0

 x%0             /divide each of x by 0 
ø ∞ ∞ ∞ ∞        /∀x∈ℚ (x%0) ∈ {-∞,∞,ø}, beware (0%0) = ø, enjoy responsibly

 3%x             /divide 3 by each of x
∞ 3 1.5 1 0.75
```

<a name="v-indexing"></a>
**Indexing** is zero-based as you would expect, and if you pass a vector of 
indices, you get back vector of items:

```q
 x:2 4 8 16 32
 
 x[2]          /get 3rd element of x
8

 x 2           /no need for brackets
8

 x[1 4]        /get 2nd and 5th item
4 32           /gives another vector

 x 1 4         /no need for brackets
4 32

 y:1 4         /y is an index vector
 x y           /same as x[y] less []
4 32           
```

<a name="v-shp"></a>
Pairwise operations on vectors of incompatible **shape** make much less sense 
to k than division by zero, and will throw an error:

```q
 x:0 1 2 3 4
 y:0 1 2
 x+y
 
x+y
 ^
length error
```

Note the difference between shape and length. This reminds us that a vector can
be composed not just from atoms but from other vectors as well, and there is no
practical limit on the depth of nesting. In other words, vectors can 
have **arbitrary shape**:

```q
 y:(1;1 1;1 2 1;1 3 3 1)     /pascal's triangle
 y
1
1 1
1 2 1
1 3 3 1 
```

Vector arithmetic is **penetrating**, which means that vector operators 
*apply at depth* for as long as operands have compatible shape:

```q
 x:(1 2 3;4 5 6;7 8 9);x     /square matrix 3*3
1 2 3
4 5 6
7 8 9

 y:(1 4 7;2 5 8;3 6 9);y     /y is transposed x 
1 4 7
2 5 8
3 6 9

 x=y
1 0 0
0 1 0
0 0 1

 x>y
0 0 0
1 0 0
1 1 0 

 x+42
43 44 45
46 47 48
49 50 51
```

### two types of types

Type system in k gets strict when it has to, but also agrees that implicit 
casts and type coersion have their strengths — especially when done right, 
which in k they are.

Before we see the examples, the first thing you need to know about types in k 
is that they are divided into two broad classes: **vector types** and **atomic 
types**. That is, a vector with a single element, say, `42`, is not the same 
type as an atomic integer of the same value. Finally, since functions and other 
things in k are also assignable values, they have their place in type system 
too. Those are **special types** and we will not cover them here in much detail.

Here is a quick overview of k types and their symbolic names:

```q
atom      vect        type
  `i        `I        int
  `f        `F        float
  `c        `C        char
  `n        `N        name
  `D        `D        date
  `t        `T        time
```

This is not very revealing, so lets see them in action. The operator to query 
the type of anything in k is `monadic @x`, and if you are not sure what we mean 
by `monadic`, it is a good time to start over.

<a name="typ-num"></a>
```q
 @42         /int scalar
`i

 @.5         /float atom
`f

 @0 1 2      /int vector
`I

 v:0 1 .5 2
 @v          /presence of 0.5 promotes vector to float
`F

 v 1         /2nd element, trailing f is short for 1.0
1f
```

<a name="typ-char"></a>
Like in C, there is no dedicated type for strings in k. Strings are just 
**char vectors**:

```q
 @"k"        /"k" is char atom
`c

 s:"kei";@s  /s is char vector
`C
 
 s 0         /1st element of s
"k"
```

<a name="typ-name"></a>
However, k has something C doesn't. We have a type called **name**, which is 
the same idea as **internalized string** found in some other languages. This 
means that a single instance of an arbitrarily long string can be placed into 
a global hash table that persists for a lifetime of a k process and can later 
be referenced by its hash key as many times as necessary without creating 
additional copies of the string. Names come handy in many situations, for now 
lets just see how they quack:

```q
 a:`kei              /"kei" is now internalized
 @a                  /name atom
`n

 b:`kei`kei`kei      /vector of three references to a single instance of "kei" string
 @b                  /vector of names
`N

 @`"ken iverson"     /spaces in names, no problem
`n
```

<a name="typ-time"></a>
**Temporal types** in k are `date` and `time`:

```q
 d:1981-02-01        /yyyy-mm-dd
 @d                  /atomic date type is special, it is a capital D, same as date vector
`D

 t:12:34:56.789      /hh:mm:ss.sss
 @t
`t

 dt:d+t;dt           /operations on temporal types is a story for another day
1981-02-01T12:34:56.789 
```

<a name="typ-lambda"></a>
As you already know, k lambda is an assignable value, so it must to have 
its own type, which is does, and more than one:

```q
 @{x+y}                 /type of lambda gives away its rank
`2

 nil:{0}                /don't expect nil to have rank zero
 @nil                   /niladic functions don't exist in k
`1

 a:{x},{x+x},{x*x}      /a vector of lambdas, sure, why not
 a[2]16                 /calls 3rd lambda, same as a[2][16]
256
```

<a name="typ-mix"></a>
Of special mention is the **composite vector** type, or you could also say 
**mix vector**. Such vectors are either a mixture of atoms of disparate types, 
or contain something more complex than atoms, e.g. other vectors.

```q
 c:0,1,"a",2,3          /a char impostor among ints, c is composite
 @c                     /a composite type symbol is just a backtick
`

 a:(1 2 3;4 5 6;7 8 9)  /a vector of vectors is a composite vector
 a
1 2 3
4 5 6
7 8 9
 @a
```

<a name="typ-cast"></a>
**Type casts**, both explicit and implicit, are demonstrated by the following
examples which also give a general feel of how type coersion behaves. The `cast`
operator in k is a dyadic `t$x`, where `t` is the type name and `x` is a cast 
subject. If you look closer at the argument `t`, you could say there is some 
wordplay going on here, "type name of a type name is name". It could be a 
valid observation, but the proof of this conjecture will have to wait until 
the end of next chapter.

```q
 1+.5                  /int plus float is float, no surprises here
1.5

 1f*2                  /1f is the same as 1.0, saves one keystroke
2f 

 `i$42.99              /explicit cast `f to `i just drops mantissa
42

 `i$42.0 42.99         /same is true for float vectors
42 42

 0+"abc"               /adding an int atom to a char vector yields an int vector of its ascii codes
97 98 99

 `c$1+"HAL9000"        /increment ascii codes by one, cast back to char, surprise:
 "IBM:111"

 "012"+"345"           /sum of char vectors adds their ascii codes pairwise, result is still a char vector
"ceg"

 1+`kei                /no math for names
  ^
type error

 a:1 2 3               /define a int vector
 a[0]:1f               /replace its first element with a float
 @a                    /ouch, int vector got demoted to composite
`
 a:`f$a                /explicitly cast composite to float
 @a                    /voila, a float vector
`F

 `i$1981-02-01         /integer representation of dates is puzzling at first
-15674

 15674+1981-02-01      /adding 15674 days solves the mystery: all dates in k are simply offsets from:
2024-01-01

 @10                   /a type name of 10
`i 

 @@10                  /type name of a type name of 10
`n
```

There is a lot more to be said about the type system, but this last expression 
above urges us to proceed to the next section, which is all about giving a 
rational explantation how `@@10` actually works.

### right to left and back again

It did not escape your attention that the syntax for indexing vectors and 
calling functions is the same:

```q
 f:{x+x}      /some function
 d:2 4 8 16   /some data items
 i:0 3        /some indices

 f[d]         /call a function
4 8 16 32

 d[i]         /index a vector
2 16

 f[d[i]]      /compose the two
4 32 
```

What you also know that k actively encourages you to omit brackets whenever 
possible, so lets do exactly that:

```q
 f d i        /same as f[d[i]]
4 32
```

And here comes an astonishing truth. Once we drop the brackets, it suddenly 
becomes absolutely natural to read this expression *from right to left*. Take 
your time to contemplate and process this statement. In very little time you 
will see how it works in practice, and once you put it to practice yourself, 
you will see that this way of functional composition is beautiful, elegant 
and intuituve.

**k expressions are read, written and evaluated right to left**

Just to be clear, when we say "expressions" we don't mean "programs", and this 
is a very important distinction. Below is a diagram of a small **k program** 
that consists of three identical expressions `f d i` with parens added for 
clarity. Further down is the order of evaluation of the entire program:

```q
/   L       T       R
/(f d i);(f d i);(f d i)

/   I   >   II  >  III
/(3 2 1);(6 5 4);(9 8 7)
/   <       <       <
```

 **k programs are read, written and evaluated left to right**

<a name="rtl-precedence"></a>
Now that we know which way the rivers flow in k land, we are ready to discuss 
a related, no less important subject of precedence.

We all take it for granted that multiplication and division bind stronger than 
addition and substraction and should be calculated first, and it feels almost 
natural that a computer language must have complex operator precedence hierarchy
to do anything useful, and k disagrees with that:

**There is no operator precedence in k expressions unless explicitly 
overridden by round brackets**

That is, by default **all operators** in a k expression are treated equally and 
evaluated strictly from **right to left**, and that includes **arithmetic** 
operators, e.g. `*` has no precedence over `+`. Here are some basic math 
expressions, annotated with their order of evaluation:

```q
 3+2+1        /"take 1, add 2, add 3"
6

 3*2+1        /"take 1, add 2, multiply by 3"
9

 (3*2)-1      /"take 2, multiply by 3, sub 1"
5

 -1+3*2       /same as above, without parens
5
```

It is much easier to get used to lack of precedence than you may think, 
and once you do, you will generally want to avoid using parens unless you 
absolutely have to. The last example from above shows the basic strategy of 
ditching them: it is usually possible to rearrange the expressions so that 
the order of evaluation becomes linear. Although precedence override is often 
inevitable and can be beneficial, it can also have an adverse effect on 
readability, because it breaks the natural flow of code comprehension. That 
is, once you learn to read k expressions right to left, you want to go fast 
and uninterrupted, but precedence override gets in your way, so when you 
write code, think of the reader and minimize the use of round brackets.

----------------

Finally, we can revisit the question raised in the type system discussion:

```q
 @@10             /"type name of a type name of 10" is actually, right to left...
`n                /..."get 10, apply monadic @, get `i, apply monadic @, get `n"
```

This is a convincing proof of our earlier conjecture that `type name` of 
a `type name` in k is `name`.∎

----------------

**Practice:**

Lets revisit the code from the first snippet in this document:

```q
 x:(1 2 3;4 5 6;7 8 9)

x=x+1                 /how can a universal truth be false?
```

Too easy, but we'll make up for it.

----------------

### no stinking loops

This part might be easier to digest than the previous, especially if you are 
familiar with functional programming. The heading says it all - no matter how 
you try, you will not find a k construct that resembles an explicit `for` loop. 
It is simply absent, and not just because it is verbose and causes untold 
damages from the same trivial errors people keep on making coding `for` loops.
Technically speaking, `while` construct does exist in k, but this fact is better
be ignored just to avoid temptation.

The main reason explicit loops are missing from k is because they are 
*unnecessary*. Of course k has loops, but they are *implicit* and hardly ever
referred to by that name. Also, it comes without saying that k supports 
**recursion**, which is a no less elegant way to avoid loops in many situations.

An idea that displaces thinking in explicit loops is a simple and strong 
abstraction known as *adverbs*. Before we see them in action, it helps to 
understand why they are called that way:

An **adverb** if a **modifier** that takes some **verb** (which is a short 
way of saying "a user-defined function or a native operator"), and makes that 
verb's action applicable to an **input vector** in some desirable way to 
produce an **output**, which can be a scalar value or another vector, 
depending on which adverb is used.

A good example of how adverbs replace loops is `sum`. Say, we have an 
input `in:1 2 3 4 5`, and what we want is a sum of its elements. Thinking 
in implicit loops suggests something like that:

```c
int sum(int[]in){
  int i=0,acc=0;
  for(;i<sizeof(in);++i)
    acc+=in[i];
  return acc;
}
```

But imagine you could state the problem to a computer like this:

**"put a `+` between all adjacent items and give me the grand total"**

And that is the simplest way to describe what k adverb `over` does when it is 
used to modify dyadic `+`. Only `over`, as all other adverbs, is *general* and 
will happily modify *any* dyadic operator or function. Described more formally,
`over` looks like this pseudocode:

1. set `acc` to 0 (a.k.a. accumulator)
2. while `next x`, set `acc` to the result of `v[acc;next x]`
3. return `acc`

The above is nothing else but a general case of the explicit loop found in 
`sum()`, as well as of **all other** explicit loops of this particiular family,
which is known as `fold` or `reduce` among functional folks.

And since `over` is just `v/x`, this is how `sum` function looks like in k:

```q
 s:{+/x} 
 s 1 2 3 4 5
15 
```

It is a good moment to look back at the C version, one last time. Be surprised
to hear that its `for` loop declaration contains an ancient, but ever so 
popular [bug](https://stackoverflow.com/questions/37538/how-do-i-determine-the-size-of-my-array-in-c),
which k version does not because fixing bugs in `+/x` is much easier. Besides, 
even if the C code wasn't broken, it would only work for integers.

You could be tempted to see of what other use `over` could be. Let's introduce 
a new k operator, `!x til`, and implement another obvious candidate for `over`:

```q
 x:!9                          /! is til, get first n integers
 x                             /tada, we have all ints up to 8
0 1 2 3 4 5 6 7 8

 fact:{*/1+!x}                 /fact x 'mul over 1 plus til x'
 fact 10 
3628800 
```

Now that you parted ways with loops, you are ready to discover there are 
**6 adverbs** in k that modify verbs in very different ways. Please welcome 
the magnificent six, and note that only most trivial use cases are shown:

----------------
adverb **each** is `f'x`

where `f` is a `monadic` verb and `x` is an input vector

```q
 a:0 1 2 3 4    /some data
 sq:{x*x}       /a function that takes one argument

 sq'a           /each applies f to each element of x and returns a vector of results
0 1 4 9 16      /each of a, squared
```
----------------
adverb **over** is `f/x`

adverb **scan** is `f\x`

where `f` is a `dyadic` verb and `x` is an input vector

```q
 a:0 1 2 3 4    /some data

 +/a            /over inserts a plus between adjacent elements (i.e. 0+1+2+3+4) and returns the final result
10              /sum of a

 +\a            /scan is exactly the same as over, but returns all intermediate results as well
0 1 3 6 10      /running sum of a
```
----------------

adverb **eachleft** is `x f\:y`

adverb **eachright** is `x f/:y`

where `f` is a `dyadic` verb and `x` and `y` are left and right inputs, 
either vectors or atoms

```q
 10 20 30-\:5   /eachleft gives (10-5),(20-5),(30-5)
5 15 25         /each of left, substracted by right

 5-/:10 20 30   /eachright gives (5-10),(5-20),(5-30)
-5 -15 -25      /left, substracted by each of right
```
----------------

adverb **eachprior** is `x f':y` and `(f':)x`

first form is `seeded eachprior` where `f` is a `dyadic` verb, and `x` is a 
seed value and `y` is an input vector

second form is `seedless eachprior` where `f` is a `dyadic` verb, and `x` is 
an input vector


```q
 2+':4 8 16          /seeded eachprior        gives (2+4),(4+8),(8+16)
6 12 24              /sum of first item and seed, then sum of each item and the item prior to it

 (+':)4 8 16         /seedless eachprior      gives (4),(4+8),(8+16)
4 12 24              /first item stays as is, then sum of each item and the item prior to it
```
----------------

Okay, this doesn't seem like much, adverbs seem to be doing pretty basic stuff.
But hold that thought for a minute.

**Recap:**

We have seen:

* what k type system looks like
* how basic vector and atom math works
* which way to read and comprehend k code
* what is the only existing precedence rule
* why there is no `for` and why there are `adverbs`

----------------

**Practice:**

Okay, we are back to your doubts about adverbs. Consider this example of two 
adverbs working together:

```q
 x:!9                          /til 9
 x+:1                          /add 1 to each of x, also x:x+1
 x
1 2 3 4 5 6 7 8 9

 x*\:/:x                       /"x times eachleft eachright x"
1 2  3  4  5  6  7  8  9    
2 4  6  8  10 12 14 16 18
3 6  9  12 15 18 21 24 27
4 8  12 16 20 24 28 32 36
5 10 15 20 25 30 35 40 45
6 12 18 24 30 36 42 48 54
7 14 21 28 35 42 49 56 63
8 16 24 32 40 48 56 64 72
9 18 27 36 45 54 63 72 81 
```

And your goal here is to make sure you understand the logic and the order of 
evaluation of this expression, which only consists of one operator and two 
adverbs. And you have everything you need:

* read right to left
* there is no precedence
* no explicit loops either
* k interpreter is your friend

Take your time, make sure you got it before advancing to the next chapter, 
where things will get a lot less innocent, and fast.

-------------------

Well done. There is a bonus waiting for you, you finally get to know the 
meaning of monadic `+`:

```q
 mat:(1 2 3;4 5 6;7 8 9)       /shall there be mat

 mat                           /print matrix as is
1 2 3
4 5 6
7 8 9 

 +mat                          /flip aka transpose
1 4 7
2 5 8
3 6 9
```

## proverbs

### how to solve it

The title of this chapter is borrowed from a legendary book published back 
in 1945, a small volume by mathematician George Pólya where he shows how to 
tackle problems and arrive to solutions. It is a very inspiring read.

Lets tackle a little problem. We will look at a k function that actually does 
something very useful and implements a familiar algorithm. The subject of 
the game is to figure out how it is implementented in k and to identify the 
algorithm.

It is more useful to dissect it on paper. Once we are done, you will be very 
tempted to try a lot of new things on your own. So here is the code:

```q
/what is f[] and how it works?
f:{$[2>#?x;x;,/f'x@=x>rand x]} 
```

Almost nothing looks familiar here, and the whole little monster is just 
creepy.But once we take it apart, you will find it is actually very simple 
and readable:

```q

f:{$[2>#?x;x;,/f'x@=x>rand x]} 

f:{...}           /f is a function, that is a good start
f:{.x.}           /f takes only one implicit argument, x
f:{.f.}           /f clearly calls f, so it is recursive

$[?;?;?]          /the entire body of f is nothing else but
$[c;t;f]          /a ctf cond, aka if-then-else aka ternary

2>#?x             /c:      boolean condition
x                 /t:      do this if c is 1
,/f'x@=x>rand x   /f:      do that if c is 0

2>#?x             /we don't how to read this, but it is clear that f[]
                  /halts recursion when it evaluates to 1, returning x
                  /so lets find out what it means, going right to left

                  /we have two new operators, both in monadic context:
                  /monadic ?x is 'distinct'       unique elements of x
                  /monadic #x is 'count'       count the elements of x

#?x               /'count distinct'         count unique elements of x
2>#?x             /'greater'   true if count distinct x is less than 2

$[2>#?x;x;...]    /"if x has <2 unique items, return x, otherwise ..."
```

Coffee break, here is what we know so far:

1. the function is recursive
1. its overall control flow
2. the condition that stops recursion

This gives us confidence to wrestle down the last part, the recursion step:

```q

,/f'x@=x>rand x   /this must be the recursion step, read right to left:

 x:4 0 1 2        /an tiny dataset to help us see what is going on here
 
 rnd:rand x       /pick a random element from x (rnd added for clarity)
 rnd
2 

 cmp:x<rnd        /bool vector of 0s where x[n]<rnd, 1s where otherwise
 cmp
0 1 1 0

 idx:=cmp         /= is 'group': 2 vectors, indices of 0s and 1s in cmp
 idx
0|0 3
1|1 2

 pts:x@idx        /dyadic @ is 'index': elements of x at indices in idx
 pts
0|4 2
1|0 1

pts:x@=x>rand x   /"partition x by pivot: items < rnd and items >= rnd"

x:f'pts           /adverb each: apply f to each partition, recurse down 


,/x               /,/ is 'raze': unwind aka flatten a vector of vectors

 v:(1 2 3;4 5 6)
 v
1 2 3
4 5 6
 ,/v
1 2 3 4 5 6
```

Now that we know what every specific part does, we can zoom out and see the 
big picture. Feel free to use the interpreter to play around and test your 
ideas. And of course, `f` is nothing else but:

-------------------

```q
 qs:{$[2>#?x;x;,/qs'x@=x>rand x]}        /quicksort by random pivot

 qs 9 2 5 5 1 8 1 3 6 1                  /sort an int vector
1 1 1 2 3 5 5 6 8 9

 qs 2.6 -∞ 8.6 π 1.7 ∞ 3.5 5.6           /sort a float vector (hello π)
-∞ 1.7 2.6 π 3.5 5.6 8.6 ∞

 qs "edrofgtnljgrpliifp"                 /sort a char vector
"deffggiijllnopprrt" 
```

This is not the fastest `quicksort` ever written, but in real life you would 
simply use the built-in operator which is a lot more efficient. It is just 
monadic `^x`:

```q
 ^2.6 -∞ 8.6 π 1.7 ∞ 3.5 5.6             /^x is 'sort'
-∞ 1.7 2.6 π 3.5 5.6 8.6 ∞
```

But what our DIY sort function demonstrates very well is the principle of 
**doing more with less**, and that is what k is all about.

The annotated breakdown of `qs` code gives a good impression of what is 
typically going on inside of k programmer's head, but tells you nothing about 
how fast it usually happens. A proficient k programmer would read and 
understand `qs` in well under two minutes. With a bit more practice, you 
will agree that reading k programs is easy and fun.

-------------------

Speaking of fun, compare the functionality of these two programs:

```java
package com.less.with.more.doing.sort;
public final class qs{public void s(int[] x){}}
```

```q
qs:{$[2>#?x;x;,/qs'x@=x>rand x]}
```

-------------------

And now compare the source code of these two programs, and then the size 
of their runtimes:

```java
import java.util.Arrays;  
public class S{public static void main(String[] a){ 
int[] x={5,4,3,2,1};Arrays.sort(x);
System.out.printf("%s",Arrays.toString(x));}} 
```

```q
 ^5 4 3 2 1
```

```sh
   252M May 17 13:59 jdk-8u211-macosx-x64.dmg
    79M May 17 13:50 jre-8u211-macosx-x64.dmg
   109K May 17 13:54 k.tgz
```

-------------------

Check out more `quicksort` in the wild in 
[C++](https://gist.github.com/christophewang/ad056af4b3ab0ceebacf), 
[Python](https://gist.github.com/anirudhjayaraman/897ca0d97a249180a48b50d62c87f239),
[JavaScript](https://gist.github.com/claudiahdz/39a86084edaaabe7fc17c321c0bb6896) 
and [Java](https://github.com/Code2Bits/Algorithms-in-Java/blob/master/sort/src/main/java/com/code2bits/algorithm/sort/QuickSort.java).

-------------------

**Recap:**

While analysing `qs` code, you have learned:

* ctf cond `$[c;t;f]`
* monadic `?x distinct`
* monadic `#x count`
* monadic `rand x`
* monadic `=x group`
* monadic `,/x raze`
* dyadic `x@y index`

Also, in the previous chapter you have seen:

* monadic `!x til (first x integers)`
* monadic `+x flip (transpose)`

Finally, for completeness sake:

* dyadic `t@x cast`
* monadic `@x type`
* monadic `^x sort`

* dyadic `x:y assign`
* dyadic `x=y equal`


Although this is still a small part of k operator arsenal, if you can do 
`quicksort` with this much, you can do a lot more. And then add vector 
arithmetic, and then take everything to the power of 6 adverbs.

-------------------

**Checkpoint exercise:**

1. take another good look at the code of `qs` function
2. retrace the steps of the analysis we did together
3. in a new k session, try to reproduce `qs` from scratch

It sounds much harder than it really is. It might take more than one attempt, 
but you will be amazed how fast you will get there. However, before advancing 
to the next chapter, make sure that you do.

-------------------

*\`nyi* ∎
