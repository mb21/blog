---
title:  Pure functional programming in JavaScript
date:   2021-01-23
layout: post
tags:   tech
---

---

This is the last part of a three-part series:

- [Part 1: What is functional programming?](/blog/2021/01/23/functional-programming.html)
- [Part 2: Pure functional programming and shared mutable state](/blog/2021/01/23/pure-functional-programming-and-shared-mutable-state.html)
- Part 3: Pure functional programming in JavaScript

---

In the first part of this blog series, we looked at the functional programmimg style with some examples given in JavaScript. In the second part, we looked at pure functional programming and why shared mutable state is the root of all evil. In this final part we look at what pure functional programming can mean in JavaScript.


### React.js

By using React.js’s state handling functionality (`useState`, `useReducer`), you also avoid shared mutable state. Every mutation of state is only applied on the next re-render, so for the duration of the current rendering cycle, there is no mutation of shared state. If you need side effects (to modify state outside React), you use `useEffect`.


### Do pure functions exist in JavaScript?

[Arguably](https://hackernoon.com/do-pure-functions-exist-in-javascript-b128ed5f0ed2), in JavaScript there are no pure functions, since basic building blocks of the language can be tampered with between function calls. For example the `Array.map` prototype can be polluted, making any function that uses `.map` return something else than it did before the tampering.

But as long as you have an agreement among all programmers working on the code to not do such crazy things, the notion of a pure function is still useful in JavaScript.


### Immutability in practice

JavaScript doesn’t ship with immutable data structures, but you might think of:

- libraries like Immutable.js [used to](https://github.com/immutable-js/immutable-js/issues/1689) enjoy some popularity, but it's not the same thing as having support built right into the language, as it adds some overhead (both syntactical and in terms of dependencies).
- you can use [Object.freeze](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/freeze), but you have to remember to write that everywhere you create a new object and it’s shallow (the freeze doesn’t affect nested objects).
- the [spread syntax](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Spread_syntax) lets you easily create a shallow copy of an object or array

What many end up doing in practice is that developers sort of agree to not modify shared objects (but instead create new ones using spread syntax or using methods like `Array.concat` that return new objects). Functions using those objects are strictly speaking not pure (since they read from shared mutable state), but as long as you are confident that no other part of the program actually mutates them, you can think of them as pure functions for all intents and purposes. This may seem suboptimal (because it is), but along with things like prototye pollution, this is kind of just the way JavaScript works.

Because making lots of new objects can be expensive, in rare cases, you may also want to forgo purity in JavaScript simply due to performance reasons. (But beware of premature optimization!) These functions still don't do any I/O and except for the arguments received, they don't access non-local variables. But they may modify the objects given to them as arguments. It is then the caller's responsibility to take those modifications into account, or to not use the references to those objects anymore – which in the absence of Rust’s borrow checker, is of course a lot easier said than done and can be the cause of bugs.