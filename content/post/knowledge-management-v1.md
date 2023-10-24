+++
categories = ["emacs", "notes"]
date = 2019-02-10T20:00:00Z
description = ""
draft = false
slug = "knowledge-management-v1"
tags = ["emacs", "notes"]
title = "Knowledge Management"

+++


When I'm in meetings, I try to take notes. There are TODO items, things I'd like to remember and questions I might want to ask about. The problem is that I don't have a good way of taking this information and easily using it when I'm doing the work. All of these notes go in an [org-mode](https://orgmode.org/) file in [Emacs](https://www.gnu.org/software/emacs/), but it is pretty ad-hoc, even though Org supports features like [agendas](https://orgmode.org/org.html#Agenda-Views), [tagging](https://orgmode.org/org.html#Tags) and [meta data](https://orgmode.org/org.html#Properties-and-Columns). I'm taking a stab at getting more organized and thought it would be good to share my first iteration.

The first thing was to break up the single file into separate files. I created a inbox file to capture random notes. Org has a capture feature that allows you to quickly add notes using templates, so my plan is to add notes to my inbox file and process it accordingly. The other files I have are for todos, meetings and standups. The todos file is intended to be a backlog. Meetings is where I'll track meeting notes. When I do find a Todo item in a meeting, I'll try to capture that in my Todos. 

The stand up file is where I schedule my day. I take a note of what I did yesterday and usually add Todo items that I'll be working on that day. I was currently doing this in my ad-hoc standups file, but the means of scheduling the action items I'd generate throughout the day wasn't really working. Org has a refile concept that I'm hoping to let me move things around as I decide to work on them. 

Org is a really powerful tool. I'm sure as I try out different techniques, new features might become more helpful. It is also fun to hack a bit with Emacs to make things a little easier. What I'm most excited about is the opportunity to create a real knowledge management system. The balance between low friction and valuable process likely changes over time based on experiences. I feel like this investment will help keep this balance while providing a fun way to keep hacking.



