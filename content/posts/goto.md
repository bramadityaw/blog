+++
date = '2025-11-17'
draft = false
title = 'Goto Considered Harmless'
excerpt_separator = '<!--more-->'
tags = [ 'programming languages'
       , 'english'
       ]
+++
Computing has progressed so far that a lot of our foreparents'
statements are treated like passages from sacred texts: universal
laws that don't need to be considered with historical context due
to their supposed timelessness. One such statement is Edsger Dijkstra's
'GOTO considered harmful'. This article aims to convince you that
`goto` isn't so bad these days.

<!--more-->

Recently, I watched [a video](https://www.youtube.com/watch?v=v1Mfirg2-Z8)
that compiles every `goto` statement that exists in the Linux kernel
accompanied with a rave soundtrack. It's pretty cool.

At the start of the video, you can see some angry and horrified emails
on the usage of `goto` in the kernel. Linus and co respond the usual way.
Scott Robert Ladd in particular mirrors the sentiment of this article's
excerpt in that 'your opinions about `goto` are religious, not technical'.
The video's author sneaks in a cheeky comment:

```c
// Why do we let dead dudes
// tell us how to write code?
```

[Go To Statement Considered Harmful](https://homepages.cwi.nl/~storm/teaching/reader/Dijkstra68.pdf)
talks about an observation that Dijkstra had where a programmer's
ability in his time is the inverse of the amount of `goto` statements they wrote.
He argues that `goto` statements make a program's execution hard to
follow when reading the source code, since the `goto` statement can
make the program's execution jump to non-obvious places.
When a programmer uses exclusively structured constructs
such as `if` statements or `while` loops, he argues that
the program's execution can be traced more easily, using
well defined control flow constructs that enable
what he calls a 'programmer independent coordinate system'.

Since what Dijkstra said is gospel, let us commit heresy.
Behold! A program with cross procedure `goto`!

```c
int f()
{
    foo:
        return 0;
    goto bar;
}

int g()
{
    bar:
        return 1;
    goto foo;
}

int main()
{
    return f();
}
```

Back when Dijkstra wrote the article, this could actually
be a valid program, where you can `goto` arbitrary labels.
Dijkstra discourages languages that provide this
mechanism (accept for assembly instructions, which
he acknowledged as legitimate), as it messes up the point
of structural programming and division of code into separate procedures.

Nowadays, if he were to program today, he wouldn't
need to worry. The C program above wouldn't compile,
since you can only `goto` a label defined in the same
procedure. This preserves procedural abstractions.
His vision of structured programming is
fulfilled, especially in modern imperative languages
that only allows labels as a mechanism to break out of nested loops.
