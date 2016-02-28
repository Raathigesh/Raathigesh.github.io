---
published: false
---


Redux is a flux library which helpes to manage application state in JavaScript applications. Even though its mostly used with ReactJS, it's a framework agnostic solution for JavaScript state management. This post aims to introduce redux concepts with a very minimalistic example.

Three fundamental parts of Redux
1. The State 
2. Actions
3. Reducers 

## The State
Redux maintains the application state in a single state object. This state object could store information related to the application such as who is the current logged in user or it could store information related to the UI state such as a state of a UI element. For example an expandable element is expanded or collapsed.

But why? For example when you build web applications, multiple components are interested in a piece of information. For example weather the user is authorized or not. So a global state is the best way to store such information so each individial UI components can access.

![SingleState.PNG]({{site.baseurl}}/_posts/SingleState.PNG)


## Actions
User interface can trigger actions. When an action is triggered, it could change the global application state.

An action have two properties, the type of the action and the data required to change the state.

An Example redux action. The type of the below action is 'SET_AUTHORIZE' and the data is 'true'.

{% highlight javascript %}
 {
 	type: 'SET_AUTHORIZE',
    data: true
 }
{% endhighlight %}

### Action Creator
Action Creator is a place an action is created. Action creator is simply a function which returns an action object. SetAuthorization() is an action creator which creates the 'SET_AUTHORIZE' action.

{% highlight javascript %}
function SetAuthorization() {
	return  {
      type: 'SET_AUTHORIZE',
      data: true
 	}
}
{% endhighlight %}

## Reducer
So far we have a global state and actions with the information on how to change the state. But who is going to change the state? Reducer is. 

Despite the fancy name, Reducer is just another function with a switch case. 

But the very important part is, a reducer is responsible for managing a branch of your global state. If we go back to our previous global state, we need two reducers to manage this state as follows.

- App Reducer - To manage the state.app branch or sub state
- User Reducer - To manage the state.user branch or sub state

![SingleState.PNG]({{site.baseurl}}/_posts/SingleState.PNG)






