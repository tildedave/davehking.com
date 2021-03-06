---
layout: post
title: 'Suggesting Technical Improvements'
is_unlisted: 1
---

About six months ago, Tilt Engineering switched from technology-focused teams to [product-focused teams](http://engineering.tilt.com/engineering-your-organization/) - what this meant was that rather than have "API" or "Website" teams, we have a few teams focused around core customer flows (my team owns login/signup/invites).  The main benefit I've seen from this is that it allows development of new features to happen cross-platform: the same team owns the stack all the way from the JavaScript and CSS in a frontend widget down to the data persistence layer.  This is a really powerful way to create value for our customers.  However, quality and velocity of software delivery is to a great deal determined by the health of the overall codebase - the technology that's being used, how modern it is, what libraries are used and do they help or hinder the problem space, how much legacy code is around, and so on.  At our company, these concerns are largely independent of the distinctions drawn between product teams, and to maintain a high standard of quality, technology conversations still need to happen, no matter who's assigned to what team.

Here, I'll focus on one particular problem - making technical changes that require the buy-in of a whole technology group.  These are drastic changes in the codebase - introducing a new framework, switching your ORM, adding a new type of database, adding a new level of automated testing.  I see leading technical changes across a codebase as one of the key responsibilities of a senior developer, and I've led several of these in my career.  (The [data loading infrastructure](https://www.tildedave.com/2013/06/20/large-scale-client-side-data-loading.html) we built on the Rackspace Cloud Control Panel stands out as probably both the most work and having had the most overall benefit for the product.)

My model for leading technical change is:

* have an idea
* anticipate resistance
* come with code
* implement everywhere

The goal here is not for you to 'win' - it's to make things better.  The best ideas should win, no matter where they come from.  If you've got an idea, it's on you to make its strengths shine through, but to abandon it if a better one comes along.

## Have An Idea

Having the right idea really helps!  But how can you develop ideas into the right ones to bring to the team?

_Follow your passions._  I'm particularly passionate around testing - better tests, faster tests, and making sure that tests catch things that our customers otherwise might.  I'm less passionate around other things - after going overboard on SOLID earlier in my career, I find it really hard nowadays to get worked up about object factoring.  "Are there tests?  Okay, I can probably live with your particular preference for object responsibility."  That's my internal "technical compass" and yours is likely to be completely different.  If you're passionate about something, you'll have a lot more fun finding a way it can be improved.

_Know the problem space by seeing how other people solve the problem._  Engineering isn't science.  The same concepts are continually reintroduced as part of new libraries - new technology is really just solving the same problems as the old technology, in a better way.  Frontend build tooling is a good example here.  I've gone from hand-rolled Maven plugins to [Jawr](https://jawr.java.net/) to [Closure Compiler](https://developers.google.com/closure/compiler/)/LESS/YUICompressor to Gulp with Browserify, and now primarily use [Webpack](webpack.github.io).  Each of these tools solves the same basic problem - building a frontend codebase into one that can be served to the client with a minimum number of HTTP requests.  However, at each level, the tool takes on more and more responsibility.  Webpack's [CSS loader](https://github.com/webpack/css-loader) will automatically inline small PNGs and rename background images/webfonts into filenames based on an md5 hash so you don't have to manually purge your CDN on upload.  The core concepts haven't really changed since I started doing webapp development five years ago - combine your frontend assets into a few files, shrink them as small as they can be, and utilize caching as much as possible.  Putting ideas in the context of past problems both ensures you are solving real problems and allows you to leverage ideas that have worked for other teams across the industry.

_Know the problem space by reading a lot of code._  To have the right ideas that will improve the quality and velocity of a development team, you need to be connected with the problems that the development team faces in their day-to-day.   The single best way to see this is by reading as much code as you possibly can - I generally try to make sure that I understand the problem that's being solved and how the code achieves that.  Even when I moved into a primarily supervisory role in my last job I still read just about every line of code that our Control Panel team produced across our JavaScript, Python, Selenium, and Chef stacks (20+ people in 3 locations).  If you're looking to be an "on the ground" technical leader, I can't recommend this activity enough.

## Anticipate Resistance

Okay, so you have an awesome idea.  It would definitely improve things - happier customers, happier developers.  Unfortunately you can't do this one all by yourself.  Now how are you going to sell this thing to the team?  Here I mean "team" as basically anyone who might conceivably care about this.  Generally this includes anyone working in the same technology area.

_Don't assume a solution will win purely on technical merit._  Again, engineering isn't science - solutions need to be implemented by actual people.  It's foolish to expect that just you think that a solution is technically superior that your peers will also see this.  It's up to you to sell the idea to the rest of the team.

_Identify potential detractors._  Knowing how people are going to react to your suggestions is pretty important.  Based on what you know about them, which members of your team might oppose the idea?  Of course, if there's a disagreement, there might be an opportunity to strengthen the idea and make it into an even better one.  I try to have these types conversations in a 1-1 setting - "hey, I was just thinking about X, what do you think? any problems you can forsee?"  Getting early feedback from individual team members will almost certainly result in a better idea - and you want the best ideas possible.  (Meetings can be a good place for brainstorming, but not great for working through issues that detractors might have as the immediacy doesn't tend to encourage careful analysis.)

## Come With Code

Okay, you're reasonably certain that this idea has a chance to see production - related work checks out, other members seem broadly okay with it.  What's next?

_Present the idea to everyone._ You'll want to present this in a formalized way to everyone, maybe using a set of slides before digging into the code, maybe block off a conference room for an hour, maybe bring it up in a scheduled team retrospective team.  These formalized presentations are really important in creating mind-share around new ideas and I strongly recommend them.  Synchronous time lets people know this stuff is important and also helps create a positive narrative around an idea's acceptance on the team.

_You must implement a prototype._  This prototype doesn't need to be "ready to merge", but it does need to be a basically complete solution to the problem at hand.  You can't have a meeting to propose a big piece of work that you'll only do if the team agrees.  You are basically producing a demo.  Demos can cut corners on certain things (tests for one), but the main goal is to prove that the idea is a viable one and will work within your codebase.  It's not useful to suggest a solution that is done outside of the context of your technology stack.

Where can you find time to create this demo?  You'll want buy-in from your supervisor (if they're a good one hopefully they'll encourage you!)  Otherwise (to steal a line from Hunter S. Thompson), I hate to advocate nights and weekends, but they've always worked for me.  (I do understand this isn't how it works for everyone...)

## Implement Everywhere

Awesome, the meeting went well.  You've got some good feedback from the team about the way forward and it seems like you're on track to install the idea into the codebase.  The awful old ways are dead, time for the new way.

_You are the advocate, you must finish the job._  Even after a whole team presentation, you can't expect everyone to understand everything that was proposed.  They'll still be digesting the details and you are the expert on those, having implemented the prototype - you know its ins and outs.  That means it's up to you to continue the legwork of getting the idea installed.

_Provide good examples in the codebase._  You can't expect everyone to do the right thing in the codebase just because they were at that meeting.  You need to provide them with good examples in the codebase - showing them what code to mimic, basically.  Just because you've provided a solution that works in one case doesn't mean that you can expect other people to generalize it to other cases - assume that you must provide leadership until the idea has been firmly implanted and other people have innovated on top of it.

_Sometimes doing it everywhere is a waste of time._  Of course, sometimes doing it "everywhere" would be a huge time sink and of questionable utility (this is a bigger problem in a large codebase).  You may have a less-frequently updated part of the code which doesn't see a lot of development.  Going through and updating this code might not end up being a good investment.  On a past project, after redesigning our popover pattern to "frameworkize" the separation between the view (what the user saw in the popover) and the controller (what happened when clicking save), we chose to leave a section of our site with 18 different popovers unconverted and following a legacy inheritance-based pattern.  While this made future updates to that section a hassle, I'm not convinced it was the wrong choice - we infrequently made changes to that code and over time the popovers were gradually migrated to the new pattern over the course of various hack days (though I'm sure a few of the old ones still remain).

# A Recent Example: Improving Tilt's Lightboxes

At Tilt, the lightbox is one of our core design patterns.  A lightbox covers the page and presents the user with a dialog.  On mobile it stretches to cover the rest of the page.  Lightboxes can exist in the middle of a wizard context with "forward" and "back" buttons (contributing to a tilt involves choosing the amount in one lightbox and entering your credit card in another). Back in February, we ran into some problems with our existing lightbox setup - as lightboxes were stored in memory, it made it rather difficult to develop lightbox #3 in a 5 step process.  Additionally, various actions on mobile worked better as full page loads, rather than JavaScript popups - Facebook share and oauth login to name two examples.  On leaving the site to go to Facebook, we didn't have a great solution for resuming the lightbox flow on returning to the site.

The basic idea that I came up with was to use [react-router](https://github.com/rackt/react-router) for our lightboxes; we eventually landed on using query parameters for the state of which lightbox was displayed (you can see an example of this on my [Github](https://github.com/tildedave/react-router-lightboxes)).  This solved the technical problem - relatively simple, would allow redirect URIs to return to the page on mobile, and allow an easier development workflow.

I had to build team buy-in: we had recently introduced a different lightbox framework that had (finally) decoupled the "next" and "previous" concepts from an individual lightbox view (this was important because certain lightboxes would appear both inside and outside of various multi-step wizards flows).  I worked with another team member to make sure that we were still carrying forward the good things from the previous refactor while introducing yet another pattern.

After this, I converted a few lightboxes from our site to use the new code, and presented a complete working demo at a retrospective: worked through some toy examples, displayed the real examples, and walked through the implementation with the team by projecting code onto a monitor.  I got a list of takeaways from this, implemented them one-by-one, then got final signoff from the team in the form of a code review that I made sure to have everyone look at.

For final implementation I converted every "new-style" lightbox in the site to use the new solution - except for a flow that was under active development by a different product team.  To minimize disrupting that team I held off on converting that flow beyond a "proof of concept" branch that I periodically rebased.  Finally, about a month after using the new solution everywhere else, we converted that final flow and then deleted the classes associated with the old setup.

I found this example a really fun challenge - I got to learn react-router better (an exciting technology that allows for some really powerful development patterns), building team buy-in wasn't a given because we had just changed lightbox frameworks *again* back in December (meaning there was fatigue around yet another pattern), and the work involved in installing it turned out to be surprisingly challenging (specifically around Internet Explorer support).  We've continued to build on top of this lightbox framework but that isn't to say that it will survive forever - it's always waiting to be improved further by the next great technical idea.

## Conclusions

In this article I've walked through my thought process around leading technical change.  Change leadership is a pretty important topic in general, outside of the technical context, and there are a lot of great resources out there - the book [Switch](http://www.amazon.com/Switch-Change-Things-When-Hard/dp/0385528752) is a really easy to read book about change leadership from a business perspective.  Leading technical change is exciting because done right, it can lead to both better customer outcomes (less bugs around edge conditions) and a better developer day-to-day experience (less cognitive load around handling those edge conditions).  Plus, you usually get to delete a lot of code!
