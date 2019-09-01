---
layout: post
title:      "CRUD and Redux: Updating Part 2"
date:       2019-09-01 22:51:44 +0000
permalink:  crud_and_redux_updating_part_2
---


In my last blog post I discussed how an edit action would work in my React/Redux application.  To quickly sum it up, I added an edit button to each 'wedding plan' in my list of plans, and clicking this button would fetch the plan in question using the plan ID and pre-populate the input form with the plan's information.  I can then edit the information and re-submit the input form, and the plan's information would re-write instead of write.

I ran into a challenge with this process that is worth sharing - what is the best way to pre-populate the state of the input form?  In my last blog post, I tried utilizing the method constructor to set the state using my prop:

```
  constructor(props) {
    super(props);
    this.state = {
      description: props.plan.length == 0 ? "" : props.plan.description,
      vendor: props.plan.length == 0 ? "" : props.plan.vendor,
      location: props.plan.length == 0 ? "" : props.plan.location,
      time: props.plan.length == 0 ? "" : props.plan.time,
      completed: props.plan.length == 0 ? false : props.plan.completed,
      user_id: props.plan.length == 0 ? 0 : props.plan.user_id
    }
  }
```

This did not work.  Even though my state was being updated immutably and Redux was capturing the difference, my component was not re-rendering.  I then tried to set the state in componentDidMount, which, after experiencing this first hand, is a big no-no.  This causes an endless loop of re-rendering.  After a couple hours of researching I found a lifecycle method that works wonders, and that is componentWillReceiveProps:

```
  componentWillReceiveProps(nextProps) {
    if (nextProps.plan.description !== this.state.description) {
      this.setState({ description: nextProps.plan.description });
    }
    if (nextProps.plan.vendor !== this.state.vendor) {
      this.setState({ vendor: nextProps.plan.vendor });
    }
    if (nextProps.plan.location !== this.state.location) {
      this.setState({ location: nextProps.plan.location });
    }
    if (nextProps.plan.time !== this.state.time) {
      this.setState({ time: nextProps.plan.time.replace("Z","") });
    }
    if (nextProps.plan.completed !== this.state.completed) {
      this.setState({ completed: nextProps.plan.completed });
    }
    if (nextProps.plan.user_id !== this.state.user_id) {
      this.setState({ user_id: nextProps.plan.user_id });
    }
  }
```

This method is able to compare the existing props to the upcoming props and will only set the state if a change is encountered.  This avoids an endless loop.

HOWEVER, this is not the best option either.  After reading React's docs, this is not suggested either.

> Note
> 
> This lifecycle was previously named componentWillReceiveProps. That name will continue to work until version 17. 


A suggestion around this?

> If you used componentWillReceiveProps to “reset” some state when a prop changes, consider either making a component fully controlled or fully uncontrolled with a key instead.
> 

After this information, even though my input form is successfully pre-populating, I am to tackle this from a different approach.  My next path forward is making my input form fully controlled.

Stay tuned!
