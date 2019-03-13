---
layout: post
title:      "Chorizo x Javascript"
date:       2019-03-13 19:05:42 -0400
permalink:  chorizo_x_javascript
---


The goal of my latest portfolio project was to "AJAX-ify" my Rails app named "Chorizo".  "Chorizo" is a Ruby on Rails application with a heavy emphasis on MVC architecture that allows a user to keep track of chores for a given household.  By "AJAX-ify", I mean adding asynchronous javascript requests into the flow of my MVC.  This new AJAX flow would hijack my MVC route, dynamically request data from the Rails backend, and dynamically render this data on the front-end (all without leaving the page).

It wasn't until this project that it dawned on me - AJAX and MVC do not really flow together, at all.  My "Chorizo" app was routing to very different views practically every click event, whereas AJAX was looking for a single view that it could update as needed.  Once this "single page app" mentality clicked, the rest started to flow.

I began to add AJAX requests into the app on a smaller scale, not expecting the app to flow dynamically on a grander scale.  For example, my chores#show route was an established view - adding a "Next Chore" click event to this view and dynamically rendering the "next chore" was easily doable without having to re-work my entire app.  A code snippet below walks through the process:

	$('#js-next').on('click', function (e) {                                             #identify the click event
 		e.preventDefault();                                                                          #prevent the default routing
 		let nextId = parseInt($("#js-next").attr("data-id")) + 1;        #use the current id to compute the next id
   		$.get("/chores/" + nextId + ".json", function(data) {           #send an AJAX request to the /chores/"next chore" route
   			let chore = new Chore(data);                                                   #turn the response into a Javascript Object Model
   			$("#chore-descrip").html(chore.formatFullChore());      # load the reponse into the div (updating the DOM)
   			$("#js-next").attr("data-id", nextId);                                       #updated the "next id" so this click event works in the future
   		});
	});


As I understand it, the next sections (React and Redux) will continue with this "single page app" mentality, and "updating state" will become second nature.  It sounds like "Chorizo" has a major face-lift in it's future!
