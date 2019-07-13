---
layout: post
title:      "Learning C# Cont..."
date:       2019-07-13 14:22:43 +0000
permalink:  learning_c_cont
---


As I dive deeper into learning C#, I can't help but jump straight into coding in order to further my understanding of the language.  I've taken to .NET Fiddle to try out some basics.  Let's look at a very basic, example which outlines how Interfaces, Classes, and Inheritance work in C#.

```
using System;

interface IExercise {
	void Workout();
}

class Cycle : IExercise {
	public void Workout () {
		Console.WriteLine("I choose to exercise by cycling!");
	}
}

class Walk : IExercise {
	public void Workout () {
		Console.WriteLine("I choose to exercise by walking!");
	}
}

class Run : Walk {
	new public void Workout () {
		Console.WriteLine("I choose to exercise by walking fast, and then running!");
	}
}
	
					
public class Program
{
	public static void Main()
	{
		//experiment with outputs here
		new Walk().Workout();

	}
}
```

Let's walk through the syntax:

**"using System;"**  is a namespace declaration.  "System" is a particular namespace that equips the language with some built in fundamentals we take for granted when coding.  To quote Microsoft:
> The System namespace contains fundamental classes and base classes that define commonly-used value and reference data types, events and event handlers, interfaces, attributes, and processing exceptions.
> 

**Interface IExercise** is an interface.  Interfaces are responsible for declaring variables, methods, properties, etc. however they cannot implement them.  In order to implement the code declared in an interface, we use a class. * A class will implement an interface.*

**Class Cycle/Walk** are classes.  As I just mentioned, these classes are responsible for implementing the method Workout(), since the interface cannot hold this responsibility.  Interestingly, each class can implement it's own version of the same method.  We will analyze the outputs of this code in a bit.

**Class Run** extends Class Walk.  This means Class Run inherits everything that Class Walk can do, but can override certain features.  Notice the "new" keyword in the statement "new public void Workout () ".  This "new" keyword signifies an override from whatever behavior that was defined in Class Walk.

**public class Program** and **public static void Main** is where we implement all of the code we've defined above.  In my example above, by typing the statement "new Walk().Workout();" I am implementing the method Workout from the Walk class.

Let's take a look at some example outputs.

* If I run the code new Walk().Workout();, the output will be "I choose to exercise by walking!".  This is because the method Workout() is being executed from the Walk class.
* If I run the code new Cycle().Workout();, the output will be "I choose to exercise by cycling!".  This is because the method Workout() is being executed from the Cycle class.
* If I run the code new Run().Workout();, the output will be "I choose to exercise by walking fast, and then running!".  This is because the method Workout() is being executed from the Run class, and the "new" keyword supersedes the existing method.
* If I run the code IExercise().Workout();, the compiler will give me an error.  The error will be "Compilation error: Cannot create an instance of the abstract class or interface 'IExercise'".  Why?  Because interfaces are for declarations, NOT implementations.


My takeaway from this coding exercise?  Using a online compiler system like .NET Fiddle is extremely helpful in understanding a new language.  This exercise has taken me one step closer to having a well-rounded understanding of C#.




