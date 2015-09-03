---
layout: post
title: ESLint - keep your JavaScript on a leash
categories: []
tags: []
published: false
date: 2015-09-01
comments: false
---

I am a fan of JavaScript. I love how unopinionated it is. Funny thing is that 2 years ago this was the reason why I've been hating it. But I wrote some code since then, I got bored of strongly typed C# (writing custom class for every small DTO, how annoying!), fell in love with the simplicity of Node.js and now I see world in different colors.

It's common knowledge that writing JS can be tricky. Without types, interfaces and proper code hints making mistakes is inevitable. Also JS has its specific pitfalls like global variable scope, messed up `this` scope, variables shadowing and and so on. There are some ways to solve those issues:

- reading JS books, like JS The Good Parts
- learning ES6, a new version of JS that fixes some of the problems
- not writing JS ;)
- taking help from the JS community

I would like to focus on the last one.

# Linters
JS community provided us with linters. Linters are static code analysis tools that help us to find code problems that could cause unexpected behavior. The first linters I've been using were JSHint and JSLint. Thanks to IDE integrations those tools guarded my JS code by highlighting potential code problems and I was always up to date.

Then ESLint made it's entrance.

# ESLint
How ESLint is different? Well, it supports ES6 (a must in 2015) and it's **pluggable**, and that means everyone can write his own plug-in to handle their own linting rules. That's very powerful and that's the reason I broke up with JSHint.

The very first plug-in I've installed was [eslint-plugin-react](https://github.com/yannickcr/eslint-plugin-react) to lint my JSX files and see how it is working. I must say that the result is just great.

# Installation



But the community of JS is cool and provides us with tools that helps to deal with JS problems. The most popular are linters. In this post I will present [ESLint - "The pluggable linting utility for JavaScript"](http://eslint.org/).