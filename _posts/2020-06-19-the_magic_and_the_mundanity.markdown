---
layout: post
title:      "The Magic and the Mundanity"
date:       2020-06-19 15:46:12 +0000
permalink:  the_magic_and_the_mundanity
---


Having now made my first fully functional CLI project, I’m struck by two simultaneous, but widely divergent feelings:

1. This was deeply, rapturously magical.
2. This was deeply, mundanely mechanical.

To be clear, experiencing simultaneous, but widely divergent feelings is just kind of where I like to hang out. And I think part of my current mixed-up-ness comes from the dawning reality of finally understanding—in some small, partial, neophyte way—what’s always already been going on under the hood whenever I’ve relied on tech.

I’m not *quite* having Neo’s “I can see the Matrix all around me!” moment–I’ve worked with literary languages too long to be shocked at learning how machine languages make the world function—but I am pleasantly surprised that coding is every bit as emotional, powerful, and absorbing as reading a good book.

So, let’s talk about CLI magic.

When I first approached this project, I definitely dreamt big. Initially, I wanted to develop an app that would work with API for the Digital Public Library of America (DPLA), an incredibly timely effort to make a fully-online public library with digital materials available to anyone, anywhere. With just three weeks of coding under my belt, I planned to put an entire digital library catalog at everyone’s fingertips. Here was the project for me!

Needless to say, access to digital texts has been an urgent need for everyone during COVID, and is simply important for everyone under ‘normal’ circumstances. And given that public libraries are often 1) spread out, 2), under-funded, and 3) transmission vectors, they simply aren’t accessible for everyone. A common joke in librarianship is that you’ll never be as sick as you are in your first year of the profession. That joke isn’t funny anymore.

So, I sat down to make my first GET requests from the DPLA’s API, visions of decentralized library access dancing in my head. Time to be the hero-librarian I could never been when I was, well, actually a librarian. I was ready for magic!

And nothing happened.

I double-checked my API key (side bar: *why is a public library requiring API keys?*), reconfigured my query, and hit enter in the browser yet again…

And nothing happened.

I triple-checked my API key (side bar: *no, really, why are librarians requiring API keys?*), re-read the API documentation from start to finish, experienced seven minutes of imposter syndrome, did my best to invoke Alan Turing, revised my request, tried again…

And nothing happened.

Yep, the DPLA’s API was busted, plain and simple. I was back at square one with my CLI project.

A couple hours of frantic searching later, I landed on a similarly public-minded project that—though I didn’t know it yet—had similarly public-minded limitations. In the interest of fully embracing my adoptive home, Colorado, I decided to work with the National Park Service’s API, in order to supply users with a smorgasbord of options for excursions.

The headaches I ran into with the National Park Service (NPS) API were less overt (it actually accepted GET requests), but still seem fairly precursory. For example:

1. There’s seemingly no way to pull data for *all* NPS sites at once. Any non-query data requests will tell you that 497 parks returned results, but only 50 can be accessed at a time. The invisible modifier on all NPS requests is a hard-and-fast limit of 50 data returns. Attempting to manually override that limit gets you a refused request.
 
2. There’s no way to query the NPS API except through a few specific fields. Literally all of the keys and values are there for searching on, but NPS simply hasn’t built queries for them.
 
3. Some of the data is incomplete or improperly formatted. Initially, my project included a “Fees” attribute for every park that would display the costs associated with visiting each NPS site. However, that proved immediately problematic because of how the data was set up, and I needed to remove the function.
 
4. For ten minutes, the NPS API went down. It went down coincidentally while I was looking up a state without any National Parks (which is not to say no *NPS-designated* sites). So, I furtively and irresponsibly Googled, and discovered that almost half of the US states *don’t* include a National Park (weird, right?). 

5. Acting too quickly, I made a second list of states to exclude from search results, ignoring that the dataset of 497 sites *clearly* meant that NPS data referenced all sites, not just National Parks. When the API came back and I discovered that Alabama was *not* returning an empty array, I realized my mistake. 

Some of these limits were actually helpful, and seemed like design choices. For example, I began my project wanting to give users the option of searching by zip code. However, that option would require pulling all the data (which is a no-no) and then iterating over each of the returned hashes in order to find matching zip codes. That’s not actually that hard, but it’s also kind of useless. Remember, many NPS sites are in the middle of nowhere, and the likelihood that a user would know their zip codes without first needing to visit another resource is pretty much nil. Querying by state—one of the few queries the NPS API allows—just makes more sense.

That being said, in the future I would like to implement geospatial data so that users could search based on their current location. Each and every NPS site comes with longitude and latitude coordinates (albeit, spread out across the hash for no discernible reason), and I’m sure there are gems I could use for calculating relative distances from a user’s coordinates. So, there’s room to grow the app, which is great!

One change that I did implement upon feedback from my husband was the simple reference of states by name after they’re queried by postal abbreviation. Yes, this means there’s a huge hash of state abbreviations and names at the end of the app, and no, that doesn’t look particularly pretty, but the reality is that the relationship between abbreviations and names is arbitrary; there’s no real way to avoid hardcode (which was, thankfully, just a copy-paste away).

To be very clear here: I believe in public institutions, and I think they need more funding, period. I am one-thousand-percent that guy who thinks he should be taxed more, so long as those taxes are spent on facilitating and forwarding the public good. So, I don’t think the problems with either the DPLA or NPS API’s are anything more than an unfortunate side effect of the US’ continual gutting of funding for public projects. 

That being said, these are digital resources whose problems urgently need solving because their physical equivalents—libraries and parks—simply aren’t always on the table. Ensuring equity of access means ensuring equity of digital access—and that means ensuring *quality* of digital access.

In retrospect, building an entire library OPAC over the course of three days simply wasn’t feasible. In truth, the failures of DPLA’s API saved me from a lot of headaches down the road when it came to implementing and filtering queries, as well as juggling the truly dizzying amount of meta-data that exists for each and every catalog item. Librarians really like records, turns out. Juggling 497 National Park sites, by contrast, is a *much* better scope for Baby Coder’s First CLI Project.

What I’ve learned over the course of this CLI Project, in addition to an incredible amount of new Ruby methods, is that the mundane in tech never fully demystifies the magical in it, and the mystical in tech never fully dissolves the nitty-gritty either. I still believe in, and feel, the magic of technology, even though I’m sometimes elbows-deep in code that I can’t always sort through.

By that same token, I still believe in, and feel, the magic of public institutions, even though I’ve seen, firsthand, the grisly way that sausage gets made. I just wish the API’s were better.

