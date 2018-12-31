---
layout: post
title: Tests, Experiments, and Various Effects
comments: true
author:
  display_name: Emma Tosch
  email: etosch@cs.umass.edu
---
Reading through some software engineering textbooks, I've felt vindicated in my hunch that SE has a distinctly "scientific" feel about it. By this I mean the empiricism, adherence to the scientific method, etc., all feels quite different from other subdisciplines of CS.

For about a year now, [Kaleigh](http://cs.umass.edu/~kclary) have been chatting more and more about how testing in software engineering feels so much like experimental design. As I've delved more into the SE literature, it's become clear that that is no accident -- the [SE textbook](https://smile.amazon.com/Fundamentals-Software-Engineering-Carlo-Ghezzi/dp/0133056996) that UMass uses uses "test" and "experiment" almost interchangably in the validation chapter, and I've seen similar language and approaches in test suite generation to experimental designs such as Latin squares.

To narrow things down a bit, I've been thinking more about how to take e.g. an individual acceptance test in [Toybox](https://github.com/KDL-umass/Toybox) and think about it in terms of experimentation. In order to do that, we need to reason about counterfactuals and even candidate underlying causal models. Below is a collection of perhaps overly-detailed musings meant to help focus my dissertation writing that are deeply intertwined with conversations we have been having around XAI...

<!--summary-->

# Testing Setup

Consider the simplest test for Breakout we described in our [NeurIPS workshop paper](https://arxiv.org/pdf/1812.02850.pdf): the case where an agent is able to complete the game without dying for each final brick. We set up this test to pass if the agent could clear the final brick on the board. Implicit in this test is the counterfactual question: had the final brick been different (i.e., in a different row or in a different column), would the agent still be able to complete the game? Framed as a counterfactual, we can see that this question is really asking: does the brick position affect whether the agent can finish the game. Note that this question is different from "Does the last brick affect the agent's ability to complete the game?," which is how I might phrase it if I were not starting from the counterfactual. This seems significant to me because the counterfactual forces me to identify the quality of the brick that needed to be different. Bricks can have position, color, a location in memory, etc. It could be possible that this particular brick at this particular time for this particular agent is easy to hit because its memory location has an influence on the pseudorandom number generator that the agent uses (which for this example will have a stochastic policy).

Anyway, when we run the test, we are asserting the predicate

$$\forall b_t \in Bricks : \left(\neg\text{is_dead}(t_{b_0}) \wedge \text{is_dead}(b_{t_{max}})\right) \longrightarrow \left(\text{game_over}(t_{max}) \wedge \text{lives}(t_0) = \text{lives}(t_{max})\right)$$

The specifics don't matter a ton -- the idea is that our test's outcome is a first order statement. Also, for convenience, let's name our winning condition:

$$W(t_1, t_2) = \text{game_over}(t_2) \wedge \text{lives}(t_1) = \text{lives}(t_2)$$

Now, that winning condition was defined for a particular brick setup, which was implicit in the problem setup. To tighten things up a bit, let's instead talk about states, which encapsulate all sorts of things. For ease of reasoning right now, let's just say it's the JSON for our Breakout game. Then we have:

$$W(s_{t_1}, s_{t_2}) = \text{game_over}(s_{t_2}) \wedge \text{lives}(s_{t_1}) = \text{lives}(s_{t_2})$$

We'll start consistently using $$s$$ to mean a state and a subscript to be the features that we index on. So, in the above example, state was indexed by time. It's important for the winning condition that the game over condition be associated with the greater time index. We could have added to this predicate a conjunction with the expression $$\neg\text{game_over}(s_{t_1})$$, but that is unnecessary, given the rules of the game -- if the game were over at time step $$t_1$$, then there would be no time step $$t_2$$. Maybe you could argue that the final state of the game continues in perpetuity. I would say it only really matters if it makes your proofs easier.

Finally, as a last exercise in the testing space, let's drop the indices altogether and instead introduce a $$\text{happens_before}$$ predicate. Things start to get a little dicey here. For Breakout, because we can't add bricks, we know that at least some features of the state have at minimum a partial order. For ease of reasoning, let's assume that we are tracking time ticks in the JSON, to make this predicate meaningful. Now we have:

$$W(s, s') = \text{happens_before}(s, s') \wedge \text{game_over}(s') \wedge \text{lives}(s) = \text{lives}(s')$$

Let's end this section by saying that $$\mathcal{W}$$ is the set of states that satisfy the winning condition predicate $$W$$.

# Experiment Setup

If we think about things in terms of an experiment, we need to phrase things differently. For starters, we can express whether the agent has won at time $$t$$ using the indicator function: $$\mathbb{1}_{\mathcal{W}}(s_t)$$. Since you can only win once per game, we can then express whether an agent wins during a particular run as $$\sum_{t=0}^{\infty} \mathbb{1}_{\mathcal{W}}(s_t)$$. We're using infinity as the upper bound, since we don't know the length of time a particular game might run *a priori*, but in practice we might would that upper bound to be a $$t_{max}$$.

If both the agent and the environment are deterministic, then this is sufficient to describe whether an agent ever actually wins the game. If either the agent or the environment are stochastic, then we will want to talk about the probability of the agent winning the game ($$\mathbb{E}\left[\sum_{t=1}^\infty \mathbb{1}_{\mathcal{W}}(s_t)\right]$$, or $$P(\mathcal{W})$$). This probability can be estimated empirically, by seeding the agent and/or environment pseudorandom number generator with an appropriate number of seeds.

What if we wanted to talk not about whether the agent ever wins the game, but if the agent wins the game for a particular state configuration? We we really cared about in that previous test was whether the agent could complete the game for a particular configuration. Some coordinates $$(x, y)$$ are the last brick if the predicate $$L$$ is true:

$$L(x, y) = \forall b_{ij} \in Bricks : \left(i = x \wedge j = y \longrightarrow \neg\text{is_dead}(b_{ij})\right) \wedge \left(i \not= x \vee j \not= y \longrightarrow \text{is_dead}(b_{ij})\right)$$

Let $$\mathcal{L}$$ be the set of states that satisfy the predicate $$L$$. Let $$b_{x_fy_f}$$ be the final brick we observe while watching our agent play, and $$s_{b_{x_fy_f}}$$ be the corresponding state. Unfortunately, other important features of the state are free to vary when this condition holds. Particularly problematic for us is the ball position. Consider the following possible interpretations:

1. $$s_{b_{x_fy_f}}$$ refers to the first state where $$\mathcal{L}$$ holds (i.e., the state immediately after the penultimate brick is hit)
2. $$s_{b_{x_fy_f}}$$ refers to the last state where $$\mathcal{L}$$ holds (i.e., the state immediately before $$b_{x_fy_f}$$ is hit)
3. The collection of states an agent could be in if it follows its policy starting from (1) until (2) (i.e., on-policy states).
4. The collection of states an agent could be in if it executes any action starting from (1) until (2) (i.e., both on-policy and off-policy states).
5. The collection of all possible states expressible from the JSON, consistent with the environmental physics, starting from (1) until (2) (i.e., unreachable states).

Note that the first two conditions could be expressed in terms of temporal logic. The latter three conditions correspond to the terminology we used in the [generalization paper](https://arxiv.org/pdf/1812.02868.pdf). The latter three conditions also clearly have logical and graphic-theoretic implications, where the transitions from state to state generate a path. (3) is a single path (existential) satisfying a predicate, (4) is a collection of paths, and (5) is the union of two disjoint collections (reachable and unreachable paths). We might also think about (5) as a grammar, generating all syntactically correct statements in our "language" of state transitions, whereas (4) and (3) provide syntactic restrictions on the statements we may generate. I'll write more about this framing later, but I just wanted to throw that out there for now...

Anyway, for our tests, we restricted the situation to an unverified murky area between (2) and (3) -- we took (1) and then reset the game. This is tantamount to forcing the agent to miss the ball. Although this is technically an intervention, we could have achieved the same goal through a far more laborious method of saving states where the agent fails to hit the final ball after hitting the penultimate brick (note that this would probably have to be sampled from early in training, since well-trained agents ace Breakout).

Now we have a "control" state for experimentation, which we'll call $$s^0_{b_{x_fy_f}}$$.

# Now back to the good part!
So now we have set up the preliminaries necessary to express the experiment we want to run. We'll focus on a pared-down version, then generalize, and then discuss the challenges inherent in formally reasoning about this kind of experimentation.

The restricted version of the experiment we want is to find out whether the agent can complete the game when we move the brick to the right. Intervening on state to move the final brick to the gives us $$s^0_{b_{(x_f+1)(y_f)}}$$. If gameplay is deterministic, then we can just ask whether $$\sum_{t=0}^\infty\mathbb{1}_\mathcal{W}(s_t)\mathbb{1}_\mathcal{L}(s^0_{b_{x_fy_f}}) = \sum_{t=0}^\infty\mathbb{1}_\mathcal{W}(s_t)\mathbb{1}_\mathcal{L}(s^0_{b_{(x_f+1)(y_f)}})$$ holds. That is, does changing the environment in this one, very specific way change the outcome (i.e., whether the agent wins the game)?

This experiment doesn't tell us many things -- does it matter if the agent hits the brick right away, or does it fumble around before doing so? Does it appear to behave randomly under this intervention (which, in Breakout, would lead to immediate death), or does it appear to selecting the same sequence of actions as it had been executing before? However, if we extend it to the case where the outcome is stochastic, then we can phrase things a bit differently. Since talking about a single outcome doesn't give us much, we we will need to start talking about expected outcomes. Now the quantities of interest are $$\mathbb{E}\left[\sum_{t=0}^\infty\mathbb{1}_\mathcal{W}(s_t)\mathbb{1}_\mathcal{L}(s^0_{b_{x_fy_f}})\right]$$ and $$\mathbb{E}\left[\sum_{t=0}^\infty\mathbb{1}_\mathcal{W}(s_t)\mathbb{1}_\mathcal{L}(s^0_{b_{(x_f+1)(y_f)}})\right]$$, which are equivalent to $$P(\mathcal{W}\vert S = s^0_{b_{x_fy_f}})$$ and $$P(\mathcal{W}\vert do(S=s^0_{b_{(x_f+1)(y_f)}}))$$. If the distributions of $$\mathcal{W}$$ differ, then we know moving the brick one to the right will affect whether the agent can win the game.

This formalism only captures the specific case of moving a single brick to the right. If the change makes a difference, we may ask ourselves whehther it the fact that we moved a brick at all that caused the agent to perform differently, or whether horzontal movement caused the change. These differences could have serious implications for the agent: if any intervention on brick location causes a dramatic change in outcome, we might be left wondering whether the agent is especially brittle. On the other hand, if horizontal movement causes the problem, we might reason that some columns are harder to hit than others. In the latter case, what we are observing is that there is another, different, cause that is the true cause of the change in the agent's behavior.

There are a lot of potential hypotheses that any given experiment could be testing. Causal inference generally relies on the assumption that all variables that matter have been recorded or measured, and are represented in the graph that denotes causes and their effects. Our system allows users to trivially manipulate the values of entries in the JSON. However, we may not be manipulating what we are thinking we are manipulating. When we moved the brick one space to the right, we only reset the $$x$$ value; we did not do anything to "position" because there is no concept such as position. Sure, we organized the JSON so that most people looking at it would understand what we mean by position, but this kind of detail is easy to overlook and may be impossible for an artificial agent to learn. 

We don't know whether that particular $$x$$ value had meaning, whether rightward columns were harder, or whether there was some other, yet unknown reason for observing this effect. One of the many issues we may have is that we could be observing a direct effect when we are actually interested in a higher-level concept, such as "position." When performing experimentation in the real world, we accept this, perhaps because as human beings, we mostly share a similar understanding of reality. For agents backed by deep models, we have no idea whether x position matters, or whether the agent effectively has a lookup table from the input values to actions.
