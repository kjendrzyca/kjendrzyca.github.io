---
layout: post
title: Smuggling good practices
categories: []
tags: []
published: True
date: 2015-07-20
comments: true
---

Every devoted software developer has his private super sexy side-project on the private computer where the code is good and where magic unicorns live. We love those projects. We are proud to present them to other people.

Why do we have those projects? Well, I don't know all of the reasons but:

- some people are excited about how cool things can be (for me this thing is React)
- some are tired of their boring projects they need to implement at work (for me - constantly writing CRUD apps in Angular)
- some just want to have fun because they love to code in their favorite language (for me this thing is JavaScript)

When working on this #notworkrelated code there is less pressure and we have time and energy to focus on writing complicated things the easy way, to communicate through code in the most elegant way, to use design pattern that is the best in this one specific case. We can feel like Neo after loading up the Kung fu program - we know things.

And then we come back to work. Often that is not a place for magic unicorns.

<span class="more">--</span>

## Good and bad practices
Since I started my career as software developer, I constantly find people talking about good practices. SOLID, DRY, YAGNI, Clean Code in general, TDD, BDD, DDD, refactoring, pair programming, code review and so on.

We know and love them all, don't we? At least, I love the ideas behind most of them. In my opinion everyone should be familiar with those practices. Most of them are fundamental knowledge we need to learn to be able to work efficiently with other developers. Reading 1000 pages of C# book and memorizing everything is not enough.

But the fact is that despite all those super-fancy methodologies and techniques, **the code we are working with on a daily basis is often just an untamed piece of shit**.

[![Source: http://photos.rossfinlayson.com](/img/Shit_Fountain_sculpture.jpg)](http://photos.rossfinlayson.com/index.php/Trips/Project49/37-Illinois/DSC_0782)

I don't have a lot of experience but I have seen pretty disgusting things already. Examples?

8 levels of inheritance (no composition at all) with messed up abstraction levels, where JS scripts were loaded from database in UI layer and injected straight to the UI. Then, the mighty eval was parsing them. That was the only way to write JS for this app. And this was UI intensive app with complicated logic that could be easily managed with any of the existing frameworks or libraries. But no, someone decided to just write spaghetti jQuery everywhere. 1000 lines in one file. They give me something like that after 3 weeks of professional coding and expect that I will make a code review with smile on my face. No unit tests (because it's hard to test js right? We need to wait for the next century to see that coming). Well, how can you tell that person that he is an idiot in the polite way? Difficult stuff.

More?

Method that has 3000 of VB code, using Hungarian notation and abbreviation for every variable and method name. Good place to stay for the night.

Things like "well, we have *X* (a lot) global bool flags in this class already, adding one more won't make a difference, let's do this and finish this functionality ASAP". Senior developer said that. Difficult stuff.

Data warehouses written entirely in dynamic SQL (4 files, over 1000 lines of code each). All that without using any version control system.

Angular controllers that have 600 lines of code because client "just wants MVP". #nodirective #noneedtothink.

You can think that I'm whining here. Nah, not anymore. Since everything that I've mentioned is just normal for this industry I think we as developers are responsible for doing something about this repulsive state of the code we see every day.

## Problems
Developers I know constantly have problems with few common things:

### Lack of time
The most popular one. People are often telling us that there is no time to do things right. We should just focus, use the simplest solution there is (stackoverflow all things) and deliver ASAP.

### Technologies we need to use
Sometimes we just don't like something. Sometimes the technology we use is inadequate for the job and it's not possible to do things right using it - like dynamic SQL warehouses (and changing the technology or framework would take the oh so precious time).

### Non-technical managers that are hard to convince that refactoring is a part of our job
Well, I've met a few people that were deaf to the technical arguments of development team, no matter how hard they tried. Some business people just don't want to believe that swimming in spaghetti code is making the team slow at implementing new features. It makes no difference for them if it is ```if-else``` block (multiplied by ten) or elegant [strategy pattern](http://www.oodesign.com/strategy-pattern.html).

### Co-workers who don't know yet that writing ugly, duplicated code now will kick their asses later
Or they don't give a shit. They just want to sit their 9-5 job and make money. Because writing code is easy. Making it maintainable and readable is hard, never-ending activity. But they don't care.
I've heard of people that are proud of themselves because the company they are working for cannot fire them - they cannot be replaced because only they know how some particular piece of code works.

### Random shit
Hearing about this shit is as easy as going to the kitchen and listening to the coworkers that always have something new to complain about.

But you know what? It doesn't matter. You are the only person that can do things right. Not managers, not technology, not co-workers. You. I think of it as a responsibility.

## Solution
I was disappointed by the quality of the code I've been reading every day. But I discovered that **the key thing and often the only solution is to smuggle good practices to the code.** No one will pay you for that. Most people don't care. But believe me - you will save a lot of sanity points for you and friends in your team that will use this code later.

How to do it?

Same rules as when smuggling drugs (I don't know anything about smuggling drugs, just watched some movies, so I'm making things up here).

### 1. Find reliable partners
Working alone is a lot harder. Especially when you try to smuggle good code and practices. Find people that think like you so you can double your chances.

### 2. Find a good place to start the business
Not every piece of code is worth making it better. You cannot do it whenever you like. Someone may be implementing new functionality connected to the code you want to touch. Let them avoid merging hell.

### 3. Prepare and provide solid and tested stuff
People need to see that the new approach is better in some way. When people will realize that your stuff is good they will look for more.

### 4. Start small
Starting big will give you troubles with local ~~cops~~ managers immediately. They will see big changes as a possibly wasted time and will try to stop you.

### 5. Be consistent
Never stop. It will be hard to do things better but eventually you will get used to that. It will become your secret weapon.

## Summary
Sometimes, someone just needs to start to think differently. Do things some other way and see what happens. Challenge others to think, once at least in a while. From time to time people will catch up and start to mimic those examples and smuggle good practices with you.

Some time ago I was skeptical about writing anything in AngularJS. In my opinion this framework encourages people to write bad code. But together with some members of my team we started to smuggle little improvements to our workflow. We tried different patterns, to structure code differently. And while it's still a pain in the ass to write something using this framework we feel better about it. Also people around us are grateful that there are less WTFs in the air around us.

I hope I encouraged you (even if a little) to think differently about bad and good software practices. Please leave your comment and let me know about your solutions to that problem.