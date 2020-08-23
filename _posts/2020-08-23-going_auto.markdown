---
layout: post
title:      "Going Automatic (But Not Fully)"
date:       2020-08-23 18:50:40 -0400
permalink:  going_auto
---


After feeling like I blazed through the Sinatra project, I was really surprised to discover that Rails--for all its bells, whistles, and form-generating magic--was actually a huge adjusment. I've had some time to reflect, though, and I've settled on a few key takeaways for parsing through the friction I've felt while *ahem* Riding the Rails.

Central to my confusion with Rails was the switch from Sinatra's tried-and-true form tags, replete with explicit actions and methods, to Rails, well, numerous options for form generation, all of which generate forms whose actions and methods are often invisibilized by the arugments that are passed in. Take for, example, a form in my Sinatra application:

```
<h4>Build a new project.</h4>
<form action = '/projects' method='post'>
<p>Author:
<input type='text' id='author' name='author'>
<p>Title:
<input type='text' id='title' name='title'>
<p>Notes:
<input type='text' id='notes' name='notes' size=30>

<button type='submit' id='submit' class='btn grey waves-effect waves-light'>
Create Project
<i class='material-icons right'>send</i>
</button>
</form>
```

Rendered in Rails, this might look something like:


```
<%= form_for @project do |p| %>

<%= f.label :name %><br>
<%= f.text_field :name %><br>

<%= f.label :author %><br>
<%= f.text_field :author %><br>

<%= f.label :notes %><br>
<%= f.text_area :notes %><br> 

<%= f.submit "Submit Project" %>
<% end %>
```

Now, the maxim that "Rails Is Smart" is really helpful here. So, Rails--unlike Sinatra--knows that there's something called "@project," which--passed in from the controller--tells it exactly how to set up our form, and even if this is a form for a new project, or an edit form for an existing project. That's all great!

However, with my latest Rails project, things *immediately* got confused when I started off by trying to utilize Harvard University's library API. Because I was generating search results and *then* generating models based on those results, I didn't actually have a model to work off of--the entire point was to keep my database as lean as possible.

So, while Rails' "form_for" is good at dealing with known quantities, with a search result it didn't really have anything to wrap around, and I needed to go back to "form_tag," a sort of intermediary between Sinatra's Trollopian verbosity and Rails' modernist succinctness.

Using Rails, then, isn't just about leaning on the framework to do everything for you; it's about knowing how much customization you need to supply in order to achieve a given task. What's really cool, though, is that Rails automaticity--sometimes good, sometimes bad--helped me to be cognizant of all of my app's architecture, every step of the way. 

In that sense, I never felt my mind going "automatic"; Rails "magic" was never easy--it was always strategic; a tool, not a shortcut. That sense of thoughtful, intentional, flexibility has proven not just useful, but instructive, throughout the entire course of this project.
