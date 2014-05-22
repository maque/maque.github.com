---
layout: post
title: "YMNI vs YAGNI"
date: 2014-03-10 18:08:59 +0100
comments: false
categories: PrinciplesRevisited
---
YAGNI (**You aren't gonna need it**) principle sound nice when you hear it. After all why to bother your self wasting time for something that you probably won't use.
Well, it sounds good only for features or bunch of "maybe need" methods like getters & setter.

But sometimes you can start excusing your laziness with yagni. For example when you know you need only two categories with items. That's the plan, so it's easy to you just duplicate lists and rename them. It's easier than playing with embedded list, geting header for each of them, specially when you are using some external tools like Kendo UI. And definitely easier when you are working with legacy code.

And then suddenly, client call and he want 20 list for tomorrow. You already did two, can't you just copy and paste 18? I'm sure it's like 5min. for you, isn't it?

So You May Need It

If you have already followed YAGNI principle to far it will become hell for you. You didn't write any administration panel, there is no table in database for product type, ale the tables assumes that there are only two product types. It wouldn't be a problem if you were developing in nice & clean scrum/agile/bdd work place with time to analyze every new feature.
But our life isn't so easy. Our PM's not necessary had everything set up with client, sometimes there is no written agreement at all about changes, fixes & features and client IS ALWAYS EXPECTING TO MAKE IT ASAP!
Even if you PM understand you had followed YAGNI principle doesn't mean you can wait with release to next month. Probably they want this change today at 5pm, maybe tomorrow morning.

If you would follow YAGNI really strict you will end up with not layered code, no abstraction and not prepared to any changes. It's not only if you follow this principle standalone, but also if you have continuous refactoring it's still not as good as it sounds.

Reason is simple: Client is always lying.
He lies about changes. He will tell you he need only change logo, but then he reminds himself that also other "few minor" changes are needed.
He lies about deadline.Very often deadline is fluid, you are waiting for aproval from pm's and directors, each of them want to change "only small thing". You never have "finished" software at the day of realese - you have only software that director agreed to show to the people.

Also, let be honest, assuming you are working in company - do you really have time to write bunch of code lines without need for using it? Maybe at the very beginning of project with no legacy code what so ever.

If you found yourself adding manually records to database, because in the last moment client change mind, you know you followed YAGNI to far.

Here are my few tips for working with YAGNI but keeping in mind YMNI

**1. Assume you will need release your code 5 times in one day. Each with different set of features. Each for different server.**

With this assumption you will prepare really good plan for releases. You will prepare proper source control workflow (git workflow, branch by feature). With this assumption you can't just overwrite/copy&paste files in folder. There is no time for that and there is no space for mistake.You need to have build check & unit test before each release.
Also although your code is clean&perfect doesn't mean you release process is. You spend so much time with IoC, TDD and SOLID that now changing manually connection string after releasing to new server seems good enough. Well, it isn't.

**2. Assume you will need add this one setting, role, product, type 100 times more in the future.**

You saw this so many times, why now you are believe this will be different?

**3. Assume there will be a lot of exceptions and don't make any.**

You can start project with set of features, nice and clean, logically composed. But then suddenly client will tell you something like this: "Well, we want to show this product the same as it was, but with special sparkling animation, just for this one". Do not believe that! Don't try to put special flag, "if", exception, or any other 'hack' just for one item. Remember about doing this 100 times? This is so obvious and yet I saw that so many times.