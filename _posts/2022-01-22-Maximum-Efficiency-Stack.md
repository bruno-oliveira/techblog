---
layout: post
title: Maximum Efficiency Stack
published: true
---

One recent tweet sparkled my interest and I decided to write a post about it. There's usually a lot of good content on Twitter that can motivate me to write and, this tweet definitely fits the bill:

 ![tweet_stack.png]({{site.baseurl}}/images/tweet_stack.png)

The basic idea behind this tweet is an important one, especially nowadays, while new stacks keep appearing everywhere and new ways of doing old things are praised in deteriment of "older" stacks that are battle-tested, proven to work and have stood the test of time. With such a proliferation of what seems to be new technology (but, for the most part, is just a rehash and repackaging of the true foundational concepts that have remained largely unchanged over the years) it can feel daunting to be "left on the station" instead of jumping on the adoption bandwagon, but, what this tweet proposes instead and that I absolutely agree with is exactly the opposite: _there's no need to jump on the bandwagon, you haven't even taken the time to explore the station properly._

The concept of _exploring the station_ is even more relevant nowadays because it gives you depth within a certain tech stack, and, when you gain enough depth and expertise, you will be able to apply all the knowledge you have to tackle new problems by leveraging old tools and the real "need" to jump on the bandwagon will simply not be there anymore. Not because you don't want to, but, because you don't need to.

There is yet another aspect of deliberately not jumping on bandwagons that can only be experienced after a certain amount of time and that is the realization that you can _maximize_ your usage of a certain stack the longer you stick with it, which means that in the long run, _not_ chasing always the latest and shiny new technology will actually be beneficial for your career and knowledge retention. Deep and focused knowledge can be several times more powerful than the counterpart of shallow and diffuse knowledge.

### Importance of going deep and focused into a single area

Knowledge use and applicability is directly proportional to the depth and time invested in learning and retaining said knowledge: at the risk of oversimplifying too much, if you know how to write an "hello world" style program in 5 or 6 different langauges, you can claim to have a high breadth of knowledge: maybe you know a bit the differences between different build systems for different langauges, maybe you get a flavor for purely functional languages instead of object-oriented ones, but, in the end, all the bits and pieces of knowledge you retain are so shallow that they are basically not usable anywhere outside of the said context of an "hello world" program. If, by contrast, you know object-oriented concepts very well, if you know how and when to apply design patterns to refactor an OO program into reusable components that make it easier to test and refactor, than you have _deep knowledge_ and such knowledge is much more useful because it's transversal to the fundamentals of the craft which means that the number of situations where this knowledge can be applied is also much larger, and that makes it much more useful.

Part of the reason why this happens is that knowledge usage is cumulative over time, as we can observe in the chart below:

 ![lindy.jfif]({{site.baseurl}}/images/lindy.jfif)

Essentially, this means two things:

- it takes time until knowledge gained _in the past_ will allow you to leverage your current knowledge usage to its' maximum potential;
- the longer you stick with the same stack, your _maximum efficiency stack_, then the more ways in which you will manage to leverage the knowledge you gained;

When these two things are looked at from the perspective of the versatility and usefulness of the knowledge you are applying and gaining, the benefits of sticking to a single stack and going really deep into it become more apparent: it's only after a lot of exposure to the same concepts and tech stack that you start realizing what you can achieve with it that you couldn't have thought possible when you had just started out learning it. 

In fact, just as you can see in the chart above, there is a certain time threshold after which your foundational knowledge starts to compound on top of all the things which you have sticked long enough with and as a result you start to expand your range of applicability within the knowledge you have in ways that you couldn't do if you had kept jumping from new technology to new technology.

The longer you stick with a certain stack, the more your knowledge will expand in depth: you will start to make more connections for example between a certain framework and the language you are using it with: you will understand how the basic building blocks of the language can be combined in ways that give birth to the huge underlying framework you are leveraging to write software.

### Jumping on the bandwagon is an antipattern 

The other important aspect worth mentioning related to the point above is that it is an antipattern trying to jump on the bandwagon for the most recent thing instead of sticking with the true and tried older tech stacks that still work perfectly. 

New technology usually stems from a specific environment where it was created to solve a very particular problem that a particular company of a certain size and scale faced, and, once the technology is deemed applicable at a broader context, it's usually open-sourced and there's a period of adoption and engagement from many companies with the technology a bit like an S-curve: adoption starts slowly, then the early adopters really expand the knowledge about it and the adoption grows fast over a very short period of time and then, as time passes, it tends to stabilize again as the companies who are more risk-averse will finally embrace it and adopt it last after all (or most of) the quirks have been ironed out by the mass adoption driven by the early adopters.

However, in many cases, certain tech stacks work just fine and many companies simply don't need to adopt any new technology to keep their business and development teams nimble and malleable to change. Adopting a new technology completely when coming from a different stack is actually a mistake in the sense that it can be seen as trying to fit a shape in the wrong peg: technology adoption should always be driven by true enablers to the current processes within your team and company and not because "everybody else" is doing it.

If you focus on your teams' needs, enabling your developers to do the right thing, focus on shipping on time and meeting your customer's needs, then the technology choices will become obvious and not the other way around.

### An example of a Maximum Efficiency Stack

For myself, simply focusing on backend development, my maximum efficiency stack is probably common to many other devs out there:

- Java + Springboot + Hibernate: this is the backbone of back-end development for me and it's what I've used so far throughout my career and it has served me very well. The statically typed aspect combined with the verbosity and ease of writing and reading code written in it largely amplify my capabilities as a developer;
- IntelliJ as IDE: essentially, any IDE that will seamlessly integrate with the above stack would be a huge plus for me, and, currently that is IntelliJ;
- Docker: Docker has become popular for local setups and development, especially when used in combination with several libraries such as Testcontainers to allow me to write integration tests that can use services, databases, and anything else I can think of all abstracted on top of a container which is very powerful to increase the resilience and confidence of local testing;

I think when combining these three different building blocks together with Gitlab for example and CI/CD, this is the stack that I can confidently return back to time and again and knowing that with some minimal effort I can deliver the most value through my work.

Obviously, different people will rely on different stacks and have different experiences, but, this is an example of mine.

### Conclusion

It's important to stay up-to-date with the recent developments in the software industry and to apply critical judgement to know when something needs to be adopted, can be researched, can improve yours and your team performance or is simply generating hype without adding a lot of value. However, as times change and new things come and go, it's also very valuable to know that you have a certain stack that you can always return back to to make things flow well for you or your team and ensure that there's a stable ground to firmly explore uncharted territory from. So, explore, experiment, try things out, but, more importantly, _find your maximal efficiency stack_ and stick with it and you will reap huge benefits.
