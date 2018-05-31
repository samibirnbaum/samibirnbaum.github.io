---
layout: post
title: Rails! API!! Devise!!! JWT's!!!!
---

**I had dreamed this day would finally come...** Ok that's a bit melodramatic, but to say I hadn't lay awake thinking about this concept would be wholly untrue...

<!--more-->

My journey into web-development started with all the good stuff on the frontend, as it does for most people. I even went the whole hog and threw in a framework (AngularJS) just for good measure. But now I was in Star Wars territory, this was the life of a server-side developer, time to separate the men from the boys (at least in my child-like mind).

Welcome Ruby on Rails. This was great, I could build a whole application back-to-front using this single framework Ruby on Rails. But hold on one second... If I could build everything with Rails, then what was the point of all the really cool frontend frameworks that everyone was raving about (currently React).

Well unfortunately it turns out that if you wanted to build an application using Ruby on Rails, you would miss out on all the cool functionality of the frontend frameworks like single page applications and 2-way data binding.

This left me in quite a predicament. I could have a really bespoke backend with Ruby on Rails but sub-standard frontend views. Or I could have a really bespoke frontend with Angular but a sub-standard database-as-a-service backend.

Well I wanted both (I screamed, lying down kicking my legs against the floor).

I wanted to have my cake _and_ eat it!

Why couldn't I have a bespoke backend using Rails and a bespoke frontend using whichever framework I so desired?

This pursuit led me to the crazy world of **Rails! API!! Devise!!! JWT's!!!!**

I would build my backend using Rails new API mode. This would allow my backend to be completely agnostic and interact with whichever frontend I wanted. I needed to set up a good authentication system, especially as I was using an API, but I was able to do this using Devise and JWT's.

Once I had the backend working as its own unit, as an API, I would be free to connect to that backend using HTTP requests from whichever frontend I desired, Angular, React, or even Android and IOS Applications.

Admittedly, this would be far more work but think of the benefits in the long-run. I would have one backend for all different forms of my application. I could have a native mobile application and a website all running off one single backend. Moreover, as the pace of change on the frontend gets ever more Usain-Bolt-like I would be able to adapt my frontend to the latest designs without being concerning about the star wars server side stuff.

Time to sit back, have my cake **and** eat it!

In my personal opinion, this division of labour between the backend and the frontend is how applications (especially sizeable ones) should be built. But hey! What do I know?! I'm just a developer with a child-like mind.

[A project I built using this methodology](https://samibirnbaum.com/portfolio/memorial-notifier-api.html){:target="_blank"}. 

