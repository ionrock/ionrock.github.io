+++
date = 2023-08-03T16:04:18Z
description = ""
draft = false
slug = "velocity"
title = "Velocity"

+++

I've been thinking a lot about team velocity. IndyCar's are some of the fastest race cars and get up to a top speed of 236mph, but compared to Top Fuel drag racers that hit 329mph, they are quite a bit slower. The obvious difference is that drag racers don't turn!

Applying this to organizations and teams, velocity requires two critical elements.

1. A Speedometer
2. A Finish line

Going fast is arbitrary, but 120mph is a measure. Similarly, building lots of tools, automation, etc., is pointless if you're not driving toward the user's success. Digging deeper, the question a team or organization needs to answer is what are you measuring that makes visible the speed, and what are you measuring that gives feedback you're on the right track.

The DORA Metrics are a good place to start measuring team velocity. They are:

* Deployment Frequency
* Lead Time for Changes
* Time to restore service
* Change Failure Rate

These metrics are powerful because they reflect essential deliverables, such as how often you deploy to more cultural and process measurements when considering the time it takes for changes to reach production. You can consider other measures depending on your organization, but these are a great start.  In a nutshell, these are good monitors for an engineering org.

The next challenge is to ensure there is a precise finish line to focus on. This is where things become more complicated because while DORA metrics are helpful to measure how fast you're going, the success of the organization is measured by very different metrics. Assuming the organization is a business, we can generalize the business metrics into a few different buckets.

* Revenue - Did some products make more money?
* ARPU/MRR/ARR - Are users spending more with the business?
* Funnel - This is where the business sees a proxy to future revenue.

It is exceptionally hard to connect work teams do directly to these sorts of metrics. There can be organizational hurdles in the way such as access to the data. The impact of some projects may have an extended lead time before it is reflected in the business. The business may be looking at the wrong metrics where making an impact isn't actually helpful.

There are many exercises, such as [Goal Tree Mapping](https://support.optimizely.com/hc/en-us/articles/4410288505741-Improve-metrics-that-matter-with-your-optimization-program), that aim to help with aligning impact. These are helpful for organizations to go through, but as a team, it is often out of your control. To effectively attribute work to business metrics you need two crucial elements.

1. Metrics the team can influence
2. A story to communicate how this impacts business metrics

The metrics a team can influence can come from existing metrics the team tracks. The key is to find metrics that obviously influence business metrics in the eyes of leadership. This is where the story becomes critical. For example, if there is a Kubernetes team that supports the engineering organization, the story around meeting SLOs is likely not enough. It is more powerful to contextualize the SLOs around the work the team has accomplished that reflects the reason the team exists. Have we seen more or faster deployments? Have tweaks allowed more efficient use of the infrastructure? The story is where you connect the daily work to an impact on the business and offer a clear metric that you can continue to report to leadership and improve upon over time.

The first step is simply recognizing an important metric that impacts the business directly. A Product Engineering team need only look at the borders of their services to see what makes sense. There is some call to action somewhere that leads to an API call you can measure. This is where you start and evolve from there. If you find your work doesn't influence this API call, ask yourself 2 questions.

1. Why doesn't our work improve this metric?
2. Does our work protect this metric?

If your critical API calls are not changing due to the work of the team, can you go faster? Is a major refactoring safe to do? Do you have the headroom to try new things? Is your service reliable enough? There is value in maintaining the system. As a team, when you don't have a lot of influence on customer behaviors, that is the time to start testing the limits and trying new things that didn't seem possible.

It is not enough to simply go fast. The goal is to win the race and there are rules. The rules involve communication with your leadership and helping others understand why the work is valuable. When you find that communication is exceptionally difficult, you might need a different metric or you might need to change directions. Thankfully, when you go fast changing course only becomes easier.
