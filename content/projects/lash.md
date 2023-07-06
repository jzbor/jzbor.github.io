---
title: "Lambda Shell"
date: 2023-07-06T23:48:27+02:00
description: "
A simple REPL shell for [untyped lambda expressions](https://en.wikipedia.org/wiki/Lambda_calculus).
It provides provides named terms, reduction strategies and capture-avoiding substitution and extends lambda calculus by macros and directives.
"
---

[Github](https://github.com/jzbor/lash) ⨳ [Documentation](/lash)

{{< param description >}}

# Examples

There are builtin terms `SUCC` and `NIL` to create natural numbers using church numerals:
```
[λ] @usestd
@usestd

[λ] one := SUCC NIL
one := SUCC NIL

[λ] two := SUCC (SUCC NIL)
two := SUCC (SUCC NIL)

[λ] !normalize (ADD one two)
\f . \x . f (f (f x))
```

You can select different reduction strategies at runtime:
```
[λ] @usestd
@usestd

[λ] !vnormalize (AND TRUE FALSE)
AND TRUE FALSE
(\q . TRUE q TRUE) FALSE
(\q . (\y . q) TRUE) FALSE
(\q . q) FALSE
FALSE

[λ] @set strategy normal
@set strategy normal

[λ] !vnormalize (AND TRUE FALSE)
AND TRUE FALSE
(\q . TRUE q TRUE) FALSE
TRUE FALSE TRUE
(\y . FALSE) TRUE
FALSE
```


