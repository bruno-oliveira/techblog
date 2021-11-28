---
layout: post
title: Learn on-demand or in-bulk?
published: false
---
An interesting post on the HN Ask section, posed a question that prompted me to write this short piece:

"Which one is better - a) Read all books/blogs/... about the relevant technologies related to a project and start working b) Read books/blogs/... on need basis as you keep working on your project."

This is a really interesting question and, critically looking at it, I believe there are two sides to it: if you are working on a personal project, there is a certain approach you can take, and, if you are working at your job, probably the exploratory aspect will differ a little bit, because the environment and the tools at your disposal are also different, so, I will try to approach this interesting question from both perspectives.

### Learning for a side project 

A side project is essentially a greenfield project where you will wear ALL the hats. You'll have to be the developer, the main stakeholder, the main client (sometimes), the main customer relations person and the main contributor. 

This means that no matter the complexity of the thing, you are in complete control. You can work on it as much or as little as you'd like to and there won't be any extra pressure to deliver. This is a great opportunity to broaden your horizons and try out new technologies. As such, I belive that learning on demand here is the best: you open up a tutorial, finish it, try to tweak it to do what you are trying to accomplish, repeat ad eternum. 

I think in this scenario, learning on demand is good because you're like a one man army and working as a full stack, there will be parts of one side of the stack that you'll be less familiar with, so, learning on demand can bring you the most outcome here. 

### Learning at work

Learning at work is a bit different than working on side projects, because the context is very different too. The code you're writing will be read, maintained and modified by others and more importantly, it will exist to support your company's business, so, taking a "greenfield project" approach to working on a given feature at work poses more of a risk than when doing it for a side project.

The idea at work should be to try as much as possible to stick to existing patterns and both _before_ and _during_ the work being done, take an hybrid approach between on-demand and deep learning:

- you should attempt to look up anything you may require, first, in your own codebase: chances that someone else worked on a similar feature before are relatively high and, since it's all "in-house", it should already be implemented using the patterns that best match your codebase. This is the on-demand piece of the work: you conduct a search through the codebase when you realize that there is something you might need somewhere

- once you find it, the time for the deep learning part comes in, and, this is where you will usually have to do a deeper dive to understand the contexts from both "ends": your own, related to the feature you are currently working on. Why did you realize you needed "this" specific thing in the first place? Grasping the context within your work is important. Then, the next step is understanding the context from the perspective of the "implementer site" where you found an already existing implementation.
In a sense, you're doing the work of an "adapter pattern", right? You are taking apart different contexts that are apparently linked through their need of "having implemented" a given feature, and you are adapting an implementation to ensure that the commonality shows so that your feature becomes complete.

At work, it's fine to take opportunities to use a full-on exploratory approach as well. When trying out a new technology to improve some infrasructure related area of the codebase for example, or when working on a previously agreed upon process improvement within the team, where usually the contexts are less restrictive and there is room to try out new things and experiment. These are situations where, due to their nature, it's completely fine to try out something entirely new. A word of caution though, for, if you get these things to gain traction within the team, they will have to be maintained, adpoted and understood by your colleagues, and they will have to go through the process of becoming embedded in your codebase and workflows. It's useful to document and write down key points of this "embedding" process, in order to make these initiative adoption easier and more straightforward for other people who will have the same desire for innovation.

### Conclusion

It is important to understand the two approaches of deep, bulk work and on-demand work, know when to use one or the other and leverage them for their strengths where possible. Being well-versed in both will make you better at innovating and also better at doing deep-dives, and, I'd argue that you need both aspects to become the best developer you can be.