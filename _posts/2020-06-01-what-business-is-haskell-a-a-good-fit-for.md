---
layout: post
title:  What business is Haskell a good fit for?
date:   2020-06-01
tags:   tech
---

From [On Marketing Haskell](https://www.stephendiehl.com/posts/marketing.html):

> It’s true that if you’re managing a software project the choice of tools does matter, but this choice pales in comparison to the following simpler ways to mitigate risk:
>
> 1. Offset the risk using as many legal and insurance instruments possible.
> 2. Having a highly liquid talent pool.
> 3. Factoring software failures into the expectations and economics of projects.
> 4. Ability to restart the project with different assumptions and team if it all goes awry.

This makes sense, within the constraints of most business environments.

But maybe it’s just a question of having the right environment to build software [properly](/blog/2014/04/28/Good-Design.html)? Is there a right business model to do so?

Most software projects still have a high risk of failure, even if you de-risk the technical implementation part significantly, say, by having a proficient team, that’s known to work well together, using a proper programming language and tech stack.

The remaining risk is usually dominated by working with wrong requirements. The problem to be solved might not be well-understood by either the customer or the engineers. Or maybe either the customer or the engineers understand, but fail to communicate to the other party. Or in the process of working on it, the problem is being better understood by one party, but this understanding doesn’t translate to the other, so requirements are not adjusted, etc. This problem might be exacerbated by contracting software development out.[^1]

For startups, risk is obviously usually dominated by non-tech issues (product-market-fit, timing, etc). But it is a business model where I see having the ability to quickly refactor and change the software as having a potentially huge upside. Correctness is even less important in startups though (I mean, Facebook was written in PHP).

[My responses on Twitter](https://twitter.com/mb2100/status/1267124635516182529) to “On Marketing Haskell”:

> Very insightful, thx! Spot on about marketing to software managers and higher ups. But isn’t choice of programming language more often delegated down, say to team lead? There the only point in your list remaining is hiring/onboarding..? That’s where I see Simple Haskell shine.
>
> Your point is basically: to higher ups, the prog-lang doesn’t matter. Which is true and (as you say) under-appreciated by us programmers. But that doesn’t answer the question why some languages end up having critical mass in industry while others don’t. Sure, marketing – but to devs.
>
> Similarly, node.js’s marketing was async+v8=speed, and devs love to think they’re writing high-speed/performance code. Why node succeeded, was of course for an entirely different reason: ubiquitous frontend devs entered the backend and a shared ecosystem was created around that.
>
> Thus not actually an entirely different reason. The marketing (to devs), enabled an influx of talent to create a decent ecosystem (even if most of the npm packages are crap, there is one okayish one for every use-case).
>
> I would also agree that Haskell’s greatest strength is correctness. Unfortunately, few devs find that an appealing argument. It implies that they’re not writing correct software in whatever language they’re currently using.
> 
> How would I rephrase “correctness” to market Haskell to other devs? Don’t know, something like “enables you to build unbreakable systems”? 🤷🏾‍♂️😁
> 
> Or maybe just “enables you to refactor quickly and fearlessly”. That emphasizes the improvements in development speed and ability to adjust to changing requirements that a strong type-system enables. That’s what industry is interested in, not “correctness”.

There is also the great point raised in [If Haskell is so great, why hasn't it taken over the world?](https://pchiusano.github.io/2017-01-20/why-not-haskell.html)

>  Haskell is not that much better than, say, Java, for many of the software systems people write today.

For those “business applications”, the advantages of Haskell are outweighed by the huge disadvantage of not having a big developer pool readily available for growing a team and quickly filling in replacements.

Also, for those business apps, what dominates the code is simply transforming data from one representation to another: i.e. I/O across system-, team- and/or human/machine-boundaries and interfaces. (That’s why I think it’s amazing that something like [Airtable](https://airtable.com) hasn’t “taken over the world” for CRUD GUIs.) But when all you need to do is read in some JSON, change one field, and spit it out again, Haskell doesn’t help you much. Its strengths only come into play once you’ve parsed the data into your [ADT](https://en.wikipedia.org/wiki/Algebraic_data_type). And figuring out what the right ADT is, boils down to defining the [semantics of the data](/blog/2014/10/05/In-Search-of-Truth-for-Knowledge-based-Systems.html), where we’re sort of back to the point about requirements.

---

To summarize: sure, better marketing to developers would help. And initiatives like [Simple Haskell](https://www.simplehaskell.org/), as well as more batteries-included libraries with more beginner-friendly docs and examples would help. And Rust seems to have made inroads using those strategies, with the help of being backed by a big, credible, player: Mozilla.

But while we’re stuck in the chicken-and-egg situation of not enough devs using Haskell, and Haskell not being a good choice in industry because of not enough devs for hire – the question remains: what business model and problem is Haskell already now a good fit for?

Or phrased differently: is there a way of working, where all other risks are reduced enough, so that the de-risking of the project by using a robust language actually removes a significant fraction of the total risk?



[^1]: But do you need to be a [tech company](https://stratechery.com/2019/what-is-a-tech-company/)? Not necessarily. But if you’re doing software as a project (as opposed to a product), you’re doomed – and sometimes, the continued investment in software isn’t worth it, if you’re not creating an ecosystem or will benefit from zero marginal costs.