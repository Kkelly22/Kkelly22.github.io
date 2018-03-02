---
layout: post
title:      "Sinatra Portfolio Project"
date:       2018-03-02 18:46:25 +0000
permalink:  sinatra_portfolio_project
---


I wrote a Project Management app for my Sinatra Portfolio project.  This app has a basic sign up/sign in home screen, and allows a Project Manager to add both Project and Client objects.  This layout gives a Project Manager the ability to keep track of all projects (past/present/future) with details like name, budget remaining, status, and client. 

This was the first time a pre-written test did not tell me exactly what "has many/belongs to" relationships needed to exist, and it was my main point of confusion.  In sum, I started off with a "has many, belongs to" relationship between Project Manager and Project.  This was clear cut - a Project Manager has many projects, and a project belongs to a Project Manager.  Taking it a step farther, I added client.  Conceptually, I wanted the aspect of "client" to be more than just a text field.  I wanted the ability to see all projects relating to a particular client similar to how I could view all projects relating to a project manager.  For this reason, I decided to make Client a class.  But this is when things got conceptually tricky - I now had projects belonging to both a Project Manager AND a Client.  Did I need to associate the Project Manager class and the Client class (has many through Projects?).   I came to the answer no - because conceptually it did not seem to make sense that a Project Manager had many Clients and vice versa.  My app seems to be working well, but I am not 100% on my decision to not relate the two.

The second point of confusion I encountered was having the ability to delete an instance of the parent class without deleting an instance of the child class.  When I created the class Client, I offered the ability to delete the client altogether.  However, since a project belonged to a client, I was left with an orphaned project (on the client side).  I came to the realization this could not happen, and added "dependent: :destroy" to my Client class association.  This way, if a client is ever deleted, all of the projects associated to this Client will also be deleted.  Conceptually, this seems to make sense.

Creating your own logical associations between classes, in my opinion, is the most challenging part of designing any app structure.
