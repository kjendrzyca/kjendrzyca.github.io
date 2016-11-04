---
layout: post
title: How to learn JavaScript and leave fatigue behind
categories: []
tags: []
published: true
date: 2016-11-04
comments: true
---

Learning JavaScript is a pretty good choice these days. It can do a lot of things for you:

- [run a web server](https://nodejs.org/)
- [test a webpage](http://phantomjs.org/)
- [program your Arduino](https://github.com/ecto/duino)
- [render 3D graphics](https://threejs.org/)
- [write an app](https://facebook.github.io/react-native/) for [your phone](http://cordova.apache.org/)
- [build a desktop app](http://electron.atom.io/)
- [control a robot](https://github.com/rwaldron/johnny-five)
- [play with IoT](http://iotjs.net/)

Some friends asked me how to get started with JS. Well, I learned JS not so long ago and I talked with some dev-people about their experience of learning JS. Based on that I will describe what in my opinion seems to be a good approach.

<span class="more">--</span>

## Basics

I will assume that you are not a complete newbie to programming and you know what a *for loop* is. This post will cover the most common use case for learning JS - writing web apps. When you learn the language you can try other things from the list above.

The good news - there is a lot of free content on how to learn JS and you can make use of that.

For starters, you need to learn the basics. It doesn't really matter how. What matters is that you need a solid foundation. And you don't start with jQuery or React.

Some people recommend books:

* [Head First HTML5 Programming](http://shop.oreilly.com/product/0636920010906.do) - focused on JS for web development
* [Eloquent JavaScript](http://eloquentjavascript.net/) - free online book
* [JavaScript: The Definitive Guide](http://shop.oreilly.com/product/9780596805531.do)
* [You Don't Know JS](https://github.com/getify/You-Dont-Know-JS) - this one is a popular recommendation lately

Some people don't like books and recommend online courses instead:

* [Code School](https://www.codeschool.com/learn/javascript) - probably the best one. Why? It's well structured so you are learning it step by step, in a logical order, finishing tasks in web editor. I took the course myself, so that's why I'm recommending it.
* [Code Academy](https://www.codecademy.com/learn/javascript)
* [Udacity](https://www.udacity.com/course/javascript-basics--ud804)
* [Frontend Masters](https://frontendmasters.com) - there is a course or two for beginners. An advantage - it features some recent JS superstars.

Taking an online course is an option if you are willing to pay. What's nice about online courses is that they are interactive and they can get you to the point where you can say "I know some handy JS tricks now, let's see what I can do with those".

Some people don't like neither online courses nor books. They recommend watching [The Ultimate JS Superstar - Douglas Crockford](https://www.youtube.com/playlist?list=PL7664379246A246CB).

In my opinion it's worth watching to complement your knowledge, but not a good thing for beginners.

Finally, some people (me included) recommend reading [MDN JavaScript Guide](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide). You can find there everything you need to know and it's free. It's well structured and nicely divided into chapters - from the basics to more advanced topics. I would use it if I had to learn JS from scratch once again.

## The Good Parts

At this point, you should feel that you know what JS is about and feel confident about using it. You should also have the feeling that JS is somehow broken but you can't say what's wrong exactly.

JS can be strange sometimes. Its dynamic nature can lead to the funniest bugs you'll ever encounter.

<blockquote class="twitter-tweet" data-lang="en"><p lang="en" dir="ltr">js love &lt;3 <a href="http://t.co/TAFBVq4cEQ">pic.twitter.com/TAFBVq4cEQ</a></p>&mdash; Krzysztof Jendrzyca (@kjendrzyca) <a href="https://twitter.com/kjendrzyca/status/568531691658018816">February 19, 2015</a></blockquote>
<script async src="//platform.twitter.com/widgets.js" charset="utf-8"></script>

JS has some awful parts that are best avoided. This book describes most of them and provides the distilled version of the language:

![JavaScript: The Good Parts](/img/thegoodparts.jpg)
*source: [O'Reilly](http://shop.oreilly.com/product/9780596517748)*

If you want to be a serious JS developer you should read this book. The benefits of doing that:

- you can call yourself a serious JS developer because every serious developer has read The Good Parts
- you will become aware of the bad parts
- you will know how to avoid them

The same guy who wrote this book is an author of the first widely-used linter (aka static code analysis tool) for JS - [JSLint](http://www.jslint.com/).
Later it was replaced by [JSHint](http://jshint.com/) and now we are using [ESLint](http://eslint.org/), but more about that later.

Some of the bad parts were fixed by the new version of JS (the previous one is called ES5, the new one ES2015) and we'll come to that in a minute, too.

## The Ongoing Task Of Mastering JS

This is where things become serious. I think learning JS is a never-ending story. You know the good parts and the bad ones, but there is a lot ahead of you. Below are the things you need to learn simultaneously to fully grasp the topic.

### Design Patterns

Design patterns are useful for programmers. They help with communication and with solving common programming problems. But design patterns are a concept. The implementation may differ depending on what language you are using.

The cool thing about JS is that you can do one thing in a thousand different ways. The same goes for applying design patterns.
To stay sane I would recommend picking one way of doing things and stick to it until you or someone else discovers how to do it better (hardcore JS people reading this are laughing because they already know [how fast the ecosystem is changing](https://hackernoon.com/how-it-feels-to-learn-javascript-in-2016-d3a717dd577f#.3b8yfzxie)).

My pick was [JavaScript Patterns by Stoyan Stefanov](http://shop.oreilly.com/product/9780596806767.do.). At some point (when I only knew jQuery) this book helped me to get a job. I can still read the code I've written then without ripping my eyes out.

### The Pillars

Eric Elliot wrote two great posts about the pillars of JS:

- [Prototypal OO](https://medium.com/javascript-scene/the-two-pillars-of-javascript-ee6f3281e7f3)
- [Functional Programming](https://medium.com/javascript-scene/the-two-pillars-of-javascript-pt-2-functional-programming-a63aa53a41a4)

Deep knowledge about those two will help you write better JS code. Without this knowledge, you are like a child wandering in the fog.

### Libraries and Frameworks

You don't want to do things from scratch. Your employer doesn't want you to. To provide value ASAP you need tools.

If you want to write a web server in JavaScript you need [Node.js](https://nodejs.org/).
Node is an open-source, multiplatform runtime environment for writing the backend apps. Most common use cases are web servers, but it can do a lot more like [robotics](http://nodebots.io/), [games](https://developer.mozilla.org/en-US/docs/Games/Tools/Engines_and_tools) or even [desktop apps](http://electron.atom.io/).

The most popular web framework for Node is [Express](http://expressjs.com/) and it's often used with [MongoDB database](https://www.mongodb.com/).

Node comes with a package manager called [NPM](https://www.npmjs.com/). NPM registry seems to be the largest ecosystem of open source libraries - just as they say on their website. What they don't say is that a lot of those libraries are just crap and you should avoid installing too much of them. However, there is a lot of great ones that will solve most problems that can come to your mind. Just don't rely on this power too much. If you can write something in 8 lines, do it and put it in the `utils` directory instead of downloading a library. You don't want [a left-pad incident](http://www.theregister.co.uk/2016/03/23/npm_left_pad_chaos/) in your life.

If you want to write a frontend app there is also a lot of options:
[jQuery](https://jquery.com/) is a good thing to know. Especially if you are coding *websites*. It's used for animations, galleries, form's validation, making AJAX request and a ton more. Some people say it can solve every problem there is.

[![Use jQuery](/img/usejquery.gif)](/img/usejquery.gif)

jQuery is not enough for *web applications*. For that the most popular pick right now is [React](https://facebook.github.io/react/) and its ecosystem. It was designed by Facebook to deal with complex web applications but it's cool for the small ones too. I'm using it because of its simplicity. It focuses on doing one thing well and it can be adjusted to your needs. [Redux](http://redux.js.org/) plays well with it.

There is also Ember, Backbone, Angular 1 and 2, Vue (this is my second favorite), Elm, Aurelia, Cycle, Polymer, Meteor, Mithril and the list goes [on and on](https://medium.com/@sachagreif/the-state-of-javascript-front-end-frameworks-1a2d8a61510#.xeuslxrse).

I've been using Angular 1 for some time but it kicked my butt so many times that I decided it's not worth my efforts.

For modern frontend you'll also need:

- a way to download the libraries, the one you should go for is NPM, (or super-fresh [Yarn](https://github.com/yarnpkg/yarn)) there is also [Bower](https://bower.io/), but it's slowly dying
- a way to package the app: [Webpack](https://webpack.github.io/) (more swag), [Browserify](http://browserify.org/) (less swag), [Rollup](http://rollupjs.org/) (total swag, but not yet as popular as the previous two) or [SystemJS](https://github.com/systemjs/systemjs) which also has its own package manager - [jspm](http://jsmp.io)
- a way to test your app: the most popular test runners are [Mocha](https://mochajs.org/), [Jasmine](http://jasmine.github.io/), and [tape](https://github.com/substack/tape), all of them are cool and you really need to [judge yourself](https://medium.com/javascript-scene/why-i-use-tape-instead-of-mocha-so-should-you-6aa105d8eaf4#.ylp0u59lr) which one to use
- linter (aka static analysis tool): this one can help with a lot of problems caused by JS "bad parts", right now most people are using [ESLint](http://eslint.org/) which is the most powerful one.

### Modern JS - ES201x

Most of the really bad parts were fixed in the new version of JS - ES2015, which is still often called ES6 - if you want to know why and what's the full story [click here](https://benmccormick.org/2015/09/14/es5-es6-es2016-es-next-whats-going-on-with-javascript-versioning/). Introduced fixes should be your main reason to use it. You will be able to write more readable and robust code.

ES2015 is pretty mainstream right now. Most of the examples for modern libraries are written in ES2015. It's backward compatible so all the ES5 examples from the books mentioned above work with the new version.

Browser support is getting better and better (Chrome 54 supports 97% of new functionalities) but if you want to be sure it will work on older browsers you should use [babel](https://babeljs.io/). It [transpiles](https://en.wikipedia.org/wiki/Source-to-source_compiler) the code from ES2015 to ES5 that is supported by all browsers.

Here is the compatibility table for browsers: [http://kangax.github.io/compat-table/es6/](http://kangax.github.io/compat-table/es6/)

The current version of Node (7.0.0) supports 99% of ES2015 features - no need for transpiling at this point.

Here is the compatibility table for Node:
[http://node.green/](http://node.green/)

You should also keep an eye for the next ES201x releases.

## JavaScript Fatigue

In the recent paragraphs, I was talking a lot about new trends, great libraries being replaced by other great libraries. Everyone agrees - JavaScript is evolving quickly. Some people don't like that, they get confused, they don't know where to start. I understand them, as I said before - we just want to provide value. Fragmentation and rapid evolution prevent us from doing that.

In my opinion, the solution is to have a solid understanding of the basics and foundations. With that knowledge the fatigue disappears and it's just another framework/library/convention to learn. A part of our job.

Of course, you can pick just one solution that suits your needs and use it everywhere. That's also a way. Just remember not to become religious about the tools you've chosen.

## Final hints

- avoid w3schools.com, if you want correctness use [MDN](https://developer.mozilla.org/)
- visit [http://www.2ality.com/](http://www.2ality.com/) if you are looking for "in-depth" blog posts about JS
- know your tools, it will spare you the frustration (for starters I recommend [understanding Chrome DevTools](https://developers.google.com/web/tools/chrome-devtools/))

Happy learning!
