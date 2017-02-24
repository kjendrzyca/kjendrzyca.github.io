---
layout: post
title: Dances with Yaks
categories: []
tags: [software development, refactoring, yak, yaks]
published: false
date: 2017-02-27
comments: false
---

![yaks](/img/yak-main.jpg)
*Image by [Dmitry Sumin](https://www.flickr.com/photos/dmitrysumin/)*

Meet Erik. Very proactive and always ready to help Node.js developer.

![Erik](/img/erik.jpg)

Erik got a task to add GeoJSON validation to the REST service they are working on in the project right now. He decided to write his own piece of validation because not a single NPM package covers all the edge cases he needs to cover.

<span class="more">--</span>

In his project they have a separate package that holds all kind of generic functionality, it's called `common-utils`. Erik needed to add the validation to the `common-utils` package and then reuse it in the REST service.

He started the work, entered the flow zone and proceeded with very enjoyable TDD session. It felt really good. At some point, he had to throw some exceptions (after all this is a validation plugin). The problem was that all the errors in the project are held in another package - `common-errors`.

It seemed as a quick change. Erik cloned the `common-errors` repository, added the new errors, created the pull request, and after some time he continued working on `common-utils` validation. He discovered that the `common-utils` used very outdated `common-errors`. What a surprise. When he bumped the version in his `package.json`, half of the unit tests stopped working.

He couldn't leave it like that. There was no choice, he decided to fix all the red tests first and then continue with his original task. He created a new branch in the repo just for the `common-errors` version bump and started fixing the tests. Some errors were replaced by others and some changed their interface so fixing the tests quickly became burdensome. He needed to investigate everything case by case and watch out to not break anything. All the REST services in the project depend on that functionality.

It took some time but, eventually, all tests become green again. Erik created the next PR with the fixes and got back to work on his validation.

After a while the validation was ready. Erik needed to merge the previous PR to create a new one with finished validation.

Unfortunately, there were 22 comments waiting for him. It turned out that in some cases he made the wrong choice in replacing the old errors with new ones. Another thing to fix. In some cases, he didn't agree with the comments and raised the discussion with the team. And discussions on generic solutions could take forever...

After a lengthy debate and a whiteboard session, they agreed on what to do. There was another problem, though. They discovered that the scripts responsible for running tests on docker containers had to be updated. `common-utils` was very outdated. That's the cost of migrating everything to new ES.

Erik got back to work. First, he needed to make the changes to his PR and update the docker images for Elastic.

He managed to do both, but it took far much time than he expected. It was almost 5 pm...

This kind of phenomenon is very common in software development. You start with the original task and find more and more things that need to be fixed and drift off further and further due to unforeseen obstacles. Sometimes even forgetting what was the original task.

We call it **yak shaving**.

I love how it's depicted by this gif:

![yak shaving malcolm in the middle](/img/yak-shaving-malcolm.gif)

## How to take care of your yaks so they don't breed too much and eat all the green grass in your code

When I was thinking about this problem some time ago I realized how hard it is to deal with it. If you are like me, you want to apply the [boy scout rule](http://deviq.com/boy-scout-rule/):

> Leave your code better than you found it.

You want to apply this rule as often as possible. Instead of committing a week of work just for code cleanup you do it as a daily practice.

That's what Erik was trying to do. But he ended up shaving a few hairy yaks in the process. How to deal with that?

### Be aware (of the yaks)

The first thing you need to do is to **recognize that you are approaching a yak**.

Remember that not everyone in the team will be a good boy scout and you will have a lot of mess in the code. Someone once said to me:

> There is no good code. There is only bad and terrible code.

There will be a lot of yaks. Always. Every time you clean the code remember you can encounter one. You probably create some yaks in the process.

Mentor your team to apply boy scout rules, if you don't want the yaks to grow their fur.

### Postpone

> Now is better than never.
> Although never is often better than *right* now.
> ~[Zen of Python](https://www.python.org/dev/peps/pep-0020/)

But what to do when you find yourself already shaving a yak? Well, stop and ask yourself two questions:

**Does it need to be shaved RIGHT NOW?**

and

**Why do I have to shave it?**

Every code refactoring needs to have a goal. Yak shaving is pretty similar and often equal to refactoring. If you define a goal it may turn out that the change you are trying to make is not needed at the moment.

Or *it can be postponed*. If so, make a task for the yak, describe the goal and the benefits of this change. Description is always important. If someone picks up this task in a few weeks/months the goal you have in mind now may no longer be valid.

There is always something to fix in the codebase. When you postpone shaving, you make room for other more important tasks.

### Shut up your ego

Sometimes I see developers that try to fix everything they see. Everything needs to shine. It hurts their ego if the code isn't as perfect as they want. Or just exactly as they would like it to be (*wink*).

Sometimes they get lost in this process. They forget you work in sprints where the goals are already defined and your main job is to deliver what you promised to deliver.

This is mostly a problem of developers without discipline, with too much focus on the technicalities instead of problems they're supposedly trying to solve for their clients. Or overly proactive junior developers that want to be seen and get promoted ASAP (been there, done that).

Sometimes people that join the team try to show off. They preach about their "previous experience" and how they would "fix" the code base. Without the knowledge about the code and the project they will tell you "how it should be done".

All this is ego talking and ego should be handled with care.

Don't be like that. Be pragmatic. Try to figure out the situation you are in. Familiarize yourself with the codebase. Have priorities and goals. Then, and only then - act. Fix what really needs to be fixed.

## Summary

Yak shaving is a complicated topic and there are no silver bullets. Eventually, you will need to deal with a big guy like the one below:

![yak-robatics](/img/yak-robatics.gif)

You can work to minimize those kinds of encounters by:

- leaving the code better than you found it AKA `the boy scout rule`
- being aware of yaks
- remembering that there is no good code, only bad and terrible code (deal with that)
- postponing (it does not have to be shaved right now)
- shutting up your ego
- being pragmatic
- having goals and priorities

**Some yaks don't need to be shaved to be happy.** Just look at them:

![happy yak](/img/happy-yaks.jpg)
*Image by [Elias Carlsson](https://unsplash.com/@eliascarlsson)*

If you know some other ways, drop a comment!
