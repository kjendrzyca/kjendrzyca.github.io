---
layout: post
title: Object calisthenics - Game Of Life Kata
categories: []
tags: []
published: true
date: 2015-02-03
comments: true

---
Object calisthenics is a group of rules for software development exercises (like code katas) that - when followed - should boost code readability and overall maintainability.

There are 9 of these rules:

1. Only One Level Of Indentation Per Method
2. Don't Use The ELSE Keyword
3. Wrap All Primitives And Strings
4. First Class Collections
5. One Dot Per Line
6. Don't Abbreviate
7. Keep All Entities Small
8. No Classes With More Than Two Instance Variables
9. No Getters/Setters/Properties

Today I was a participant in [Game Of Life code kata](http://en.wikipedia.org/wiki/Conway's_Game_of_Life) and the main rule was - we use object calisthenics.
We worked in 3 groups of 4 people. After implementing the whole thing we switched in groups and reviewed each other code providing comments about mistakes and failures in following calisthenics rules.
<!--more-->

##The Rules

Some of these rules are pretty straightforward, some of them are extreme. But every one is worth to look at it.

### 1. Only One Level Of Indentation Per Method
This one is easy. It's basically about avoiding [Arrow anti-pattern](http://c2.com/cgi/wiki?ArrowAntiPattern) which looks like this:

{% highlight csharp %}
if
    if
        if
            if
                do something
            endif
        endif
    endif
endif
{% endhighlight %}

This smells really bad and I'm sure that you know what I mean. The key is to clean this sort of mess and extract responsibilities to other methods with meaningful names.

### 2. Don't Use The ELSE Keyword
For me it's complementary to the first rule. By using ```else``` block you are adding complexity to your code. It sounds silly but just think about that. I'm sure that after 2 weeks "if-elsed" code is really hard to read. What makes it like that is another virtual path of execution that you need to visualize in your mind. Solution for that is simple - don't use the ```else``` keyword and return from the method as soon as something is not ok:

{% highlight csharp %}
if(isSthThatYouWantToDoImpossible) {
    return new ErrorStuff();
}

var theRightStuff = GetTheRightStuff();

return theRighStuff;
{% endhighlight %}

### 3. Wrap All Primitives And Strings
This one is hard. I suppose that the main idea is to use [Value Objects](http://martinfowler.com/bliki/ValueObject.html) to wrap variables like ```int money``` in class ```Money``` etc. This rule adds complexity to your code but can improve readability. Also if you mix it with rule no. 5 it can noticeably improve code quality by delegating responsibilities to the correct classes.

### 4. First Class Collections
Similar to the previous one. Wrapping collections in their own classes and providing methods like ```AddSth(Something something)``` allows you to manage collections by their own specialized methods, not just simple interfaces like generic ```Add()``` or ```Remove()```.

### 5. One Dot Per Line
I love this one. It's not really about the dots (because using [Fluent Api](http://martinfowler.com/bliki/FluentInterface.html) is ok). Simply put it's [Law Of Demeter](http://c2.com/cgi/wiki?LawOfDemeter) - "talk to your friends, not strangers".

A method in class can call other methods of:

- its class
- method parameters
- any object created in method scope
- any global class object

What are the benefits? You are creating the layers of abstraction. You will not end up with methods chain like this:

{% highlight csharp %}
looksLikeSimpleObject.GimmeDbLayer()
    .GimmeCurrentDbContext()
    .GimmeCurrentConnection()
    .DoMagic(someControlFromTheUI);
{% endhighlight %}

**Not using Law Of Demeter is just a code smell**.

### 6. Don't Abbreviate
It's a shorthand for **use better names unless you want to burn in hell**. No one likes variables like ```int a```, ```string mnkName``` ("mnk" states for "monkey", obviously). Naming is one of the most important things in software development and here is a random comment from Uncle Bob to prove that:

> "The ratio of time spent reading (code) versus writing is well over 10 to 1 ... (therefore) making it easy to read makes it easier to write."
> <br />-- <cite>Robert C. Martin, Clean Code: A Handbook of Agile Software Craftsmanship</cite>

Ok I have one more:

> "So if you want to go fast, if you want to get done quickly, if you want your code to be easy to write, make it easy to read."
> <br /> -- <cite>Robert C. Martin, Clean Code: A Handbook of Agile Software Craftsmanship</cite>

There is more, just google it.

### 7. Keep All Entities Small
Why? Because if something is small then it is easy to read. According to object calisthenics rules, methods should be short, like about 5 - 10 lines of code. Classes should be no longer than 50 lines. But I think this can be extended to 100-150 lines.

For me the rule of thumb is to extract responsibilities (if there are any) to other classes. By following this rule all classes will remain short.

### 8. No Classes With More Than Two Instance Variables
Say whaaat?! Yeah really. Legends say that if a class manages more than 2 instance variables it loses cohesion. I agree that sometimes it is hard to follow the flow of this kind of classes. Keeping only 2 instance variables in class may be the key to overcome the mess we sometimes create.

### 9. No Getters/Setters/Properties
I think this one may be the most powerful one. Getters and setters are popular because it is easy to use them. But I always have the feeling that it breaks encapsulation somehow. It is a smaller evil if you keep the management of class with public properties in one place. Still - a class that have only getters and setters is kind of weak and defenseless.

According to the rule no. 9 you should **"Tell, don't ask"**. The class that you are using should do things for you instead of ejecting its own guts straight in your face.

##My thoughts
As mentioned earlier we tried to implement the Game Of Life algorithm using the above-mentioned rules.
So we started with string like this one:

{% highlight text %}
var golString = "******
                 **#***
                 ******";
{% endhighlight %}

And tried to parse it to use later as the generation that needs to be evolved.
And hell, it was hard. Using algorithms and mixing them with object calisthenics rules is really hard. Sometimes you just want to use simple string and it should do only what the string does, nothing else. You don't want to wrap it to improve readability or separate the concerns. You just want it to hold the text.

We spent so much time playing with this string that we almost didn't noticed that the time is over. The group that was checking our solution didn't have much to look at.

I learned some things though.

The first would be that some of the most experienced developers have problems with following these rules. Why? Because they are so good that they know that the problem can be solved with 6 lines of code. And they don't need calisthenics rules to be efficient and write readable code.

The second would be that implementing business logic using these rules can improve code quality quite nicely. "One level of indentation" makes your code simple. Wrapping primitives gives you the opportunity to give those classes their own behavior. They are not stupid POCO classes anymore. Thanks to "One dot" rule aka "Law Of Demeter" all responsibilities are better delegated, concerns separated and unicorns start flying around.

Using "Two instance variables" rule is controversial and I will use it with care (like every other rule I suppose).

As a .Net developer I like to use "only getters/setters" classes sometimes. In infrastructural code mostly. But I see the value of dumping this pattern in business logic.

Those rules are connected with every other "good software practices" like DRY, SOLID etc. Even with some approaches to software development like DDD. So probably there is some golden rule for designing beautiful object models.

After all the other teams came up with pretty good solutions. They focused on **solving the real problem** with these rules and they succeeded.

For me using object calisthenics was a refreshing experience and I will definitely try to implement the Game of Life following OC rules once again. I will use it to exercise with other programming problems.

Maybe I will come up with new conclusions that will simplify my code even more.
