---
layout: post
title:  "Object Relationships"
date:   2017-09-26 21:13:25 +0000
---


What is the most important thing about object relationships?  "Scope".

Object relationships mimick relationships in the real world.  An object in the real world has attributes, behaviors, and interactions, and the same can be said with the objects we create through OO programming.  However, when we are programming these attributes, behaviors, and interactions through methods it is important that we are 'aware of our surroundings'.  Each receiver of these methods has a "scope".  This scope can be thought of as the habitat for which these methods will work.  The 4 scopes (that I am aware of) are Main, Class, Instance, and Local.  The farther down the list you go, the more narrow the scope will be.

First, we start with main.  When we create a session in IRB for example, we are creating a new universe to code in.  This is where the subsequent code will live, and the "scope" refers to everything.

Secondly, creating an object within main starts with creating a class.  This class is a both a FACTORY and a BLUEPRINT, meaning not only does the class create new instances of the object, but also assigns attributes for each object.  For example, a class of Dog can create new instances of Dog, and also give each dog a breed, coat, temperment, etc.  The scope of this class is "all dog instances" that have been created.  When we define a class method, the method will act upon the class as a whole.  For example, keeping track of ALL of the instances in the class using the "@@all" variable.  It is the class's responsibility to keep track of all instances of the class, so we make the ".all" method a CLASS method, not an INSTANCE method. 

Furthermore, within each class are instances.  With the example above, an individual instance of a dog would be Golden Retreiver.  This instance belongs to a class, has attributes defined by the class, but only has a "scope" of the INDIVIDUAL INSTANCE.  When we define an instance method, the method will act upon the individual instance.  For example, keeping track of each instances NAME using the "@name" variable.  It is the instances's responsibility to keep track of it's own name, so we make the .name method an INSTANCE method (a method is implicitly assumed to be an instance method unless otherwise specified).

Lastly, within each method you are "local".  The scope of local is literally within the method.  If we were to create a local variable within a method, we could not refer to this variable outside of the method because it no longer exists.

It is essential to understand the scope of the code you are writing to accurately relate objects to one another.  If we were to relate a Dog object to an Owner object, we could not accomplish this without refering to the keyword "self".  Self is entirely dependent on the scope, and is an introspective keyword that is literally "self aware".  To relate a dog to an owner, we would need express this by "dog.owner = self" within the Owner class, or "owner.dog = self" within the Dog class.  When we say "dog.owner = self", the scope of self is an instance of the owner class.  When we say "owner.dog = self", the scope of self is an instance of the dog class.
