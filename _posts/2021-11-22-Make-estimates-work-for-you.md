---
layout: post
title: Make estimates work for you
published: true
---   
Recently, we've been experimenting at work with looking at ticket estimates under a different light than always. As many other software companies, we've ended up falling victims of the mantra: more points = more value, and, well, this can create some really awkward icebreakers in retros and other meetings, where the focus shifts towards looking at the "net negative space" instead of focusing on real progress. 

The driver for conversation becomes "what went wrong?" when the sprint points fall short of The Average™, instead of "what was The Value™ delivered in the sprint?". This feels like a waste of effort, because tying value to number of story points is a completely artificial correlation that _definitely_ does not imply causation. The biggest examples we see of this, are the "tickets" that we can solve over a slack call, or a coffee with a customer or a manager or PO, simply by chatting or reframing a given problem under a different perspective. What if instead of measuring points completed, we could measure something like: "time not wasted chasing a wrong solution"? I bet in some cases, not all of course, but some, the value "gained" would be very high and just as impactful, if not more, than smashing your point record. This is because the inherent value of the work can't be fully quantified with a discrete scale of points, but, instead, by other discrete metrics that stem _from_ the work delivered but are only visible down the pipeline, like: attrition rate, customer satisfaction, number of bugs reported over X weeks for feature Y, impact of outages, etc. If **these** numbers align, then it means we are doing a good job, regardless of the points. So, after all, why do we need points? Why do we have points at all?

### It's all about predictability

Points are proxies for future work efforts, based on previous efforts. In essence, with points, we can have a somewhat reliable approximation of exactly how much work the team can do in one full sprint in terms of a combination of things like holidays, team capacity, urgency of the work and planned work, in such a way that we can predict with some degree of certainty how much we can complete in a given timeframe. Usually, this desire for _having_ these numbers in the first place, stems from product teams wanting to ensure completion of roadmap items by a certain date, or to tell a deadline to an important client, etc. However, I think that this is the wrong frame of mind to have regarding the way points work (or should work).
Part of the problem here is that when we attempt to extrapolate these "sprint-level" estimates to timelines that are more appealing to other stakeholders, so, quarters, or half a year or so, the estimates end up falling short by a factor that can't be seen as non-negligible. In essence, it doesn't extrapolate because it's a way of working that spans over the course of several sprint windows where priorities are adjusted or shifted, but, always within that "sprint period", so, when asked to give larger estimates based on points, it can be dangerous to extrapolate the sprint estimates, because the points weren't designed for this.

### An alternative - to make estimates work for you

The best way to use estimates, at least in my perspective, is to have a concretely, well-stated and well-defined "sprint goal", articulated in such a way that it can be always tied to some form of business value, or, if it's a more technical or internal effort, at least, tied to a goal that states exactly what we want to achieve by day X. Some examples include: 

- "New users endpoint queries should leverage native queries for performance reasons. Queries should be faster than 2s.";

- "Deliver first 3 endpoints for feature X";

These goals are immediately understood by fellow colleagues and stakeholders, they deliver some form of technical value or support an upcoming feature or functionality, and both these sprint goals can be tied to real customer needs or a piece of a roadmap vision.

Within a 2-week span, the way this will be done, and, _especially_ how many points it will take, is basically irrelevant if something is not delivered as part of the Sprint goal established originally. So, you know, when you spend a sprint and you only did 2 endpoints for feature X, then, it doesn't really matter if it was 21, 34, 13 or 100 points. What matters is that the goal to deliver that value increment for the product or your customers (we can be lenient here and assume that customers are also for example our FE team colleagues) was not achieved, and, _that_ is what we should be talking about. The creation of value or the lack of ability for creating that value. 

If we shift the discussion in that direction, we will learn much more useful things about everything and everyone: the needs of other stakeholders and customers will be laid bare before us to evaluate, maybe the goals and our capacity to deliver real Value™ has been underestimated, and our capacity to work as a team unified towards a single goal can also be evaluated and discussed.
No matter how you look at it, this is a much more interesting and engaging discussion to have than talking about the missing points or lack of predictibility.
