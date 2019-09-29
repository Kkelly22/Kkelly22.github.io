---
layout: post
title:      "Custom JSON Serializers"
date:       2019-09-29 21:52:28 +0000
permalink:  custom_json_serializers
---


I was recently attempting to pass some RSpec tests that involved testing JSON responses.  What I learned along the way is intuitive now that I look back on it, but worth highlighting in case anyone is struggling with a similar issue.

Ruby on Rails comes equipped with a gem, 'active_model_serializers', that allows you to respond with custom JSON responses using Active Model Serializer.  This is quick and easy to set up:

1) Include gem 'active_model_serializers' in your Gemfile.
2) Run 'bundle install' to install the gem
3) For each Model in your application, run 'rails g serializer model_name'.
4) Set up each serializer to mimic your models.  For example, if my model Users 'has many chores', then my Users serializer should also 'has many chores'.

But what if I want to include my chores association when viewing all Users, but I want to exclude my chores association when viewing just one User?  Specifying the serializer in my render json statement.  For example:

```
        def show
            @user = User.find_by(id: params[:id])
            render json: @user, :except => [:created_at, :updated_at], serializer: UserSerializer, status: 200
        end
```

In my UserSeralizer, I *will not* include the "has many chores" association.

```
    def index
            @users = User.all
            render json: @users, :except => [:created_at, :updated_at], serializer: UsersSerializer, status: 200
        end
```

In my UsersSeralizer, I *will* include the "has many chores" association.

Magic!

