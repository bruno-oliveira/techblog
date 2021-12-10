---
layout: post
title: On the path to become a better developer
published: false
---

There are many books and blog posts and youtube videos detailing how you can advance in your career and become a better developer. Typically, advancing in your career means aiming for and reaching positions like Senior Software Engineer or Staff Software Engineer and, usually, getting to those positions, implies that, at some extent, and some point in time, you must already be performing at the required level while still being one level below the target.

Since I am a medior developer for a while now, who has worked in quite a few companies, worked with many people both more senior than me as well as of similar level and also more junior, I think I am at the best position to write about what I have been doing myself in order to become a better developer and grow into more senior roles, and also, what I've read and seen other people do that makes them distinguished as a more senior developer.

### Have great habits

As with many things, this one is quite obvious: if you want to improve, start by having great habits and encouraging other members of your team to follow you and foster such habits. Usually, these can be very small things that, when done consistently, can raise the bar for the quality of your work and the standards with which you will evaluate others' work. Examples of such habits can be:

- follow the boyscout rule: whenever possible, do marginal improvements in the codebase. Sometimes, simply refactoring a method into separate ones with more descriptive names cam go a long way. Clean up dead code, add unit tests when/during fixing a bug. Leverage IDE linters: IntelliJ is great at pointing duplication, long methods, redundant calls and at making it trivial to refactor methods. Learn how to leverage these and spread the knowledge across your team;

- keep an eye on operational things and raise alerts in relevant slack channels where and when needed: examples include for example, failed CI/CD pipelines for production releases, test coverage dropping, outages, etc. It's sometimes easy to ignore these things or wait for platform teams or others to raise the alarms, but, being proactive in either raising the issues with the right people or even working through them yourself is a great trait to have, and, again, leading by example is great since you can motivate others to do the same and gain relevant experience early;

### Writing documentation and structuring loose notes

Documentation is extremely underrated in general and it has quite a bad reputation. It's hard to maintain and it takes effort to keep updated and, more often than not, if "promoted" poorly, it can end up simply being forgotten or not really "adopted" by the team, factors which only aggravate the dislike that developers have to it.

