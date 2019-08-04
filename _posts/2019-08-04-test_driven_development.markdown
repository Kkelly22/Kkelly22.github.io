---
layout: post
title:      "Test Driven Development"
date:       2019-08-04 20:50:51 +0000
permalink:  test_driven_development
---


**Test Driven Development, or "TDD"**, is a software development process that relies on a 'development cycle' in order to implement a new software feature.  This development cycle relies on 3 main phases, which can be broken down as follows:

1) Write a test that, when passed, would accurately reflect the new software feature you are attempting to implement.  When first written this test will fail because the code is not yet implemented.
2) Write the code to implement the new feature.  Development will continue until the test is passing.
3) Refactor the code once the test is passing.

![](https://www.google.com/url?sa=i&source=images&cd=&ved=2ahUKEwj5i7rggerjAhXLMd8KHcGgB2cQjRx6BAgBEAU&url=https%3A%2F%2Fmedium.com%2F%40luisfmachado%2Fswift-test-driven-development-tdd-810add46a1b9&psig=AOvVaw3ITTKb0iy_jOi73igFvJUt&ust=1565035476935518)

These tests can be separated into three main categories: 

1) Unit Testing.  Testing a unit of code in isolation to make sure the code works.
2) Integration Testing. Building on unit tests, this test combined units of code to ensure a larger combined functionality works.
3) Functional Testing.  Sometimes referred to as 'end to end' testing, this builds off integration testing and tests the full functionality of a chunk of the system.

Now that we know a little bit about Test Driven Development, let's talk pros and cons.

Pros: When you develop with TDD you have a  much clearer sense of what your code *should be* doing.  The specifications and requirements are clearly defined; the code either passes the test or fails, and it's easy to pinpoint the failure.
Cons: The development takes time, and time is of the essence.  If you are coding at a client's request, I would certainly make sure you and the client are on the same page before you spend hours implementing a test suite.

**Capybara.  What is it and why do we use it?**

When implementing end-to-end testing, we need a way to simulate the user interaction.  Capybara is a web-based test automation software that allows us to mimic user interaction.  With Capybara, we can simulate when a user "fills in" a form, "clicks" a button, "submits" a form, etc.

In sum, "TDD" is a fantastic way to keep your code on track and prevent bugs.  It takes time, but it's ultimately worth the effort to ensure your code is correct.  With advancements like Capybara, "TDD" has become an attainable and comprehensible way to write these test suites.
