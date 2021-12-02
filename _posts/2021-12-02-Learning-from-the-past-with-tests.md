---
layout: post
title: Learning from the past with unit tests
published: true
---
Testing is almost a science in itself. There are people who love it, people who hate it, people who can't work without it. There are also different interpretations of what the benefits of testing exactly are. 

Some people like to think that it's a way of ensuring correctness of the code being written and tested, in a very tight loop, basically, TDD. This is only true under two assumptions that, in my experience, more often than not, are not always verified:

- You really need to do things in a _real_ TDD fashion: red-green cycle is imperative, otherwise, you are only fooling yourself about the correctness of the tests as an aftertought: first you need to truly write a failing test that is self-contained: interfaces and supporting classes need to exist in the code and it needs to be possible to stub behaviors where necessary to make the setup complete. Without any underlying implementation, the tests will obviously fail, and, once you have implemented the functionality and the tests pass, you know the code is doing what it needs to do and it's doing it well. It's important to not touch the tests afterwards: the perservation of the interfaces under functional code is critical for this loop to mean anything.

- Once changes are made to the functionality and tests do fail, it's a sign for you to carefully investigate the current and old interfaces and class structures under test and understand _why_ things are failing. This will mean that the underlying business domain has changed and the tests may need to be updated, but, again: it is critical that you add new tests that also cover the new changes made in as much of an isolated context as possible to validate them for correctness.

Other people simply look at automated tests as a set of pre-release tasks that are simply required to happen. It can even be "team policy" or "company policy": automated pipelines are required to be run on every commit. Usually, these people can work through and expand the test suite, but, the value they gain out of the tests is arguably lower. There's a considerable difference between doing something you fundamentally see the value of, versus doing something just because it's somehow enforced by the processes in place. That alone will impact the value you will get out of tests as an engineer.

Yet other group of people, and, this is related to the reason that inspired this post, they look at tests as "learning from the past, to avoid mistakes in the future". In this vision, tests do not exist for assessing correctness of new code or existing code under changes, nor do they exist for simply abiding a process. They exist as _lessons from the past_.

In this vision, tests are added to the codebase on the ocassion of real production failures and/or unexpected flow paths or state of the data, and they encode the gained insights from production failures from the past and embed these same insights in the code, so that similar scenarios won't resurface or, if they do by some reason, that changes in the logic can be caught by this safety net full of insights from past experiences. In this vision, tests are a mirror into our assumptions from the past, and, by ensuring their correctness we can boost our confidence that we haven't repeated any of our *past* mistakes by a few (valuable!) tests now in place.

To conclude, no matter which group you are a part of: learn and invest time and effort into writing tests and architecturing your apps, infra and developer teams to learn how to write tests. Make it so that writing test-covered code is the path of least resistance. Make quality the default. World will be a better place if you do.
