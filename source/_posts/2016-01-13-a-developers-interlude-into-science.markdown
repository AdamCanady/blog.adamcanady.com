---
layout: post
title: "A developer's interlude into science"
date: 2014-11-25 00:06:44 -0600
comments: true
categories: 
---

*This post is a work in progress*

Science is great. It's awesome to see the ways people use math to describe the world and how clever abstractions help us understand nature better.

This term, I'm in a couple physics courses and a chemistry course. As someone whose courseload has been dominated by computer science courses, it's hard not to relate everything back to CS.

A few notable examples below.


## Chemistry
### Chemical Naming
Ever since I learned how to name molecules according to some basic IUPAC rules, I really have wanted to write a program to represent molecules as data and figure out how to name them according to the rules. This is one of those things where there is a well defined written algorithm for it, but it may or may not have been implemented yet. My professor indicated that a program called ChemDraw can do this, but sometimes/often gets the name wrong.

### Chemical Structure Analysis
Using NMR and IR spectroscopy, we can determine a lot about a molecule's structure. Each time I sit down with a problem set or an exam question, it's easy to start applying the algorithm I've developed 

I have some thoughts on how this could be automated. Perhaps if you had a sufficiently large training set, it would be possible to machine learn strucutres for compounds.

<!--### Chemical Reactions-->



## Physics
### Visualization of equations
One of the things I really detest about the way physics is currently taught is that the student is just spoonfed a few equations, then told to solve some problems. I feel like that's a doable way to learn, but it's suboptimal because the student isn't really invested in the problem. An alternate teaching style would be to give a student sufficient instrumentation such that they could come up with a solution to describe a phenomenon like simple harmonic oscillation on it's own, but in practice this isn't really feasible due to time constraints. That also seems like a suboptimal solution.

I wonder if there's some middleground, where computer simulations (D3 + worrydream.com's work) could help manipulate a system in real time to give a student intuition about what's going on behind the scenes.

Side note: one thing I've found more and more is that people get really caught up in notation and it's likely that use of better notation would lead to better understanding of a system. In my opinion, computer scientists are better at naming variables (even though, according to XKCD, it's the hardest problem in comp sci). When I see an omega on the board, that doesn't really symbolize angular velocity so much as the variable name angular_velocity would. Doing math in programming languages is easier and more clear despite the excess activiation energy required to type the variable name.
