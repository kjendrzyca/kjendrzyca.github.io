---
layout: post
title: "Material Design: Part I"
categories: []
tags: []
published: true
date: 2015-03-16
comments: true
---
Modern CSS frameworks like Bootstrap or Foundation are currently on the crest of a wave. Thanks to CSS language preprocessors like SASS or LESS it is a lot easier to build and maintain this kind of software.

I like using Bootstrap. It was a little bit hard to learn and use it at the beginning but I didn't give up. Right now my approach to creating websites is simplified. I don't need to reinvent the wheel and I can focus on delivering products to the client.

But there is something new, something different. It's called **Material Design**.
<span class="more">--</span>

## Goals
Material design guidelines were first presented by Google in the middle of 2014 and are well described on [the official website](http://www.google.com/design/spec/material-design/introduction.html).

Google developed those guidelines with two main goals in mind:

> Create a visual language that synthesizes classic principles of good design with the innovation and possibility of technology and science.

> Develop a single underlying system that allows for a unified experience across platforms and device sizes. Mobile precepts are fundamental, but touch, voice, mouse, and keyboard are all ﬁrst-class input methods.

By using "material as a metaphor" of space, surfaces and meaningful motion they want to simplify the use of everyday applications. Flavor that with **bold, colorful, eye-catching graphics and typography**, icons that are easy to click (it is often problematic on mobile devices) and you have something that is at least interesting.

[![Mobile app by Anton Aheichanka (source: http://www.materialup.com/posts/secret-project)](/img/materialapp.gif)](http://www.materialup.com/posts/secret-project)

*Mobile app by Anton Aheichanka (source: [http://www.materialup.com/](http://www.materialup.com/posts/secret-project))*

Common problem of many applications is that we don't always know where to click and what's going to happen after clicking some element. We're not sure about the flow.
Also the design varies between devices. Sometimes the same app looks totally different on PC and mobile device.

Material design is trying to solve those problems by applying consistent guidelines for every device.

I'm using Google Play Music, application presented on the image below. I must admit that when I first started this app I immediately knew how to use it, what's clickable and what's not.

[![Material design application example - Google Play Music (source: Google Play)](https://lh6.ggpht.com/4DrSejk1VERLz-k7O0-TgWOFf_5vwq4uAeqQ8tpcIzDeuxdYS5TZHAmgq7lx2l35dNox=h900-rw)](https://lh6.ggpht.com/4DrSejk1VERLz-k7O0-TgWOFf_5vwq4uAeqQ8tpcIzDeuxdYS5TZHAmgq7lx2l35dNox=h900-rw)

*Material design application example - Google Play Music (source: Google Play)*

As you can see this application has depth. Adding physical properties like depth, thickness, shape or shadow define the whole concept of material design.

##How to use it?

In my current project the client wants his app to be easy and intuitive to use. Also it should have nice look and feel. Sounds like material design, so why not to use it?

We (my team and I) started looking into available framworks. As we are using Angular.js the first guess was [Angular Material](https://material.angularjs.org). There are some nice examples of how to use provided directives. Sadly using them looks like this:

![Spaghetti](http://upload.wikimedia.org/wikipedia/commons/0/05/Classic-spaghetti-carbonara.jpg)

*Spaghetti (source: Wikipedia)*

I mean, I like spaghetti but not in the code.

The second interesting link on Google was [Material Design For Bootstrap](http://fezvrasta.github.io/bootstrap-material-design/). It looks very promising but it's not MIT for commercial apps. Let's go further.

Finally we found the thing called [Materialize](http://materializecss.com).
The first impression was like: "looks like Bootstrap, or very similar - let's give it a try."

##Materialize - first impressions

Materialize is SASS framework based on default 12 column grid system. It is used by applying CSS classes (rows, containers, cols and stuff) to your HTML code, just like in Bootstrap. Documentation is ok (if you look at the most common components), it has MIT license and it's hosted on Github. So if we are talking about simplicity - **looks perfect**.

It seems that Materialize has all of the necessary components that you would like to use when building websites and web apps based on material design.

When I started to use it I needed to port existing front-end code from Bootstrap. There is one thing I remember the most. I was able to remove a lot of CSS classes from HTML elements and it still looks ok.

So I came to conclusion that it can be easier to use Materialize than any other CSS framework. The main reason for that is the fact that *material design is concrete*. There is a finite set of rules and you should follow them to make sure your app looks good.

There is one type of app bar. There is one type of floating action button. There are dos and don'ts. There is even a guideline stating that *you should only use images that express personal relevance* (!).

This is the most consistent set of UI design rules I've ever seen so far. I'll give it a try.

(And I will re-evaluate my opinion after a few weeks.)
