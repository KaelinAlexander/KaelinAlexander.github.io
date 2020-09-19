---
layout: post
title:      "Learning to Debug Like a Boss with My First Full-Stack Application"
date:       2020-09-19 18:14:06 +0000
permalink:  learning_to_debug_like_a_boss_with_my_first_full-stack_application
---

**Or; "It's Not Me, It's Materialize"**

So far my journey through the wonders of coding has been an incredibly humbling experience—and rightly so. While I joined Flatiron School as a fairly tech-competent person, and I’ve written before about how much my coding journey has brought back those wonderful, awkward feelings of 90’s pre-teen computer camp, make no mistake: coding has bruised my ego just as often as it’s made me feel like a (very introverted) badass.

Particularly as someone who’s been on the other side of education for a while—I taught college-level English for about a decade and was a librarian for a hot minute—it’s been profoundly, dizzyingly wonderful to find myself utterly displaced as the knowing subject in the room. In fact, a good deal of my time at Flatiron has been focused on learning when not to go it alone, and when to lean on my classmates, the tech coaches, and—of course—my truly fantastic cohort lead, Enoch. I might be physically alone for my coding journey (and my quarantine, naturally), but I’m also intricately connected to all the people who have helped me, and who I’ve helped in turn—and I wouldn’t have it any other way.

However, along with learning when to ask for help, I’ve also needed to learn how to identify bugs that are well within my (admittedly still very small) wheelhouse. With my latest project—a full-stack API that allows uses to generate herbalist magicks—those bugs have generally fallen into a few distinct categories:

**1)	Linguistic Dissonance**

When I first started learning Japanese in high school, I had already been taking French for a couple years. I wasn’t fluent, but I knew enough nouns to be dangereux. As I adapted to speaking Japanese, something kind of incredible happened for a period of two months: whenever I didn’t know a word in Japanese, but had it in French, I would automatically substitute that word in, without thinking and without knowing I was doing it. 

This mortified me, befuddled my classmates, and fascinated my Japanese teacher because it led to sentences like “Kuruma wo conduire-shimashita” (Roughly, “I [Japanese] did the [French] driving [Japanese] of the car.” When I went to re-learn French in my 20’s, the reverse happened: I would find myself wondering “Does ‘kuruma’ take ‘le’ or ‘la’?” when Japanese nouns don’t have gender (or plurals, really).

As we’re semi-shifting from Ruby to JavaScript, I’m finding myself having similar linguistic whiplash on a vastly different register. All too often, I found myself attempting to shoehorn Ruby logic into a JavaScript function—which is an awkward fit at best, and especially in light of JavaScript’s hugely different object types. Lovely, dependable, Ruby, which feels like a close friend after only four months is a non-entity on the front-end. And, while Ruby has trained me into generative habits of thought, it’s also a bit like my tenth-grade French: I know just enough to get into awkward situations when I risk trying a cognate that turns out to mean “condoms” instead of “preservatives.”

The solution, of course, is to Ask Dr. Google, and the sheer wealth and generosity of JavaScripters is on full display at StackOverflow. Helper functions take on a whole new necessity when we’re dealing with vanilla JavaScript after riding multiple Ruby libraries for our last couple of projects, and I’m happy to learn how flexible JS is on that front—provided, of course, that I can train myself away from assumptions and typos around syntax, case, and keywords.

**2)	Invisible Libraries**

Rails was a trip in a lot of ways, and I often found myself bristling against its automation as often as I was leaning on it. The lack of libraries in vanilla JavaScript offered a great and welcome sense of clarity on the front-end, and my rather baroque Rails project provided me with plenty of experience parsing the three many-to-many relationships in my Spellmaker app. This time, I was sure, I knew what I would be dealing with, thanks in no small part to Enoch’s tireless review sessions.

Imagine my surprise when, having built out full CRUD for my “Spell” model, my “Component” model simply wouldn’t load. As in, the class’ declarative first-line came back with redundancy errors that claimed “Component” had already been set. But how could that be? Wondering if I had misunderstood JavaScript scope (I hadn’t) and with horrors about the potential for hoisting, I went through all of my code and replaced all block variables, lest they were somehow influencing my code.

Realizing that such a thing as a “Component” exists in React, I worried that perhaps “Component” might be a reserved word in vanilla JS, too—but no searches proved conclusive. Distraught, and struggling with the reality of needing to rename one of my models and its associated everything, I slunk into Tuesday’s Open Office Hours, convinced that I would have an afternoon of find-and-replace hell.

It turned out, Materialize was the problem, and I literally couldn’t have known. Yep, Materialize—not React, not JS, not Rails, not anything I was apparently coding in—reserved the word “Component” as a keyword. My need for beautiful styling out of the box had, it turns out, compromised my class models. Thankfully, the fix was a lot less arduous than it seemed—the JavaScript class was renamed; everything else remained the same—but it was truly a case of “It’s not me, it’s the library.” Lesson learned.

**3)	More Nodes, More Problems**

Along with Materialize’s macro issues, I also learned a lot about the value of vanilla HTML. See, Materialize doesn’t just impose keyword; it also ends up drastically affecting JS functions, particularly as my functions themselves needed to work on an ever-broadening set of elements.

Enoch’s truly magnificent review sessions helped me to realize just how many things would need to be updated dynamically over the course of a single JS fetch and its fallout. JS has truly unlocked my sense of how the internet works, and of the labor that goes on behind incredibly mundane tasks on the web.

As I shifted from simple fetches to their display ramifications, then, I began to find myself running up against Materialize yet again. Do you want to reset select options? Materialize will want you to do it in a weird way. Do you want to incorporate forms within cards? Materialize will force you to change the formatting. Do you want for pre-populated text not to overlap with labels? Materialize needs you to call a function. Over and over again, I learned that the magic of the Materialize library came with rules—rules that weren’t always apparent, but that required me to code nimbly, flexibly, and responsibly.



It’s trite to say that all these debugging challenges made me stronger insofar as they didn’t kill me—but it’s also simply true. Bugs that would’ve sent me immediately hitting the “Ask a Question” button just a month ago are simply no big deal now; they might crop up every now and then, but I have a sense of how to intuit not just how to tackle them, but when to tackle them—and when to find resources, help, or simply a break that will empower me to try a different tack.

