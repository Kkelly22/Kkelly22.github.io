---
layout: post
title:      "What is Kotlin?"
date:       2019-10-27 23:27:27 -0400
permalink:  what_is_kotlin
---


I recently learned of a new programming language called Kotlin, and I'd like to learn more about it.  What is its history?  What is the difference between Kotlin vs other popular languages?

From what I can gather, Kotlin is designed to interperate Java.  Per Wikipedia, it is a "cross-platform, statically typed, general-purpose programming language with type inference".  The language was created in 2011 by JetBrians, lead by Dmitry Jemerov, with the purpose of fixing Java's shortcomings.

The language is a fully object oriented language while still fully interoperable with Java code.  This allows companys to make a gradual migration from Java to Kotlin.

Some of the differences are highlighted below per Wikipedia:

1) Semicolons are optional as a statement terminator; in most cases a newline is sufficient for the compiler to deduce that the statement has ended.

2) Kotlin variable declarations and parameter lists have the data type come after the variable name.

3) Variables in Kotlin can be immutable, declared with the val keyword, or mutable, declared with the var keyword.

4) Class members are public by default, and classes themselves are final by default, meaning that creating a derived class is disabled unless the base class is declared with the open keyword.
