---
layout: post
title: Balancing forces in code reviews
published: true
---

There are several things we need to keep in mind as we are writing code to deliver a certain feature. The set of things changes with time, with the sense of urgency that the feature itself requires and also with team culture.

One important thing that (at least the good) teams do and have in place, is code reviews. Each team and even each set of tools and people will encourage slightly different processes to conduct and do code reviews. Some tools make it easy to add inline comments, others are more geared towards mob programming where the code gets reviewed on the fly, as the work is being done and other tools are simply functioning as an asynchronous convergence point for the reviewer and the author to converge and check progress or append to existing work.

The common factor in all these different flavors for code reviews is the human factor: we always need a reviewer to go over the code changes we have made, and, that will always superimpose on top of all the automated tooling and processes that are in place, because, they just exist to facilitate and mediate human communication.

Here is where things can start to become more fuzzy, because, well, humans, and human interactions, are always fuzzy. A person might have an opinion about a given way to structure a certain piece of logic that you might disagree with. Or they might start suggesting other unrelated improvements to the codebase that have nothing to do with the main goal of the PR itself. What to do then? If left unchecked, this fuzziness can cause huge delays in the code review process that tend to snowball over time and delay things even longer. It's important to go into the fundamentals of why code review exists in the first place. After examining them, we can come up with a simple solution to streamline this process and make everyone happy by minimizing the "back-and-forth"ness that is inherent in this process.

### Why to do code reviews

Code reviews are proven to raise the quality bar for projects and teams who have implemented it versus teams who don't, and there are [papers](https://www.researchgate.net/publication/303099526_Code_review_quality_how_developers_see_it) written about it. This feels a bit too vague of a statement, but, even thinking about it empirically, it makes sense. If one person who hasn't written the code takes an additional look at it, surely they will find even marginal improvements that can aid with readibility or maintainability, like renaming things or using a specific pattern more suited to the task at hand.

More important than that, they will be able to validate the implementation against the specified requirements - is the PR actually implemented the change that itself was created for? Sometimes a misunderstanding in the requirements can make an entire PR obsolete. This is like a first layer of defense - if this looks good enough, the review can proceed where then the reviewer will delve deeper into the validated implementation and check for the classic things: bugs, race conditions, inneficient access to the data layer, repeated work, off-by-one errors, etc. Again, this is like being entrenched in the middle of war and having to watch for unexpected traps or things you can't (fore)see. Sometimes, even the most well-intentioned PR that is solving the correct problem can introduce an inneficiency that can later be hard to untangle yourself out of. So, you need to be vigilant. Also, we are all human, and humans are fallible, so code reviews from this lens serve a dual purpose:

- ensures that there are several lines of defense between a PR and a production deployment;
- brings the team together by sharing ownership of the work between reviewer-author pairs;

So, remember these basic principles before going into your next code review no matter as a reviewer or as an author.

### Improving the state of the art for code reviews

A way to fight back against the type of "scope creep" that is so prevalent in code reviews without you having to personally push back, is to simply nip it at the bud, i.e. make it a company or team-wide agreement that there can be no scope creep in reviews and no boyscouting. This might feel strict and, maybe it is, but, it is also extremely important because it aligns people by the same guiding principle: _code being reviewed, should be only concerned with the change it was meant to address and nothing else_.

Extra work being done on top of a usually already complex PR is a recipe for disaster. Scope and focus on the business logic gets dilluted in the middle of all the nitpicking and formatting, important details can get lost and the time to crawl through lots of unnecessary small changes increases exponentially the more you have to "keep coming back for more". 

The best way to improve the state of the art for code reviews is to simply devise a team-wide policy that needs to be followed by every member in the team, no matter if they're the most senior or if they started today. A policy can make wonders for consensus, and, simultaneously, it gives you a way out of almost any pointless discussion you can potentially get involved in. 

Policy needs not to be super strict either, simply make it give some structure to the way feedback is given while still allowing for some leeway on how each person does things. For example:

- no formatting comments allowed: defer all of that to a linter or commit hook that runs a style checker on every commit;

- no "scope creep": anything spotted by a reviewer that can be seen as unnecessary for this specific feature, can be made into a follow-up ticket; this ensures that the focus stays on the current functionality;

- have some team or language conventions and adhere to those, paying extra attention when these are being (or need to be) broken;

I think that with these guidelines in place, teams can have faster, leaner and more meaningful code reviews without going down the downward spiral of getting lost in the irrelevant details.
