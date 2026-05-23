---
layout: post
title: "On Teaching Students to Debug"
date: 2024-09-15
tags: [teaching, engineering]
---

The first thing I noticed when I started teaching computer science was that students do not know how to be wrong. They type a line of code, run it, see an error, and immediately start changing things — deleting, rewriting, guessing — without ever stopping to read what the error actually says.

I recognized this immediately because I had done it myself. Not when I was a student, but at my first job, writing C++ for storage firmware at NetApp. The codebase was enormous — millions of lines, subsystems I had never touched, behaviors that emerged from the interaction of components written by engineers who had since left the company. When something broke, the temptation was always to poke at it: change a flag, recompile, see if that helped. It was faster than thinking. It was almost never faster than thinking.

<!--more-->

What I eventually learned, and what I now try to teach, is that debugging is a discipline with a method. It is not a feeling — the frantic energy of trying things until something works — and it is not talent. It is a set of practices that can be named and practiced deliberately.

## Read the error

This sounds obvious. It is not obvious to a fifteen-year-old who is embarrassed that their code does not work and wants to fix it as fast as possible.

An error message is information. It has a type (`TypeError`, `IndexError`, `NameError`), a location (line number, file), and a description. These three things together almost always tell you what is wrong. The location tells you where Python thinks the problem is; the type tells you what kind of problem it found; the description tells you what, specifically, went wrong.

Students learn to read error messages the way they eventually learn to read compiler output: reluctantly at first, then with genuine appreciation when they realize the compiler is trying to help them.

## Reproduce it reliably

Before you change anything, you need to be able to make the bug happen on purpose. If you can't reproduce it, you can't fix it — you'll just change something at random and convince yourself the problem is solved until it reappears.

This is harder than it sounds in classroom code because students' projects are often small enough that reproduction is trivially easy. But the habit matters. At NetApp, some of the worst bugs were timing-dependent: they appeared under load, on specific hardware configurations, at specific moments in a multi-threaded sequence. The engineers who fixed them quickly were the ones who started by understanding the conditions that made them reproducible.

## Narrow the search space

Once you can reproduce the bug, you need to figure out where it lives. The fastest way to do this is binary search: find the midpoint of the suspicious code, add a print statement (or a log, or an assertion), and ask: is the bug before or after this point? Then repeat.

Students find this boring. They want to find the bug, not conduct a methodical search for it. I spend a lot of time explaining that the boring systematic approach is almost always faster — and more reliably faster — than intuition and luck.

---

The deeper lesson, which I am still learning to articulate well, is that debugging is fundamentally about maintaining an accurate model of what is happening. Bugs exist in the gap between what you think the code does and what it actually does. The way to close that gap is not to change things until the gap disappears but to narrow it — carefully, deliberately — until you can see exactly where your model diverges from reality.

This is a skill that transfers. It applies to firmware and to Python games and, I suspect, to a lot of other things. The ability to sit with a broken system, resist the urge to thrash, and think carefully about what you actually know — that is worth teaching directly, because most people will never figure it out on their own.
