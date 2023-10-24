+++
categories = ["linux", "productivity"]
date = 2019-03-03T04:16:37Z
description = ""
draft = false
slug = "not-quite-the-year-of-the-linux-desktop"
tags = ["linux", "productivity"]
title = "Not Quite the Year of the Linux Desktop"

+++

Every so often I get tired of looking at the same old screens. It is not as if there are tons of programs I use throughout the day. There is a web browser, slack and Emacs. At some point I get antsy and want to see what is I could improve things. Specifically, I recently was thinking about my desktop environment and if something lighter weight might help save a little power and speed things up. The tl;dr is that I started with the default [GNOME](https://www.gnome.org/) that comes with [Pop_OS](https://system76.com/pop) and I'm going to be continuing with it using a different theme.

First off, my desktop needs are pretty minimal:

1. Allow tiling my browser, Slack and Emacs on my big monitors using my keyboard.
2. Support floating windows (ie browser windows and occasional terminals for ssh) for meetings.
3. Allow a reasonably easy transition from my big monitors to my laptop screen and back again.

With that in mind, one big plus for Linux desktops is that most have some concept of tiling along with keybindings that moving windows around is pretty reasonable. One thing to note is that I used to use [StumpWM](https://stumpwm.github.io/) a for a long time, but that ends up being painful because I often need to be particular about where I put windows on video meetings. I like to keep my window close to my camera so it looks more like I'm looking at the people in the meeting. Not to mention when I share a window, I'd rather just use my mouse to get a decent size.

Thankfully, almost all the desktops I tried let me get the pseudo tiling experience without much trouble. Kudos Linux Desktop!

Where things fell flat consistently is dealing with "hidpi" aspects. The short and skinny of the experience is that I'd try something like [Xfce](https://xfce.org/) on my big monitors. I get things working, add a couple keybindings, pick a theme and generally feel like I could get things done. Then I'd disconnect my monitors and start painfully trying to find the right settings and xrandr madness to get things to be legible on my laptop screen.

Eventually, I would just start on my laptop screen to see how things would look from the get go. It was incredibly frustrating because even if I did find a reasonable way get things looking decent, I almost always still had to close apps to get the new DPI or screen settings to be applied. The end of the day, it was extremely frustrating, especially if the environment didn't provide an easy "restart" function, which many didn't.

I will say that while Linux generally seems to miss the mark for "hidpi", I suspect that the extra "hidpi-daemon" that System 76 ships with Pop_OS is really nice. It seems to pay attention to the monitors and takes an educated guess as to what the right settings should be. The apps (likely b/c they are GTK already) look fine and it is workable when I connect or disconnect monitors. There are still weird bits like when I switch to my monitors or laptop screen, the mouse cursor will stay the same size as when the app was started. Put another way, if I start my browser with my laptop screen first and switch to my monitors, I get a huge arrow until I restart the app. It is definitely annoying, but usually not too bad assuming I started the apps while connected to my monitors.

So, after trying [Xfce](https://xfce.org/), [i3](https://i3wm.org/), [Openbox](http://openbox.org/wiki/Main_Page), [Enlightenment](https://www.enlightenment.org/), [Budgie](https://ubuntubudgie.org/), and [KDE Plasma](https://kde.org/plasma-desktop), I'm back to GNOME and have switched from the Pop theme to [Arc](https://github.com/horst3180/Arc-theme).

All of this makes me want to get a Mac and forget about it, but at the same time, I do like the choice. When I get antsy like this, I know I can try some new things that are going to be different, and in some cases, radically different. I usually will learn something as well. I can't say it is "worth it", but between the moments of extreme frustration, I'm having some fun remembering part of what made Linux so fascinating in the first place, even if most of the [lcars](https://cdn.wallpapersafari.com/69/16/lzna3q.jpg) themes seem to have fallen by the wayside.
