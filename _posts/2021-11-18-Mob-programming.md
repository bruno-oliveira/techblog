---
published: false
---

As a developer, at least once in a while, I bet you've experienced something like this: you get assigned a ticket at a beginning of the sprint, and, start working on it. It's a relatively self-contained and small ticket, should be wrapped up in about a week's time. You make good progress everyday, no real blockers, and, after 4 days of work, interspersed with meetings in between, you add your final tests, clean it up, and put it up for review. Thursday, 12h00. With some luck, you get your review feedback today, process it Friday morning, and right near the end of the day, you can merge it and slide into the weekend with a feeling of a job well done... Except... it's never like this, right?

There are always extra meetings happening, the person who is reviewing is busy or lacks some fundamental context about the work you've done, so, we need to align there before proceeding... With this, we move on to the next week... Now, with everyone free of other meetings and having the right context, the work can finally proceed! You process a new set of comments which now touch upon some more fundamental pieces of the work...

This requires you to add more tests, maybe do some QA work by deploying this on an acceptance machine and validate that the changes still preserve the original functionality. After this, the new code you just wrote, will need to be looked at again, and, then, and only then, it can be merged. The original 4 days of "bulk work" can easily extend to take more like 7 or 8 days, and, with 10 days in a sprint, a seemingly small ticket can drag for a long time. Why is this?

I think the main reason is that the cycles of "writing the code" and "reviewing it" are fundamentally decoupled in time. This happens everywhere I've been so far. You write the code. Do your best possible work. And then the review cycle starts. Only _after_ you've done the work. 

Never truly _during_. I think this is a huge gain waiting to be exploited by more teams and more people.

This relies on the concept of _Mob Programming_. The idea is that you have always 2 (or more) people involved in the entire process, which, can't be called development process, but, instead, combines in one continuous workflow the tasks of development and review, which are to be seen as one single continuous activity constantly being done by several people.
This not only increases the time to merge, but, at the same time, it improves quality because small details are usually ironed out **right there and then**, which leaves time to look at things that can have a larger impact, like performance or real business domain correctness, for example. Obviously this doesn't mean that the formal review process should be discarded, it should still happen. The idea is to make it more of a formality because the two people involved (coder and reviewer) are now in sync on both small details and larger decisions thanks to the collaborative effort expended during the development process, so, the review was actually done _during_ the work part itself.

Obviously, there are several drawbacks to this approach that need to be considered:

- It's a big shift from the traditional way of working: this requires a change in processes that can sometimes be almost institutional and so ingrained in a certain way of working, that it can do more harm than good. It's also something that can't be "soft-tried", you just need to either do it for a sprint or two, or, not do it at all, which adds an extra resistance element to its adoption;

- For smaller teams, or teams operating in a "sub-teams" approach, where certain sub-teams are formed to tackle different tasks, it's also hard to put this process in place, because the velocity of the parallel sub-teams would eventually decrease in order to pull in more people to participate in the integrated, short feedback loop that this methodology proposes; this can be unacceptable in some settings;

- Not every person feels comfortable to be working so closely with someone else, basically coding "live" with an audience;

