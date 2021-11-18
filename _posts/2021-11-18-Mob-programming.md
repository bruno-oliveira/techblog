---
published: false
---

As a developer, at least once in a while, I bet you've experienced something like this: you get assigned a ticket at a beginning of the sprint, and, start working on it. It's a relatively self-contained and small ticket, should be wrapped up in about a week's time. You make good progress everyday, no real blockers, and, after 4 days of work, interspersed with meetings in between, you add your final tests, clean it up, and put it up for review. Thursday, 12h00. With some luck, you get your review feedback today, process it Friday morning, and right near the end of the day, you can merge it and slide into the weekend with a feeling of a job well done... Except... it's never like this, right?

There are always extra meetings happening, the person who is reviewing is busy or lacks some fundamental context about the work you've done, so, we need to align there before proceeding... With this, we move on to the next week... Now, with everyone free of other meetings and having the right context, the work can finally proceed! You process a new set of comments which now touch upon some more fundamental pieces of the work...

This requires you to add more tests, maybe do some QA work by deploying this on an acceptance machine and validate that the changes still preserve the original functionality. After this, the new code you just wrote, will need to be looked at again, and, then, and only then, it can be merged. The original 4 days of "bulk work" can easily extend to take more like 7 or 8 days, and, with 10 days in a sprint, a seemingly small ticket can drag for a long time. Why is this?

