---
layout: post
title: Tips for joining an existing project 💡
---

I don't like change!...

<!--more-->

Joining an existing project is daunting at the best of times. 
There are a lot of things to try and wrap your head around and it takes a lot of mental and emotional energy.
Most human beings by nature do not like change (I'm one of them 🙂), it is uncertain and requires expending more effort than staying put does.

However, change is inevitable and positive. A new project brings new experiences and sometimes a change of scenery can bring some freshness 
to your daily routine.

So here are some tips that I have picked up along the way to try and help ease the transition onto an existing project.

---

### Lower your expectations and go exploring 🔎

This might sound counterintuitive but coming into a project at 100mph with expectations to have an immediate impact are probably not realistic 
and will likely lead to you feeling frustrated. 

I understand the desire to do this and it comes from a good place of caring about what you do and wanting to help.

You may also feel like "I am being paid to be here so I need to be doing things". 

However, these expectations and pressures are often self-imposed.
Ask yourself, where are these expectations and pressures coming from?

Often the answer is from your own desire to get things done or have an impact.

Instead, give yourself a buffer when joining a new project.
You could call it the exploration phase, the discovery phase or the onboarding phase.

It doesn't matter what you call it, what matters is that mentally you give yourself time to get up to speed
without pressures or expectations to deliver.

Depending on the size and complexity of the project this could be weeks or even a couple months or even longer.

⭐ Pro Tip: communicate this with the rest of the team, let them know you will be in an exploratory phase where you 
get up to speed with all the things there are to learn about the new project. 

Remember everyone who joins the project will have to do this anyway, it just helps to set some healthier expectations for
yourself and the team around you.

---

### Be sensitive 💙

When you join a new project it can be fairly common to immediately see something that the new team has done or are doing that you feel doesn't seem right
or could benefit from some significant improvement.

The likelihood is that you are correct. Your observations with a new perspective may have spotted something which the rest of the team have been doing
habitually without thinking about it and you can see a clear and obvious approach to improve this for everyone.

But before you jump in and start suggesting changes, just take a moment to be sensitive. 

Every project and process has its idiosyncrasies and some have a context
behind them that explains how they ended up this way. 

Moreover, some people may have spent a lot of time honing these processes or code structures, so be sensitive
to the possibility that critiquing _something_ might also be viewed as critiquing _someone_.

⭐ Pro Tip: Consider holding off suggestions until the discovery phase has passed. This
gives you the time to gain some more context on how certain things developed but it also means that when you come to make a suggestion you will be respected 
by the rest of the team for having taken the time to understand things first.

---

### Onboarding Checklist ✅

This is it! Your first day on the project and you arrive at the daily sync (on time, because it is your first day). 

There is tendency to feel a bit out
of things when everyone is going through their cards or tasks for the day and everyone seems to have a clear idea of what they are doing.

You also want to feel part of it and want to have something concrete to say in the sync.

A quick way to be able to do this is to create a task for onboarding and add an onboarding checklist to it. The team you are joining may already have
an onboarding checklist for onboarding new people anyway, but why not create a card for it and add some of your own things that you like to do for onboarding
as well (dare I say, you may even add some things from this list 😉).

⭐ Pro Tip: Having an onboarding checklist that is visible will give you something to communicate about in sync but also give good visibility to the rest
of the team about what you are doing.

---

### Business Overview 💰

Sometimes we forget that behind the codebase there is often a business. 

In fact sometimes the hardest thing about joining a new project is getting up to speed with all the domain
knowledge.

Consider asking someone from the business side of things (preferably not another developer) if you can schedule a call just to have a chat about how the business works.

This will not only give you invaluable information about what you are working with but you will also discover what are the best channels for communication to
get hold of stakeholders.

---

### Technical Architecture Overview 🎛

So far we still have not looked at anything technological, but let's do that, without heading into the codebase just yet.

Ask one of the developers or someone from the DevOps team (if there is one) for a chat to go through the technical architecture.

Often you will find that understanding the technical architecture can help to answer a lot of questions that you would encounter in the codebase anyway.

For example:

- How many databases are there?
- What type of database are we using?
- How many front-end clients interact with our server?
- Is this a monolith or micro-services?
- Is there an API?
- Do we integrate with 3rd party API's?
- What technologies are we using?
- How many environments are there besides production?
- Which branch deploys to which environment?

You will be surprised how many things you will discover about a project by gaining an understanding of the overall architecture and at some point
you will likely run into issues with deployments or certain bugs that require knowledge of this anyway.

⭐ Pro Tip: Create your own diagram of the architecture. It will come in handy later when you forget things. You could also add it to the documentation to
help future developers onboard.

---

### UI Walkthrough 🖥

This may seem more obvious, but why not book in a chat with someone from QA or a developer to walk through the UI.

Often it will be too vast to walkthrough all of it, so I find it helpful to ask to walkthrough the part of the UI that you will likely interact with most 
in your work. Go through some happy paths just to get a brief overview and you will pick the rest up as and when you encounter those areas.

⭐ Pro Tip: If the project does not have a UI, ask for a walkthrough of the API docs or even better a walkthrough on [Postman](https://www.postman.com/) where you can see those API requests in action.

---

### Codebase Walkthrough 👨‍💻

I have actually rarely seen this done, but a senior developer on a project I joined recently did this with me and I found it really helpful.

The idea is not to go into detail and look at individual lines of code or do any deep dives, you can do that when you get a task in that specific area. The
main purpose is to get a high level overview of where certain parts of the code live. Focus more on folders and files rather than what is in those files.

It can be as simple as where `assets` are stored or where the `JS` files are kept. But often it will actually expose certain design patterns that are used in the
codebase and this is a good springboard for asking questions about certain styles within the code.

---

### Pull down the repo and get it running locally 💻

Finally! 

Something I never do, but I should, is actually read the `ReadMe`!

So often I just jump into trying to get the project set up that I overlook something as simple as reading the `ReadMe`. I then 
ask questions only to be sheepishly redirected back to the `ReadMe`. Hopefully it is up to date and will help you get the project set up locally.

But if there is something not up to date, make a note of it, even something as simple as typeo, remember that because we will use that to our advantage later.

---

### Generate an ERD diagram 📈
 
If like me, you are a visual learner, I find this to be a neat trick to help you to get up to speed with the database quickly, without having to trawl through the 
`schema`.

There are different tools out there that can do this for you, but if you are using `Rails` there is a [great gem](https://github.com/voormedia/rails-erd) called `rails-erd` that
will do this for you.

This can help you to also understand the size of the system you are working with, how many data points there are, and if there is a [big table](https://wiki.c2.com/?GodTable) you need to watch out for.

---

### Lets ship a thing 🚢

Remember that typeo we spoke about earlier, let's use that to our advantage.

You might not be ready to commit any working code to the project yet but you might be able to improve some documentation somewhere that lives inside the 
repo after your own onboarding experience.

Create a card for this change like you would for any coding task. Treat it exactly the same as you would any coding task even if it is only a minor correction.

You might feel like this is overkill, but this is a really good way to learn the workflow of making a change on a feature branch and deploying that change
through the different environments all the way to production with minimal risk. You will also see how you move the card along on whichever task planner tool
you use.

You will get to learn and ask questions about the end-to-end process from development all the way to production in a relatively safe environment. This will
lessen the information load when you come to work on your first code-based task and allow you to focus on the code itself without having to also learn the
process at the same time.

---

### Ask for easy tasks/cards 😃

Yep that's right, explicitly ask for easy tasks! 

We already set expectations when we spoke to the client about the discovery phase, so lets use that time to do some discovering.

The purpose of asking for easy tasks is not to give you an easy time (even though by now you deserve one!). The purpose is also not to be able to ship 
things quickly. Everyone knows you could change the wording of a button quickly. 

The purpose of an easy task is to give you time to look at that area of the
codebase and learn some things about it. Removing complexity from the task itself allows you to focus and work through the complexity of the codebase whilst 
feeling slightly more comfortable about being able to make a rather trivial change. 

You will likely encounter some design patterns and get a feel for some of the 
automated tests that might be used, as well as linting, and hopefully it will be a springboard for pairing with other developers as well.

⭐ Pro Tip: Ask for 3 or 4 simple tasks that all focus on the same area of the code. Focusing on one area to begin with can help to reduce cognitive overload
and you can dive into other areas of the code at a later stage. Start small and simple.

---

### Ask any question ❓

Lastly, ask, ask and ask some more.

It can feel embarrassing sometimes to feel like you are asking so many questions and even vulnerable to be showing others that you know very little.

But at some point on this project everyone knew nothing. Everyone asked the most simple questions because no one was born with the divine knowledge of how these things worked or came to be.

So allow yourself to be human and ask away.

---

I hope you find some of these tips useful. 

It goes without saying that everyone onboards in different ways and ultimately everyone should onboard
in the way that feels most comfortable and natural to them. 
There is no one size that fits all. 

But maybe you can add one of these tips to your 
onboarding arsenal for the next time you join an existing project.


Thanks for reading! ✌️