However, documentation can come in many shapes and sizes, and, not all technical documents need to be very formal in structure or be approved by other people to be considered useful and to provide their value. In fact, one of the main benefits of "simply writing" is that it becomes almost natural to have an habit of documenting what you do by compiling loose notes, similar to keeping a [knowledge log](https://bruno-oliveira.github.io/techblog/Keep-a-log/).

As you grow into the team, the domain and also, by tapping on your accumulated knowledge from before, you can become the sole carrier of invaluable pieces of "tribal knowledge": this is the style of knowledge that compiles things like certain operations to spin up some test data, cleanup of old jobs, troubleshooting operational issues, tweak the infrastructure to test _that_ hard thing needed for _that_ type of bug and so on, and, when looked at as a cohesive unit, this knowledge is extremely valuable for newcomers and old people in the team. If you get into the habit of writing things down and take the time to refactor your own loose notes into a more structured form of documentation, you will be able to expand your influence and grow a lot by becoming someone that other people can look up to when they have questions. Besides, writing the documentation forces you to confront your own knowledge and can make you realize where the gaps lie, so, by filling in those gaps with the goal of writing documentation, you are both helping your team and yourself, which is a great way to grow your influence by increasing the confidence in your own knowledge.

### Seek growth opportunities

Another trait that's fundamental to grow as an engineer and become more comfortable in more senior positions is seeking growth opportunities with intent. Not all opportunities are the same, and, more fundamentally, not all the opportunities arise at the right time to be tackled, especially growth opportunities. I like to think of these opportunities as [stretch work](https://stackoverflow.blog/2021/08/16/using-stretch-work-assignments-to-help-engineers-grow/). Stretch work is essentially the type of work that in order to be done forces you to go the extra mile, in several different ways:

- maybe you need to integrate work with several different teams;

- maybe it's work involving a large cross-cutting concern module that affects the entire codebase;

- something that has never been done before;

By seeking these opportunities, you can establish yourself in different ways across your team members depending on your position: if you are aiming to grow towards more senior positions, it's a great way to show to relevant people that you can actually deliver and do the work that consistently puts you at a higher level. 

If, on the other hand, you are already a senior and aiming to go even higher, it can serve both as an inspiration to other colleagues, that can be motivated by your "go-getter" attitude and can take it as a nice incentive to attempt it themselves, in turn becoming better developers, which makes you act as a very efficient force multtiplier across your team, which is the most efficient way to increase your impact indirectly - if you can make others around level up to perform at your level, you have effectively "removed yourself" from their growth path as a single point of contact, which leaves you free to pursue even more challenging work.

### Learn to delegate and help

While actively seeking challenging and growth work is a great way to improve yourself at a technical level, the path towards becoming a better developer is also made of growing at a personal level and as a team player. One great way of doing that is by delegating certain bits of your work to people who are newer to the team and/or more junior to you and helping them along the way. Remember that you were once in their shoes and, while certain knowledge can be fairly obvious to you, it will certainly be new to other people, so, by delegating work with which you are familiar, you can help new people growing more accostumed to the codebase and to team processes while supporting them. This fosters a collaboration environment from the get-go to new people which helps teams gel together better.

It's also a great way to practice your teaching/explaining skills which also form a huge part of what means to be a more experienced developer - while anyone can sling out code to implement something or fix a certain bug, not everyone can articulate a technical decision clearly and practicing that while supporting other colleagues is a great way to challenge yourself in a setting where everyone can benefit.

An important part of becoming more experienced is understanding that you can't tackle every single task that would come your way, especially, as you gain domain knowledge and experience, learning on to delegate while supporting others is as important as handling things yourself.

### Focus on business impact

At the early stages of your career, and, sometimes, of a new job, even if you are experienced, there's a large chunk of your time, effort and mental energy in learning the tech stack that you are going to be using for your daily job very well. Each team will have an opinionated view on how to use a certain tech stack, how to test code, how to separate the persistency layer from the services that actually encapsulate the business logic, etc, etc. Even within well-established frameworks like, for eg. Flask or Springboot, there can be many ways of accomplishing the same task, and, what constitutes the "right way" or the "wrong way", will usually be in the eye of the beholder: maybe the way to encapsulate business logic is different now than your previous job, and, well, if you can stand behind the technical choices, it's just something that you will need to invest some time into learning. However, that can be considered the easy part, let's say.

Why? Because what matters, especially, as you gain more experience and domain knowledge, is understanding that all the code that you write has an impact. It's a nice idea to adopt a bit the mentality of seeing every newly introduced abstraction, class, method, variable, line, as being newly added technical debt. Every decision you make can and should be supported in terms of the impact it has on customers and the business that the code you're writing is powering. If you introduce a new abstraction on top of your persistency layer, and manage to turn a 12 sec query into a 3 sec query, which in turn, will make that very large and important customer be very pleased with the new generation speed of the dashboards they need, then, it's a perfectly acceptable abstraction to maintain and live with, because it directly translates into high business impact. Obviously, not all the cases will be so straightforward, but, when they are, they can be seen as opportunities to exercise your judgement as an engineer who wants to grow into a more senior role, by asking: "Is this justified?", "Do we have data in place that by doing X we can improve a certain business metric that adds value to our clients by a factor of Y?" and so on and so forth.

Having the thought, top of mind, of assessing the business impact of _any_ technical decision is a key skill to develop to become a more experienced developer. It's also very hard, because its usually very difficult to know the complete picture of the software landscape and there can be dependencies that are not in plain sight that can affect certain decisions, so, honing this skill is a key aspect.

### Keep an open mind

### Participate in technical interviews

### Mentor junior people

### Be kind and respectful

### Conclusion

These are just some of the traits that I've seen in many senior and staff engineers that make me feel like 
