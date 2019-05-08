---
layout: post
title:      "Class Components vs Functional Components"
date:       2019-05-08 23:55:27 +0000
permalink:  class_components_vs_functional_components
---


There are two types of components we can create - one is a Class Component, and one is a Functional (or stateless) Component.  The differences between the two are not obvious at first, however they are important to note.

First and foremost - syntax:

**Class:

class TestComponent extends React.Component {
    render() {
		    return something
		}
}**


**Functional:

const TestComponent = props => display something**


At first glance, we see that a class component extends React.Component.  This means a class component is capable of maintaining state.  A functional component is stateless.  If your end game is to simply display data that has been passed down as props, then a functional component is the right choice.  All other scenarios would require the use of a class component.  These class components have access to maintaining state and also lifecycle hooks meaning a lot more functionality is built in.

However, a class component can be used *all the time* and you will achieve the same results.  Why should we use a stateless component over a class, if a class has more functionality?  Among other things, **performance**.  Because a class component is a Javascript class, React creates instances of this class during processing.  If all we need to do is display a prop, we lose efficiency if we choose to create a class by the sheer amount of code that is processed.

Armed with the knowledge of a functional component over a class component, I will aim to code my front-end with more efficiency and performance in mind, instead of defaulting to the use of a class component every time.
