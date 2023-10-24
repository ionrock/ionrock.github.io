+++
date = 2019-12-13T18:52:52Z
description = ""
draft = false
slug = "manager-deliverables"
title = "Manager Deliverables"

+++

One of the hardest things going from programming to managing has been the change in output. People often write about it is challenging being a manager because you don't get those quick wins like you do as a programmer. Some challenging bug doesn't get fix in a day and you don't get repeated test suite passes as you work. Instead, you are forced to look at the larger picture, waiting for projects to get to a state where they can be communicated out for public consumption. At first this wasn't that hard for me to deal with, but I'll admit that now, I'm feeling antsy and would love some way to check in some manager code in the nonexistent manager version control system.

The problem is, as a manager, what do you really deliver? I've read articles about this sort of thing in general terms. As a manager, you likely work with budgets, job descriptions and communications regarding a project road map. But no one really tells you what that looks like in practice. Some aspects are organization specific like how you handle your budget requirements. While other pieces, such as a road map for your team, don't have a predefined format or well established tool in place. To put this in perspective, imagine having to write software without any obvious choices for your code editor, version control, deployment platform, and Stack Overflow and you start to see why this is a big shift.

At this point, I'll try to share what I've been using. Honestly, I can say that I've been using it successfully, but something is better than nothing!

First off, we use Confluence so that is the deployment target for a lot of this information. Our confluence homepage includes some important elements.

* List of the team members and what they do
* Documentation and links to important resources
* Instructions on how to work with the team (for example, how to run an experiment)
* The team mission and functions

This information comes from a team charter document that includes sections for:

* Team Composition
* Mission
* Objectives for the year
* Engagement Model
* Services We Own (may not be helpful for every team)
* Commitments
* Vision

This is kept in a Google doc that we occasionally revisit. This is all information that often comes out at offsites for getting the team aligned towards a shared goal. Once we have this doc sorted out, we'll add the relevant bits to the confluence page.

Another aspect we keep front and center is the list of projects we work on. Each project summary should have:

* Problem it aims to solve
* Goals that are achievable
* Stakeholders
* Deliverables for the project
* What is in scope and out of scope (clearly define what you will and won't do)
* Success Metric
* Design

Here the design is not necessarily an in depth element, but something that helps the organization at large understand the project. This is not a where you put mock ups or architecture used for the implementation. It is where you summarize the behavior so people understand what the deliverables will actually look like when the goals are met.

We also keep a lot of our agile ceremony docs in our confluence page. Things like retros and some planning docs intended to communicate up and out. These end up being team specific, so do what works as it often changes.

Another document that I keep around is a road map spreadsheet. This is something that I don't always do a good job keeping up to date, but with that said, the format was given to me my manager and I think reflects some good ideas regarding what is important about a road map.

Here is how it looks:

<table>
    <thead>
        <tr>
            <th colspan=4></th>
            <th bgcolor="lightgreen" colspan=3>Q1</th>
        </tr>
        <tr>
    	    <th>Project</th>
        	<th>Staffing</th>
        	<th>% Allocation</th>
        	<th>Role / Task</th>
            <th>Jan</th>
            <th>Feb</th>
            <th>...</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>Coral</td>
            <td>Mary</td>
            <td>35%</td>
            <td>Feature Work / Dev</td>
            <td bgcolor="lightblue"></td>
            <td bgcolor="lightblue"></td>
            <td></td>
        </tr>
    </tbody>
</table>

There are a couple important elements that are helpful. First off, the staffing aspect is important because you are providing a high level overview of what you expect the person to work on. More importantly, you're declaring the bandwidth of the team. You'll likely have projects that have no staffing until much later in the road map because you don't have the resources. When you need to ask for more people for the team, the road map clearly shows what these people could be working on and how it can impact the business. It also clearly shows why some project can not be done without shifting priorities. At a higher level, it reveals the justification for the team. Projects don't always need a fully staffed team. They can eventually be set on autopilot, so it is important to have some documentation why your team exists and what it brings to the organization. Lastly, this is a good place to ensure you link to relevant tracking tools and documentation over time. This helps to make sure it stays relevant and useful to you, as the manager.

I'll admit right now I'm pretty horrible at keeping this document up to date. I often punt and just use our Jira to keep track of essential project tasks. That said, I also have run into the situation where I'll need to scramble to get a road map together for a specific ask. If I had this up to date, that ask would be much easier.

This is clearly not an exhaustive list of things, but hopefully it presents some options for how to think about what you should be doing as a manager in terms of day to day output. As a programmer, it can feel pretty terrible to simply update this content all the time. But, it really is valuable as a leader. As a manager, it is your job to understand what is being worked on and what will be worked on in the future according to the needs of the organization. You need this understanding as you represent the team to the rest of the organization. Now, if only there was a nice plain text tool that I could use with Emacs to work with all this stuff!
