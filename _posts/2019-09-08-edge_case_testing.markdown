---
layout: post
title:      "Edge Case Testing"
date:       2019-09-09 01:13:58 +0000
permalink:  edge_case_testing
---


Edge case testing is a vital step to execute if you'd like to consider your code fully vetted.  What are edge cases, and why are they important to test?

Edge cases are sets of data that your code will analyze that are ** a-typical** to data that typically passes through.  For example, if you have a method computing the sum of two numbers, one or both of those numbers being negative could be an edge case.  If you have a method measuring the length of a string, the string being 'undefined' is an edge case.

These are important to test because, although they may be incredibly rare, the possibility of these edge cases executing does exist.  This means that there is potential for your code to break, which we never want.

What are common edge cases to test for?  While there is no rule of thumb, here are some common edge cases to watch out for:

1.  Testing a string
      a. Empty string
			b. Excessively long string
			c. Null as an argument
			
2. Testing in integer
      a.  0
			b. Negative numbers
			c. Excessively high numbers
			d. Null as an argument

The edge cases above are obvious and intuitive for two basic data types.  However, we know that methods can take more than one argument, so combining the edge cases above can elevate the number of edge cases exponentially.  For example - your method takes one integer and one string.  I can test for the following edge cases:

1. Empty string and 0 
2. Empty string and a negative number
3. Empty string and an excessively high number
4. Empty string and null
5. Excessively long string and 0
6. Excessively long string and a negative number
7. Excessively long string and an excessively high number
8. Excessively long string and null
9. Null argument and 0
10. Null argument and a negative number
11. Null argument and an excessively high number
12. Null argument and a null argument

You can see by analyzing two simple arguments, edge case testing can get pretty involved.
