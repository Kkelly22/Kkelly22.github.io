---
layout: post
title:      "Choreizo - Spice Up Your Chores"
date:       2018-08-15 17:25:38 -0400
permalink:  choreizo_-_spice_up_your_chores
---


For my Rails portfolio project, I wanted to create an app that I would actually use in my day to day life.  "What am I passionate about?" I thought.  The answer was sadly..chores.  If it were up to me, I would have my house looking like a model home at all times.  My significant other, however, not so much.  Enter..CHOREIZO!  Here to Spice Up Your Chores and your life.

The concept of Choreizo is simple - you create a user profile (sign up/log in/log out) and from there start building your household structure.  The user starts by building a Household, and then adds Chores to that household.  The user can then assign a chore to a user (whether it be themselves, or another user of the household), which in turn will create a chore "completion".  This "completion" record will have a Boolean value of "completed" which is defaulted to false.  Once the user completes the chore, the Boolean value gets flipped to true and the chore is no longer on the users to-do list.

This app separates the idea of a chore and a chore completion.  A chore is a relatively permanent aspect of the household, whereas a chore completion (aka task) is a constantly changing instance of a chore.  This ideology, along with the model relationships in general, was the toughest to figure out.  The has_many belongs_to relationship does make sense conceptually when referring to one model against one model.  However, once a couple of models start interacting and belonging to each other, the relationship logic becomes extensive.  In my case, it took me plenty of time and a study group to realize that a chore belonged to a household, **not** a user.  A user did not possess the permanent aspect that was the chore, they possessed the passing instance of a chore, aka chore completion.  Therefore, a household may have many chores, but a user has many completions, and has many chores *through completions.

Once the model relationships were established, however, the RESTful communication between Model/View/Controller provided a very organized structure to start building the application.  Throughout this entire curriculum, establishing model relationships has been my weakness, and I will continue to work towards a better understanding.

The spicy part about Choreizo? Completing a chore earns you points, and points can be exchanged for prizes.  Well, not yet.  Completing a chore does earn you points, but I hope to one day implement the notion of "redeeming points for prizes", whether that be through Venmo or a good faith coupon that says "I'll buy you a 6 pack if you mow the lawn".  For now, we will have to rely on "I have more points than you, so it's your turn to do the dishes".
