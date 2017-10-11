---
title: "Visiting Euruko 2017"
---

[Euruko](https://euruko2017.org) that took place on 29th-30th September 2017 was my first Euruko. Well, actually it was my first tech conference since I switched my career to programming. And I loved it. Let me tell you why...

## The atmosphere

First of all, the atmosphere of both the meeting and wonderful city of Budapest. I've been to a number of local meetups and while they are full of people who want to share their experience, it is nowhere near what I witnessed during this conference. Since the moment I registered and started mingling with people, I felt that I was a part of something special. The community is so open and friendly and it was actually really easy to start chatting with people (something I am not usually really good at...). The countries, experiences and ideas represented during Euruko were so diversified and everyone felt welcomed. This was reflected in the topics of the talks. It started with the man who created Ruby...

## Keynote

Matz keynote was about the future of Ruby. The main topic was connected with a topic that pops out quite often in various conversations - Ruby performance and what can be done to improve it. Matz showed the current state of things and challenges that the language developing team faces. On the one hand, there is an urge to start from scratch and rewrite everything using knowledge that was gained throughout the years but also risking alienating part of the community due to incompatibilities (something that happened to Python and [its painful way to get to version 3](https://www.activestate.com/blog/2017/01/python-3-vs-python-2-its-different-time). On the other, there are technical challenges - making something faster means using more resources. The team has a clear objective though - [make Ruby 3 three times faster](http://rubykaigi.org/2017/presentations/vnmakarov.html) than 2.0 while using the same amount of memory. This was quite an interesting talk, especially since Matz is such a nice and humble person. This was a perfect introduction and taste of what was going to come next.

## The talks

I liked that they were so diverse (just like the people attending). They ranged from discussing empathy to being junior dev to describing the most embarassing failure to really technical and complex machine learning topics. These were given from a different perspectives and the speakers came from all over the world.

While there really was no weak talk, these are the three I enjoyed the most:

### Rescuing legacy codebases with GraphQL and Rails by Netto Farah

I've tried out some tutorials for [GraphQL](http://graphql.org) in the past. This presentation definitely encouraged me to try out more. The solution itself is a response to some challenges of classic REST APIs.

Netto described a task of refactoring an old monolithic app that his company was maintaining and how GraphQL helped in resolving some of the issues that they had and also what problems did they noticed when implementing it.

Ths most common issues with APIs are connected with the necessity of maintaining multiple endpoints depending on what information is actually required by the client. An alternative would be to always send more data than is required and allow clients to pick what they need while ignoring the rest. Such a waste.

In addition, we have multiple clients, changing requirements and also evolving APIs. In order to preserve compatibility with older clients or with ones that expect a specific response, we often end up with a number of versions for the API V1, V2, V3, internal, etc. It is not known when something can be updated or is no longer necessary. They also make a noise in the codebase.

Another issue is necessity of documenting the APIs and keeping everything up-to-date. Of course, there is a lot of tools that try to make our lives easier, but in the end, we often end up with incorrect information somewhere.

GraphQL is a solution that tries to solve some of the issues. It's interface with types and the way that the queries are defined allows to build a self-documenting queries thanks to the types. The client can only request information that is required and then backend with only send what was requested. Other benefits include predictable results, composable queries and ability to use GraphQL on top of existing apps. It can also be used to easily choose database environment (e.g. with multiple databases when one is for write and one replica with read-only).

Seeing this presentation made me eager to try this out in a more complex project as soon as possible. It was really helpful that Netto was so excited about this technology and even did some live coding (which is always scary). He also shared some challenges that they encountered while building GraphQL in Rails (n+1 queries, monitoring and errors logging) and how they managed to solve it.

### Predicting Performance Changes of Distributed Applications by Wojtek Rząsa

This talk was especially interesting due to its academic feel and the way that it was structured. Wojtek is a PhD on Rzeszow University of Technology in Poland and he teaches Ruby and Rails while also performing some interesting experiments on the side. He shared results of two of such cases involving Heroku and performance on the servers.

The first one was based on a controversy from some time ago when [Heroku changed intelligent routing to random routing](https://genius.com/James-somers-herokus-ugly-secret-annotated). Wojtek built a simulation to check if the performance really gets worse and understand how much worse it would get. The results were that indeed random routing is better from a perspective of vendor (scalability, they don't have to detect busy/idle dynos) while the customers get a worse performance.

The second experiment was connected with checking if getting more performant dyno will benefit a particular application (6 x standard 1x dyno vs 3 x 2x dynos). Also here with a simulation, the conclusion that Wojtek reached allowed to judge the solutions before investing a lot of money in actual servers. Additionally, the simulation helped with a problem whether Heroku was scaling dynos vertically or horizontally (faster CPUs vs more CPUs). Horizontal would make no difference, vertical would be much faster. Experiments done on Heroku dynos have shown that Heroku scales horizontally and upgrading dynos would not make a difference in this particular example.

All this was achieved thanks to modelling random and intelligent HTTP routers. All was done in Ruby and with the following benefits:

- reusability (what was built can be used in multiple scenarios)
- flexibility
- different level of results
- what if scenarios (what if there were more intelligent routers)

### How to Make It As A Junior Dev and Stay Sane by Katelyn Hertel

The last talk that I want to write about was not really about tech, but more around soft-skills and how to manage in a difficult programming environment. This was especially interesting for me, as I found myself in such situations where I felt overwhelmed by tasks at hand and felt lost and wanted to quit.

Katelyn described some of the most important aspects that allow to "stay sane" while being junior dev, but actually I think that this advice was something that everyone can follow. There was also a part devoted to more experienced developers and leaders who sometimes do not have time or do not know about the issues that a new person in the company may have.

- ask for advice - it is important to ask questions when we do not know something rather than being stuck for hours. This may be scary, but more often than not, others are there to help. Katelyn also shown how superhero poses done in bathroom can help overcome fear (and it actually work on her on the scene as she became much more confident after standing like Superman)
- manage time better - keeping a schedule, booking time slots or even having a todo list where we can cross things of the list at the end of the day can be really helpful (keep a schedule or at least a todo list)
- speak up - say when something is not right. The issues may be connected simply with the fact that others simply don't know that something is wrong
- learn to say no - this is really hard for me, but also something that can help stay sane if I manage to finally learn it. The advice is to be more assertive. Don't be afraid to say 'no' if something is not possible or will make you overburdened.
- set goals - short term like what you do in your everyday life. They should bring you closer to long term goals. And those long term goals are about life, family and the big picture)
- care about yourself - buy yourself something nice, have a night out, watch a movie, turn off communicators when on holidays or during weekends. Try to recharge your batteries.

There were also some lessons for management or senior staff - listen to people and offer your knowledge, help with task prioritization, praise for saying no, be the success story to look up to, guide setting others goals and make sure they are not working too hard.

These were all important lessons for I think most of the people in the programming business (and not only!). Following at least some of those can make life a lot easier. I hope to incorporate them step by step to manage my tasks and time better.

## Next year

You can probably tell that I enjoyed Euruko a lot. This is only scratching a surface, but these truly were two great days. I also found out that the event is truly community lead. It turned out that everyone can try and organize Euruko by doing a short presentation about their town or city and the remaining participants vote on the one that they liked the most. This is really crazy and awesome.

The next year Euruko is going to Vienna. I hope to be there as well. It will also be the year when Ruby turns 25.
