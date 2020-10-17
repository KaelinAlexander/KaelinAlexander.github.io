---
layout: post
title:      "A New State of Mind for State in Redux"
date:       2020-10-17 00:23:49 +0000
permalink:  a_new_state_of_mind_for_state_in_redux
---



When I first started my React/Redux project—a client that stores and models information about various species of dinosaurs—I thought I knew the value of that library’s most obvious asset: a centralized store to which (hypothetically) all components can be connected, and from which they can derive anything they might need to know about the backend, but without unnecessary fetch request.

As I built out my project, though, I came to appreciate the real flexibility that store gives us, particularly when it’s de-coupled from state. See, in “vanilla” React (which is really an ironic way of saying “extremely fancy JavaScript”), state and props are all we have for shuffling data between components. That endless tethering isn’t just an onerous game of hot potato between data stores; it’s also a liability insofar as it can force components to hold on to state that they don’t really need, simply so that they can pass it on to components that do.

With Redux, though, that endless game of catch—less server-intensive, I guess, from an endless game of requests to an API, but just as baroque—comes to an end. By connecting components directly to the Redux store, centralized state becomes a lot more of a buffet; you take what you want, and leave what you don’t—when and where you want it.
The real fireworks, though, are when Redux frees up component’s state for much more interesting things than merely holding onto, showing, or updating models.

With this project, I wanted to utilize Bulma, a CSS framework that is at least as robust as Materialize and, seemingly, much less prone to bugs. Out of the box, Bulma-React offered me a ton of components—columns, cards, tabs, buttons, and all manner of typography, just to name a few—that were, again, take what you want and leave what you don’t. That economy is a real asset for new developers, since there’s no real possibility of overwhelm; if a Bulma component is available to you, that’s because you chose to pick up the tool.

Where I challenged myself previously through complicated object relations (Five join tables in one project? Sure!), this time I wanted to think a bit more about UI. Thankfully, Redux is the perfect tool for bridging form with content. How?
Well, let’s review the steps necessary for getting a Modal to work in JavaScript. Briefly, to set up a modal, you need to:

1. Find a CSS framework that comes with modals, or write the necessary CSS yourself.
2.  Set up your modal somewhere in the DOM.
3.  Place an event listener on that DOM element after targeting it.
4.  Modify the modal, toggling “is-active,” or the syntax of your CSS framework’s choosing.
5.  Modify the modal again when it’s closed.

Admittedly, doing that in JavaScript isn’t all that bad, but it does require some acrobatics.

In Redux, though, the magic of state is also a blessing for easy implementations of smooth UI. Freed from merely serving as a vehicle for data attributes, thanks to the magic of mapStateToProps, state can serve as a catch-all for UI expansion.

So, rather than going through all manner of targeting and re-targeting and modifying DOM elements, as in truly vanilla JavaScript, it’s incredibly easy to toggle a modal with the magic of state. How?

Well, for starters, you can set up state to handle UI. In this implementation, I first set up my state to two UI attributes:
  
```
state = {
			modalToggle: "modal",
			deleteId: null
	}
```

The first, “modalToggle,” is initially set to “modal”—the default attribute property that Bulma needs within the modal’s className. Then, rather than hard-coding the JSX for that modal, I set up its className attribute as equal to that attribute of state itself:

<div className={this.state.modalToggle}>
		<div className="modal-background"></div>
		<div className="modal-card">
		<div className="modal-card-head">
		<p className="modal-card-title">Are you sure you want to delete this dinosaur?</p>


Toggling the modal on and off is as easy as updating state:

```
handleClick = event => {
		this.setState({
				modalToggle: "modal is-active",
				deleteId: event.target.parentElement.id
		})
}
```

That second attribute, deleteId, is also an incredible bit of economy. Because the icons that trigger the modal are generated for every item in an index, it would be a pain to have to pass the id for deletion from function to function, as I’d likely need to in JavaScript. By storing the deleteId within state, the delete function itself has an easy, accessible place for targeting the right dinosaur for, well, digital extinction:

```
handleDelete = event => {
		let deleteId = parseInt(this.state.deleteId)
		this.props.deleteDinosaur(deleteId)
```


All of this is possible because Redux opens up new possibilities for state—in and out of the store.

