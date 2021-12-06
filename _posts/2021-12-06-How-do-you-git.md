---
layout: post
title: How do you git?
published: true
---
Using git as a system for version control is more and more becoming the standard way of keeping your code versioned for its changes. There is probably a minority of companies that don't use it, but, most of them will, and every company does it differently. The way a company uses git (or not at all) can tell you a lot about its engineering culture and what is valued within the development teams by the leadership.

When leveraged correctly, using git can be a great tool to ensure that all the team is aligned on what moving code from development to production means both in terms of quality and also of the approach taken when managing feature branches. Let's see some different aspects of how several teams use git. Note that this is based on my current experience and on reading several blog posts detailing different approaches, so this is not an exhaustive list and its meant to be used more as guidelines or a sort of checklist on what is (or isn't) being done within a team. Let's see some approaches.

### Merging directly to main 

One of the main approaches that some teams take is to merge code directly to the main branch, so, the production branch, without requiring any approval or code review after the code is written. This approach has some advantages that can be a real strength on strong teams with good practices and test coverage:

- code is finalized faster since there's no process in place _after_ the code is written. Simply finalize it and merge it.

- prototyping can land faster in production if deemed valuable.

There are also a few drawbacks of course, and, the main one is that if there's any correlation between the way git is used and the quality of the code being written and the way the team works, it is _less likely_ that a team will be a highly-functioning team if it uses git in this way, since obviously this way of working is a bit more risky than having a process in place that ensures quality of the code going into production, which is also one of the drawbacks:

- code quality can suffer in the sense that if code gets merged directly without being reviewed, we can introduce inneficiencies or bugs that would otherwise be caught.

- lack of consistency across different PRs. If we merge code in an ad-hoc fashion, the codebase can quickly become inconsistent in the sense that each person will write things in a certain way which can affect consistency and decrease maintainability in the long run.

### Creating a branch and enforcing a reviewer to review the changes

By creating a feature branch and enforcing a code review before merging, we get an assurance that an extra pair of eyes looks over the code with a fresh perspective and can flush out new potential bugs and also ensure that the new code follows the team standards for quality and consistency.

While it means that sometimes the lead time between opening a new MR and merging it into production can grow when compared to the previous approach, it also means that the assurance of correctness will increase which in turn means that there is less time spent on fixing bugs or ironing out post-production issues, which means that there is more time to focus on feature development. So highlighting advantages and disadvantages:

Advantages:

- quality and consistency are enforced during a code review. It keeps the code being reviewed to the same standards as existing code which is good for the team and the health of the project;

- people learn the importance and impact of doing code review - details are usually flushed out and chances of introducing bugs are lower than when no review happens;

Downsides:

Downsides are mainly operational but, are usually so minimal compared to doing things the right way that it's simply not worth to dwell over these:

- lead times increase: reviews usually take time and require the attention of multiple team members;

- if people do start a review and have to switch to any task with higher priority the review time is basically undefined and impossible to determine which can be a bottleneck in some situations;

### Conclusion

When working with git, make sure that in order to reap its benefits to the fullest, you integrate it with a review policy that requires the review and approval of at least one more team member. By doing so, you ensure that knowledge regarding the domain is also spread across multiple team members which is an advantage in itself.
