---
layout: post
title: Software evolution and kintsugi
published: true
---

![kintsugi-bowl.jpg]({{site.baseurl}}/images/kintsugi-bowl.jpg)
  
Often in life, it's said that the perfect is the enemy of the good. What this means is that sometimes, it's worthy to settle on a good enough approach for doing something, even if it's obvious that there could be improvements in some areas. The issue, of course, is that the _sunk cost fallacy_ is very real, and, sometimes, attempting to reach perfection from a system that is already good enough can warrant more problems that will (in many cases) outweight the promised benefits. So, it is important to maintain a critical view on when to judge a system as being good enough for a given purpose as opposed to attempt and make it "perfect", because, in life, perfection is often elusive.

This ties in with the world of software development in the sense that _there is no perfect system_. Why? Because requirements keep evolving, conditions keep changing, stakeholders change their minds, etc. A system that is thought to be great today will be obsolete tomorrow.

### Change is the only constant

In software development, the only true constant is change. What this means is that working on and maintaining software is very much like having quicksand in your hands: you can't predict the future and, simultaneously, you can't code defensively every time or try to anticipate every possible scenario during the design stage, otherwise, your codebase will start to grow in directions that it didn't need to, and, that's how technical debt and similar issues occur, when there's code in place that wasn't needed.

However, in the face of changing requirements, it's inevitable that sometimes, code will need to be patched or adjusted under time or budget constraints, which, in turn, can make the code look "sub-optimal" from the perspective of someone who would look at it from the outside with fresh eyes. It matters, as a developer, to understand that change is constantly happening and it's important to develop the _feel_ and intuition to know when something is good enough and ship it, versus knowing when to keep polishing it. **Embrace the imperfections, that, in turn, make the code as good as it can be, for its circumstances**.

### Working code is great code

As a result of accepting that we can't write perfect code, we become more liberal and accepting of code that is good enough. So, what is code that is good enough? Well, there are many, many books, articles, conferences and posts online attempting to define what makes for code that is good enough, and, sometimes, beauty is in the eye of the beholder: what is good enough for one person, might not make the cut for someone else, and, this type of distinction also comes from the culture that is in place within the company and within your team, but, personally, what makes for code that is deemed to be "good enough" is the following:

- there is documentation available about the project _and_ it's continuously updated: documentation is a great indicator because it is **hard** to write and even harder to maintain. If people within a team care enough to maintain updated documentation about how to compile and run the code, what is the way the team works, etc, that's most likely an indication that the code itself will be in good shape.

- CI/CD is setup and easy to configure: Tied in to the previous point, if there is a setup for CI/CD in place,if it is easy to extend it and if new code when written gets easily into the pipelines, then that's a good sign that the underlying architecture will be thought out with the idea of supporting this workflow in mind, which, again, is a good sign.

- all types of tests are present: that goes for unit, e2e, acceptance and integration tests. Again, supporting all the types of tests well, requires not only a good infrastructure for testing, but, simultaneously, good undrlying architecture.

Without even looking at the code directly, these three aspects, in my opinion, will be the sign of a codebase supported by code that is good enough: good where it can be, pragmatic where it needs to be.

### Embrace the Kintsugi

[Kintsugi](https://www.artsy.net/article/artsy-editorial-centuries-old-japanese-tradition-mending-broken-ceramics-gold) is a great analogy for how to work with modern software. The idea is that you should embrace the mending bits and pieces that glue your code together and keep it working.

Even though the "ugly" parts of the code base can feel convoluted and harder to grasp, they are like the story of the code over its lifetime and they end up shaping the code that you're working with right now and they will shape and guide your current and future decisions, so, by embracing these imperfections you are honing the work of all the people who came before you and were once in the same position that you are in yourself right now.

Imperfections can feel sloppy but in most of the cases, they are the result of practicing software engineering, and, remember:

_"Software Engineering is programming integrated over time."
