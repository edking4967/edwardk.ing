---
layout: post
title: "The Hidden Cost of Clever Code"
date: 2025-01-20
tags: [engineering]
---

There is a kind of code that experienced programmers learn to dread. It is not bad code — it is not sloppy or broken or careless. It is, in fact, technically impressive. It is dense with knowledge: obscure language features, elegant abstractions, the kind of thing that makes a junior engineer feel like they are looking at something written by someone much smarter than them.

It is also, in my experience, almost always the wrong thing.

<!--more-->

I ran into this at NetApp in the form of a particularly involved macro. Someone — years before I arrived — had written a C preprocessor macro that expanded to about forty lines of code. It was genuinely clever. It handled a class of resource management problems that would otherwise require repetitive boilerplate, and it did so in a single line at the call site. The engineer who wrote it clearly understood C preprocessing at a deep level.

I spent three days understanding it well enough to modify it safely. I have spent much more time since then thinking about whether the macro was a good decision.

## The legibility asymmetry

Clever code is typically written by someone at the peak of their understanding of a problem. They have been immersed in it. The abstractions feel obvious to them because they built the abstractions. The language features feel natural because they just researched them.

The person who has to read that code six months later — possibly the same person — does not have that context. They are coming to it cold. And the cost of acquiring that context is paid in full every time someone new touches the code.

This is what I mean by legibility asymmetry: the cost to write clever code is paid once, by one person, and the savings accrue to that same person in the short term. The cost to read and modify clever code is paid repeatedly, by everyone who comes after, for as long as the code exists.

In a codebase that outlives its authors — and most production codebases do — this is a bad trade.

## What "simple" actually means

I want to be careful here because "write simple code" is advice that is often given and rarely useful. Simple does not mean naive. It does not mean avoiding abstraction or writing everything in a flat, procedural style.

Simple means: the code reflects the problem it solves as directly as possible. A well-named function that does one thing is simple. A loop with a clear predicate is simple. A class whose methods correspond to meaningful operations in the domain is simple.

What is not simple: an abstraction that requires knowing about five other abstractions to understand. A function that does subtly different things depending on its arguments. A type system trick that encodes business logic in the compiler's inference engine.

The test I now use: could I explain this to a competent programmer who does not know this codebase, in under five minutes, without simplifying? If not, it is probably too clever.

## A classroom observation

I teach a unit on code review to my AP students, and every year the same thing happens. A student writes something technically sophisticated — usually involving a list comprehension with a complex conditional, or a lambda passed to `sorted()` — and when I ask them to explain it, they can. Perfectly. And then I ask them to come back in a week and explain it again, without looking at it, and they cannot.

Code is written once and read many times. The programmer you are writing for is not yourself as you are right now, immersed in the problem, caffeinated, confident. The programmer you are writing for is yourself in six months, or your teammate next quarter, or me trying to figure out what this does at two in the afternoon.

Write for that person.
