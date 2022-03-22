---
title: Moving up the career ladder
layout: post
published: false
---

**Introduction**

It has been a long while since I've written here, however, that doesn't mean I've not been [actively writing](https://typeshare.co/boliveira) in other places and exploring other writing formats. Just keep writing! That has been. my motto for a while and I try to apply it to myself as much as possible.

A great deal of what I write about is actually influenced by what I read, because, when reading, I usually end up forming my own opinions and thoughts on the subject, and, 9 times out of 10, I find that with a little bit of effort in structuring, I can make a nice blog post out of it, so, here we are again.

The latest topic I've been interested on is on the overall career progression for software engineers, not only because I have some more experience under my belt, but also because it's a great way to _deliberately_ grow as an engineer to understand what the levels above yours are responsible for. It's not always easy to do those things retroactively, but, even knowing what they are can set you on an upwards trajectory because you can branch out of your comfort zone and speed up your own growth.

A great book tying closely with this topic is ["The Coding Career Handbook"](https://www.learninpublic.org/) by Shawn Swyx Wang. I've only now started with it, but, the first chapter related to career progression is interesting to dissect in further details: it's about how to well in your new role as a junior developer, or, in other words, becoming an _effective_ junior developer.

There is a lot covered in the book, but, some of the main points that resonated with me on which I will be elaborating upon are the following:

- asking good questions;

- adding value;

- grow your knowledge;

- rely on your team;

Note that some of these are based on the book, while others are my own.

I agree with everything I've read so far and, as an intermediate software developer, it's interesting to read this and look back at how my own progression went from becoming an effective junior to becoming an intermediate developer. All of the above aspects were crucial in fostering my growth and these are the type of things that will always serve you well no matter how far you are in your career. Simply, the way they will manifest and the scope they will have will look different at different stages of your career, but, for now, let's look at how to leverage this to become an effective junior which naturally fosters the transition to an intermediate developer.

**Asking good questions**

Asking good questions is [hard](http://www.catb.org/esr/faqs/smart-questions.html), because when you're beginning your career, the amount of unknown unknowns is too high. You don't know what you don't know, and, obviously being in that position makes it inherently hard to ask good questions. 

The main reasoning behind this is that it's very easy to ask bad questions: "This doesn't work, can you help me?" it's an extremely common and yet, pretty bad question. 

There are other examples of more elaborate questions that are still terrible. A better, still terrible version of the previous question could be, for instance: "I see that my code does not compile because it can't find this Jackson library to parse some JSON, can you help me?".

The main issues with both of these questions, that generalize to what constitutes a bad question, is that they don't really show a deep level of engagement with the problem behind a very superficial scratch on it. 

I like to use what I call a _depth-first_ approach to put myself on a position where I can ask better questions: the main idea is that whenever I am faced with a problem that I can't immediately figure out, there will be several threads that can point out to what the real problem is and what potential solution(s) can be.
So, here's my mini-framework on how to ask better questions:

1. Fully understand the problem

The impact of this first step can't be overstated.

It's not uncommon to not get any bang for the buck when you're asking the wrong questions. Especially when starting out it's very common to go deep down the _wrong_ rabbit hole. Usually, a combination of lack of experience, together with not a lot of domain knowledge, can make this understanding of the problem be the hardest part to get right! When something fails, it's critical to have both the context and experience within the domain to understand why the failure is occuring: inspecting design docs, reading the database schema and forming a mental picture are great enablers for the next step in our mini-framework.

2. Look in the code, issue tracker or docs for _similar_ problems that happened before

After you have formed some understanding of the issue, by getting acquainted with the domain and the data model, you will realize that your understading of the bug will likely shift from simply interpreting the error as is: "NullPointerException at line X: Customer is null" to something more contextual, like: "Okay, this service loads customer data from this importer batch job that delegates it to other service that performs some data aggregation, so, maybe the aggregation is failing at some step".

Performing this translation in our head is the single most important step you can take towards asking better questions. Why? Because you are now speaking the jargon of our colleagues and of your domain. A NullPointer is always a null pointer, but, a customer aggregation not producing the expected result? That's _interesting_! And, if it's interesting, it means it's worth exploring.

The way this exploration is done can likely vary from team to team or company to company, but, reading internal documentation, searching your issue tracker for similar solved issues or simply making chitchat with someone else on the team can go a long way.

Here it matters to state that not all teams or companies will have a culture that favors psychological safety, or, less harshly, helpful senior developers willing to hear you out. You need to get the lay of the land and adjust your approaches accordingly. Going solo is fine, it just means you need to go to step 3, the one before you finally formulate your question.

3. Attempt to write a test. No tests? Add the first one ever. Can't or don't feel comfortable? Write everything down in plain English

You're almost ready to formulate your formal question asking for help on your issue.

You've gained understanding of the problem, you've read the code, browsed the internal documentation, wikis, and looked all around Github and have an understading of the problem besides the code, you can actually frame it in terms of the domain you'll be working on. Awesome, that's great progress!

The next logical step is to attempt to codify all this knowledge into a test, any test really, can be unit test or integration test, that attempts to "challenge" your current understanding. Write a test that exercises the minimally required amount of code to spell out your assumption: "Aggregation at the service XYZ, must produce a non-null customer", or something. So, write a test, add the assertion that you expect, and, observe the test should fail, because well, there is a bug somewhere within the logic, so, if the test encodes the wrong logic, it should fail.

A decent litmus test will be verifying that after your understanding is complete and changes yet again, and you go and fix the production code, while leaving the test untouched, it should now pass.

If you can't make the test pass right away because of lack of knowledge of the underlying services or if you can't add a test straight away for whatever reason, write down your understading of why you believe the bug is happening and what the expected behaviour should be. This will further prompt you to try and reinforce your own understanding so you can write everything relevant down.

4. Ask your _depth-first_ question

Now, after your own investigations, codebase and documentation research and even, if possible, producing some written artifact about your understanding of the issue, either in code or in plain English, asking a well-targeted question is the easiest step of the process.

And, there you go, a simple framework that guides you towards doing your own research in the codebase as well as its surroundings, checking in with colleagues if possible and enhancing the codebase by adding tests. A great by-product of actually doing all of this work is that 
