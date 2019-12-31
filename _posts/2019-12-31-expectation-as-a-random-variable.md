---
layout: post
title: Expectation as a Random Variable
comments: true
author:
  display_name: Emma Tosch
  email: etosch@cs.umass.edu
---

No joke, this post has been on my to-do list for *years*. I'd like to finish out 2019 by marking it done. So here we go: how should we consider the "type" of the expectation functional? Is it a random variable or no?

<!--summary-->

So first, some context: this question came up when I was teaching in 2018. I'd put it as a question on a quiz and it turned out to be significantly more controversial than I'd anticipated. At the heart of the issue is how different communities choose to define the same concept, and how context changes things.

To start with, I wrote the question with a "correct" answer of yes, the expected value (i.e., the output of the expectation functional, when applied to a random variable) is a random variable. Here was my reasoning:

1. We teach students that a random variable is a map from outcomes to the reals.
2. Expectation is a function from random variables to the reals.
3. Expectation is defined for constants.
4. Ergo, constants must be considered elements of the set random variables.
5. Ergo, the expected value is a random variable.

[Luis](https://www.linkedin.com/in/lpineda-umass/?originalSubdomain=ca) was skeptical. He pointed out that a constant is not a function, to which I replied, but it could be...a constant could also be treated as a function that takes any element of any sample space, and happens to always return the same value.

 He thought this was a bit of a hack, so we each talked to our peers and came back with different answers. As someone who still has one foot in PL, I chatted with folks who were like, that sounds perfectly reasonable to me! Types are a kind of predicate on the input, so if expectation works on constants, then constants must be members of the type that maps from events to real numbers (i.e., a function). Furthermore, we have measure-zero probability spacesthe Dirac delta, and Wikipedia tells me that there is a such a thing as a Dirac measure, so why shouldn't we generalize and treat constants this way? The folks Luis talked to were largely in AI and data science, and they were like, that's crazy, how could you ever consider a constant to be a random variable?!?! It doesn't vary!

And here, for the first time, I actually paid attention to that term, "variable," and the emphasis on *variation*. I actually had been working on a project where taking on a single variable was not enough -- PlanAlyzer. Our random assignment check needed to also include reasoning about the cardinality of treatments, since reasoning about treatment effects necessitates reasoning about at least two things. Here was a case where the overly general idea of what it means to be a random variable that I'd developed from more of a PL perspective was no longer really appropriate.

So is a constant a random variable? I'd say it depends on the context. If you know any good papers that address this question, or any other good blog posts, please feel free to post in the comments!
