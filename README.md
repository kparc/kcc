# +/∞

plus over infinity, aka k crash course

**[genesis](#genesis)**

* k → [ø](#ø) | [who](#who) | [why](#why) | [wha](#wha) | [how](#how)

**[exodus](#exodus)**

* [get](#get) | [run](#run)
* style → [cmt](#annotations) | [sep](#separator) | [tab](#indentation) | [ids](#identifiers) | [space](#space) | [bad](#bad-form)
* parlance → [xyz](#implicit-arguments) | [proj](#projection) | [rank](#rank) | [+:](#explicit-monadics)

**[numbers](#numbers)**

* vector math → [v≠a](#vectors-vs-atoms) | [v+v](#v-plus-v) | [v+a](#v-plus-a) | [v x](#v-indexing)  | [t≠s](#v-shp)
* [type system](#types-of-types) → [num](#typ-num) | [char](#typ-char) | [name](#typ-name) | [date](#typ-time) | [dict](#typ-dict) | [tab](#typ-tab) | [λ](#typ-lambda) | [ø,∞](#typ-nul) | [mix](#typ-mix) | [cast](#typ-cast) 
* order of eval → [rtl](#right-to-left) | [(1)2](#precedence)
* [no stinking loops](#no-stinking-loops) → [over](#nsl-overscan) | [scan](#nsl-overscan) | [e↣](#nsl-each) | [e↔](#nsl-eachlr) | [e↤](#nsl-eachprior)

**[proverbs](#proverbs)**

* reading code → [how to solve it](#how-to-solve-it)
* writing code → [three triangles](#three-triangles)
* metrics → [apples and oranges](#apples-and-oranges)
* learning plan → [gladly beyond](#gladly-beyond)

---------------------

## genesis

### ø

Computer languages have been around, but in the beginning was the Word. We will be writing code in a language called k, but it helps to talk about it first.

k is different. At first, you will be questioning its design, and it will respond by questioning things that you consider common sense, but soon it will become a constructive conversation, and here is how.

The first thing newcomers frown upon is why the assignment operator is `:` instead of `=`. But before you close the tab, try a simple thought experiment:

```java
x = x + 1
```

Most programmers will agree that this expression makes perfect sense, but if you show it to a math guy, be ready to hear "no, it isn't". And once you see what makes him think that way, you will also see why we assign values with `:` 
in k. The above expression looks nonsensical to a k programmer for the same reason it is to a math guy, and k will most always evaluate it to false. It is possible to produce a k expression where `x=x+1` evaluates to true, and once you can, please submit a pull request and say "hello".

k has a different perspective on some other things as well, but it is not necessarily wrong. It can just as well be right, but in a different way, and this short introduction invites you to look at those things that other way. And we hope they might also feel obvious and natural to you, like `x≠x+1` just did.

---------------------

This crash course is not looking to make you an expert k programmer, because that takes a lot of time and effort. Instead, it aims to give enough confidence and motivation for you to continue on your own. We value your time, so we promise it will be fast and violent.

* The text cuts a lot of corners on general programming and CS at some expense of readability.
* The course is driven entirely by densely annotated code, comments contain essential material.
* New syntax is often introduced inline, some is self-explanatory, some relies on your intuition.
* The narrative is linear, all chapters build on previous.
* Skipping exercise will halt your progress.

This might feel a bit intense, but we hope the course is still lightweight enough to be completed in one session.

This document is **not a k reference**. The majority of subjects are discussed at depth sufficient to give a solid general overview, but by no means exhaustive.

### who

The man behind k is a computer scientist by the name Arthur Whitney. He is the principal designer of the language, and he is an iconic figure in a community of some of the most sophisticated programmers and scientists employed by some of the most influential institutions on the planet. Since early 90s, he delivers ever more powerful revisions of a concept he has been refining throughout his career, a system to build very efficient software that transforms large amounts of data into large amounts of money.

That is, k enjoys much success in the world of finance, where this kind of problems existed long before the term **big data** was coined. Many people embraced the k way and made successful careers by building solutions using k, and they appreciate their tool as much as they appreciate the man behind it, and we believe they have their reasons.

### why

There is a good chance that you have heard or read about k language. A lot of people know the story. What is much less likely is that you have ever met a professional k programmer. This happens not just because k programmers are rare, but also because k is not fishing for cheap publicity. This is how we all heard about a language called k, but what we mostly hear is how much it sucks to be a Java programmer.

All jokes aside, implementations of similar systems in languages like C++ or Java usually involve thousands of lines of code written by large teams, built on top of complex library stacks and even more complex infrastructure. Such projects are often expensive and inflexible, go over budget and miss deadlines.

In comparison, k solutions are typically a few factors of magnitude less code, implemented by small and agile teams, rarely require external dependencies, and ship on time. 

At first it could be hard to understand how this can be true, imagine the effort of keeping 100 lines of code in sync with rapidly changing requirements and free of bugs, compared to 10,000 lines of code that do the same thing. Against all intuition, it is not 100 times easier, but 10,000 times easier, because the effect of cyclomatic complexity is devastating.

### wha

k is an simple, expressive and powerful computer language.

The power stems from the fact that k is designed as a *tool of thought*. The vocabulary, syntax and the choice of abstractions offered by the language drive you to think about problems in a focused and clear way that quickly takes you to efficient and elegant solutions. And the reason why thinking in terms of k is so effective is nothing supernatural: brevity is a soul of wit.

k programs are concise, the syntax of the language is terse, and there is no boilerplate code to write. In k, most of the time is spent on thinking about the problem rather than writing and refactoring code or browsing source.

### how

k runtime environment is an incredibly compact and efficient piece of software. 
The entire system is:

* a single binary executable
* without any external dependencies
* that fits in the cache of your CPU

And that gives a selection of fundamental algorithms, data structures, techniques and primitives that withstood the test of decades of production use in some of the world's most demanding data processing environments. Inner components of the system fit together and complement each other to deliver *performance*. It is not uncommon for k newcomers to experience shock when they first see how much can be done with a few precise keystrokes, and how fast.

All of k programming takes place in **REPL**, an idea that is actually much older than many seem to think. It has been around for at least half a century, and is known as *dialogue approach*, a live conversation between a human and machine as a flow of questions and answers. And in k, this conversation is much more fluent than in any other modern REPL-driven system you may be familiar with, because the questions are short and the answers are fast. This is the essence of the way of k, an experience that all k programmers consider immensely satisfying. People who write k for living love their jobs.

## exodus

The only known way to learn how to program is to write programs, so you will need a live k environment. As all things k, it takes very little effort.

### get

We will use a trial version of k, which comes with a reasonable limit of 1 gigabyte of workspace per k process. This is for your own protection, so that you don’t accidentally convert too much data into too much money too early, because, as any k programmer will tell you, with great power comes great responsibility.

The k interpreter is currently available for `Linux` and `macOS` on `x86_64` architecture.

Without further ado, install [conda](https://anaconda.org). Shell integration is optional but recommended. Once you have it, install the package called `shakti`, which is nothing else but `k` in disguise:

```sh
conda install -c shaktidb shakti
```

As all things k, the development of k itself is happening very fast. New builds are published up to several times a week, so make sure you always use the latest version:

```sh
alias kup="conda update -c shaktidb shakti"
kup
```

### run

Assuming conda's `bin` is in your PATH, Start your very first k session like so:

```sh
$ k
2019-04-21 15:38:18 40core 270gb avx2 © shakti m2.0 prod
 █
```

There isn't much to write home about, but startup banner actually packs a lot of useful information:


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

When it comes to that, always include the banner in your bug reports.

At any time during k session, you can:

`\h` view k reference card

`\l` view k change log

`\\` quit k session

At this point we highly recommend to avoid issuing any of the above commands, especially the latter.

---------------------

**Practice:**

Make sure you have `rlwrap` utility installed, and put an alias `alias k="rlwrap k"` into your rc file. This makes your spartan k development environment a lot more pleasant to use.

Type in your first k expressions, and enjoy your first answers:

```q
 2+2      /simplest face of k is a calculator
4

 x:42     /: is assign so x is now the answer
 x=x+1    /= is equal, and of course it isn't
0

 kcc:+/∞  /we knew you'd want to try this one
 kcc      /and what it happens to be is just:
 █
```

Indeed, the title of this document seems to make sense to k interpreter and evaluates to exactly that, and very soon you will easily infer what it actually means.

---------------------

### remarks on style

As any other language, k expects a programmer to observe and follow certain conventions on coding style and terminology in order to understand the code written by the others and let their own code be understood. While some rules of the house of k are universal, some are not.

#### annotations

Commenting your k code is the best way not to end up coding Java for food, unless you are Arthur Whitney. We dare to assume you are not, so comments start with `/`. When used inline, prepend at least one space. Here is an annotated declaration of two variables:

```q
/annotations are your friends
x:42

y:42 /now, always and forever
```

#### separator

character in k is `;` and it is used for one thing and one thing only, to separate k expressions. As you can see above, k doesn't require you to terminate the line explicitly with `;` because **`\n` is also an expression separator**. Separator is used the same way and means the same thing everywhere in any context (except comments), e.g. to separate expressions inside a function body, vector declaration, function arguments, etc. Later we will see that separator is also a part of certain language constructs, but it has the same meaning there as well. But by far the most frequent implicit use of a separator you will encounter in the wild is to separate expressions within one line:

```q
x:1; y:2; z:3   /one line, three expressions
z:1;y:2;x:3     /denser version of the above
```

#### indentation

This is a tricky subject in k. Basically, what you generally want is **no indentation**. This means if your k expression is getting so large that you are tempted to split it into separate lines, you likely need to refactor or return to the blackboard. Sometimes, however, indentation is fine and even necessary, and it is always *one space*. Not two, not four, one. Tabs will be frowned upon because they take a lot of *space*, see below.

#### identifiers

Variable names in k follow an unusual convention. Capitals are used by k programmers very sparingly, which applies both to code and comments. Identifiers in `camelCase` can sometimes be tolerated, while `c_style` identifiers are not permitted at all since `_` is an operator. Identifiers of functions and variables are very often boiled down to an absolute minimum, names 1-3 characters long are commonplace, which does not impact readability given that their definitions are annotated. Short identifiers might sound like a bad idea to Java programmers who are used to see identifiers longer than 100 bytes, but unlike Java, k source requires very little or no scrolling. When the entire program fits in your visual buffer, "cryptic" identifiers are no longer a problem because their annotated declarations are always right in front of you:

```q
kei:42   /kenneth eugene iverson
```

#### space

This is a major point of contention in software development. There are several approaches to k code organization, and our take on the subject is a subjective opinion, which is up for you to consider:

* Screen space is about three keystrokes: **`\n`**, **`\t`** and 0x20, less surprisingly. If we define two extremes as "tall, lean, sparse and readable" and "robust, wide, dense and cryptic", then C and Java are good examples of `tlsr`, and k is all the way down `rwdc` road.

* The right balance between two extremes is `asap`, or "adequately spaced and annotated program". While k syntax encourages you to produce very dense code, think of others and don't sacrifice too much of readability. A waste of space is a waste of time — but so is unreadable code.
  
* Comments are part of the code and also take space, so boil them down to some reasonable size as well.

* With k, it is possible to minimize code scrolling or even avoid it completely. When the entire program or component fits in your view, you lose no time on navigating and switching contexts. For example, every code block in this document fits on a laptop screen and remains readable on mobiles.

* Syntax highlighting is essential and bad highlighting is worse than none, so choose carefully from k syntax definitions available for your editor. The best is often the one you wrote yourself, and k syntax is extremely regular and simple.

* Medium is the message, so we refer to k code in this document. Please send pull requests to help us improve it, and if you like the style, it is yours to have. 

#### bad form

Bad form in k is code bloat. Avoid writing extra code if you can — there is too much of it written already. Look to remove any inessential code, yours or not. But if you have to write more, make it is useful, secure, compact, maintainable, portable and scalable.

--------------------

**practice**

We don't know much k to practice style yet, so this one will be read-only. Here is a trivial C program formatted in two different ways. Compare their strengths.

**tslr:**

```c
#include <stdio.h>

int
main(int argc, char **argv)
{
  int x = 'a';

  for(int i=0; i<26; ++i){
    putchar(x++);
  }

  return 0;
}
```

**rwdc:**

```c
#include <stdio.h> //k.h
typedef int I;
#define O putchar
#define DO(n,x) {I i=0,_i=(n);for(;i<_i;++i){x;}}
```

```c
#include "k.h"
I main(){I x='a';DO(26,O(x++))}//nsl
```


### remarks on parlance

The most important terminology in k revolves around functions. Functions in k are first-class citizens. k has anonymous functions, eval, apply, recursion, and then some. It takes a leap of faith to believe it, but k is probably more lispy than certain Lisps, only you don't need to get past any parens. However, since there are no linked lists under the hood, k is not lisp, because it was designed to be fast.

#### implicit arguments

This is an an uncommon feature, most languages require you to explicitly declare function arguments. Of course you can also do that in k if you want to, but if you don't, a function can have up to three implicit arguments called `x`, `y` and `z`, which means you declare them by simply referencing them in the function body. It is a very convenient feature, not nearly as scary as it sounds:

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

Note that when calling a function with three arguments `f[1;2;3]` we had to use square brackets and use an expression separator, because each argument passed to a function is an expression in its own right. However, second function only takes one argument, and we were allowed to omit brackets — although we could also say `f[2]`.

This illustrates the core principle of k syntax — almost everything that you intuitively feel you should be able to omit, can and should be omitted. Top candidates for omission are square `[]`, round brackets `()` and space `0x20`. The lesser you type, the better your code will get.

Syntax for explicit argument declaration `{[a;b]}` is just a side remark. It is good to know, but we won't see it in this text again.

#### projection

Also known as *function view*, is a simply a reference to a function with some arguments preset to a value, and at least one **free**, or elided argument. For example, if a function of rank 3, `f[x;y;z]`, only receives first and third arguments, it will return its projection of rank 1:

```q
 f:{x+y+z}      /a function of rank three
 p:f[1;;3]      /a projection of f[1;?;3]
 p 2            /is same as call f[1;2;3]
6
```

#### rank

Function rank is another way of saying *valence*, a fancy word that describes a simple idea that is extremely important to be understood well. Rank of an operator or a function is basically the maximum count of arguments they take. Two functions shown above have ranks of 3 and 1, respectively. 

Two specific ranks are so important that they have their own names. A function or an operator that takes...

* one argument is **monadic**
* two arguments is **dyadic**

As you will see, the vast majority of native operators in `k` have exactly two completely different meanings based on the context where they are used, which is in turn defined by the number of arguments offered to the operator.

For example, when you used your first ever k operator in the expression `2+2`, you have used the `+` operator in a dyadic context since it received *two* operands to work on, left and right, so it was inferred to be `dyadic + plus`. The `monadic + flip` will be introduced later, and has entirely different semantics.

#### explicit monadics

This language construct that allows to explicitly declare an operator to be monadic regardless of its context. This is commonplace and very often necessary. Will introduce the monadic override syntax using the `+` operator as an example, and later on you will see how this works in practice.

An operator is declared to be explicitly monadic if followed by `:`:

```q
+          /context-aware, either monadic flip or dyadic plus
+:         /always stays a monadic flip, disregarding context
```

> You will not get far in this course without a strong grip on the idea that some things in k land are **monadic** and even **explicitly monadic**, while others are **dyadic**. Make sure you have it.

On a more general note, functions in k can be of rank 1 to 9:

* it is not really possible to define a function with no arguments. Rank zero, or *niladic* functions do not exist in k.
* a function cannot take more than nine explicit arguments, and some say this is an overly generous limit.


-------------------

**recap**

So far you know how to:

* add two integers
* assign values to variables
* declare and call basic functions
* be friends with `x`, `y` and `z`
* tell monadic and dyadic apart
* explicitly declare monadic ops
* annotate your code

This is a good start, but tells you absolutely nothing about what k really is, and from here things will start to get real.

## numbers

### vectors vs atoms

The word `atom` is a synonym for `scalar value`, or simply `scalar`. Every language has them, and in k they are as useful as elsewhere. But k belongs to a family of *vector languages*, which means its fundamental type is an ordered set of atoms or other ordered sets.

In k parlance, terms "array", "list" and "vector" are often used interchangeably and refer to the same thing, but we will stick with `vector` to avoid confusing you, because vectors are much more general than classic *arrays* and have nothing to do with *linked lists*. 

```q 
 x:(0;1;2;3;4)    /one way of declaring an integer vector
 y:0 1 2 3 4      /same effect using more informal syntax

 x
0 1 2 3 4
 y
0 1 2 3 4

 a:42             /a scalar variable, an atom with a name
 v:,42            /a vector of length 1, one integer item
```

k is strictly "**pass by value**", i.e. there are no references or pointers being passed around, although it is an illusion created by the underlying implementation. In reality, k avoids making copies of stuff unless it becomes absolutely necessary:

```q
 x:0 1 2 3 4     /everything is passed by value
 y:x             /so this will make a copy of x
 y               /y is a clone, not a reference
0 1 2 3 4        /(in reality it only pretends)

 y:x:0 1 2 3 4   /same effect in one expression
                 /y and x are actually the same
                 /until one of them is modified
```

<a name="v-plus-v"></a>
The first thing you need to know about vectors is that most operations you expect to work for atoms work equally well for vectors, too:

```q
x:y:0 1 2 3 4    /x and y are twin copies

 x+y             /pairwise sum of vectors
0 2 4 6 8 

 x*y             /product is pairwise too
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

 x%0             /divide each by 0, ouch
ø ∞ ∞ ∞ ∞        /∀x∈ℚ (x%0) ∈ {-∞,∞,ø}, beware (0%0) = ø, enjoy responsibly

 3%x             /divide 3 by each of x
∞ 3 1.5 1 0.75
```

<a name="v-indexing"></a>
**Indexing** is zero-based as you would expect, and if you pass a vector of indices, you get back vector of items:

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
Pairwise operations on vectors of incompatible **shape** make much less sense to k than division by zero, and will throw an error:

```q
 x:0 1 2 3 4
 y:0 1 2
 x+y
 
x+y
 ^
length error
```

Note the difference between shape and length. This reminds us that a vector can be composed not just from atoms but from other vectors as well, and there is no practical limit on the depth of nesting. In other words, vectors can have **arbitrary shape**:

```q
 y:(,1;1 1;1 2 1;1 3 3 1)    /pascal's triangle
 y
,1
1 1
1 2 1
1 3 3 1 
```

Vector arithmetic is **penetrating**, which means that vector operators *apply at depth* for as long as operands have compatible shape. It is a good time to introduce the `monadic +x` to better see how this works:

```q
 mat:(1 2 3;4 5 6;7 8 9)    /shall there be mat:
 mat                        /a square matrix 3*3
1 2 3
4 5 6
7 8 9 

 tam:+mat                   /monadic + is 'flip'
 tam                        /y is a transposed x
1 4 7
2 5 8
3 6 9

 mat=tam
1 0 0
0 1 0
0 0 1

 mat>tam
0 0 0
1 0 0
1 1 0

 mat+42
43 44 45
46 47 48
49 50 51
```

-----------------------

**practice**

First, lets make sure `+x flip` operator transposes rectangular matrices just as well as squares, which would be of little surprise. Then try to flip something less obvious, and after that you have two more transformations to apply. Inspect all intermediate results and make sure you follow their logic:

```q
 mat:(1 2 3 4;6 7 8 9)     /a rectangular matrix
 +mat                      /flip it, no big deal
1 6
2 7
3 8
4 9

 t:(,1;1 1;1 2 1;1 3 3 1)  /t is triangle vector
 t:+t                      /flip it, what gives?
 t:t>0                     /t greater than zero?
 t:(+t)+t                  /t transposed plus t?
 █
```

-----------------------

No rocket science, all pretty basic, but carry on.

### types of types

Type system in k gets strict when it has to, but also agrees that implicit casts and type coercion have their strengths — especially when done right, which in k they are.

Before we see the examples, the first thing you need to know about types in k is that they are divided into two broad classes: **vector types** and **atomic types**. That is, a vector with a single element, say, `42`, is not the same type as an atomic integer of the same value. Finally, since functions and other things in k are also assignable values, they have their place in type system too. Those are **special types** and we will not cover them here in much detail.

Here is a quick overview of basic k types and their symbolic names:

```q
atom      vect        type
  `i        `I        int
  `f        `F        float
  `c        `C        char
  `n        `N        name
  `D        `D        date
  `t        `T        time
```

This is not very revealing, so lets see them in action. The operator to query the type of anything in k is `monadic @x`, and if you are not sure what we mean by `monadic`, it is a good time to start over.

<a name="typ-num"></a>
```q
 @42         /int scalar
`i

 @.5         /float atom
`f

 @0 1 2      /int vector
`I

 v:0 1 .5 2
 @v          /0.5 promotes vector to float
`F

 v 1         /2nd item, f is short for 1.0
1f
```

<a name="typ-char"></a>
Like in C, there is no dedicated type for strings in k. Strings are just **char vectors**:

```q
 @"k"        /"k" is char atom
`c

 s:"kei";@s  /s is char vector
`C
 
 s 0         /1st element of s
"k"
```

<a name="typ-name"></a>
A type called **name** is the same idea as **internalized string** found in some other languages. This means that a single instance of an arbitrarily long string can be placed into a global hash table that persists for a lifetime of a k process and can later be referenced by its hash key as many times as necessary without creating additional copies of the string.

We could say that in case of names k actually passes *references* instead of *values*, but they are not pointers and there is no arithmetic defined for them. Names come handy in many situations, for now lets just see how they quack:

```q
 a:`kei              /"kei" is now internalized
 @a                  /name atom is its hash key
`n

 b:`kei`kei`kei      /three references to "kei"
 @b                  /vector of string pointers
`N

 @`"ken iverson"     /spaces in names, why not?
`n

 $a                  /$ converts names to chars
"kei" 
```

<a name="typ-time"></a>
**Temporal types** in k are `date` and `time`:

```q
 d:1981-02-01        /yyyy-mm-dd, ok to expect iso 8601 compliance
 @d                  /NOTE: date atom is `D same as date vector `D
`D

 t:12:34:56.789      /hh:mm:ss.sss, max resolution is milliseconds
 @t
`t

 dt:d+t;dt           /advanced date ops is a story for another day
1981-02-01T12:34:56.789 
```

<a name="typ-dict"></a>
**Dictionaries** are maps of keys to values, another way of saying *hashmaps* or *associative arrays*, and they are as useful in k as elsewhere. Keys and values can be of any type, both vector and scalar. Dictionary type name is **\`a**, and there are two different notations for defining them:

```q
 d:`a`b!(1 2 3;4 5 6)      /keys!values
 d
a|1 2 3
b|4 5 6 

 d1:{a:1 2 3;b:4 5 6}      /{k:val;...}
 d1
a|1 2 3
b|4 5 6 

 (@d;@d1)                  /type is `a
`a`a

 d`a                       /key lookup (aka d[`a] or d `a)
1 2 3

 !d                        /dict keys
`a`b 

 . d                       /dict vals (note the space!)
1 2 3
4 5 6 
```

<a name="typ-tab"></a>
**Tables** are *flipped dictionaries*, and they require a separate large discussion. We will only describe their syntax here for the sake of completeness. Table type is **\`A** and notation is the same as dict, only with `+x flip` operator prepended. Dictionary will not flip unless all values are the same length.

No comments on any of this for now:

```q
 x:`goo`apl`amz
 y:1 2 3 4 5 6
 
 t:+`s`d`p!(x,x;`D$y;1.5*y)  /table is a transposed dict
 @t
`A 
 
 t                           /trades: stock, date, price
s   d          p
--- ---------- ---
goo 2024-01-02 1.5
apl 2024-01-03 3
amz 2024-01-04 4.5
goo 2024-01-05 6
apl 2024-01-06 7.5
amz 2024-01-07 9

 select avg p by s from t   /pretend you didn't see this
s  |p
---|----
amz|6.75
apl|5.25
goo|3.75
```

<a name="typ-lambda"></a>
**Lambdas** are assignable values and have their own type, and more than one:

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

<a name="typ-nul"></a>
**Null** values in k are typed, integer null is `Ø` and float null is `ø`. **Infinity** is a scalar float `∞`. Working with nulls and infinities can be very tricky, and it is very important to pay attention to their types:

```q
 n:ø          /float null is type float
 @n
`f

 N:Ø          /int null is type integer
 @N
`i

 n=N          /equal, but not the same!
1

 @∞           /infinity is a float atom
`f
```

<a name="typ-mix"></a>
**Composite vector** type, or you could also say **mix vector**, is of special mention. Such vectors are either a mixture of atoms of disparate types, or contain something more complex than atoms, e.g. other vectors:

```q
 c:0,1,"a",2,3          /a char impostor among ints, c is mix
 @c                     /a mix type symbol is just a backtick
`

 x:(1 2 3;4 5 6;7 8 9)  /a vector of vectors is composite too
 x
1 2 3
4 5 6
7 8 9
 @x
` 
```

<a name="typ-cast"></a>
**Type casting**, both explicit and implicit, is demonstrated by the following examples which also give a general feel of how type coercion behaves. The `cast` operator in k is a dyadic `t$x`, where `t` is a type name and `x` is a subject of cast:

```q
 1+.5                  /int plus float is float, no surprises here
1.5

 1f*2                  /any float operand promotes result to float
2f 

 `i$42.99              /explicit cast from `f to `i drops mantissa
42

 `i$42.0 42.99         /`F to `i will round down the entire vector
42 42

 0+"abc"               /numeric operands demote `c and `C to ascii
97 98 99

 `c$1+"HAL9000"        /add 1 to ascii, cast back to `c, surprise:
 "IBM:111"

 "012"+"345"           /sum ascii codes of chars, result stays `C
"ceg"

 a:1 2 3               /lets start with a nice uniform int vector
 a[0]:1f               /now, replace its 1st element with a float
 @a                    /whoops, our int vector got demoted to mix
`
 a:`f$a;@a             /explicit cast to float solves the problem
`F

 `i$1981-02-01         /dates represented as ints look like this:
-15674

 15674+1981-02-01      /and they are simply offsets in days from: 
2024-01-01

 `i$2024-01-01         /so the epoch date itself must be exactly: 
0

 1+`kei                /no math for names, this type is immutable 
  ^
type error

 @@42                  /what is type name of a type name of int?
 █
```

There are things left to be said about the type system, but the expression `@@42` above (which evaluates to some kind wordplay, "type name of a type name is `name`") urges us to the next section which is all about how to make sense of this expression.

------------------

### right to left

As you must have noticed, the syntax for indexing vectors and calling functions is identical:

```q
 l:{x+x}      /some monadic function l[x]
 t:2 4 8 16   /some random integer vector
 r:0 3        /index vector: indices of r

 l[t]         /apply function l to each t
4 8 16 32

 t[r]         /items of t at indexes in r
2 16

 l[t[r]]      /compose: apply l to t at r
4 32 
```

What we also know that k actively encourages us to omit brackets whenever possible, so lets do exactly that:

```q
 l t r       /exactly the same as l[t[r]]
4 32
```

And here is comes: once we drop the brackets, it suddenly becomes absolutely natural to read this expression *right to left*. Take your time to contemplate and absorb this fact. In very little time you will see how it works in practice, and once you put it to practice yourself, you will agree that this way of functional composition is simple, elegant and intuitive:

**k expressions are read, written and evaluated right to left.**

But when we say "expressions" we don't mean "programs", and this is a very important distinction:

 **k programs are read, written and evaluated left to right.**

This might sound confusing, but look at the diagram of a small k **program** that consists of three identical expressions `l t r`, with parens added for clarity. Further down is the order of evaluation of the entire program, which leaves no room for confusion:

```q
/   L       T       R
/(l t r);(l t r);(l t r)

/   I   >   II  >  III
/(3 2 1);(6 5 4);(9 8 7)
```


#### precedence

This is another important subject which has to do with the way rivers flow in k land.

We all take it for granted that multiplication and division bind stronger than addition and subtraction and should be calculated first, and it feels almost natural that a computer language must have complex precedence hierarchy to do anything useful, and k disagrees with that:

**There is no operator precedence in k expressions unless explicitly overridden by round brackets.**

That is, by default **all operators** in a k expression are treated equally and evaluated strictly from **right to left**, and that includes **arithmetic** operators, e.g. `*` has no precedence over `+`. Here are some basic math expressions, annotated with their order of evaluation:

```q
 3+2+1     /"take 1, add 2, add 3"
6

 3*2+1     /"take 1, add 2, multiply by 3"
9

 (3*2)-1   /"take 2, multiply by 3, sub 1"
5

 -1+3*2    /same as above, without parens
5
```

It is much easier to get used to lack of precedence than you appears at first, and once you do, you will generally want to avoid using parens unless you absolutely have to. The last example from above shows the basic strategy of ditching them: it is usually possible to rearrange expressions so that the order of evaluation becomes **linear**.

Although precedence override is often inevitable and can be beneficial, it can have an adverse effect on readability. That is, when you read a k expression right to left, you want to go fast and uninterrupted, but precedence override gets in your way.

>While writing an expression, think of your reader and try to minimize the use of round brackets.

----------------

Now we can revisit the last expression from the previous chapter:

```q
 @@42     /"type name of a type name of 42" actually reads backwards:
`n        /"get 42, apply monadic @, get `i, apply monadic @, get `n"
```

Now we have a convincing proof that type name of a type name is indeed a `name`.∎

----------------

**practice**

Lets revisit the code from the first snippet in this document:

```q
 x:(1 2 3;4 5 6;7 8 9)

 x=x+1    /how can a universal truth be so false?
 █
```

Too easy, but we'll make up for it.

----------------

### no stinking loops

This part might be easier to digest than the previous, especially if you are familiar with functional programming. The title, borrowed without permission from [the legendary k resource](http://nsl.com), says it all - you will not find a k construct that resembles an explicit `for` loop, and although there is a `while` construct in k, it is almost never used in practice.

And this is not just to avoid untold damages from trivial errors people keep making in their loop definitions. The main reason explicit loops are banned from k is because k offers something better. The idea that displaces them is a simple and strong abstraction called *adverbs*, and before we see them in action, it helps to understand why they are called that way:

An **adverb** is a **modifier** that takes some **verb** (which is a short way of saying "a user-defined function or native operator"), and makes that verb's action applicable to an **input vector** in some desirable way to produce an **output**, which can be a scalar value or another vector, depending on which adverb is used.

A good example of how adverbs replace loops is `sum`. Say, we have an input `in:1 2 3 4 5`, and what we want is a sum of its elements. Thinking in implicit loops suggests something like:

```c
int sum(int[]in){
  int i=0,acc=0;
  for(;i<sizeof(in);++i)
    acc+=in[i];
  return acc;
}
```

But imagine if you could state the problem to a computer like this:

**"put a `+` between all adjacent items and give me the grand total"**

And that is the simplest way to describe what k adverb `over` does when it is used to modify dyadic `+`. Only `over`, as all other adverbs, is *general* and will happily modify *any* dyadic operator or function. Described more formally, `over` looks like this pseudocode:

1. if `x` is an atom, return `x`
2. set `acc` to 0 (a.k.a. accumulator)
3. while `next x`, set `acc` to the result of `v[acc;next x]`
4. return `acc`

The above is nothing else but a general case of the explicit loop found in `sum()`, as well as of *all other* explicit loops of this particular family. In functional speak, one would say adverb `over` *folds* a vector of values and *reduces* them into one.

And since `over` is just `v/x`, this is how `sum` function looks like in k:

```q
 s:{+/x}            /s is 'plus over x'
 s 1 2 3 4 5
15 
```

It is a good moment to look back at the C version, one last time. Be surprised to hear that its `for` loop declaration contains an ancient but ever so popular [bug](https://stackoverflow.com/questions/37538/how-do-i-determine-the-size-of-my-array-in-c), which k version does not because spotting bugs in `+/x` is much easier. Besides, even if the C code wasn't broken, it would only work for integers.

You could be tempted to see of what other use `over` could be. Let's introduce a new k operator, `!x til`, and implement another obvious candidate for `over`:

```q
 x:!9               /! is til, get first n integers
 x                  /tada, we have all ints up to 8
0 1 2 3 4 5 6 7 8

 fact:{*/1+!x}      /fact x 'mul over 1 plus til x'
 fact 10 
3628800 
```

Now that you parted ways with loops, and discussed `over` in details, it is time to meet the rest of **six k adverbs**. Please welcome the magnificent six, and note that only most trivial use cases are shown:

<a name="nsl-overscan"></a>
----------------
adverb **over** is `f/x`

adverb **scan** is `f\x`

where `f` is a `dyadic` verb and `x` is an input vector

```q
 a:0 1 2 3 4    /some data

 +/a            /puts a + between items, 0+1+2+3+4
10              /and returns the final result only 

 +\a            /scan returns intermediate results
0 1 3 6 10      /running sum, aka debugger of over
```

<a name="nsl-each"></a>
----------------
adverb **each** is `f'x`

where `f` is a `monadic` verb and `x` is an input vector

```q
 d:42,"a",`kei   /some composite vector
 fn:{@x}         /some monadic function
 fn'd            /apply fn to each of d
`i`c`n           /the type of each item

 f:{1%x},{x*x}   /reciprocal and square 
 {x 25}'f        /call each of f for 25 
0.04 625
```

<a name="nsl-eachlr"></a>
----------------

adverb **eachleft** is `x f\:y`

adverb **eachright** is `x f/:y`

where `f` is a `dyadic` verb and `x` and `y` are left and right inputs, 
either vectors or atoms

```q
 10 20 30-\:5   /eachleft does (10-5),(20-5),(30-5)
5 15 25         /each of left, substracted by right

 5-/:0 20 30    /eachright does (5-0),(5-20),(5-30)
5 -15 -25       /left, substracted by each of right
```

<a name="nsl-eachprior"></a>
----------------

adverb **eachprior** is `x f':y` and `(f':)x`

first form is `seeded eachprior` where `f` is a `dyadic` verb, and `x` is a 
seed value and `y` is an input vector

second form is `seedless eachprior` where `f` is a `dyadic` verb, and `x` is 
an input vector


```q
 2+':4 8 16    /seeded eachprior gives (2+4),(4+8),(8+16)
6 12 24        /sum 1st item and seed, then sum each item and its prior

 (+':)4 8 16   /seedless eachprior gives (4),(4+8),(8+16)
4 12 24        /first item stays as is, then sum each item and its prior
```
----------------

This doesn't seem like much, adverbs seem to be doing pretty basic stuff. But hold that thought for a minute.

**recap**

We have seen:

* what k type system looks like
* how basic vector and atom math works
* which way to read and comprehend k code
* what is the only existing precedence rule
* why there is no `for` and why there are `adverbs`

----------------

**practice**

We are back to your doubts about adverbs. Consider an example of two adverbs working together:

```q
 x:!9                       /til 9
 x+:1                       /add 1 to each of x, also x:x+1
 x
1 2 3 4 5 6 7 8 9

 x*\:/:x                    /"x times eachleft eachright x"
 █
```

Your goal is to make sure you understand the logic and the order of evaluation of this expression, which only consists of one operator and two adverbs. And you have everything you need:

* read right to left
* there is no precedence
* no explicit loops either

----------------

Bonus question:

```q
 kcc:+/∞     /how come k sums up infinity this fast?
 kcc
 █

 +\(1+!3)%0  /a tale of parens and division by zero
 █
```

k interpreter is your friend. Take your time, don't rush it, make sure you got all of it before advancing to the next chapter, where things will get a lot less innocent, and very fast.

## proverbs

### how to solve it

The title of this chapter is borrowed from a legendary book published in 1945, a small volume by mathematician George Pólya where he shows how to tackle problems and arrive to solutions. It is a very inspiring read.

Lets tackle a little problem. We will look at a k function that actually does something very useful and implements a familiar algorithm. The subject of the game is to figure out how it is implemented in k and to identify the algorithm. It is very useful to dissect all of it on paper, so put your interpreter aside for now.

So here is the code:

```q
/what is f[], and can we read it?
f:{$[2>#?x;x;,/f'x@&:'~:\x<*1?x]}
```

This little monster is deliberately designed to make as little sense as possible at first glance, but once we take it apart, you we hope you'll agree is actually very simple and readable:

```q

f:{$[2>#?x;x;,/f'x@&:'~:\x<*1?x]}

f:{...}             /f is a function, that is a good start
f:{.x.}             /f takes only one implicit argument, x
f:{.f.}             /f clearly calls f, so it is recursive

$[?;?;?]            /the entire body of f is nothing else but
$[c;t;f]            /a ctf cond, aka if-then-else aka ternary

2>#?x               /c:      boolean condition
x                   /t:      do this if c is 1
,/f'x@&:'~:\x<*1?x  /f:      do that if c is 0

2>#?x               /we don't how to read this, but it is clear that f[]
                    /halts recursion when it evaluates to 1, returning x
                    /so lets find out what it means, going right to left

                    /we have two new operators, both in monadic context:
                    /monadic ?x is 'distinct'       unique elements of x
                    /monadic #x is 'count'       count the elements of x

#?x                 /'count distinct'         count unique elements of x
2>#?x               /'greater'   true if count distinct x is less than 2

$[2>#?x;x;...]      /"if x has <2 unique items, return x, otherwise ..."
```

Coffee break, here is what we know so far:

1. the function is recursive
1. its overall control flow
2. the condition that stops recursion

This gives us confidence to wrestle down the last part, the recursion step:

```q

,/f'x@&:'~:\x<*1?x   /this must be the recursion step, read right to left:

 x:4 0 1 2           /an tiny dataset to help us see what is going on here

 rnd:1?x             /x?y is 'find': picks x random elements from vector y
 rnd                 /list with one random item from x
,2 

 rnd:*rnd;rnd        /*x is 'first': return the head element of a vector x
2

 cmp:x<rnd           /bool vector of 1s where x[n]<rnd, 0s where otherwise
 cmp
0 1 1 0

                     /~x is 'not': boolean ¬x, non-0 turns 0, all 0 turn 1

 mask:~:\cmp         /explicit 'not' scan: returns cmp and negation of cmp
 mask
0 1 1 0
1 0 0 1

                     /&x is 'where': return indices of x where x are not 0

 idx:&:'mask         /explicit 'where' each: apply 'where' to each of mask
 idx 
1 2                  /mask[0] has 1s at indices 1 and 2
0 3                  /mask[1] has 1s at indices 0 and 3

 pts:x@idx           /dyadic @ is 'index': elements of x at indices in idx
 pts
0 1                  /list of items in x less than pivot rnd
4 2                  /list of items in x greater or equal to pivot rnd


 pts:x@&:'~:\x<*1?x  /"partition x by pivot: items < rnd and items >= rnd"

 x:f'pts             /adverb each: apply f to each partition, recurse down 

 ,/x                 /,/ is 'raze': unwind aka flatten a vector of vectors
 v:,/(1 2 3;4 5 6)   /in other words, raze flattens first level of nesting
1 2 3 4 5 6
```

Now that we know what every specific part does, we can zoom out and see the big picture. Feel free to use the interpreter to play around and test your ideas.

-------------------

And of course, `f` is nothing else but:

```q
 qs:{$[2>#?x;x;,/qs'x@&:'~:\x<*1?x]}     /qsort on rand pivot

 i:9 2 5 5 1 8 1 3 6 1                   /a hairy int shuffle
 f:2.6 -∞ 8.6 π 1.7 ∞ 3.5 5.6            /a π in a float soup
 c:"edrofgtnljgrpliifp"                  /a char entropy pool 
 mess:(i;f;c)

 qs'mess                                 /restore order quick 
 █
```

And of course this is not the quickest `quicksort` ever written, but this is just a toy. In real life you would simply use the built-in operator which is a lot more efficient:

```q
 ^3 2 1                                  /monadic ^x is 'sort'
1 2 3

 sort:^:'                                /explicit 'sort each'

 (qs'mess)~(sort mess)                   /x~y 'match' operands
1 

 \t:10000  qs'mess                       /apply qs 10000 times
 █
 \t:10000  sort mess                     /fix 10000x more mess
 █ 
```

But what our DIY sort function is very good for is to demonstrate the principle of **doing more with less**, and that is what k is all about.

Check out examples of `quicksort` in the wild in [C++](https://gist.github.com/christophewang/ad056af4b3ab0ceebacf), [Python](https://gist.github.com/anirudhjayaraman/897ca0d97a249180a48b50d62c87f239), [JavaScript](https://gist.github.com/claudiahdz/39a86084edaaabe7fc17c321c0bb6896) and [Java](https://github.com/Code2Bits/Algorithms-in-Java/blob/master/sort/src/main/java/com/code2bits/algorithm/sort/QuickSort.java).

-------------------

**recap**

Previously we have seen:

* monadic `!x til (first x integers)`
* monadic `+x flip (transpose)`
* monadic `$x string`
* monadic `@x type`
* monadic `^x sort`
* dyadic `t@x cast`
* dyadic `x:y assign`
* dyadic `x=y equal`

And `qs` code brought a few more:

* ctf cond `$[c;t;f]`
* monadic `?x distinct`
* monadic `#x count`
* monadic `*x first
* monadic `~x not`
* monadic `&x where`
* monadic `,/x raze`
* dyadic `x@y index`

Although this is still a small part of k operator arsenal, if you can do `quicksort` with this much, you can do a lot more. And then add vector arithmetic, and then take everything to the power of 6 adverbs.

-------------------

**practice**

1. take another good look at the code of `qs` function
2. retrace the steps of the code analysis
3. in a new k session, reproduce `qs` from scratch

It sounds much harder than it really is. It might take more than one attempt, but you will be amazed how fast you will get there. However, before advancing to the next chapter, make sure that you do.

-------------------

The annotated breakdown of `qs` code gives a good impression of what is typically going on inside of k programmer's head, but tells you nothing about how fast it usually happens. A proficient k programmer would read and understand `qs` in well under two minutes. With a bit more practice, you will agree that reading k programs is easy and fun.

-------------------

### three triangles

It is time to write our first k program, and this time around there will be a lot less hand-holding. We will solve the classic Project Euler [p18](https://projecteuler.net/problem=18), also known as [p67](https://projecteuler.net/problem=67):

```q
By starting at the top of the triangle below and moving to adjacent numbers on the row below, the maximum total from top to bottom is 23:

       →3
     ↑7   4
    2  ↑4   6
  8   5  ↑9   3
------------------
9 + 4 + 7 + 3 = 23
```
Problems 18 and 67 are simply two bigger triangles, and the challenge is to find the **sum** of maximum paths in them. While 18 can be solved by bruteforce, 67 can not, but efficient algorithm is absolutely trivial. Is given away in the example above, we simply need to fold rows going bottom up, like so:

```q
8   5   9   3
  8   9   9         /max
  +   +   +         /sum
  2   4   6
 10  13  15         /out
   13  15           /max
    +   +           /sum
    7   4
   20  19           /out
     20             /max
      +             /sum     
      3
     23             /out
```

It is easy to see that the key to the solution is a function that *reduces* the current row (`max`) and *merges* it into the next (`sum`). It expects two arguments, i.e. both rows to work with, and returns `out`. So, lets implement it:

```q
 r4:8 5 9 3      /take two bottom rows to assist thinking
 r3:2 4 6
  
 0|42            /x|y is max: returns largest of operands
42 
 1_1 2 3         /x_y is drop: discards x items of a list
2 3 

 |':r4           /max eachprior: get max element pairwise
8 8 9 9

 1_|':r4         /drop first result of seedless eachprior

 r3+1_|':r4      /pairwise sum: merge bottom row into top
10 13 15

 row:{y+1_|':x}  /row reduction operation, x bottom, y up

 row[r4;r3]      /r4 and r3 are fine, so should be others
10 13 15
```

Great, we have the reduction function, now lets apply it *over* the test triangle to make sure it folds it into what we expect. Since we are reducing a vector into a an atom, it is very clear which adverb we want to use:

```q
 t:(,3;7 4;2 4 6;8 5 9 3)

 |t            /monadic |x is reverse the order of vector
8 5 9 3
2 4 6
7 4
,3

 row/|t        /apply row reductor over reversed triangle
,23

 *row/|t       /*x is first: simply return the first item
23

 mxpath:{*{y+1_|':x}/|x} /maximum path in triangle vector
 mxpath t
23 
```

Looks like the `mxpath` is doing pretty well. Lets fetch the input file for the problem 67, load it, parse it and solve it:

```q
 /backslash cmd executes an os command from k:
 \curl https://projecteuler.net/project/resources/p067_triangle.txt > p67.txt

 lines:0:"p67.txt"  /0:x reads a text file as vector of lines
 lines 2            /just to make sure we have something real
"52 40 09"

 t:`k?'lines        /parse each line of input as k expression
 t 2
52 40 9

 #t                 /a bigger triangle, but not a bigger deal
100

 mxpath t           /returns max path sum, the solution to 67
 █
```

We didn't tell you do this, but the complete program can also be written as a single k expression:

```q
 *{y+1_|':x}/|`k?'0:"p67.txt"   /load, parse and fold
 █
```

----------------------

**recap**

We have seen some new stuff:

* shell `\cmd`
* dyadic `x|y max`
* dyadic `x_y drop`
* monadic `|x reverse`
* monadic `0:x load text`

----------------------

**practice**

1. Reproduce `mxpath` from scratch in a new k session, same way you did with `qs`.
   
2. Find a way to load and parse the triangle from problem 18, and solve it using your own code.

3. Verify solutions for 18 and 67 on [Project Euler](https://projecteuler.net).

4. Once you provide a correct answer to an Euler problem, you can browse its discussion forum. You might want to check out some other solutions to 18 and 67 in other computer languages.

-------------------

### apples and oranges

There is no new material in this small chapter, so we can go straight to practice.

**practice**

Many things in life can only be understood in comparison. Compare functionality of these two programs:

```java
package com.less.with.more.doing.sort;
public final class qs{public void s(int[] x){}}
```

```q
qs:{$[2>#?x;x;,/qs'x@&:'~:\x<*1?x]}
```

Now, compare the source code of these two:

```java
import java.util.Arrays;  
public class S{public static void main(String[] a){ 
int[] x={5,4,3,2,1};Arrays.sort(x);
System.out.printf("%s",Arrays.toString(x));}} 
```

```bash
$ echo "^5 4 3 2 1" | k
1 2 3 4 5
```

Finally, compare the size of their runtimes:

```sh
   252M May 17 13:59 jdk-8u211-macosx-x64.dmg
    79M May 17 13:50 jre-8u211-macosx-x64.dmg
   109K May 17 13:54 k.tgz
```

----------------------

### gladly beyond

We have covered a lot of ground, good time to put things into perspective. Below is a complete map of k operators, and those marked with bullets you have already seen and used at least once:

```
   x+y         +x
-------------------------   
:  ● assign
+  ● add        ● flip
-  ● subtract   ● negate
*  ● multiply   ● first
%  ● divideby   ◦ inverse
&  ◦ min|and    ● where
|  ● max|or     ● reverse
<  ● less       ◦ up
>  ● more       ◦ down
=  ● equal      ◦ group
~  ● match      ● not
!  ● key        ● enum
,  ● catenate   ● list
^  ◦ except     ● sort
#  ◦ take       ● count
_  ● drop       ◦ floor
?  ● find       ● distinct
@  ● index      ● type
.  ◦ apply      ● value
$  ● pad|cast   ● string
```

It really feels like we have explored more than we didn't, and that is a huge progress indeed. But many things remain to be discovered, because operators is only one aspect of k — and this short introduction could not possibly cover everything.

We conclude with a list of subjects that you are now ready to explore on your own:

|k language                       |k platform                          |
|:--------------------------------|:-----------------------------------|
|additional k operators           |debugging and securing k systems    |
|tables and k-sql language        |building clients and servers in k   |
|vector aggregates                |benchmarking, testing and tracing   |
|entropy sources, math primitives |disk I/O, persistence and streaming |
|advanced use of adverbs, threads |IPC and distributed workloads       |
|native csv, tsv, json and utf    |fault tolerance and monitoring      |
|integrated cryptography core     |scripting, deployment, OS tuning    |
|nanosecond time, datetime math   |interop with Python, Julia and C    |
|k-expressions, \`0               |tech support and user community     |
|design of internal components    |k resources, tools and packages     |

-----------------

[∎](mailto:me@kel.as)
