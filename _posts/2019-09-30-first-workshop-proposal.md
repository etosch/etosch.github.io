---
layout: post
title: Reflections on My First Workshop Proposal
comments: true
author:
  display_name: Emma Tosch
  email: etosch@cs.umass.edu
---

About two months ago I put together my first workshop proposal. It was a unique experience that I was able to navigate with ease due to unfailing support from my fellow organizers. While I won't post the actual document here, if you are interested in reading it, shoot me an email so I can confer with my fellow organizers and send a copy over via email.

<!--summary-->

# Overview

This was a proposal was for a one-day workshop at AAAI 2020 for evaluating reinforcement learning agents. It came out of work I submitted last year to AAAI 2019 with KDL lab mates and collaborators at Brown ([this work](https://arxiv.org/pdf/1812.02868.pdf) ended up at a NeurIPS Workshop). The two faculty members involved were [David Jensen](http://cs.umass.edu/~jensen) and [Michael Littman](http://cs.brown.edu/~mlittman). One of the odd things I'll discuss below was that I was *not* the obvious choice to spearhead this effort. Our proposal was conditionally accepted, provided that we merged with another workshop on evaluation. We ultimately found that the two workshops were actually quite different and offered to withdraw our proposal. I will be detailing our timeline and decision-making process below.


# The What: How we can to choose the topic

Workshop proposals were due on a Friday. I came across the call one week before proposals were due. It was a Friday around noon when I shared the call with fellow KDL members. We discussed possible topics for proposals, and David ultimately recommended a return to the themes of our AAAI 2019 submission. That paper came out of our explainable AI work (with Brown and Charles River Analytics): we ran into the problem that agents aren't really explainable via counterfactual reasoning (i.e., phrasing "why did you do X?" as "what would need to have been different in order to make you do Y instead of X?") and found that they can exhibit some really weird behavior under *semantic* intervention. We had one very enthusiastic reviewer, one fairly indifferent reviewer, and one hater (I see you, reviewer #2!). At issue is the fundamental way RL researchers think about how an agent should behave under out-of-sample states. In our time since submission, we've seen some other papers crop up on ArXiV that have tried to address similar questions/issues. We've been tracking them and haven't seen any published yet. Therefore, this seemed like an excellent topic for an workshop!

# The Who: How I came to spearhead this effort

After agreeing on the topic, [Akanksha](https://akanksha95.github.io/) asked who would be expected to turn around a workshop proposal in a week. [Sam](https://samwitty.github.io/) and Akanksha were away at internships. [Jun](https://junkilee.github.io/)'s primary interest wasn't really in the evaluation space. [Kaleigh](http://cs.umass.edu/~kclary) was most squarely working in this space at the time, but she was on her way out for a ten day computer-free vacation as we were discussing topics. While David would be available for comments and guidance, he did not have the bandwidth to do the writing. Furthermore, we had not yet spoken to Michael. I thought about it over the weekend before chatting with David Monday morning to make the case for why we should go ahead and do this and to explain that I sort of was the only option for writing it.

# The Why: Making a solid case that this was worth the time

David's first reaction was: what do we, as a group, get out of this, and what do you, Emma, get out of this? We had already discussed the worthiness of the topic, but we had not discussed whether it made sense for our group in particular to be doing this. One of the questions David always asks when choosing a research topic or writing grant proposals is: what are our unique competencies? KDL is really a methodology lab, and Michael is an expert in RL. Michael has been wanting to run/participate in a workshop that covers evaluation for RL for some time. We knew that there were other people out there struggling to publish on the same topic, and were not sure why communication between authors and reviewers seemed so difficult. We had a very particular set of skills that would give us the credentials to attract tastemakers in the field and potentially work through this communication impedence. We might better learn how to express our ideas in ways that fit into RL reviewer's frameworks. We might also understand our failings and the holes in our reasoning, which would help us write better in the future. We would raise the profile of KDL in this community. Finally, the point for me was to raise my personal profile during my job search (and to distract from my other work, natch!).

# The Timeline

This was the most stressful part of the process. I messaged Michael after speaking with David on Monday and made the pitch. He was enthusiastic and kindly provided a past draft for a workshop. That draft was hugely beneficial for me  -- I had no idea what a workshop proposal even looked like! I spent Monday and Tuesday working on my draft and by Wednesday morning had something I was quite proud of. The meat of the proposal was about three pages of text using the fullpage packaged in LaTeX. After working in feedback from David and Michael, the three of us started strategizing whom to ask to be on the organizing committee. This is where having both connections and time is so important, and due to the time was the weakest part of our proposal. We essentially had two days at that point to send the proposal around and find interested organizing committee members. Fortunately, Michael had just attended an RL conference and had seen a bunch of folks. Unfortunately, because that conference was so recent, it was quite likely that they were still traveling and/or behind on email. In the end, we were able to add a well-known RL researcher because she happened to be at MSR at the same time as Michael. Phew!

# The Content

I am very proud of this part. Maybe it didn't matter, but I really liked the structure of the proposal and angle I chose, so I will share that here.

I started with your standard introduction -- scope out the problem space, narrow it to the actual topic, and then hone in on exactly what we are proposing to do. The introduction was five paragarphs (just over half a page, single-spaced). After that, I organized the proposal accoding to two questions: "What should we be evaluating?" and "How do we ensure the soundness of our evaluation?" Within these two sections, I chose three representive example perspectives on the questions: "metrics," "domain," and "generalization" for the first question, and "appropriate statistical measures," "benchmarks," and "designing and selecting environments with evaluation in mind" for the second. My thinking was that we could organize the workshop into problems that fit into one of these two questions, and use the listed perspectives to drive our search for participants. I am grateful to the feedback from Michael, David, and [Phil Thomas](http://cs.umass.edu/~pthomas) (he agreed to be on the organizing committee as well) for making this as strong as it could be. There were some really fun email threads about these topics that perfectly illustrate why academic computer science is so special. :)

I also made sure to include a section on timeliness, since that was specifically called out in the call for workshops. I included a draft schedule, since Michael had one in the draft he showed me.


# The Outcome

Our notification email indicated that we were conditionally accepted, provided that we merge our workshop with another. It was not clear to me whether the other workshop organizers were asked to do the same thing -- the email included the other organizers emails, but they were not cc'ed. I thought about emailing the workshop organizers, but we recieved the notification email on a Saturday and were asked to provide a revised proposal by the the following Friday. Since at this point I was in the midst of a five-week deadline run (as in, I had a deadline/deliverable every Friday for five weeks), I wanted to get this resolved ASAP. I immediately sent out a poll to the other organizers asking to have a call on Monday or Tuesday and attached our proposal. One of the other organizers responded on Sunday with their workshop proposal. I was a little worried about the timeline because the other organizers all appeared to be in industry, in California, which could make coorindation difficult.

On Monday morning I chatted with David and said that while I would be happy to have a call with the other folks, at that point I felt that we would not be able to achieve the objectives that formed our rationale for submitting in the first place: the other workshop was on evaluation of human-labelled data and was also going to be run at HCOMP, a conference for human computation. It was a significantly different topic that would likely have little overlap in interest with our target audience.

Of course, I was sad that this was the situation. A part of me definitely wanted to fight for our workshop -- I believed in it, and we all worked so hard to turn it around! However, given the choice between merging, fighting, and folding, it was clear (given how busy everyone was) that the best thing to do was to offer to withdraw. It turned out that David was of the same mind. We talked it over with our organizing committee and after a short discussion, everyone was on the same page.

David handled the communication here on out. He notified the other workshop organizers, and then a day later sent out a short message about the situation to the overall workshop organizers. When other workshop organizers responded, they agreed that it would be hard to merge. They also complimented our proposal as well-written and well-thought-out and asked if they could use some of our ideas in the organization of their workshop.


# Conclusions

So that's that! I figured I would write up a retrospective of the experience, since it was novel to me. Even though we withdrew, I was very proud of the work I did for this effort. It was fun and collegial, and I learned a lot about the process.


# Unorganized other thoughts


__Workshops in Systems vs. ML__ It is my understanding that it significantly more common in AI/ML for students to organize workshops than it is for SIGPLAN conferences. I suspect that some of this is due to scale (an issue I've been thinking about a lot, and how it pertains to reviewing). I see this even at the institution level, where our machine learning lunches are student-run, whereas our systems and database lunches are faculty-run. This isn't because students don't rise to the occassion in systems -- it's seen as a faculty thing. I suspect that part of it is that there are just fewer graduate students in systems than in ML, so faculty would rather run systems lunches like well-oiled machines than occassionally loop in one eager student. I've also noticed that our speakers tend to be faculty, with a sprinkling of industry people, whereas in ML the speakers are primarily students and post-docs.

__Organizing work that isn't your primary area__ One of the things I've really liked about this line of work is that it *isn't* my primary research topic. It's actually given me a lot of clarity to contribute because I don't have all the emotional baggage of feeling like I need to own the ideas. More than any other project I've been on, it has felt like this work is really owned by the group. I imagine that this must be what it feels like to have graduate students.
