---
layout: post
title: A Basis for a Mathematical Theory of Computation
comments: true
author:
  display_name: Emma Tosch
  email: etosch@cics.umass.edu
categories:
 - reading-list
---

It perhaps should not surprise me that there are not histories of PL the way there are histories of other sciences: computer science is such a new discipline and most overviews of how things came to be currently live in blog posts. I think it would be fun to have a history class that treats earlier academic papers as primary sources and strives to understand the cultural contexts of intellectual trends. Maybe this is too niche, but a history of the academic paper would also be very cool, and might help us as a community address better address its shortcomings in light of changing technologies, cultural norms, etc.

Anyway, I'm trying to read classic papers related to the topics covered by my thesis. Since my research is interdisciplinary, I've been thinking about how to address some of the common questions and misconceptions that come up when folks trained in, say, machine learning, interact with folks trained in programming lanaguages. Today I'm posting on John McCarthy's 1963 paper [A Basis for a Mathematical Theory of Computation](https://ropas.snu.ac.kr/~kwang/4190.310/mccarthy63basis.pdf) (the link is to the correction).

**TL/DR Version**: The intro to this paper is interesting for the perspective it gives on the field at a point in time, but the particular formalisms have evolved since then. Students of PL would be better served working through Software Foundations to learn and appreciate McCarthy's approach. A later paper, such as Wright and Felleisen's "A Syntactic Approach to Type Soundness" would probably be a more useful primary source.

<!--break-->

# Introduction 

One of the things I like about this paper is the refreshingly high level view of the current state of comptuation, circa 1963. The second sentence of the introduction presents computation as "the science of how machines can be made to carry out intellectual processes," and states matter-of-factly that "We know that any intellectural process that can be carried out mechanically can be performed by a general purpose digital computer."  What's interesting to me about this statement is how it can feel like this perspective on what computation bubbles up cyclicly. I have the impression that the computing community routinely tries to branch out into other disciplines, overextends itself and its metaphors, and then recoils in shame for a bit to the fundamentals, before the next generation of researchers attempts to apply principles of comptuation to a broader swath of problems once again. 

McCarthy seems certain in the introduction that the fundamental weaknesses of computers lies in the poverty of expression of state of the art programming languages. Although developments in numerical analysis, automata theory, and computability theory had helped elucidate the nature of computation, McCarthy expresses a concern that they are too narrow in scope (numerical analysis), not narrow enough (computability theory), and culturally geared toward purely theoretical research questions (automata theory). He feels that there is a missing link in the quest to prove properties of real computer programs that users actually run.


McCarthy lists three programming languages in his introduction: ALGOL, COBOL, and UNCOL. McCarthy essentially dismisses these three languages with a disdain that would not be out of place on Reddit or Hacker News, but I might interpreting his take on UNCOL as a sicker burn than it actually is. There is definitely both sass and humility in this paper ("We hope that the reader will not be angry about the contrast between the great epectations of a mathematical theory of computation adn meager results presented in this paper") that makes it a more interesting read than most. In any case, McCarthy's main concern is that none of these languages gets at the universal language of computation that would permit proofs of equivalence under transformation, etc.

# Formalisms

McCarthy starts with a setup that should be familiar to most students of programming languages: he defines what he means by computable functions, gives formal definitions and examples for various S-expressions, and defines the evaluation rules for expressions. I believe that this is mostly a rehash of his earlier paper that outlined LISP. I've definitely used these function definitions when working through the older version of Software Foundations. I think most students would be better served by working through Software Foundations to learn these concepts than by reading through this part of the paper.

The section on "ambiguous functions" is interesting to me because I've never heard this terminology used. It sounds like "ambiguous functions" are meant to be relations. It also sounds like the definition of an ambiguity operator could be used for subtyping of some kind (especially due to McCarthy's use of "heridtary" when describing subsets of ambiguous functions' domains), but the implications of the ambiguous function are not obvious to me.


# Properties

This section starts with what amounts to a presentation of logic, i.e., a semantics for computer programs. It serves primarily to illustrate how the syntax described in the previous section of the paper can be unified with a logical semantics to express properties of computer programs. The specific theorems presented here again look like exercises from Software Foundations. 

# Relation to Other Formalisms

This section seems particularly relevant for historical context. Proof systems for computer programs have developed far beyond what was proposed in this paper. This section portrays what McCarthy is attempting as a very nascent undertaking. The main comparisons that can be made are the study of recursive functions in the tradition of Church and computability theory as expressed via Turing machines. It seems the main intellectual contribution from McCarthy is his emphasis on higher level control, specifically through the if/switch-function.


Some stray observations:
* One of McCarthy's goals is to be able to express programs symbolically so that major changes in program behavior can be represented by small change is in the program representation. He then writes something about programs "learning from experience" and ends this point asserting that "having a convenient representation of one's behavior available for modification is what is meant by consciousness." Everything old is new again! He even ends the paper with the assertion that the whole point of computing as an undertaking is the development of artificial intelligence. 
* Another of McCarthy's goals that I would imagine might start recieving more attention is point 5, "To give a quantitative theory of computation" a la Shannon. 
* This paper predates the development of the C programming language by about six years.
* McCarthy cites his forthcoming paper "Computer Programs for Checking Mathematical Proofs." I tried looking this up and Google Scholar only gave me a link to a citation, no paper. How much earlier work is left uncited because we haven't re-typed and indexed old papers?
