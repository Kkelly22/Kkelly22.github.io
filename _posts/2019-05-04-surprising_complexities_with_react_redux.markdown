---
layout: post
title:      "Surprising Complexities with React/Redux"
date:       2019-05-04 19:06:39 +0000
permalink:  surprising_complexities_with_react_redux
---


For my final React/Redux portfolio project, I created a 'Wedding Itinerary' application.  This app allows a user to store several aspects of their wedding day into a database - mainly a Bride, Groom, Wedding Location, Wedding Datetime, and individual plans for the day.  Altogether, this creates a snapshot of the wedding day, aka a 'Wedding Itinerary'.  

As I was developing these features, I ran into an issue that helped exemplify the difference between 'data' and 'state'.  The issue I'm referring to is the very common and much needed 'Username and Password'.  Naturally, the plans created and stored by the current user had to **belong** to the current user.  I created a has_many/belongs_to relationship to handle this connection on the back-end.  However, when making fetch requests to my API, I found the only way keep track of the current user from the front-end was by state.  This works well, until the page reloads.  In comes Javascript Web Tokens - a way to keep track of the current session and pass data back and forth securely between the front-end and back-end.  Admittedly, I do not fully understand how JWT works, so I left it out of my application.  For now, the Wedding Itinerary App is only storing the current user until the page reloads.  Luckily, the asynchronous nature of my SPA (single page app) keeps things moving smoothly without the page needing to re-load.  Until then, I look forward to learning more about JWT and eventually adding this feature to the Wedding Itinerary App.

Another feature of React/Redux that seems suprisingly complex is the "update" action (CR**U**D).  To acheive this, it seems we'd need to use a fetch request to get the data, set the state, route to the input form component, bypass the state initialization, and use the state to pre-populate the form.  This seems straight-forward *except* for by-passing the state initialization.  This is another aspect I hope to implement in the Wedding Itinerary App once I have better understanding of the process.
