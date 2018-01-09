---
layout: post
title:      "Rack and the Internet"
date:       2018-01-09 00:17:25 +0000
permalink:  rack_and_the_internet
---


Rack is a Web Server Interface for Ruby.  Simply put, it connects the ruby code we write to the web. 

First things first, to use Rack we must 'require Rack' and have a config.ru file (among other things).  When the command 'rackup config.ru' is run a connection to a local server (only accessible on the local computer) is started.  This establishes our server connection.  Next, our config.ru file should contain the command "run Application.new".  Our class "Application" carries out what our app *actually does* with a "call" method.  This call method passes in the environment of the server connection, and will contain requests to the server, responses to the server, and and how we handle those requests and responses.

As I started to explain above, the two main forms of communication to make this process work are **requests** and **responses**.  These requests and responses communicate through a universally accepted protocol called HTTP or Hyper Text Transfer Protocol, created by Tim Berners-Lee.  We piggyback off of Rack to code these responses and requests:
> resp = Rack::Response.new
> req = Rack::Request.new(env)

Since the "req" variable takes in the current environment, we can use this variable to analyze the users behavior and code how our application will respond.  We can then send back data with the "resp" variable depending on what the user asked for.  For example, we can determine if the user attempted to GET (HTTP variable GET) the webpage ending in /profile/ by analyzing the statement *req.path.match(/profile/)*.  We can write back responses with *resp.write*, like write back an entire HTML document or just a simple statment "Hello World".  We can also assign a status of the request with *resp.status=*.  To finalize the communication, we write *resp.finish*.

This is the very basic groundwork of starting a server, receiving requests, and responding to requests with Rack.  Rack is a very low level module to utilize.  Sinatra is a higher level module to utilize, which is soon to be learned....
