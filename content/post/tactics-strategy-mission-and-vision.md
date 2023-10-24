+++
categories = ["management"]
date = 2019-01-14T22:30:00Z
description = ""
draft = false
slug = "tactics-strategy-mission-and-vision"
summary = "My attempt to understand tactics, strategy, mission and vision as it pertains to organizations."
tags = ["management"]
title = "Tactics, Strategy, Mission and Vision"

+++


When I read about "strategy" I'm often not clear on what the intent is for a business or leader. Is strategy more general and long term where as a tactic is typically limited? I've [read](https://diogomonica.com/2018/10/07/a-pirates-take-on-strategy-vs-tactics/) "Tactics is the use of armed forces to win battles; strategy is the use of battles to win the war.”  This all makes sense in the abstract, but when I try to define a "strategy" or "tactic" it gets murky fast.

Another pair of terms that gets confusing is "mission" vs. "vision". There is some variance in actions vs. end result respectively, but again, that is one subtle difference if you ask me. They say those can't do, teach, so with that in mind, I'll try to tease apart these terms to see if we can't find some practical advice when confronted with the task of communicating your strategy, tactics, mission and vision.

## WARNING

I want to be really clear here that you should not be looking at this document as some sort of reference. It is an exercise for myself to have a reason to try to better define these terms for my own edification. If you get something from it, that is great! If I'm wrong or get you confused, that is on you. Wish me luck!

## Strategy vs. Tactics

I played chess a lot in high school and there were tactics like [forks and skewers](https://en.wikipedia.org/wiki/Chess_tactic). The thing about a tactic was that it was really just a tool. It wouldn't win you the game, it just helped you gain advantages. Strategy, on the other hand, provided some guidance. For example, in chess it is a strategy to [control the center](https://chess.stackexchange.com/questions/5142/why-is-the-centre-of-the-board-considered-important-in-chess) of the board. This is provides some guidance of what you're working towards in the absence of a concrete goal. When you start a game of chess, you're goal is checkmate, but you need some strategy to help get there when there isn't a clear path.

Putting these together, you use your tactics as tools to accomplish your strategy, which should put you in a position to hit your goal. Outside of chess, your goal might be to increase reliability of your service (think an SRE team). One strategy might be:

> Ensure every team has a clearly defined set of metrics to measure reliability.

One tactic you might take would be:

> We will place a SRE on every development team.

None of this says it will work, but hopefully this helps clarify the idea bit more within the scope of a team. If you are thinking tactically, you might be brainstorming ideas that might be helpful meeting your goals. Strategic thinking is likely seeing what tactical ideas might allow the team to achieve some milestone. There are likely tons of other great examples, but I think this gets the point across well enough for now.

## Mission vs. Vision

Unfortunately, I don't have a really concise example or analogy to differentiate between a mission vs. a vision. The mission should provide the big picture of what you're actually doing.  The QA organization in a company might have a mission of:

> The QA team ensures the quality of our product through maintaining the quality of our code.

I'm sure this isn't a great mission, but it does suggest couple elements that have an impact for how the group works. For example, "the quality of our code" suggests that QA is not a group of people clicking in the application performing smoke tests. No, the work involves being involved in the code base, possibly writing tests, integration frameworks, and improving the CI pipelines. The point being, the mission is helping to define the work getting done in generic terms that offer some direction, while at the same, being general enough to grow over time as the organization changes.

Vision, on the other hand, is intended to be what success looks like in the long term. Going back to the the QA org for a minute, the vision might be:

> To allow teams to move fast and break things without breaking them in production.

Again, I doubt this is an ideal example, but it does reveal a bit more about what the vision should provide. Compared to the mission, the vision provides a long term target to aim for. In this case, it shapes the QA function in terms of speeding up iteration time while ensuring quality. To contrast, it could have been focused on ensuring quality at all levels of the stack or protecting the customer, both would result in very different outcomes. Even though this vision isn't great, it starts to shed light on what a vision **may** accomplish. The purpose is to provide where things are headed on for the longer term in such a way as to contextualize the work.

## Why does it matter?

As a software engineer, it can be hard to understand why these things matter at all. The big reason is yet another bit of managementese, alignment!  My own practical understanding of alignment is when people make daily decisions that are in line with the group's goals. People understand what it means to be "in line" by referring to the defined strategy, mission, and vision. As confusing as this stuff can be, it should be clear why it is important. It is an artifact of the culture and provides an internal compass when we make all our small daily decisions at work.

While I can't be positive, I think this exercise has been helpful for me to better understand what these different terms mean and how to write them. If anyone things I'm totally off here, please get in touch and let me know.
