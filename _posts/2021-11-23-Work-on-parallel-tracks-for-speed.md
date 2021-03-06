---
layout: post
title: Working on parallel tracks
published: true
---   
Usually, when thinking about what really makes a team move fast, the first tendency is to look at how many points the team is commited to, what is the churn, what is actually being done or not. This is usually interesting, in the sense that, while the numbers can give you some accurate measurement of speed, if you want to look at it from that angle, they don't often tell the whole story. The whole story is better told by looking at _execution patterns_, or in other words, _how_ such a velocity is achieved.

This is highly team dependent and even within each team, factors like the size of the team, if it's a team that is comprised of a _business vertical_ or a single capability, the areas of expertise of the members and so on, all affect the way velocity will change. One thing that I think is worthwhile to mention and explore is working using what is best defined as parallel tracks.

### What are parallel tracks

I like to think of parallel tracks as having "virtual" sub-teams during a sprint, working collaboratively on a small feature. The idea is that even with very small teams (eg. 3/4 BE devs, 2/3 FE devs) it is the best usage of throughput to split the work even into pairs or trios as follows:

- 2 BE devs + 1 FE dev work collaboratively on feature X;
- 1 BE dev + 1 FE dev work collaboratively on feature Y;

The idea with the parallel tracks is to create avenue-like areas of work where "Team X" can move at their own pace and independently of "Team Y". In this way, work can advance in parallel on independent features, not only naturally increasing "points throughput" but also, and more importantly, increasing value troughput. 

One of the major benefits of using this approach is that the people of each sub-team can have a higher focus for a longer period of time on a single feature, effectively increasing the code quality, diminishing future re-work and improving the ability to respond to changing requirements within the sprint that the feature is being worked on, increasing the overall agility of the team.

It's also important to realize that the way to reap the most benefits out of this approach, requires that each "sub-team" working on a given feature is a "full-stack team", with people from the BE team as well as the FE team collaborating together. Why? Well, usually, teams work decoupled between FE and BE, to allow for leeway on both fronts: if there's work which introduces a dependency between the teams, usually, in order to keep both teams independent, the planning or priorities is to be adjusted in a way that the inter-dependent work is not a problem, but, this also adds a lot of "stagger" for a given feature. If the BE team does the work and only within 2 or 3 sprints, the FE team can hop in and leverage the work done a month ago or so, it's always a big context switch and it can drag several people back into work that they thought it was done. Staggering the work allows for both teams to work on different things, but, in essence, it's still only moving the problem further down the line instead of structurally addressing it.

The best way to address this structurally, is to devise each of these sub-teams in a way that they can work indepedently on a _complete_ feature. Here, by _complete_ we mean something that can be delived to the relevant stakeholders or the customer and makes for a _ready to use_ feature. When we have people from both sides of the stack taking ownership of a given feature by ironing out details together and verifying implementation details **while** working on it, the chances of successfully delivering the right thing in time increase significantly, because the team can be agile and efficient implementing the feature and validating it with the relevant stakeholders.

When you realize that your team can operate in this fashion for a complete sprint, and, simultaneously, make great progress on several features at once, it really becomes a force multiplier for the value that your team can deliver in a sprint.
