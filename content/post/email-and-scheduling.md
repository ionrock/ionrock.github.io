---
categories: ["emacs", "notes", "productivity"]
date: 2019-02-26T17:16:41Z
description: ""
draft: false
slug: "email-and-scheduling"
summary: "Isn't there some other email and calendar other than G Suite?"
tags: ["emacs", "notes", "productivity"]
title: "Email and Scheduling"
---

For a long time I used [Emacs](https://www.gnu.org/software/emacs/) ([mu4e](https://www.djcbsoftware.nl/code/mu/mu4e.html)) for email. It worked pretty well in so far as I was able to quickly read and participate in mailing lists, copy relevant links to my TODO list and work through a healthy amount of email quickly. Generally, things were good, but there was definitely some friction. I really couldn't send HTML emails. This wasn't a huge problem, but it did limit my ability to include images and links were arguably a little kludgey. Personally, I was OK with it, but often times when communicating out to a larger audience in the company I'd go ahead and use the Outlook Web client. Another pain point was that I needed to sync my email on a cadence. Every so often that meant an important email could be a little late. Again, nothing too horrible, outside of missing the context of some conversations around the office for a minute or two.

For my calendar, I never could get a reasonable Emacs situation. I did try a few tools that would sync my calendar to org files. From there I could use the built in org agenda, but it was difficult to get into a flow with this because meeting invites needed to be confirmed, which ended up needing to happen in my actual calendar.

Lately, I've just used G Suite for my email and schedule, which is generally OK.

The other day I needed to use my laptop without the power attached and realized that part of the reason my battery life was so poor was because Chrome used so much power. Part of this was simply too many tabs open, but even after reducing my tab count, I realized I still always had my mail and calendar open in pinned tabs and they seemed to be using CPU pretty consistently. This got me thinking, once again, about other options.

After searching a bit, I came back pretty disappointed. I can certainly use Emacs for email without much issue. I think if I were to dive back in, I'd like to find a good way to send HTML email, including my company signature. For the calendar, I'm much more limited. I generally don't look at my meeting requests and just see optional events on my Google calendar. A quick click and I can confirm I'm coming or decline. When I looked at other desktop calendars for linux (there are few...) not only were they rough around the edges (naive text clipping), I lost the simple attending functionality. What's more, notifications become something of an unknown. Thankfully, it seems GNOME provides notifications, but it doesn't seem very configurable.

At the end of the day, I'm OK sticking to G Suite, but part of me is sad there aren't more options. I remember when "productivity suites" were a big deal and there were a few good competing options out there. I think the problem ends up being really hard because the software that controls the server has a huge advantage over any other clients. This is one of those areas where there is unlikely going to be a large number of Open Source options because it is such a huge challenge. It takes too much time to cover the account management, email and calendar APIs along side creating a good user interface for a group of volunteers to create something really good. This is especially true when there are some options, like [Evolution](https://wiki.gnome.org/Apps/Evolution/) and [Thunderbird](https://www.thunderbird.net/en-US/), that already have developers interested in the space.

I'll probably still play around with using Emacs for this some more. The end of the day, I don't actually have to use email that often and I like the idea of keeping my calendar view in Emacs, close to my notes. I'm hopeful that tools like [Nylas](https://www.nylas.com/) might help reawaken some of the interest in "groupware" tools a bit. Every so often I wonder if I need to go out and get a tinfoil had to avoid the prying eyes of Google, but it doesn't take long to feel the huge amount of friction moving would be. Until then, I'll keep my eyes peeled for other options.
