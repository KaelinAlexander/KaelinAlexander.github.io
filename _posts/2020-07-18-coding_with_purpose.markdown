---
layout: post
title:      "Coding with Purpose"
date:       2020-07-18 22:37:13 +0000
permalink:  coding_with_purpose
---


The Sinatra project has been an opportunity not just to branch out and test my skills, but also to try to build an app that will actually serve a function out in the wild. Sure, the CLI project was a fun proof of concept, but the tools at our disposal with Sinatra are much more robust, so this really finally feels like Baby Developer’s First App.

One of my real joys over the last year is that I’ve started working for my sister’s editorial agency. Cheesy as it sounds, there’s something deeply satisfying about working for—essentially—the family business. This isn’t something I really ever considered a possibility given that my parents are educators, but my sister’s all-around go-getter-ness led her to quit a job in publishing and found her own company, and I’m incredibly lucky that she’s brought me on board. Essentially, we work with publishers and authors to guide manuscripts through the entire process of becoming books.

As the business has expanded over the last several years, we’ve continued to work primarily with spreadsheets that track deadlines, assignments, and documents. While this is fine in and of itself, it’s also not really sustainable over the long haul. As we work on more and more projects, we need a simple, elegant system for tracking processes and ensuring that everything is on target. There are a lot of moving pieces with each phase of book development, and Google Sheets really doesn’t do everything we need. And while there are several options for project management platforms, a lot of them are both expensive and overly elaborate.

For my project, then, I decided to develop a content management system that would allow us to keep track of our projects and editorial teams. This was a bit of a step up from the basic requirements of the assignment, but at this point I think it’s important both to challenge myself and to think about all the customizations that are necessary for an app to—as the advice continually goes—build and utilize objects that emulate real world relationships.

Essentially, then, my app uses four models, as well as a joined association:

1)	Users, who are essentially our administrative team of three people.
2)	Projects, created by an individual user, but visible to the whole team. These are the books we work on.
3)	Tasks, created for projects by any user. These represent components of a book project, such as copyediting, developmental editing, and design.
4)	Editors, who are assigned tasks to complete.

Projects belong to users, who have many projects. Tasks belong to projects, and can have many editors (though, typically, there’s just one per task). Editors, in turn, can have many tasks. The many-to-many relationship between editors and tasks is represented by a join table, which I called “AssignedTasks.”

Clearly, there’s a lot on the table here, and there have been some pain points for implementation. However, I’m really proud with the beta version of the system, which has a lot of room for growth, but also allows for a lot of very quick customizations.

Some of the major pain points involved:

1)	As soon as the “Delete” functions were initialized, I started getting a ton of errors from abandoned associations. 

This ended up getting an easy fix that I really couldn’t have known about: the use of a “dependent: destroy” keyword for “has_many” models. That way, if a project is destroyed, all of its tasks are destroyed and, by extension, if a task or editor is destroyed, their associated AssignedTask on the join table is destroyed. Enoch immediately saw what was happening and clued me into this tool.

2)	With empty databases, many instance variables ended up falling apart, causing—you guessed it—more errors.
The fix for this issue, was easy enough though; as soon as an instance variable is made, I simply ran checks for existence or emptiness and developed routes accordingly. Granted, this won’t be as much of an issue with full databases, it’s still worth engineering around.
3)	Nested forms are simply a pain, but worth it. Rather than developing each task on an individual basis, I used nested forms to allow users to create multiple boilerplate tasks all at the same time.

4)	I needed to use a lot of ERB. With four models, there was only so much opportunity for copy-pasting and helper methods. I’m guessing I’ll get read to filth over separation of concerns, and while there’s definitely some room for refactoring, the truth is that a lot of what’s here is simply necessary unless I ended up leaning on a lot more metaprogramming than I’m comfortable and confident writing at this point.

5)	Materialize messed up my forms. Out of the box, Materialize overrode a lot of my forms’ inputs, rendering them either useless or invisible. While the fixes weren’t actually that onerous, I didn’t know that when I first brought Materialize into the project. Ultimately, the benefits of using it outweighed the pain points in the long run, but I’d still much rather just get better at CSS and utilize that.

On the other side of this project—though not yet on the other side of its review, of course—I’m feeling much more confident. I’m really glad that I stretched myself with this project, even if there are clearly functions I need to build out, and it simply needs to be a lot prettier before it’s ready for primetime.

I actually built something my editing team can use, and that gives the project a totally different feel than the CLI project. Moving forward, I’ll definitely plan to work on projects whose utility is immanent, even if it means needing to take new challenges into account.

