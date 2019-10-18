---
layout: post
title:      "UI Patterns"
date:       2019-10-18 20:50:59 +0000
permalink:  ui_patterns
---


I've recently been attempting to update my single page app with tried and true UI design principles to give my application a better look and feel. In my previous blog posts, you'll see I discuss three major aspects that took my application to the 10-yard line:

1) Font Pairing
2) Texture
3) Bootstrap

I have implemented each key component above, but my application still looks lacking.  I realize this is due in large part to its **layout**.  I took to the web to research Web Layout Best Practices, and here is what I found:

There are 12 main layouts, which have been proven successful over time, and they are:

Cards
Grids
Magazine
Container-free
Split Screen
Single-page Web Apps
F Pattern
Z Pattern
Horizontal Symmetry
Approximate Horizontal Symmetry
Vertical Symmetry
Asymmetry

It is not as easy as picking one from this list at random - it is important to contemplate which layout pairs well with my functionality.  My application has a list, or "itinerary" display, with an input form to add more to the schedule.  Keeping this in mind, it sounds like the "Z Pattern" best suites my needs.

To quote [this resource](https://www.uxpin.com/studio/blog/web-layout-best-practices-12-timeless-ui-patterns-explained/),
> Like the F pattern, the Z pattern layout mimics natural user scanning methods. However the Z pattern is better suited for sites with a singular goal and less content.
> 

My application has one singular goal - to add things to an itinerary and view the content of the itinerary.  I have minimal content, so I believe this is the best choice.

I will implement this and let you know how it goes!

