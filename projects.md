---
layout: page
title: Projects
header: true
permalink: projects.html
---

### Toybox: Rethinking Atari Benchmarks

I have been working with [John Foley](http://jjfoley.me), [Kaleigh Clary](http://cs.umass.edu/~kclary), and [David Jensen](http://cs.umass.edu/~jensen) on developing a new testing framework for reinforcement learning. I designed a prototype version that my collaborators and I used to investigate the behavior of generalized agents in our work, [Measuring and Characterizing Generalization in Deep Reinforcement Learning](https://arxiv.org/pdf/1812.02868.pdf). I presented Toybox at the [IBM AI Systems Day](https://researcher.watson.ibm.com/researcher/view_group.php?id=9595) and as a poster at the [2018 NeurIPS Systems for ML Workshop](http://learningsys.org/nips18/acceptedpapers.html). We are currently preparing a full-length conference submission. If you are interested in contributing to our suite, please join our [Slack team](http://openthetoybox.slack.com).

[ <a href="https://arxiv.org/pdf/1812.02850.pdf">Systems4ML Paper</a> ] [ <a href="{{ base.url }}/2018-10-03-IBM-AI-Systems.pptx">AI Systems Day Slides</a> ] [ <a href="https://github.com/KDL-umass/Toybox">code</a> ] [ <a href="toybox.bib">bibtex</a> ]

### PlanAlyzer: Static Anlaysis for Online Field Experiments

A few years ago now, [Eytan Bakshy](https://eytan.github.io/) designed a DSL for online field experiments, [PlanOut](https://facebook.github.io/planout/). I had the great fortune to intern with him at [Facebook](https://research.fb.com/core-data-science/), where we investigated possible applications of static analysis to the experimental design space. While we started out focusing on generating contrasts and inferring probability of treatment assignment, we found there were errors and threats to validity of the experiments that only existed at the intersection of programs and experiments.  At various points in this project, I worked with UMass folks [Emery Berger](http://cs.umass.edu/~eberger) and [Eliot Moss](http://cs.umass.edu/~moss) on the PL side of things, and had a wonderful resource in causal inference in [David Jensen](http://cs.umass.edu/~jensen). I presented this work at [NEPLS](https://www.nepls.org/Events/29/) in 2016 and [OOPSLA 2019](https://2019.splashcon.org/program/program-splash-2019). 

[ <a href="https://www.youtube.com/watch?v=F0KdOOXKy1M&list=PLyrlk8Xaylp6enzqOraP0sSd5HzVq3DZ5&index=69&t=0s">OOPSLA 2019 Talk</a> ] [ <a href="https://github.com/KDL-umass/PlanAlyzer">code</a> ] [ <a href="https://github.com/KDL-umass/PlanAlyzer">OOPSLA paper</a> ] [ <a href=""> bibtex </a> ]

### SurveyMan: Programming and Debugging Surveys

I worked with [Emery Berger](http://www.cs.umass.edu/~emery) on a programming language and runtime system to design, debug, and deploy scientific surveys on the web. We collaborated with [Joe Pater](http://blogs.umass.edu/pater) from [Linguistics](http://www.umass.edu/linguist); this work became my [Synthesis Project](https://www.cs.umass.edu/grads/synthesis-and-ms-project), which earned an [Outstanding Synthesis Project](https://www.cs.umass.edu/oaa2015). We first presented [SurveyMan](http://surveyman.org) at the [2014 Off the Beaten Track workshop](http://popl-obt-2014.cs.brown.edu). This work won first place at the [PLDI Student Research Competition](https://www.cs.umass.edu/news/latest-news/pldi-2014-awards-emery-berger-and-plasma-students). We later presented the full paper at [OOPSLA 2014](http://2014.splashcon.org/program/program-splash2014), where it won a [best paper award](http://www.nsf.gov/news/news_summ.jsp?cntn_id=133191&org=NSF) (3 awarded in total).

[ <a href="papers/SurveyMan-OBT.m4v">OBT slides</a> ] [ <a href="http://dl.acm.org/citation.cfm?id=2660206">OOPSLA 2014 Full Paper</a> ] [ <a href="newpsla2014.pdf">OOPSLA 2014 slides</a> ] [ <a href="https://github.com/KDL-umass/PlanAlyzer">code</a> ][ <a href="surveyman.bib">bibtex</a> ]

### COSMOS: A New Experimental Criterion for Genetic Programming

Typical Genetic Programming experiments focus on the convergence of the best candidate program in a population. Practicioners often use both parametric and non-parametric hypothesis tests to compare metrics such as computational effort or mean-best-fitness. [Lee Spector](http://faculty.hampshire.edu/lspector/) and I found that the number of independent runs needed to ensure reliability of such tests varied greatly across problems. We proposed a new criterion for determining the number of independent runs required to make inferences about a set of Genetic Programming techniques. Presented at the First Workshop for Understanding Problems, GECCO 2012.

[ <a href="papers/cosmos_paper.pdf">GECCO UP Paper</a> ][ <a href="papers/cosmos_slides.pdf">GECCO UP Slides</a> ][ <a href="http://github.com/etosch/COSMOS.git">code</a> ][ <a href="cosmos.bib">bibtex</a> ]


### Older Projects

* _Creating Conversational Characters Using Question Generation Tools_.
[Xuchen Yao](http://cs.jhu.edu/~xuchen), Emma Tosch, Grace Chen, [Elnaz Nouri](http://www-scf.usc.edu/~enouri/), [Ron Artstein](http://ron.artstein.org), [Anton Leuski](http://people.ict.usc.edu/~leuski), [Kenji Sagae](http://people.ict.usc.edu/~sagae), [David Traum](http://people.ict.usc.edu/~traum). _Dialogue and Discourse_, Volume 3, Issue 2.

* _Evaluating Conversational Characters Created through Question Generation_.
Grace Chen, Emma Tosch, [Ron Artstein](http://ron.artstein.org), [Anton Leuski](http://people.ict.usc.edu/~leuski), [David Traum](http://people.ict.usc.edu/~traum/). _Proceedings of the Twenty-Fourth International Florida Artificial Intelligence Research Society Conference_

* _Compositional Autoconstructive Dynamics_.
[Kyle Harrington](http://kyleharrington.com), Emma Tosch, [Lee Spector](http://faculty.hampshire.edu/lspector/), [Jordan Pollack](http://pages.cs.brandeis.edu/~pollack). _Proceedings of the Eighth International Conference on Complex Systems_
