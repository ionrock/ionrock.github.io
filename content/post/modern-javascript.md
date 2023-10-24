+++
date = 2023-09-27T14:54:13Z
description = ""
draft = true
slug = "modern-javascript"
title = "Modern JavaScript"

+++

Recently, I've embarked on a journey to write code again. It has been a long time since I've built something, especially with any UI that wasn't a CLI. I don't have any lofty goals to do something innovative. I just want to quickly display and work with data in a database. I had hoped all the new tooling would make this easy. I was wrong.

My path started with [Next.js](https://nextjs.org/) and [Fomantic](https://fomantic-ui.com/). The Next tutorial was helpful and I got something up and running. I had already created a Go web application. I hoped that I could quickly connect the two together. I punted on this momentarily as I heard [Tailwind](https://tailwindcss.com/) was the better CSS framework to leverage through [shadcn/UI](https://shadcn-ui-theme-explorer.vercel.app/default/home). This all seemed promising at first. I played around with fake data and managed to make a few components that seemed promising. It was at this point I hit a wall.

When I tried to connect to my API, things became extremely cumbersome. Next has a handy local development environment that spins up a web server and supports some node.js "API Routes". It meant I'd need to spin up my web app separately. This isn't a dealbreaker, but it means considering it a separate service with a different address to connect to. I had hoped to use some Go code for things like auth, but if we have two distinct services, I can't rely on simple cookies (even though it would have worked locally on localhost with different ports). Beyond this, there was very little automation that I could find to load the data. I believe using Typescript would have allowed me to define types on the front end that duplicated my types in my API, but that seems like I just created two model definitions I'd need to keep in sync.  That feels like a waste of time.

I'm sure there were options around gRPC that could have helped avoid redefining types everywhere, but it was not obvious. I didn't dive deep into
