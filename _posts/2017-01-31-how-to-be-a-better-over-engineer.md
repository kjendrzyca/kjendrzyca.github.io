---
layout: post
title: How to become a better over-engineer
categories: []
tags: [over-engineering, experience, learning]
published: true
date: 2017-01-31
comments: true
---

![React](/img/over-engineering.jpg)
*Image by [Ant Rozetsky](https://unsplash.com/@rozetsky)*

During your career, you will be often asked to code something that may look like a simple functionality. A simple HTML form or some piece of code that is sending emails. You will feel this urge to hack and ship it ASAP. They just wanted to keep it simple, right?

But deep inside you feel it's wrong. Don't you? Sometimes you have to do better and over-engineer a little.

<span class="more">--</span>

The thing is you know that clients never know what they want. It's your responsibility to help them realize that. It's the reason they pay you. To solve problems, to foresee obstacles and help them make the best product.

It is a hard task. You need to have a framework you can follow in situations like that.

## Sending emails

Let's say you get to implement a module that is sending emails. The requirement says that the system should send a concrete email after successful registration on your page.

The simplest way would be to have a file with the text, load it when needed and use a built-in library to handle email sending.

This is the worst thing to do.

Remember that clients don't know what they want. Writing such simple functionality is just stupid. What if they want to extend it in the future? What if they want to send other emails? What about performance?

Simple text file won't do. You need to have proper abstraction.

Start with generic configuration loader that can handle SMTP configuration in various formats (JSON, YAML and so on). Serve it as a tree of objects. It would be great if every configuration node could be represented as a different class. You will need to parse the values from the configuration. Create a separate class for the string field, int field etc. Don't forget to include a config for your templating engine. You always need to keep things clean.

Speaking of which, don't use any simple open source libraries like Handlebars as templating engine! It's probably not efficient enough to handle all the edge cases that are to come. Performance is key. You don't want your client to rely on someone else's OSS side-project. It can be buggy. It's always better to write and test your own thing (strive for 100% code coverage).

Your solution must be rock-SOLID, DRY and most importantly - generic. You never know what functionalities the client will request in the future.

Remember that everything needs to be extendable and customizable. It will be easier to change it. EmailProcessor, TemplateLoader, TemplateProcessor, ConfigurationLoader, ConfigurationParser, EmailSendingManager - if you don't have them it's **bad code**.

## Forms

Let's switch domains. Imagine you have to implement a simple form on a website. "Simple form", that's a funny term. Trust your experience. You know that every "simple form" could become a platform one day. What to do?

First of all, forget about vanilla JS. You should at least use React. Back it up it Redux if you feel that the application will become much bigger. Trust your guts.

Of course, the best solution would be to use Angular. It's a framework, not just a library. It's easy to plug in more functionalities as you go. And of course, it has a proper dependency injection system built-in. You can build abstractions the same way as explained in the email example. Services, factories, and providers - that sounds like robust and cohesive code. Your client will thank you one day.

## Dealing with haters

I hope you start seeing a pattern here. Clean, generic code is the key. It's ready for change, ready for what future may bring. There is really small chance that client will request a functionality that cannot be added to your solution.

Unfortunately, every coin has two sides and **some people will try to judge you.**

Mostly, those would be your less experienced team members. They will try to argue that you don't need such generic, sophisticated solution. That you should avoid complexity. Oh boy, how wrong are they.

You should stay calm in those situations. Don't judge, don't be like them. They need to be a shining example. Give them a little guidance. There are few simple tricks you can use:

1) Use your "years of experience" in the argument.

This one is very hard to argue with. Use it if you have at least 5 years of experience. The more years of experience you have the stronger you are.

People will try to change your mind, but they often didn't see the things you saw. Besides, you are not doing anything wrong. Just trusting your guts based on your previous projects (see point 2).

2) Evangelize

Tell them about your previous projects. Tell them how stupid the clients were. Tell the stories about how they failed because they didn't trust you.

Tell everyone about your own inventions. It would be the best if you wrote a framework. If it's something you can call a "framework for everything" you are basically invincible.

Tell them why you think agile doesn't work. Why you should focus on perfecting the code instead of having meetings (people will love you for this one).

Do all this to build a trust in you.

3) If you are a senior or lead developer, remind them of that.

Sometimes people forget their place. You should use your authority. I know you don't want to be a prick but sometimes you need to suffer to make your team better.

Maybe they will finally learn something and thank you one day.

4) Use clever talk if you don't have the experience.

"Fake it till you make it" they say. And that's what you should do.

You cannot show that you don't have the experience. You should work on your vocabulary to have a lot of sophisticated words you can use in the argument. They will not argue if they don't understand you.

Be everywhere and take part in every discussion. Always have something to say. It's a weapon that works against weaker minds.

5) Do it anyway

You will sometimes get a lot of comments on code review that you don't agree with. The best strategy is to say "thank you, I will consider that" and ignore them. Then merge the feature. There is a 50-100% chance no one will find out. If they do then there is 50-100% chance there will be too late and no one will have time to reimplement the feature.

This may look sneaky but remember - you are doing this for the good of your client. One day the team will understand their mistakes.

## Summary

This is it. That's how I see it and I hope it will help you become a better over-engineer. There is a lot of obstacles along the way, but you can't give up. It's good for the clients. One day everyone will realize how valuable you are. You should be ready for that moment.

---

Now, let's get serious. This post was born to vent my frustrations from my experience with the behaviors I often see. If I were to describe them in one sentence I would say "lack of pragmatism, thinking, and common sense".

Don't over-engineer everything based on bad experiences from the past. Don't be self-opinionated. Engage in the discussion and make decisions based on facts.

**Remember that experience is tricky.**

You can have 10 years of experience, sure. But if you did the same thing for those 10 years then you really have just 1 year of experience.

Be open to learning even if you claim to have 10 years of experience.

> What software developers do best is learn. ~ @codinghorror

What your experience should teach you is to remember to test your ideas before applying them.

You will often be right about certain things but there will be no way to convince your team or your client. No one will listen.

Don't try to be clever, though. Don't be a prick. Express your concerns and let people make their own mistakes. [Sometimes it's the best way to learn](http://aimforsimplicity.com/post/thesuperpowerofmakingmistakes/).
