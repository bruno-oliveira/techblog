---
layout: post
title: Atomic habits & Programming
published: true
---

I've just recently finished reading the book "[Atomic Habits"](https://jamesclear.com/atomic-habits) by James Clear, and, it's a very fascinating book that touches upon the power of making tiny changes to achieve remarkable results. The main takeaway can be boiled down, in simple terms, to a simple idea: _what could you achieve if you focused on getting 1% better than yesterday, every day, for a year?_ Doing some math, we can arrive at the following two formulas that illustrate this difference clearly:

1.01^365 = 37.783..

0.99^365 = 0.0255..

The idea is that improving by 1% every day will lead you to extraordinary results, and, conversely, slacking off over time can make you really hit rock bottom in terms of your performance and achievements. This might look like a very obvious statement and that's because it is. What is really hard to realize and make happen is to _really_ put in the daily effort. Every single day. Without a fail. This can be extremely hard to do. It's easy to slack off, let life get in the way or lose motivation, but, ultimately, the real recipe for achieving success is to show up and _consistently_ put in the effort. Only then it will be possible to achieve good results. Be it with running to get in shape or coding features with your colleagues at work, there really is no magic recipe besides _showing up every day and put in the effort._ In fact, according to the book this trait of relentless consistency is what distinguishes a professional from an amateur or from someone who is not truly commited.

At our job, it's easy to show up every day, because we have a contract we signed that stipulates the hours we need to put in daily. Day after day, week after week, year after year. Besides this, our jobs, and I will now drill down specifically into programming, as this is my area of work also offer very tangible rewards in the form of nice appraisals from colleagues, nice features delivered to clients, a sense of belonging and achievement and all these factors contribute greatly for making writing code for a living almost into a habit.

Note that while I say almost here, that is a very important classifier. An habit is something one can do without thinking after having perfected it over time in such a way that it can be done almost in auto-pilot. Programming or, better put, developing and writing software is far from being classified as an habit on its own, because it's something that requires constant engagement, exploration and thinking and it's far from being of the passive or more auto-pilot nature that habits normally tend to become associated with.

However, at our jobs, we are constantly operating at several layers of "engagement", such as, attending meetings, gathering requirements, talking to clients, actually writing code, debugging issues, helping colleagues, etc.

When all of these activities are considered as a whole, a bit like looking at a mountain range from afar, the bigger picture can never be seen as something you do on auto-pilot, it requires engagement and context switching and constant focus. However, within each of these layers, there are some things we can actually make an habit out of in a way that we can reap benefits from them by using our mental capacity in the best way possible. I will touch upon the 4 laws of habit formation exposed in the book and make a paralel with some of the tasks we are faced with as developers on our daily job. The 4 laws described in the book are: _make it visible_, _make it attractive_, _make it easy_ and _make it satisfying_. Let's look at some examples based on these 4 laws and see how to apply them at a micro-level for some of the tasks we are faced with every day while we need to write software. Bear in mind that these will be simple examples that are presented to illustrate the power of these concepts as drivers for finding things that can be improved over time. As with everything, these can be made as simple or as complex as you'd like and can be adjusted to fit almost any situation.

### Make it visible

Making things visible in the context of software engineering is a full-time job in its own right: whether you are a data scientist looking to make sense of data or a developer working in observability or tools to aid with debugging, distributed tracing, etc, making things visible is often the first most important step to take in the direction of the desired improvement we want to make. A bit like the idea that _you can't measure what you don't know_, the same is true for developers.

If you don't know you have a performance problem in a very critical query, or if you don't know your RDS instances are nearing full-on storage, you can't take action. So, the first rule of fostering good habits in the context of coding is: make things visible. Take proper time to sync with your devOps or Platform teams (hell, create one if it doesn't exist yet!) and make things visible: a centralized place to look at logs from a production machine, a Slack bot configured to send alerts when storage goes whack. Email alerts, etc. There are many possibilities that can be explored here, but, the main point is: make things visible and fine-tune them so you get only alerts for what is truly relevant in any given context: nothing is on fire when everything is on fire. With the right settings, observability is a very powerful tool to leverage within your teams and company as a whole.

### Make it attractive

This can be a more subjective law to follow in the context of writing software, but, usually, it all starts with a bad consequence that can be avoided, and, by tweaking it, you can get something positive out of it: _this query is super hard to make performant, but, if we don't do it, client X will keep complaining and we might lose them. ===> Let's focus our energy on fixing this so we will keep client X, maybe land Y as well and we will get some nice contracts next quarter._

If the whole team can be rallied behind an attractive goal for everyone involved, it will make it easier for every person involved to be a bit more commited towards the goal, to push themselves further, grow and trust in the process and knowing that in the end, on the other side, the team will emerge stronger from a technical point of view and be well positioned to achieve a nice attractive goal.

### Make it easy

Developers have complex tasks at hand almost daily, and, anything that can be made easy, should be: tell them where to find the devOps guy when a pipeline breaks and they will be able to know who to go to when something gets broken.

Foment a culture of knowledge sharing and psychological safety so that doing the right thing becomes the default: ask questions, share tribal knowledge, promote and foster writing documentation that is version controlled so that it makes it easy to find the right pieces of information at the right time and do the right thing. If they have their local development environments set up for success, it will be easier to write unit tests, if they are reliable, they will run them more often and find more bugs and areas of improvement. If all it takes to get a preview pipeline deployment environment live is run a Maven command, they will get behind it.

Focusing on automating and making the right things easier to do is setting up people for success and it's a huge force multiplier that every team should strive to achieve.

### Make it satisfying

When a job is well done, everybody wins. Developers feel happy because a hard task is now behind them, they learned something new and challenged themselves and everybody grows.

A great point to make here is to focus on sharing customer success stories with clients directly with development teams for example: when developers know, first-hand, from a client be it someone else within the company (like a different department) or an external client showcasing their appreciation to a Product Owner, it's important to let these small wins trickle down and reach the folks who were actually writing the code to make these features a reality. People love having some recognitions from a job well done and it will motivate them to keep doing their best. What is enjoyable, is more likely to be repeated and that can happen at large-scale efforts as well as on the smallest of details. The important is to recognize the importance of praising a job well done.

## Conclusion

We saw how the 4 laws described in the book "Atomic Habits" can be mapped at a very high level to some of the tasks that developers need to do everyday by looking at their jobs as a continuous stream of many different tasks that form a coherent picture when looked at a whole. Each of these laws can be seen and mapped to smaller sub-tasks within some contexts of the job of a programmer and how they can guide and orient teams towards functioning better both as their own cohesive unit as well as integrating themselves better within the larger context of the organization.

There can be many more possible mappings for these laws at different levels of granularity and types of tasks, and, you can try to explore it by yourself and see how well they suit you for your particular context or team.

PS: The book touches upon much more than what fits in this post, and, I highly recommend any developer or manager to read it, in case you haven't yet.
