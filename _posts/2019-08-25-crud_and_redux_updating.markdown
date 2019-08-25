---
layout: post
title:      "CRUD and Redux: Updating"
date:       2019-08-25 18:02:25 +0000
permalink:  crud_and_redux_updating
---


I am in the middle of designing a Wedding Itinerary application, which, for the most part, boils down to CRUD operations which allow a user to keep track of a wedding day itinerary.  The Create, Read, and Delete portions of this task were pretty straight forward, but the Update action initially threw me for a loop.  Let's talk through it.

My goal is to click an 'edit' button which targets the specific piece of data I'd like to edit (in this case a wedding plan), *pre-populate* an input form with this data, make the desired changes, and upon submission *rewrite* the data.  Looking at my application, I have several things at my disposal due to the existence of the Create and Delete operations.

First and foremost, I already have a button that 'deletes' a plan from the wedding itinerary.  Piggybacking from that, I can add a button that instead triggers the edit process. When this button is clicked, what is the next logical step?  My first inclination was to connect this button to an 'updatePlan' action and reducer, but that was incorrect!  How do I know which plan I need to update if I've never told my application to read it?  The next logical step is to FETCH the singular plan I'd like to update.

```
 <td><button onClick={() => this.props.fetchPlan(plan)}> X </button></td>
```

This fetchPlan action has been set up in my planActions.js file to utilize the Plan ID from the button click and fetch the singular plan.

```
export const fetchPlan = (plan) => {
  let data = {
    method: 'GET',
    headers: {
      'Accept': 'application/json',
      'Content-Type': 'application/json'
    }
  }

  return dispatch => {
    fetch(`users/${plan.user_id}/plans/${plan.id}`, data)
      .then(response => response.json())
      .then(plans => dispatch({
          type: 'FETCH_PLAN',
          payload: plan
      }))
      .catch(err => err)
  }
}
```

The next logical step is to set up a FETCH_PLAN reducer.  But let's take a step back - where are we putting this information once it is fetched?  The state, yes, but where in the state?  I can't overwrite my existing "plans" state, and "current user" state is certainly not the correct place for it.  Let's create a new state to keep track of called "current_plan", and our FETCH_PLAN reducer can update the state "current_plan".

```
export default function managePlans(state = [], action) {
	switch (action.type) {
		case 'FETCH_PLAN':
        	return action.payload
	    default: return state
	}
}
```

OK.  At this point, we can click an 'edit' button, and our new state "current_plan" should update with the plan we've clicked.  What now?  My next inclination is to pass this current_plan as a prop down to my Plan Input component like so:

```
 <PlanInput user={this.props.current} plan={this.props.current_plan}/>
```

I now have a functioning edit button which, upon being clicked, fetches the plan information and passes it down to the input form.  What next?  Pre-populate the form fields with the existing data if they exist.  How do I do this?  Let's try setting the state:

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

The code above will hopefully set the state to blank if the "current_plan" is empty (behaving like the normal "create" action), and will populate the state if the "current_plan" is populated.  The last thing to do?  If the "current_plan" is populated, we want to *re-write* the data.  If the "current_plan" is blank, we want to revert to our original "create" action and *write* the data.

```
 handleOnSubmit(event) {
    event.preventDefault();
    if (this.props.plan.length == 0) {
       this.props.createPlan({...this.state, user_id: this.props.user.id});
    } else {
      this.props.updatePlan({...this.state});
    }
   
    this.setState({
      description: '',
      vendor: '',
      location: '',
      time: '',
      completed: false,
      user_id: 0
```

I'm currently still in the process of figuring this all out, but I think I'm on the right path!
