---
layout: post
title:      "Learning C#"
date:       2019-07-08 01:16:10 +0000
permalink:  learning_c
---


C# is an object oriented programming language developed by Microsoft.  Ruby is an object oriented programming language developed by Yukihiro "Matz" Matsumoto.  Although they are entirely different languages with various pros and cons on each side, their object oriented nature provides a commonality which allows programmers to curb the learning curve that comes along with picking up a new language.

In my case, I am learned in Ruby and would like to learn C#.  My initial tactic to picking up the basics of C# is simple - understand the syntactical differences between Ruby and C#.  Knowing the basics of C# syntax paired with understanding its object oriented roots will acheive a basic understanding of the lanuage - at least enough of an understanding to be able to start coding.

Let's look at a very basic example in C# which highights class syntax ([taken from Tutorials Point](http://https://www.tutorialspoint.com/csharp/csharp_basic_syntax.htm)):

```
class Rectangle {
      
      // member variables
      double length;
      double width;
      
      public void Acceptdetails() {
         length = 4.5;    
         width = 3.5;
      }
      public double GetArea() {
         return length * width; 
      }
      public void Display() {
         Console.WriteLine("Length: {0}", length);
         Console.WriteLine("Width: {0}", width);
         Console.WriteLine("Area: {0}", GetArea());
      }
}
```

If I were to right the same code in Ruby, I would write the following code:

```
class Rectangle
	length = 4.5
	width = 3.5

	def GetArea
		length * width
	end

	def Display
		area = GetArea
		puts "Length: {0}" + length
		puts "Width: {0}" + width
		puts "Area: {0}" + area
	end
end
```

I notice several main differences right off the bat:
1. C# declares its classes with {} syntax, whereas Ruby does not.
2. C# specifies the data type when declaring its variable, Ruby does not.
3. C# declares an access level when declaring types, Ruby does not.

In sum, in the C# example above, I can ascertain that the length and width variables are of type "doubles", the Acceptdetails function is of return type "void" with public access, the GetArea function is of return type "double" with public access, and Display function is of return type "void" with public access.  A return type of "void" simply means no value is returned.

My first impression the comparison - the C# syntax is slightly more complex, but tells the programmatic story up front.  Ruby is more readible, but the programmatic logistics are not as obvious.
