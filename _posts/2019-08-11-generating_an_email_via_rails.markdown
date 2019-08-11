---
layout: post
title:      "Generating an Email via Rails"
date:       2019-08-11 12:20:47 -0400
permalink:  generating_an_email_via_rails
---

I was recently asked to build out a piece of functionality that I had never done before - sending an automated email after filling out a form.  To my surprise (but not really), Rails had this functionality already built in.  In this blog post, we're going to walk through setting up a basic mailer.

First, let's utilize our generator to create the files we need.  In my example, my mailer will be tied to a user, so I will call it "UserMailer".  My generator command will be "rails generate mailer UserMailer".  This will give me the following files:

```
      create  app/mailers/user_mailer.rb
      invoke  erb
      create    app/views/user_mailer
      invoke  test_unit
      create    test/mailers/user_mailer_test.rb
      create    test/mailers/previews/user_mailer_preview.rb
```

Now that the basic functionality is there, let's customize it.  I want to send a welcome email that provides the user with a unique "code" tied to their account.  The user can share this code with friends and family.  Friends and family can then login using just this code, instead of creating an account themselves.

```
class UserMailer < ApplicationMailer
	default from: 'kk504408@gmail.com'

	def welcome_email
    	@user = params[:user]
    	mail(to: @user.email, subject: 'Welcome to Your Wedding Itinerary')
  	end
end
```

In the example above, I am sending am email from my personal email to the users email.  Obviously, for this to work the user will need to have an "email" attribute in our database.  I will place a 'required' validation on this attribute in my model/user.rb file.

To set up the content of my email, I set up a view within views/user_mailer called "welcome.text.erb":

```
Welcome to the Wedding Itinerary App, <%= @user.bride %> & <%= @user.groom %>
=============================================================================
 
You have successfully signed up a Wedding Itinerary,
your username is: <%= @user.username %>.
your shareable wedding code is: <%= @user.wedding_code %>
  
Thanks for joining and have a great day!
```

Sending the email boils down to one line of code - calling the mailer.  In my case, I want to send the email once the user successfully signs up.  I will add this to the create method of my users controller:

```
  def create 
    user = User.create(user_params)
    if user && user.valid?
      UserMailer.with(user: user).welcome.deliver_now
      render json: { current: user }
    else
      render json: { error: 'Failed to Sign Up' }, status: 400
    end
  end
```

The only thing left to do at this point is connect my personal email to the application via environment variables.  A more in depth look at this process can be found [here](http://railsapps.github.io/rails-environment-variables.html). 

For more information on Action Mailers, you can visit [here](https://guides.rubyonrails.org/action_mailer_basics.html) for the official documentation.
