---
layout: post
title: 'Four Months of iOS Programming'
is_unlisted: 1
---

So I'm still at Tilt.  About a year ago we [reorganized our teams](http://engineering.tilt.com/engineering-your-organization/) around product areas - this January we did the other half of this and moved our mobile application delivery to be a responsibility of our product teams.  My team is now responsible for delivering features across the website (tilt.com), iOS, Android, and the API (our notifications platform).

At Tilt, the iOS app is our "flagship product" - of our various platforms, it's the most important one to build product features into for our users ("Tilters").  Because of the need to deliver on the iOS platform, we've also started getting people across the organization contributing into our iOS codebase.  I and a few others on the team are now getting on-the-job training in Objective C and Swift, as we shift our team's primarily deliverable to be features in the iOS app.

It's been more than ten years since I've done any native development (Windows MFC development in C++ in 2002).  Getting into the iOS ecosystem has been a new set of technologies to learn and a whole new development cycle.  Lots of struggling to understand auto layout and make sure my containers don't collapse to 0 height and width (CSS didn't have this problem!).  Making stuff that works great in the iPhone 6 simulator but is visually broken on the postage-stamp-sized iPhone 4s.  And of course, back to waiting for compile times.

I've gone through a technology transition a few times in my career: my first job was helping to maintain an search cluster (Java with Lucene), where I needed to learn Red Hat Linux.  I moved into web apps, where I needed learn Java web technologies (Struts + JSP) and a little JavaScript.  Next, I moved to a project using much more modern (at the time) technologies - Closure Library JavaScript and Python Django.  Each time it's been really jarring, but it's always opened me up to more challenges and better opportunities.

Going through a technology transition as a team lead is a bit different than as a pure individual contributor.  My role is primarily to drive team success - my daily routine is a combination of project management (where are the tickets at, are there any blockers), code reviews (based on what I know of the system, is there anything I can do to improve), and longer-term thinking (is everyone happy?  how can I help people with their career goals?).  I'm still pretty involved in the day-to-day of the various codebases, but I don't measure my success primarily through code output any more.

In the past, I made it through these transitions by spending a lot of time (especially out-of-work time) to get myself to a point where I was comfortable in the new area.  This time things feel different; it's still important to get up to speed on the new stuff, but at the same time, I know that my team won't be successful if I have to be the one that knows and does everything.  I've held off on doing large refactorings that I might otherwise dive into as a learning mechanism, and spent a lot more time on the smaller meat-and-potatoes stuff: fixing crashes, style tweaks, copy changes.

There's still valuable tactical guidance that I have to give, but I need to let everyone else learn the new stuff at their own pace, and making sure that they have the resources to succeed.  It can be tough to watch people struggle, especially when a lot of time gets put into something that ends up getting thrown away - during the learning process I expect people to struggle more, but struggling is a big part of the learning process.  This has resulted in a bit of a slower burn but it feels a lot more sustainable.
