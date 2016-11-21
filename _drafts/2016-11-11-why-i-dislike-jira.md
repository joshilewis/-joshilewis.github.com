=Why I dislike Jira (and other similar tools)=

**TL;DR:** Jira (and similar tools) is great for keeping track of bugs, and for tracking, coordinating and auditing work. It is a terrible way to communicate and collaborate across a team. Don't use it as a communication tool.
--------
There are some common anti-patterns I've seen in organisations that use Jira (and other similar tools). This is what I've experienced in several environments: A team goes into Backlog Refinement and/or Sprint Planning and the Product Owner (or whomever is responsible for documenting requirements) projects Jira onto the screen in the boardroom. One by one, each work-item is opened individually and the PO reads through what he or she has written. There's a little bit of discussion, the delivery team decides they're ready to play planning poker, they do so and provide an estimate for the work-item, which is captured, and then they move on to the next work-item.

The primary problem I see with this scenario is it relegates the delivery team (analysts, programmers, testers etc) to being *order takers*. The PO tells the delivery team what is required, and they go off and do it. The delivery team plays no part in exploring, understanding and defining what is required. In general, in these types of environment, the delivery team have very little understanding of the users of their software, and what problems the users are trying to solve. Why? Because they're always told what needs to be done, and why a user might want that to be done. They're never given the opportunity to understand what the user's problem actually is. (I don't believe the 'As a ... I want ... So that ... structure is particularly effective in rectifying this.)

At this point I need to make clear an opinion of mine: In the past, we believed that we could deliver amazing software products through treating a delivery team as order takes, *we'll tell you what we want and you'll do it*. I believe those days are now passed. If exploring and defining the product-to-be-created is not done collaboratively, with the delivery team participating fully, there is a clear limit to how successfully an organistion will be able to deliver great products. The reasoning behind this opinion is fodder for another article.

Almost all organisations I've experienced do not work in this way.  So let's examine the typical flow of events outlined above, when requirements aren't defined collaboratively. Instead of having a conversation, what often happens is everyone just reads what's been written down. Yes, there is some discussion and a few questions, but fundamentally the conversation is framed (and limited) by what the PO had written down previously (however long ago that was). "We don't need a conversation because all you need to know is in Jira, just read it."

Because there is a lot of content, and because the PO clearly took a lot of time and effort to write all of this content, there is a tendency to avoid asking difficult question. It must be the correct solution, right? They must have thought of everything, right?

The PO made a big investment in writing all of this down. How likely are they to be open to suggestions around solving the problem in a different way? (This is true for everyone, not just POs. Programmers are notorious for being attached to previous work.)

The opportunities for and likelihood of achieving **shared understanding** in this scenario are severely diminished. Because there is so much *stuff* written down, 'communication' must have taken place, right? We all understand what we're trying to achieve, right? The likelihood of coming up with a good solution to the problem is also severely diminished.








 - tool enslavement - workflows, configuration
  - emotional investment 
 - used as communication tool
  - PO enters lots of information
  - instead of having a conversation, PO says 'read Jira'
  - low-bandwidth, high-latency documentation
  - no opportunity for validation of understanding
  - not conducive to shared understanding
 - Because time and effort spent in writing stories a priori, more inclined to be married to those ideas, less open-minded to solving the problem
