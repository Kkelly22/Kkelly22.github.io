---
layout: post
title:      "OR Impedance Mismatch"
date:       2019-06-16 19:46:35 -0400
permalink:  or_impedance_mismatch
---


OR Impedance Mismatch - a term we hear when discussing database architecture.  Although this term sounds complex, we can break it down into a couple of understandable and digestible concepts.  Understanding this issue will help us design a more flawless architecture from the get-go.

Object-Relational Impedance Mismatching.  This term describes a set of issues that can arise when we use an OO programing language together with a relational database.  At the core, Objects use classes and Relational databases use tables, and this subtle difference is responsible for the two not "talking" smoothly 100% of the time.  There are 5 different ways this relationship can fail:

Granularity.  This simply means that the class to table relationship is not 1:1.  It is very possible that the object model is more granular than the relationship model - meaning there are more classes in the object model than tables in the relational database (or vice versa).

Inheritance.  OO Programming languages are fundamentally equipped with inheritance, but relational tables are not.

Identity.  A relational table considers "sameness" in only one way - the primary key.  OO Programming Languages look at this a little differently - the notions of "identity" and "equality" coexist.  

Associations.  OO Programming uses associations as one-directional references, whereas relational tables use foreign keys.

Data Navigation.  In OO Programming you access data by hopping through connected associations, whereas in a relational table you use SQL queries and joins to connect the data you are interested in retrieving.  The latter is a much more efficient way of retrieving data.

As I said earlier, these differences are subtle.  If you don't look out for each issue, you may look over it entirely.  However, being aware of these subtleties will help us build a database structure will less flaws, meaning less bugs.

