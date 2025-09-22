+++
date = '2025-09-22'
draft = true
title = 'Trailing Commas?'
excerpt_separator = '<!--more-->'
tags = [ 'programming languages'
       , 'english'
       ]
+++
Trailing commas is a syntactic feature that seems odd at first sight. Why would anyone need something like this?<!--more-->

The reason for this is due to VCSs being line oriented.

If VCSs are character oriented, this wouldn't be a heavily requested feature by programmers. (Or will it? I don't know. Fight me in the comments.)

But there is an alternative to this if you're a stubborn language designer (or the maintainer of the JSON spec).

I've been dabbling in Elm (as one does). The way they write records intrigue me. 
```elm
type M
    = M
    { foo : Foo
    , bar : Bar
    , baz : Baz
    }
...
```
Elm doesn't have trailing commas. They place the first field _without_ inserting a new line after the curly brace and placing the comma _before_ the field, aligning it with the first curly brace. This is also a trend, I believe, in other, older, ML-derived languages such as OCaml, Haskell, etc.

Which is why I format all my JSON like this.
```json
{ "name": "Nutfah"
, "
}
```
