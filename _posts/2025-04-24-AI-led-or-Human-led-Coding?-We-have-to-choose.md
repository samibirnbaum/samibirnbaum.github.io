---
layout: post
title: AI-led or Human-led Coding? We have to choose.
---

It is time we take a closer look about how we code with AI and the ramifications on our industry.

<!--more-->

## I should never have clicked the button

Something really challenging happened to me at the back end of last week. In retrospect it probably wasn't surprising, but it was challenging nonetheless.

I had been working on a feature to add some permissions to a codebase, a relatively trivial feature. It was a codebase that I only started working on a couple of weeks ago so I took the time to understand the problem and get familiar with some of the architecture.

Within 3 hours I had a PR up and was confident in my changes.

As I went to close the corresponding GitHub issue I saw a button that I had not seen before on the GitHub UI: "**Code with Copilot Agent Mode**".

![A picture of a man standing next to a button with a sign saying not to push the button](https://images.thoughtbot.com/jg4jqxxr3o7ciojzzhcktl8wfix6_10cf08f51904cd9896466b29f7db08d2.jpg)

I should never have clicked it! I had completed the feature anyway and was only on GitHub to close the issue, but my curiosity got the better of me...

And so I clicked the button. Little did I know that this would lead to a weekend of ruminations, questions of self-worth and angst.

Instantly, GitHub opened a new tab in the browser to an online instance of Vistual Studio Code for the given codebase. But it didn't stop there. The editor then gave birth to a right-sided panel with Github Copilot in **Agent Mode**.

I watched aghast as the GitHub issue description was injected into the right-sided panel prompt and the Copilot Agent proceeded to get to work creating files, editing files and running terminal commands to add the same
feature that had taken me hours, in **minutes**.

Queue existential crisis and a long weekend of ruminating about how life would never be the same.

![A picture of a penguin looking thoughtfully into the distance](https://images.thoughtbot.com/vklzs9qqao3lonc1bgi5o2j8mtew_images.jpeg)

I should add one caveat here that technically speaking the Copilot Agent did not complete the task, it did get close but it required me making some changes and prompting it a few times here or there.

However, I could not shake the question, **should I be using a Coding Agent going forward?** I know it would take some time getting used to but maybe with enough context and prompt engineering this is the new way to code!

I ruminated on this for far too long over the weekend, but I decided to collate my thoughts so hopefully it prevents someone else having to ruminate in the future.

## AI is not going away

My initial reaction was to try and negate AI entirely. My mind considered AI to be a threat and so it felt reassuring to try and remove AI entirely from the picture.

I did this by conjuring up thought processes about AI just being some sort of hype or even better the world simply running out of energy to support AI infrastructure allowing the way we code to return to what it once was.

Whilst this felt reassuring, the sense of calm was short-lived because this did not seem realistic or likely.

I therefore had to come terms with AI being a part of how we code. The horse has bolted and cannot be returned to the stable.

## So what are my options?

### Human-led coding with AI support

This acceptance allowed me to reframe my concerns.

I probably will be using AI when I code, but perhaps there are different ways or methodologies of coding with AI.

I thought about how I currently use AI when I code, before I clicked that dreaded Copilot Agent button.

I tend to take time to understand a problem so I can consider an appropriate solution whilst taking into account the bigger picture and overall code architecture. We can call this the planing phase.

I then utilise [TDD](https://thoughtbot.com/upcase/testing) and [outside-in testing](https://thoughtbot.com/upcase/videos/outside-in-testing) to consider the best place to write my first test that will help me drive towards the most efficient solution. We can call this the implementation phase.

In either of these phases I may reach out to an LLM to ask a question about a concept I do not understand or to help me with some syntax, but it is **I** who chooses to reach out when **I** feel the LLM will best benefit me.

I like to think of this as **Human-led coding with AI support**.

![A coder controlling a small robot like a puppeteer](https://images.thoughtbot.com/nn56evwbz662qydp4v6x3q2vh9yz_ChatGPT%20Image%20Apr%2023%2C%202025%2C%2005_15_11%20PM.png)

### AI-led coding with Human support

The other, recently discovered, way of coding with AI using the Copilot Agent looks rather different. It tends to start with an AI prompt and the AI sits in the driving seat going through the planning and implementation phase simultaneously.

Your role is to check over the AI's work and make corrections here or there.

A helpful way to think of this is **AI-led coding with Human support**.

![A robot controlling a coder like a puppeteer](https://images.thoughtbot.com/j0rbvqgm18frdaho9fjl6ne0hzxs_ima123ge.png)

Being able to verbalise and conceptualise these 2 different ways of coding was really helpful. I could now see two approaches to coding with AI.

Human-led or AI-led.

## But which one will you choose?

It is important to acknowledge that both options are valid.

Both can be used and will be used by different people. They are both options available to software developers, and like any choice about tools and implementations both have their advantages and disadvantages.

However, on a very practical level, one needs to make a decision about which one to use. This was my next conundrum to grapple with:

**Should I be a Human-led or AI-led developer?**

## Do I have to choose?

But before I answer that question I think it is worth considering why you need to make a choice. Why do we have to be the ones to make a choice about how we code?! Surely we can just ride the wave and see where things go?!

The answer to this question hinges on the assumption that AI companies have our best interests in mind.

They don't.

Let me use a social media example for a moment.

Whilst social media does a lot of good, the companies behind many of these platforms are primarily interested in money and this often correlates with screen time. They are not producing these applications for the betterment of society but rather to increase screen time of their users.

Social media is neither inherently bad or good. However, the onus is on us as individuals to decide how we incorporate social media into our lives. If you use social media without clear boundaries or choices you will
probably find yourself using it in unhelpful or unhealthy ways.

The same, I believe, is true for coding with AI.

AI is encroaching more and more into our craft and the way we work. It will continue to do so, for the same reason social media continues to do so, money. It will not be done with deep thought for the betterment of
software, our craft, or the craftspeople.

![A meme with two men labelled "Big Tech" and "VC's" shoveling money into a furnace labelled "AI"](https://images.thoughtbot.com/zjgi6qk0n8q1i6pvdccd6c5ndvjd_3a676706-30c6-4998-949a-0ca5f6637854_368x317.jpg)

Therefore, making a decision about how to use AI becomes a choice you have to make, boundaries you have to consider, it cannot be something that is left to prolificate unattended.

## Should I be Human-led or AI-led?

It is a difficult question to answer because I can only do so based on the knowledge I have in front of me now in an ever changing landscape. It is also difficult because very often in coding the answer is "it depends".

Whilst these are both true I think it is helpful to establish a general rule, notwithstanding the exceptions.

I believe we can do this by looking at key values within software development.

### Speed 🏎️

I think about what life would look like as an AI-led developer. Immediatley, I think about completing features far quicker, the speed with which code could be written and features could be shipped.

But I wonder if, in this case, looks can be deceiving.

Because AI code requires checking, a craftsperson who cares about their work and the impact on the wider codebase as a whole will not be able to avoid having to understand the problem properly and the ramifications of the solution.

**I don't think you can avoid that "planning phase". All you can do is delay it until later.**

Arguably, it is harder to understand a problem or a solution after it has been written (think code reviews and understanding old code).

However, AI-led development lends itself to this.

Human-led development is arguably less cognitively intense as it allows the planning phase to happen sequentially and not retroactively.

And be careful not to misunderstand me here, Human-led development still involves the use of AI. I am not arguing to down AI tools. However, Human-led development allows you to utilise the speed of AI for smaller tasks along the way which shouldn't require intense checking.

### Knowledge 🧠

I don't have a metric for this but I believe my assumption is reasonable.

Imagine an AI-led developer who spends most of their time doing code reviews and making tweaks. They are working with a preconceived notion of how to solve a problem and are evaluating that specific problem. They are utilising different parts of their brain in comparison to the Human-led developer.

The Human-led developer has to start the process with creativity and critical thinking. They may have 5 different options of how to build a feature in front of them. Some of those may involve different technologies and
perhaps architectural changes.

In order to make an informed decision they will have to have a broad enough knowledge-base to weigh up the best approach.

This sort of creative and broad thinking, I believe, forces a developer to have a better understanding and deeper knowledge of the whole software ecosystem.

AI-led development does not lend itself to this as it proposes a solution which will naturally create a bias towards pursuing that solution.

In smaller features this may not have an impact but overtime I believe there will be a vast knowledge gap between AI-led and Human-led developers that will be fairly self-evident and when it comes to working on bigger, more diverse software projects. You will want that broad-knowledge and versatility which AI-led development does not foster.

As I said, it is a hard metric to quantify but I think over the next couple of years we will see the impact of this within the software developer community.

### Prompt Quality ✍️

The knowledge factor also plays a big role in the quality of your AI prompts.

You may have heard people say that an LLM is only as good as the dataset it was trained on. Whilst this is true, there is another truism that should not be ignored.

**The output of an LLM depends on the quality of the prompt.**

Consider the following 2 prompts for a performance issue:

"I have a query that is slow, how can I make it faster?"

"I have a query that I believe is slow. I am not sure if the slow performance is happening in application memory or at the database level with the `SQL` query. Here are the results of the `EXPLAIN ANALYZE` query I ran. I would like to first be able to benchmark the query at the application and database level so I can determine where the transaction is the most expensive and also so I can measure any improvements. I am also wondering if there are some other options available within Postgres, perhaps creating a `View`, because the table I am querying has lots of records, what do you think?"

As you can see, there is a major difference between the 2 prompts. The former is not a bad prompt and will likely yield some results, but the focus is more narrow on the database component.

However, the latter utilises a broad knowledge base to include the application speed and also opens up the LLM to using a different approach.

This is another reason why knowledge is important and my theory is that Human-led developers will write better prompts because they have maintained a broader understanding and critical thinking habits.

### Scale 🏗️

But lets say you really love doing code reviews and reading through legacy code and you enjoy the path of least resistance, so you are willing to forgo the knowledge gains.

I still feel that at some point you will run into limitations with AI-led development.

Anecdotally, I have played with AI-led development on a personal side project and what I found is that the complexity of the code increased as the codebase got bigger and more features were added.

As a consequence, the LLM started to provide less accurate results and solutions that did not work. This led to even more complex code and a codebase that was very difficult to work with.

From my experience, this forces you, at some point, to return to Human-led development.

### Code Quality 🧑‍💻

I have often considered why this is and I think it comes down to the biggest challenge of writing software.

**The biggest challenge is not writing code, it's writing code that is resilient to change.**

Just ask [Sandi Metz](https://sandimetz.com/products) who has written books dedicated to this topic.

At some point the requirements will change and therefore the code that you (or someone else) has written will be required to change.

**The biggest cost will be your ability to make that change.**

Have you ever heard someone say we need to rewrite this software all over again?!

The reason rebuilds are required is because the **cost of change outweighs the cost of a rebuild**.

That means your codebase is so complex and convoluted that it is struggling or unable to adapt to requirement changes.

This is a bad place to be.

Kent Beck and Martin Fowler touch on this in their book Planning Extreme Programming (XP Series), where they talk about the different levers you can pull to increase your development speed:

> The other lever is internal quality. This reflects the quality of the internals of the system: how well it is designed, how good the internal tests are, and so on. This is a very dangerous lever to play with if you allow internal quality to drop you'll get a small immediate increase in speed, rapidly followed by a much bigger decrease in speed. As a result you must keep an eagle eye on this lever and make sure it is always up as far as it can go. Nothing kills speed more effectively than poor internal quality.

And I believe that AI-led development puts code quality at risk.

There are three main reasons why I think this is:

#### 1. Narrow vision

In my experience LLMs tend to focus on fixing the issue at hand based on the prompt provided. This naturally lends itself to a narrower vision.

In contrast a human can take into account the bigger picture, the codebase as a whole, wider business requirements as well as intuition about what the future holds.

#### 2. Refactoring

One of the most important things you can do as a developer is refactor as you develop new features. This was captured by Kent Beck when he said:

> First make the change easy, then make the easy change.

Humans are good at this, we start to build a new feature and notice a code smell or some code that doesn't seem to be a part of a given object and would be better placed elsewhere.

These small incremental refactors are what keeps the whole codebase ticking along and resilient to change. It is the versatile midfielder in the middle of the pitch keeping the rest of the team in good shape so they are ready for the next phase of play.

In my experience LLMs are not good at spotting these changes and making them unless actively prompted to do so with some good old Human-led development.

#### 3. Technical Debt

Have you ever thought about what the biggest contributor to technical debt is?

In my experience it is speed.

There seems to be a correlation between moving quickly and accruing technical debt.

Unfortunately, AI-led development lends itself to coding faster but speed is not always the best thing because it comes with consequences and one of those consequences is technical debt.

### Slowly does it 🐢

There is another more subtle consequence of everything happening very quickly.

Have you ever noticed what happens when you are working on a feature but not writing code. The pauses in between, perhaps when you run your specs or just stare at the trees in the wind.

**Pauses or moving slowly allow space for thought.**

These moments are sometimes the most important as they are the moments when your brain is allowed to wonder and you think about a new edge case that no one else has thought of, or a better architecture that unblocks future development.

Numerous times whilst working on a feature I find myself creating cards for tangential improvements that have risen to the surface along the way.

Moving slowly comes with this benefit, time allows the brain to absorb information and for thoughts to rise to the surface.

Human-led development allows for these moments.

### Enjoyment 😄

This sounds obvious. It is important for us to enjoy what we do.

Perhaps AI-led development is more enjoyable for you but I've always enjoyed the craft.

For me the enjoyment is sometimes less about the destination and more about the journey.

I like being in the weeds of the code, going deep into a bug and the root cause. I find the process engaging and stimulating.

**But it goes deeper then just having a good time.**

Humans need joy to be productive. We think and perform at our best when we are happy. The inverse is true for demotivated people.

If AI-led development is not enjoyable for you then human nature is to be less creative and struggle to maintain high levels of care and attention because you are not enjoying your modus operandi.

If AI-led development makes you feel this way then you should feel **empowered to choose** Human-led development for its enjoyment and the way that contributes to yours and your teams productivity as a whole.

## So what's it gonna be?

As I said before both AI-led and Human-led development are valid options and there are tradeoffs between the two.

But I believe that we have to choose.

![A coder thinking about whether to be an AI-led developer or Human-led developer](https://images.thoughtbot.com/kczoqhucz2i44u42804gil18hg1i_ChatGPT%20Image%20Apr%2024%2C%202025%2C%2002_45_43%20PM.png)

At this stage in history we don't have quantitative metrics that tell us which way to choose, I believe it will take a few years for those to arrive. However, we can use our experience.

We have to carve out a way that works for us, and in order to do this we must create boundaries and make a choice about how we want to incorporate AI into our lives and into our industry, because the AI companies will pursue their own agendas which may be different to ours.

We care about what it takes to build great software of the highest quality which can stand the test of time.

I take pride in Human-led development.
