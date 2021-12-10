---
layout: post
title: On the path to become a better developer
published: true
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

Keeping an open mind is also very important, and, while it has become arguably easier thanks to the huge flow of information available online and the constant innovations happening in our field, that should naturally foster a curious mind and an openess to receive innovation with open arms, there is still a huge intrinsic factor that can limit your growth as an engineer and that is the one of sticking to old habits or old technologies. While it is important to be well versed in a given tech stack and knowing things from first principles, there is a difference between knowing something and _only_ using that same something to accomplish tasks. It's easy to get biased the longer you spend under a certain tech stack, and it can shape the way you think about problems in ways that can sometimes limit you. If you only knew OOP when you started your professional career, all the problems will be seen under that same light to you. Focus on keeping an open mind and embrace change. In our field, _change is the only constant_. Some things that can help with this are, for example:

- attend workshops or conferences to stay up-to-date on the latest trends in the industry;

- force yourself to explore and learn new language features of your language of choice: even the same old reliable tech stack you know and love will grow and change over time, so try to stay up-to-date;

- if you are so inclined, learn a new language for a small hobby or side project, and try to grasp its fundamentally new ideas. You might get inspiration for your day to day work;

### Participate in technical interviews

As engineers grow within a company and/or within a certain tech stack and business domain knowledge, it's common for more experienced engineers to attend technical interviews to assess potential future colleagues. If you have the chance, seize it and attend such interviews. I personally found surprising myself that it is possible to get nervous even while being on the "other side", as an interviewer. You will also notice many different candidates, and you will see which ones are more confident, more nervous, the ones who know or don't know something, and it gives you a great insight into the more psychological factor these interviews can have on someone as a candidate.

This, in turn, will make you well-equipped in the future yourself to be able to showcase your knowledge better and project an image of self-confidence. It is important as you grow into your career that you know how to judge others and how to perform yourself under stress and this is a great opportunity to do so.

### Mentor junior people

Mentoring in an official capacity is something that, as far as I know, is still not that common in the industry, at least, not in the places where I have worked. A mentor is essentially a person who engages in an exchange with a mentee, in such a way that there can be a symbiotic relationship of knowledge sharing and transfer. As a more experienced person who has seen a few projects to completion, maybe a few of them fail and also as a person with more knowledge of both the ecosystem for developers as well as the "political arena" within a company, you can bring a lot of value to more junior people by helping them navigate the complex environment at several layers of responsibility. Knowing how to lay out the knowledge in such a way that the mentee can benefit the most from it while also making you learn in the process is a good trait to have in terms of growing in your career.

### Be kind and respectful

Last but not least, as engineers grow further into their careers, it's only natural that as their experience grows and the number of successful projects piles up, they grow a bit of an attitude of, let's say, superiority towards more junior people, or that they feel that mentoring is beneath them as they need to focus on being even more successful by themselves.

I think this is one of the most important aspects to stress out on this list: our jobs are technical by nature and hard enough even with the right team and right codebase to work with. I think it's extremely undervalued the impact that being kind and respectful can have on the performance of the team and colleagues and, the best of all, it's totally free. If you are kind and foster a culture of [psychological safety](https://blog.container-solutions.com/how-i-learned-to-stop-worrying-and-love-psychological-safety-at-container-solutions) people will naturally feel safer to speak up or raise issues without fear of being cancelled and, equally important, you will be seen as a person who is level-headed and can act according to the situations which is a very important trait to have. 

If you want to grow as a developer, leave your ego at the door and embrace a culture of psychological safety.

### Conclusion

These are just some of the traits that I've seen in many senior and staff engineers that made me want to learn from them and grow myself to be more like them. I think it's very hard to find a single person who can embody all of these aspects at the same time, especially because some of these aspects are also constrainted by the environment people are operating in, which can hinder the possibility that all of them will be seen in a single individual.

However, by learning from multiple people over several years, I truly believe that by striving to work on each of these aspects yourself, you will be able to ramp up your growth in a much more focused and efficient way than by simply wandering around the block for too long.

Most of these aspects are as much things that can be learned as things that are intrinsic to the person itself and by balancing both of these aspects, you might surprise yourself!
